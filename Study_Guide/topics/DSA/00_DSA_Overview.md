# DSA Overview
**Hub for both Systems and Software tracks** · Interview Prep pattern tables: [🎯 Interview Prep Resources](../../🎯%20Interview%20Prep%20Resources.md) §DSA

## How to use constraints

| Constraint / signal | Complexity implied | Typical patterns | Examples (LC #) |
|---|---|---|---|
| n ≤ 20 | O(2ⁿ) / O(n!) | Backtracking / bitmask | 78, 46, 39 |
| n ≤ 100 | O(n³) | Simulation / DP | 62, 72, 221 |
| n ≤ 1,000 | O(n²) | DP / pairs | 300, 1143, 72 |
| n ≤ 10⁵ | O(n log n) / O(n) | Sort / two pointers / heap | 56, 215, 347 |
| n ≤ 10⁶ | O(n) | One-pass / prefix / counting | 560, 724 |
| Sorted input | — | Binary search / two pointers | 33, 34, 167 |
| Many queries | — | Prefix / Fenwick / segment | 303, 307 |
| Tree (n nodes) | — | DFS / BFS / tree DP | 104, 236, 124 |
| Weighted graph | — | Dijkstra | 743, 787 |
| Unweighted shortest | — | BFS | 994, 127 |
| Top-K | — | Heap / Quickselect | 215, 347 |
| All possibilities | — | Backtracking | 17, 51 |
| Min/Max over choices | — | DP | 70, 322, 416 |

**Rule:** read constraints before coding — they pick the pattern.

---

## Pattern → file map

| Family | Spot it when | Strategy file |
|---|---|---|
| Arrays / strings / SW / TP | Windows, prefixes, pairs on sorted | [Arrays_Strings.md](Arrays_Strings.md) |
| Binary search | Sorted / “min X that works” | [Binary_Search.md](Binary_Search.md) |
| Stacks / queues / monotonic | Next greater, sliding max | [Stacks_Queues.md](Stacks_Queues.md) |
| Heaps | Top-K, merge streams | [Heaps.md](Heaps.md) |
| Linked lists ★ | Pointer rewiring, cycles | [Linked_Lists.md](Linked_Lists.md) |
| Trees | Traversals, BST, LCA | [Trees.md](Trees.md) |
| Graphs | Edges, components, shortest | [Graphs.md](Graphs.md) |
| DP | Overlapping subproblems | [Dynamic_Programming.md](Dynamic_Programming.md) |
| Recursion / backtracking | Subsets, permutations, boards | [Recursion_Backtracking.md](Recursion_Backtracking.md) |
| Sorting / greedy | Sort then scan, intervals | [Sorting.md](Sorting.md) |
| Bit manipulation | Masks, XOR, firmware | [Bit_Manipulation.md](Bit_Manipulation.md) |
| STL / container choice | Need hash vs tree vs heap vs deque | [STL Quick Reference](STL/00_STL_Quick_Reference.md) |

> **OA caveat:** some platforms (e.g. Samsung-style) forbid STL — see [Samsung_RD](../../companies/tier_S_semiconductor/Samsung_RD.md).

---

## Study order by track

### Software / Product SDE
Overview → [Arrays_Strings](Arrays_Strings.md) → [Binary_Search](Binary_Search.md) → [Trees](Trees.md) → [Graphs](Graphs.md) → [Dynamic_Programming](Dynamic_Programming.md) → [Stacks_Queues](Stacks_Queues.md) / [Heaps](Heaps.md) → [Recursion_Backtracking](Recursion_Backtracking.md)  
Lens: [Software_Product_SDE](../../archetypes/Software_Product_SDE.md)

**OA signal (paraphrase):** Product OAs (e.g. Amazon-style SDE OA reports) often mix medium arrays/strings, hashing, and one harder graph/DP — train timed Mediums, not only Easy grind. See [Amazon July SDE-1 OA discuss](https://leetcode.com/discuss/post/6919037/amazon-july-sde-1-oa-by-anonymous_user-7vjd/) for recent vibes only (formats change).

### Semiconductor / Systems (Tier S)
Overview → [Linked_Lists](Linked_Lists.md) ★ → [Bit_Manipulation](Bit_Manipulation.md) → [Arrays_Strings](Arrays_Strings.md) (basics) → [Heaps](Heaps.md) / [Stacks_Queues](Stacks_Queues.md) → Trees/Graphs light → DP last  
Lens: [Semiconductor_Systems](../../archetypes/Semiconductor_Systems.md)

---

## Pattern hubs (external — deep-link, do not copy)

### Hubs
- [Sean Prashad LeetCode Patterns](https://seanprashad.com/leetcode-patterns/)
- [AlgoMonster flowchart](https://algo.monster/flowchart)
- [AlgoMaster DSA patterns](https://algomaster.io/practice/dsa-patterns)
- [LearnYard DSA practice](https://learnyard.com/practice/dsa/)
- [Coding Interview Patterns (GitBook)](https://dvpr.gitbook.io/coding-interview-patterns)
- [Awesome LeetCode Resources](https://github.com/ashishps1/awesome-leetcode-resources)

### Discuss / pattern deep-dives
- [All LeetCode articles on coding patterns](https://leetcode.com/discuss/post/5366542/all-leetcode-articles-on-coding-patterns-1uhy/)
- [Decoding essential DSA patterns](https://leetcode.com/discuss/post/4336794/decoding-essential-dsa-patterns-by-bayma-jnoz/)
- [Important useful links](https://leetcode.com/discuss/post/665604/important-and-useful-links-from-all-over-ocy8/)
- [Sliding Window technique](https://leetcode.com/discuss/post/1773891/sliding-window-technique-and-question-ba-9tt4/)
- [Two Pointers problems](https://leetcode.com/discuss/post/1688903/solved-all-two-pointers-problems-in-100-z56cn/)
- [All about Binary Search](https://leetcode.com/discuss/post/6595669/all-about-binary-search-by-leadingtheaby-bdch/)
- [Binary Search for beginners](https://leetcode.com/discuss/post/691825/binary-search-for-beginners-problems-pat-0hei/)
- [Become master in Linked List (hi-malik)](https://leetcode.com/discuss/post/1800120/become-master-in-linked-list-by-hi-malik-qvdr/)
- [Master tree patterns](https://leetcode.com/discuss/post/5020529/master-tree-patterns-by-mercer80-8b0z/)
- [Graph for beginners](https://leetcode.com/discuss/post/655708/graph-for-beginners-problems-pattern-sam-06fb/)
- [DP for beginners](https://leetcode.com/discuss/post/662866/dp-for-beginners-problems-patterns-sampl-atdb/)
- [Greedy for beginners](https://leetcode.com/discuss/post/669996/greedy-for-beginners-problems-sample-sol-rf7c/)
- [Monotonic stack/queue template](https://leetcode.com/discuss/post/2347639/a-comprehensive-guide-and-template-for-m-irii/)
- [All types of bits patterns](https://leetcode.com/discuss/post/3695233/all-types-of-patterns-for-bits-manipulat-qezp/)
- [Bit manipulation basics](https://leetcode.com/discuss/post/3629570/bit-manipulation-basics-for-beginners-co-92g0/)
- [Bit manipulation patterns for interviews](https://leetcode.com/discuss/post/7025916/bit-manipulation-patterns-for-coding-int-6pap/)

### Other
- [Chanda-Abdul Sliding Window pattern (GitHub)](https://github.com/Chanda-Abdul/Several-Coding-Patterns-for-Solving-Data-Structures-and-Algorithms-Problems-during-Interviews/blob/main/%E2%9C%85%20%20Pattern%2001%20%3A%20Sliding%20Window.md)
- [Pattern tracker spreadsheet](https://docs.google.com/spreadsheets/d/1Ua4rU9cvOYNEQS2fE8J0QBFouAq_Y6ZgprII7yXBzVw/edit?gid=0#gid=0)
- [Pattern notes doc](https://docs.google.com/document/d/1nVMbnHCLcb_lp4CpG6oYe7Ln-Ssz971KjX0mjf1e4Bw/mobilebasic)
- [donnemartin / system-design-primer](https://github.com/donnemartin/system-design-primer) (Software / HLD track)

---

## AI-assisted practice
Struggle ≥20 min → ask for *hints/patterns*, not full solutions → stress-test edge cases after you solve.

## Resource Panel
- [🧮 DSA pattern hubs (library)](../../library/DSA_Pattern_Hubs.md)
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- [Complete DSA Roadmap](https://drive.google.com/file/d/10e8Q1yVymwxWhz9LgcWxwrkpW9eMxRla/view)
- [Awesome LeetCode Resources](https://github.com/ashishps1/awesome-leetcode-resources)
- Cheatsheets: [00_INDEX appendix](../../00_INDEX.md)
- Tracks: [Software_Product_SDE](../../archetypes/Software_Product_SDE.md) · [Semiconductor_Systems](../../archetypes/Semiconductor_Systems.md)
