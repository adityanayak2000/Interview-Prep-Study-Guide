# Linked Lists ★
_Highest-priority DSA topic for semiconductor OA & systems interviews · M.E. CS_

> 🚪 [Start](../../START_HERE.md) · 🗺️ [Map](../../README.md) · 🏢 [Companies](../../companies/README.md) · 📚 [Library](../../library/README.md) · 🔍 [Find](../../FIND.md)

**Tier S weight:** Critical · **Related:** [DSA Overview](00_DSA_Overview.md) · [C++ Fundamentals](../Cpp_Fundamentals.md) · [OOPs & LLD](../OOPs_LLD.md) (LRU)

---

## a) Why it matters

> **Flag:** Linked lists are the single highest-leverage DSA topic for semiconductor and systems recruiters on this list. Multiple campus reports say “practice maximum questions of linked lists.” Product companies ask them too — for Qualcomm / TI / MediaTek they are nearly non-negotiable.

| Company | Why lists show up | File |
|---|---|---|
| **Qualcomm** | Tech R1 often opens with LL coding (Nth from end, detect/length of cycle). OA + interviews reward pointer fluency. | [Qualcomm](../../companies/tier_S_semiconductor/Qualcomm.md) |
| **Texas Instruments** | C mastery = applied pointer surgery: reverse, merge, cycle, midpoint live. | [Texas Instruments](../../companies/tier_S_semiconductor/Texas_Instruments.md) |
| **MediaTek** | Past candidates: drill **maximum** LL + stack; both OA and interviews. | [MediaTek](../../companies/tier_S_semiconductor/MediaTek.md) |
| **AMD** | Systems/firmware tracks use lists to probe NULL checks, in-place mutation, no leaks. | [AMD](../../companies/tier_S_semiconductor/AMD.md) |
| **Arm** | Same pointer-fluency bar; list bugs = visible segfaults / infinite loops. | [Arm](../../companies/tier_S_semiconductor/Arm.md) |

**Also high:** Intel, Micron, Sandisk/WD, Infineon — firmware/systems paths. **Product crossover:** Flipkart, Visa, Walmart, PayPal, ServiceNow — reverse / merge-k / **LRU (LC 146)** as LLD+DSA hybrid.

**Why “★ highest” for this cohort:** Target mix is semiconductor-heavy vs a pure FAANG plan. List bugs kill interviews because they are *visible* and reveal a weak mental model of heap objects.

**Recurring Qualcomm / MediaTek ladder (master cold):**
detect cycle (fast/slow) → find entrance (Floyd) → length of cycle → remove cycle.

---

## b) Concept summary

### Node model
```cpp
struct ListNode {
    int val;
    ListNode* next;
    ListNode(int x) : val(x), next(nullptr) {}
};
// Doubly-linked: ListNode* prev;  // LRU, some design problems
```
Always **draw boxes and arrows** before coding. Say aloud: “who points to whom after this line?”

