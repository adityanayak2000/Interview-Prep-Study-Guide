# Interview Prep Resources — Context File
_Extracted from: 🎯 Interview Prep Resources.docx | Saved: 2026-07-18_
_Purpose: Persistent context so I never need to re-read the docx again._

---

## WHAT THIS FILE CONTAINS
Full index of resources across: DSA, OOPs/LLD, OS, DBMS, CN, System Design, Git, CS Cheatsheets, Company-wise Qs, Systems/Embedded, ML/AI, GenAI, DevOps, Aptitude.

---

## 1. DSA

### Constraint → Algorithm Cheat Table (from the doc)
| Constraint | Implied Complexity | Pattern |
|---|---|---|
| n ≤ 20 | O(2^n / n!) | Backtracking / Bitmasking |
| n ≤ 100 | O(n³) | Simulation / DP |
| n ≤ 1,000 | O(n²) | DP / Pair Checks |
| n ≤ 10⁵ | O(n log n) | Sorting / Linear Scan |
| n ≤ 10⁶ | O(n) | One-pass / Prefix Sum |
| Sorted Input | — | Binary Search / Two Pointers |
| Many Queries | — | Prefix Sum / Segment Tree / Fenwick |
| Tree (n nodes) | — | DFS / BFS / Tree DP |
| Weighted Graph | — | Dijkstra / Shortest Path |
| Unweighted Shortest Path | — | BFS |
| Need Top K | — | Heap / Quickselect |
| Need Count/Frequency | — | HashMap |
| Need All Possibilities | — | Backtracking |
| Need Min/Max Over Choices | — | DP |

### Key AI-Assisted DSA Strategy
- Struggle first (20 min minimum)
- Analyze constraints before picking pattern
- Pattern mastery: 2 slow → 2 repetition → 2 under pressure

### DSA Patterns Map (pattern summaries are in the doc — full detail)
**Arrays & Strings:** Two Pointers, Sliding Window, Merge Intervals, Prefix Sums, Hashmaps, Sorting
**Binary Search:** Basic, Search on Answer, Boundary/Count, Mountain/Bitonic
**Trees:** Traversal, Construction, Path Sum, LCA, Validation
**DP:** Memoization, 1D DP, Subsequence DP, Knapsack, Interval DP, Counting Ways
**Linked Lists:** Fast/Slow, Dummy Node, In-Place Reversal, Recursive Tricks
**Stacks & Queues:** Monotonic Stack, Design, Expression Stack, Sliding Window Deque
**Heaps:** Kth Largest, Heap+Hashmap, Merge K Sorted, Design/Streams, Heaps in Graphs
**Graphs:** Connected Components, Shortest Path, Cycle Detection, DAG/Topological Sort, Bipartite Check

### Key PDF Resources
- Complete DSA Roadmap (98 Pages): https://drive.google.com/file/d/10e8Q1yVymwxWhz9LgcWxwrkpW9eMxRla/view
- 30 Coding Patterns: https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view
- DSA Revision Sheet Template: https://docs.google.com/spreadsheets/d/1_v-8mOxArQgedzcZxCqtdl7KhVVKfMwV_DQa3mBAn3g/

### Key GitHub Resources
- Awesome LeetCode Resources: https://github.com/ashishps1/awesome-leetcode-resources
- Algo Notes Gitbook: https://liuzhenglaichn.gitbook.io/algorithm
- Your STL Notes (practice .cpp): https://github.com/adityanayak20/Striver-TUF-Plus/tree/main/STL
- In-repo STL quick reference: Study_Guide/topics/DSA/STL/ (Quick Reference + Containers + Algorithms)
- notescs interview notes hub: https://github.com/notescs/notes

