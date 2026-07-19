# C++ Fundamentals
_M.E. CS interview core · semiconductor / embedded filter_

## Why it matters
HirePro / CoCubes OAs at Tier S are **code-output heavy**: pointers, `sizeof`, `volatile`/`static`/`extern`, struct padding, light C++ (virtual, RAII). Interviews add whiteboard memory layout, Rule of Five, `atomic` vs `volatile`. High weight at:

| Company | How C/C++ shows up |
|---|---|
| [Qualcomm](../companies/tier_S_semiconductor/Qualcomm.md) | Output MCQs; MMIO/`volatile`; memory layout; smart pointers in software rounds |
| [Texas Instruments](../companies/tier_S_semiconductor/Texas_Instruments.md) | HirePro keyword + padding + pointer arithmetic |
| [MediaTek](../companies/tier_S_semiconductor/MediaTek.md) | Struct sizes, function pointers, embedded C style |
| [AMD](../companies/tier_S_semiconductor/AMD.md) | Modern C++: move, RAII, atomics, vtable |
| [Arm](../companies/tier_S_semiconductor/Arm.md) | Alignment/packing on strict-alignment CPUs; AAPCS awareness |

Day-before: [Boss Sheet](#boss-sheet) + re-solve the [MCQ bank](#code-output-mcq-bank).

---

## Concept summary

### 1. Memory layout — TEXT / DATA / BSS / HEAP / STACK

```
HIGH
│  STACK ↓          locals, return addr  (per thread)
│  mmap / libs
│  HEAP ↑           malloc / new
│  BSS              uninit globals (zeroed by loader)
│  DATA             init globals
│  TEXT / RO        code + often string literals
LOW
```

| Segment | Contents | Example |
|---|---|---|
| TEXT | Instructions | `main`, functions |
| DATA | Initialized globals/statics | `int g = 5;` |
| BSS | Zero globals/statics | `int g;` / `static int s;` |
| HEAP | Dynamic | `malloc` / `new` |
| STACK | Frames | `int local;` |

BSS stores only *size* in the binary (zeros filled at load). String literals → typically RO. Each thread: own stack; shared heap/globals. Stack overflow → `SIGSEGV`.

```c
int in_data = 42;       /* DATA */
int in_bss;             /* BSS */
void foo(void) {
    int local = 1;      /* STACK */
    static int fs = 7;  /* DATA */
    int *h = malloc(4); /* HEAP */
    free(h);
}
```

---

### 2. Pointers
Pointer = address; type sets load size + arithmetic scale. Arrays decay to `&arr[0]` except `sizeof` / `&arr`.

| Declaration | Meaning |
|---|---|
| `int *p[10]` | Array of 10 pointers |
| `int (*p)[10]` | Pointer to array of 10 ints |
| `int (*fp)(int)` | Function pointer |
| `const int *p` | Can't modify pointee via `p` |
| `int * const p` | Can't reseat `p` |

`void*` — cast before dereference. Double pointer — callee updates caller's pointer (`realloc` out-param). **Never** return `&local`. `a[i] == *(a+i) == i[a]`.

```c
void grow(int **pp, size_t n) {
    int *q = realloc(*pp, n * sizeof *q);
    if (q) *pp = q;
}
typedef void (*isr_t)(void);
isr_t table[] = { uart_isr, timer_isr }; /* HAL jump table */
```

---

### 3. `malloc` vs `new`
| | C heap | C++ |
|---|---|---|
| Allocate | `malloc` / `calloc` / `realloc` | `new` / `new[]` |
| Free | `free` | `delete` / `delete[]` |
| Init | `malloc` uninitialized; `calloc` zero | Runs constructor |
| Failure | `NULL` | Throws `std::bad_alloc` (unless nothrow) |

**Never mix** `malloc` with `delete`. On `realloc` fail, old pointer stays valid. Conceptual malloc: header *before* user pointer; split/coalesce free chunks; large → `mmap`.

Bugs to recognize: **UAF**, **double-free**, leak, buffer overflow. Hygiene: `p = NULL` after free. Embedded often: pool / no heap after init.

---

### 4. Keywords — `volatile` / `static` / `extern` / `const`

| Keyword | Interview one-liner |
|---|---|
| `const` | No write through this lvalue |
| `volatile` | Every access observable to compiler (MMIO, ISR flag) — **not** thread sync |
| `static` (local) | Lifetime = program; init once |
| `static` (file) | Internal linkage |
| `extern` | Declare; definition lives elsewhere |
| `register` | Archaic; can't take address in C |

```c
static volatile uint32_t *const REG = (uint32_t *)0x4000C000u;
void send(char c) { *REG = c; } /* must actually store */

int tick(void) {
    static int n; /* BSS → starts 0 */
    return ++n;   /* 1, 2, 3, … */
}
```

Casting away `const` then writing = **UB**. C++11 function-local static init is thread-safe ("magic statics").

---

### 5. Struct padding (`sizeof`)
Member at offset multiple of its alignment. Struct size rounded up to multiple of max member alignment.

```c
struct A {
    char c;   /* 0 */
    /* 3 pad */
    int  i;   /* 4 */
    char d;   /* 8 */
    /* 3 pad */
}; /* sizeof(A) == 12 typically */

struct B { int i; char c; char d; }; /* sizeof == 8 — reorder saves space */

#pragma pack(push, 1)
struct P { char c; int i; char d; }; /* sizeof == 6 — unaligned risk on ARM */
#pragma pack(pop)
```

| Struct (typical LP64) | `sizeof` |
|---|---|
| `{char,char,char}` | 3 |
| `{char,int}` | 8 |
| `{short,int,char}` | 12 |
| `{double,char}` | 16 |
| `{char,double,char}` | 24 |

Prefer reorder over pack. Bit-field layout = implementation-defined.

---

### 6. vtable / vptr
Polymorphic object → hidden **vptr** (often @0) → class **vtable** of function pointers. Virtual call = load vptr + indirect call.

```
Derived object: [ vptr | Base fields | Derived fields ]
                    │
                    ▼
              vtable[Derived]: &Derived::f, …
```

```cpp
struct B {
    virtual void f() { std::cout << "B"; }
    virtual ~B() = default; /* required for delete via B* */
    int b;
};
struct D : B {
    void f() override { std::cout << "D"; }
};
B *p = new D;
p->f(); /* "D" */
```

During ctor/dtor, dispatch uses *currently constructed* class. Slicing (`B b = d;`) drops derived + polymorphism. Pure virtual → abstract. MI may need multiple vptrs/thunks.

---

### 7. RAII & smart pointers
**RAII:** acquire in ctor, release in dtor — exception-safe cleanup.

| Type | Ownership |
|---|---|
| `unique_ptr` | Exclusive; move-only — **default choice** |
| `shared_ptr` | Shared; atomic refcount in control block |
| `weak_ptr` | Non-owning; breaks cycles; `lock()` → `shared_ptr` |

Prefer `make_unique` / `make_shared`. Refcount thread-safe; **pointee** is not. Never `delete` what a smart pointer owns.

```cpp
struct Node {
    std::shared_ptr<Node> next;
    std::weak_ptr<Node> back; /* break cycle */
};
```

---

### 8. Rule of Five
If you manage a raw resource: destructor, copy ctor, copy assign, **move ctor**, **move assign** (or `= delete` / `= default` deliberately). Prefer **Rule of Zero** (compose `vector` / `unique_ptr`).

`std::move` = cast to rvalue ref — does not move by itself. Leave moved-from object **valid**. Mark moves `noexcept` so `vector` can relocate efficiently.

```cpp
class Buffer {
    size_t n_{}; char *data_{nullptr};
public:
    explicit Buffer(size_t n) : n_(n), data_(new char[n]{}) {}
    ~Buffer() { delete[] data_; }
    Buffer(const Buffer& o);           /* deep copy */
    Buffer& operator=(const Buffer& o); /* copy-and-swap */
    Buffer(Buffer&& o) noexcept : n_(o.n_), data_(o.data_) {
        o.n_ = 0; o.data_ = nullptr;
    }
    Buffer& operator=(Buffer&& o) noexcept;
};
```

Don't `return std::move(local)` — can inhibit NRVO.

---

### 9. `atomic` vs `volatile`

| | `volatile` | `std::atomic` |
|---|---|---|
| Role | Suppress compiler elision (MMIO) | Synchronize threads |
| Atomic RMW | No | Yes |
| Memory order | None | acquire/release/seq_cst/… |
| Threads | **Insufficient** | Correct tool |

```cpp
std::atomic<bool> ready{false};
int data = 0;
void producer() {
    data = 42;
    ready.store(true, std::memory_order_release);
}
void consumer() {
    while (!ready.load(std::memory_order_acquire)) {}
    /* data == 42 */
}
```

Interview fail phrase: *"I'll just make it volatile for threads."*

---

## Most-asked patterns
1. Draw TEXT/DATA/BSS/HEAP/STACK; place `static`, `malloc`, local.  
2. Predict `sizeof` / `offsetof` for mixed structs.  
3. Pointer arithmetic + `i[a]` + array decay in `sizeof` param.  
4. `volatile` for MMIO vs `atomic` for threads.  
5. Virtual call path; why virtual destructor.  
6. Implement / narrate Rule of Five Buffer.  
7. `unique_ptr` vs `shared_ptr` vs cycle + `weak_ptr`.  
8. UAF / double-free recognition in code review.  
9. Unsigned + signed conversion gotchas.  
10. Endianness via `union` (little-endian OA default).

---

## Practice bank
1. Classify 8 variables into segments.  
2. Write `memcpy` / `memmove` (overlap).  
3. Three `sizeof` puzzles + one `#pragma pack` risk on ARM.  
4. Toy bump allocator (interview).  
5. Sketch `unique_ptr` move-only.  
6. Fix broken busy-wait flag with atomics.  
7. Timed: [MCQ bank](#code-output-mcq-bank) in 25 minutes (HirePro pace).  
8. Explain `extern "C"` / name mangling.  
9. Empty class with virtual → size includes vptr (not 1).  
10. Placement `new` one-liner use case.

---

## Code-output MCQ bank
<a id="code-output-mcq-bank"></a>
_Qualcomm / TI / MediaTek style. Assume GCC/Clang, LP64, little-endian x86 unless noted. Prefer saying **UB** in interviews when that's the real answer._

**Q1.**
```c
int main() {
    int x = 5;
    printf("%d %d", x++, ++x);
}
```
**Answer:** **UB** (unsequenced modifications). Compilers may print `5 7` / `6 6` — say UB aloud.

**Q2.**
```c
int a[3] = {1,2,3};
printf("%d", 2[a]);
```
**Answer:** `3` — `a[2] == *(a+2) == 2[a]`.

**Q3.**
```c
char *s = "gate";
printf("%c", *((s+2)-1));
```
**Answer:** `a`.

**Q4.**
```c
struct S { char a; int b; char c; };
printf("%zu", sizeof(struct S));
```
**Answer:** typically **`12`**.

**Q5.**
```c
int main() { static int i; printf("%d", i); }
```
**Answer:** `0`.

**Q6.**
```c
int f(void){ static int x = 5; return x++; }
int main(){ printf("%d %d", f(), f()); }
```
**Answer:** `5 6`.

**Q7.**
```c
void f(int a[]){ printf("%zu", sizeof a); }
int main(){ int b[10]; f(b); }
```
**Answer:** `sizeof(int*)` → typically **`8`** (decay).

**Q8.**
```c
int x = 3; int *p = &x;
printf("%d", p == &*p);
```
**Answer:** `1`.

**Q9.**
```c
int x = 5; const int *p = &x; x = 6; printf("%d", *p);
```
**Answer:** `6`.

**Q10.**
```c
char a[] = "ABC"; char *p = a; printf("%c", ++*p);
```
**Answer:** `B` (`a[0]` becomes `'B'`).

**Q11.**
```c
int arr[] = {10,20,30}; int *p = arr;
printf("%d", *++p + 1);
```
**Answer:** `21`.

**Q12.**
```c
unsigned u = 1; int i = -2;
printf("%d", (u + i) > 0);
```
**Answer:** **`1`** — `i` promoted to unsigned; sum is large unsigned.

**Q13.**
```c
int x = 0xFF; printf("%d", (char)x);
```
**Answer:** often **`-1`** if `char` signed (GCC x86 OA key).

**Q14.**
```c
union U { int i; char c[4]; };
union U u; u.i = 0x12345678;
printf("%02X", (unsigned char)u.c[0]);
```
**Answer:** little-endian **`78`**.

**Q15.**
```cpp
struct B { virtual void f(){ std::cout << "B"; } };
struct D : B { void f(){ std::cout << "D"; } };
int main(){ B *p = new D; p->f(); }
```
**Answer:** `D` (also note: non-virtual `~B` → UB on `delete p`).

**Q16.**
```cpp
int a = 1;
auto f = [a]() mutable { return ++a; };
std::cout << f() << f() << a;
```
**Answer:** `213` — lambda copy; outer `a` stays 1.

**Q17.**
```cpp
std::vector<int> v{1,2,3};
auto w = std::move(v);
std::cout << v.size() << w.size();
```
**Answer:** typically **`03`**.

**Q18.**
```cpp
struct T {
    T(){ std::cout << "C"; }
    T(const T&){ std::cout << "X"; }
    ~T(){ std::cout << "D"; }
};
T f(){ return T(); }
int main(){ T t = f(); }
```
**Answer:** C++17 elision → often **`CD`**.

**Q19.**
```c
int i = 5;
printf("%d %d %d", i, i<<1, i>>1 || i&1);
```
**Answer:** `5 10 1`.

**Q20.**
```c
const int x = 10;
int *p = (int*)&x; *p = 20; printf("%d", x);
```
**Answer:** **UB** — may print 10, 20, or fault (RO).

### MCQ pattern cheat
1. `a[i]` ↔ `i[a]` · 2. Param `sizeof` decays · 3. Padding math · 4. `static` persists/0 · 5. Endian union · 6. Unsigned mix · 7. Virtual = dynamic type · 8. `move` empties std containers · 9. Unsequenced mods = UB · 10. Signed `char` + `0xFF` → −1

---

## Oral add-ons (systems C / modern C++)
_Paraphrased interview themes from [YC C Interview series](https://yc-kuo.medium.com/contents-e8eedc905fa) + [notescs C++/OOP notes](https://github.com/notescs/notes/tree/main/C-CPP-OOPS-for-Interviews)._

| Topic | What to say |
|---|---|
| **Endianness** | Little: low byte @ low address (x86 default in OAs). Probe with `union` / byte cast — already in MCQ bank. |
| **Call by value** | Args are copies; pointers/refs update caller's object. Arrays decay to pointers when passed. |
| **Scope / lifetime** | Auto locals die at `}`; statics live for process; never return `&local`. |
| **Makefile (1-liner)** | Declares build graph: targets, deps, recipes; incremental rebuild via timestamps. |
| **Bitwise / `#pragma pack`** | Masks, shifts, struct packing for wire formats — know trailing pad returns if you `#pragma pack(1)`. |
| **Shallow vs deep copy** | Default copy shares pointers → double-free; deep allocates new buffer (Rule of Five). See [OOPs_LLD](OOPs_LLD.md). |
| **C++ cost vs C** | Virtual calls, exceptions, RTTI, abstraction have costs — most are **optional** if you design for zero-overhead (YC Series 04). Prefer RAII over manual `malloc` for safety. |
| **Lambdas vs `std::bind`** | Prefer lambdas (captures, inlining); abandon `std::bind` for new code (YC Series 02). |
| **Smart pointers** | Prefer `unique_ptr`; `shared_ptr` only for shared ownership; `weak_ptr` for cycles. |
| **Friend functions/classes** | `friend` grants a non-member function or whole external class access to private/protected members — a bridge between otherwise-unrelated classes; not mutual or inherited (friending B in A doesn't let A see B's privates, and B's subclasses don't inherit the friendship). |
| **Namespaces** | Scope identically-named identifiers to avoid collisions; nested namespaces chain with `::`; an unnamed namespace is the C++ analog of C's file-local `static`. A local variable shadows both global and namespaced same-name variables unless explicitly qualified. |

---

## Boss Sheet
<a id="boss-sheet"></a>

### 10 critical facts
1. Segments: TEXT | DATA | BSS | HEAP↑ | ↓STACK.  
2. Pointer arithmetic scales by `sizeof(*p)`; arrays decay (except `sizeof`/`&`).  
3. Match `malloc`/`free` and `new`/`delete` (`new[]`/`delete[]`); never mix.  
4. `volatile` = observable accesses (MMIO); **not** for threading.  
5. `static` local = persistent; file `static` = internal linkage; `extern` declares.  
6. Struct padding: align members; trailing pad; reorder before pack.  
7. vptr → vtable for virtual dispatch; virtual destructor for polymorphic delete.  
8. RAII + prefer `unique_ptr`; `shared_ptr` refcount; `weak_ptr` breaks cycles.  
9. Rule of Five (or Zero); `std::move` is a cast; moved-from stays valid.  
10. `std::atomic` for threads; `volatile` ≠ atomic ≠ synchronized.

### 3 pitfalls
- Dangling pointer (`free` / return `&local`).  
- Assuming no padding / wrong `sizeof`.  
- "`volatile` for thread flags" (fail).

### 5 drills
1. Draw memory layout + place 5 example symbols.  
2. Three struct `sizeof` puzzles cold.  
3. One-minute `volatile` vs `atomic`.  
4. Sketch vptr/vtable + why virtual dtor.  
5. Re-solve MCQs Q1–Q20 without looking (25 min).

---

## Resource Panel (library)
- [cppreference](https://en.cppreference.com/w/)
- [Effective Modern C++ resources (Meyers)](https://www.aristeia.com/Books/EMC++_Resources.html)
- [The Linux Programming Interface](https://man7.org/tlpi/)
- [Linux Device Drivers 3rd Ed](https://lwn.net/Kernel/LDD3/)
- [YC C++ / OS / Concurrency Roadmap (per-article)](YC_Cpp_OS_Concurrency_Roadmap.md)
- [YC Kuo — Contents (hub)](https://yc-kuo.medium.com/contents-e8eedc905fa)
- [C IQ 01 — Pointers & Endianness](https://yc-kuo.medium.com/c-interview-questions-01-pointer-c35df76f5252)
- [C++ Series 01 — OOP/Virtual](https://yc-kuo.medium.com/c-interview-01-oop-virtual-polymorphism-204d8d466087)
- [C++ Series 04 — Runtime cost vs C](https://yc-kuo.medium.com/c-series-04-runtime-cost-of-c-compared-to-c-26bd41214884)
- [notescs — C/C++/OOPS for Interviews](https://github.com/notescs/notes/tree/main/C-CPP-OOPS-for-Interviews)
- [STL Quick Reference (day-before)](DSA/STL/00_STL_Quick_Reference.md) · [Striver-TUF-Plus STL drills](https://github.com/adityanayak20/Striver-TUF-Plus/tree/main/STL)
- [OOPS Boss Sheet](https://drive.google.com/file/d/1s0HeZt05eck7cuwXxQZtDiZ_NEPfZwo6/view)
- [Bit/Math Cheatsheet](https://drive.google.com/file/d/1gPXenSrwfnme7NSrGBt4DnCWKBkza8-m/view)
- Systems Top-100 **Groups 1–2** (C/bitwise + Modern C++): [Interview Prep context §9](../../Interview_Prep_Resources_Context.md)
- Index: [00_INDEX.md](../00_INDEX.md)
- Related: [OOPs_LLD](OOPs_LLD.md) · [OS](OS.md) · [Concurrency](Concurrency_Multithreading.md) · [Systems Interview](Systems_Interview.md)