### Dummy / sentinel
`ListNode dummy(0); dummy.next = head;` — avoids special-casing empty list or head deletion/swap. Return `dummy.next`. Default move when head may change ([LC 19](https://leetcode.com/problems/remove-nth-node-from-end-of-list/), [LC 24](https://leetcode.com/problems/swap-nodes-in-pairs/), [LC 25](https://leetcode.com/problems/reverse-nodes-in-k-group/)).

### Fast / slow (Floyd)
| Goal | Setup | When done |
|---|---|---|
| Midpoint | slow+1, fast+2 | `fast` (or `fast->next`) null → slow is mid |
| Cycle detect | same | pointers meet ⇒ cycle ([LC 141](https://leetcode.com/problems/linked-list-cycle/)) |
| Cycle entrance | after meet, reset one to head; both +1 | meet again = entrance ([LC 142](https://leetcode.com/problems/linked-list-cycle-ii/)) |
| Nth from end | advance fast by `n`, then both | `fast` at end → slow before target |

Even-length midpoint: decide if you need first or second mid (problem-dependent).

### In-place reversal
Save `nxt` → rewire `cur->next = prev` → advance. Variants:
- Full: [LC 206](https://leetcode.com/problems/reverse-linked-list/)
- Sublist `[left, right]`: [LC 92](https://leetcode.com/problems/reverse-linked-list-ii/)
- K-group: [LC 25](https://leetcode.com/problems/reverse-nodes-in-k-group/) — reverse each full block of k; leave remainder

### Recursive tricks
Reverse / merge / remove via recursion. Depth **O(n)** stack — mention risk in systems interviews; prefer iterative unless asked.

### Merge
- Two sorted: dummy + compare pick ([LC 21](https://leetcode.com/problems/merge-two-sorted-lists/))
- K sorted: min-heap of heads **O(N log k)** or divide-and-conquer ([LC 23](https://leetcode.com/problems/merge-k-sorted-lists/))
- Sort list = merge-sort on lists ([LC 148](https://leetcode.com/problems/sort-list/))

### Intersecting lists
Align lengths, or two-pointer switch: `a = a ? a->next : headB` ([LC 160](https://leetcode.com/problems/intersection-of-two-linked-lists/)). Same idea on arrays: [LC 287](https://leetcode.com/problems/find-the-duplicate-number/) (Floyd on nums).

### Palindrome / reorder / partition
- Palindrome: mid + reverse 2nd half + compare ([LC 234](https://leetcode.com/problems/palindrome-linked-list/)); optionally restore
- Reorder: mid + reverse 2nd + weave ([LC 143](https://leetcode.com/problems/reorder-list/))
- Partition around value x ([LC 86](https://leetcode.com/problems/partition-list/))

### Copy with random / flatten
- Random: HashMap old→new, or weave interleaved clones ([LC 138](https://leetcode.com/problems/copy-list-with-random-pointer/))
- Multilevel flatten ([LC 430](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/))

### LRU Cache
DLL + `unordered_map<key, node*>`; move-to-front on get/put; evict tail ([LC 146](https://leetcode.com/problems/lru-cache/)). LFU adds freq buckets ([LC 460](https://leetcode.com/problems/lfu-cache/)).

### Complexity & bugs
Most classics: **O(n) time, O(1) extra**. Recursion O(n) space. Merge-k heap O(N log k).

**Classic bugs:** lost `next` before rewiring · null deref · off-by-one Nth-from-end · forgot to update head after full reverse · cycle false positives if `fast` not checked · dummy not returned.

### Six drawings you must code cold
1. Reverse full  
2. Reverse left–right  
3. Reverse k-group  
4. Cycle detect + entrance  
5. Merge two + merge k  
6. LRU get/put  

---

## c) Most-asked patterns

| # | Pattern | Anchor problems |
|---|---|---|
| 1 | Reverse full / partial / k-group | [LC 206 — Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/), [LC 92 — Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/), [LC 25 — Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/) |
| 2 | Fast/slow mid / cycle | [LC 876 — Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/), [LC 141 — Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/), [LC 142 — Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/), [LC 202 — Happy Number](https://leetcode.com/problems/happy-number/) |
| 3 | Nth from end / remove | [LC 19 — Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/), [LC 2095 — Delete the Middle Node](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/) |
| 4 | Merge sorted | [LC 21 — Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/), [LC 23 — Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) |
| 5 | Palindrome / reorder / partition | [LC 234 — Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/), [LC 143 — Reorder List](https://leetcode.com/problems/reorder-list/), [LC 86 — Partition List](https://leetcode.com/problems/partition-list/) |
| 6 | Add / swap nodes | [LC 2 — Add Two Numbers](https://leetcode.com/problems/add-two-numbers/), [LC 445 — Add Two Numbers II](https://leetcode.com/problems/add-two-numbers-ii/), [LC 24 — Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/) |
| 7 | Intersect / Floyd on array | [LC 160 — Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/), [LC 287 — Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/) |
| 8 | Copy random / flatten | [LC 138 — Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/), [LC 430 — Flatten a Multilevel Doubly Linked List](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/) |
| 9 | Sort list (merge sort) | [LC 148 — Sort List](https://leetcode.com/problems/sort-list/) |
| 10 | Design LRU / LFU | [LC 146 — LRU Cache](https://leetcode.com/problems/lru-cache/), [LC 460 — LFU Cache](https://leetcode.com/problems/lfu-cache/) |

**OA tip:** If `n ≤ 1e5`, stay O(n) or O(n log n). Pointer problems that “feel” O(n²) almost always have an O(n) two-pointer rewrite.

---

## d) Question bank

### Easy (≥5)
1. [LC 206 — Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
2. [LC 21 — Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)
3. [LC 141 — Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)
4. [LC 876 — Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)
5. [LC 234 — Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)
6. [LC 83 — Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/) _(bonus)_
7. [LC 203 — Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/) _(bonus)_

### Medium (≥8)
1. [LC 19 — Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)
2. [LC 142 — Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)
3. [LC 92 — Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/)
4. [LC 2 — Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)
5. [LC 143 — Reorder List](https://leetcode.com/problems/reorder-list/)
6. [LC 148 — Sort List](https://leetcode.com/problems/sort-list/)
7. [LC 138 — Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)
8. [LC 146 — LRU Cache](https://leetcode.com/problems/lru-cache/)
9. [LC 24 — Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/) _(bonus)_
10. [LC 61 — Rotate List](https://leetcode.com/problems/rotate-list/) _(bonus)_
11. [LC 86 — Partition List](https://leetcode.com/problems/partition-list/) _(bonus)_

### Hard (≥5)
1. [LC 25 — Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)
2. [LC 23 — Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)
3. [LC 460 — LFU Cache](https://leetcode.com/problems/lfu-cache/)
4. [LC 432 — All O(1) Data Structure](https://leetcode.com/problems/all-oone-data-structure/)
5. [LC 287 — Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/) _(Floyd on array — same intuition)_

**Drill order for Tier S (1 week):** Easy bank → cycle ladder (141→142) → 19 + 92 → 143/148 → 25 → 23 → 146.

---

## e) C++ code snippets

### 1) Reverse iterative — [LC 206](https://leetcode.com/problems/reverse-linked-list/)
```cpp
ListNode* reverseList(ListNode* head) {
    ListNode* prev = nullptr;
    while (head) {
        ListNode* nxt = head->next;  // save
        head->next = prev;           // rewire
        prev = head;
        head = nxt;
    }
    return prev;  // new head
}
```

### 2) Detect cycle + entrance (Floyd) — [LC 142](https://leetcode.com/problems/linked-list-cycle-ii/)
```cpp
ListNode* detectCycle(ListNode* head) {
    ListNode *slow = head, *fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) {          // meet inside cycle
            slow = head;             // reset one to head
            while (slow != fast) {
                slow = slow->next;
                fast = fast->next;
            }
            return slow;             // entrance
        }
    }
    return nullptr;                  // no cycle
}
```
**Oral 90s:** Meeting point is `μ + a·λ` into the walk; resetting to head walks `μ` more steps so both land on entrance. Cycle length: from meeting point, count until revisit.

### 3) Reverse K-group (sketch) — [LC 25](https://leetcode.com/problems/reverse-nodes-in-k-group/)
```cpp
// Helper: reverse [head .. tail) ; returns new head of segment
ListNode* reverseSeg(ListNode* head, ListNode* tail) {
    ListNode* prev = tail;           // after reverse, segment points to old "after"
    while (head != tail) {
        ListNode* nxt = head->next;
        head->next = prev;
        prev = head;
        head = nxt;
    }
    return prev;
}

ListNode* reverseKGroup(ListNode* head, int k) {
    ListNode dummy(0); dummy.next = head;
    ListNode* pre = &dummy;
    while (true) {
        ListNode* tail = pre;
        for (int i = 0; i < k; ++i) {  // need k nodes
            tail = tail->next;
            if (!tail) return dummy.next;  // remainder stays
        }
        ListNode* nxt = tail->next;        // node after this group
        ListNode* newHead = reverseSeg(pre->next, nxt);
        ListNode* newTail = pre->next;     // old head is new tail
        pre->next = newHead;
        pre = newTail;                     // advance group cursor
    }
}
```
**Interview note:** Count-first (only reverse full groups). Dummy makes reconnecting groups clean. Can also reverse by walking `k` then calling the LC 206 reverse on that window.

---

## Systems follow-ups (after coding)

Ask yourself / expect from Arm / AMD / Qualcomm interviewers:
- How many cache lines does pointer-chasing touch vs a contiguous array scan?
- Intrusive kernel lists (`list_head`) vs allocator-backed nodes?
- Who owns `new` nodes — `delete`, unique ownership, or pool?
- What breaks if the list is shared across threads without a lock?

---

## f) Boss Sheet

<a id="boss-sheet"></a>

### 10 facts
1. **Dummy** when head may change; return `dummy.next`.
2. Reverse: save `nxt` → `cur->next = prev` → advance.
3. Fast/slow meet ⇒ cycle; reset one to head ⇒ **entrance**.
4. Midpoint: fast×2, slow×1; decide first vs second mid on even length.
5. Nth from end: maintain gap of `n` between two pointers (+ dummy for delete).
6. Merge two sorted: dummy + compare-and-pick.
7. Merge k sorted: min-heap of heads, **O(N log k)**.
8. Palindrome / reorder: mid + reverse second half + compare / weave.
9. **LRU** = DLL + hashmap; move node to head on access; evict tail.
10. Draw pointers; **never** overwrite `next` before saving it.

### 3 pitfalls
1. **Lost next** — rewiring without `nxt = cur->next` → orphaned / cycle / segfault.
2. **Off-by-one Nth / k-group** — wrong gap or reversing a partial last group when problem forbids it.
3. **Forgot new head** — after full reverse, return `prev`, not the original `head` (now a tail).

### 5 re-solve the night before
1. [LC 206 — Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) (iterative, no peek)
2. [LC 142 — Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/) (explain entrance aloud)
3. [LC 19 — Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/) (dummy + gap)
4. [LC 25 — Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/) (sketch is enough if timed)
5. [LC 146 — LRU Cache](https://leetcode.com/problems/lru-cache/) (from scratch ≤25 min)

---

## Pattern guides (external)

Deep-link only — paraphrase templates; do not paste articles.

- [Become Master in Linked List — hi-malik (Discuss)](https://leetcode.com/discuss/post/1800120/become-master-in-linked-list-by-hi-malik-qvdr/)
- Hub pattern indexes: [00_DSA_Overview](00_DSA_Overview.md)

## g) Resource Panel

- [Linked List Cheatsheet](https://drive.google.com/file/d/1lDSq_JKCrY0L-j81UGmMI1nAqCU_cSJx/view)
- [Complete DSA Roadmap](https://drive.google.com/file/d/10e8Q1yVymwxWhz9LgcWxwrkpW9eMxRla/view)
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- [Become Master in Linked List — Discuss](https://leetcode.com/discuss/post/1800120/become-master-in-linked-list-by-hi-malik-qvdr/)
- [Awesome LeetCode](https://github.com/ashishps1/awesome-leetcode-resources)
- [Qualcomm LC archive (legacy)](https://drive.google.com/drive/folders/1UhFhWBPzqy7onkduX74I8k2TDmvSaA5Z)
- [STL Quick Reference](STL/00_STL_Quick_Reference.md) · [practice repo](https://github.com/adityanayak20/Striver-TUF-Plus/tree/main/STL)
- [Link registry](../../00_INDEX.md) · [Interview Prep Resources Context](../../../Interview_Prep_Resources_Context.md)

---

## Definition of done

- [ ] Six canonical drawings from memory  
- [ ] Full Easy / Medium / Hard bank touched once  
- [ ] LRU from scratch in ≤25 minutes  
- [ ] Floyd entrance explained aloud in ≤90 seconds  
- [ ] Reverse k-group sketch written without notes  

_Back:_ [Topics README](../README.md) · [DSA Overview](00_DSA_Overview.md)
