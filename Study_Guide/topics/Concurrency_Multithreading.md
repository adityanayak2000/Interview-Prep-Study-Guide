# Concurrency & Multithreading
**FIRST-CLASS for Tier S** · Cross-links: [OS](OS.md) · [C++ Fundamentals](Cpp_Fundamentals.md) · [Systems Interview](Systems_Interview.md)

## Why it matters
MediaTek often asks **write Producer-Consumer**. Qualcomm / TI grill mutex vs semaphore, races, atomics. Storage / firmware tracks (Micron, WD, Infineon, Arm, Intel) probe threads + memory ordering awareness. Product companies (Commvault, etc.) ask thread-safe designs.

| Company | How concurrency shows up |
|---|---|
| [MediaTek](../companies/tier_S_semiconductor/MediaTek.md) | Bounded buffer / Producer-Consumer code |
| [Qualcomm](../companies/tier_S_semiconductor/Qualcomm.md) | Sync primitives in OS round |
| [Texas Instruments](../companies/tier_S_semiconductor/Texas_Instruments.md) | Mutex vs spinlock (embedded) |
| [NVIDIA](../companies/tier_S_semiconductor/NVIDIA.md) / [AMD](../companies/tier_S_semiconductor/AMD.md) | Parallelism, atomics, C++ memory model |

