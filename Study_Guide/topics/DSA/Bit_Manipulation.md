# Bit Manipulation ★ (Tier S)
_Masks · XOR tricks · Firmware-facing bit ops · Counting bits_

> 🚪 [Start](../../START_HERE.md) · 🗺️ [Map](../../README.md) · 🏢 [Companies](../../companies/README.md) · 📚 [Library](../../library/README.md) · 🔍 [Find](../../FIND.md)

**Related:** [DSA Overview](00_DSA_Overview.md) · [Cpp_Fundamentals](../Cpp_Fundamentals.md) · [Semiconductor_Systems](../../archetypes/Semiconductor_Systems.md)

---

## a) Why it matters

For **semiconductor / firmware** tracks, bit fluency is as important as linked lists. Register maps, flags, and “set/clear/toggle bit N” appear in Qualcomm / TI / Micron-style loops alongside C pointers.

| Company | Why bits show up | File |
|---|---|---|
| **Qualcomm** | Low-level C, masks in coding + systems chat | [Qualcomm](../../companies/tier_S_semiconductor/Qualcomm.md) |
| **Texas Instruments** | Embedded C; bit-fields and masks in MCQ + coding | [Texas Instruments](../../companies/tier_S_semiconductor/Texas_Instruments.md) |
| **Micron** | Firmware emphasis: bit-level thinking | [Micron](../../companies/tier_S_semiconductor/Micron.md) |
| **Arm / AMD / Intel** | Architecture + embedded software interviews | Tier S board |

Product track: XOR / single-number / subset masks still appear; prioritize after arrays/BS/DP.

---

## b) Concept summary

### Operators (C/C++)
`& | ^ ~ << >>` — know precedence; prefer unsigned or explicit casts when shifting into sign bit. Arithmetic vs logical right shift: interview-safe to use unsigned or mask.

