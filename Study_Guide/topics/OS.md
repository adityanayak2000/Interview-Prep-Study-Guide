# Operating Systems
_M.E. CS interview core · Tier S semiconductor filter_

> 🚪 [Start](../START_HERE.md) · 🗺️ [Map](../README.md) · 🏢 [Companies](../companies/README.md) · 📚 [Library](../library/README.md) · 🔍 [Find](../FIND.md)

## Why it matters
Semiconductor / systems companies treat OS as a hard filter — whiteboard paging walks, scheduling numericals, and Producer-Consumer code. High weight at:

| Company | How OS shows up |
|---|---|
| [Qualcomm](../companies/tier_S_semiconductor/Qualcomm.md) | R2 deep-dive: page tables, TLB, scheduling; sync primitives |
| [Texas Instruments](../companies/tier_S_semiconductor/Texas_Instruments.md) | HirePro OS MCQs; mutex vs spinlock in embedded context |
| [MediaTek](../companies/tier_S_semiconductor/MediaTek.md) | Scheduling comparison tables + **write Producer-Consumer** |
| [AMD](../companies/tier_S_semiconductor/AMD.md) | Threads, affinity, memory ordering awareness |
| [Arm](../companies/tier_S_semiconductor/Arm.md) | TLB/ASID, RTOS priorities, priority inversion |

Also hammered at IBM / Cisco / Commvault (IPC, deadlock) and storage companies (disk/FS). If you can narrate **VA → TLB → page table → frame** and code a correct `pthread` bounded buffer, you clear most Tier-S OS rounds.