Day-before: [Boss Sheet](#boss-sheet) + redraw PC from blank.

---

## Concept summary

### Threads vs processes (quick)
Thread shares address space / FDs; process owns them. See [OS](OS.md) for PCB, fork/COW, cost of switches.

### Critical section
Need **mutual exclusion**, **progress**, **bounded waiting**. Race: `counter++` is load-add-store — not atomic.

### Primitives

| Tool | Meaning | Use when |
|---|---|---|
| **Mutex** | Ownership lock; only owner unlocks | Protect shared data |
| **Semaphore** | Counter; `wait`/`post` (P/V) | Resource counts, signaling |
| **Binary semaphore** | 0/1 — similar to mutex but **no ownership** | Prefer mutex for locking |
| **Spinlock** | Busy-wait | Short CS on multiprocessor; never hold while sleeping |
| **Futex-based lock** | Fast-path/slow-path hybrid | Uncontended: pure atomic bit-test-and-set, no kernel call; contended: falls back to a kernel wait/wake syscall (Linux `futex`) — cheapest of both worlds |
| **Condvar** | Wait for predicate; always with mutex | Producer-Consumer, barriers |
| **`std::atomic`** | Lock-free flags/counters | Simple shared state; not a substitute for complex CS |
| **`volatile`** | May change outside program (MMIO) | **Never** for thread sync |

### Condition variables (Mesa style — pthreads / C++)
Always:
```text
pthread_mutex_lock(&m);
while (!predicate)   // NOT if — spurious wakeups
  pthread_cond_wait(&cv, &m);  // atomically unlocks m, waits, re-locks
// critical work
pthread_mutex_unlock(&m);
```

### Deadlock
Four Coffman conditions: mutual exclusion, hold-and-wait, no preemption, circular wait.  
**Prevention:** lock ordering (always A then B). **Avoidance:** Banker's (see OS). **Detection:** wait-for graph.

### Priority inversion
Low-priority holds lock needed by high-priority; medium runs forever. Fix awareness: **priority inheritance** / ceiling. Common RTOS / Arm interview topic.

### Memory ordering (awareness level)
Writes can appear reordered without barriers. `std::atomic` with default `seq_cst` is safest for interviews; know that `volatile` does not order threads.

### Mutex vs Atomic vs Lock-free (CAS) — decision tree
Paraphrased from practical C++ concurrency guidance (see [YC C++ Series 05](https://yc-kuo.medium.com/c-series-05-mutex-atomic-lock-free-cas-de7f6d3b7997)):

1. Shared state? No → no sync.  
2. Multi-variable invariant? → **mutex** (default).  
3. Single variable with a ready `atomic` op? → **`std::atomic`**.  
4. Hot path *and* you invent a new RMW protocol? → **CAS loop** only after profiling + backoff; otherwise stick to mutex.  

Polling ≠ lock-free. Prefer correctness over clever atomics in most Tier S interviews.

### Mesa vs Hoare monitors
**Hoare:** signaler hands CPU to waiter immediately. **Mesa** (pthreads/C++): signaler finishes; waiter eventually runs and **must recheck** predicate → always `while`, not `if`. (YC OS Walkthrough 02.)

### Dining Philosophers (interview sketch)
N forks; grab left then right → circular wait. Fix with **total lock order** (or one philosopher grabs opposite-handed), leave one fork "out" via an admission-cap semaphore (N−1 seated at once), or a butler limiting concurrent diners. **Trap:** one big mutex around "grab both forks" is deadlock-free but serializes all eating — not the preferred fix. C++17 idiom: `std::scoped_lock(mutexes[left], mutexes[right])` locks both atomically regardless of acquisition order. See [Little Book of Semaphores](https://greenteapress.com/semaphores/LittleBookOfSemaphores.pdf). Oral sibling of OS FAQ Q16.

### Readers-Writers fairness — the starvation trap
The textbook "first-reader locks writers, last-reader unlocks" solution above is deadlock-free but **not fair**: a steady stream of arriving readers can starve a waiting writer indefinitely (liveness bug, not deadlock). No-starve fix: add a **turnstile** semaphore in front of the reader-entry path that a waiting writer can also lock — once a writer queues there, no *new* readers sneak in, guaranteeing the writer eventually gets in while already-admitted readers finish normally. (Paraphrased from Little Book of Semaphores.)

### Classic semaphore problems (beyond PC / RW / Dining)
Oral-only patterns worth recognizing by name — all from the Little Book of Semaphores:
- **Rendezvous** — two threads each have a first/second half of work; neither's second half may start until the other's first half is done. Naive "wait-then-signal on both sides" deadlocks; correct shape is **signal-then-wait** on both sides.
- **Multiplex** — mutex generalized to N concurrent holders; just initialize the semaphore to N, no extra bookkeeping.
- **Barrier / turnstile** — rendezvous generalized to N threads: counter+mutex, last arriver opens a gate; a **reusable** barrier needs *two* turnstiles (arrival phase + departure phase) or a fast thread can lap around and corrupt the next round's counter.
- **Cigarette Smokers** — an agent places two of three ingredients on a table; the smoker missing the third should grab both and smoke. Naive "each smoker waits on its two missing ingredients" deadlocks; fix needs intermediary "pusher" logic (boolean state + mutex) that only signals the correct smoker once the complementary ingredient is confirmed present.
- **Sleeping Barber** — bounded-queue producer-consumer with a twist: if the waiting room is full, the customer **balks and leaves** instead of blocking — needs a non-blocking capacity check, not a blocking wait.

### Common concurrency bug taxonomy (beyond deadlock)
Real-world bug studies (MySQL, Apache, Mozilla, OpenOffice) found ~97% of non-deadlock concurrency bugs fall into two buckets: **atomicity violations** (a sequence of accesses assumed indivisible but not actually protected as one unit — e.g. null-check then dereference with no lock spanning both) and **order violations** (code assumes event A always precedes event B with nothing enforcing it — fix with a condition variable/semaphore, not a bare assumption). (Paraphrased from OSTEP Ch32.)

### Embedded callout — FreeRTOS producer-consumer
RTOS uses mutex / counting semaphore APIs (`xSemaphoreTake`/`Give`) around a buffer; same empty/full + ownership ideas. Watch `volatile` for ISR flags separately from task sync. Optional deep dive: [FreeRTOS STM32 PC](https://yc-kuo.medium.com/hands-on-freertos-on-stm32-mcu-01-producer-consumer-problem-e3cc921e0660).

---

## Pattern drills

1. Bounded-buffer **Producer-Consumer** (mutex + empty/full semaphores **or** mutex + two condvars).  
2. **Readers-Writers** (shared vs exclusive; starvation variants).  
3. Race on `counter++` → fix with mutex or `atomic`.  
4. Two-lock deadlock → fix with global order.  
5. Odd/even printer with two threads + condvar.  
6. Thread-safe singleton (C++11 magic static or call_once).

---

## Code — Producer-Consumer (semaphores)

```c
/* mutex m; sem empty = N; sem full = 0; */
void* producer(void* arg) {
  for (;;) {
    item = produce();
    sem_wait(&empty);
    pthread_mutex_lock(&m);
    buf[in] = item; in = (in + 1) % N;
    pthread_mutex_unlock(&m);
    sem_post(&full);
  }
}
void* consumer(void* arg) {
  for (;;) {
    sem_wait(&full);
    pthread_mutex_lock(&m);
    item = buf[out]; out = (out + 1) % N;
    pthread_mutex_unlock(&m);
    sem_post(&empty);
    consume(item);
  }
}
```

## Code — Readers-Writers (writer-prefer sketch)

```c
/* mutex m; int readers=0; sem wrt=1; */
void reader_enter() {
  pthread_mutex_lock(&m);
  if (++readers == 1) sem_wait(&wrt);  // first reader blocks writers
  pthread_mutex_unlock(&m);
}
void reader_exit() {
  pthread_mutex_lock(&m);
  if (--readers == 0) sem_post(&wrt);
  pthread_mutex_unlock(&m);
}
void writer() {
  sem_wait(&wrt);
  /* write */
  sem_post(&wrt);
}
```
_(Say aloud: this can starve writers if readers keep arriving — the no-starve fix adds a turnstile in front of reader-entry that a waiting writer can also lock; see Concept summary above.)_

## Code — C++ atomic flag
```cpp
std::atomic<bool> ready{false};
// publisher
data = 42;
ready.store(true, std::memory_order_release);
// consumer
while (!ready.load(std::memory_order_acquire)) { /* spin or yield */ }
use(data);
```

---

## Practice bank
**Easy:** define race / CS / deadlock vs starvation; mutex vs binary semaphore  
**Medium:** implement PC; RW; odd/even threads; fix two-lock deadlock  
**Hard:** lock-free stack sketch; reusable barrier (two turnstiles); dining philosophers (resource hierarchy); cigarette smokers (pusher-thread fix); sleeping barber (balk-on-full)

**Write from blank (MediaTek ≤15 min):** redraw OS.md PC (`while` + two condvars) or POSIX-Threads folder **9**.

**Hands-on map — [POSIX-Threads](https://github.com/adityanayak20/POSIX-Threads):**
| Folder | Drill |
|---|---|
| 1–3 | create/join, multi-thread, struct args |
| 5 | detached vs joinable |
| 6–7 | shared counter + mutex (race→fix) |
| **8** | PC with mutex only (know limitations) |
| **9** | **PC = mutex + condition variables (canonical)** |
| 10 | counting semaphore (“farmer”) intuition |

---

## Boss Sheet
<a id="boss-sheet"></a>

**10 facts:** process vs thread; CS triad; mutex ownership; semaphore count; spinlock short CS; CV + `while`; 4 deadlock conditions; lock ordering; atomic ≠ volatile; priority inversion.  
**+2 facts:** readers-writers is starvation-prone without a turnstile fix; futex locks are fast-path (atomic, no kernel) until contended, then fall back to a kernel wait/wake.  
**3 pitfalls:** `volatile` for threads; `if` instead of `while` on CV; nested locks without order.  
**+1 pitfall:** one big mutex around "grab both forks" in dining philosophers — deadlock-free but kills concurrency.  
**5 drills:** draw PC; code PC blank; race on ++; two-lock deadlock; atomic publish/consume.  
**+1 drill:** name the two buckets that cover ~97% of non-deadlock concurrency bugs (atomicity violation, order violation) and give a one-line fix for each.

---

## Resource Panel (library — do not dump catalogs)
- [POSIX Threads notes](https://github.com/adityanayak20/POSIX-Threads) — folders **8–9** = PC practice
- [Little Book of Semaphores (PDF)](https://greenteapress.com/semaphores/LittleBookOfSemaphores.pdf)
- [OSTEP (Concurrency Ch 26–32)](https://pages.cs.wisc.edu/~remzi/OSTEP/)
- [YC C++ / OS / Concurrency Roadmap (MT + Series)](YC_Cpp_OS_Concurrency_Roadmap.md)
- [YC Kuo — Contents (hub)](https://yc-kuo.medium.com/contents-e8eedc905fa)
- [MT 01 Overview](https://yc-kuo.medium.com/hands-on-multithreading-with-c-01-overview-e29087ebeadb)
- [MT 03 Deadlock](https://yc-kuo.medium.com/hands-on-multithreading-with-c-03-deadlock-97c42333d8e1)
- [MT 04 Producer-Consumer](https://yc-kuo.medium.com/hands-on-multithreading-with-c-04-producer-consumer-problem-26abdddc485d)
- [C++ Series 03 — Mutex/Semaphore + LC](https://yc-kuo.medium.com/c-series-03-mutex-semaphore-with-leecode-0de966275919)
- [C++ Series 05 — Mutex/Atomic/CAS](https://yc-kuo.medium.com/c-series-05-mutex-atomic-lock-free-cas-de7f6d3b7997)
- [FreeRTOS STM32 PC (optional)](https://yc-kuo.medium.com/hands-on-freertos-on-stm32-mcu-01-producer-consumer-problem-e3cc921e0660)
- [OS Boss Sheet](https://drive.google.com/file/d/1YquLAtpYmeTLMpyUfb6qd2rVwnQpsz74/view)
- [OS MCQ Practice](https://drive.google.com/file/d/11fADR2f8lIkK3HLQnGZ7jBhjBFa5Dd2G/view)
- Top-100 **Group 3** (OS / paging / concurrency): see [Interview Prep context §9](../../Interview_Prep_Resources_Context.md)
- [00_INDEX — OS/Concurrency](../00_INDEX.md)
- Related: [OS](OS.md) · [Cpp](Cpp_Fundamentals.md) · [Systems Interview](Systems_Interview.md)