### Cheatsheet PDFs (in doc's "Interview Cheatsheet" section)
- Space Complexity: https://drive.google.com/file/d/1VN4YXK83x9hu6beUPhrlI6D5Ij0-kRht/view
- Time Complexity: https://docs.google.com/document/d/1Vh19VzdiAbD2x7Tpw0YOvisXcY-NhyJqmtmlIOTQMzg/edit
- Array: https://drive.google.com/file/d/1PGLEG1Kn5sg6dOq_4QPykBKdvy3Qf3Mj/view
- String: https://drive.google.com/file/d/1GgKKAJcFRJBfSHbsTO_H0UKUYXqefp-i/view
- Linked List: https://docs.google.com/document/d/1lDSq_JKCrY0L-j81UGmMI1nAqCU_cSJx/edit
- Stack: https://docs.google.com/document/d/1GtEmGU912cF_WGf2wzLl87gyJDJ43D_t/edit
- Queue: https://drive.google.com/file/d/19wuChBcx4puSFgryqi-GHqLiGm24vS8q/view
- Binary Tree: https://drive.google.com/file/d/1hHBgLeTgRiQsmy_3OrcvOXZSJogl2zdQ/view
- Heap: https://docs.google.com/document/d/1DU11jH301gG0C35SLmptIRIkz5ui0STQ/edit
- Graph: https://drive.google.com/file/d/1Oyu009O6X5wKw-ETC-GxsFDjHJTWDNXS/view
- Trie: https://drive.google.com/file/d/10SmQg-F4cQQPBTxPUDyxdgMF99Qijr44/view
- Bit/Math: https://drive.google.com/file/d/1gPXenSrwfnme7NSrGBt4DnCWKBkza8-m/view
- Recursion/Backtracking: https://drive.google.com/file/d/1zXVZNiAKTHX39mvugroPntfrrROV8GEx/view
- Intervals: https://drive.google.com/file/d/1t3lK0hN2b0pESWkGMMHpys5iJbFVKdEI/view
- Greedy: https://drive.google.com/file/d/16rArMG-reo4xZgZNcDRfIMRilrK8KPZY/view
- DP: https://drive.google.com/file/d/1fc0H-9Uhb-dJeIKBHsovWMlGWZ3gM3Fv/view

### Handwritten Notes (Striver Series PDFs - drive links in doc)
Striver 180, SDE Sheet, DSA Sheet Part 1&2, Recursion, Stacks & Queues, Trees (3 PDFs), Graphs (4 PDFs), DP (4 PDFs)

---

## 2. OOPs / LLD

### Core Focus
Abstraction, Encapsulation, Polymorphism, Inheritance, SOLID Principles, Creational/Structural/Behavioral Design Patterns

### 6-Step LLD Mental Model
1. Requirement Clarification
2. Identify Core Entities
3. Define Relationships (inheritance, composition, aggregation)
4. Class to Function Mapping
5. Model Core Interactions (sequence of method calls)
6. Discuss Principles & Patterns

### Key Resources
- OOPS Interview Questions PDF: https://drive.google.com/file/d/19E0KwbC_ufqGPl6-sgL8jMWASraCiQ0E/view
- Dive Into Design Patterns (Shvets): https://drive.google.com/file/d/1uu3Ye48X9h0YifMl56o2BbN5vkQdFiJk/view
- OOP Notes IT Bootcamp: https://drive.google.com/file/d/1WBf4vRUpJIORoqP8VH50RWdeTyRMUnrR/view
- Java Interview Series: https://drive.google.com/file/d/1mgPSPuxAHYfvfe0ha64so6p87kh0LwYt/view
- Spring Boot Series: https://drive.google.com/file/d/1K9Wo14cyiQLJ47x5MsIhTNKkdWC9qzbF/view
- awesome-low-level-design (GitHub): https://github.com/ashishps1/awesome-low-level-design
- LLD CrashCourse (Sunchit): https://github.com/Sunchit/SystemDesignLLDCrashCourse.git
- Design Patterns Video (Christopher Okhravi): https://www.youtube.com/playlist?list=PLrhzvIcii6GNjpARdnO4ueTUAVR9eMBpc
- OOPS Boss Sheet: https://drive.google.com/file/d/1s0HeZt05eck7cuwXxQZtDiZ_NEPfZwo6/view

### LLD Practice Problems
**Standard:** Tic Tac Toe, Chess, Parking Lot, Elevator, Inventory Mgmt, Car Rental, Vending Machine, File System, Logging, Splitwise, ATM, Snake & Food
**With Concurrency:** Movie Ticket Booking, LRU/LFU Cache, Pub-Sub (Kafka-style), Thread-safe Rate Limiter

---

## 3. Operating Systems