Day-before: read only the [Boss Sheet](#boss-sheet) footer.

---

## Concept summary

### 0. Kernel-entry vocabulary — interrupt vs exception vs trap
Control transfers into the kernel come in three flavors: **interrupt** (externally triggered — a device finishes I/O), and two internally-triggered exceptions — **trap** (deliberate, e.g. a syscall; resumes at the *next* instruction) and **fault** (recoverable, resumes at the *same* instruction once fixed, e.g. a page fault); an **abort** is unrecoverable. Naming conventions clash across texts — MIPS-style reserves "interrupt" for external events only, while x86-style lumps everything under "interrupt-driven."

**Footgun:** trap ≠ interrupt generically — trap is synchronous/intentional (syscall), interrupt is asynchronous/external; fault resumes the same instruction, trap resumes the next one. (Paraphrased from YC OS Walkthrough 01.)

### 1. Processes vs threads
**Process** — OS abstraction for a running program: private virtual address space, PCB, FDs, credentials. `fork()` + COW; `exec()` replaces image.

**Thread** — schedulable CPU entity *inside* a process. Shares TEXT/DATA/BSS/heap/FDs. Private: stack, registers, TLS, `errno`.

**Cost order:** coroutine switch ≪ thread switch < process switch (page tables / TLB).

| | Process | Thread |
|---|---|---|
| Address space | Private | Shared |
| Creation | Heavy (`fork`) | Light (`pthread_create` / `clone`) |
| Communication | IPC | Shared memory + sync |
| Crash blast radius | Isolated | Can corrupt whole process |

**States:** New → Ready → Running → Waiting → Terminated. Preemption: Running→Ready. I/O: Running→Waiting→Ready.

**Footguns:** `fork` in a multithreaded process duplicates **only the calling thread**. Zombie = exited but not `wait`ed. `volatile` does **not** fix `counter++` races.

```c
/* Shared vs COW — interview sketch */
int g = 0; /* DATA: threads share; fork COW-copies on write */

void *worker(void *arg) {
    (void)arg;
    g++; /* race without lock */
    return NULL;
}
```

---

### 2. CPU scheduling
**Formulas:** TAT = CT − AT · WT = TAT − BT · RT = first-run − AT.

| Algorithm | Preemptive? | Starvation? | Notes |
|---|---|---|---|
| **FCFS** | No | No | Convoy effect: short jobs behind long |
| **SJF** | No | Yes (long) | Best avg WT if BT known; impractical |
| **SRTF** | Yes | Yes | Preemptive SJF; more switches |
| **Priority** | Optional | Yes (low) | Fix with **aging** |
| **RR** | Yes | No | Quantum *q*: small → fair + overhead; large → ≈ FCFS |
| **MLFQ** | Yes | Mitigated | Demote CPU hogs; boost periodically |

Linux **CFS** ≠ classic MLFQ (fair share via `vruntime`) — always dispatches the runnable process with the lowest accumulated `vruntime`; time slice is recomputed dynamically (weight ÷ sum of runnable weights × target latency window, floored at a min granularity), not a fixed quantum; priority = "niceness" mapped to a weight table; kept in a red-black tree for O(log n) next-to-run lookup. RT: RMS (shorter period → higher prio) vs EDF.

**Proportional-share alternative (awareness):** Lottery scheduling hands out tickets proportional to desired CPU share and draws a random winner each round — converges probabilistically to fair shares with near-zero bookkeeping; Stride scheduling is its deterministic sibling (accumulate a "pass" value by `stride = const/tickets`, always run lowest pass) but loses lottery's trivial handling of jobs joining/leaving. (Paraphrased from OSTEP Ch9.)

**Numerical drill (know cold):**

| Process | AT | BT |
|---|---|---|
| P1 | 0 | 7 |
| P2 | 1 | 4 |
| P3 | 2 | 1 |
| P4 | 3 | 4 |

- **FCFS** avg WT = **6**; **SJF** avg WT = **5.25**.
- **RR q=2:** careful arrivals mid-quantum → avg WT ≈ **6.25**. Always state arrival/tie-break rules.

**Priority inversion:** H blocked on lock held by L while M runs forever. Fix: priority inheritance / ceiling (Arm / FreeRTOS favorite).

---

### 3. Paging, TLB, thrashing
**Paging** — fixed pages (e.g. 4 KiB); VPN + offset → PTE → PFN. Internal fragmentation (~½ page); **no** external fragmentation of frames.

**TLB** — caches VPN→PFN. Miss = page walk (≠ page fault). ASID/PCID avoids full flush on context switch.

**Page fault** — page not resident (or protection). Load from disk/swap, update PTE, retry instruction.

**Replacement:**
| Algo | Key fact |
|---|---|
| FIFO | **Belady's anomaly** possible |
| OPT | Offline lower bound |
| LRU | Approximate via clock / ref bits |
| Clock | Second-chance circular scan |

**Thrashing** — more time paging than computing; working set > allocated frames. Fix: reduce multiprogramming, swap out a process, more RAM, local replacement.

**VA walk (32-bit, 4K pages):** VA `0x0040A123` → offset `0x123`, VPN `0x0040A`. PTE frame `0x2B` → PA `0x2B123`.

```c
#define PAGE_SHIFT 12
uint32_t translate(uint32_t *pt, uint32_t va) {
    uint32_t vpn = va >> PAGE_SHIFT;
    uint32_t off = va & 0xFFF;
    if (!(pt[vpn] & 1)) return UINT32_MAX; /* fault: present bit */
    return ((pt[vpn] >> 12) << 12) | off;  /* simplified PTE */
}
```

**EAT intuition:** high TLB hit rate matters more than raw DRAM latency for many workloads.

---

### 4. Synchronization
| Need | Choose |
|---|---|
| Sleepable mutual exclusion + ownership | **Mutex** |
| Resource count / signaling | **Semaphore** |
| Tiny CS, IRQ / non-sleepable, MP | **Spinlock** |
| Wait on predicate | Mutex + **condvar** (`while`, not `if`) |
| Single-variable RMW | `std::atomic` |

**Never** spin on UP if holder can't run. Mesa semantics → always recheck condition.

---

### 5. Producer-Consumer (write from memory)

```c
/* Bounded buffer — MediaTek / systems interviews
 * cc -pthread pc.c -o pc
 */
#include <pthread.h>
#include <stdio.h>

#define BUF_N 8
#define N_ITEMS 20

static int buf[BUF_N], head, tail, count;
static pthread_mutex_t mu = PTHREAD_MUTEX_INITIALIZER;
static pthread_cond_t not_full  = PTHREAD_COND_INITIALIZER;
static pthread_cond_t not_empty = PTHREAD_COND_INITIALIZER;

void produce_item(int item) {
    pthread_mutex_lock(&mu);
    while (count == BUF_N)
        pthread_cond_wait(&not_full, &mu);
    buf[tail] = item;
    tail = (tail + 1) % BUF_N;
    count++;
    pthread_cond_signal(&not_empty);
    pthread_mutex_unlock(&mu);
}

int consume_item(void) {
    pthread_mutex_lock(&mu);
    while (count == 0)
        pthread_cond_wait(&not_empty, &mu);
    int item = buf[head];
    head = (head + 1) % BUF_N;
    count--;
    pthread_cond_signal(&not_full);
    pthread_mutex_unlock(&mu);
    return item;
}

void *producer(void *arg) {
    (void)arg;
    for (int i = 1; i <= N_ITEMS; i++) produce_item(i);
    return NULL;
}
void *consumer(void *arg) {
    (void)arg;
    for (int i = 1; i <= N_ITEMS; i++) (void)consume_item();
    return NULL;
}

int main(void) {
    pthread_t tp, tc;
    pthread_create(&tp, NULL, producer, NULL);
    pthread_create(&tc, NULL, consumer, NULL);
    pthread_join(tp, NULL);
    pthread_join(tc, NULL);
    return 0;
}
```

**Semaphore sketch:** `sem_wait(empty)` → lock → write → unlock → `sem_post(full)` (mirror for consume).

---

### 6. Deadlock + Banker's overview
**Coffman (all four required):**
1. Mutual exclusion  
2. Hold and wait  
3. No preemption  
4. Circular wait  

Break any one → prevention. Practical fix: **global lock ordering**.

**Avoidance — Banker's:** grant only if resulting state is **safe** (exists a finish order). Need = Max − Allocation. Safety: Work = Available; repeatedly find unfinished P with Need ≤ Work, then Work += Allocation.

Classic safe sequence example: `<P1, P3, P4, P0, P2>` for the standard 5-process / 3-resource snapshot (Available (3,3,2)). Rarely used in general-purpose OS (needs a-priori max claims) — still an OA staple.

**Detection & recovery:** let deadlock potentially happen; periodically scan a wait-for graph for cycles, then kill/rollback a process to break it — common in DB systems. **Ignoring (ostrich algorithm):** the pragmatic default in most general-purpose OSes — restart manually if truly frozen; rational when prevention/avoidance overhead outweighs the (rare) cost of an actual deadlock. (Paraphrased from YC OS Walkthrough 05 + LC Discuss Part 3.)

**Starvation** ≠ deadlock (progress possible but unfair). **Livelock** = states change, no useful progress — the tell vs. deadlock: livelocked processes are still consuming CPU / changing state, they just never converge to completion.

---

### 7. IPC (brief)
| Mechanism | Copy? | Best for |
|---|---|---|
| Pipe / FIFO | Kernel buffer | Byte streams (related / named) |
| **Shared memory** | No after setup | **Highest bandwidth** (still needs sync) |
| Message queue | Yes | Discrete messages |
| Socket | Yes | Local (`AF_UNIX`) or remote |
| Signal | Notification | Events only — async-signal-safe handlers |

Qualcomm-style design: camera→encoder at 4K60 → shmem ring + futex/sem, zero-copy pixels; Binder for control path only.

---

### 8. Disk scheduling (brief)
HDD seek dominates. Head@53, requests `{98,183,37,122,14,124,65,67}`:

| Algo | Idea | Typical total seek (this set) |
|---|---|---|
| FCFS | Queue order | ~640 |
| SSTF | Nearest (may starve) | ~236 |
| SCAN | Elevator to end, reverse | ~331 |
| C-SCAN | One direction + jump | higher, more uniform wait |
| LOOK | SCAN but only to last request | practical |

SSD: no mechanical seek — FTL/GC matter more; OAs still ask HDD algos. Know inode / hard link vs symlink / journaling one-liners.

---

## Most-asked patterns
1. Draw what threads share vs private; PCB vs TCB.  
2. Gantt + avg WT for FCFS / SJF / RR / Priority under time pressure.  
3. Page fault path vs TLB miss; Belady → which algo?  
4. Mutex vs spinlock vs semaphore decision.  
5. **Code** Producer-Consumer; why `while` not `if`.  
6. Four deadlock conditions + one Banker's safety sequence.  
7. Fastest IPC? Why sync still required?  
8. Priority inversion + inheritance.  
9. Thrashing / working set.  
10. SCAN vs SSTF numerical.

---

## Practice bank

| # | Prompt | Target |
|---|---|---|
| 1 | Address-space diagram: place globals, heap, per-thread stacks | whiteboard ≤3 min |
| 2 | SRTF on AT/BT table; state tie-break | numerical |
| 3 | RR q=2 with mid-quantum arrivals | OA trap |
| 4 | FIFO vs LRU vs OPT on `1,2,3,4,1,2,5,1,2,3,4,5` (3 frames) | 9 / 10 / 7 faults classic |
| 5 | Two-level page-table walk for a VA | Qualcomm style |
| 6 | Write PC from blank in ≤15 min; then 2P/2C mental stress | MediaTek |
| 7 | Banker's: Need table → safe? → grant/deny request | TI/QC MCQ |
| 8 | Design shmem IPC for ISP pipeline | systems design |
| 9 | Disk: SSTF vs LOOK from head 50 | numerical |
| 10 | Explain COW after `fork` through write fault | oral |

**Rapid-fire:** zombie vs orphan · `clone` flags · soft vs hard RT · false sharing · `SIGPIPE` · Mesa vs Hoare · futex fastpath.

---

## Interview FAQ
Compact oral answers (definition → why it matters → key points → trap). Sourced themes: OSTEP, YC Kuo OS Walkthrough, Little Book / concurrency links, LC Discuss Part-3 checklist.  
**Tier S tip:** semiconductor rounds grind **paging, scheduling numericals, sync/PC** hardest; Q31–50 still appear in OA/HR and storage roles — learn them cold, but do not skip Q21–26 for Qualcomm/TI.

### Operating System Basics (01–10)

**01. What is an operating system?**  
Resource manager + abstraction layer between hardware and apps: multiplexes CPU, memory, and I/O; enforces isolation; provides system-call APIs.  
*Trap:* Calling “just a GUI” an OS (kernel is the core).

**02. Main functions?**  
Process/thread management, CPU scheduling, memory management (VA/PA), FS & I/O, IPC, protection/security, accounting. Often also networking stacks.  
*Trap:* Listing only “file management.”

**03. Process vs thread?**  
Process = address space + resources (PCB). Thread = schedulable CPU unit sharing that space (own stack/regs/TLS). See Concept §1.  
*Trap:* Claiming threads have private heaps by default.

**04. Multiprogramming vs multitasking vs multiprocessing?**  
**Multiprogramming** — keep CPU busy by switching among jobs in memory (classic batch/degree of MP). **Multitasking** — interleaved/interactive time-sharing (preemptive fairness). **Multiprocessing** — ≥2 CPUs/cores execute truly in parallel.  
*Trap:* Using the three as synonyms.

**05. Context switch?**  
Save/restore registers (± FPU) and scheduler metadata so another thread/process runs. **Thread switch** cheaper than **process switch** (page tables/TLB). Cost: cache/TLB pollution + switch latency.  
→ Deeper performance angle in **Q14**.

**06. Monolithic kernel vs microkernel?**  
**Monolithic** — most services (FS, drivers, networking) in kernel mode → faster syscalls, larger TCB, one bug can panic. **Microkernel** — minimal kernel; services as user processes → message IPC overhead, better isolation/restart. Linux ≈ monolithic (+ modules); QNX/seL4 ≈ microkernel style.  
*Trap:* “Microkernel always safer *and* faster.”

**07. Process creation and termination?**  
Creation: `fork`/`clone` (COW) or spawn; parent may `exec` image; wait with `wait`/`waitpid`. Termination: exit(status) → zombie until reaped; orphan reparented (often init). Crash → abnormal termination + signals.  
*Trap:* Forgetting zombies = unfinished reaping.

**08. Preemptive vs non-preemptive scheduling?**  
**Preemptive** — OS can force deschedule (timer, higher prio). **Non-preemptive** — runs until block/exit/yield. Modern desktop/server mostly preemptive.  
→ Same topic as **Q13**.

**09. System calls vs normal function calls?**  
Syscall: user→kernel via trap/`syscall` instruction, privileged path, copies/validates args, returns with errno/status — much slower than a user-mode call. Examples: `read`, `mmap`, `clone`. libc wrappers hide the trap.  
*Trap:* Thinking `printf` itself is always a single syscall (stdio buffers).

**10. Kernel mode vs user mode?**  
CPU privilege rings: kernel mode can touch privileged registers/I/O/page tables; user mode faults on privileged ops. Dual-mode enables protection.  
*Trap:* Conflating “root user” with kernel mode (root is still user-mode processes with caps).

### Process Management (11–20)

**11. Process scheduling?**  
Scheduler picks a **ready** runnable entity; dispatcher context-switches. Long-term (admit), mid-term (swap), short-term (CPU) levels. Goals: throughput, latency, fairness, utilization, deadlines (RT).  
*Trap:* Ignoring I/O-bound vs CPU-bound mix.

**12. Scheduling algorithms?**  
FCFS, SJF/SRTF, Priority (+ aging), RR (quantum), MLFQ, lottery; Linux CFS (`vruntime`). RT: RMS/EDF. See Concept §2 table.  
*Trap:* Claiming SJF is always used in practice (needs BT oracle).

**13. Preemptive vs non-preemptive?**  
See **Q08**. Add: preemption enables interactivity and RT priority; causes more switches and must be safe wrt kernel critical sections. Non-preemptive simpler but convoy/poor response.

**14. Context switch performance impact?**  
Direct cost (save/restore) + indirect (cache/TLB cold). Excessive switching under tiny quantum or thrashing hurts throughput. Measuring: involuntary context switches (`/proc`, `perf`).  
See **Q05**.

**15. Synchronization with semaphores?**  
Semaphore = counter + wait/`P` + post/`V` queues. Binary ≈ lock without ownership; counting = resource slots. Classic PC: empty=N, full=0, mutex for buffer integrity. Prefer mutex for mutual exclusion of data; use sem for signaling/counts. Deep dive: [Concurrency](Concurrency_Multithreading.md) · [Little Book of Semaphores](https://greenteapress.com/semaphores/LittleBookOfSemaphores.pdf) · OSTEP Ch 31.

**16. Dining philosophers?**  
N philosophers, N forks; all grab left then right → circular wait deadlock. Fixes: **resource ordering** (lowest fork id first, or one philosopher grabs opposite-handed), admission cap (allow only N−1 seated at once via a counting semaphore, guaranteeing someone can always get both forks), or waiter/butler (limit concurrent eaters).  
*Trap:* wrapping "grab both forks" in one big mutex prevents deadlock but serializes all eating — kills the concurrency the problem is meant to preserve; prefer ordering or the admission-cap fix. Interview for deadlock literacy more than for tableware. → [Concurrency](Concurrency_Multithreading.md).

**17. Critical section?**  
Code touching shared state. Requirements: mutual exclusion, progress, bounded waiting. Protect with mutex/spinlock/atomics for simple cases. Never leave CS while holding spinlocks across sleep.  
*Trap:* Relying on `volatile` for CS.

**18. Readers–Writers?**  
Many concurrent readers **or** one writer. Classic first-reader locks writers (`wrt`); can starve writers — mention fair/writer-preference variants. → [Concurrency](Concurrency_Multithreading.md) · Little Book.

**19. Process communication using IPC?**  
Processes communicate via kernel-mediated channels or shared memory. Choose by bandwidth, bidirectional need, and whether parties are related. Control path (sockets/Binder) vs bulk data (shmem ring) split is a common systems design answer.

**20. IPC mechanisms?**  
Pipes/FIFOs, message queues, **shared memory** (+ explicit sync), sockets (`AF_UNIX` or TCP/UDP), signals, Android Binder. Shared memory = highest bandwidth after setup; still needs mutex/futex/sem. See Concept §7.

### Memory Management (21–30)

**21. Virtual memory?**  
Each process sees large contiguous VA; OS+MMU map via page tables to frames (or disk). Enables isolation, overcommit/swap, sparse mappings (`mmap`). OSTEP Virtualization piece.

**22. Paging advantages?**  
Fixed-size pages: simple allocation, no external fragmentation of frames, easy protection/COW/sharing, demand paging. Cost: page tables + TLB misses + internal fragmentation (~½ page).

**23. Page fault?**  
Access to not-present / protection-violating VA → trap → OS loads/allocates or sends SIGSEGV → retry or kill. **Minor** (already in RAM, fix PTE) vs **major** (disk). ≠ TLB miss. → Concept §3.

**24. Allocation / deallocation?**  
Physical frames: free lists/buddy. User heap: `malloc`/`free` (split/coalesce). Kernel: slab/buddy. On free page: clear PTE, add frame to free pool; may write dirty pages to swap.

**25. Thrashing & working set?**  
Thrashing: page-fault rate so high CPU works for the pager. Working set ≈ pages touched recently; if Σ WS ≫ RAM, thrash. Fix: reduce degree of MP, local replacement, more RAM. See Concept §3.

**26. Page replacement: LRU / FIFO / Optimal?**  
**OPT** = future-knowing lower bound. **FIFO** = queue (Belady’s anomaly). **LRU** = replace least recently used (clock approximates). Know fault counts on classic reference strings.  
*Trap:* Belady “always” — only FIFO (and some stackless) families.

**27. Page table purpose?**  
Maps VPN → PTE (frame/PFN + present/R/W/U/dirty/accessed/ASID…). Walked on TLB miss. Multi-level / hashed / inverted variants for sparse VA spaces. OSTEP Ch 18–20.

**28. Demand paging?**  
Bring page in only on fault → faster start, less I/O; accepts fault latency. Prepaging optional warm-up.

**29. Segmentation fault?**  
Hardware/OS fault for invalid/unprivileged access: NULL deref, wild pointer, stack overflow, writes to RO TEXT, exceeding `mmap`. Handler may dump core / kill with `SIGSEGV`. Not the same as “segmentation as memory model” (though related historically).

**30. Process swapping?**  
Move entire process (or large chunks) between RAM and backing store to free frames (mid-term scheduler). Distinct from **paging** individual pages; modern OSes emphasize paging more; “swap out” still discussed.

**Extra oral (LC Top-17 gaps):** Kernel vs shell (kernel = privileged core; shell = user UI parsing commands). **MMU** translates VA→PA with TLB assist. **fork()+COW** — share pages read-only until write. **Belady** / **Banker's** — Concept §3 §6. **Cache** — on-CPU SRAM levels; locality; unrelated to “page cache” naming — say both carefully. Paging vs **segmentation**: pages fixed size; segments logical variable size (external frag risk).

### File Systems (31–40)
_OA/services/storage depth — complete answers; Tier S still ranks these below paging/sync._

**31. What is a file system?**  
Organization of persistent data: namespace (dirs), metadata (inode/FCB), data blocks, allocation maps, consistency (journal/fsck). Components: user API (`open`/`read`), VFS, FS driver, block layer.

**32. FAT vs NTFS vs ext4?**  
**FAT** — simple table; limited permissions/journaling. **NTFS** — Windows: ACLs, journaling, compression/encrypt options. **ext4** — Linux: extents, journaling, large files, POSIX perms. Choose by OS & features, not “speed alone.”

**33. File allocation / deallocation?**  
Reserve blocks via free bitmap/freelist; update inode pointers/extents; on delete, remove dir entry, free blocks (lazy/delayed free possible). Journaling orders metadata/data for crash safety.

**34. FCB / inode?**  
Per-file metadata: owner, mode, timestamps, size, block map/extents, link count. Directory entry usually stores name → inode number. Multi hard links share one inode; delete when link count 0.

**35. File descriptors & FD table?**  
Per-process integer handle → kernel file object (offset, flags) → inode/socket. `0/1/2` stdin/out/err. `dup` shares description. Closing last FD may release resources.

**36. FAT?**  
File Allocation Table: linked list of clusters in a table; EOF marker. Simple, fragmentation-prone, limited scale — USB/legacy still common.

**37. Sequential vs direct vs indexed allocation?**  
**Sequential/contiguous** — fast sequential I/O, hard to grow. **Linked** — easy grow, poor random. **Indexed** (inode block lists/extents) — random OK, metadata overhead; Unix-like use multilevel indexes/extents.

**38. File buffering?**  
Cache disk blocks in page cache/buffer cache → fewer I/Os, better latency; risks: dirty data loss on power fail → `fsync`/barriers/journal. libc `stdio` adds another user buffer.

**39. Symbolic link?**  
Special file storing a path string; lookup redirects. Can dangle; relative vs absolute. Contrast **hard link** (same inode, can’t cross FS usually, no dirs typically).

**40. File permissions?**  
UNIX: `ugo` rwx + sticky/setuid/setgid; ACL extensions. Checks on open/path walk. Windows: ACLs. Principle of least privilege for installs/services.

**RAID levels (oral add-on):** RAID 0 stripes with **zero** redundancy (pure speed/capacity — a common trap is assuming "RAID" implies safety). RAID 1 mirrors (fault tolerance, doubles storage cost). RAID 4 stripes at block level with one dedicated parity disk (reconstruct a failed disk from parity + the rest). Storage-adjacent rounds (IBM/Cisco/Commvault) may ask this; skip for pure product SDE. (Paraphrased from YC OS Walkthrough 04.)

### Device Management (41–50)

**41. Device driver?**  
Kernel (or user-mode) module translating high-level I/O to device register ops / DMA / IRQs. Hides hardware quirks behind block/char/net interfaces.

**42. Device allocation / deallocation?**  
Exclusive devices may be locked to a process; shared via queues. Release on close/`release` callback; hotplug add/remove updates device tree.

**43. Device / disk scheduling?**  
For HDD: FCFS, SSTF, SCAN, C-SCAN, LOOK (Concept §8). For general devices: fair queues, priority (audio/RT). SSD: no seek — scheduling different (NCQ/parallel).

**44. Interrupt handling?**  
Device raises IRQ → CPU traps to ISR → acknowledge/clear → bottom-half/tasklet/workqueue for heavy work → wake waiters. Top-half must be short; disable carefully.

**45. Device control block (DCB)?**  
Kernel structure describing device: state, queues, buffers, driver pointers — analogous to PCB for devices (terminology varies by textbook/OS).

**46. Spooling?**  
Simultaneous Peripheral Operations On-Line: buffer jobs (print/disk) so CPU never waits on slow device; classic multiprogramming enabler (YC OS Walkthrough 01 theme).

**47. Device registers?**  
Memory-mapped (`volatile` MMIO) or port I/O control/status/data registers. Drivers read/write them to command hardware.

**48. Polling vs interrupt-driven I/O?**  
**Polling** — busy-loop status bit (simple, wastes CPU; OK for tiny waits). **Interrupt-driven** — sleep until IRQ (efficient). High rate may use polling/NAPI hybrids.

**49. Device queue?**  
Pending I/O requests waiting for the device/driver; scheduler or driver drains queue; used for fairness/batching and disk elevator.

**50. Device management overview?**  
OS owns naming, drivers, buffering, scheduling, interrupts/DMA, errors, and power. Goal: share slow hardware safely among many processes with good throughput/latency.

---

## Boss Sheet
<a id="boss-sheet"></a>

### 10 critical facts
1. Process = resource + address space; thread = schedulable unit sharing that space.  
2. Context switch: registers; process switch also page tables / TLB.  
3. TAT=CT−AT; WT=TAT−BT; FCFS convoy; SJF optimal avg WT; RR quantum tradeoff; aging fights priority starvation.  
4. VA → (TLB hit) or page walk → PA; TLB miss ≠ page fault.  
5. Thrashing = working set does not fit; throughput collapses.  
6. FIFO can Belady; LRU/OPT do not; clock ≈ LRU.  
7. Mutex = ownership; semaphore = counter; spinlock = busy-wait (short CS, MP).  
8. Deadlock needs all four Coffman conditions; Banker's grants only safe states (Need=Max−Alloc).  
9. Producer-Consumer: mutex + not_full/not_empty; **`while` + cond_wait**.  
10. Shared memory = fastest bulk IPC; still needs explicit sync.  
11. Trap (syscall) resumes *next* instruction; fault resumes *same* instruction; interrupt is external — don't conflate the three.  
12. Deadlock has four handling families: prevention, avoidance (Banker's), detection+recovery, and ignoring (ostrich) — most general OSes just ignore it.

### 3 pitfalls
- Treating mutex ≡ binary semaphore (ownership / who may `V`).  
- Forgetting Belady on FIFO; conflating TLB miss with page fault.  
- Using `if` around `cond_wait` (spurious wakeups / Mesa).  
- Locking "grab both forks" in one big mutex for dining philosophers — deadlock-free but serializes all eating.

### 5 oral drills
1. Draw paging + TLB path end-to-end.  
2. Compare RR vs SJF (metrics + when each wins).  
3. Walk Banker's safety on a fresh table.  
4. Code Producer-Consumer from memory.  
5. Thrashing + working-set + one fix.  
6. State the four deadlock-handling families and give a one-line example of each.

---

## Resource Panel (library)
_Interview Prep OS & Concurrency section + Systems Top-100 Group 3 — deep-link, do not paste PDFs._

- [📚 OS / Systems PDFs & MCQs hub](../library/OS_Systems_PDFs.md) — MCQ bank, cheatsheets, OSTEP in one place
- [OS Boss Sheet](https://drive.google.com/file/d/1YquLAtpYmeTLMpyUfb6qd2rVwnQpsz74/view)
- [OSTEP (free book)](https://pages.cs.wisc.edu/~remzi/OSTEP/) — prioritize Ch 4–8, 13–15, 18–22, 26–32, 36–42
- [Little Book of Semaphores (PDF)](https://greenteapress.com/semaphores/LittleBookOfSemaphores.pdf)
- [YC C++ / OS / Concurrency Roadmap (Walkthrough 01–05)](YC_Cpp_OS_Concurrency_Roadmap.md)
- [YC Kuo — Contents (hub)](https://yc-kuo.medium.com/contents-e8eedc905fa)
- [OS Walkthrough 01 — Scheduling](https://yc-kuo.medium.com/os-walkthrough-01-multi-threading-cpu-scheduling-3435ac7d7126)
- [OS Walkthrough 02 — Synchronization](https://yc-kuo.medium.com/os-walkthrough-02-synchronization-cb61326c0430)
- [OS Walkthrough 03 — Memory](https://yc-kuo.medium.com/os-walkthrough-03-memory-49b4e236beaf)
- [OS Walkthrough 04 — FS & I/O](https://yc-kuo.medium.com/os-walkthrough-04-file-management-i-o-ab7e22f8150a)
- [OS Walkthrough 05 — Deadlock](https://yc-kuo.medium.com/os-walkthrough-05-deadlock-f42be5c02cc3)
- [LC Discuss — Part 3 Top 17 OS Qs](https://leetcode.com/discuss/post/5873921/part-3-top-17-os-interview-questions-wit-4fiw/)
- [POSIX Threads notes](https://github.com/adityanayak20/POSIX-Threads)
- [OS CodeHelp Cheatsheet](https://drive.google.com/file/d/1cVm80CaUVny9MKHjzbQi2b3wcuTZSsUM/view)
- [OS Interview Questions PDF](https://drive.google.com/file/d/1hyoWnDiDXaxJJ8pvVbpiTJZIzshEJbf-/view)
- [OS MCQ Practice](https://drive.google.com/file/d/11fADR2f8lIkK3HLQnGZ7jBhjBFa5Dd2G/view)
- [Bedtime Stories on OS](https://drive.google.com/file/d/1BMtW2e2Lm-ngAhAssicyN4lFq5InLJ6j/view)
- [OS InterviewBit PDF](https://drive.google.com/file/d/1-2aR5Jq1YVAB8hrrsdFxTJqGExgop8Ms/view)
- [OS Bootcamp Notion](https://woozy-pluto-cb4.notion.site/Operating-Systems-IT-Bootcamp-2023)
- [Advanced OS Notes PDF](https://drive.google.com/file/d/1S7Ucn7G-s7XoYYLLjjDrx2Isq-UrIEtS/view)
- [exajobs/os-collection](https://github.com/exajobs/os-collection.git)
- Systems Top-100 + dependency graph: [Interview Prep context §9](../../Interview_Prep_Resources_Context.md)
- Index: [00_INDEX.md](../00_INDEX.md)
- Related: [Concurrency](Concurrency_Multithreading.md) · [C++ Fundamentals](Cpp_Fundamentals.md) · [Systems Interview](Systems_Interview.md)
