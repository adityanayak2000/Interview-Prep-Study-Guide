# Commvault (SDE)
**Role(s):** Software Development Engineer (SDE, C++/Java); SDE Intern → performance-based FTE conversion; SDET (Python / JavaScript — separate track)
**Tier:** P
**Status:** done-v3

## Process Overview
Commvault India early-career **SDE** hiring is **campus-heavy** (single-college, pool campus, internship drives) with occasional **off-campus** screening via hiring agency / careers portal. The signature gate is a **multi-hour machine-coding / LLD round** after OA — not a LeetCode-only loop.

| Channel | Typical funnel |
|---|---|
| On-campus (common) | Language lock (C++ or Java) → OA → optional short coding screen → **5–8 hr machine coding** (mentor checkpoints) → 1–2 technical → HR |
| Pool campus | Same shape; higher cohort sizes and steeper cutoffs |
| Off-campus (rare; thin reports) | DEV vs TEST choice → OA → machine coding → technical(s); HR sometimes skipped |

**M.E./M.Tech CS:** Public write-ups mostly cite **B.Tech CS/IT** eligibility (often CGPA **7.5–8+**). No India reports isolate M.E./M.Tech — treat PG as **same technical loop** when eligible; confirm CGPA/branch rules on each drive invite. Off-campus PG-specific data is **insufficient**.

> Separate track: **SDET** (Python/JS OA + test-oriented interviews) — not covered below.

## Online Assessment (OA)
Format **varies by drive**; treat the invite as binding. Do not assume one fixed question set.

- **Platform (sourced):** College campus portal; **geeekd.com** (reported); off-campus 2020 via hiring agency — platform not named
- **Duration:** ~60–120 minutes most common (some drives split timed sections)
- **Language lock:** Choose **C++ or Java** for SDE **before** OA; used in OA + later rounds (change usually disallowed)
- **Sections & format (reported variants):**
  - **Variant A:** 15–20 language MCQs (25–45 min) + **2–3** DSA coding problems (40–60 min)
  - **Variant B:** Timed split — e.g. DSA 40 min (3 problems) + MCQ 30 min (17 questions on OOP/OS/DBMS/core CS)
  - **Variant C (older off-campus):** **6** coding problems in **2 hours** (DP, BST, backtracking)
  - **Variant D (some campuses):** Aptitude + language MCQs, then a **separate** 1-hour coding screen (4 problems) before the long round
- **Negative marking:** Not consistently reported
- **Topics tested:** DP, graphs, strings/arrays, backtracking, BST; language MCQs on **OOP**, pointers, inheritance, output prediction; core CS (OS, DBMS) in MCQ sections
- **Difficulty:** Medium → Hard coding; strong MCQ accuracy often matters for cutoff
- **Shortlist bar (examples only):** solving **2/3** coding problems + solid MCQs; cohort-dependent

## Interview Rounds
1. **OA** — screening (see above)
2. **Optional coding screen (~1 hr)** — 4–5 DSA problems (not on every drive)
3. **Machine coding / LLD (5–8 hrs)** — **main differentiator**
   - Remote desktop / VM on company or candidate machine; screen share + webcam; assigned **mentor**
   - ~30–60 min **design first** (classes, APIs, data structures) — mentor approval required before coding
   - Periodic checkpoints (~20–45 min); **elimination** if design or progress is weak
   - Reported problem domains: **file system** (create/delete/copy/move, versioning, disks, encryption), **virtual memory** (RAM/SWAP, paging, eviction), **music player**, **IPL auction**, **ride booking**, OS segment/memory puzzles
   - Runnable, correct output expected; mentors may hint at bugs; **Google allowed** in some drives
4. **Technical interview (45 min – 2.5 hrs)** — projects (deep); live coding (easy–medium DSA: strings, linked lists, trees, DP); **OS** (threads, file systems, memory, scheduling, deadlocks); **DBMS** (ACID, transactions); **OOP/C++** (polymorphism, vtable, pointers); occasional **CN**; discussion of machine-coding approach
5. **HR (~10–15 min)** — goals, relocation, behavioral; sometimes merged with offer call or skipped

**Offer shapes reported:** SDE Intern with FTE conversion; Intern + FTE directly (drive-dependent).

## Topic Weights
| DSA | OS | C/C++ | DBMS | CN | LLD | HLD | Concurrency | Aptitude |
|---|---|---|---|---|---|---|---|---|
| High | Very High | Very High | Med–High | Low–Med | Very High | Low | Med–High | Low–Med |

