# **Interview Prep**

# **Interview Preparation** 

This document serves as the central command center for your Software Development Engineer (SDE) interview preparation. It organizes resources across foundational CS subjects and DSA.

## **Data Structures & Algorithms**

This guide helps you choose the optimal algorithm based on a problem's constraints (n) and characteristics. Strong candidates read constraints like clues, as the limits often dictate the time complexity required for a successful solution.

| Constraint / Signal | Time Complexity Implied | Optimal Pattern / Algorithm | LeetCode Examples (Problem \#) |
| :---- | :---- | :---- | :---- |
| n ≤ 20 | O(2^n) / O(n\!) | Backtracking / Bitmasking | 78, 90, 46, 47, 77, 39 |
| n ≤ 100 | O(n³) | Simulation / DP | 62, 63, 64, 120, 931, 221 |
| n ≤ 1,000 | O(n²) | DP / Pair Checks | 300, 673, 1143, 72, 516, 647 |
| n ≤ 10⁵ | O(n log n) / O(n) | Sorting / Linear Scan | 56, 215, 347, 973, 128, 253 |
| n ≤ 10⁶ | O(n) | One-pass / Counting / Prefix Sum | 303, 560, 724, 930, 974, 523 |
| **Sorted Input** |  | Binary Search / Two Pointers | 33, 34, 35, 153, 167, 704 |
| **Many Queries** |  | Prefix Sum / Segment Tree / Fenwick | 303, 304, 307, 370, 1109, 2381 |
| **Tree with n nodes** |  | DFS / BFS / Tree DP | 104, 112, 113, 543, 124, 226 |
| **Weighted Graph** |  | Dijkstra / Shortest Path | 743, 787, 1514, 1631, 1334, 1976 |
| **Unweighted Shortest Path** |  | BFS | 994, 1091, 127, 752, 934, 1293 |
| **Need Top K** |  | Heap / Quickselect | 215, 347, 692, 703, 973, 1046 |
| **Need Count Frequency** |  | Hash Map | 1, 49, 128, 217, 242, 383 |
| **Need All Possibilities** |  | Backtracking | 17, 22, 40, 51, 52, 79 |
| **Need Min/Max Over Choices** |  | Dynamic Programming (DP) | 70, 198, 213, 322, 279, 416 |

### **How to Approach DSA: The AI-Assisted Strategy & Execution**

1. **The Golden Rule: Struggle First (20 min minimum):** Always spend at least 20 minutes genuinely trying a problem before seeking help. You must build your "struggle muscle."  
2. **Analyze Constraints First:** Read the problem constraints (n) to instantly determine the required time complexity (e.g., N ≤ 10⁵ implies O(N log N) or O(N)). This dictates the optimal pattern.  
3. **Ask AI Smart Questions:** If stuck, ask for hints or conceptual explanations, never the full solution. Use prompts like: "What pattern am I overlooking?" or "Critique my complexity analysis."  
4. **Master the Pattern:** Solve the first 2 problems of a new pattern slowly for conceptual understanding. Solve the next 2 for repetition. Solve the final 2 under time pressure for interview readiness.  
5. **Final Step: Stress Test:** After solving a problem, use an AI tool to stress-test your solution: "What edge cases am I missing? Can you challenge my code quality and complexity?"

### **DSA Pattern Map – How To Pick The Right Approach Fast**

#### **Arrays & Strings**

| Pattern | Core Idea | Spot It When | Example |
| :---- | :---- | :---- | :---- |
| Two Pointers | Move two indices to compare or scan a range | Sorted input, pairs/triplets, two ends | Two Sum, 3Sum |
| Sliding Window | Track a moving subarray or substring | Max/min length/sum of a contiguous segment | Min Size Subarray Sum, Longest Substring Without Repeating |
| Merge Intervals | Sort intervals then merge or clip overlaps | Input is \[start, end\] ranges that must be combined | Merge Intervals, Insert Interval |
| Prefix Sums | Precompute running sums for O(1) range queries | Many subarray sums or counts on same array | Subarray Sum Equals K, Range Sum Query |
| Hashmaps | Store counts or mappings for O(1) lookup | Frequency, grouping, existence checks | Group Anagrams, First Unique Character |
| Sorting | Sort first, then scan once | Order not given and logic becomes easier on sorted data | Sort Colors, Meeting Rooms II |

#### **Binary Search**

| Pattern | Core Idea | Spot It When | Example |
| :---- | :---- | :---- | :---- |
| Basic Binary Search | Halve the search space on sorted data | Sorted array and direct target lookup | Search Insert Position, Find Min in Rotated Array |
| Binary Search on Answer | Search on the value of the answer, not the index | “Minimum X that works” or “maximum X possible” | Split Array Largest Sum, Capacity to Ship Packages |
| Boundary Count Search | Find first or last position that meets a condition | Need lower/upper bound or count in sorted data | First and Last Position of Element, Count Negatives in Sorted Matrix |
| Mountain / Bitonic Search | Find peak, then search both sorted sides | Array strictly rises then decreases | Find Peak Element, Find in Mountain Array |

#### **Trees**

| Pattern | Core Idea | Spot It When | Example |
| :---- | :---- | :---- | :---- |
| Tree Traversal | Visit nodes in preorder, inorder, postorder, or level order | Binary tree traversal problems | Binary Tree Inorder Traversal, Level Order Traversal |
| Tree Construction | Rebuild tree from traversals or sorted data | Need to reconstruct tree structure | Build Tree From Preorder & Inorder, Sorted Array to BST |
| Path Sum | Track sums along root-to-leaf paths | Path or cumulative value questions | Path Sum, Binary Tree Maximum Path Sum |
| LCA and Search | DFS or BST rules to find nodes and ancestors | Need relationship between nodes | Lowest Common Ancestor, Search in BST |
| Validation / Properties | Check whether tree satisfies property | Tree validation or metrics | Validate BST, Diameter of Binary Tree |

#### **Dynamic Programming**

| Pattern | Core Idea | Spot It When | Example |
| :---- | :---- | :---- | :---- |
| Memoization | Save repeated states/results | Overlapping recursive subproblems | Fibonacci, Climbing Stairs |
| 1D DP / Memoization | Linear DP with previous states | Sequential optimization/counting | Fibonacci, Climbing Stairs |
| Subsequence DP | Longest increasing/common subsequence, edit cost | Order matters but not contiguity | LIS, LCS, Edit Distance |
| Knapsack Style | “Take or skip” decision with limit/target | Subset, partition, target-sum problems | Partition Equal Subset Sum, Target Sum |
| Interval DP | Cost depends on where to split/cut | Partitioning intervals/ranges | Burst Balloons, Strange Printer |
| Counting Ways | Count paths/sequences/combinations | “How many ways” questions | Distinct Subsequences, Unique Paths |

#### **Linked Lists**

| Pattern | Core Idea | Spot It When | Example |
| :---- | :---- | :---- | :---- |
| Fast and Slow Pointers | Two speeds to find middle or detect cycles | “Find mid”, “detect cycle”, nth from end | Linked List Cycle, Remove Nth Node From End |
| Dummy Node | Fake head to simplify insert/delete | Many head edge cases or rewiring | Add Two Numbers, Merge Two Sorted Lists |
| In-Place Reversal | Rewire pointers to reverse segments | “Reverse list”, “reverse k group” | Reverse Linked List, Reverse Nodes in K Group |
| Recursive Tricks | Solve list recursively node by node | Pairwise or elegant recursive solutions | Swap Nodes in Pairs, Flatten Multilevel List |

#### **Stacks & Queues**

| Pattern | Core Idea | Spot It When | Example |
| :---- | :---- | :---- | :---- |
| Monotonic Stack | Maintain increasing/decreasing order | “Next greater/smaller”, daily temperatures | Next Greater Element, Daily Temperatures |
| Design Using Stack/Queue | Use stack or queue to build behavior | State processing or streaming behavior | Implement Queue Using Stacks, Design Circular Queue |
| Expression Stack | Use stacks for operators and operands | Parsing/evaluating expressions | Basic Calculator, Evaluate Reverse Polish Notation |
| Sliding Window Deque | Deque keeps useful window elements | Need min/max over sliding window | Sliding Window Maximum, Moving Average from Data Stream |
| Queue Simulation | Build queue behavior with stacks | Queue operation implementation | Implement Queue Using Stacks, Design Circular Queue |

#### **Heaps / Priority Queues**

| Pattern | Core Idea | Spot It When | Example |
| :---- | :---- | :---- | :---- |
| Kth Largest / Smallest | Maintain heap of size k | Need kth element repeatedly | Kth Largest Element in Array, K Closest Points |
| Heap \+ Hashmap | Count frequency then use heap | Top frequent elements | Top K Frequent Elements, Sort Characters by Frequency |
| Merge K Sorted | Heap stores one item from each list | Multiple sorted streams/lists | Merge K Sorted Lists, Smallest Range From K Lists |
| Heap Design / Streams | Heap maintains dynamic median/order | Online or streaming data | Task Scheduler, Find Median From Data Stream |
| Heaps in Graphs | Priority queue for shortest paths | Weighted graph optimization | Network Delay Time, Cheapest Flights Within Stops |

#### **Graphs**

| Pattern | Core Idea | Spot It When | Example |
| :---- | :---- | :---- | :---- |
| Connected Components | DFS/BFS/Union Find groups nodes | Counting disconnected regions | Number of Islands, Connected Components in Undirected Graph |
| Shortest Path | BFS for unweighted, Dijkstra for weighted | Minimum distance/time/cost | Shortest Path in Binary Matrix, Network Delay Time |
| Cycle Detection | DFS state tracking or Union Find | Need to detect loops | Course Schedule, Redundant Connection |
| DAG / Topological Sort | Linearize dependencies | Task ordering / prerequisite problems | Course Schedule II, Alien Dictionary |
| Bipartite Check | Split graph into two groups | Constraints/conflict coloring | Is Graph Bipartite, Possible Bipartition |

### **📁 Handbooks & PDF Documents**

* **Complete DSA Roadmap:** [Complete DSA Roadmap (98 Pages)](https://drive.google.com/file/d/10e8Q1yVymwxWhz9LgcWxwrkpW9eMxRla/view?usp=drive_link)  
* **30 Coding Patterns:** [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view?usp=drive_link)  
* **DSA Revision Sheet Template:** [DSA Revision Sheet Template](https://docs.google.com/spreadsheets/d/1_v-8mOxArQgedzcZxCqtdl7KhVVKfMwV_DQa3mBAn3g/edit?usp=drive_link)

### **💻 GitHub Repositories & Gitbooks**

* **Leetcode Awesome Resource:** [Leetcode Awesome Resource Github](https://github.com/ashishps1/awesome-leetcode-resources?utm_source=sp_auto_dm&utm_referrer=sp_auto_dm&fbclid=PAVERTVgSlhENleHRuA2FlbQIxMABzcnRjBmFwcF9pZA81NjcwNjczNDMzNTI0MjcAAafY1GZPuzAF2hyyahtMVCm3JFTTlm17HNFTbNFnTBfqgsFeJGGVgAIlHfd8nA_aem_ZmFrZWR1bW15MTZieXRlcw)  
* **Algorithm Notes:** [Algo Notes Gitbook](https://liuzhenglaichn.gitbook.io/algorithm)  
* **STL Notes (practice):** [Github STL Notes](https://github.com/adityanayak20/Striver-TUF-Plus/tree/main/STL)  
* **STL Quick Reference (Study Guide):** `Study_Guide/topics/DSA/STL/00_STL_Quick_Reference.md`

### **🌐 Web Articles, Platforms & Interactive Tools**

* **Practice Sheet (Rising Brain):** [Practice Sheet (Rising Brain)](https://www.risingbrain.org/sheet)  
* **DSA Patterns Reference:** [DSA Patterns Reference](https://bpgc-dsa-patterns.netlify.app/)

---

---

## **Object-Oriented Programming (OOPs)**

This section is dedicated to Object-Oriented Design (OOD), SOLID Principles, and advanced Design Patterns, which are crucial for Low-Level Design (LLD) interviews.

## **Core Focus Areas**

* **Foundations:** Abstraction, Encapsulation, Polymorphism, Inheritance.  
* **Design Principles:** SOLID (SRP, OCP, LSP, ISP), Loose Coupling, and Inheritance vs. Composition.  
* **Design Patterns:** Focus on Creational, Structural, and Behavioral patterns (e.g., Strategy, Observer, State).

## **Study Strategy: LLD 6-Step Mental Model**

1. **Requirement Clarification** — Ask before you design  
2. **Identify Core Entities** — Define classes and attributes  
3. **Define Relationships** — Inheritance, composition, aggregation  
4. **Class to Function Mapping** — Add methods, discuss inputs/outputs  
5. **Model Core Interactions** — Walkthrough key flows as a sequence of method calls  
6. **Discuss Principles & Patterns** — Apply SOLID and relevant design patterns

### **📁 Handbooks & PDF Documents**

* **OOPS Interview Questions:** [OOPS Interview Questions.pdf](https://drive.google.com/file/d/19E0KwbC_ufqGPl6-sgL8jMWASraCiQ0E/view?usp=drive_link)  
* **Reference Book for Design Patterns:** [Dive Into Design Patterns (Alexander Shvets)](https://drive.google.com/file/d/1uu3Ye48X9h0YifMl56o2BbN5vkQdFiJk/view?usp=sharing)  
* **OOP Concepts & SOLID:** [OOP Notes - IT Bootcamp 2023.pdf](https://drive.google.com/file/d/1WBf4vRUpJIORoqP8VH50RWdeTyRMUnrR/view?usp=drive_link)  
* **Java for Interviews:** [Java Interview Series.pdf](https://drive.google.com/file/d/1mgPSPuxAHYfvfe0ha64so6p87kh0LwYt/view)  
* **Spring boot Series.pdf:** [Spring boot Series.pdf](https://drive.google.com/file/d/1K9Wo14cyiQLJ47x5MsIhTNKkdWC9qzbF/view)

### **💻 GitHub Repositories & Gitbooks**

* **Master Git Repo (LLD/OOP):** [awesome-low-level-design](https://github.com/ashishps1/awesome-low-level-design)  
* **Sunchit LLD Crash Course:** [SystemDesignLLDCrashCourse.git](https://github.com/Sunchit/SystemDesignLLDCrashCourse.git)

### **🎬 Video Courses & Tutorial Playlists**

* **Video Reference for Design Patterns:** [Design Patterns in Object Oriented Programming (Christopher Okhravi)](https://www.youtube.com/playlist?list=PLrhzvIcii6GNjpARdnO4ueTUAVR9eMBpc)

---

---

### **Practice Problem Bank**

* **LLD Problems:** Tic Tac Toe, Chess, Parking Lot, Elevator System, Inventory Management, Car Rental, Vending Machine, File System, Logging System, Splitwise, ATM Machine, Snake & Food  
* **LLD \+ Concurrency:** Movie Ticket Booking, Cache with eviction (LRU, LFU), Pub-Sub Model like Kafka, Thread safe Rate Limiter  
* **AI-Assisted Learning Loop:** Use the 6-step model with an AI tool to walk through problems, then attempt on your own, and finally ask the AI to find gaps/suggest improvements. The goal is to build the instinct to decompose any system cleanly under time pressure.

## **Operating Systems (OS) & Concurrency**

## **Core Focus Areas**

This roadmap covers the most common SDE interview topics, focusing on conceptual clarity and concurrency challenges.

1. **Process & Threads:** Process states, PCB (Process Control Block), difference between Process and Thread, Context Switching.  
2. **Scheduling:** Scheduling algorithms (FCFS, SJF, Priority, Round Robin), objective of multiprogramming.  
3. **Synchronization & IPC:** Critical Section Problem, Semaphores (Binary vs. Counting), Mutex, IPC mechanisms (Pipes, Sockets, Shared Memory).  
4. **Deadlocks:** The four necessary conditions (Mutual Exclusion, Hold and Wait, No Pre-emption, Circular Wait), prevention, and Banker's Algorithm (avoidance).  
5. **Memory Management:** Logical vs. Physical address space, Paging, Segmentation, Virtual Memory, Thrashing, Page Replacement Algorithms (FIFO, LRU).  
6. **I/O & Storage:** File Systems, Disk Scheduling algorithms (FCFS, SSTF, SCAN).  
7. **Kernel & System Basics:** Types of Kernels (Monolithic vs. Microkernel), system calls, dual-mode operation.

### **📁 Handbooks & PDF Documents**

* **Conceptual Notes:** [Bedtime Stories on Operating Systems.pdf](https://drive.google.com/file/d/1BMtW2e2Lm-ngAhAssicyN4lFq5InLJ6j/view?usp=sharing)  
* **General Interview Guide:** [OS\_InterviewBit.pdf](https://drive.google.com/file/d/1-2aR5Jq1YVAB8hrrsdFxTJqGExgop8Ms/view?usp=sharing)  
* **Bootcamp/Online Notes:** [Operating Systems IT Bootcamp 2023](https://woozy-pluto-cb4.notion.site/Operating-Systems-IT-Bootcamp-2023-033e086ddc474089ad92ce63050cbd3a)  
* **MCQ Practice Bank:** [Os Mcq.pdf](https://drive.google.com/file/d/11fADR2f8lIkK3HLQnGZ7jBhjBFa5Dd2G/view?usp=drive_link)  
* **Advanced OS Concepts:** [Os Operating System Notes 164.pdf](https://drive.google.com/file/d/1S7Ucn7G-s7XoYYLLjjDrx2Isq-UrIEtS/view?usp=drive_link)  
* **OS Interview Cheatsheet:** [Operating Systems by CodeHelp.pdf](https://drive.google.com/file/d/1cVm80CaUVny9MKHjzbQi2b3wcuTZSsUM/view?usp=drive_link)  
* **OS Interview Questions:** [Operating System Interview Questions.pdf](https://drive.google.com/file/d/1hyoWnDiDXaxJJ8pvVbpiTJZIzshEJbf-/view?usp=drive_link)

### **💻 GitHub Repositories & Gitbooks**

* **OS Github Repo:** [OS Github Repo](https://github.com/exajobs/os-collection.git)

---

---

## **Database Management Systems (DBMS)**

## **Core Focus Areas**

1. DBMS vs RDBMS  
2. Keys — Primary, Foreign, Candidate, Composite, Unique  
3. Normalization — 1NF, 2NF, 3NF, BCNF  
4. Functional Dependencies  
5. Transactions and ACID Properties  
6. Concurrency Control and Locking  
7. Shared Lock vs Exclusive Lock  
8. Deadlocks — conditions, prevention, recovery  
9. Indexing — clustered vs non-clustered  
10. B+ Trees basics  
11. Joins — inner, outer, self, cross joins  
12. Views, Stored Procedures, Triggers basics  
13. Query Optimization fundamentals  
14. Isolation Levels — dirty read, phantom read, non-repeatable read  
15. SQL Constraints — NOT NULL, UNIQUE, CHECK, DEFAULT

**Most common Interview patterns:**

* ACID explanation  
* Normalization problems  
* Indexing internals  
* Transaction isolation scenarios  
* Deadlock situations  
* Join-based reasoning questions

### **📁 Handbooks & PDF Documents**

* **SQL Basic Notes:** [SQL Basic Notes.pdf](https://drive.google.com/file/d/1VxXZziTmA_4Tm4XLS9NYOGpTA8BYrtFn/view?usp=sharing)  
* **SQL Animated Notes:** [SQL Interview Series.pdf](https://drive.google.com/file/d/1Qrt3G4gUDyFU3A1IhvKFbrdx1xUhDRwR/view)  
* **SQL Interview Guide:** [SQL Interview Guide.pdf](https://drive.google.com/file/d/17vulPDcuIkbbx9UZXgnqoMfceQmDtYnb/view?usp=sharing)  
* **DBMS Full Notes:** [DBMS Full Notes.pdf](https://drive.google.com/file/d/1KLm-chZD9hdOwIlFsKv6eemKzsbV80Wh/view?usp=sharing)  
* **SQL in 16 Pages:** [MASTER SQL IN 16 PAGES. .pdf](https://drive.google.com/file/d/1DXz5z2BtU_fTmdn0r1m8elilEKc1vHH4/view?usp=sharing)  
* **DBMS Q/A:** [DBMS INTERVIEW QUE & ANS.pdf](https://drive.google.com/file/d/1wwBTS1POgOpo4IwTEwMWdPDycgBN7tY7/view?usp=sharing)  
* **DBMS Top 100 Q/A:** [SQL Top 100 Questions.pdf](https://drive.google.com/file/d/1Px6ez6Sn7jb1DOSWE8kwesANdhhyjRzj/view?usp=drive_link)  
* **Leetcode SQL Practice Solutions:** [Leetcode SQL Solutions.pdf](https://drive.google.com/file/d/1LZfJqnrAxvqI2lKTsnkYxP4lHgJp9Gc8/view?usp=drive_link)

### **🎬 Video Courses & Tutorial Playlists**

* **Database 101:** [YouTube Playlist](https://youtube.com/playlist?list=PL5Lsd0YA4OME2HC5m9QSfXG9cxb9Cvz5L&si=dij6DgcHtce1PE8f)

### **🌐 Web Articles, Platforms & Interactive Tools**

* **Practice: LeetCode Top 50 SQL Problems:** [LeetCode Top 50 SQL Problems](https://leetcode.com/studyplan/top-sql-50/)

---

### **Resources & Notes**

---

## **Computer Networks (CN)**

## **Core Focus Areas**

#### **1\. Network Models & Fundamentals**

* **OSI Model:** All 7 layers, responsibilities, protocol mapping.  
* **TCP/IP Model:** Layer mapping with real-world protocols.  
* **"What happens when you type google.com?"** — Complete end-to-end flow.

#### **2\. Transport Layer (TCP/UDP)**

* **UDP vs TCP:** Reliability vs. speed tradeoff, use cases.  
* **TCP 3-Way Handshake:** SYN, SYN-ACK, ACK flow.  
* **TCP Reliability:** Sequencing, retransmission, flow control.

#### **3\. Application Layer (HTTP/S)**

* **HTTP Basics:** Request/response cycle, stateless nature.  
* **HTTP Methods:** GET, POST, PUT, DELETE, PATCH.  
* **HTTP Status Codes:** 200, 301, 400, 401, 403, 404, 500\.  
* **HTTPS/TLS:** Encryption, certificates, TLS handshake basics.

#### **4\. Network Services & Infrastructure**

* **DNS Lookup Flow:** Browser → resolver → root → TLD → authoritative.  
* **Cookies vs Sessions vs JWT:** Authentication fundamentals.  
* **Load Balancers:** Round Robin, Least Connections, L4 vs L7.  
* **Reverse Proxy vs Load Balancer:** Core distinction.  
* **NAT:** Private/public IP translation, PAT basics.

### **📁 Handbooks & PDF Documents**

* **Short Notes:** [Computer Networks Quick Notes.pdf](https://drive.google.com/file/d/1OymHd6cW-KQ4L36DVCEeD2OUdknXQBwY/view?usp=sharing)  
* **Notes:** [Networking Concepts - Blue Team Resources.pdf](https://drive.google.com/file/d/12dJ0VPDdLkFtnkjHkMEBxcixqERr37IP/view?usp=sharing)

### **💻 GitHub Repositories & Gitbooks**

* **Github Repo Notes:** [notescs/notes/blob/main/Computer-Networks-for-Interviews/README.md](https://github.com/notescs/notes/blob/main/Computer-Networks-for-Interviews/README.md)

### **🎬 Video Courses & Tutorial Playlists**

* **Comprehensive Video Course (General CN):** [Playlist Link](https://youtube.com/playlist?list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&si=H8-LWNEtmtk2rMTg)  
* **TCP/UDP Deep Dive:** [Playlist Link](https://youtube.com/playlist?list=PLIFyRwBY_4bS-PQZoF0UySdG0sH9VA0bn&si=aHlR0KWqRbfoEs1M)  
* **Cryptography Essentials:** [Playlist Link](https://youtube.com/playlist?list=PLIFyRwBY_4bQvq5PuJASilkHSVGLZtceZ&si=qHK_T8QoUPkzk9a6)

---

---

## **System Design**

## **General System Design**

* **Core Concepts:**  
  * CAP Theorem (Consistency, Availability, Partition Tolerance)  
  * Consistency Models (Eventual, Strong)  
  * Data Partitioning Strategies (Horizontal/Sharding, Vertical)

#### **DevOps, Microservices & Tools**

* **Containerization (Docker & Kubernetes)**  
* **Microservices**

### **📁 Handbooks & PDF Documents**

* **System Design Questions Ebook:** [system-design-questions-ebook.pdf](https://drive.google.com/file/d/1RZGN4VZgFc5w8LRkhpoXfpmtfB_n9hzY/view)  
* **DevOps or Cloud Engineer interview:** [𝐃𝐞𝐯𝐎𝐩𝐬 𝐨𝐫 𝐂𝐥𝐨𝐮𝐝 𝐄𝐧𝐠𝐢𝐧𝐞𝐞𝐫 𝐢𝐧𝐭𝐞𝐫𝐯𝐢𝐞𝐰.pdf](https://drive.google.com/file/d/1p4Gb06r5Y1bWX_Bp6mCg0ehbgXKFF74D/view?usp=sharing)  
* **Microservices Interview Questions:** [Microservices Interview Questions.pdf](https://drive.google.com/file/d/1eK9SLit0HU8v7BauGEb1aBM6dhBeQkjm/view)

### **💻 GitHub Repositories & Gitbooks**

* **Master Git Repo (HLD):** [awesome-system-design-resources](https://github.com/ashishps1/awesome-system-design-resources?tab=readme-ov-file)  
* **Sunchit System Design Interview Series:** [SystemDesignInterviewPreparationSeries.git](https://github.com/Sunchit/SystemDesignInterviewPreparationSeries.git)  
* **Sunchit System Design Crash Course:** [SystemDesignCrashCourse.git](https://github.com/Sunchit/SystemDesignCrashCourse.git)

### **🌐 Web Articles, Platforms & Interactive Tools**

* **HLD Primer:** [System Design Fundamentals](https://systemdesignschool.io/primer)  
* **Top 50 System Design Questions:** [Threads Post](https://www.threads.com/@techie_programmer/post/DX6dOqlmY2r?xmt=AQG0Hhe-C_yt6ug7KrYmQR_o-bmi1jCTaw-S7eQ6qeHhWw)  
* **System Design For Beginners: Everything You Need in One Article:** [Medium Article](https://medium.com/@shivambhadani_/system-design-for-beginners-everything-you-need-in-one-article-c74eb702540b)  
* **Docker Architecture: Components and Usage:** [Medium Article](https://praveendandu24.medium.com/understanding-docker-architecture-an-in-depth-overview-of-docker-components-and-usage-f1a26bd217f9)  
* **Kubernetes for Beginners:** [Medium Article](https://praveendandu24.medium.com/kubernetes-tutorial-for-beginners-mastering-the-basics-in-1-hour-332db7b5916b)  
* **Kubernetes: Game-based Learning:** [k8sgames](https://k8sgames.com/)  
* **Benefits and Pitfalls (Microservices):** [Threads Post](https://www.threads.com/@techie_programmer/post/DYTn3jzoPrb?xmt=AQG0HWnQfis-M3MnNMlZ2AGun3EPsoQ1wB_RTMGKVrKZ4w)

## **Git & Version Control**

### **Git Commands Reference**

* **Quick Resource:** [Git Commands Cheatsheet (Full PDF)](https://drive.google.com/file/d/1-zh1-ihR47RiJQ8hNSE-EUL_zbjV6Dj8/view?usp=sharing)

### **Core Concepts & Resources**

* **Core Concepts Breakdown:**  
  * **Repository:** Project folder (local or remote)  
    * **Commit:** Save a snapshot of your changes  
    * **Branch:** Parallel version of your project  
    * **Merge:** Combine branches  
    * **Clone / Push/Pull:** Sync local and remote repos  
* **Git Professional Guide:** [Git Pro Book](https://git-scm.com/book/en/v2)  
* **Git Concept Videos:** [Git Branching](https://youtu.be/Q1kHG842HoI)

# **Interview Cheatsheet**

# **Foundations**

* [space-complexity-cheatsheet.pdf](https://drive.google.com/file/d/1VN4YXK83x9hu6beUPhrlI6D5Ij0-kRht/view)  
* [Time Complexity](https://docs.google.com/document/d/1Vh19VzdiAbD2x7Tpw0YOvisXcY-NhyJqmtmlIOTQMzg/mobilebasic)

# **Core Data Structures**

* [array-mastery-cheatsheet.pdf](https://drive.google.com/file/d/1PGLEG1Kn5sg6dOq_4QPykBKdvy3Qf3Mj/view)	  
* [string-mastery-cheatsheet.pdf](https://drive.google.com/file/d/1GgKKAJcFRJBfSHbsTO_H0UKUYXqefp-i/view)  
* [linkedlist-mastery-cheatsheet.docx](https://docs.google.com/document/d/1lDSq_JKCrY0L-j81UGmMI1nAqCU_cSJx/mobilebasic)  
* [stack-mastery-cheatsheet.docx](https://docs.google.com/document/d/1GtEmGU912cF_WGf2wzLl87gyJDJ43D_t/mobilebasic)  
* [queue-mastery-cheatsheet.pdf](https://drive.google.com/file/d/19wuChBcx4puSFgryqi-GHqLiGm24vS8q/view)  
* [binary-tree-mastery-cheatsheet.pdf](https://drive.google.com/file/d/1hHBgLeTgRiQsmy_3OrcvOXZSJogl2zdQ/view)  
* [heap-mastery-cheatsheet.docx](https://docs.google.com/document/d/1DU11jH301gG0C35SLmptIRIkz5ui0STQ/mobilebasic)  
* [graph-mastery-cheatsheet.pdf](https://drive.google.com/file/d/1Oyu009O6X5wKw-ETC-GxsFDjHJTWDNXS/view)  
* [trie-mastery-cheatsheet.pdf](https://drive.google.com/file/d/10SmQg-F4cQQPBTxPUDyxdgMF99Qijr44/view)

# **Algorithms & Advanced Patterns**

* [bit-and-math-mastery-cheatsheet.pdf](https://drive.google.com/file/d/1gPXenSrwfnme7NSrGBt4DnCWKBkza8-m/view)  
* [recursion-backtracking-mastery-cheatsheet.pdf](https://drive.google.com/file/d/1zXVZNiAKTHX39mvugroPntfrrROV8GEx/view)  
* [intervals-mastery-cheatsheet.pdf](https://drive.google.com/file/d/1t3lK0hN2b0pESWkGMMHpys5iJbFVKdEI/view)  
* [greedy-mastery-cheatsheet.pdf](https://drive.google.com/file/d/16rArMG-reo4xZgZNcDRfIMRilrK8KPZY/view)  
* [dp-mastery-cheatsheet.pdf](https://drive.google.com/file/d/1fc0H-9Uhb-dJeIKBHsovWMlGWZ3gM3Fv/view)

# **CS Subjects**

* [os-mastery-cheatsheet.pdf](https://drive.google.com/file/d/1YquLAtpYmeTLMpyUfb6qd2rVwnQpsz74/view?usp=drivesdk)  
* [Threads Notes](https://github.com/adityanayak20/POSIX-Threads)  
* [OOPS Boss Sheet.pdf](https://drive.google.com/file/d/1s0HeZt05eck7cuwXxQZtDiZ_NEPfZwo6/view)  
* [DBMS-BOSS-SHEET.pdf](https://drive.google.com/file/d/1r1Yn5xhka9jpb75z8PO2SgD4g4F_Tcc_/view?usp=drivesdk)  
* [Computer-Network-Boss-Sheet.pdf](https://drive.google.com/file/d/1maLFnmWgjgJyCd6cQ4CHIlVbLIMRMaAm/view?usp=drivesdk)  
* [cloud-fundamentals-cheatsheet.pdf](https://drive.google.com/file/d/11VMfojBhBjGQa_JMvC6_kAgiwjrqyU9f/view)

# **System Design**

* [HLD system design Boss sheet.pdf](https://drive.google.com/file/d/1YClCcB5e1tq1dNNnXeDQUnibCjCLykYI/view)  
* [LLD/Design Pattern Boss sheet.pdf](https://drive.google.com/file/d/1vG8CqGV8kGYOqTbA812-mKHKyeP1jGAQ/view)

# **Career Preparation**

* [resume-audit-checklist.pdf](https://drive.google.com/file/d/1sWlKCDKVJ0g9PLWBz_dBTOSETPEB0MTO/view)  
* [FAANG\_READY\_TEMPLATE.pdf](https://drive.google.com/file/d/1AF3-vDvHabiUZFNWVI_FxjEqxjkhZQNW/view)  
* [HR/Behavioural Round Boss Sheet.pdf](https://drive.google.com/file/d/1jsOro7s9jwRc-TvANeAVNjmf8bErkMX5/view?usp=drivesdk)  
* [awesome-behavioral-interviews](https://github.com/ashishps1/awesome-behavioral-interviews)  
* [Top 30 HR Questions for Freshers.pdf](https://drive.google.com/file/d/1bWFEAyMbFFaFrvXMJX2R7kkPA4LNeksR/view)  
* [Madhumitha’s\_DSA\_Notes.pdf](https://drive.google.com/file/d/11_enW1g-82iT94TcusBk5euWY24tii--/view)  
* [MERN Stack Interview Questions.pdf](https://drive.google.com/file/d/1WepCn-fPcStjSTbAf0EEP0l0EGD_Efwp/view?usp=drive_link)  
* [Machine Learning short notes.pdf](https://drive.google.com/file/d/1olRoyE_Vm6eOwN8sSbihpXV1O8f6aYOH/view?usp=sharing)  
* [Domain Wise Roadmaps](https://github.com/nileshhadalgi016/digital-landfill.git)

# **Interview Tips**

General instructions and tips

Hiring process of any IT company  
First round is coding round  
In general 2 technical round in SIPs ( each round is around 40-50 mins in general)   
Followed by this there is a HR round (30-45 mins in general)

What are the expectations in these technical rounds?  
\-\> most important is DSA  
\-\> then comes your core fundamentals knowledge ( oops and dbms only in your case)  
\-\> your internship experience \+ your projects  
Companies don't expect much from you in terms of your development exposure, for sips.  

Your introduction :- make sure that it’s balanced, it should describe you technically on high lvl.  
The flow of intro can be 

1) Your background  
2) Your cp achievement   
3) Your internship experience (must)  
4) Your personal projects short description( if they are good enough )  
5) Your hobbies

DSA based rounds   
\-\> a problem statement will be given your are expected to solve it as optimally both in terms of space and time possible.

\-\> If your interviewer is a cpier then he may ask a tough question as compared to other cases, so don't exaggerate much about your cp skills much otherwise be prepared for a tough question, i don't say that this always happens, but in some case it had happened. 

Possible situation which can arise

1) You already know the solution :- many times interviewer takes some standard problem which we have already solved, don't directly tell the final(most optimized) solution logic this will hint them that you have already solved it, they want to test your thinking skills, the purpose of these dsa round is to test how you approach a problem intuitively. First do a fast ran on brute and then go to optimal brute, discussion on the brute and optimal brute should be very fast, you cant afford your time to lose on those solution which interviewer is not interested, after this move to most optimal solution then discuss that in detail, you are expected to know the time and space complexity, if you fail in this, this will make a bad impression on the interviewer.  
   Brute —-------\> optimal brute —----\> optimal  
2) You are given a new problem which reduces to some standard problem which you have solved :-  At such situation, make sure to not lose your calm, during interviews we become tensed, a medium rated question become hard, in most of the situations question given are not tough, but we frame them as tough, now your confidence and calm behavior will play a key role here.  
1) Make sure you have clarified all the necessary details here, like constraints and you have proper understanding of the question, don't  be in a hurry, it happens many times we mis understand the problem then we move in the wrong direction and realize this very later, make sure you have properly communicated with the interviewer about the problem requirement you can even take example clarify the expected output form the interviewer, after this make some smart observation, if you are calm enough then the logic will the click and problem will be reduced to original subproblems from which it is constructed.  
3) Completely new problem, now its all about you experience and intuition  
   \-\> Now it's all about how calm you are and how much exposure you have to various problems, just try to reach the most optimal solution you can make, start from the brute and keep on optimizing it, in this process you can ask the guidance of the interviewer as well.

**Most important :-** Don't be silent in this process, always try to show that you are trying to reach the solution actively, it should be clearly visible that your brain it actively working towards the logic construction, sometimes its okay even if you are not able to solve the problem, in such situation it’s  all about how you approached the problem, how close you were to actual solution, how well you have communicated your present solution to interviewer.  
If you are not sure about the approach which you have in mind, you can simply ask, “ am i moving in the correct direction”, most probably you will get a reply.  
Or sometimes you can ask for hints indirectly, but dont ask in the starting, interviewer will only help only if you are trying and using your brain actively, after some attempts of thought you can   
Simply ask “ can you guide me a little towards the right direction”, if the interviewer sees that you have applied some considerable effort and after that you are asking for a guidance most probable you will get a hint, sometimes they give hints without asking.  

\-\> Mostly you have to write code on google doc, so make sure you are comfortable with writing code on it, your code will be mostly dry run ( except few cases when you have to code on some platform and few basic test case are run against it), so you may no write the correct code without compiling it, but your interviewer will dry run it, so make sure you have went through your code properly and dry run it, from your side.

\-\> while writing code make sure that your code quality is good, basically all the variables and functions names should make sense, while writing the code keep on speaking your thought procedure.

Core subject based round   
Questions will be mostly direct, whether you know them or not, i mean it wont take to realize this except for some questions related to sql query, for which you may need time to actually process the solution in your mind.  
These rounds are mostly tests of your knowledge.

1) You know the right answer :- no problem then  
2) You know something :- speak whatever you know( but be relevant), don't be silent in any case.  
3) You don't know anything : \- say “ i am not able to recall it, can we come back to this question later” instead of “ i don't know”, or you can say “ right now i am not able to recall but i will make sure to go through this after this interview”.

Project and internship experience based rounds  
\-\> prepare an intro of your internship experience, like what you did, how it was helpful etc, same for your personal projects, you can expect a burst of questions from the interviewer side.

Possible cases  
\-\> your interviewer knows the techstack used :- He might grill you on questions related to tech stack used in worse case, so should have atleast basic idea of techstack used, he may ask some basic question related to techstack, if he goes deeper, you can simply say “ it been quite a long time i have used this tech stack, this project is quite old, so i am not very proficient in the tech stack now”, they are more interested in your learning capability more than how much knowledge you presently have.  
But to deal with this, it’s always better to go through top 40-50 questions related to that techstack, so that atleast you can show that you are well versed with the basics atleast.

\-\> he/she doesnt know about it :- well in this case the discussion is only going to happen at high lvl overview of the project, he might ask you basic things, which even he don't know, if you fail to answer this is going to frame a bad impression, so atleast a basic idea of what is being used is necessary.

Tip:- make a question and answer script of your project and internship experience.

What type of question should you prepare for the interview?  
\-\> these following are some of the question you can prepare

1) What techstack was used and why only this one?  
2) What was the motivation for this project?  
3) What was the most challenging task you faced during the making of this project?  
4) Any future plans for your projects  
5) Learnings from this projects  
6) Role as a teammate ( if it was a group project)  
7) High level overview of architecture and flow of the website   
8) how will you overcome the challenges of maintaining scalability.  
9) He might change some condition in your project and then ask you are you going to handle and implement it.

\-\> if you have done the projects on your own then such questions should not be a problem, if you have copied it then be prepared with some sets of questions.

\-\> to get question specific to your project or internship experience, use chatgpt give all the context and description of your project to chatgpt, and ask him to act as an interviewer, and ask all possible questions.

LLD based rounds( the worse case )  
\-\> mostly it won't be asked, but still lets cover it, try to understand that a solving a good lld problem, needs one to make a detailed UML( given that its good problem) along with it discussion followed by its code completion. This will take around 40-50 mins or more, so the whole round is dedicated towards lld only, in maximum cases you have 2 technical round, it’s not possible to judge  on everything other than lld in just one round, so if a lld question is asked it will be easy, either it will be direct application of some design pattern or no design pattern will be used to solve it, usually u wont need to make a uml cause questions is anyways simple, you can focus on the coding part and discuss it in detail.  
Tips :- 1\) There is no single right answer to such a question, you may need to make assumptions, just make sure that whatever assumption u made is communicated properly to the interviewer.  
2\) It may happen that in the starting you are clueless, completely fine, it's not like classical dsa rounds, you need to build the so based on your interaction with the interviewer, he may also hint in between, also keep on asking whether i you are  moving in the current direction, and if you are wrong what is expected here.  
3\) practice a little writing classes and objects, usually during cp we are not interested in such things, but here these things right usage matters a lot.

Interview preparation resources 

**( if you have very less time for any topic then just go through top 40-50 questions of it google it)**

\-\> Oops in c++ specifically   
    Part 1 :- [https://youtu.be/i\_5pvt7ag7E](https://youtu.be/i_5pvt7ag7E)   
    Part 2 :- [https://youtu.be/b3GccK5\_KSQ](https://youtu.be/b3GccK5_KSQ)   
All topics are not covered in this video you will need to go through these as well  
[Video-1](https://www.youtube.com/watch?v=HK6gnkQIgqI&list=PLu0W_9lII9agpFUAlPFe_VNSlXW5uE0YL&index=26)  | [Video-2](https://www.youtube.com/watch?v=Tk-4KUoatg8&list=PLu0W_9lII9agpFUAlPFe_VNSlXW5uE0YL&index=27)   
[Video-3](https://www.youtube.com/watch?v=GTJTsMR_fro&list=PLu0W_9lII9agpFUAlPFe_VNSlXW5uE0YL&index=28)  | [Video-4](https://www.youtube.com/watch?v=kzMQpPX7TUY&list=PLu0W_9lII9agpFUAlPFe_VNSlXW5uE0YL&index=44) (diamond problem very important)   
[Video-5](https://www.youtube.com/watch?v=eYV-TohBaa0&list=PLu0W_9lII9agpFUAlPFe_VNSlXW5uE0YL&index=45)  | [Video-6](https://www.youtube.com/watch?v=0YQ_yhX46uk&list=PLu0W_9lII9agpFUAlPFe_VNSlXW5uE0YL&index=55)  
[Video-7](https://www.youtube.com/watch?v=fB3JHNnlRfI&list=PLu0W_9lII9agpFUAlPFe_VNSlXW5uE0YL&index=56)  | [Video-8](https://www.youtube.com/watch?v=-noYyWtdXSI&list=PLu0W_9lII9agpFUAlPFe_VNSlXW5uE0YL&index=57)   
[Video-9](https://www.youtube.com/watch?v=RBAWWutf0fY&list=PLu0W_9lII9agpFUAlPFe_VNSlXW5uE0YL&index=58)  | [Vpointer & Vtable](https://youtu.be/47ZP-0iBicI) ( very important ) 

Reading resources  
[https://www.codingninjas.com/studio/guided-paths/oops-in-c](https://www.codingninjas.com/studio/guided-paths/oops-in-c)   
[Interface vs abstract class](https://stackoverflow.com/questions/1913098/what-is-the-difference-between-an-interface-and-abstract-class)  
[Stack vs Heap memory allocation](https://www.geeksforgeeks.org/stack-vs-heap-memory-allocation/)  
[Encapsulation vs inheritance](https://stackoverflow.com/questions/742341/difference-between-abstraction-and-encapsulation)     
[Diamond Problem](https://www.makeuseof.com/what-is-diamond-problem-in-cpp/)  
[Dynamic Binding](https://www.geeksforgeeks.org/dynamic-binding-in-cpp/) 

[DBMS](https://www.youtube.com/watch?v=eYpXCdvKwEQ&list=PLDzeHZWIZsTpukecmA2p5rhHM14bl2dHU) (you may not need to go through all the videos keep following points in mind while going through this playlist )  
\-\> Try to cover till lec 14 ( it should be sufficient in most of the cases)  
\-\> There are some examples of how to design ER model of something, focus on the general procedure of how to design it, similar question was asked in last year internship interviews of sprinklr( design bookmy show from the dbms perspective)  
     This is a playlist containing various problems ( very few company will ask this so not important i would say, you can focus on other topics if you have time i would say).  
      [https://www.youtube.com/playlist?list=PLlGqj2KrYnpSIavv7ZdRkD8VWUwwZ2dF2](https://www.youtube.com/playlist?list=PLlGqj2KrYnpSIavv7ZdRkD8VWUwwZ2dF2)   
      [https://www.youtube.com/watch?v=oiT54MhQy90\&t=1s](https://www.youtube.com/watch?v=oiT54MhQy90&t=1s)   
\-\> Apart from that relational model, sql(lec 9 and 10\) i mean everything is important cover all of them properly.  
\-\> beyond lec 14, its less probable that it will be asked unless u have a bad luck or your interviewer wants to grill you on this.  
\-\> if you get time lec 15 can be considered giving time. 

Reading resources   
[https://drive.google.com/file/d/1y3KKghRhQjKfbWhvLipMOCCemKd\_XdTm/view?pli=1](https://drive.google.com/file/d/1y3KKghRhQjKfbWhvLipMOCCemKd_XdTm/view?pli=1)  (luv babbar notes)   
[https://www.codingninjas.com/studio/guided-paths/dbms-database-management-systems](https://www.codingninjas.com/studio/guided-paths/dbms-database-management-systems) ( may not need to go through this above notes will be more than sufficient)

SQL :- [https://www.w3schools.com/sql/](https://www.w3schools.com/sql/) ( for basics)  
\-\> for problem practise refer luv babbar sql problem video if you have time you can go though these extra problems as well  
\-\>[https://www.linkedin.com/posts/guptaabhishek17\_sql-most-asked-questions-ugcPost-7081472445857038336-jyvJ?utm\_source=share\&utm\_medium=member\_android](https://www.linkedin.com/posts/guptaabhishek17_sql-most-asked-questions-ugcPost-7081472445857038336-jyvJ?utm_source=share&utm_medium=member_android) ( this one as extra is more than sufficient)  
\-\>[https://www.w3resource.com/sql-exercises/](https://www.w3resource.com/sql-exercises/) ( more problems) 

Puzzles   
\-\> [https://drive.google.com/drive/folders/1b18TJq-trvyUyRogxJd3SGcZIsoZYE5h?usp=sharing](https://drive.google.com/drive/folders/1b18TJq-trvyUyRogxJd3SGcZIsoZYE5h?usp=sharing)   
 ( that 75 problems contains lots of famous problems)  
\-\> [https://www.geeksforgeeks.org/top-100-puzzles-asked-in-interviews/](https://www.geeksforgeeks.org/top-100-puzzles-asked-in-interviews/) ( extra problems , might contains overlapping problems with the above drive) 

Bit manipulation ( not so important)  
\-\>[https://drive.google.com/file/d/1w-EGdHZtP5mgXi7FSaVOuQu1WgmI7iXp/view?usp=sharing](https://drive.google.com/file/d/1w-EGdHZtP5mgXi7FSaVOuQu1WgmI7iXp/view?usp=sharing) 

DSA or c++ specific theory question and little ignored topics  
\-\> heaps( not so important) :- [https://www.geeksforgeeks.org/introduction-to-heap-data-structure-and-algorithm-tutorials/](https://www.geeksforgeeks.org/introduction-to-heap-data-structure-and-algorithm-tutorials/)   
[https://www.youtube.com/watch?v=RU08pp\_VPSs\&list=PLEJXowNB4kPyP2PdMhOUlTY6GrRIITx28](https://www.youtube.com/watch?v=RU08pp_VPSs&list=PLEJXowNB4kPyP2PdMhOUlTY6GrRIITx28) ( a detailed playlist )

\-\> maps( hashing) :- [https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/) 

\-\> sets :- [https://stackoverflow.com/questions/2558153/what-is-the-underlying-data-structure-of-a-stl-set-in-c](https://stackoverflow.com/questions/2558153/what-is-the-underlying-data-structure-of-a-stl-set-in-c) 

\-\> vectors :- [https://duggal-shweta2010.medium.com/how-are-vectors-implemented-internally-in-c-5787abf1c38f](https://duggal-shweta2010.medium.com/how-are-vectors-implemented-internally-in-c-5787abf1c38f)   
   
\-\> Sorting :-  
Bubble Sort:		[Blog](https://www.geeksforgeeks.org/bubble-sort/) | [Video](https://youtu.be/Jdtq5uKz-w4)  
Selection Sort: 		[Blog](https://www.geeksforgeeks.org/selection-sort/) | [Video](https://youtu.be/GUDLRan2DWM)  
Insertion Sort:		[Blog](https://www.geeksforgeeks.org/insertion-sort/) | [Video](https://youtu.be/i-SKeOcBwko)  
Counting Sort: 		[Blog](https://www.geeksforgeeks.org/counting-sort/) | [Video](https://youtu.be/imqr13aIBAY)  
Merge Sort:		[Blog](https://www.geeksforgeeks.org/merge-sort/) | [Video](https://youtu.be/cWvruDR-hJA)     
Bucket:                         [Blog](https://www.geeksforgeeks.org/bucket-sort-2/) | [Video](https://www.youtube.com/watch?v=7mahJ1axrR8)              
Radix:                           [Blog](https://www.geeksforgeeks.org/radix-sort/) | [Video](https://youtu.be/XdQXaHXmtzk)     

\-\> red-black trees(not  important) :- [https://www.topcoder.com/thrive/articles/An%20Introduction%20to%20Binary%20Search%20and%20Red-Black%20Trees](https://www.topcoder.com/thrive/articles/An%20Introduction%20to%20Binary%20Search%20and%20Red-Black%20Trees) 

\-\> pointers :- [https://www.scaler.com/topics/cpp/pointers-in-cpp/](https://www.scaler.com/topics/cpp/pointers-in-cpp/) ( very nice blog)  
[https://www.geeksforgeeks.org/dynamic-memory-allocation-in-c-using-malloc-calloc-free-and-realloc/](https://www.geeksforgeeks.org/dynamic-memory-allocation-in-c-using-malloc-calloc-free-and-realloc/) 

Data structure design based problems  
\-\> [https://leetcode.com/problems/design-hashmap/](https://leetcode.com/problems/design-hashmap/)   
\-\> [https://leetcode.com/problems/design-hashset/](https://leetcode.com/problems/design-hashset/)   
\-\> [https://leetcode.com/problems/lru-cache/](https://leetcode.com/problems/lru-cache/)   
\-\> [https://leetcode.com/problems/lfu-cache/](https://leetcode.com/problems/lfu-cache/)   
\-\> [https://leetcode.com/problems/insert-delete-getrandom-o1/](https://leetcode.com/problems/insert-delete-getrandom-o1/)   
\-\> [https://www.geeksforgeeks.org/find-maximum-in-a-stack-in-o1-time-and-o1-extra-space/](https://www.geeksforgeeks.org/find-maximum-in-a-stack-in-o1-time-and-o1-extra-space/)   
\-\>[https://www.geeksforgeeks.org/design-a-stack-that-supports-getmin-in-o1-time-and-o1-extra-space/](https://www.geeksforgeeks.org/design-a-stack-that-supports-getmin-in-o1-time-and-o1-extra-space/)   
\-\> [https://leetcode.com/tag/design/](https://leetcode.com/tag/design/) ( extra practise)

Some topics asked in interviews not common in CP  
\-\> Binary tree :- [https://www.youtube.com/watch?v=OYqYEM1bMK8\&list=PLgUwDviBIf0q8Hkd7bK2Bpryj2xVJk8Vk](https://www.youtube.com/watch?v=OYqYEM1bMK8&list=PLgUwDviBIf0q8Hkd7bK2Bpryj2xVJk8Vk)   
\-\> Linked list :- [https://www.youtube.com/watch?v=BkrePFaqaxw\&list=PLKZaSt2df1gz775Mz-2gLpY9sld5wH8We](https://www.youtube.com/watch?v=BkrePFaqaxw&list=PLKZaSt2df1gz775Mz-2gLpY9sld5wH8We)   
\-\> Tries :- [https://www.youtube.com/watch?v=dBGUmUQhjaM\&list=PLgUwDviBIf0pcIDCZnxhv0LkHf5KzG9zp](https://www.youtube.com/watch?v=dBGUmUQhjaM&list=PLgUwDviBIf0pcIDCZnxhv0LkHf5KzG9zp)

Low level design ( basics only not important)  
\-\> while dealing with such problems understanding of abstract class ( for c++) and interface for( java) is must, one should be proficient in principles of oops well, code quality also matters a lot.  
A good lld code follows SOLID principles, you dont need to dive deep into various design pattern of low level design, some basic exposure of standard problems and few basic design principles should do the job in most of the cases.  
\-\> Tip :-  for each topic and example/problems ask chatgpt, most of the video content covers system design in java, so for concepts you can refer the video but for code it’s very easy to get with chatgpt in c++.  
\-\> There is no single right answer for a Sytem design problem.  
\-\> System design consists of two part first part is HLD ( high level design ), idts any company ask this atleast company coming for on campus placements, second part is LLD ( low level design) very few company ask this in there interviews, like sprinklr , uber etc, if you are lucky you will not be asked about any problem related to this even the basic one, **mostly u will not need to answer this in interviews, but i will try to cover its basic as per my understanding for the worse case.**  
[Solid-Principles](https://www.freecodecamp.org/news/solid-principles-explained-in-plain-english/) ( most probably you wont be asked but since a good lld follows this, its knowledge is important while designing anything) | [https://www.youtube.com/watch?v=XI7zep97c-Y](https://www.youtube.com/watch?v=XI7zep97c-Y)   
Few design patterns which may not be asked directly but they can be helpful  
\-\> [Observer design pattern](https://www.youtube.com/watch?v=Ep9_Zcgst3U&list=PL6W8uoQQ2c61X_9e6Net0WdYZidm7zooW&index=5) |  [Blog](https://www.scaler.com/topics/design-patterns/observer-design-pattern/)   
\-\> [Decorator design pattern](https://www.youtube.com/watch?v=w6a9MXUwcfY&list=PL6W8uoQQ2c61X_9e6Net0WdYZidm7zooW&index=6) |  [Blog](https://www.scaler.com/topics/design-patterns/decorator-design-pattern/) 

Few standard problems   
Design a tic tac toe   
Design a snake and ladder game   
Design a chess game  
Design a elevator system  
Design a parking lot  
Design a coffee machine  

For the solution of these, i will suggest to use chatgpt, just write the problem statement and tell him to design this in detail having all the advanced functionality, and after answer of this ask him to write a detailed code as well, apart from that you can search online of there solutions as well. But remember there is not single right answer for such problems.  
You can refer this nice playlist as well  
[https://www.youtube.com/watch?v=rliSgjoOFTs\&list=PL6W8uoQQ2c61X\_9e6Net0WdYZidm7zooW](https://www.youtube.com/watch?v=rliSgjoOFTs&list=PL6W8uoQQ2c61X_9e6Net0WdYZidm7zooW) 

Language specific questions  
\-\> C :-  [https://www.geeksforgeeks.org/c-interview-questions/](https://www.geeksforgeeks.org/c-interview-questions/)   
\-\> C++ :- [https://www.geeksforgeeks.org/cpp-interview-questions/](https://www.geeksforgeeks.org/cpp-interview-questions/) 

HR interview prep   
\-\> [https://drive.google.com/file/d/1SYcsdthIkC\_yioySe66yh5-vgz1\_mwM3/view](https://drive.google.com/file/d/1SYcsdthIkC_yioySe66yh5-vgz1_mwM3/view) 

Interview bit question on any tech stack or cours  
[https://www.interviewbit.com/technical-interview-questions/](https://www.interviewbit.com/technical-interview-questions/) 

# **📊 Master Progress & Status Tracker**

| Subject | Core Focus Areas | Priority | Target Date | Current Status |
| :---- | :---- | :---- | :---- | :---- |
| **DSA**  | Data Structures & Algorithms | High | Date | In Progress |
| **OOPs**  | Object-Oriented Design & SOLID | High | Date | Not Started |
| **OS**  | Linux, Process Sync, Memory | Medium | Date | Done |
| **DBMS**  | SQL, Normalization, ACID | Medium | Date | Not Started |
| **CN**  | OSI Layers, TCP/UDP, DNS | Low | Date | Not Started |
| **System Design**  | HLD, DevOps & Microservices | Medium | Date | Not Started |

This plan is optimized for a **4–6 hour daily commitment**, focusing on building strong fundamentals and pattern recognition.

| Block | Duration | Focus Area | Action Item |
| :---: | :---: | :---: | :---- |
| **Morning / Deep Work** | 2.5 hours | DSA: New Concept & Practice | 1\. **Learn & Practice:** Master 1 new DSA pattern/concept. 2\. **Solve (Time Boxed):** Solve 2 Easy/Medium problems related to the new concept. **NO AI** during the attempt. 3\. **Log & Reflect:** Document your approach and sticking points in your tracker. |
| **Mid-Day / Core CS** | 1.5 hours | Foundational Subjects | 1\. **Conceptual Review:** Spend 45 minutes on one Core CS subject (OS/DBMS/CN) following the Core Focus Areas lists. 2\. **Practice:** Practice 5-10 SQL queries, review 1 LLD problem walk-through, or focus on a specific theory topic (e.g., Deadlocks). |
| **Evening / Review & Synthesis** | 1.0 \- 2.0 hours | Review & Mock Simulation | 1\. **Spaced Repetition:** Re-solve 1 problem from yesterday’s session faster. 2\. **AI Review:** Attempt 1 Medium/Hard problem, then use an AI tool to review your code quality and complexity (Mistake Analysis). 3\. **Weekend Focus:** Dedicate weekend time to a 1-hour Mock Interview. |

# **Handwritten DSA Notes**

# **Handwritten DSA Notes**

### **DSA Sheet Solutions & Prep**

* [ Striver's 180 questions solved.pdf](https://drive.google.com/file/d/1zfBXYy__LNTKm0qC0aszl1Zoqk_1UURm/view?usp=drive_link)  
* [SDE sheet striver solution .pdf](https://drive.google.com/file/d/1whEfWd7KQW7kXYXdzxuVRQz-PWFUW9zB/view?usp=drive_link)  
* [Striver DSA Sheet 3 Approaches Part 1.pdf](https://drive.google.com/file/d/1nwZ_VwbwSloOKFIps92Ce1irrlj5yEp0/view?usp=drive_link)  
* [Striver DSA Sheet 3 Approaches Part 2.pdf](https://drive.google.com/file/d/1x0TjNUP1r7HkKHhgSsz8Yi07m8cXn7Zo/view?usp=drive_link)

---

### **Recursion & Backtracking**

* [Striver\_Recursion-Backtracking-Notes.pdf](https://drive.google.com/file/d/1rNrWQiIUwGnecJNkv1hAaYOJ5Hq_6u3P/view?usp=drive_link)  
* [Recusrion & Backtracking Notes Animated.pdf](https://drive.google.com/file/d/1wQcSRGCRAPCt87WdrXcGBllzNoQR09xn/view?usp=drive_link)

---

### **Stacks & Queues**

* [Stacks & Queues Notes Animated.pdf](https://drive.google.com/file/d/1OEpohOV9yRf_ldmMLBfkKmtLbK2sjBsQ/view?usp=drive_link)

---

### **Trees**

* [Complete Notes of \_Free ka Tree Series\_.pdf](https://drive.google.com/file/d/1fh6mIEY2px80kFwDU-v79Yp-4Lqwzkjd/view?usp=drive_link)  
* [BinaryTree.pdf](https://drive.google.com/file/d/1akmaJUv_XwLkh0uHV-aOF60rzjKnTWoJ/view?usp=drive_link)  
* [Trees Part 1 Notes Animated.pdf](https://drive.google.com/file/d/1i8RhCKChChBr3kO_3_EkrmIbOPrgLDXi/view?usp=drive_link)  
* [Trees Notes Part 2 Notes Animated.pdf](https://drive.google.com/file/d/1QcY04yqscIRRdD2KlDYwsveCrw4aEgup/view?usp=drive_link)

---

### **Graphs**

* [Complete Notes of \_Striver's Graph Series\_.pdf](https://drive.google.com/file/d/1VxC98obMPzO63H4idPJ6IucIU2V1VCUS/view?usp=drive_link)  
* [Handwritten\_Notes\_of\_Graph\_Series\_Playlist\_of\_Striver\_Take\_You\_Forward.pdf](https://drive.google.com/file/d/1vF2Ufl4Ovh0oLOfCOnYaehQZjE_6WQnI/view?usp=drive_link)  
* [Graph Data Structure Notes 🔥.pdf](https://drive.google.com/file/d/1IP4MxEyi_qx_hAPi-jCWuZuwuBOp6Sq2/view?usp=drive_link)  
* [GRAPH NOTES.pdf](https://drive.google.com/file/d/1xCionLAdBZuhV0z9BRYG62dDbaKAzq3y/view?usp=drive_link)  
* [Graphs Part 1 Notes Animated.pdf](https://drive.google.com/file/d/1lQa1ZN2UFacCo2aEEIo-N-fLr08zIbHO/view?usp=drive_link)  
* [Graphs Part 2 Notes Animated.pdf](https://drive.google.com/file/d/12Luq-HYFXifYjMLhweJAA4g9JoLBukrY/view?usp=drive_link)

---

### **Dynamic Programming (DP)**

* [Handwritten\_Notes\_of\_Dynamic\_Programming\_Playlist\_of\_Striver\_Take.pdf](https://drive.google.com/file/d/1qWhASDAAPGRSRsHOhT1XLigGWcB1VCE8/view?usp=drive_link)  
* [Dynamic Programming Notes💡.pdf](https://drive.google.com/file/d/1zitXZEFA15ijJs8pTeX1YyMXyrupmCP8/view?usp=drive_link)  
* [Dynamic Programming Notes.pdf](https://drive.google.com/file/d/1pgME-lDNeyDDE4RJvfHmsL69QwBjSl-k/view?usp=drive_link)  
* [DP on Strings.pdf](https://drive.google.com/file/d/1aG26Kmif0JCqiSaDDWhWyXG5dvn28C_M/view?usp=drive_link)  
* [Dynamic Programming Notes Part 1 Aninated .pdf](https://drive.google.com/file/d/1rjF--EzRcaPDW5Qh1WcxwhcKAfZRW5Bq/view?usp=drive_link)  
* [Dynamic Programming Notes Part 2 Animated.pdf](https://drive.google.com/file/d/1yQdRgwTvPXu08nxEBE1GJGamXTaRdE-v/view?usp=drive_link)

# **Company Wise LC Qs**

# **Company Wise Leetcode**

This tracker provides direct access to curated interview preparation folders for various top-tier technology companies. Use these resources to focus your practice on company-specific patterns and frequently asked questions.

**2023 OA Screenshots:** [2023\_OA](https://drive.google.com/drive/folders/1gwzOS1cYQEg59mUG_y3ZuIRj8tSGoN1e?usp=drive_link)

| Company Name | Folder Link |
| :---- | :---- |
| Accenture | [📁 Accenture](https://drive.google.com/drive/folders/1B1I_7A_qicWJYwUhP-I23W4SiMlHTtIm) |
| Accolite | [📁 Accolite](https://drive.google.com/open?id=1e55A06Q_hRsafe_qK27sJ4ZN_RA2yXLq) |
| Adobe | [📁 Adobe](https://drive.google.com/open?id=1ymThHOSEnaYujMEyCe1IhC8JjjTUcD55) |
| Affirm | [📁 Affirm](https://drive.google.com/open?id=1mXnMZyjzl159h8Vs2pQ2Z-hXSB1j8bCI) |
| Agoda | [📁 Agoda](https://drive.google.com/open?id=1OmS0S452bjoqeExuHncKBKaICRkZwIAv) |
| Airbnb | [📁 Airbnb](https://drive.google.com/open?id=1L7ftl6Y2cEAUZktu88JqOyqYlktoIQwV) |
| Airtel | [📁 Airtel](https://drive.google.com/open?id=1OkUk-ul48FbYaATGwbmvWTB1MVtGEF6G) |
| Akamai | [📁 Akamai](https://drive.google.com/open?id=13II_F12yoLCH0BINCt_j-IWqyCm0XPuV) |
| Akuna Capital | [📁 Akuna Capital](https://drive.google.com/open?id=1SZGt3wrZ5o2yiQNcV7lM2XmE-3N-ZQqH) |
| Alibaba | [📁 Alibaba](https://drive.google.com/open?id=102rlImUPfn_lVFtFMXNPDboaro-4wmyx) |
| Altimetrik | [📁 Altimetrik](https://drive.google.com/open?id=1Vv7vNM4BTkDFaxq-3f5jmgDzpjF0OW0Q) |
| Amazon | [📁 Amazon](https://drive.google.com/open?id=1O40viCxLcGgyeXDG0qSpqHlVoi05YaIt) |
| AMD | [📁 AMD](https://drive.google.com/open?id=1zBl9lO0GB9RXGFl-UP_5xlSF2cDH3sP4) |
| Amdocs | [📁 Amdocs](https://drive.google.com/open?id=1nIi91V8qBgTRyRdsvMHwKbHtK0rHmRbO) |
| American Express | [📁 American Express](https://drive.google.com/open?id=1SHpoKGNRZllW1oiwFpEBBcnAmIPWEEy7) |
| Anduril | [📁 Anduril](https://drive.google.com/open?id=1cmXFfNFms4NknFfab6TbdcYFePjPPy0t) |
| Apple | [📁 Apple](https://drive.google.com/open?id=1pNcJF5mtiD3bh9riILRuYv3sPHyz01Ql) |
| Arcesium | [📁 Arcesium](https://drive.google.com/open?id=1Sfq1IwFxCNk6IeDpyuoNimQG2Xwm66GQ) |
| Arista Networks | [📁 Arista Networks](https://drive.google.com/open?id=14QU7oPNiWGBFptSMzSF60tYUFJRdq9XX) |
| athenahealth | [📁 athenahealth](https://drive.google.com/open?id=1JRjW68yghV0JmBuFL8hzeQ_x9gqpOJ2h) |
| Atlassian | [📁 Atlassian](https://drive.google.com/open?id=1MlD0pCtiUmyP72g9P7Wd53OhAitUJ0ka) |
| Attentive | [📁 Attentive](https://drive.google.com/open?id=1R0YxBju55voFpxweH9-bpNY1RJI6T83f) |
| Autodesk | [📁 Autodesk](https://drive.google.com/open?id=1ajkGnMluLK6keT5wQqy4a-hLteUvDtnI) |
| Avito | [📁 Avito](https://drive.google.com/open?id=1OyXCRpzWr4n5aS7C4OqguWE82CyXhESd) |
| Baidu | [📁 Baidu](https://drive.google.com/open?id=1sgDFFy6CmI6J8ECGebMlyS8ba0La27cd) |
| Barclays | [📁 Barclays](https://drive.google.com/open?id=1YoT09H5UoTDz_uNYOUdav36xg1DNWYsh) |
| BitGo | [📁 BitGo](https://drive.google.com/open?id=16BnHHrWS4zgOWPbI0mqb55Sss8Os6LG_) |
| BlackRock | [📁 BlackRock](https://drive.google.com/open?id=1Bldaf6FLkcCSYabxjIztfjSRyxpivmv1) |
| Blizzard | [📁 Blizzard](https://drive.google.com/open?id=1Gb7n9lbVuK_l8tS_cC6BI8g53Yuq_YlZ) |
| Block | [📁 Block](https://drive.google.com/open?id=1VrSUzHj83GTUwl2Ky9OjrZjctjq4PICx) |
| Bloomberg | [📁 Bloomberg](https://drive.google.com/open?id=11I-PhoKzuqml1S6RXuylyYmnI5yhBw6k) |
| BNY Mellon | [📁 BNY Mellon](https://drive.google.com/open?id=1pVsyDiWC7QWBxKr2NfXgTokGk3beohNW) |
| Bolt | [📁 Bolt](https://drive.google.com/open?id=15dt9f6As39xcRFaoRZGPGc1QhscOv7X6) |
| Booking.com | [📁 Booking.com](https://drive.google.com/open?id=108N3BPpScdK8AS6x_xwT68P2IuI40AdA) |
| Box | [📁 Box](https://drive.google.com/open?id=1nCbilEA5D1KL7A7jeIXnSxe-VI-5stDI) |
| BP | [📁 BP](https://drive.google.com/open?id=1pO1rNsGw3EWSclIkRitIrc-FriHT_Bpn) |
| ByteDance | [📁 ByteDance](https://drive.google.com/open?id=1bEW6WTQr2L6Oez-_PNfqyYmMrds2PfPH) |
| Cadence | [📁 Cadence](https://drive.google.com/open?id=1VG0U-wqDSEA-32KuEYwGbHi85ZFYXZ8z) |
| Capgemini | [📁 Capgemini](https://drive.google.com/open?id=1ukBfQDY4PRTFyuPf47NsFcbHYKnrc13J) |
| Capital One | [📁 Capital One](https://drive.google.com/open?id=1AuzX-UQfm4Vz9JNa6eLQkgdij7JvG1SC) |
| CARS24 | [📁 CARS24](https://drive.google.com/open?id=1Z8diux4Z0-7qIbAoEM4jOi2UwGZEuNkO) |
| carwale | [📁 carwale](https://drive.google.com/open?id=1wvo4TtnYimvzR6Md9O7kDPbf_o0wkwrn) |
| Cashfree | [📁 Cashfree](https://drive.google.com/open?id=1UL2W1Mm3OIZrBQG2JCqze47-ga1g68XK) |
| Chewy | [📁 Chewy](https://drive.google.com/open?id=1j4YMMVCQ7aqsuf1enajMBnkP5eiE5QfU) |
| Cisco | [📁 Cisco](https://drive.google.com/open?id=18dsRPtaCh-yaNEbIkslxieGraeV-ekXs) |
| Citadel | [📁 Citadel](https://drive.google.com/open?id=18INK9y9bxlwwBi2aays4cn71DBfdPap7) |
| Citrix | [📁 Citrix](https://drive.google.com/open?id=1P-00g9YbG_cc8yfvnccp3JPGUoIt9jC4) |
| Cloudera | [📁 Cloudera](https://drive.google.com/open?id=1lIMWrOgz94OsZTOIOMw3pBh1LtkwBKuO) |
| Cloudflare | [📁 Cloudflare](https://drive.google.com/open?id=1GUYdtTSsC-lMFdZ45cml0ETarEbWlM8S) |
| Cognizant | [📁 Cognizant](https://drive.google.com/open?id=1QRt7enfBjfUxjyCbge0WoIChkY3A3WpD) |
| Coinbase | [📁 Coinbase](https://drive.google.com/open?id=1JnL1HT1zDo8SvL0P0SrzlvBcnl0NiaZw) |
| Commvault | [📁 Commvault](https://drive.google.com/open?id=1YBKvsIgfBoTqtKZyQZwZJpNbGdZQThVh) |
| Confluent | [📁 Confluent](https://drive.google.com/open?id=1rFGqkzD1HAEYOaLSN3fBuUi6LUwU6oFm) |
| ConsultAdd | [📁 ConsultAdd](https://drive.google.com/open?id=15LeiyrtvBPjUy4N2Duc7QcfUi90uek7L) |
| Coupang | [📁 Coupang](https://drive.google.com/open?id=1X_JSkAJdV_tafllLOMpcQqh-fzgUymx6) |
| Coursera | [📁 Coursera](https://drive.google.com/open?id=1IA44btX6NiGdZkFh8I3nVP5qgKrl1Htd) |
| CrowdStrike | [📁 CrowdStrike](https://drive.google.com/open?id=14WLwlcA8dO4f7fHdxbDDWu6-I2oGeA8B) |
| Cruise | [📁 Cruise](https://drive.google.com/open?id=18-77bPsLyGYaGQixJYKSdjva45tZJBtC) |
| CureFit | [📁 CureFit](https://drive.google.com/open?id=1UT3465HRfiDCaYxcbEj---T1io2HfmrN) |
| Darwinbox | [📁 Darwinbox](https://drive.google.com/open?id=1RuVuTHHa6YeFOnsWi-wlByY6qbCYGSnN) |
| Databricks | [📁 Databricks](https://drive.google.com/open?id=1cG94y_tzFeFistNoNkkdcvUV_xYPj1AY) |
| Datadog | [📁 Datadog](https://drive.google.com/open?id=16dBrKhP-y3oYPomiD4zM9Lmi0TTwlC7Y) |
| DE Shaw | [📁 DE Shaw](https://drive.google.com/open?id=1jOPmLReAur38igktceGfl4qIRmfUST1l) |
| Deliveroo | [📁 Deliveroo](https://drive.google.com/open?id=1PtZB8o-VrR-LAHNNx4hPfG7tfJCawDXU) |
| Dell | [📁 Dell](https://drive.google.com/open?id=1YunIQMdWo099dfNH2FuLRlXoDRshbiI1) |
| Deloitte | [📁 Deloitte](https://drive.google.com/open?id=1BYLd-0DuP8p5ESstuS11U1B0Q67lDrxx) |
| Deutsche Bank | [📁 Deutsche Bank](https://drive.google.com/open?id=1c6q9zT4ygYwQbJcsTCasANUqouPd-fed) |
| DevRev | [📁 DevRev](https://drive.google.com/open?id=1lfDQxgZmbBbDt3MsLPX-BBbENEYSjv8v) |
| Directi | [📁 Directi](https://drive.google.com/open?id=10tGu45Y8eXHopN0twNK4bBERdpdynN6V) |
| Disney | [📁 Disney](https://drive.google.com/open?id=15pTmj2R_QU6-022nJj0h0i_B1niH19HX) |
| Docusign | [📁 Docusign](https://drive.google.com/open?id=1jI-1ySHGzBgZkKD2OpCTi33lfyKS1lQD) |
| DoorDash | [📁 DoorDash](https://drive.google.com/open?id=1UCUCDqh_ItvPAjFX32lurPw-yhu8122W) |
| DP world | [📁 DP world](https://drive.google.com/open?id=1WpsdyTQlnjYQbje5tOeEwWUTx6beBufm) |
| Dream11 | [📁 Dream11](https://drive.google.com/open?id=1JjftIecvW9MoIV2CammBRdekSznibsDC) |
| Dropbox | [📁 Dropbox](https://drive.google.com/open?id=1bvxVUnG0ZC31wWoRagHc_f5INTOVPVsE) |
| DRW | [📁 DRW](https://drive.google.com/open?id=1raEuHYpvLq10apgRbMWzrQobZmkkCC5w) |
| Dunzo | [📁 Dunzo](https://drive.google.com/open?id=11tWfWUNTx3U1j98qOv48kclw6ZZtkJG_) |
| eBay | [📁 eBay](https://drive.google.com/open?id=1mhtqaQ01qhu5Q8b8ph286iOEqhbv_tcE) |
| EPAM Systems | [📁 EPAM Systems](https://drive.google.com/open?id=1WkcKYvN1lUujGBr0kkw1sh0HHhcQd3WO) |
| Epic Systems | [📁 Epic Systems](https://drive.google.com/open?id=1IOiloxbYYAyidh4VcJ1aFNyLQomhrrJa) |
| Expedia | [📁 Expedia](https://drive.google.com/open?id=1c46wiwLnpAlVBNRebjL-3yESzibG-fiR) |
| FactSet | [📁 FactSet](https://drive.google.com/open?id=11PEQ3OCneCPgfWTNAeY6QjpLUTBGIdmI) |
| Flexport | [📁 Flexport](https://drive.google.com/open?id=1TodRBv5thGicMM5kOjPWIBrpI0KOk_bj) |
| Flipkart | [📁 Flipkart](https://drive.google.com/open?id=1tA0-Lm9LgC5lu2j3HyrSzq-HI2rMwvGI) |
| FreshWorks | [📁 FreshWorks](https://drive.google.com/open?id=1sNyE5iH6nrePk1lPCnW6iOCFwmE3vlgA) |
| GE Healthcare | [📁 GE Healthcare](https://drive.google.com/open?id=1o2xRu85kRfYt8u_TLnM0xGUbVS_6h6g_) |
| Geico | [📁 Geico](https://drive.google.com/open?id=1NElOv4JOpbbh_C9_igFkuI3Sp1sqQi9C) |
| Gojek | [📁 Gojek](https://drive.google.com/open?id=1l6-VKuaKe6xebR65Jm8TZQtCgYe8IAVO) |
| Goldman Sachs | [📁 Goldman Sachs](https://drive.google.com/open?id=1I92o5HDSfjOABW8b4ssCA5YoxGxCcAyU) |
| Google | [📁 Google](https://drive.google.com/open?id=1rUkxD-dn7V6Oxy3CmmOYqhzGmB-xhCm3) |
| Grab | [📁 Grab](https://drive.google.com/open?id=1GNmBefJQ9H38FP4jn-DsPingHy5-kW81) |
| Grammarly | [📁 Grammarly](https://drive.google.com/open?id=1n1MtKP3mFAb3ZSfmrFSmPANCuLOHlIcp) |
| Graviton | [📁 Graviton](https://drive.google.com/open?id=1Rm8glxj8QuOZFqjE7FYn94bzdTWPGW5t) |
| Groww | [📁 Groww](https://drive.google.com/open?id=1P9OYyoOKKgxSHBC51LZGsZVjPTXytiiK) |
| GSN Games | [📁 GSN Games](https://drive.google.com/open?id=1i0GclaCvhNNEkCr-hpDX5w0lWyH2EEee) |
| HashedIn | [📁 HashedIn](https://drive.google.com/open?id=1NF_fK3EXTpqSu-0aGNxzWClo5gl-lrtz) |
| HCL | [📁 HCL](https://drive.google.com/open?id=1eIucsYKlrIdE383jgtpaWsS0HyAFSKmU) |
| HPE | [📁 HPE](https://drive.google.com/open?id=1Fl8TF2dkPeYAC69b9BTpfPhIpVhwjZFT) |
| Hubspot | [📁 Hubspot](https://drive.google.com/open?id=1p8D38axQPaKd59SLPJHlAQWZnZtymeJa) |
| Hudson River Trading | [📁 Hudson River Trading](https://drive.google.com/open?id=1qqEIMNwqs9lRD6qMKiKoamAmSNIKTcbP) |
| Hulu | [📁 Hulu](https://drive.google.com/open?id=1LwaYsQ-PaMdU_hKCZLGZ6ZaKWH1KI2HE) |
| Huawei | [📁 Huawei](https://drive.google.com/open?id=1mpDKO06oQjmjKI5RucINEiMdYv5Ldlia) |
| IBM | [📁 IBM](https://drive.google.com/open?id=1f4oi1Va8PCuwV41N0uWF_xRoh-7uvKcQ) |
| IMC | [📁 IMC](https://drive.google.com/open?id=13TGyWDqwjJTABpglDIookAI8UpSzXjNL) |
| Indeed | [📁 Indeed](https://drive.google.com/open?id=1qfiHI4GgUnaGC7UTqZBHE1Ut_JgQkD86) |
| InMobi | [📁 InMobi](https://drive.google.com/open?id=1fmrIUF0Df9YewiQwzGUi5hWw1-jjGoAu) |
| Infosys | [📁 Infosys](https://drive.google.com/open?id=1wv6jOaJNOIrlyeE6vrxfYuth7jg5MBwk) |
| Instacart | [📁 Instacart](https://drive.google.com/open?id=19l97Td5oGFgS6C3dPtPkTgiO1VM4-o95) |
| Intel | [📁 Intel](https://drive.google.com/open?id=1TeHV9T-OWRHniXS9L9BT73UN04BKfbb_) |
| Intuit | [📁 Intuit](https://drive.google.com/open?id=1emCnYYpKOFvV7gbhH2_cIoBEASGV7PB1) |
| IXL | [📁 IXL](https://drive.google.com/open?id=1Cqg6QmdA0oJhJaC2U11p-CTbb0DivaQ1) |
| J.P. Morgan | [📁 J.P. Morgan](https://drive.google.com/open?id=1FT18CfuevWF0AJWEFCPXBj3l1KmpjJVU) |
| Jane Street | [📁 Jane Street](https://drive.google.com/open?id=1vqQeZQ59v5qfULXhtGL039u-CEpxFJ4o) |
| jio | [📁 jio](https://drive.google.com/open?id=1Yo4kkklPINCXJ0Ho6qIZBdrhMkl6mLQv) |
| josh technology | [📁 josh technology](https://drive.google.com/open?id=11dW0T8kukjOhQSyN_szxIReTeEMEtAlH) |
| Jump Trading | [📁 Jump Trading](https://drive.google.com/open?id=1NRp1me7kcm2AIUAz_BZTMp97IJFPjMGu) |
| Juspay | [📁 Juspay](https://drive.google.com/open?id=1WB4o6brprQUIeuaCx4tt66Odq2gpVf2q) |
| Karat | [📁 Karat](https://drive.google.com/open?id=1Neu-NiNMdwuRb8v2-E9pf9l2ujq0f4Ps) |
| KLA | [📁 KLA](https://drive.google.com/open?id=17uBqBgcFsEWoBdjHKXUEDIWJGpwwDx8n) |
| LinkedIn | [📁 LinkedIn](https://drive.google.com/open?id=1uu_04_zuaDxqEofLZnPWDErlqtn7SAyt) |
| LiveRamp | [📁 LiveRamp](https://drive.google.com/open?id=1TZSlJlOaeX65P_kyNeYPclI0VVN8zkGZ) |
| Lowe's | [📁 Lowe's](https://drive.google.com/open?id=1RJP3q122bPKIxQbUd-m-LLpt2wRpvlhB) |
| Lucid | [📁 Lucid](https://drive.google.com/open?id=1jU7CAw-6UFpfyk5vInqrMSg2lXCcrIGX) |
| Lyft | [📁 Lyft](https://drive.google.com/open?id=1K6l7QrWx29gtKddVANmla782OVpySyhU) |
| MakeMyTrip | [📁 MakeMyTrip](https://drive.google.com/open?id=1w0nfhNHbYyx3AXejG0-VJ6hvy9DReIbL) |
| Mastercard | [📁 Mastercard](https://drive.google.com/open?id=1z6dGcWWST4bvF2rD4S7-jWx1A7DvoK8G) |
| MathWorks | [📁 MathWorks](https://drive.google.com/open?id=1Pfq673YsY2UOBJd4qtMeP2dSNPS3AuMj) |
| Media.net | [📁 Media.net](https://drive.google.com/open?id=196ML5Bl9puhzkkwXWFocFy4w7YlwDLRt) |
| Meesho | [📁 Meesho](https://drive.google.com/open?id=1Mvl0-UeYun-HzhxdLZTRWeb_0pU_1K-G) |
| Mercari | [📁 Mercari](https://drive.google.com/open?id=1mmVmI81II0HOvNPXmKuJm_7NFepZ4Bfn) |
| Meta | [📁 Meta](https://drive.google.com/open?id=1qpF82wSIRKT7QOrz9EZ-3HIpTKNaEFHz) |
| Microsoft | [📁 Microsoft](https://drive.google.com/open?id=1Cq3COb0qfJq3rPvxfQqkjxOGXZAmoYeW) |
| Millennium | [📁 Millennium](https://drive.google.com/open?id=1rBYzwqBf9uTxziqDHBrZjn4Uq10gtABL) |
| Mitsogo | [📁 Mitsogo](https://drive.google.com/open?id=1q1SOZVz4BDOeeEYwOFIgs4J72w-577TJ) |
| Moloco | [📁 Moloco](https://drive.google.com/open?id=1PvlNVAYyqWN-gZzDsnhW7digrtKu0c5r) |
| MongoDB | [📁 MongoDB](https://drive.google.com/open?id=1aRP9zx42h6awb9o52QDb0RqSp5eQuK99) |
| Morgan Stanley | [📁 Morgan Stanley](https://drive.google.com/open?id=1Lqwd8sQaTLhUpMuHhEvSn9TzbP2BBs06) |
| Moveworks | [📁 Moveworks](https://drive.google.com/open?id=16f7e7DFi2-RIcSgw12tPzfxLs2WdpV4g) |
| Myntra | [📁 Myntra](https://drive.google.com/open?id=1zp3TgXu0Uwg9XYuIfDMbF0MbHx6ZS4lU) |
| Nagarro | [📁 Nagarro](https://drive.google.com/open?id=14_S96j3GbMeq0duPNAOXZ55K5n7bkHC_) |
| NetApp | [📁 NetApp](https://drive.google.com/open?id=1GEdVSZ_vYDSdiZbRsqa2I18Wh16fxluq) |
| Netflix | [📁 Netflix](https://drive.google.com/open?id=16rH4hanKNbcMhaO5JuzGWVnAv4MtnTV9) |
| Nextdoor | [📁 Nextdoor](https://drive.google.com/open?id=1oEGHLen58fUEilt1LUPWQVGipQV25JCd) |
| Niantic | [📁 Niantic](https://drive.google.com/open?id=1EOx0u1sbRfMAtJ8OYqn2oh34T-aifQBq) |
| Nielsen | [📁 Nielsen](https://drive.google.com/open?id=1tcCq_KVvAoDS7kwrRxoBE7UQfPhgZYep) |
| Nike | [📁 Nike](https://drive.google.com/open?id=131lsD_IcCgybEq0zKQOLMl6-z7yOGWNb) |
| Nordstrom | [📁 Nordstrom](https://drive.google.com/open?id=1w6z37jJS-jBiAr9kT0pPAjvNg7Bp19YI) |
| Nutanix | [📁 Nutanix](https://drive.google.com/open?id=1uXBc9qX4lIc23O5SULEtXhS4Rz_qZsay) |
| Nvidia | [📁 Nvidia](https://drive.google.com/open?id=14FEf44knSilEmS-oKSDjcJnBVAuDCy9X) |
| Okta | [📁 Okta](https://drive.google.com/open?id=1OspMMNdRqCRtD-RX_aHzk4XlT7scD2LC) |
| OKX | [📁 OKX](https://drive.google.com/open?id=1Mapo_qWdwzKSlYJYcDtGFY-iYCoqgMEJ) |
| OpenAI | [📁 OpenAI](https://drive.google.com/open?id=1VxLbWedrwnzS6MsBMUSh0fU3P80Y4ntW) |
| opentext | [📁 opentext](https://drive.google.com/open?id=1zatwWKUMP69tla6BEdvp5iQXj2BbraWD) |
| Oracle | [📁 Oracle](https://drive.google.com/open?id=1xFw8INWIhhvK1WgVCc8GIrhbruuv813y) |
| Otter.ai | [📁 Otter.ai](https://drive.google.com/open?id=1h2Cz7B3m30FkceRTYRRVTL92DSrGOgh5) |
| oyo | [📁 oyo](https://drive.google.com/open?id=19qfDvM-pBw3p2HZwzFqlBgK8YwKeaiQi) |
| Ozon | [📁 Ozon](https://drive.google.com/open?id=10alqlYTV8BHjBU6HN3v6Qg6epPOooTwi) |
| Palantir Technologies | [📁 Palantir Technologies](https://drive.google.com/open?id=1Aur4unwTu5mnlf-XuUtlAg44EjrVm58P) |
| Palo Alto Networks | [📁 Palo Alto Networks](https://drive.google.com/open?id=1v2EOr1yKcBb4zN6_cl4zSgPpKdaZQYhJ) |
| PayPal | [📁 PayPal](https://drive.google.com/open?id=1PskhlSn8-gQbKb4R4s1v1TGZDjZQ4dqW) |
| Paytm | [📁 Paytm](https://drive.google.com/open?id=1eRoyC6bbQ9XlOlEz__DVRBI8xrepRgiS) |
| persistent systems | [📁 persistent systems](https://drive.google.com/open?id=1AdlU1ml5dvYK12Us_C8FiGBr2wIj_D-3) |
| PhonePe | [📁 PhonePe](https://drive.google.com/open?id=1j9pSVd8sgmXwspBnK396Jzn7Oh92A6sC) |
| Pinterest | [📁 Pinterest](https://drive.google.com/open?id=1ksX-03tdaDNba0zcMTzwozAxD5m_pCq8) |
| Pocket Gems | [📁 Pocket Gems](https://drive.google.com/open?id=1h7Yd36xWBg4FqjWICYgwLX8RxhLQwW-H) |
| Point72 | [📁 Point72](https://drive.google.com/open?id=1mgHI1x3kU5OCih2ZA7qHxMvaGZzMvxdo) |
|  |  |
| Pure Storage | [📁 Pure Storage](https://drive.google.com/open?id=1nj0pxoMNiZ7QD77T3QlnQSb1SSQy9PbE) |
| Qualcomm | [📁 Qualcomm](https://drive.google.com/open?id=1UhFhWBPzqy7onkduX74I8k2TDmvSaA5Z) |
| Quora | [📁 Quora](https://drive.google.com/open?id=1pykM0jvgXGOfy6RqFPTuY0bA3frWbBgK) |
| Rakuten | [📁 Rakuten](https://drive.google.com/open?id=1ayblEYrBIQ0LcfChfVBgu5mlqx0z6wAJ) |
| razorpay | [📁 razorpay](https://drive.google.com/open?id=1qjboDiNTXoiSMVe9m9dQ68Sbgo-GIApI) |
| RBC | [📁 RBC](https://drive.google.com/open?id=1eb5mHLur1akFMxjJgzpPsyYrpaGZoFnj) |
| Reddit | [📁 Reddit](https://drive.google.com/open?id=1drnGTzXgkG3cPw_VQU9RIWNZqN9JnI9Y) |
| Revolut | [📁 Revolut](https://drive.google.com/open?id=17JFv9aaiStdvLk9b8Y55FQLC5X-w6Kjs) |
| Ripple | [📁 Ripple](https://drive.google.com/open?id=1w3QxGf_CS7Pp6QtbBIyQBfYdf0jq9XU2) |
| Rippling | [📁 Rippling](https://drive.google.com/open?id=1yw1xZLxC0B1s5UuEC0O1WrTUmw9jYC6h) |
| Roblox | [📁 Roblox](https://drive.google.com/open?id=12e3TnK6rC5D1uqMzJYeAW03ivCC9zCac) |
| Robinhood | [📁 Robinhood](https://drive.google.com/open?id=1jbnnGw8i1DnV9KhmzA8IWtjBdwbfF32f) |
| Roku | [📁 Roku](https://drive.google.com/open?id=17I5MOFiqKNd2a77v1eCJFmVG9Ivcg9Ty) |
| Rubrik | [📁 Rubrik](https://drive.google.com/open?id=15KMqxoxKKL9ChVILnz37N1CvPSapSKdc) |
| Salesforce | [📁 Salesforce](https://drive.google.com/open?id=1zlOKITmzK8v9aOAnSAlOACpI6cUUz4ei) |
| Samsara | [📁 Samsara](https://drive.google.com/open?id=19qCdEJqg5dBlY40RyJh_W9w3zq854vRx) |
| Samsung | [📁 Samsung](https://drive.google.com/open?id=1uH35q9eu7lp67bYGtUCQJTG6h0kWD4JF) |
| SAP | [📁 SAP](https://drive.google.com/open?id=19OeV9pSp5mQYis8AO3DRhFUW2fTIIBS_) |
| ServiceNow | [📁 ServiceNow](https://drive.google.com/open?id=1ETx9ZJsO5EV5DEIOxuCl6vxEgeRrm-mX) |
| Shopee | [📁 Shopee](https://drive.google.com/open?id=1-c5u-2ivhXG9feQ4XZ5sk-ksqvt-PVIl) |
| Shopify | [📁 Shopify](https://drive.google.com/open?id=17aW6xfNL-8Q7Arhe-TQTPZ9lDq1n10KA) |
| SIG | [📁 SIG](https://drive.google.com/open?id=1_A_3WiAQKJ9DL7_-TQxiPO2E6ZQ9d3wG) |
| Sigmoid | [📁 Sigmoid](https://drive.google.com/open?id=1DIQLhySMJXMgFqENub1B2yJPm5i4xRky) |
| Siemens | [📁 Siemens](https://drive.google.com/open?id=1D7LaH_uB4MuAVS93XoYLQohB2C1AGufg) |
| Snap | [📁 Snap](https://drive.google.com/open?id=15nvIhF0M6YX_ei4dM0Qq3C-mlFDJGIS4) |
| Snowflake | [📁 Snowflake](https://drive.google.com/open?id=1vC1XV4aw5-5qZvgfw3gpNpj1jn4Z5UUN) |
| SoFi | [📁 SoFi](https://drive.google.com/open?id=1HNoZYeTG0TucwxevHA8M3yVrh29YBNXN) |
| Spotify | [📁 Spotify](https://drive.google.com/open?id=1IqR4KWBwbYI-nQVzXr1Wo2UW-ol0DURb) |
| Sprinklr | [📁 Sprinklr](https://drive.google.com/open?id=1S0VqY1MzRFMeEBmhOVmtPwFjA-qbs8Gi) |
| Squarepoint Capital | [📁 Squarepoint Capital](https://drive.google.com/open?id=1PG4d_th1kXEKHFVfudj2QfJ-FIRwCcCh) |
| Stripe | [📁 Stripe](https://drive.google.com/open?id=1nwtSogJ_oC-kJyW9vl26YXPxyd6uL3pw) |
| Swiggy | [📁 Swiggy](https://drive.google.com/open?id=1u-Bior_3FRpbuQySr2U0XJsTYuzpXeyc) |
| tcs | [📁 tcs](https://drive.google.com/open?id=1RONae-Cv4RgHCdYH1d0uIYhbBffYfTSp) |
| Tekion | [📁 Tekion](https://drive.google.com/open?id=1Gd70Q_18YWqLQAExqWDGBOVoOVdgEdI8) |
| Tencent | [📁 Tencent](https://drive.google.com/open?id=1QdD6CXZ9bOmIxP7tFRE8ESC-os7SMMru) |
| Tesla | [📁 Tesla](https://drive.google.com/open?id=1L-AI8VOE3PTAacoSAbvmhugNQb1VN8mc) |
| thoughtspot | [📁 thoughtspot](https://drive.google.com/open?id=1sinVL3iKCh7C4WGZAX8fWnbaadAyGs1Y) |
| ThoughtWorks | [📁 ThoughtWorks](https://drive.google.com/open?id=1DIY1_HBtjS6DyNLLzxUa-0dvHMPKnI97) |
| TikTok | [📁 TikTok](https://drive.google.com/open?id=1Ih6hFhSjzMACN0rD_otnxGu2S-aurKcW) |
| Tinkoff | [📁 Tinkoff](https://drive.google.com/open?id=1WkRw0MbrKGSqTFHdsgUyCsuC9RKj57VY) |
| Trilogy | [📁 Trilogy](https://drive.google.com/open?id=1yV2hZaIizoEsS-rcRyM3pXA8bpoV98Lz) |
| Turing | [📁 Turing](https://drive.google.com/open?id=1pxNf8FVHdSJDGbQ1Zl8gQXU08GaavdeP) |
| Turo | [📁 Turo](https://drive.google.com/open?id=1igDv7_P5wfEqvv9qmOZR361ibmGOU-bI) |
| Twilio | [📁 Twilio](https://drive.google.com/open?id=1mltU3UiYFPmCWZe8qbxCUAXMh1yN6zR4) |
| Twitch | [📁 Twitch](https://drive.google.com/open?id=1TNaNTxaFmQMdRrCw9T0kfML88KbeP_2Z) |
| Two Sigma | [📁 Two Sigma](https://drive.google.com/open?id=1ybslELn-ItntUf_wi7rRxyanrIJpFwk3) |
| Uber | [📁 Uber](https://drive.google.com/open?id=1SIEklWjYlr5Gc0LaPz5CSdF_F422ML36) |
| UiPath | [📁 UiPath](https://drive.google.com/open?id=1rAt2W6RfGkj7QlK0Zbaa7gq_wKHz8Ha9) |
| UKG | [📁 UKG](https://drive.google.com/open?id=151loznXD1o_m7m-oVWQAX8I4n69LaHnj) |
| Veeva Systems | [📁 Veeva Systems](https://drive.google.com/open?id=1IEimNA0YrHUvHNHqNfvJbgbujw5kY4sA) |
| Verily | [📁 Verily](https://drive.google.com/open?id=1ZWaNBVharCz2Xz5PLIkCH2CazmdTO30W) |
| Verkada | [📁 Verkada](https://drive.google.com/open?id=1A2aKbJxgt7MovjpXDCB7QfE5v4AtiMZ4) |
| Virtu Financial | [📁 Virtu Financial](https://drive.google.com/open?id=14PkavVKWDmwkAFp9domDFFBiJSNMLXdi) |
| Visa | [📁 Visa](https://drive.google.com/open?id=1Y1ebUCg8TTy1UmAZhQmKww0syGZQlubW) |
| VK | [📁 VK](https://drive.google.com/open?id=1Gq5mNms0QVyjktVsx89mD_eDpB7a9f0U) |
| VMware | [📁 VMware](https://drive.google.com/open?id=1QLTFe5NQxKeusWYQjB8CI3lcddbh48YE) |
| Walmart Labs | [📁 Walmart Labs](https://drive.google.com/open?id=1FkivLwgz-h0PO_tD_yo_Uo_Oi9LODquW) |
| Warnermedia | [📁 Warnermedia](https://drive.google.com/open?id=170Exk2Exjlgj-Vn2QGnTHOzzh0OOqUmI) |
| Wayfair | [📁 Wayfair](https://drive.google.com/open?id=1oDi_d2Trf-Qwl5GHWTHdtJu2Bo3sSvDj) |
| Wells Fargo | [📁 Wells Fargo](https://drive.google.com/open?id=113tb7SpLzGqoq9gAQuAPExhl99BDKZ-k) |
| Wipro | [📁 Wipro](https://drive.google.com/open?id=1ZD8KjdXGuUN7sjbGqIq5DMRDLkASkwR4) |
| Wix | [📁 Wix](https://drive.google.com/open?id=1R7zThUb0UN2sC0JG8FJVN1YD4SDSyolr) |
| Workday | [📁 Workday](https://drive.google.com/open?id=1MMhcRgznnyBWrhHlGujeTnkIcyy1Ug7J) |
| X | [📁 X](https://drive.google.com/open?id=1vpStl0N4AVhXaWhjUtDGTHEcAAeZJWY2) |
| Yahoo | [📁 Yahoo](https://drive.google.com/open?id=1OBM9GgpBYf21j0X6TlilbQkWALy5UKje) |
| Yandex | [📁 Yandex](https://drive.google.com/open?id=1HH19KmKd2dRjf6VzGuNN7CyEwjAJNJKn) |
| Yelp | [📁 Yelp](https://drive.google.com/open?id=143hJUxuZm0k-Soa4CTJbkDnjiCS8vPaR) |
| Zalando | [📁 Zalando](https://drive.google.com/open?id=1nbV-67nTF3vn-boROuXcWiGaR6pLpr85) |
| Zenefits | [📁 Zenefits](https://drive.google.com/open?id=1xurrETZzSenQyfXdUTuBLX6gYFJtfxT0) |
| Zepto | [📁 Zepto](https://drive.google.com/open?id=1t_oN8fKVNrB7hlIHkEFUb3mGD91Lo7Pb) |
| Zeta | [📁 Zeta](https://drive.google.com/open?id=1xAGmVFqzigGV7ss48atYYplL0MuApFnJ) |
| Zillow | [📁 Zillow](https://drive.google.com/open?id=1rpz7vUQRn3gCwjsxOhobSk5f5lR8nsHv) |
| Zoho | [📁 Zoho](https://drive.google.com/open?id=1bWIaqJGqER5DRE6UPnP1nOLn4kvkt_R2) |
| Zomato | [📁 Zomato](https://drive.google.com/open?id=11tC_ZRqWkLeXZ3fOjYDC4mcWm7vqc2c0) |
| Zopsmart | [📁 Zopsmart](https://drive.google.com/open?id=1rgR22zpeQQavJROLU-AdsNICq2hpAyjz) |
| ZS Associates | [📁 ZS Associates](https://drive.google.com/open?id=1yIXAkOaMtSqCqqHW-SgaRxYoOME7otsd) |
| ZScaler | [📁 ZScaler](https://drive.google.com/open?id=1QZOIoh3AIoR8r4dBDt6JENe_V1_Vra7P) |

# **DevOps Resources**

## **Resources to learn cloud**

* **Docker Internals:** [learndocker.online](https://learndocker.online/) (Free, structured, and deep-dive)  
* **Kubernetes Core:** *Kubernetes in Action* by Marko Lukša (Excellent for deep conceptual understanding) [Manning Publications](https://learning.oreilly.com/library/view/kubernetes-in-action/9781617297618/)  
* **Local K8s Testing Tools:** [k3s.io](https://k3s.io/) or [Orbstack](https://orbstack.dev/) (Lightweight alternatives to Minikube)  
* **Monitoring & Observability:** *Prometheus Fundamentals* YouTube Playlist by Julius Volz [Introduction to the Prometheus Monitoring System](https://www.youtube.com/watch?v=STVMGrYIlfg&list=PLyBW7UHmEXgylLwxdVbrBQJ-fJ_jMvh8h)  
* **Cloud-Native Design Patterns:** *Designing Distributed Systems* by Brendan Burns (Free PDF available on official Microsoft Azure documentation) [Free PDF → info.microsoft.com](https://info.microsoft.com/rs/157-GQE-382/images/EN-CNTNT-eBook-DesigningDistributedSystems.pdf)  
* **Public Cloud Practical Guide:** [Learn AWS in a Month of Lunches](https://www.manning.com/books/learn-amazon-web-services-in-a-month-of-lunches)  
* [https://www.nextwork.org/roadmaps/cloud-engineer](https://www.nextwork.org/roadmaps/cloud-engineer)  
* [DevOps projects](https://docs.google.com/document/d/1-adpUS9KmJHRCCa4aaeNv4bYx9CRCm90iwWksnGdKbc/mobilebasic)  
* https://github.com/NotHarshhaa/kubernetes-projects-learning

# **ML-AI Resources**

# **Beginner-to-Expert Roadmap**

## **Phase 1: Foundations (Math & Classical ML)**

* **Math:** Brush up on Linear Algebra, Calculus, and Probability.  
* **ML Core:** Master core algorithms and AI principles.  
* **Programming:** Gain framework proficiency with PyTorch.  
*   
* 

| Resource | Type/Difficulty | Description/Value |
| :---- | :---- | :---- |
| [Stanford AI, ML, and Math Cheatsheets](https://lnkd.in/g4yvustf) | GitHub Repo, Beginner | Covers Probability, Statistics, Algebra, and Calculus. Essential for foundations. |
| [CS221: Artificial Intelligence](https://lnkd.in/ehwXig2p) | Course, Beginner | Stanford's introductory course on AI principles. |
| [CS229: Machine Learning](https://lnkd.in/eZPepJrM) | Course, Intermediate | Flagship course covering supervised and unsupervised learning. |
| [CS229M: Machine Learning Theory](https://lnkd.in/eTKRsd-C) | Course, Advanced | Theoretical/statistical backbone of ML algorithms. |
| [PyTorch Fundamentals](https://lnkd.in/gfN8rjYm) | GitHub Repo, Beginner | Hands-on notebooks for tensors and matrix math. |

*   
* 

## **Phase 2: Deep Learning & Neural Networks**

* **Concepts:** Understand network architectures and DL optimizations.  
* **Visualization:** Study mechanics like gradient descent and backpropagation.  
* **Computer Vision:** Explore applying neural networks to visual data.  
*   
* 

| Resource | Type/Difficulty | Description/Value |
| :---- | :---- | :---- |
| [CS230: Deep Learning](https://lnkd.in/e8pz9QpY) | Course, Intermediate | Course on building, tuning, and training neural networks. |
| [CS236: Deep Generative Models](https://lnkd.in/eTQRzVdZ) | Course, Advanced | Course on generative modeling (VAEs, GANs, Diffusion). |
| [Deep Learning YouTube Playlist](https://www.linkedin.com/in/analyticalrohit/recent-activity/all/) | YouTube, Intermediate | 26-lecture series covering CNNs, RNNs, LSTMs, and Backpropagation. |
| [The Little Book of Deep Learning](https://www.linkedin.com/in/analyticalrohit/recent-activity/all/) | Book (PDF), Intermediate | Details DL architectures and optimizations by François Fleuret. |
| [CS231N: Deep Learning for CV](https://lnkd.in/eJfeWK9A) | Course, Advanced | Stanford's definitive computer vision course using deep learning. |

* 

## **Phase 3: NLP & Transformer Architecture**

* **Language Basics:** Study word vectors and seq2seq models.  
* **Attention Mechanism:** Deep dive into Self-Attention and modern transformer architectures.  
*   
* 

| Resource | Type/Difficulty | Description/Value |
| :---- | :---- | :---- |
| [CS224N: Natural Language Processing](https://lnkd.in/eEN8U6-j) | Course, Intermediate | Course on deep learning for NLP, word vectors, and seq2seq. |
| [Attention Mechanism Step-by-Step](https://www.linkedin.com/in/analyticalrohit/recent-activity/all/) | Blog/Code, Intermediate | Guide to coding Self-Attention and Causal Self-Attention from scratch. |
| [Transformers & LLMs Cheatsheet](https://www.linkedin.com/in/analyticalrohit/recent-activity/all/) | Cheat Sheet, Intermediate | 4-page VIP cheatsheet on BERT, GPT, T5, and LoRA. |

* 

## **Phase 4: Building & Training LLMs**

* **Construction:** Build GPT-like models from scratch in PyTorch.  
* **Theory:** Understand scaling laws, pre-training pipelines, and foundational architectures.  
*   
* 

| Resource | Type/Difficulty | Description/Value |
| :---- | :---- | :---- |
| [Generative AI for Beginners](https://www.linkedin.com/in/analyticalrohit/recent-activity/all/) | Course, Beginner | Microsoft's 18-lesson course on GenAI, Vector DBs, and Low Code Apps. |
| [MIT GenAI Crash Course](https://www.linkedin.com/in/analyticalrohit/recent-activity/all/) | YouTube, Beginner | 7-hour overview of Stable Diffusion, GANs, and Foundation Models. |
| [A Visual Guide to LLMs](https://www.linkedin.com/in/analyticalrohit/recent-activity/all/) | PDF / Blog, Beginner | Visual breakdowns of tokenization, embeddings, and attention. |
| [GPT LLMs from Scratch (PyTorch)](https://lnkd.in/gnWaaYYH) | GitHub Repo, Intermediate | 10 Jupyter Notebooks breaking down LLM architecture. |
| [CME295: Large Language Models](https://lnkd.in/eJgZ3-Vn) | Course, Advanced | Stanford's academic deep dive into Large Language Models. |

## **Phase 5: Applied LLMs (Fine-Tuning, RAG, Eval)**

* **Adaptation:** Master LoRA/QLoRA for preference alignment.  
* **Retrieval:** Implement indexing and routing for RAG systems.  
* **Measurement:** Use benchmarks and "LLM-as-a-judge" to evaluate performance.  
* 

| Resource | Type/Difficulty | Description/Value |
| :---- | :---- | :---- |
| [RAG Explained Step-by-Step](https://www.linkedin.com/in/analyticalrohit/recent-activity/all/) | PDF Guide, Beginner | Visuals breaking down Naive, Graph, and Agentic RAG. |
| [RAG From Scratch (LangChain)](https://www.linkedin.com/in/analyticalrohit/recent-activity/all/) | YouTube, Intermediate | Series on implementing indexing, retrieval, and routing. |
| [LLM Evaluation Guide](https://www.linkedin.com/in/analyticalrohit/recent-activity/all/) | PDF Guide, Intermediate | Hugging Face's guide on benchmarks and LLM-as-a-judge. |

## **Phase 6: Autonomous Systems (Agents & RL)**

* **Frameworks:** Design autonomous workflows using industry-backed agent frameworks.  
* **Reinforcement Learning:** Build alignment foundations and scale RL environments.  
* 

| Resource | Type/Difficulty | Description/Value |
| :---- | :---- | :---- |
| [Introduction to Agents (Google)](https://www.linkedin.com/in/analyticalrohit/recent-activity/all/) | PDF Guide, Intermediate | 54-page framework detailing orchestration and memory. |
| [Harness Engineering for AI Agents](https://lnkd.in/gZUVNQjD) | Course, Advanced | Teaches how to build robust control systems for AI coders. |
| [CS234: Reinforcement Learning](https://lnkd.in/e9ZErmTV) | Course, Advanced | Rigorous Stanford course covering MDPs and Q-Learning. |
| [Guide to RL Environments](https://github.com/adithya-s-k/RL_Envs_101) | PDF / Repo, Advanced | Hugging Face's guide on scaling RL environments. |

## **Phase 7: Interview Prep & Mastery**

* **Interview Prep:** Test knowledge gaps with dedicated LLM interview resources.  
* **Continuous Mastery:** Stay updated with foundational research and structured long-term curricula.

| Resource | Type/Difficulty | Description/Value |
| :---- | :---- | :---- |
| [Top 1% NLP Papers Playlist](https://www.linkedin.com/in/analyticalrohit/recent-activity/all/) | Papers, Advanced | Curated list including Word2Vec, BERT, GPT-2/3, and Attention. |
| [AI Engineering from Scratch](https://lnkd.in/gCxv4e4d) | GitHub Repo, Beginner | 503-lesson curriculum structured into 20 phases. |

# **Gen AI Resources**

**📹 Videos:**  
1\. LLM Introduction: [https://www.youtube.com/watch?v=zjkBMFhNj\_g](https://www.youtube.com/watch?v=zjkBMFhNj_g)  
2\. LLMs from Scratch: [https://www.youtube.com/watch?v=9vM4p9NN0Ts](https://www.youtube.com/watch?v=9vM4p9NN0Ts)  
3\. Agentic AI Overview (Stanford): [https://www.youtube.com/watch?v=kJLiOGle3Lw](https://www.youtube.com/watch?v=kJLiOGle3Lw)  
4\. Building and Evaluating Agents: [https://www.youtube.com/watch?v=d5EltXhbcfA](https://www.youtube.com/watch?v=d5EltXhbcfA)  
5\. Building Effective Agents: [https://www.youtube.com/watch?v=D7\_ipDqhtwk](https://www.youtube.com/watch?v=D7_ipDqhtwk)  
6\. Building Agents with MCP: [https://www.youtube.com/watch?v=kQmXtrmQ5Zg](https://www.youtube.com/watch?v=kQmXtrmQ5Zg)  
7\. Building an Agent from Scratch: [https://www.youtube.com/watch?v=xzXdLRUyjUg](https://www.youtube.com/watch?v=xzXdLRUyjUg)  
8\. Philo Agents: [https://www.youtube.com/playlist?list=PLacQJwuclt\_sV-tfZmpT1Ov6jldHl30NR](https://www.youtube.com/playlist?list=PLacQJwuclt_sV-tfZmpT1Ov6jldHl30NR)

**🗂️ Repos**  
1\. GenAI Agents: [https://github.com/nirdiamant/GenAI\_Agents](https://github.com/nirdiamant/GenAI_Agents)  
2\. Microsoft's AI Agents for Beginners: [https://github.com/microsoft/ai-agents-for-beginners](https://github.com/microsoft/ai-agents-for-beginners)  
3\. Prompt Engineering Guide: [https://lnkd.in/gJjGbxQr](https://lnkd.in/gJjGbxQr)  
4\. Hands-On Large Language Models: [https://lnkd.in/dxaVF86w](https://lnkd.in/dxaVF86w)  
5\. AI Agents for Beginners: [https://github.com/microsoft/ai-agents-for-beginners](https://github.com/microsoft/ai-agents-for-beginners)  
6\. GenAI Agents[https://lnkd.in/dEt72MEy](https://lnkd.in/dEt72MEy)  
7\. Made with ML: [https://lnkd.in/d2dMACMj](https://lnkd.in/d2dMACMj)  
8\. Hands-On AI Engineering:[https://github.com/Sumanth077/Hands-On-AI-Engineering](https://github.com/Sumanth077/Hands-On-AI-Engineering)  
9\. Awesome Generative AI Guide: [https://lnkd.in/dJ8gxp3a](https://lnkd.in/dJ8gxp3a)  
10\. Designing Machine Learning Systems: [https://lnkd.in/dEx8sQJK](https://lnkd.in/dEx8sQJK)  
11\. Machine Learning for Beginners from Microsoft: [https://lnkd.in/dBj3BAEY](https://lnkd.in/dBj3BAEY)  
12\. LLM Course: [https://github.com/mlabonne/llm-course](https://github.com/mlabonne/llm-course)

**🗺️ Guides**  
1\. Google's Agent Whitepaper: [https://lnkd.in/gFvCfbSN](https://lnkd.in/gFvCfbSN)  
2\. Google's Agent Companion: [https://lnkd.in/gfmCrgAH](https://lnkd.in/gfmCrgAH)  
3\. Building Effective Agents by Anthropic: [https://lnkd.in/gRWKANS4](https://lnkd.in/gRWKANS4).  
4\. Claude Code Best Agentic Coding practices: [https://lnkd.in/gs99zyCf](https://lnkd.in/gs99zyCf)  
5\. OpenAI's Practical Guide to Building Agents: [https://lnkd.in/guRfXsFK](https://lnkd.in/guRfXsFK)

**📚Books:**  
1\. Understanding Deep Learning: [https://udlbook.github.io/udlbook/](https://udlbook.github.io/udlbook/)  
2\. Building an LLM from Scratch: [https://lnkd.in/g2YGbnWS](https://lnkd.in/g2YGbnWS)  
3\. The LLM Engineering Handbook: [https://lnkd.in/gWUT2EXe](https://lnkd.in/gWUT2EXe)  
4\. AI Agents: The Definitive Guide \- Nicole Koenigstein:  [https://lnkd.in/dJ9wFNMD](https://lnkd.in/dJ9wFNMD)  
5\. Building Applications with AI Agents \- Michael Albada: [https://lnkd.in/dSs8srk5](https://lnkd.in/dSs8srk5)  
6\. AI Agents with MCP \- Kyle Stratis: [https://lnkd.in/dR22bEiZ](https://lnkd.in/dR22bEiZ)  
7\. AI Engineering: [https://www.oreilly.com/library/view/ai-engineering/9781098166298/](https://www.oreilly.com/library/view/ai-engineering/9781098166298/)

**📜 Papers**  
1\. ReAct: [https://lnkd.in/gRBH3ZRq](https://lnkd.in/gRBH3ZRq)  
2\. Generative Agents: [https://lnkd.in/gsDCUsWm](https://lnkd.in/gsDCUsWm).  
3\. Toolformer: [https://lnkd.in/gyzrege6](https://lnkd.in/gyzrege6)  
4\. Chain-of-Thought Prompting: [https://lnkd.in/gaK5CXzD](https://lnkd.in/gaK5CXzD).  
5\. Tree of Thoughts: [https://lnkd.in/gRJdv\_iU](https://lnkd.in/gRJdv_iU).  
6\. Reflexion: [https://lnkd.in/gGFMgjUj](https://lnkd.in/gGFMgjUj)  
7\. Retrieval-Augmented Generation Survey: [https://lnkd.in/gGUqkkyR](https://lnkd.in/gGUqkkyR).

**🧑‍🏫 Courses:**  
1\. HuggingFace's Agent Course: [https://lnkd.in/gmTftTXV](https://lnkd.in/gmTftTXV)  
2\. MCP with Anthropic: [https://lnkd.in/geffcwdq](https://lnkd.in/geffcwdq)  
3\. Building Vector Databases with Pinecone: [https://lnkd.in/gCS4sd7Y](https://lnkd.in/gCS4sd7Y)  
4\. Vector Databases from Embeddings to Apps: [https://lnkd.in/gm9HR6\_2](https://lnkd.in/gm9HR6_2)  
5\. Agent Memory: [https://lnkd.in/gNFpC542](https://lnkd.in/gNFpC542)  
6\. Building and Evaluating RAG apps: [https://lnkd.in/g2qC9-mh](https://lnkd.in/g2qC9-mh)  
7\. Building Browser Agents: [https://lnkd.in/gsMmCifQ](https://lnkd.in/gsMmCifQ)  
8\. LLMOps: [https://lnkd.in/g7bHU37w](https://lnkd.in/g7bHU37w)  
9\. Evaluating AI Agents: [https://lnkd.in/gHJtwF5s](https://lnkd.in/gHJtwF5s)  
10\. Computer Use with Anthropic: [https://lnkd.in/gMUWg7Fa](https://lnkd.in/gMUWg7Fa)  
11\. Multi-Agent Use: [https://lnkd.in/gU9DY9kj](https://lnkd.in/gU9DY9kj)  
12\. Improving LLM Accuracy: [https://lnkd.in/gsE-4FvY](https://lnkd.in/gsE-4FvY)  
13\. Agent Design Patterns: [https://lnkd.in/gzKvx5A4](https://lnkd.in/gzKvx5A4)  
14\. Multi Agent Systems: [https://lnkd.in/gUayts9s](https://lnkd.in/gUayts9s)

**📩 Newsletters**  
1\. Gradient Ascent: [https://lnkd.in/gZbZAeQW](https://lnkd.in/gZbZAeQW)  
2\. DecodingML by [Paul](https://www.linkedin.com/in/pauliusztin/): [https://lnkd.in/gpZPgk7J](https://lnkd.in/gpZPgk7J)  
3\. Deep (Learning) Focus by [Cameron](https://www.linkedin.com/in/cameron-r-wolfe-ph-d-04744a238/): [https://lnkd.in/gTUNcUVE](https://lnkd.in/gTUNcUVE)  
4\. NeoSage by [Shivani](https://www.linkedin.com/in/shivanivirdi/): [https://blog.neosage.io/](https://blog.neosage.io/)  
5\. Jam with AI by [Shirin](https://www.linkedin.com/in/shirin-khosravi-jam/) and [Shantanu](https://www.linkedin.com/in/shantanuladhwe/): [https://lnkd.in/gQXJzuV8](https://lnkd.in/gQXJzuV8)  
6\. Data Hustle by [Sai](https://www.linkedin.com/in/saibysani18/): [https://lnkd.in/gZpdTTYD](https://lnkd.in/gZpdTTYD)

# **Systems Resources**

# **Company-Wise Software Systems Interview Bible**

This document serves as the definitive technical roadmap for candidates targeting software roles within the semiconductor and pure-systems ecosystem. It focuses exclusively on the software stack—from language primitives to the Linux kernel and low-level system design.

## **1\. Unified Systems Learning Dependency Graph**

Success in systems programming follows a strict hierarchy of dependencies. You cannot master the Linux Kernel without understanding C memory layout, nor can you optimize performance without understanding Computer Architecture.

**Level 1: Language Primitives (C & Modern C++14/17/20)**

* **C Core:** Pointers, memory layout (stack/heap/data/text), function pointers, `volatile`, `static`, `extern`, and bitwise manipulation.  
* **C++ Evolution:** RAII, Smart Pointers (`unique_ptr`, `shared_ptr`), Move Semantics, Template Metaprogramming, and vtable internals.

**Level 2: Computer Architecture (Software Perspective)**

* **CPU Internals:** Pipeline stages, branch prediction, and instruction sets (ARM vs x86).  
* **Memory Hierarchy:** Cache levels (L1/L2/L3), cache lines, associativity, and cache coherence protocols (MESI).

**Level 3: Operating Systems Core & Concurrency**

* **OS Fundamentals:** Virtual memory, paging, TLB, demand paging, and context switching.  
* **Concurrency:** Mutexes, semaphores, spinlocks, atomics, and memory barriers.

**Level 4: Linux Kernel Basics, Device Drivers & Tooling**

* **Kernel Primitives:** System calls, ISRs (Interrupt Service Routines), Top/Bottom Halves (Tasklets, Workqueues), and MMIO.  
* **Tooling:** Proficient use of GDB, Valgrind, `perf`, and `eBPF`.

**Level 5: Low-Level System Design (LLD) & Performance Optimization**

* **LLD:** Designing thread-safe buffers, memory pool allocators, and lock-free data structures.  
* **Optimization:** Loop unrolling, SIMD (AVX/NEON), and cache-aware programming.

---

## **2\. Dedicated Company Deep-Dives**

### **2.1 Qualcomm & MediaTek (The Mobile SoC Giants)**

## 

| Category | Details |
| :---- | :---- |
| **Core Teams** | Modem Firmware, Snapdragon/Helio HAL, Graphics Drivers (Adreno/Mali), Power Management, Android BSP. |
| **Skills Prioritized** | Bare-metal C, RTOS (QuRT), ARM Architecture, Android Binder, Camera/Audio HAL development. |
| **Interview Process** | 1\. Online Assessment (C/C++ & Logic). 2\. Technical Screen (Pointers & Bitwise). 3\. Rounds: 2 Coding (DSA \+ Systems), 1 OS/Kernel, 1 Hiring Manager. Difficulty: High. |

### **2.2 NVIDIA & AMD (GPU & Compute Powerhouses)**

## 

| Category | Details |
| :---- | :---- |
| **Core Teams** | CUDA/ROCm Core, Display Drivers, AI/Tensor Cores Software, Compiler Backend (LLVM), Virtualization. |
| **Skills Prioritized** | High-performance C++, Parallel Programming, SIMD, GPGPU Architecture, Kernel-mode drivers. |
| **Interview Process** | 1\. Phone Screen (C++ Internals). 2\. Virtual Onsite: 4-5 Rounds. Focus on Cache Coherence, Parallelism, and heavy C++17/20 templates. Difficulty: Elite. |

### **2.3 Intel & ARM (The Architecture Architects)**

## 

| Category | Details |
| :---- | :---- |
| **Core Teams** | Architecture Simulators (Gem5), Toolchains/Compilers, BIOS/UEFI, Firmware, Kernel Optimization. |
| **Skills Prioritized** | Instruction Set Architecture (ISA), Micro-architecture, LLVM/GCC, System-on-Chip (SoC) modeling. |
| **Interview Process** | 1\. Screening (Arch Fundamentals). 2\. Technical: Focus on Cache lines, Pipeline hazards, and Assembly-to-C mapping. Difficulty: Very High. |

### **2.4 Micron & Texas Instruments (Memory & Embedded Control)**

## 

| Category | Details |
| :---- | :---- |
| **Core Teams** | SSD Firmware, NAND Flash Management, Automotive RTOS, Industrial IoT, Signal Processing. |
| **Skills Prioritized** | Fixed-point arithmetic, DMA, FTL (Flash Translation Layer), Wear-leveling, I2C/SPI/UART protocols. |
| **Interview Process** | 1\. Basic Coding. 2\. Heavy focus on Embedded C, Interrupts, and Hardware-Software interfacing. Difficulty: Moderate to High. |

### **2.5 Broadcom, NXP & Synopsys/Cadence**

## 

| Category | Details |
| :---- | :---- |
| **Core Teams** | Network Switch Silicons, Automotive Safety (ISO 26262), EDA Core Engine (Graph Algos), Compilers. |
| **Skills Prioritized** | Networking Stacks (TCP/IP), Real-time Constraints, Multi-threading, Performance-critical C++. |
| **Interview Process** | 1\. Technical Screening. 2\. Onsite: Heavy focus on System Design and Concurrency. EDA roles focus on Graph Theory and Algorithmic Efficiency. |

---

## **3\. Topic-Wise Preparation & Resource Index**

### **3.1 Low-Level C & Modern C++**

* **Theory:** Understanding the object model, memory alignment (`alignas`), and the cost of `std::function` vs. function pointers.  
* **Resources:**

#### **📁 Handbooks & PDF Documents**

* [C++ Reference Documentation](https://en.cppreference.com/w/)  
  * [Effective Modern C++ by Scott Meyers (Resource Guide)](https://www.aristeia.com/Books/EMC++_Resources.html)  
  * [Guru of the Week (GotW) C++ Challenges](https://herbsutter.com/gotw/)

### **3.2 Operating Systems & Concurrency**

* **Theory:** Virtual memory management, demand paging, scheduling algorithms, and the 1:1 vs M:N threading models.  
* **Resources:**

#### **🌐 Web Articles, Platforms & Interactive Tools**

* [OSTEP Online Chapters: Operating Systems Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/)  
  * [The Linux Programming Interface (TLPI)](https://man7.org/tlpi/)  
  * [Preshing on Programming (Memory Barriers/Atomics)](https://preshing.com/archives/)

### **3.3 Linux Kernel & Device Drivers**

* **Theory:** Linux Kernel subsystems (VFS, MM, Process Mgmt), Character vs. Block drivers, and eBPF for observability.  
* **Resources:**

#### **🌐 Web Articles, Platforms & Interactive Tools**

* [Linux Device Drivers, 3rd Edition (Free Online)](https://lwn.net/Kernel/LDD3/)  
  * [Linux Kernel Documentation](https://www.kernel.org/doc/html/latest/)  
  * [Bootlin Training Slides (Embedded Linux & Kernel)](https://bootlin.com/training/)

### **3.4 Computer Architecture & Performance**

* **Theory:** MESI Protocol, False Sharing, SIMD (Single Instruction Multiple Data), and Branch Prediction impact.  
* **Resources:**

#### **🌐 Web Articles, Platforms & Interactive Tools**

* [Agner Fog’s Optimization Manuals](https://www.agner.org/optimize/)  
  * [Computer Architecture: A Quantitative Approach (Supplemental Material)](https://www.elsevier.com/books/computer-architecture/hennessy/978-0-12-811905-1)  
  * [Performance Analysis Guide (Brendan Gregg)](https://www.brendangregg.com/linuxperf.html)

### **3.5 General Systems & Networking**

* **Resources:**

#### **📁 Handbooks & PDF Documents**

* [Computer Networks Quick Notes](https://drive.google.com/file/d/1OymHd6cW-KQ4L36DVCEeD2OUdknXQBwY/view?usp=sharing)  
  * [Networking Concepts Guide](https://drive.google.com/file/d/12dJ0VPDdLkFtnkjHkMEBxcixqERr37IP/view?usp=sharing)  
  * [System Design Fundamentals](https://systemdesignschool.io/primer)

---

## **4\. Top 100 System Interview Questions**

### **Group 1: C/Bitwise & Memory Layout**

1. Explain the memory layout of a C program (Text, Data, BSS, Stack, Heap).  
2. How do you implement a generic `memcpy` that handles overlapping memory?  
3. Implement a function to count set bits in an integer (Brian Kernighan’s algorithm).  
4. Explain the difference between `char *p = "Hello"` and `char p[] = "Hello"`.  
5. How do you detect if a machine is Big-endian or Little-endian?  
6. Explain the `volatile` keyword and when it is mandatory in embedded systems.  
7. Write a macro to find the offset of a member in a struct.  
8. How does `malloc` work internally? (Explain SBRK vs MMAP).  
9. Implement an aligned `malloc` and `free`.  
10. What is the use of a flexible array member in a struct?  
11. Explain function pointers and their role in implementing polymorphism in C.  
12. What happens if you `free` a pointer twice?  
13. How do you swap two bits at given positions in a byte?  
14. Explain `static` in three different contexts (global, local, function).  
15. What is "Structure Padding" and "Packing"? How do you avoid it?  
16. Implement a Circular Buffer in C.  
17. How do you access a specific hardware register at address `0x40001000`?  
18. Explain the difference between `inline` functions and macros.  
19. What is a "Dangling Pointer"?  
20. Implement a linked list reversal using recursion and iteration.

### **Group 2: Modern C++ Internals & Performance**

1. Explain the internal layout of a C++ object with a vtable.  
2. What is RAII, and how does it prevent resource leaks?  
3. Explain Move Semantics and `std::move`.  
4. Difference between `std::unique_ptr` and `std::shared_ptr`.  
5. What is "The Rule of Five" in C++?  
6. How does `std::vector` manage its memory? What is the cost of `push_back`?  
7. Explain Template Metaprogramming and SFINAE.  
8. What is the "Curiously Recurring Template Pattern" (CRTP)?  
9. Explain `constexpr` and how it differs from `const`.  
10. What are Smart Pointers? Implement a basic `shared_ptr`.  
11. Explain the "Diamond Problem" and how virtual inheritance solves it.  
12. What is `std::atomic`, and why is it preferred over `volatile` for threads?  
13. Explain the C++ Memory Model (Acquire-Release semantics).  
14. What are Lambda expressions? How do they capture variables internally?  
15. Explain `std::variant` and `std::optional` (C++17).  
16. How do you use `type_traits` to check if a class is polymorphic at compile time?  
17. Difference between `static_cast`, `dynamic_cast`, `reinterpret_cast`, and `const_cast`.  
18. What is "Object Slicing"?  
19. How does `std::sort` work? (IntroSort).  
20. Explain the cost of exceptions in C++.

### **Group 3: OS Architecture, Paging & Concurrency**

1. What is a "Page Fault"? Explain the full walk of a page fault.  
2. Difference between a Process and a Thread.  
3. Explain TLB (Translation Lookaside Buffer) and its role.  
4. What is "Thrashing" in an OS?  
5. Explain the Producer-Consumer problem and implement it using Condition Variables.  
6. What is a Deadlock? List the four necessary conditions.  
7. Difference between a Mutex and a Binary Semaphore.  
8. Explain "Priority Inversion" and how "Priority Inheritance" solves it.  
9. How does a Spinlock differ from a Mutex? When would you use a Spinlock?  
10. What is "Demand Paging"?  
11. Explain the "Dining Philosophers" problem.  
12. What is a "Context Switch"? What data is saved during a switch?  
13. Explain the Buddy System for memory allocation.  
14. What are "Futexes" (Fast Userspace Mutexes)?  
15. Explain "Dirty Reads" and "Phantom Reads" in the context of isolation.  
16. How do you implement a Thread Pool?  
17. Explain "False Sharing" and how to prevent it.  
18. What is the difference between Pre-emptive and Non-preemptive scheduling?  
19. What is a "Zombie Process" and a "Orphan Process"?  
20. Explain the CAP Theorem.

### **Group 4: Linux Kernel & Driver Primitives**

1. What is a "System Call"? How is it triggered (int 0x80 vs syscall)?  
2. Explain Top Halves and Bottom Halves in Linux.  
3. What are "Tasklets" and "Workqueues"?  
4. How does the Linux Virtual File System (VFS) work?  
5. Explain the role of the Device Tree in Linux.  
6. How does a driver handle an interrupt?  
7. What is "User Space" vs "Kernel Space"?  
8. Explain `mmap()` and its advantages for file I/O.  
9. How do you implement a simple Character Driver?  
10. What is "Copy-on-Write" (COW) during `fork()`?  
11. Explain the SLAB/SLOB/SLUB allocator.  
12. What is an IOMMU?  
13. How does "Zero Copy" networking work?  
14. What is "Kernel Panic," and how do you debug it?  
15. Explain the difference between Softirqs and Hardirqs.  
16. How does the "Completely Fair Scheduler" (CFS) work?  
17. What is `kmap` and `vmap`?  
18. Explain the "Big Kernel Lock" (BKL) and why it was removed.  
19. What is eBPF and why is it revolutionary for Linux tracing?  
20. Explain the difference between `kmalloc` and `vmalloc`.

### **Group 5: Low-Level System Design & Hardware Interfacing**

1. Design a Lock-free MPMC (Multi-Producer Multi-Consumer) Queue.  
2. Design a Memory Pool Allocator for a real-time system.  
3. How would you design a software-based Cache (LRU)?  
4. Design a Logger that can handle 1 million logs/sec without blocking.  
5. Explain how a DMA transfer is initiated and completed.  
6. Design a Bitset class from scratch.  
7. How would you implement a `malloc` that is thread-safe?  
8. Design a high-frequency trading matching engine (LLD).  
9. How do you optimize a matrix multiplication for L1 cache?  
10. Design a rate-limiter for an embedded sensor.  
11. Explain the MESI cache coherence protocol states.  
12. How do you write a driver for an I2C-based temperature sensor?  
13. Design a memory-efficient "Bloom Filter."  
14. Explain "Instruction Level Parallelism" (ILP).  
15. How do you handle "Alignment" in a network packet parser?  
16. Design a custom String class with Reference Counting (COW).  
17. How do you implement a "Watchdog Timer" in software?  
18. Design an "Event Loop" for a GUI framework.  
19. Explain how to use SIMD instructions to speed up image grayscale conversion.  
20. Design a "Garbage Collector" (Reference Counting vs Mark-and-Sweep).

---

## **5\. Tactical Preparation Plans & Checklists**

### **30-Day Sprint (For immediate interviews)**

* **Days 1-7:** C/C++ Deep Dive (Pointers, vtables, Smart Pointers).  
* **Days 8-15:** OS & Concurrency (Virtual memory, Mutexes, Producer-Consumer).  
* **Days 16-22:** Computer Arch (Cache, MESI, ARM basics).  
* **Days 23-30:** LeetCode (Top 100 System Questions) \+ Mock Interviews.

### **90-Day Comprehensive Mastery**

* **Month 1:** Languages & Data Structures. Read "Effective Modern C++."  
* **Month 2:** Operating Systems & Linux Kernel. Complete OSTEP chapters.  
* **Month 3:** Low-Level System Design & Hardware Interfacing. Build 2-3 projects.

### **5 "Must-Do" Systems Projects**

1. **Custom Memory Allocator:** Implement `malloc`, `free`, `realloc` with block splitting and coalescing.  
2. **Multithreaded Web Server:** Use `epoll` (Linux) to handle 10k+ concurrent connections.  
3. **Userspace Threading Library:** Implement `thread_create`, `yield`, and `join` using `setjmp/longjmp`.  
4. **Linux Kernel Module:** A character driver that implements a simple encrypted pipe (`/dev/cryptopipe`).  
5. **SIMD Image Processor:** Use Intel AVX or ARM NEON to optimize a Gaussian Blur filter.

### **Final Readiness Checklist**

- [ ] I can explain the full lifecycle of a `malloc(100)` call from userspace to kernel.  
- [ ] I can implement a lock-free stack using `compare_and_swap`.  
- [ ] I can draw the memory layout of a C++ class with multiple virtual inheritance.  
- [ ] I can explain the difference between a page table walk and a TLB miss.  
- [ ] I can write code to reverse the endianness of an integer without using library functions.  
- [ ] I can explain why `volatile` does not provide atomicity.  
- [ ] I can use `gdb` to inspect the stack frame and find a memory corruption root cause.

# **Amazing Github Repos**

### **🧠 1\. Generative AI, LLMs & Agents**

* [Awesome LLM Apps](https://github.com/Shubhamsaboo/awesome-llm-apps)  
* [Hands-On Large Language Models](https://github.com/HandsOnLLM/Hands-On-Large-Language-Models)  
* [AI Engineering Hub](https://github.com/patchy631/ai-engineering-hub)  
* [Awesome Generative AI](https://github.com/steven2358/awesome-generative-ai)  
* [OpenAI Cookbook](https://github.com/openai/openai-cookbook)  
* [Awesome AI Agents](https://github.com/e2b-dev/awesome-ai-agents)  
* [Awesome AI Agents Collection](https://github.com/jim-schwoebel/awesome_ai_agents)  
* [llm-council](https://github.com/karpathy/llm-council)  
* [llm fit](https://github.com/everything-claude-code)

### **🏗️ 2\. Core Engineering, Architecture & Scalability**

* [System thinking](https://github.com/alex/what-happens-when)  
* [Real-world engineering](https://github.com/kilimchoi/engineering-blogs)  
* [Dive Into Refactoring (2019)](https://drive.google.com/file/d/1EpcUzqhHi7TXDiEWOsppkZUBbCCmBlQm/view?usp=drive_link)  
* [Dive Into Design Patterns](https://drive.google.com/file/d/1uu3Ye48X9h0YifMl56o2BbN5vkQdFiJk/view?usp=drive_link)  
* [DesignPatternsByCodeN](https://github.com/nishchal-muradia/DesignPatternsByCodeN.git)  
* [Scalability & trade-offs](https://github.com/binhnguyennus/awesome-scalability)  
* [Google Engineering Practices](https://github.com/google/eng-practices)  
* [API Security Checklist](https://github.com/shieldfy/API-Security-Checklist)  
* [DB Readings](https://github.com/rxin/db-readings)  
* [Backend Best Practices](https://github.com/Sairyss/backend-best-practices)

### **🗺️ 3\. Developer Roadmaps, Learning & General CS**

* [Strong fundamentals (OSSU)](https://github.com/ossu/computer-science)  
* [Public APIs](https://github.com/public-apis/public-apis)  
* [Developer Roadmap](https://github.com/kamranahmedse/developer-roadmap)  
* [Build Your Own X](https://github.com/codecrafters-io/build-your-own-x)  
* [Free Programming Books](https://github.com/EbookFoundation/free-programming-books)  
* [JavaScript Algorithms](https://github.com/trekhleb/javascript-algorithms)  
* [Awesome Lists](https://github.com/sindresorhus/awesome)  
* [The Odin Project](https://github.com/TheOdinProject/curriculum)  
* [Awesome-Selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted)  
* [20 Websites Collection](https://github.com/nileshhadalgi016/digital-landfill/blob/main/20_websites.md)  
* [Technical Book Collection](https://github.com/AniruddhaChattopadhyay/Books)  
* [Learn X in Y Minutes](https://github.com/adambard/learnxinyminutes-docs)  
* [Tech Interview Handbook](https://github.com/yangshun/tech-interview-handbook)  
* [CS Video Courses](https://github.com/Developer-Y/cs-video-courses)

### **📊 4\. Data Science, Data Engineering & Deep Learning**

#### **📁 Handbooks & PDF Documents**

* [Python Data Science Handbook](https://github.com/jakevdp/PythonDataScienceHandbook)  
* [Data Science Cheat Sheets](https://github.com/FavioVazquez/ds-cheatsheets)  
* [CS229 Lecture Notes](https://cs229.stanford.edu/lectures-spring2022/main_notes.pdf)  
* [Information Theory, Inference, and Learning Algorithms](https://www.inference.org.uk/itprnn/book.pdf)

#### **🎓 Online Courses & Specializations**

* [Andrew Ng's ML Specialization (Stanford)](https://www.coursera.org/specializations/machine-learning-introduction)  
* [Google's Machine Learning Crash Course (15 hours)](https://developers.google.com/machine-learning/crash-course)  
* [Fast.ai Practical Deep Learning](https://course.fast.ai)  
* [Hugging Face LLM Course](https://huggingface.co/learn/llm-course)  
* [Hugging Face Deep RL Course](https://huggingface.co/learn/deep-rl-course)

Note: Recommended learning order: Start with \#1 (foundations), then \#2 (Google ML), then \#3 (practical projects), then \#4 (LLMs), then \#5 (advanced RL).

#### **🎬 Video Courses & Tutorial Playlists**

* [Stanford CS229: Machine Learning](https://www.youtube.com/playlist?list=PLoROMvodv4rMiGQp3WXShtMGgzqpfVfbU)  
* [Caltech Machine Learning Course](https://www.youtube.com/playlist?list=PLD63A284B7615313A)  
* [Neural Networks: Zero to Hero](https://www.youtube.com/playlist?list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ)  
* [Backpropagation Video](https://www.youtube.com/watch?v=VMj-3S1tku0)  
* [Karpathy YouTube](https://youtube.com/@AndrejKarpathy)

#### **🌐 Web Articles, Platforms & Interactive Tools**

* [Awesome Data Analysis](https://github.com/PavelGrigoryevDS/awesome-data-analysis)  
* [Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp)  
* [Distill.pub](https://distill.pub/)  
* [CS 329S (Machine Learning Systems)](https://stanford-cs329s.github.io/)  
* [A Recipe for Training Neural Networks](https://karpathy.github.io/2019/04/25/recipe)  
* [Karpathy Blog](https://karpathy.github.io)  
* [TensorFlow Playground](https://playground.tensorflow.org)  
* [Attention Visualizer](https://attentionviz.com)  
* [Transformer Explainer](https://poloclub.github.io/transformer-explainer)  
* [Embedding Projector](https://projector.tensorflow.org)  
* [Teachable Machine](https://teachablemachine.withgoogle.com)  
* [Distill](https://distill.pub)  
* [Google AI Experiments](https://experiments.withgoogle.com/collection/ai)  
* [Lobe](https://www.lobe.ai)  
* [Playground AI](https://playgroundai.com)  
* [DeepLearning.AI Short Courses](https://www.deeplearning.ai/short-courses)  
* [3Blue1Brown](https://www.3blue1brown.com)  
* [Weights & Biases Reports](https://wandb.ai/site/reports)  
* [Fast.ai](https://course.fast.ai)  
* [Explainpaper](https://www.explainpaper.com)  
* [Random Forest](https://mlu-explain.github.io/random-forest/)  
* [Decision Tree](https://mlu-explain.github.io/decision-tree/)  
* [Logistic Regression](https://mlu-explain.github.io/logistic-regression/)  
* [Train/Test/Validation](https://mlu-explain.github.io/train-test-validation/)  
* [ConvNetJS](https://cs229.stanford.edu/people/karpathy/convnetjs/demo/classify2d.html)  
* [CNN Explainer](https://poloclub.github.io/cnn-explainer/)  
* [OpenAI Microscope](https://microscope.openai.com/)

### **🕷️ 5\. Web Scraping & Browser Automation**

* [Firecrawl](https://github.com/firecrawl/firecrawl)  
* [Crawl4AI](https://github.com/unclecode/crawl4AI)  
* [Browser-use](https://github.com/browser-use/browser-use)  
* [Crawlee](https://github.com/apify/crawlee)  
* [Scrapy](https://github.com/scrapy/scrapy)  
* [Markitdown](https://github.com/microsoft/markitdown)  
* [Scrapling](https://github.com/d4vinci/Scrapling)  
* [Autoscraper](https://github.com/alirezamika/autoscraper)  
* [Curl\_cffi](https://github.com/lexiforest/curl_cffi)  
* [ScrapeGraphAI](https://github.com/ScrapeGraphAI/Scrapegraph-ai)

### **🛠️ 6\. Assorted UI, Map & Utility Projects**

* [Project-based Learning](https://github.com/practical-tutorials/project-based-learning)  
* [Textarea.my](https://github.com/antonmedv/textarea)  
* [Map CN](https://github.com/AnmolSaini16/mapcn)  
* [City Map Poster Generator](https://github.com/originalankur/maptoposter)  
* [Codebase-to-course](https://github.com/zarazhangrui/codebase-to-course)  
* [Visual Explainer](https://github.com/nicobailon/visual-explainer)

### **🐍 7\. Python Learning & Tools**

* [Python Tutor](https://pythontutor.com)  
* [CodeChef Visualizer](https://www.codechef.com/code-visualizer)  
* [Futurecoder](https://futurecoder.io)  
* [Codedex](https://www.codedex.io/python)  
* [VisuAlgo](https://visualgo.net)  
* [CS Circles](https://cscircles.cemc.uwaterloo.ca)  
* [CodeCombat](https://codecombat.com)  
* [Replit](https://replit.com)  
* [W3Schools Python](https://www.w3schools.com/python)  
* [Scratch](https://scratch.mit.edu)

# **Osm Youtube Playlist**

### **AI & Machine Learning**

* [Building Neural Networks from Scratch](https://www.youtube.com/playlist?list=PLPTV0NXA_ZSj6tNyn_UadmUeU3Q3oR-hu)  
* [Build your own LLM Workshop](https://www.youtube.com/playlist?list=PLweJS2YZCfkeXXdfCKGaxAhm2w8p0u1z6)  
* [Deep Learning](https://www.youtube.com/playlist?list=PLgPbN3w-ia_PeT1_c5jiLW3RJdR7853b9)  
* [Deep Learning: Crash Course](https://www.youtube.com/playlist?list=PLYXB138yx3ir49HzwMB4hNEVyO-KIYs-f)  
* [Deep Learning 101](https://www.youtube.com/playlist?list=PLTl9hO2Oobd_NwyY_PeSYrYfsvHZnHGPU)  
* [Introduction to Statistics and Data Analysis](https://www.youtube.com/playlist?list=PLMrJAkhIeNNT14qn1c5qdL29A1UaHamjx)  
* [LLM Animated](https://www.youtube.com/playlist?list=PLJq-63ZRPdBu38EjXRXzyPat3sYMHbIWU)  
* [LLM Chronicles](https://www.youtube.com/playlist?list=PLNg09XqZv0dEWPpb1jJf8woP3cl_boYWZ)  
* [Math for Machine Learning](https://www.youtube.com/playlist?list=PLD80i8An1OEGZ2tYimemzwC3xqkU0jKUg)  
* [Natural Language Processing by Michael Collins](https://www.youtube.com/playlist?list=PLA212ij5XG8OTDRl8IWFiJgHR9Ve2k9pv)  
* [NumPy Tutorial](https://www.youtube.com/playlist?list=PL4KX3oEgJcffzDkv6IiZJF3v17GbLv7Wo)  
* [Probability Bootcamp](https://www.youtube.com/playlist?list=PLMrJAkhIeNNR3sNYvfgiKgcStwuPSts9V)  
* [RLHF Book (and Post-Training) Course](https://www.youtube.com/playlist?list=PLL1tdVxB1CpVpEtMHxwuR4uI4Lxjw00_y)  
* [Stanford CS224N: NLP with Deep Learning 2023](https://www.youtube.com/playlist?list=PLoROMvodv4rMFqRtEuo6SGjY4XbRIVRd4)  
* [Valuable Vector Calculus](https://www.youtube.com/playlist?list=PLug5ZIRrShJHgsWPng59fFFoqn183aO-1)

### **Computer Science Fundamentals & Systems**

* [CMU Intro to Database Systems (15-445/645 \- Fall 2024\)](https://www.youtube.com/playlist?list=PLSE8ODhjZXjYDBpQnSymaectKjxCy6BYq)  
* [Cryptography Essentials](https://www.youtube.com/playlist?list=PLIFyRwBY_4bQvq5PuJASilkHSVGLZtceZ)  
* [Database Internals](https://www.youtube.com/playlist?list=PLhgFs9q2EVg91l17UXoPdzsEhJrokLiMx)  
* [Databases 101](https://www.youtube.com/playlist?list=PL5Lsd0YA4OME2HC5m9QSfXG9cxb9Cvz5L)  
* [Distributed Databases for Engineers](https://www.youtube.com/playlist?list=PLYPO3T7Sl63s0v4u6rf9MVfhBxWeOn7l-)  
* [Intro to Networking](https://www.youtube.com/playlist?list=PLJcaPjxegjBW3oTHL02TjEw0d6nvFK_cF)  
* [Modern C++ (cpp) Concurrency](https://www.youtube.com/playlist?list=PLvv0ScY6vfd_ocTP2ZLicgqKnvq50OCXM)  
* [Operating Systems](https://www.youtube.com/playlist?list=PLWCT05ePsnGww5psXWHRLG7p30eKKt1Pd)  
* [The CPU Cache](https://www.youtube.com/playlist?list=PL38NNHQLqJqYnNrTenxBvGJSPCkV9EOWk)

### **Software Engineering & System Design**

* [Design Patterns](https://www.youtube.com/playlist?list=PLYpjLpq5ZDGsQUN89adlTUFtmT1q6-YW3)  
* [Design Patterns in Object Oriented Programming](https://www.youtube.com/playlist?list=PLrhzvIcii6GNjpARdnO4ueTUAVR9eMBpc)  
* [Golang Ecommerce Platform \- Intermediate Devs](https://www.youtube.com/playlist?list=PL5dTjWUk_cPaf5uSEmr8ilR-GtO6s7QJJ)  
* [Google Interview Questions](https://www.youtube.com/playlist?list=PLUPSMCjQ-7oc9tZlSGqgiiCGDV2jTrYkz)  
* [LLD and Machine Coding Problems | Crack SDE Interviews](https://www.youtube.com/playlist?list=PLYPO3T7Sl63u7uLLpiKCMXnRjeFIhUAvk)  
* [Master LLD Interview Questions](https://www.youtube.com/playlist?list=PLDBghK0TsNeCGMk9INNSaNZFSuTvwq-AM)  
* [Micro Frontends UI Architecture](https://www.youtube.com/playlist?list=PLrJ-e9wsoQTHueC5ub1sTvrFXitczXNdi)  
* [Modern Web Development: Front-End System Design](https://www.youtube.com/playlist?list=PLI9W87-Dqn7j_x6QtR6sUjycJR7nQLBqT)  
* [System Design](https://www.youtube.com/playlist?list=PLPkuArhPxxQGvr3qKy6bwh0ZKDiVyMOcn)  
* [System Design](https://www.youtube.com/playlist?list=PLRtLu6rCuAlkO-HiER3AKoKkSG5DPp9TX)  
* [System Design Full Course \- Mayank Joshi](https://www.youtube.com/playlist?list=PLtUBJBQF5VJgSzegWtlFiNTWehra8eSHU)  
* [System Design from First Principal](https://www.youtube.com/playlist?list=PLA12lriZjwUOHcm2HHO3OQznvfZOBjRzn)  
* [System Design Interview Prep](https://www.youtube.com/playlist?list=PLrtCHHeadkHp92TyPt1Fj452_VGLipJnL)  
* [System Design Mock Interviews](https://www.youtube.com/playlist?list=PLf3F6FcQwgqEpnucyupbIqzxyvFOz9uDq)  
* [System Design Walkthroughs](https://www.youtube.com/playlist?list=PL5q3E8eRUieWtYLmRU3z94-vGRcwKr9tM)  
* [The Ultimate Guide: Crack Coding Interviews in 3 Months](https://www.youtube.com/playlist?list=PLVItHqpXY_DDFNeS6NUUoRsloyaPRdl1l)  
* [Backend from first principles \- YouTube](https://www.youtube.com/playlist?list=PLui3EUkuMTPgZcV0QhQrOcwMPcBCcd_Q1)

# **Miscellaneous**

# **Miscellaneous**

* [Operating system : three easy pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/)  
* [High performance browser networking](https://hpbn.co/)  
* [Paper : Architecture of Database systems](https://dsf.berkeley.edu/papers/fntdb07-architecture.pdf)  
* [Red Book : Readings in Database systems](http://www.redbook.io/)  
* [https://missing.csail.mit.edu/](https://missing.csail.mit.edu/)  
* [https://github.com/practical-tutorials/project-based-learning.git](https://github.com/practical-tutorials/project-based-learning.git)  
* [AI-ML Telegram Repo](http://t.me/aibulletin56)  
* [https://fullstackopen.com/en/](https://fullstackopen.com/en/)  
* [https://udlbook.github.io/udlbook/](https://udlbook.github.io/udlbook/)  
* [https://github.com/analyticalrohit/pytorch\_fundamentals](https://github.com/analyticalrohit/pytorch_fundamentals)  
* **AI Assisted System Design:** [Clapet](https://clapet.app/d)  
* [Modern GPU Programming For MLSys](https://mlc.ai/modern-gpu-programming-for-mlsys/)  
* [awesome-gpu-engineering](https://github.com/goabiaryan/awesome-gpu-engineering)  
* [Parallel Computing: Stanford CS 149](https://gfxcourses.stanford.edu/cs149/fall25)  
* [\# 10 Open Source Repos To Replace Your $200/Month Tool Stack](https://pranathi-rai.notion.site/10-Open-Source-Repos-To-Replace-Your-200-Month-Tool-Stack-39508f00c09281d3960fd702be7caf97?utm_source=sp_auto_dm&fbclid=PAVERTVgTBMyxleHRuA2FlbQIxMABzcnRjBmFwcF9pZA81NjcwNjczNDMzNTI0MjcAAae0Z_T3aq9fxmMTGpnXyX_nlMeEixZGdn_5-93Se3SXNdfctVguK3BcOaHziA_aem_seWNid6d7AOmNpr2hfPeBA)  
* [Engineering Project Roadmap: APIs to Deep Systems](https://app.notion.com/p/Engineering-Project-Roadmap-APIs-to-Deep-Systems-39dd86ed222e810d9964c63a24e6ba5d)  
* [5-Rare-Projects](https://docs.google.com/document/d/1XC1NcQjAbfbeOxq-hskHJJT66VPCjpX0pNshDtsoCmA/edit?tab=t.0)  
* [GitHub Frontend Architecture Study List](https://beyond-the-brackets.notion.site/GitHub-Frontend-Architecture-Study-List-39c04a73276080cab949e9d916f77a74)  
* **ML-AI Book Recommendation:** [Linkedin Profile of Recommender](https://www.linkedin.com/in/suphanfayong/)  
* [C programming projects with guided practice by LabEx. · GitHub](https://github.com/labex-labs/c-practice-projects)  
* [6 AI Skills Worth More Than a Degree in 2026 🚀](https://app.notion.com/p/6-AI-Skills-Worth-More-Than-a-Degree-in-2026-39d26444682a802fa163fff84aa49729?utm_source=sp_auto_dm&fbclid=PAVERTVgTG8dJleHRuA2FlbQIxMABzcnRjBmFwcF9pZA81NjcwNjczNDMzNTI0MjcAAaczjZrPXXFx_xv5X7sZ6E4MI0tDZeYu44jVvL7eWsmmCweL5-eHKzdlTofdmA_aem_f4NOaxQx3UbTngDGvpcthw)

⭐⭐⭐

* [Complete SDE & AI Roadmap with Resources.pdf](https://drive.google.com/file/d/1t3kp2A0bofkTHpAA6vuE9_S3Fo-Mqlbu/view?usp=sharing)  
* [Holy Grail of Interview Prep A-Z Notion Link](https://jugaldb.notion.site/Holy-Grail-of-Interview-Prep-A-Z-2c6af2117b8381ae9b45c6b2d7e610d2?fbclid=PAVERTVgSVulNleHRuA2FlbQIxMABzcnRjBmFwcF9pZA81NjcwNjczNDMzNTI0MjcAAadqvjBtv8XU53d0UviPrHXkfg-r3mY4aMghTFEiYzldh-TA6PLhCmISIo7kxQ_aem_z6_DhCB912tWf4_ptPH9ww)  
* [📘 3-Year Detailed Roadmap: Stanford PhD-Level ML + Foundation Models](https://docs.google.com/document/d/1O0RqZ5A4GVY7iW6jZootd3h-ZaZ1eS7IKN4uE-69d0E/edit?tab=t.0#heading=h.ygnmn9hxsmtj)  
* [How to Pivot into an Ai:ML Engineering Role in 2026.pdf](https://drive.google.com/file/d/14aV1wmdaC3woFubcWJic1BINc5J19B6A/view?usp=sharing)  
* [LLM Open University Github Link](https://github.com/youssefHosni/LLM-Open-University-From-Begineer-to-Advanced.git)  
* [Microsoft AI-For-Beginners](https://github.com/microsoft/AI-For-Beginners)

# **Aptitude Resources**

### **Core Aptitude Topics**

* **Geometry**: [GATE Notes \- Aptitude \-Geometry.pdf](https://drive.google.com/file/d/1LJJFn25vfGk6uZes2qCxAaozy7o1q-HD/view?usp=drive_web)  
* **Percentages**: [GATE Notes \- Aptitude \- Percentages.pdf](https://drive.google.com/file/d/1370-5y5VkglQVssNmR-zCh6EwkLtmBF-/view?usp=drive_web)  
* **Averages**: [GATE Notes \- Aptitude \- Averages.pdf](https://drive.google.com/file/d/1GoOhvi_4aYpIWBWr5gKnXVFYt8l-RPCv/view?usp=drive_web)  
* **Ratio & Proportion**: [GATE Notes \- Aptitude \- Ratio & Proportion.pdf](https://drive.google.com/file/d/1whMmZ_xUCOhHAQKAa_YthJKnLrNkT62w/view?usp=drive_web)  
* **Partnership**: [GATE Notes \- Aptitude \- Partnership.pdf](https://drive.google.com/file/d/1YflCCvX-47PH2js3DnNAF2iQU0e6jQDa/view?usp=drive_web)

### **Arithmetic & Equations**

* **Alligation**: [GATE Notes \- Aptitude \- Alligation.pdf](https://drive.google.com/file/d/19CWwSKMEi3Ue-Xku1Le4EI6cNS1V4a2P/view?usp=drive_web)  
* **Time & Work**: [GATE Notes \- Aptitude \-Time & Work.pdf](https://drive.google.com/file/d/1yUjLdp9IDKwWXR-VmE-s5zeMvq_iq-cJ/view?usp=drive_web)  
* **Speed, Time & Distance**: [GATE Notes \- Aptitude \- Speed,Time & Distance.pdf](https://drive.google.com/file/d/1k-haoxayQAfWvCPCercYqDhuKdS7Dlvo/view?usp=drive_web)  
* **Profit & Loss**: [GATE Notes \- Aptitude \-Profit & Loss.pdf](https://drive.google.com/file/d/1F5nkKai4aNZBli-8kuqTyRrU_aw3NvIS/view?usp=drive_web)  
* **Simple & Compound Interest**: [GATE\_Notes\_Aptitude\_Simple\_interest\_&\_Compound\_interest.pdf](https://drive.google.com/file/d/1meQqa1SL8BvitwIFsmBva4ftXAyqiISt/view?usp=drive_web)

### **Number Theory & Formulations**

* **Number System**: [GATE Notes \- Aptitude \- Number system.pdf](https://drive.google.com/file/d/1gxPNzAedGLCe88w-CG6x4PpTL2E7G74n/view?usp=drive_web)  
* **LCM & HCF**: [GATE Notes \- Aptitude \- LCM & HCF.pdf](https://drive.google.com/file/d/1expoiz2I6z3E5AZ1BqRSQBwZCUF4o_Kv/view?usp=drive_web)  
* **Number Series**: [GATE Notes \- Aptitude \-Number series.pdf](https://drive.google.com/file/d/15mdDtlecmK945No4z6-ifEfO9Ev1i3kb/view?usp=drive_web)  
* **Formulas & Shortcuts**: [Formulas and Shortcuts for Quantitative Aptitude.pdf](https://drive.google.com/file/d/1hnIxlQ-x9w_cvAGXCfaShoTSpMhvMGKJ/view?usp=drive_web)

