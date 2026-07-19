# Systems Interview — Spine
**Tier S semiconductor / firmware / systems software track**

This file is a **navigation spine**, not a textbook. Full Top-100 question text lives in `🎯 Interview Prep Resources.md` → **Systems Resources / Top 100 System Interview Questions**. Strategy depth lives in the linked topic files.

Cross-links: [OS](OS.md) · [Concurrency](Concurrency_Multithreading.md) · [C++ Fundamentals](Cpp_Fundamentals.md) · [Semiconductor archetype](../archetypes/Semiconductor_Systems.md)

---

## Levels 1–5 dependency graph

Study **bottom-up**. Skipping Level 1–2 breaks Qualcomm/TI/Arm OAs.

| Level | Focus | Primary strategy file |
|---|---|---|
| **1** | C & Modern C++14/17/20 — pointers, RAII, smart pointers, move, vtable | [Cpp_Fundamentals](Cpp_Fundamentals.md) |
| **2** | Computer architecture (software view) — cache, pipeline, MESI awareness | Interview Prep Systems bible + company files |
| **3** | OS core & concurrency — VM, paging, TLB, mutex/sem/atomics | [OS](OS.md) · [Concurrency](Concurrency_Multithreading.md) |
| **4** | Linux kernel basics — syscalls, ISR top/bottom half, MMIO, tools | Library: TLPI, LDD3 (see Resource Panel) |
| **5** | Low-level design & performance — pools, lock-free sketches, SIMD awareness | Interview Prep Group 5 + projects list |

```text
L1 C/C++ ──► L2 Arch ──► L3 OS+Conc ──► L4 Kernel ──► L5 LLD/Perf
```

---

## Top-100 checklist (Groups 1–5)

_Do not paste full answers here. Tick groups while reading the library + drilling topics._

### Group 1 — C / Bitwise / Memory layout → [Cpp](Cpp_Fundamentals.md)
Memory layout · memcpy overlap · bit count · string literal vs array · endian · `volatile` · offsetof · malloc internals · aligned alloc · FAM · function pointers · double-free · bit swap · `static` contexts · padding/packing · circular buffer · MMIO · inline vs macro · dangling · LL reverse  

### Group 2 — Modern C++ internals → [Cpp](Cpp_Fundamentals.md)
vtable · RAII · move · unique/shared · Rule of Five · vector growth · templates/SFINAE · CRTP · constexpr · atomic vs volatile · memory model · lambdas · casts · …

### Group 3 — OS / paging / concurrency → [OS](OS.md) · [Concurrency](Concurrency_Multithreading.md)
Page fault · TLB · thrashing · Producer-Consumer · deadlock · priority inversion · futexes · scheduling · …

### Group 4 — Linux kernel / drivers → library (TLPI / LDD3)
Syscalls · top/bottom halves · tasklets · mmap · COW · SLAB · eBPF awareness · …

### Group 5 — Low-level system design → library + projects
Lock-free MPMC sketch · memory pool · LRU · logger · DMA · Bloom · SIMD multiply · …

**Full wording:** [Interview Prep Resources — Top 100](../../🎯%20Interview%20Prep%20Resources.md) §Systems · summary in [context §9](../../Interview_Prep_Resources_Context.md)

---

## Company pointers (Tier S)

| Company | Emphasize |
|---|---|
| [Qualcomm](../companies/tier_S_semiconductor/Qualcomm.md) | L1+L3; LL coding; OS deep dive |
| [Texas Instruments](../companies/tier_S_semiconductor/Texas_Instruments.md) | L1 embedded C; DBMS crossover |
| [MediaTek](../companies/tier_S_semiconductor/MediaTek.md) | L3 Producer-Consumer; LL/stack |
| [AMD](../companies/tier_S_semiconductor/AMD.md) / [NVIDIA](../companies/tier_S_semiconductor/NVIDIA.md) | L1–L2 C++ + parallelism |
| [Arm](../companies/tier_S_semiconductor/Arm.md) | Arch + RTOS priority |
| [Micron](../companies/tier_S_semiconductor/Micron.md) / [WD](../companies/tier_S_semiconductor/Western_Digital_SanDisk.md) | Bits + OS + firmware vocab |

---

## 5 must-do systems projects (library)
1. Custom malloc/free (split/coalesce)  
2. Multithreaded web server (epoll)  
3. Userspace threads (setjmp/longjmp)  
4. Character driver module  
5. SIMD image blur  

Details: Interview Prep Systems section + [context §9](../../Interview_Prep_Resources_Context.md).

---

## Resource Panel
- [OSTEP](https://pages.cs.wisc.edu/~remzi/OSTEP/)
- [cppreference](https://en.cppreference.com/w/)
- [TLPI](https://man7.org/tlpi/)
- [LDD3](https://lwn.net/Kernel/LDD3/)
- [Agner Fog](https://www.agner.org/optimize/)
- [Brendan Gregg Linux Perf](https://www.brendangregg.com/linuxperf.html)
- [POSIX Threads](https://github.com/adityanayak20/POSIX-Threads)
- [OS Boss Sheet](https://drive.google.com/file/d/1YquLAtpYmeTLMpyUfb6qd2rVwnQpsz74/view)
- [00_INDEX](../00_INDEX.md) · [Semiconductor archetype](../archetypes/Semiconductor_Systems.md)
