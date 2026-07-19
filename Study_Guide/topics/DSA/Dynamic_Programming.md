# Dynamic Programming
_1D · Knapsack-style · LIS/LCS · Grid · Subsequences_

**Related:** [DSA Overview](00_DSA_Overview.md) · [Recursion_Backtracking](Recursion_Backtracking.md) · [Arrays_Strings](Arrays_Strings.md) · [Software_Product_SDE](../../archetypes/Software_Product_SDE.md)

---

## a) Why it matters

DP is the **filter** for many product-company rounds (Flipkart-class Medium–Hard, Cred explanation interviews). Systems/Tier S: learn classic 1D late — after LL, bits, arrays basics. If constraints say `n≤1000` and “min/max over choices,” think DP before exponential search.

---

## b) Concept summary

### Recipe
1. **State** — what is enough to answer a subproblem? (`i`, `i+prev`, `i+sum`, …)
2. **Transition** — how state grows from smaller states.
3. **Base** — empty / first index / zero capacity.
4. **Order** — tabulation loops must respect dependencies; or memoized recursion.
5. **Answer** — which state(s) hold the final value?

### Space
Rolling arrays when only previous row/index needed. Mention O(n) vs O(n²) space in interviews.

### Families
| Family | State sketch | Classics |
|---|---|---|
| 1D climb / rob | `dp[i]` from i−1, i−2 | [70](https://leetcode.com/problems/climbing-stairs/), [198](https://leetcode.com/problems/house-robber/) |
| Knapsack 0/1 | `dp[i][w]` take/skip | [416](https://leetcode.com/problems/partition-equal-subset-sum/), [494](https://leetcode.com/problems/target-sum/) |
| Unbounded | coin loops | [322](https://leetcode.com/problems/coin-change/), [518](https://leetcode.com/problems/coin-change-ii/) |
| LIS | `dp[i]` ending at i | [300](https://leetcode.com/problems/longest-increasing-subsequence/) |
| LCS / edit | 2D strings | [1143](https://leetcode.com/problems/longest-common-subsequence/), [72](https://leetcode.com/problems/edit-distance/) |
| Grid | `dp[r][c]` | [62](https://leetcode.com/problems/unique-paths/), [64](https://leetcode.com/problems/minimum-path-sum/), [221](https://leetcode.com/problems/maximal-square/) |
| Interval / cat | `dp[l][r]` | [516](https://leetcode.com/problems/longest-palindromic-subsequence/), [312](https://leetcode.com/problems/burst-balloons/) |

**Not DP:** pure sliding window / greedy when local choice is optimal — don’t force DP.

---

## c) Patterns → LC

| Pattern | Problems |
|---|---|
| 1D linear | [70](https://leetcode.com/problems/climbing-stairs/), [198](https://leetcode.com/problems/house-robber/), [213](https://leetcode.com/problems/house-robber-ii/), [91](https://leetcode.com/problems/decode-ways/) |
| Knapsack / subset | [416](https://leetcode.com/problems/partition-equal-subset-sum/), [494](https://leetcode.com/problems/target-sum/), [474](https://leetcode.com/problems/ones-and-zeroes/) |
| Coins | [322](https://leetcode.com/problems/coin-change/), [518](https://leetcode.com/problems/coin-change-ii/) |
| Subsequence | [300](https://leetcode.com/problems/longest-increasing-subsequence/), [1143](https://leetcode.com/problems/longest-common-subsequence/), [516](https://leetcode.com/problems/longest-palindromic-subsequence/) |
| Grid | [62](https://leetcode.com/problems/unique-paths/), [64](https://leetcode.com/problems/minimum-path-sum/), [221](https://leetcode.com/problems/maximal-square/) |
| String edit | [72](https://leetcode.com/problems/edit-distance/), [97](https://leetcode.com/problems/interleaving-string/), [115](https://leetcode.com/problems/distinct-subsequences/) |

---

## d) Problem bank

### Easy (≥5)
1. [LC 70 — Climbing Stairs](https://leetcode.com/problems/climbing-stairs/)
2. [LC 118 — Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)
3. [LC 121 — Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
4. [LC 338 — Counting Bits](https://leetcode.com/problems/counting-bits/) (bit-DP crossover)
5. [LC 509 — Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)

### Medium (≥8)
1. [LC 198 — House Robber](https://leetcode.com/problems/house-robber/)
2. [LC 322 — Coin Change](https://leetcode.com/problems/coin-change/)
3. [LC 300 — Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)
4. [LC 1143 — Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/)
5. [LC 416 — Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/)
6. [LC 62 — Unique Paths](https://leetcode.com/problems/unique-paths/)
7. [LC 64 — Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/)
8. [LC 139 — Word Break](https://leetcode.com/problems/word-break/)
9. [LC 152 — Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)
10. [LC 221 — Maximal Square](https://leetcode.com/problems/maximal-square/)

### Hard (≥5)
1. [LC 72 — Edit Distance](https://leetcode.com/problems/edit-distance/)
2. [LC 312 — Burst Balloons](https://leetcode.com/problems/burst-balloons/)
3. [LC 188 — Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/)
4. [LC 115 — Distinct Subsequences](https://leetcode.com/problems/distinct-subsequences/)
5. [LC 1235 — Maximum Profit in Job Scheduling](https://leetcode.com/problems/maximum-profit-in-job-scheduling/)

---

## e) C++ sketches

```cpp
// coin change — unbounded knapsack (min coins)
int coinChange(vector<int>& coins, int amount) {
  const int INF = 1e9;
  vector<int> dp(amount + 1, INF);
  dp[0] = 0;
  for (int a = 1; a <= amount; ++a)
    for (int c : coins)
      if (c <= a) dp[a] = min(dp[a], dp[a - c] + 1);
  return dp[amount] >= INF ? -1 : dp[amount];
}

// LCS
int longestCommonSubsequence(string A, string B) {
  int n = A.size(), m = B.size();
  vector<vector<int>> dp(n + 1, vector<int>(m + 1));
  for (int i = 1; i <= n; ++i)
    for (int j = 1; j <= m; ++j)
      dp[i][j] = A[i-1] == B[j-1]
        ? dp[i-1][j-1] + 1
        : max(dp[i-1][j], dp[i][j-1]);
  return dp[n][m];
}
```

---

## f) Boss Sheet (10 · 3 · 5)

### 10 facts
1. Overlapping subproblems + optimal substructure ⇒ DP.
2. Say state aloud before coding transitions.
3. 0/1 knapsack: iterate capacity backward if 1D; forward for unbounded.
4. LIS O(n²) DP or O(n log n) patience.
5. LCS / edit = classic 2D string DP.
6. Grid paths: only right/down ⇒ `dp[r][c]` from top/left.
7. House robber: take vs skip; circular = two linear runs.
8. Word break: `dp[i]` = whether prefix `s[0..i)` can segment.
9. Stock DP: track held / sold / cooldown states.
10. If `n≤20`, bitmask DP may beat plain exponential.

### 3 pitfalls
1. Wrong loop order (using updated cell same iteration incorrectly).
2. Confusing subsequence (non-contiguous) vs substring (contiguous — often window).
3. INIT: `dp[0]` / unreachable = INF mistakes in min-problems.

### 5 re-solve
1. [LC 198](https://leetcode.com/problems/house-robber/)
2. [LC 322](https://leetcode.com/problems/coin-change/)
3. [LC 300](https://leetcode.com/problems/longest-increasing-subsequence/)
4. [LC 1143](https://leetcode.com/problems/longest-common-subsequence/)
5. [LC 72](https://leetcode.com/problems/edit-distance/)

---

## g) Resource Panel

- [DP Cheatsheet](https://drive.google.com/file/d/1fc0H-9Uhb-dJeIKBHsovWMlGWZ3gM3Fv/view)
- [DP for Beginners — Discuss](https://leetcode.com/discuss/post/662866/dp-for-beginners-problems-patterns-sampl-atdb/)
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- [AlgoMonster flowchart](https://algo.monster/flowchart)
- Hub: [00_DSA_Overview](00_DSA_Overview.md) · [00_INDEX](../../00_INDEX.md)

_Back:_ [Topics README](../README.md) · [DSA Overview](00_DSA_Overview.md)
