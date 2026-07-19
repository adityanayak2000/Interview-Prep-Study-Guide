# Recursion & Backtracking
_Subsets · Permutations · Combination sum · Boards / N-Queens_

**Related:** [DSA Overview](00_DSA_Overview.md) · [Dynamic_Programming](Dynamic_Programming.md) · [Bit_Manipulation](Bit_Manipulation.md) (bitmask subsets)

---

## a) Why it matters

When `n ≤ 20` and you need **all** configurations (or search with prune), backtracking is the tool. Product rounds: subsets/permutations/combination-sum; harder: N-Queens, sudoku, word search. Systems: less frequent than LL/bits — still know the template cold.

---

## b) Concept summary

### Template
```text
void dfs(state):
  if goal: record; return
  for choice in options:
    if invalid: continue
    apply choice
    dfs(next)
    undo choice   // backtrack
```

### Pruning
Skip duplicates (sort + `i>start && a[i]==a[i-1]`), cut when partial sum exceeds target, mark visited on grids.

### Recursion depth
Call stack O(n) / O(board). Mention iterative alternatives only if asked; interviews usually want clean DFS.

### Subsets vs combinations vs permutations
| Family | Order matters? | Reuse element? | Classic |
|---|---|---|---|
| Subsets | no | no (each index once) | [78](https://leetcode.com/problems/subsets/) |
| Combinations | no | no | [77](https://leetcode.com/problems/combinations/) |
| Combination sum | no | yes / no variants | [39](https://leetcode.com/problems/combination-sum/), [40](https://leetcode.com/problems/combination-sum-ii/) |
| Permutations | yes | no | [46](https://leetcode.com/problems/permutations/) |

---

## c) Patterns → LC

| Pattern | Problems |
|---|---|
| Subsets / bitmask | [78](https://leetcode.com/problems/subsets/), [90](https://leetcode.com/problems/subsets-ii/), [784](https://leetcode.com/problems/letter-case-permutation/) |
| Permutations | [46](https://leetcode.com/problems/permutations/), [47](https://leetcode.com/problems/permutations-ii/) |
| Combination sum | [39](https://leetcode.com/problems/combination-sum/), [40](https://leetcode.com/problems/combination-sum-ii/), [216](https://leetcode.com/problems/combination-sum-iii/) |
| Partition / palindrome | [131](https://leetcode.com/problems/palindrome-partitioning/), [93](https://leetcode.com/problems/restore-ip-addresses/) |
| Board / path | [51](https://leetcode.com/problems/n-queens/), [37](https://leetcode.com/problems/sudoku-solver/), [79](https://leetcode.com/problems/word-search/) |
| Phone / generate | [17](https://leetcode.com/problems/letter-combinations-of-a-phone-number/), [22](https://leetcode.com/problems/generate-parentheses/) |

---

## d) Problem bank

### Easy (≥5)
1. [LC 344 — Reverse String](https://leetcode.com/problems/reverse-string/) (recursion warm-up)
2. [LC 509 — Fibonacci](https://leetcode.com/problems/fibonacci-number/)
3. [LC 21 — Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/) (recursive)
4. [LC 206 — Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) (recursive)
5. [LC 70 — Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) (recursion→DP bridge)

### Medium (≥8)
1. [LC 78 — Subsets](https://leetcode.com/problems/subsets/)
2. [LC 46 — Permutations](https://leetcode.com/problems/permutations/)
3. [LC 39 — Combination Sum](https://leetcode.com/problems/combination-sum/)
4. [LC 17 — Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)
5. [LC 22 — Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)
6. [LC 79 — Word Search](https://leetcode.com/problems/word-search/)
7. [LC 131 — Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/)
8. [LC 90 — Subsets II](https://leetcode.com/problems/subsets-ii/)
9. [LC 40 — Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)

### Hard (≥5)
1. [LC 51 — N-Queens](https://leetcode.com/problems/n-queens/)
2. [LC 37 — Sudoku Solver](https://leetcode.com/problems/sudoku-solver/)
3. [LC 52 — N-Queens II](https://leetcode.com/problems/n-queens-ii/)
4. [LC 212 — Word Search II](https://leetcode.com/problems/word-search-ii/)
5. [LC 60 — Permutation Sequence](https://leetcode.com/problems/permutation-sequence/)

---

## e) C++ sketches

```cpp
// subsets
void dfs(int i, vector<int>& a, vector<int>& cur, vector<vector<int>>& ans) {
  if (i == (int)a.size()) { ans.push_back(cur); return; }
  dfs(i + 1, a, cur, ans);          // skip
  cur.push_back(a[i]);              // take
  dfs(i + 1, a, cur, ans);
  cur.pop_back();
}

// combination sum (reuse allowed)
void dfs(int start, int remain, vector<int>& a, vector<int>& cur, vector<vector<int>>& ans) {
  if (remain == 0) { ans.push_back(cur); return; }
  for (int i = start; i < (int)a.size(); ++i) {
    if (a[i] > remain) break; // a sorted
    cur.push_back(a[i]);
    dfs(i, remain - a[i], a, cur, ans); // i not i+1 → reuse
    cur.pop_back();
  }
}
```

---

## f) Boss Sheet (10 · 3 · 5)

### 10 facts
1. `n≤20` / “all possibilities” ⇒ backtracking (or bitmask).
2. Always undo mutations (pop / unmark).
3. Sort + skip duplicates for II-variants.
4. Subsets: take/skip or build with start index.
5. Permutations: swap-in-place or used[] array.
6. Combination sum: reuse → pass `i`; no reuse → `i+1`.
7. Parentheses: track open/close counts; never close>open.
8. Word search: mark visited, recurse 4-dir, unmark.
9. N-Queens: cols + diag sets for O(1) prune.
10. If overlapping subproblems + count/opt — consider DP instead of listing.

### 3 pitfalls
1. Forgetting to backtrack (shared `cur` polluted).
2. Duplicate answers without sort/skip.
3. Infinite reuse loop (forgot to advance start).

### 5 re-solve
1. [LC 78](https://leetcode.com/problems/subsets/)
2. [LC 46](https://leetcode.com/problems/permutations/)
3. [LC 39](https://leetcode.com/problems/combination-sum/)
4. [LC 22](https://leetcode.com/problems/generate-parentheses/)
5. [LC 51](https://leetcode.com/problems/n-queens/) (sketch)

---

## g) Resource Panel

- [Recursion/Backtracking Cheatsheet](https://drive.google.com/file/d/1zXVZNiAKTHX39mvugroPntfrrROV8GEx/view)
- [Decoding Essential DSA Patterns — Discuss](https://leetcode.com/discuss/post/4336794/decoding-essential-dsa-patterns-by-bayma-jnoz/)
- [Sean Prashad patterns](https://seanprashad.com/leetcode-patterns/)
- [AlgoMaster DSA patterns](https://algomaster.io/practice/dsa-patterns)
- Hub: [00_DSA_Overview](00_DSA_Overview.md) · [00_INDEX](../../00_INDEX.md)

_Back:_ [Topics README](../README.md) · [DSA Overview](00_DSA_Overview.md)