## Recurring Patterns & Tips
- **OOP in practice** beats theory — machine round expects clean class design in C++/Java.
- **OS + storage/backup domain fit:** file systems, memory, paging, threads show up repeatedly.
- Ask clarifying questions in the long round; explain trade-offs aloud.
- Pick **one language** early and know its OOP + STL/Java collections cold.
- Resume projects get grilled — own design decisions.
- Prep machine coding: file explorer, VM/pager, auction/booking-style constraint systems.
- Campus cutoffs are brutal after OA; speed + partial solves can still pass if MCQs are strong.
- Track **Commvault careers** + campus TPO + LinkedIn hiring posts in parallel for off-campus.

## Related topics
- [Operating Systems](../../topics/OS.md)
- [OOPs & LLD](../../topics/OOPs_LLD.md)
- [Concurrency & Multithreading](../../topics/Concurrency_Multithreading.md)
- [Graphs](../../topics/DSA/Graphs.md)
- [Dynamic Programming](../../topics/DSA/Dynamic_Programming.md)
- [Trees](../../topics/DSA/Trees.md)
- [Linked Lists](../../topics/DSA/Linked_Lists.md)
- [C++ Fundamentals](../../topics/Cpp_Fundamentals.md)

## Resource Panel
- [OS Boss Sheet](https://drive.google.com/file/d/1YquLAtpYmeTLMpyUfb6qd2rVwnQpsz74/view)
- [DBMS Boss Sheet](https://drive.google.com/file/d/1r1Yn5xhka9jpb75z8PO2SgD4g4F_Tcc_/view)
- [OOPS Boss Sheet](https://drive.google.com/file/d/1s0HeZt05eck7cuwXxQZtDiZ_NEPfZwo6/view)
- [LLD Boss Sheet](https://drive.google.com/file/d/1vG8CqGV8kGYOqTbA812-mKHKyeP1jGAQ/view)
- [Complete DSA Roadmap](https://drive.google.com/file/d/10e8Q1yVymwxWhz9LgcWxwrkpW9eMxRla/view)
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- [Commvault LC archive (legacy)](https://drive.google.com/open?id=1YBKvsIgfBoTqtKZyQZwZJpNbGdZQThVh)
- See also: [00_INDEX](../../00_INDEX.md) · [Software_Product_SDE](../../archetypes/Software_Product_SDE.md)

## Sources
- [Commvault System Recruitment Process (GFG)](https://www.geeksforgeeks.org/interview-experiences/commvault-system-recruitment-process/)
- [CommVault Interview Experience for SDE — off-campus (GFG)](https://www.geeksforgeeks.org/interview-experiences/commvault-interview-experience-for-sde/)
- [CommVault SDE On-Campus — pool campus (GFG)](https://www.geeksforgeeks.org/interview-experiences/commvault-interview-experience-for-sde-on-campus-2/)
- [Commvault Systems SDE — geeekd OA + file-system machine round (GFG)](https://www.geeksforgeeks.org/interview-experiences/commvault-systems-interview-experience-for-software-development-engineer/)
- [Commvault On-Campus 2023 — VM machine round (GFG)](https://www.geeksforgeeks.org/interview-experiences/commvault-interview-experience-on-campus-2023/)
- [Commvault SDE NIT Jamshedpur (GFG)](https://www.geeksforgeeks.org/interview-experiences/commvault-interview-experience-for-sde-nit-jamshedpur/)
- [My Commvault SDE Interview Experience (Medium)](https://medium.com/@samabhishek2605/my-commvault-sde-interview-experience-on-campus-55384a0d14b0)
- [Top 100 companies India 2024 — Commvault listed (LC Discuss)](https://leetcode.com/discuss/post/5083836/top-100-companies-india-2024-by-anonymou-7yjb/)

## Search log
- **Glassdoor:** `glassdoor.co.in/Interview/Commvault-Interview-Questions-E11561.htm` — fetch returned **403 Forbidden**; no usable India SDE process detail extracted.
- **LeetCode Discuss:** No dedicated Commvault SDE interview-experience thread found; only company-list / compensation mentions (e.g. post/5083836, post/2748640).
- **M.E./M.Tech off-campus:** No sourced India reports isolating PG eligibility or loop differences — marked insufficient above.
