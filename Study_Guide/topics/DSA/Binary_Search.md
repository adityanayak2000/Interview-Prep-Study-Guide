# Binary Search
_Classic sorted search · Binary search on answer · Rotated / bounds_

**Related:** [DSA Overview](00_DSA_Overview.md) · [Arrays_Strings](Arrays_Strings.md) · [Sorting](Sorting.md)

---

## a) Why it matters

Binary search is the default when input is sorted or the answer space is monotonic (“min X such that predicate holds”). Product OAs love rotated-array and “search on answer” (capacity, speed, days). Systems interviews use it less than LL/bits but still expect clean `lo/hi` hygiene.

---

## b) Concept summary

### Loop invariants
Pick one style and stick to it:
- **Closed `[lo, hi]`** — exit when `lo > hi`; mid may equal lo/hi.
- **Half-open `[lo, hi)`** — exit when `lo == hi`.

Always write: what is true of `lo` and `hi` after each branch?

### Overflow-safe mid
`mid = lo + (hi - lo) / 2` (never `(lo+hi)/2` on large indices).

### Lower / upper bound
- First index with `a[i] ≥ x` (lower_bound)
- First index with `a[i] > x` (upper_bound)  
C++: `std::lower_bound` / `upper_bound`. Interview: implement once cold.

### Binary search on answer
When: answer is numeric in `[L,R]`, and `ok(mid)` is monotonic (false…false,true…true or reverse). Binary search `mid`; feasibility check is often O(n) or O(n log n).

Examples: [LC 875](https://leetcode.com/problems/koko-eating-bananas/), [LC 1011](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/), [LC 410](https://leetcode.com/problems/split-array-largest-sum/).

### Rotated sorted array
Find pivot or decide which half is sorted ([LC 33](https://leetcode.com/problems/search-in-rotated-sorted-array/), [LC 153](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)).

---

## c) Patterns → LC

| Pattern | Problems |
|---|---|
| Exact / bounds | [704](https://leetcode.com/problems/binary-search/), [34](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/), [35](https://leetcode.com/problems/search-insert-position/) |
| Rotated | [33](https://leetcode.com/problems/search-in-rotated-sorted-array/), [81](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/), [153](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) |
| Peak / bitonic | [162](https://leetcode.com/problems/find-peak-element/), [852](https://leetcode.com/problems/peak-index-in-a-mountain-array/) |
| Search on answer | [875](https://leetcode.com/problems/koko-eating-bananas/), [1011](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/), [410](https://leetcode.com/problems/split-array-largest-sum/) |
| Matrix / 2D | [74](https://leetcode.com/problems/search-a-2d-matrix/), [240](https://leetcode.com/problems/search-a-2d-matrix-ii/) |
| Answer + greedy check | [1552](https://leetcode.com/problems/magnetic-force-between-two-balls/), [1482](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/) |

---

## d) Problem bank

### Easy (≥5)
1. [LC 704 — Binary Search](https://leetcode.com/problems/binary-search/)
2. [LC 35 — Search Insert Position](https://leetcode.com/problems/search-insert-position/)
3. [LC 278 — First Bad Version](https://leetcode.com/problems/first-bad-version/)
4. [LC 367 — Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/)
5. [LC 852 — Peak Index in a Mountain Array](https://leetcode.com/problems/peak-index-in-a-mountain-array/)

### Medium (≥8)
1. [LC 33 — Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
2. [LC 34 — Find First and Last Position](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
3. [LC 74 — Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)
4. [LC 153 — Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
5. [LC 162 — Find Peak Element](https://leetcode.com/problems/find-peak-element/)
6. [LC 875 — Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/)
7. [LC 1011 — Capacity To Ship Packages](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)
8. [LC 240 — Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)
9. [LC 540 — Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/)

### Hard (≥5)
1. [LC 4 — Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)
2. [LC 410 — Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/)
3. [LC 668 — Kth Smallest Number in Multiplication Table](https://leetcode.com/problems/kth-smallest-number-in-multiplication-table/)
4. [LC 719 — Find K-th Smallest Pair Distance](https://leetcode.com/problems/find-k-th-smallest-pair-distance/)
5. [LC 878 — Nth Magical Number](https://leetcode.com/problems/nth-magical-number/)

---

## e) C++ sketches

```cpp
// classic closed interval
int search(vector<int>& a, int t) {
  int lo = 0, hi = (int)a.size() - 1;
  while (lo <= hi) {
    int mid = lo + (hi - lo) / 2;
    if (a[mid] == t) return mid;
    if (a[mid] < t) lo = mid + 1;
    else hi = mid - 1;
  }
  return -1;
}

// search on answer — Koko (875)
bool ok(const vector<int>& piles, int h, int k) {
  long hours = 0;
  for (int p : piles) hours += (p + k - 1LL) / k;
  return hours <= h;
}
int minEatingSpeed(vector<int>& piles, int h) {
  int lo = 1, hi = *max_element(piles.begin(), piles.end());
  while (lo < hi) {
    int mid = lo + (hi - lo) / 2;
    if (ok(piles, h, mid)) hi = mid;
    else lo = mid + 1;
  }
  return lo;
}
```

---

## f) Boss Sheet (10 · 3 · 5)

### 10 facts
1. Sorted or monotonic predicate ⇒ binary search candidate.
2. Fix invariant: closed vs half-open — don’t mix mid-updates.
3. Safe mid: `lo + (hi-lo)/2`.
4. Lower bound = first ≥ x; upper = first > x.
5. Rotated: identify sorted half, then decide.
6. Peak: compare mid with mid+1 to pick climb direction.
7. Search-on-answer: binary on value, linear (or better) feasibility.
8. Feasibility must be monotonic — prove one sentence.
9. Duplicates in rotated (81): shrink ends carefully.
10. 2D matrix: treat as virtual 1D or staircase from corner.

### 3 pitfalls
1. Infinite loop: `lo = mid` without ensuring progress on even lengths.
2. Off-by-one returning insertion index vs found index.
3. Using float / precision when integer BS-on-answer works.

### 5 re-solve
1. [LC 34](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
2. [LC 33](https://leetcode.com/problems/search-in-rotated-sorted-array/)
3. [LC 875](https://leetcode.com/problems/koko-eating-bananas/)
4. [LC 153](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
5. [LC 410](https://leetcode.com/problems/split-array-largest-sum/) (sketch ok)

---

## g) Resource Panel

- [All About Binary Search — Discuss](https://leetcode.com/discuss/post/6595669/all-about-binary-search-by-leadingtheaby-bdch/)
- [Binary Search for Beginners — Discuss](https://leetcode.com/discuss/post/691825/binary-search-for-beginners-problems-pat-0hei/)
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- [Complete DSA Roadmap](https://drive.google.com/file/d/10e8Q1yVymwxWhz9LgcWxwrkpW9eMxRla/view)
- [Sean Prashad patterns](https://seanprashad.com/leetcode-patterns/)
- Hub: [00_DSA_Overview](00_DSA_Overview.md) · [00_INDEX](../../00_INDEX.md)

_Back:_ [Topics README](../README.md) · [DSA Overview](00_DSA_Overview.md)
