# Arrays & Strings
_Sliding Window · Two Pointers · Hash / Prefix · Highest volume for Software track_

**Related:** [DSA Overview](00_DSA_Overview.md) · [Binary Search](Binary_Search.md) · [Sorting](Sorting.md) · [Software_Product_SDE](../../archetypes/Software_Product_SDE.md)

---

## a) Why it matters

Arrays/strings are the **volume** topic for product OAs and most first coding rounds. Semiconductor tracks still need basics (prefix, two pointers on arrays) but deprioritize hard string DP.

| Signal | Pattern family |
|---|---|
| Subarray / substring with constraint | Sliding window |
| Sorted array, pairs, reverse, partition | Two pointers |
| Count / anagram / complement | Hash map |
| Range sums, balance, “at index i” | Prefix / difference |

---

## b) Concept summary

### Index hygiene
Always state aloud: inclusive vs exclusive end; empty / single-element; overflow on `mid = lo + (hi-lo)/2` when using binary-style scans.

### Prefix sums
`pref[0]=0; pref[i+1]=pref[i]+a[i]` → range sum `[L,R)` in O(1). Variants: prefix XOR, running balance (parentheses / ±1).

### Hash maps on arrays
Frequency maps, complement lookup ([LC 1](https://leetcode.com/problems/two-sum/)), anagram signatures ([LC 49](https://leetcode.com/problems/group-anagrams/)), prefix-sum + map for subarray sum K ([LC 560](https://leetcode.com/problems/subarray-sum-equals-k/)).

---

## c) Sliding Window (major)

**When:** contiguous subarray/substring; maximize/minimize length or count windows satisfying a predicate.

| Flavor | Move | Examples |
|---|---|---|
| Fixed size k | slide right, drop left | max sum of k, [LC 1456](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/) |
| Variable — expand/shrink | grow `r`, shrink `l` while invalid | [LC 3](https://leetcode.com/problems/longest-substring-without-repeating-characters/), [LC 209](https://leetcode.com/problems/minimum-size-subarray-sum/) |
| At most / exactly K distinct | freq map + shrink | [LC 340](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/) (premium), [LC 992](https://leetcode.com/problems/subarrays-with-k-different-integers/) |
| Window + deque for min/max | monotonic deque | [LC 239](https://leetcode.com/problems/sliding-window-maximum/) → also [Stacks_Queues](Stacks_Queues.md) |

**Template (variable):**
```cpp
int l = 0;
for (int r = 0; r < n; ++r) {
  // add a[r] into window state
  while (/* window invalid */ && l <= r) {
    // remove a[l]; ++l;
  }
  // update answer from valid window [l, r]
}
```

**Pitfalls:** off-by-one on shrink; forgetting to update answer when window becomes valid; using nested O(n²) when O(n) window works (`n ≤ 1e5`).

---

## d) Two Pointers (major)

**When:** sorted array; opposite ends; same-direction “slow/fast write”; partition.

| Flavor | Idea | Examples |
|---|---|---|
| Opposite ends | lo/hi meet | [LC 167](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/), [LC 11](https://leetcode.com/problems/container-with-most-water/) |
| Same direction | slow write pointer | [LC 26](https://leetcode.com/problems/remove-duplicates-from-sorted-array/), [LC 283](https://leetcode.com/problems/move-zeroes/) |
| Partition | Dutch / <pivot | [LC 75](https://leetcode.com/problems/sort-colors/) |
| Sorted merge | two arrays | [LC 88](https://leetcode.com/problems/merge-sorted-array/) |
| String reverse / palindrome | ends inward | [LC 125](https://leetcode.com/problems/valid-palindrome/), [LC 344](https://leetcode.com/problems/reverse-string/) |

```cpp
// opposite ends — two sum sorted
int lo = 0, hi = n - 1;
while (lo < hi) {
  long s = a[lo] + a[hi];
  if (s == target) { /* found */ break; }
  if (s < target) ++lo; else --hi;
}
```

---

## e) Pattern → LC (clickable)

| Pattern | Starter problems |
|---|---|
| Fixed window | [643](https://leetcode.com/problems/maximum-average-subarray-i/), [1456](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/) |
| Longest valid window | [3](https://leetcode.com/problems/longest-substring-without-repeating-characters/), [904](https://leetcode.com/problems/fruit-into-baskets/) |
| Shortest valid window | [209](https://leetcode.com/problems/minimum-size-subarray-sum/), [76](https://leetcode.com/problems/minimum-window-substring/) |
| Two pointers opposite | [167](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/), [15](https://leetcode.com/problems/3sum/) |
| Prefix + hash | [560](https://leetcode.com/problems/subarray-sum-equals-k/), [525](https://leetcode.com/problems/contiguous-array/) |
| Anagram / string hash | [242](https://leetcode.com/problems/valid-anagram/), [438](https://leetcode.com/problems/find-all-anagrams-in-a-string/) |

---

## f) Problem bank

### Easy (≥5)
1. [LC 1 — Two Sum](https://leetcode.com/problems/two-sum/)
2. [LC 26 — Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)
3. [LC 283 — Move Zeroes](https://leetcode.com/problems/move-zeroes/)
4. [LC 344 — Reverse String](https://leetcode.com/problems/reverse-string/)
5. [LC 643 — Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)
6. [LC 242 — Valid Anagram](https://leetcode.com/problems/valid-anagram/)

### Medium (≥8)
1. [LC 3 — Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
2. [LC 11 — Container With Most Water](https://leetcode.com/problems/container-with-most-water/)
3. [LC 15 — 3Sum](https://leetcode.com/problems/3sum/)
4. [LC 49 — Group Anagrams](https://leetcode.com/problems/group-anagrams/)
5. [LC 76 — Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)
6. [LC 209 — Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)
7. [LC 438 — Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)
8. [LC 560 — Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)
9. [LC 904 — Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/)

### Hard (≥5)
1. [LC 42 — Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)
2. [LC 76](https://leetcode.com/problems/minimum-window-substring/) (if Medium felt easy — treat as Hard drill)
3. [LC 239 — Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)
4. [LC 992 — Subarrays with K Different Integers](https://leetcode.com/problems/subarrays-with-k-different-integers/)
5. [LC 30 — Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)

---

## g) C++ sketches

```cpp
// LC 3 — longest substring without repeating
int lengthOfLongestSubstring(string s) {
  vector<int> last(256, -1);
  int ans = 0, l = 0;
  for (int r = 0; r < (int)s.size(); ++r) {
    unsigned char c = s[r];
    if (last[c] >= l) l = last[c] + 1;
    last[c] = r;
    ans = max(ans, r - l + 1);
  }
  return ans;
}

// LC 560 — subarray sum equals k
int subarraySum(vector<int>& a, int k) {
  unordered_map<long,int> pref{{0,1}};
  long sum = 0; int ans = 0;
  for (int x : a) {
    sum += x;
    ans += pref[sum - k];
    ++pref[sum];
  }
  return ans;
}
```

---

## h) Boss Sheet (10 · 3 · 5)

### 10 facts
1. Constraints `n≤1e5` ⇒ aim O(n) / O(n log n) — nested scan is usually wrong.
2. Contiguous + constraint ⇒ try sliding window before DP.
3. Fixed window: maintain sum/count; drop left when advancing.
4. Variable window: expand `r`, shrink `l` while invalid.
5. “Exactly K” often = `atMost(K) − atMost(K−1)`.
6. Sorted pairs ⇒ opposite two pointers (or BS).
7. In-place filter ⇒ slow write pointer.
8. Prefix + hashmap for subarray sum / balance.
9. Anagram window ⇒ fixed freq signature of length `|p|`.
10. Sliding max/min over window ⇒ monotonic deque ([Stacks_Queues](Stacks_Queues.md)).

### 3 pitfalls
1. Updating answer when window is still invalid.
2. Forgetting to move `l` after duplicate/hash hit (stuck O(n²) mentally).
3. Integer overflow on sums / mid indices.

### 5 re-solve the night before
1. [LC 3](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
2. [LC 15](https://leetcode.com/problems/3sum/)
3. [LC 76](https://leetcode.com/problems/minimum-window-substring/)
4. [LC 560](https://leetcode.com/problems/subarray-sum-equals-k/)
5. [LC 42](https://leetcode.com/problems/trapping-rain-water/) or [LC 239](https://leetcode.com/problems/sliding-window-maximum/)

---

## i) Resource Panel

- [Array Cheatsheet](https://drive.google.com/file/d/1PGLEG1Kn5sg6dOq_4QPykBKdvy3Qf3Mj/view)
- [String Cheatsheet](https://drive.google.com/file/d/1GgKKAJcFRJBfSHbsTO_H0UKUYXqefp-i/view)
- [Sliding Window — Discuss](https://leetcode.com/discuss/post/1773891/sliding-window-technique-and-question-ba-9tt4/)
- [Two Pointers — Discuss](https://leetcode.com/discuss/post/1688903/solved-all-two-pointers-problems-in-100-z56cn/)
- [Chanda-Abdul Sliding Window pattern (GitHub)](https://github.com/Chanda-Abdul/Several-Coding-Patterns-for-Solving-Data-Structures-and-Algorithms-Problems-during-Interviews/blob/main/%E2%9C%85%20%20Pattern%2001%20%3A%20Sliding%20Window.md)
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- Hub: [00_DSA_Overview](00_DSA_Overview.md) · [00_INDEX](../../00_INDEX.md)

_Back:_ [Topics README](../README.md) · [DSA Overview](00_DSA_Overview.md)
