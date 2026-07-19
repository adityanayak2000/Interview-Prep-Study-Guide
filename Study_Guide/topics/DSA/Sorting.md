# Sorting & Greedy
_Sort then scan · Intervals · Custom comparators · Greedy choice_

**Related:** [DSA Overview](00_DSA_Overview.md) · [Arrays_Strings](Arrays_Strings.md) · [Binary_Search](Binary_Search.md) · [Heaps](Heaps.md)

> **Greedy** lives here: interval scheduling, sort+scan, and “prove local choice” problems. Overview points here as primary discuss home.

---

## a) Why it matters

Many Mediums are “sort the array, then two pointers / sweep / greedy.” Interval merge/meeting rooms appear constantly in product OAs. Know when greedy works vs when DP is required.

---

## b) Concept summary

### Sorting toolkit
- Comparison sorts: `O(n log n)` — default.
- Counting / bucket when range small.
- Custom key: `sort(v.begin(), v.end(), cmp)` — stability matters for tie-breaks.
- Partial: `nth_element` for k-th (average linear).

### Sort then scan
After sorting, adjacent duplicates, consecutive ranges, two pointers ([LC 15](https://leetcode.com/problems/3sum/)), or greedy take/skip.

### Intervals
| Task | Sort key | Idea |
|---|---|---|
| Merge | start | sweep merge overlapping | [56](https://leetcode.com/problems/merge-intervals/) |
| Insert | — | merge into place | [57](https://leetcode.com/problems/insert-interval/) |
| Non-overlap remove | end | greedy earliest finish | [435](https://leetcode.com/problems/non-overlapping-intervals/) |
| Meeting rooms | start; heap of ends | count overlaps | [253](https://leetcode.com/problems/meeting-rooms-ii/) |

### Greedy
Exchange argument or “earliest deadline / largest first” intuition. If you can’t prove or find counterexample → try DP.

---

## c) Greedy (section)

**Spot it:** maximize/minimize with local decisions; sorting unlocks order; no need to revisit optimally.

Starters: [LC 455](https://leetcode.com/problems/assign-cookies/), [LC 860](https://leetcode.com/problems/lemonade-change/), [LC 134](https://leetcode.com/problems/gas-station/), [LC 55](https://leetcode.com/problems/jump-game/), [LC 45](https://leetcode.com/problems/jump-game-ii/), [LC 763](https://leetcode.com/problems/partition-labels/).

---

## d) Patterns → LC

| Pattern | Problems |
|---|---|
| Merge / intervals | [56](https://leetcode.com/problems/merge-intervals/), [57](https://leetcode.com/problems/insert-interval/), [435](https://leetcode.com/problems/non-overlapping-intervals/), [452](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/) |
| Sort + two pointers | [15](https://leetcode.com/problems/3sum/), [16](https://leetcode.com/problems/3sum-closest/), [18](https://leetcode.com/problems/4sum/) |
| Custom sort / rearrange | [179](https://leetcode.com/problems/largest-number/), [75](https://leetcode.com/problems/sort-colors/) |
| Greedy jump / gas | [55](https://leetcode.com/problems/jump-game/), [45](https://leetcode.com/problems/jump-game-ii/), [134](https://leetcode.com/problems/gas-station/) |
| Partition / labels | [763](https://leetcode.com/problems/partition-labels/), [621](https://leetcode.com/problems/task-scheduler/) |

---

## e) Problem bank

### Easy (≥5)
1. [LC 88 — Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)
2. [LC 242 — Valid Anagram](https://leetcode.com/problems/valid-anagram/) (count sort vibe)
3. [LC 349 — Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)
4. [LC 455 — Assign Cookies](https://leetcode.com/problems/assign-cookies/)
5. [LC 977 — Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)

### Medium (≥8)
1. [LC 56 — Merge Intervals](https://leetcode.com/problems/merge-intervals/)
2. [LC 57 — Insert Interval](https://leetcode.com/problems/insert-interval/)
3. [LC 75 — Sort Colors](https://leetcode.com/problems/sort-colors/)
4. [LC 15 — 3Sum](https://leetcode.com/problems/3sum/)
5. [LC 435 — Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)
6. [LC 452 — Minimum Number of Arrows](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)
7. [LC 55 — Jump Game](https://leetcode.com/problems/jump-game/)
8. [LC 134 — Gas Station](https://leetcode.com/problems/gas-station/)
9. [LC 763 — Partition Labels](https://leetcode.com/problems/partition-labels/)
10. [LC 179 — Largest Number](https://leetcode.com/problems/largest-number/)

### Hard (≥5)
1. [LC 45 — Jump Game II](https://leetcode.com/problems/jump-game-ii/)
2. [LC 315 — Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/)
3. [LC 164 — Maximum Gap](https://leetcode.com/problems/maximum-gap/)
4. [LC 493 — Reverse Pairs](https://leetcode.com/problems/reverse-pairs/)
5. [LC 327 — Count of Range Sum](https://leetcode.com/problems/count-of-range-sum/)

---

## f) C++ sketches

```cpp
vector<vector<int>> merge(vector<vector<int>>& iv) {
  if (iv.empty()) return {};
  sort(iv.begin(), iv.end());
  vector<vector<int>> ans{iv[0]};
  for (int i = 1; i < (int)iv.size(); ++i) {
    if (iv[i][0] <= ans.back()[1])
      ans.back()[1] = max(ans.back()[1], iv[i][1]);
    else ans.push_back(iv[i]);
  }
  return ans;
}

// non-overlapping: sort by end, greedily take
int eraseOverlapIntervals(vector<vector<int>>& iv) {
  sort(iv.begin(), iv.end(), [](auto& a, auto& b){ return a[1] < b[1]; });
  int kept = 0, end = INT_MIN;
  for (auto& x : iv) {
    if (x[0] >= end) { ++kept; end = x[1]; }
  }
  return (int)iv.size() - kept;
}
```

---

## g) Boss Sheet (10 · 3 · 5)

### 10 facts
1. `n≤1e5` + comparisons ⇒ expect O(n log n) sort somewhere.
2. Merge intervals: sort by start, extend last end.
3. Max non-overlapping: sort by end, greedy take.
4. Arrows / balloons: same earliest-end family.
5. Jump game: track farthest reachable.
6. Gas station: if total gas≥cost, unique start exists (prefix deficit).
7. Custom comparator must be strict weak ordering.
8. Sort colors = Dutch national flag (three pointers).
9. Greedy fails → look at DP (knapsack-like).
10. Count inversions / reverse pairs → merge sort tree (Hard).

### 3 pitfalls
1. Sorting by start when earliest-end greedy needed.
2. Unstable tie-break breaking relative order requirements.
3. Mutating intervals while iterating merge incorrectly.

### 5 re-solve
1. [LC 56](https://leetcode.com/problems/merge-intervals/)
2. [LC 435](https://leetcode.com/problems/non-overlapping-intervals/)
3. [LC 55](https://leetcode.com/problems/jump-game/)
4. [LC 134](https://leetcode.com/problems/gas-station/)
5. [LC 763](https://leetcode.com/problems/partition-labels/)

---

## h) Resource Panel

- [Greedy Cheatsheet](https://drive.google.com/file/d/16rArMG-reo4xZgZNcDRfIMRilrK8KPZY/view)
- [Intervals Cheatsheet](https://drive.google.com/file/d/1t3lK0hN2b0pESWkGMMHpys5iJbFVKdEI/view)
- [Greedy for Beginners — Discuss](https://leetcode.com/discuss/post/669996/greedy-for-beginners-problems-sample-sol-rf7c/)
- [Array Cheatsheet](https://drive.google.com/file/d/1PGLEG1Kn5sg6dOq_4QPykBKdvy3Qf3Mj/view)
- Hub: [00_DSA_Overview](00_DSA_Overview.md) · [00_INDEX](../../00_INDEX.md)

_Back:_ [Topics README](../README.md) · [DSA Overview](00_DSA_Overview.md)
