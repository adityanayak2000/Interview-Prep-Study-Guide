# Heaps
_Top-K · Two heaps · Merge K · Priority queue patterns_

> 🚪 [Start](../../START_HERE.md) · 🗺️ [Map](../../README.md) · 🏢 [Companies](../../companies/README.md) · 📚 [Library](../../library/README.md) · 🔍 [Find](../../FIND.md)

**Related:** [DSA Overview](00_DSA_Overview.md) · [Stacks_Queues](Stacks_Queues.md) · [Sorting](Sorting.md) · [Linked_Lists](Linked_Lists.md) (merge K)

---

## a) Why it matters

Heaps solve “keep extreme K”, streaming medians, and merging sorted streams in `O(n log k)`. Common in product OAs; systems tracks see merge-K and Top-K less often than LL but still useful for [LC 23](https://leetcode.com/problems/merge-k-sorted-lists/) style interviews.

---

## b) Concept summary

### Priority queue in C++
`priority_queue<T>` is a **max-heap** by default. Min-heap: `priority_queue<T, vector<T>, greater<T>>`.

### When heap vs sort
- Need all sorted once → sort O(n log n).
- Streaming / only Top-K / online → heap O(n log k) with k ≪ n.
- Quickselect average O(n) for exact k-th — mention as alternative ([LC 215](https://leetcode.com/problems/kth-largest-element-in-an-array/)).

### Two heaps (median)
Max-heap for lower half, min-heap for upper; rebalance sizes ([LC 295](https://leetcode.com/problems/find-median-from-data-stream/)).

### Merge K
Push heads (or first of each array) into min-heap; pop-push next ([LC 23](https://leetcode.com/problems/merge-k-sorted-lists/), [LC 373](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/)).

---

## c) Patterns → LC

| Pattern | Problems |
|---|---|
| Kth / Top-K | [215](https://leetcode.com/problems/kth-largest-element-in-an-array/), [347](https://leetcode.com/problems/top-k-frequent-elements/), [973](https://leetcode.com/problems/k-closest-points-to-origin/) |
| Frequency heap | [347](https://leetcode.com/problems/top-k-frequent-elements/), [451](https://leetcode.com/problems/sort-characters-by-frequency/), [621](https://leetcode.com/problems/task-scheduler/) |
| Two heaps | [295](https://leetcode.com/problems/find-median-from-data-stream/), [480](https://leetcode.com/problems/sliding-window-median/) |
| Merge / multi-pointer | [23](https://leetcode.com/problems/merge-k-sorted-lists/), [373](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/) |
| Scheduling | [253](https://leetcode.com/problems/meeting-rooms-ii/) (premium), [621](https://leetcode.com/problems/task-scheduler/), [1834](https://leetcode.com/problems/single-threaded-cpu/) |

---

## d) Problem bank

### Easy (≥5)
1. [LC 1046 — Last Stone Weight](https://leetcode.com/problems/last-stone-weight/)
2. [LC 703 — Kth Largest Element in a Stream](https://leetcode.com/problems/kth-largest-element-in-a-stream/)
3. [LC 506 — Relative Ranks](https://leetcode.com/problems/relative-ranks/)
4. [LC 1337 — The K Weakest Rows in a Matrix](https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/)
5. [LC 2357 — Make Array Zero by Subtracting Equal Amounts](https://leetcode.com/problems/make-array-zero-by-subtracting-equal-amounts/)

### Medium (≥8)
1. [LC 215 — Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)
2. [LC 347 — Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
3. [LC 973 — K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)
4. [LC 378 — Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)
5. [LC 451 — Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)
6. [LC 621 — Task Scheduler](https://leetcode.com/problems/task-scheduler/)
7. [LC 767 — Reorganize String](https://leetcode.com/problems/reorganize-string/)
8. [LC 373 — Find K Pairs with Smallest Sums](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/)
9. [LC 692 — Top K Frequent Words](https://leetcode.com/problems/top-k-frequent-words/)

### Hard (≥5)
1. [LC 23 — Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)
2. [LC 295 — Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)
3. [LC 480 — Sliding Window Median](https://leetcode.com/problems/sliding-window-median/)
4. [LC 502 — IPO](https://leetcode.com/problems/ipo/)
5. [LC 407 — Trapping Rain Water II](https://leetcode.com/problems/trapping-rain-water-ii/)

---

## e) C++ sketches

```cpp
// Top-K frequent — min-heap of size k on (freq, val)
vector<int> topKFrequent(vector<int>& nums, int k) {
  unordered_map<int,int> freq;
  for (int x : nums) ++freq[x];
  using P = pair<int,int>;
  priority_queue<P, vector<P>, greater<P>> pq; // (freq, val)
  for (auto& [v, f] : freq) {
    pq.push({f, v});
    if ((int)pq.size() > k) pq.pop();
  }
  vector<int> ans;
  while (!pq.empty()) { ans.push_back(pq.top().second); pq.pop(); }
  return ans;
}

// Kth largest — min-heap size k
int findKthLargest(vector<int>& a, int k) {
  priority_queue<int, vector<int>, greater<int>> pq;
  for (int x : a) {
    pq.push(x);
    if ((int)pq.size() > k) pq.pop();
  }
  return pq.top();
}
```

---

## f) Boss Sheet (10 · 3 · 5)

### 10 facts
1. Default C++ `priority_queue` = max-heap.
2. Top-K small: min-heap of size K; Top-K large: max-heap of size K (for smallest K).
3. Kth largest ≡ min-heap size k; top is answer.
4. Frequency + heap or bucket sort for Top-K frequent.
5. Two heaps for running median; keep size diff ≤ 1.
6. Merge K lists: heap of current heads O(N log k).
7. Task scheduler: greedy + max-heap of remaining counts.
8. “Meeting rooms II” style: sort starts, min-heap of end times.
9. Lazy deletion sometimes needed for sliding median (hard).
10. Prefer heap when k ≪ n; else sort may be simpler/faster constants.

### 3 pitfalls
1. Using max-heap when you needed min-heap of size k (wrong Kth).
2. Storing only values when ties need stable secondary keys (words).
3. Forgetting custom comparator captures indices for merge-K.

### 5 re-solve
1. [LC 215](https://leetcode.com/problems/kth-largest-element-in-an-array/)
2. [LC 347](https://leetcode.com/problems/top-k-frequent-elements/)
3. [LC 23](https://leetcode.com/problems/merge-k-sorted-lists/)
4. [LC 295](https://leetcode.com/problems/find-median-from-data-stream/)
5. [LC 973](https://leetcode.com/problems/k-closest-points-to-origin/)

---

## g) Resource Panel

- [Heap Cheatsheet](https://drive.google.com/file/d/1DU11jH301gG0C35SLmptIRIkz5ui0STQ/view)
- [Sean Prashad LeetCode Patterns](https://seanprashad.com/leetcode-patterns/) (heap / Top-K tags)
- [DSA Overview hubs](00_DSA_Overview.md)
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- [00_INDEX](../../00_INDEX.md)

_Back:_ [Topics README](../README.md) · [DSA Overview](00_DSA_Overview.md)