### Core Topics
1. Process & Threads (PCB, states, context switching)
2. Scheduling (FCFS, SJF, Priority, Round Robin)
3. Synchronization & IPC (Critical Section, Semaphores, Mutex, Pipes, Sockets, Shared Memory)
4. Deadlocks (4 conditions, prevention, Banker's Algorithm)
5. Memory Management (Paging, Segmentation, Virtual Memory, Thrashing, Page Replacement: FIFO/LRU)
6. I/O & Storage (File Systems, Disk Scheduling: FCFS/SSTF/SCAN)
7. Kernel Basics (Monolithic vs Microkernel, system calls, dual-mode)

### Key Resources
- Bedtime Stories on OS: https://drive.google.com/file/d/1BMtW2e2Lm-ngAhAssicyN4lFq5InLJ6j/view
- OS InterviewBit PDF: https://drive.google.com/file/d/1-2aR5Jq1YVAB8hrrsdFxTJqGExgop8Ms/view
- OS Bootcamp Notion: https://woozy-pluto-cb4.notion.site/Operating-Systems-IT-Bootcamp-2023
- OS MCQ Practice: https://drive.google.com/file/d/11fADR2f8lIkK3HLQnGZ7jBhjBFa5Dd2G/view
- OS CodeHelp Cheatsheet: https://drive.google.com/file/d/1cVm80CaUVny9MKHjzbQi2b3wcuTZSsUM/view
- OS Interview Questions: https://drive.google.com/file/d/1hyoWnDiDXaxJJ8pvVbpiTJZIzshEJbf-/view
- OS Boss Sheet: https://drive.google.com/file/d/1YquLAtpYmeTLMpyUfb6qd2rVwnQpsz74/view
- Threads Notes (Your GitHub): https://github.com/adityanayak20/POSIX-Threads
- OS GitHub Repo: https://github.com/exajobs/os-collection.git

---

## 4. DBMS

### Core Topics (15 areas)
DBMS vs RDBMS, Keys, Normalization (1NF-BCNF), Functional Dependencies, Transactions & ACID, Concurrency Control & Locking, Shared vs Exclusive Lock, Deadlocks, Indexing (clustered/non-clustered), B+ Trees, Joins, Views/Stored Procedures/Triggers, Query Optimization, Isolation Levels (dirty/phantom/non-repeatable read), SQL Constraints

### Most Common Interview Patterns
ACID explanation, Normalization problems, Indexing internals, Transaction isolation, Deadlock situations, Join-based reasoning

### Key Resources
- SQL Basic Notes: https://drive.google.com/file/d/1VxXZziTmA_4Tm4XLS9NYOGpTA8BYrtFn/view
- SQL Interview Series (Animated): https://drive.google.com/file/d/1Qrt3G4gUDyFU3A1IhvKFbrdx1xUhDRwR/view
- SQL Interview Guide: https://drive.google.com/file/d/17vulPDcuIkbbx9UZXgnqoMfceQmDtYnb/view
- DBMS Full Notes: https://drive.google.com/file/d/1KLm-chZD9hdOwIlFsKv6eemKzsbV80Wh/view
- SQL in 16 Pages: https://drive.google.com/file/d/1DXz5z2BtU_fTmdn0r1m8elilEKc1vHH4/view
- DBMS Q&A: https://drive.google.com/file/d/1wwBTS1POgOpo4IwTEwMWdPDycgBN7tY7/view
- SQL Top 100: https://drive.google.com/file/d/1Px6ez6Sn7jb1DOSWE8kwesANdhhyjRzj/view
- Leetcode SQL Solutions PDF: https://drive.google.com/file/d/1LZfJqnrAxvqI2lKTsnkYxP4lHgJp9Gc8/view
- LeetCode Top 50 SQL: https://leetcode.com/studyplan/top-sql-50/
- DBMS Boss Sheet: https://drive.google.com/file/d/1r1Yn5xhka9jpb75z8PO2SgD4g4F_Tcc_/view

---

## 5. Computer Networks

### Core Topics
1. OSI 7 layers + TCP/IP model
2. "What happens when you type google.com" (end-to-end)
3. TCP vs UDP (reliability vs speed)
4. TCP 3-Way Handshake
5. HTTP (methods, status codes, stateless nature)
6. HTTPS/TLS handshake
7. DNS lookup flow
8. Cookies vs Sessions vs JWT
9. Load Balancers (Round Robin, Least Connections, L4 vs L7)
10. Reverse Proxy vs Load Balancer
11. NAT

### Key Resources
- CN Quick Notes: https://drive.google.com/file/d/1OymHd6cW-KQ4L36DVCEeD2OUdknXQBwY/view
- Blue Team Networking: https://drive.google.com/file/d/12dJ0VPDdLkFtnkjHkMEBxcixqERr37IP/view
- CN GitHub Notes: https://github.com/notescs/notes/blob/main/Computer-Networks-for-Interviews/README.md
- CN Video Course: youtube playlist PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi
- TCP/UDP Deep Dive playlist: https://www.youtube.com/playlist?list=PLIFyRwBY_4bS-PQZoF0UySdG0sH9VA0bn
- CN Boss Sheet: https://drive.google.com/file/d/1maLFnmWgjgJyCd6cQ4CHIlVbLIMRMaAm/view

---

## 6. System Design (HLD + LLD)

### HLD Core Concepts
CAP Theorem, Consistency Models, Data Partitioning (Sharding), Docker, Kubernetes, Microservices

### Key Resources
- System Design Questions Ebook: https://drive.google.com/file/d/1RZGN4VZgFc5w8LRkhpoXfpmtfB_n9hzY/view
- DevOps/Cloud Engineer Interview: https://drive.google.com/file/d/1p4Gb06r5Y1bWX_Bp6mCg0ehbgXKFF74D/view
- Microservices Interview Qs: https://drive.google.com/file/d/1eK9SLit0HU8v7BauGEb1aBM6dhBeQkjm/view
- awesome-system-design-resources: github.com/ashishps1/awesome-system-design-resources
- SystemDesignInterviewPreparationSeries: github.com/Sunchit/SystemDesignInterviewPreparationSeries.git
- HLD Primer: https://systemdesignschool.io/primer
- Top 50 System Design Questions (Threads): threads.com/@techie_programmer
- HLD Boss Sheet: https://drive.google.com/file/d/1YClCcB5e1tq1dNNnXeDQUnibCjCLykYI/view
- LLD/Design Pattern Boss Sheet: https://drive.google.com/file/d/1vG8CqGV8kGYOqTbA812-mKHKyeP1jGAQ/view

---

## 7. Career / HR Preparation

### Resume & Behavioral
- Resume Audit Checklist: https://drive.google.com/file/d/1sWlKCDKVJ0g9PLWBz_dBTOSETPEB0MTO/view
- FAANG Ready Template: https://drive.google.com/file/d/1AF3-vDvHabiUZFNWVI_FxjEqxjkhZQNW/view
- HR/Behavioural Boss Sheet: https://drive.google.com/file/d/1jsOro7s9jwRc-TvANeAVNjmf8bErkMX5/view
- awesome-behavioral-interviews: github.com/ashishps1/awesome-behavioral-interviews
- Top 30 HR Questions for Freshers: https://drive.google.com/file/d/1bWFEAyMbFFaFrvXMJX2R7kkPA4LNeksR/view
- HR Interview Prep PDF: https://drive.google.com/file/d/1SYcsdthIkC_yioySe66yh5-vgz1_mwM3/view

### Interview Strategy (from doc's "Interview Tips" section)
**General Format:** Coding Round → 2 Technical Rounds (40–50 min each) → HR Round (30–45 min)
**Priority in technical rounds:** DSA > Core fundamentals (OOPs + DBMS for CS roles) > Internship/Projects
**Intro flow:** Background → CP achievements → Internship experience → Projects → Hobbies
**DSA approach:** Brute → Optimal Brute → Optimal (never jump straight to optimal even if known)
**If you don't know:** "I'm not able to recall, can we come back to this?" — never say "I don't know"
**LLD rounds:** Ask for requirements, state assumptions, clarify with interviewer, building the solution interactively

---

## 8. Company-Wise LeetCode Archives (legacy practice packs)

**LOCKED CORRECTION (v4):** These Drive folders are **company-tagged LeetCode / practice archives** from the Interview Prep doc (“Company Wise LC Qs”). They are **NOT** campus Online Assessment packs.

- **FORBIDDEN** in strategy guides: labeling them “Company OA folder” / “OA folder”.
- Optional use in Resource Panels: `[Name LC archive (legacy)](https://drive.google.com/drive/folders/FOLDER_ID)` — never required.
- Full alphabetical list lives in `🎯 Interview Prep Resources.md` §Company Wise LC — do not dump all folders into `Study_Guide/00_INDEX.md` live nav.

### 8a. Legacy screenshots (OA-ish, optional)

- **2023 OA Screenshots (root):** https://drive.google.com/drive/folders/1gwzOS1cYQEg59mUG_y3ZuIRj8tSGoN1e  
  Label as `legacy/screenshots` only. Not a substitute for researched company OA sections.

### 8b. Key LC archive folders (legacy — expand with §13)

Key companies relevant to M.E. CS (LC archive Drive folders, not OA):
- AMD: https://drive.google.com/drive/folders/1zBl9lO0GB9RXGFl-UP_5xlSF2cDH3sP4
- Amdocs: https://drive.google.com/drive/folders/1nIi91V8qBgTRyRdsvMHwKbHtK0rHmRbO
- Cisco: https://drive.google.com/drive/folders/18dsRPtaCh-yaNEbIkslxieGraeV-ekXs
- Commvault: https://drive.google.com/drive/folders/1YBKvsIgfBoTqtKZyQZwZJpNbGdZQThVh
- Flipkart: https://drive.google.com/drive/folders/1tA0-Lm9LgC5lu2j3HyrSzq-HI2rMwvGI
- IBM: https://drive.google.com/drive/folders/1f4oi1Va8PCuwV41N0uWF_xRoh-7uvKcQ
- Infosys: https://drive.google.com/drive/folders/1wv6jOaJNOIrlyeE6vrxfYuth7jg5MBwk
- Intel: https://drive.google.com/drive/folders/1TeHV9T-OWRHniXS9L9BT73UN04BKfbb_
- MathWorks: https://drive.google.com/drive/folders/1Pfq673YsY2UOBJd4qtMeP2dSNPS3AuMj
- Mastercard: https://drive.google.com/drive/folders/1z6dGcWWST4bvF2rD4S7-jWx1A7DvoK8G
- Meesho: https://drive.google.com/drive/folders/1Mvl0-UeYun-HzhxdLZTRWeb_0pU_1K-G
- Microsoft: https://drive.google.com/drive/folders/1Cq3COb0qfJq3rPvxfQqkjxOGXZAmoYeW
- PayPal: https://drive.google.com/drive/folders/1PskhlSn8-gQbKb4R4s1v1TGZDjZQ4dqW
- Qualcomm: https://drive.google.com/drive/folders/1UhFhWBPzqy7onkduX74I8k2TDmvSaA5Z
- Samsung: https://drive.google.com/drive/folders/1uH35q9eu7lp67bYGtUCQJTG6h0kWD4JF
- SAP: https://drive.google.com/drive/folders/19OeV9pSp5mQYis8AO3DRhFUW2fTIIBS_
- ServiceNow: https://drive.google.com/drive/folders/1ETx9ZJsO5EV5DEIOxuCl6vxEgeRrm-mX
- Visa: https://drive.google.com/drive/folders/1Y1ebUCg8TTy1UmAZhQmKww0syGZQlubW
- Walmart Labs: https://drive.google.com/drive/folders/1FkivLwgz-h0PO_tD_yo_Uo_Oi9LODquW
- Goldman Sachs: https://drive.google.com/drive/folders/1I92o5HDSfjOABW8b4ssCA5YoxGxCcAyU
- Google: https://drive.google.com/drive/folders/1rUkxD-dn7V6Oxy3CmmOYqhzGmB-xhCm3
- Amazon: https://drive.google.com/drive/folders/1O40viCxLcGgyeXDG0qSpqHlVoi05YaIt
- Meta: https://drive.google.com/drive/folders/1qpF82wSIRKT7QOrz9EZ-3HIpTKNaEFHz
- Apple: https://drive.google.com/drive/folders/1pNcJF5mtiD3bh9riILRuYv3sPHyz01Ql
- Databricks: https://drive.google.com/drive/folders/1cG94y_tzFeFistNoNkkdcvUV_xYPj1AY
- DE Shaw: https://drive.google.com/drive/folders/1jOPmLReAur38igktceGfl4qIRmfUST1l
- Nvidia: https://drive.google.com/drive/folders/14FEf44knSilEmS-oKSDjcJnBVAuDCy9X
- Graviton: https://drive.google.com/drive/folders/1Rm8glxj8QuOZFqjE7FYn94bzdTWPGW5t
- Morgan Stanley: https://drive.google.com/drive/folders/1Lqwd8sQaTLhUpMuHhEvSn9TzbP2BBs06
- Accenture: https://drive.google.com/drive/folders/1B1I_7A_qicWJYwUhP-I23W4SiMlHTtIm
- American Express: https://drive.google.com/drive/folders/1SHpoKGNRZllW1oiwFpEBBcnAmIPWEEy7

---

## 9. Systems / Embedded Programming (for Qualcomm, TI, AMD, Intel, Micron, ARM roles)

**Deep library home:** Full narrative, company systems profiles, and Top-100 question text live in `🎯 Interview Prep Resources.md` under **Systems Resources / Company-Wise Software Systems Interview Bible**. Also see that doc’s **Operating Systems (OS) & Concurrency** section for PDF/Notion links.

Strategy guides (`Study_Guide/topics/OS.md`, `Concurrency_Multithreading.md`, `Cpp_Fundamentals.md`, future `Systems_Interview.md`) must **deep-link** here — not copy entire catalogs.

### Topic Dependency Graph (5 Levels)
1. C & Modern C++14/17/20 (Pointers, RAII, Smart Pointers, Move Semantics, Templates)
2. Computer Architecture (Pipeline, Cache hierarchy, MESI Protocol)
3. OS Core & Concurrency (Virtual Memory, Paging, TLB, Mutexes, Spinlocks, Atomics)
4. Linux Kernel Basics (System calls, ISRs, Tasklets, Workqueues, MMIO, GDB/Valgrind/perf)
5. LLD & Performance (Lock-free data structures, Memory pools, SIMD)

### Company-Specific Systems Profiles
**Qualcomm/MediaTek:** Bare-metal C, RTOS (QuRT), ARM Architecture, Android Binder, Camera/Audio HAL. Process: OA (C/C++ & Logic) → Pointers/Bitwise Screen → 2 Coding + 1 OS/Kernel + 1 HM
**NVIDIA/AMD:** High-perf C++, Parallel Programming, SIMD, GPGPU, Kernel-mode drivers. Process: Phone Screen (C++ internals) → Virtual Onsite 4-5 rounds (Cache Coherence, Parallelism, C++17/20)
**Intel/ARM:** ISA, Micro-architecture, LLVM/GCC, SoC modeling. Process: Cache lines, Pipeline hazards, Assembly-to-C mapping
**Micron/TI:** Fixed-point arithmetic, DMA, FTL, Wear-leveling, I2C/SPI/UART. Process: Embedded C + Interrupts + Hardware-Software interfacing

### Top 100 Systems Interview Questions (full list in this doc's section 4, in 5 groups):
- Group 1: C/Bitwise & Memory Layout (20 Qs — malloc, volatile, struct padding, function pointers, circular buffer, memcpy overlap)
- Group 2: Modern C++ Internals (20 Qs — vtable, RAII, Move Semantics, CRTP, std::atomic, C++ Memory Model)
- Group 3: OS Architecture, Paging & Concurrency (20 Qs — Page Fault, TLB, Thrashing, Producer-Consumer, Deadlock, Priority Inversion, Futexes)
- Group 4: Linux Kernel & Driver Primitives (20 Qs — System calls, Top/Bottom Halves, Tasklets, mmap, COW, SLAB allocator, eBPF)
- Group 5: Low-Level System Design (20 Qs — Lock-free MPMC Queue, Memory Pool Allocator, LRU Cache, Logger, DMA, Bloom Filter, SIMD Matrix Multiply)

### Key Resources
- OSTEP (Free): https://pages.cs.wisc.edu/~remzi/OSTEP/
- The Linux Programming Interface: https://man7.org/tlpi/
- Linux Device Drivers 3rd Ed (Free): https://lwn.net/Kernel/LDD3/
- Agner Fog's Optimization Manuals: https://www.agner.org/optimize/
- Brendan Gregg Linux Perf: https://www.brendangregg.com/linuxperf.html
- C++ Reference: https://en.cppreference.com/w/
- Effective Modern C++ (Meyers): https://www.aristeia.com/Books/EMC++_Resources.html

### 5 Must-Do Systems Projects
1. Custom Memory Allocator (malloc/free/realloc with splitting & coalescing)
2. Multithreaded Web Server (epoll, 10k+ concurrent connections)
3. Userspace Threading Library (thread_create, yield, join using setjmp/longjmp)
4. Linux Kernel Module (character driver with encrypted pipe /dev/cryptopipe)
5. SIMD Image Processor (AVX or ARM NEON, Gaussian Blur)

---

## 10. Aptitude Resources (for companies with aptitude OA sections)

Key topic PDFs (all in drive):
- Geometry, Percentages, Averages, Ratio & Proportion, Partnership
- Alligation, Time & Work, Speed/Time/Distance, Profit & Loss, Simple & Compound Interest
- Number System, LCM & HCF, Number Series
- Formulas & Shortcuts for Quantitative Aptitude (1hnIxlQ-x9w_cvAGXCfaShoTSpMhvMGKJ)

---

## 11. Daily Study Schedule (from doc)
| Block | Duration | Focus |
|---|---|---|
| Morning/Deep Work | 2.5 hrs | New DSA pattern + 2 problems (no AI during attempt) |
| Mid-Day/Core CS | 1.5 hrs | OS/DBMS/CN theory + SQL practice / LLD walkthrough |
| Evening/Review | 1-2 hrs | Re-solve yesterday's problem, AI code review, weekend mock interview |

Current Status Tracker (from doc):
- DSA: In Progress (High priority)
- OOPs: Not Started (High priority)
- OS: Done (Medium priority)
- DBMS: Not Started (Medium priority)
- CN: Not Started (Low priority)
- System Design: Not Started (Medium priority)
- Multithreading & Concurrency: Not tracked separately in v1 — treat as High for Tier S companies (v2)

---

## 12. v2 Planned Tabs / Sections for Interview Prep Resources.docx
_Added: 2026-07-19 | PLAN ONLY — mark as TO ADD IN DOCX. Do not invent new Drive file IDs here._

**Role of this file vs Study Guide (v4):** This context + `🎯 Interview Prep Resources.md` are the **canonical resource library**. Strategy content lives under `Study_Guide/**`. Every topic/company **Resource Panel** deep-links here with **full `https://` URLs** (see §13). Do not re-list entire catalogs inside Study_Guide files. See `CONTRIBUTING.md` for PR / cheap-AI rules.

Legacy note: root `MASTER_STUDY_GUIDE.md` is a redirect; v1 under `Study_Guide/_archive/`. LC archives + original Interview Prep md → `Study_Guide/_legacy/`.


### Tab A — Company-Wise LC Archive Index *(legacy; TO ADD IN DOCX)*
- Purpose: optional index of §8 **LeetCode archives** (not OA) + pointer to `Study_Guide/companies/` for real process intel.
- Screenshots root only: [2023 OA Screenshots](https://drive.google.com/drive/folders/1gwzOS1cYQEg59mUG_y3ZuIRj8tSGoN1e)
- For each §8 company: Company | Full Drive folder URL | Notes (`LC archive`)
- *(TO ADD IN DOCX: curated “last used / year” column if known)*

### Tab B — Multithreading & Concurrency *(TO ADD IN DOCX)*
- Purpose: first-class resource list (v2 Master Guide Topic 2I / Concurrency Resource Panel points here).
- Seed links already in this context (expand when wiring Master Guide):
  - Threads notes: https://github.com/adityanayak20/POSIX-Threads
  - OSTEP: https://pages.cs.wisc.edu/~remzi/OSTEP/
  - OS Boss Sheet: https://drive.google.com/file/d/1YquLAtpYmeTLMpyUfb6qd2rVwnQpsz74/view
  - Systems Top 100 Group 3 (OS Architecture, Paging & Concurrency) — listed in §9
- *(TO ADD IN DOCX: dedicated cheatsheet PDF / MCQ set if you create one later — leave placeholder, no fake ID)*

### Tab C — Semiconductor C/C++ MCQ Bank *(TO ADD IN DOCX)*
- Purpose: code-output prediction style questions for Qualcomm / TI / MediaTek / Arm / Micron / WD.
- Seed: Systems Top 100 Groups 1–2 in §9; cppreference https://en.cppreference.com/w/
- *(TO ADD IN DOCX: consolidated MCQ PDF / Notion page when available — placeholder only)*

### Tab D — Week-by-week tracker *(TO ADD IN DOCX — optional)*
- Purpose: spreadsheet or Notion aligned to Master Guide 4-week / 12-week roadmaps.
- Seed: DSA Revision Sheet Template already linked in §1: https://docs.google.com/spreadsheets/d/1_v-8mOxArQgedzcZxCqtdl7KhVVKfMwV_DQa3mBAn3g/
- *(TO ADD IN DOCX: concurrency + company-mock columns)*

---

## 13. Link Expansion Helper (for Master Guide implementers)

Body links in this file should already be full `https://` URLs. If you still see shorthand elsewhere (legacy extracts), convert:

| Shorthand (legacy only) | Expand to |
|---|---|
| `drive/FILE_ID` | `https://drive.google.com/file/d/FILE_ID/view` |
| LC archive folder `drive/FOLDER_ID` in §8 | `https://drive.google.com/drive/folders/FOLDER_ID` — label **LC archive (legacy)**, never “OA folder” |
| Bare `github.com/...` | `https://github.com/...` |
| YouTube `playlist?list=ID` | `https://www.youtube.com/playlist?list=ID` |

**Never** paste bare `drive/XXXX` into `Study_Guide/**` or any strategy markdown. Always expand.  
**Never** call §8 folders “OA folders.”

### Quick full-URL examples (Boss Sheets + library)
- OS Boss Sheet: https://drive.google.com/file/d/1YquLAtpYmeTLMpyUfb6qd2rVwnQpsz74/view
- DBMS Boss Sheet: https://drive.google.com/file/d/1r1Yn5xhka9jpb75z8PO2SgD4g4F_Tcc_/view
- CN Boss Sheet: https://drive.google.com/file/d/1maLFnmWgjgJyCd6cQ4CHIlVbLIMRMaAm/view
- OOPS Boss Sheet: https://drive.google.com/file/d/1s0HeZt05eck7cuwXxQZtDiZ_NEPfZwo6/view
- HLD Boss Sheet: https://drive.google.com/file/d/1YClCcB5e1tq1dNNnXeDQUnibCjCLykYI/view
- Linked List cheatsheet: https://docs.google.com/document/d/1lDSq_JKCrY0L-j81UGmMI1nAqCU_cSJx/edit
- DP cheatsheet: https://drive.google.com/file/d/1fc0H-9Uhb-dJeIKBHsovWMlGWZ3gM3Fv/view
- Graph cheatsheet: https://drive.google.com/file/d/1Oyu009O6X5wKw-ETC-GxsFDjHJTWDNXS/view
- OSTEP: https://pages.cs.wisc.edu/~remzi/OSTEP/
- POSIX Threads notes: https://github.com/adityanayak20/POSIX-Threads
- Qualcomm LC archive (legacy): https://drive.google.com/drive/folders/1UhFhWBPzqy7onkduX74I8k2TDmvSaA5Z
- Flipkart LC archive (legacy): https://drive.google.com/drive/folders/1tA0-Lm9LgC5lu2j3HyrSzq-HI2rMwvGI
- Visa LC archive (legacy): https://drive.google.com/drive/folders/1Y1ebUCg8TTy1UmAZhQmKww0syGZQlubW
- 2023 OA Screenshots (legacy): https://drive.google.com/drive/folders/1gwzOS1cYQEg59mUG_y3ZuIRj8tSGoN1e

Implementers should use full URLs in Resource Panels (5–15 curated links per panel, not full dumps).