### Core idioms
| Idiom | Code | Use |
|---|---|---|
| Set bit i | `x \| (1u << i)` | flags |
| Clear bit i | `x & ~(1u << i)` | |
| Toggle | `x ^ (1u << i)` | |
| Test | `(x >> i) & 1` | |
| Clear lowest set | `x & (x - 1)` | Brian Kernighan count |
| Lowest set bit | `x & -x` | (two’s complement) |
| Power of two | `x && !(x & (x-1))` | [231](https://leetcode.com/problems/power-of-two/) |

### XOR
`a^a=0`, `a^0=a`, commutative. Single number ([LC 136](https://leetcode.com/problems/single-number/)), missing number, find two uniques ([LC 260](https://leetcode.com/problems/single-number-iii/)).

### Bitmask DP / subsets
`n≤20`: iterate `mask` in `[0, 1<<n)`; submasks; popcount. Bridge to [Recursion_Backtracking](Recursion_Backtracking.md).

---

## c) Patterns → LC

| Pattern | Problems |
|---|---|
| Counting / Kernighan | [191](https://leetcode.com/problems/number-of-1-bits/), [338](https://leetcode.com/problems/counting-bits/), [461](https://leetcode.com/problems/hamming-distance/) |
| XOR | [136](https://leetcode.com/problems/single-number/), [137](https://leetcode.com/problems/single-number-ii/), [268](https://leetcode.com/problems/missing-number/), [260](https://leetcode.com/problems/single-number-iii/) |
| Power / math bits | [231](https://leetcode.com/problems/power-of-two/), [342](https://leetcode.com/problems/power-of-four/), [371](https://leetcode.com/problems/sum-of-two-integers/) |
| Subsets / gray | [78](https://leetcode.com/problems/subsets/) (bitmask), [89](https://leetcode.com/problems/gray-code/) |
| Mask tricks | [201](https://leetcode.com/problems/bitwise-and-of-numbers-range/), [318](https://leetcode.com/problems/maximum-product-of-word-lengths/), [187](https://leetcode.com/problems/repeated-dna-sequences/) |

---

## d) Problem bank

### Easy (≥5)
1. [LC 136 — Single Number](https://leetcode.com/problems/single-number/)
2. [LC 191 — Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)
3. [LC 231 — Power of Two](https://leetcode.com/problems/power-of-two/)
4. [LC 268 — Missing Number](https://leetcode.com/problems/missing-number/)
5. [LC 338 — Counting Bits](https://leetcode.com/problems/counting-bits/)
6. [LC 461 — Hamming Distance](https://leetcode.com/problems/hamming-distance/)

### Medium (≥8)
1. [LC 137 — Single Number II](https://leetcode.com/problems/single-number-ii/)
2. [LC 260 — Single Number III](https://leetcode.com/problems/single-number-iii/)
3. [LC 78 — Subsets](https://leetcode.com/problems/subsets/) (bitmask solution)
4. [LC 201 — Bitwise AND of Numbers Range](https://leetcode.com/problems/bitwise-and-of-numbers-range/)
5. [LC 318 — Maximum Product of Word Lengths](https://leetcode.com/problems/maximum-product-of-word-lengths/)
6. [LC 371 — Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/)
7. [LC 187 — Repeated DNA Sequences](https://leetcode.com/problems/repeated-dna-sequences/)
8. [LC 89 — Gray Code](https://leetcode.com/problems/gray-code/)
9. [LC 393 — UTF-8 Validation](https://leetcode.com/problems/utf-8-validation/)

### Hard (≥5)
1. [LC 995 — Minimum Number of K Consecutive Bit Flips](https://leetcode.com/problems/minimum-number-of-k-consecutive-bit-flips/)
2. [LC 464 — Can I Win](https://leetcode.com/problems/can-i-win/) (bitmask DP)
3. [LC 847 — Shortest Path Visiting All Nodes](https://leetcode.com/problems/shortest-path-visiting-all-nodes/)
4. [LC 982 — Triples with Bitwise AND Equal To Zero](https://leetcode.com/problems/triples-with-bitwise-and-equal-to-zero/)
5. [LC 1178 — Number of Valid Words for Each Puzzle](https://leetcode.com/problems/number-of-valid-words-for-each-puzzle/)

---

## e) C++ sketches

```cpp
int hammingWeight(uint32_t n) {
  int c = 0;
  while (n) { n &= n - 1; ++c; }
  return c;
}

int singleNumber(vector<int>& a) {
  int x = 0;
  for (int v : a) x ^= v;
  return x;
}

// subsets via masks
vector<vector<int>> subsets(vector<int>& a) {
  int n = a.size();
  vector<vector<int>> ans;
  for (int m = 0; m < (1 << n); ++m) {
    vector<int> cur;
    for (int i = 0; i < n; ++i)
      if (m & (1 << i)) cur.push_back(a[i]);
    ans.push_back(cur);
  }
  return ans;
}
```

**Firmware interview drill (say aloud):** given `uint32_t reg`, set bits 3 and 7, clear bit 1, toggle bit 0 — write the three expressions without hesitating.

---

## f) Boss Sheet (10 · 3 · 5)

### 10 facts
1. Prefer `1u << i` over signed `1 << i` for bit i≥31 care.
2. `x & (x-1)` clears lowest set bit; loop = popcount.
3. `x & -x` isolates lowest set bit (two’s complement).
4. XOR cancels pairs; chain for single unique.
5. Power of two: single bit set.
6. Bitmask subsets when `n≤20`.
7. Range AND: find common prefix of bits.
8. Sum without `+`: XOR + carry `<<1` loop.
9. Signed right-shift is implementation-defined historically — know your compiler; prefer unsigned for bit puzzles.
10. Register talk: OR to set, AND-NOT to clear, XOR to toggle.

### 3 pitfalls
1. Shifting into/beyond sign bit on signed `int`.
2. Using arithmetic `>>` when logical zero-fill intended.
3. Off-by-one on bit index (0-based vs datasheet bit 0).

### 5 re-solve
1. [LC 136](https://leetcode.com/problems/single-number/)
2. [LC 191](https://leetcode.com/problems/number-of-1-bits/)
3. [LC 338](https://leetcode.com/problems/counting-bits/)
4. [LC 260](https://leetcode.com/problems/single-number-iii/)
5. Live: set/clear/toggle bits on a `uint32_t` (whiteboard)

---

## g) Resource Panel

- [Bit/Math Cheatsheet](https://drive.google.com/file/d/1gPXenSrwfnme7NSrGBt4DnCWKBkza8-m/view)
- [All Types of Patterns for Bits — Discuss](https://leetcode.com/discuss/post/3695233/all-types-of-patterns-for-bits-manipulat-qezp/)
- [Bit Manipulation Basics — Discuss](https://leetcode.com/discuss/post/3629570/bit-manipulation-basics-for-beginners-co-92g0/)
- [Bit Manipulation Patterns for Coding Interviews — Discuss](https://leetcode.com/discuss/post/7025916/bit-manipulation-patterns-for-coding-int-6pap/)
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- Companies: [Qualcomm](../../companies/tier_S_semiconductor/Qualcomm.md) · [TI](../../companies/tier_S_semiconductor/Texas_Instruments.md) · [Micron](../../companies/tier_S_semiconductor/Micron.md)
- Hub: [00_DSA_Overview](00_DSA_Overview.md) · [00_INDEX](../../00_INDEX.md)

_Back:_ [Topics README](../README.md) · [DSA Overview](00_DSA_Overview.md)
