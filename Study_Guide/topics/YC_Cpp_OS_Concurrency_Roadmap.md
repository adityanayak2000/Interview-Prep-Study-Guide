# YC C++ / OS / Concurrency Roadmap

Curated deep-links from [Yu-Cheng (Morton) Kuo — Contents](https://yc-kuo.medium.com/contents-e8eedc905fa) (**§1 CS → 1–1 C/C++** and **1–4 Operating Systems**).  
Use alongside in-repo topics; this page is a **link map**, not a paste of Medium bodies.

**Related strategy files:** [Cpp_Fundamentals](Cpp_Fundamentals.md) · [Concurrency_Multithreading](Concurrency_Multithreading.md) · [OS](OS.md) · [Computer_Networks](Computer_Networks.md) · [OOPs_LLD](OOPs_LLD.md)

---

## How to use (interview tracks)

| Track | Start here | Then |
|---|---|---|
| Tier S / systems oral | C IQ 01–03 → OS Walkthrough 01–05 → MT 01–05 | C++ Series 01, 03, 05 |
| Product SDE concurrency | MT 01–05 + C++ Series 03 / 05 | Little Book / OSTEP (via Concurrency Resource Panel) |
| Optional advanced | Chromium 01, CUDA 01, C++ Series 06 PGO | Only if role needs them — skip for most campus FAQs |

---

## 1–1 C/C++ — Chromium / CUDA / OOP / Multithreading / Concurrency / IQ / TCP

### Optional / advanced
- [Chromium 01: A Roadmap for Learning Chromium](https://yc-kuo.medium.com/chromium-01-a-roadmap-for-learning-chromium-b1ffa6a1df7b)
- [C++ Series 06 \| PGO (Profile-Guided Optimization)](https://yc-kuo.medium.com/c-series-06-pgo-profile-guided-optimization-8a978bd6881f)
- [CUDA 01 — Streams & Events Walkthrough](https://yc-kuo.medium.com/cuda-01-streams-events-walkthrough-5ff0a32fc1ea)

### C++ Series (core)
- [C++ Series 05 \| Mutex / Atomic / Lock-Free (CAS)](https://yc-kuo.medium.com/c-series-05-mutex-atomic-lock-free-cas-de7f6d3b7997)
- [C++ Series 04 \| Runtime Cost of C++ Compared to C](https://yc-kuo.medium.com/c-series-04-runtime-cost-of-c-compared-to-c-26bd41214884)
- [C++ Series 03 \| Mutex & Semaphore with LeetCode](https://yc-kuo.medium.com/c-series-03-mutex-semaphore-with-leecode-0de966275919)
- [C++ Series 02 \| Lambda Evolution (C++11→17; prefer lambdas over `std::bind`)](https://yc-kuo.medium.com/c-02-lambda-evolution-from-c-11-to-c-20-and-why-you-should-abandon-std-bind-2896cb80f7e5)
- [C++ Series 01 \| OOP / Virtual / Polymorphism](https://yc-kuo.medium.com/c-interview-01-oop-virtual-polymorphism-204d8d466087)

### Hands-On Multithreading with C++
Practice repo (optional): [yu-cheng-kuo-28/multithreading-cpp](https://github.com/yu-cheng-kuo-28/multithreading-cpp)

- [MT 05 — Readers-Writers Problem](https://yc-kuo.medium.com/hands-on-multithreading-with-c-05-readers-writers-problem-348a035c268e)
- [MT 04 — Producer-Consumer Problem](https://yc-kuo.medium.com/hands-on-multithreading-with-c-04-producer-consumer-problem-26abdddc485d)
- [MT 03 — Deadlock](https://yc-kuo.medium.com/hands-on-multithreading-with-c-03-deadlock-97c42333d8e1)
- [MT 02 — Synchronization](https://yc-kuo.medium.com/hands-on-multithreading-with-c-02-synchronization-534ba1fb31e3)
- [MT 01 — Overview](https://yc-kuo.medium.com/hands-on-multithreading-with-c-01-overview-e29087ebeadb)

### Sockets
- [Hands-On TCP Sockets with C++ & Vim on Ubuntu](https://yc-kuo.medium.com/hands-on-tcp-sockets-with-c-vim-on-ubuntu-0bee398abb94)

### C Interview Questions
- [C IQ 03 — Bitwise Operations / Sizes of Structs / Volatile](https://yc-kuo.medium.com/c-interview-questions-03-bitwise-operation-size-of-struct-volatile-cfc83b39fde7)
- [C IQ 02 — Makefile, Scope and Lifetime, Call by Value, & Data Types](https://yc-kuo.medium.com/c-interview-questions-02-makefile-scope-and-lifetime-call-by-value-data-type-f79ccea0af74)
- [C IQ 01 — Pointers & Endianness](https://yc-kuo.medium.com/c-interview-questions-01-pointer-c35df76f5252)

---

## 1–4 Operating Systems (YC Walkthrough)

- [OS Walkthrough 05 — Deadlock](https://yc-kuo.medium.com/os-walkthrough-05-deadlock-f42be5c02cc3)
- [OS Walkthrough 04 — File Management & I/O](https://yc-kuo.medium.com/os-walkthrough-04-file-management-i-o-ab7e22f8150a)
- [OS Walkthrough 03 — Memory Management](https://yc-kuo.medium.com/os-walkthrough-03-memory-49b4e236beaf)
- [OS Walkthrough 02 — Synchronization](https://yc-kuo.medium.com/os-walkthrough-02-synchronization-cb61326c0430)
- [OS Walkthrough 01 — Multi-threading & CPU Scheduling](https://yc-kuo.medium.com/os-walkthrough-01-multi-threading-cpu-scheduling-3435ac7d7126)

---

## Map → Study Guide topics

| YC cluster | Open in-repo |
|---|---|
| C IQ + Series 01 / 04 | [Cpp_Fundamentals](Cpp_Fundamentals.md) · [OOPs_LLD](OOPs_LLD.md) |
| MT series + Series 03 / 05 | [Concurrency_Multithreading](Concurrency_Multithreading.md) |
| OS Walkthrough | [OS](OS.md) |
| TCP sockets | [Computer_Networks](Computer_Networks.md) |
| Contents hub (all sections) | [YC Contents](https://yc-kuo.medium.com/contents-e8eedc905fa) |

---

## Resource Panel

- [YC Contents (full index)](https://yc-kuo.medium.com/contents-e8eedc905fa)
- [Little Book of Semaphores (PDF)](https://greenteapress.com/semaphores/LittleBookOfSemaphores.pdf)
- [OSTEP](https://pages.cs.wisc.edu/~remzi/OSTEP/)
- [POSIX-Threads practice](https://github.com/adityanayak20/POSIX-Threads)
- Index: [00_INDEX.md](../00_INDEX.md)
