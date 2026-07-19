# Stacks & Queues
_Monotonic stack/queue · Next greater · Valid parentheses · Sliding window max_

> 🚪 [Start](../../START_HERE.md) · 🗺️ [Map](../../README.md) · 🏢 [Companies](../../companies/README.md) · 📚 [Library](../../library/README.md) · 🔍 [Find](../../FIND.md)

**Related:** [DSA Overview](00_DSA_Overview.md) · [Arrays_Strings](Arrays_Strings.md) · [Heaps](Heaps.md)

---

## a) Why it matters

Stacks show up as parentheses / path simplify / calculator and as **monotonic** structures for “next greater/smaller” and sliding-window extrema. Queues power BFS (see [Graphs](Graphs.md)) and level-order trees. MediaTek reports often pair LL + stack drills.

---

## b) Concept summary

### Stack vs queue
- Stack LIFO: undo, nesting, deferred smaller/greater candidates.
- Queue FIFO: BFS, sliding “order of arrival.”
- Deque: both ends — monotonic window templates.

### Classic stack
Valid parentheses ([LC 20](https://leetcode.com/problems/valid-parentheses/)), min stack ([LC 155](https://leetcode.com/problems/min-stack/)), daily temperatures / next greater ([LC 739](https://leetcode.com/problems/daily-temperatures/)), decode string ([LC 394](https://leetcode.com/problems/decode-string/)), simplify path ([LC 71](https://leetcode.com/problems/simplify-path/)).

### Queue / deque
Implement queue with stacks ([LC 232](https://leetcode.com/problems/implement-queue-using-stacks/)), design circular queue, sliding window maximum ([LC 239](https://leetcode.com/problems/sliding-window-maximum/)).

---

## c) Monotonic stack / queue (major)

**Idea:** keep indices (or values) in increasing or decreasing order so the front/back is always the next useful candidate.

| Goal | Monotonic direction | Typical |
|---|---|---|
| Next greater to right | decreasing stack of values | [739](https://leetcode.com/problems/daily-temperatures/), [496](https://leetcode.com/problems/next-greater-element-i/) |
| Next smaller | increasing stack | histogram / trapping variants |
| Sliding window maximum | decreasing deque of indices | [239](https://leetcode.com/problems/sliding-window-maximum/) |
| Largest rectangle | increasing heights stack | [84](https://leetcode.com/problems/largest-rectangle-in-histogram/) |

```cpp
// next greater element index (to the right); -1 if none
vector<int> nextGreater(vector<int>& a) {
  int n = a.size();
  vector<int> ans(n, -1);
  stack<int> st; // indices, values decreasing
  for (int i = 0; i < n; ++i) {
    while (!st.empty() && a[st.top()] < a[i]) {
      ans[st.top()] = i;
      st.pop();
    }
    st.push(i);
  }
  return ans;
}

// sliding window maximum
vector<int> maxSlidingWindow(vector<int>& a, int k) {
  deque<int> dq; // indices, a[dq] decreasing
  vector<int> ans;
  for (int i = 0; i < (int)a.size(); ++i) {
    if (!dq.empty() && dq.front() <= i - k) dq.pop_front();
    while (!dq.empty() && a[dq.back()] <= a[i]) dq.pop_back();
    dq.push_back(i);
    if (i >= k - 1) ans.push_back(a[dq.front()]);
  }
  return ans;
}
```

**Pitfalls:** store indices not values when duplicates matter; forget to expire left of window; wrong strictness `<` vs `<=`.

---

## d) Patterns → LC

| Pattern | Problems |
|---|---|
| Parentheses / nesting | [20](https://leetcode.com/problems/valid-parentheses/), [22](https://leetcode.com/problems/generate-parentheses/), [32](https://leetcode.com/problems/longest-valid-parentheses/) |
| Next greater / temps | [739](https://leetcode.com/problems/daily-temperatures/), [503](https://leetcode.com/problems/next-greater-element-ii/) |
| Monotonic + histogram | [84](https://leetcode.com/problems/largest-rectangle-in-histogram/), [85](https://leetcode.com/problems/maximal-rectangle/) |
| Calculator / eval | [224](https://leetcode.com/problems/basic-calculator/), [227](https://leetcode.com/problems/basic-calculator-ii/) |
| Queue design / BFS tool | [232](https://leetcode.com/problems/implement-queue-using-stacks/), [346](https://leetcode.com/problems/moving-average-from-data-stream/) |

---

## e) Problem bank

### Easy (≥5)
1. [LC 20 — Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
2. [LC 155 — Min Stack](https://leetcode.com/problems/min-stack/)
3. [LC 232 — Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)
4. [LC 225 — Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/)
5. [LC 496 — Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)

### Medium (≥8)
1. [LC 739 — Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)
2. [LC 394 — Decode String](https://leetcode.com/problems/decode-string/)
3. [LC 71 — Simplify Path](https://leetcode.com/problems/simplify-path/)
4. [LC 150 — Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)
5. [LC 503 — Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)
6. [LC 402 — Remove K Digits](https://leetcode.com/problems/remove-k-digits/)
7. [LC 456 — 132 Pattern](https://leetcode.com/problems/132-pattern/)
8. [LC 735 — Asteroid Collision](https://leetcode.com/problems/asteroid-collision/)
9. [LC 946 — Validate Stack Sequences](https://leetcode.com/problems/validate-stack-sequences/)

### Hard (≥5)
1. [LC 84 — Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)
2. [LC 239 — Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)
3. [LC 32 — Longest Valid Parentheses](https://leetcode.com/problems/longest-valid-parentheses/)
4. [LC 85 — Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/)
5. [LC 224 — Basic Calculator](https://leetcode.com/problems/basic-calculator/)

---

## f) Boss Sheet (10 · 3 · 5)

### 10 facts
1. Nesting / undo ⇒ stack.
2. BFS level order ⇒ queue.
3. Next greater ⇒ monotonic decreasing stack of indices.
4. Sliding window max ⇒ monotonic decreasing deque; expire `i-k`.
5. Histogram largest rectangle ⇒ increasing stack + sentinels.
6. Min stack: store pairs `(val, min_so_far)` or dual stack.
7. Circular next-greater: iterate `2n` with `i % n`.
8. Asteroid / collision problems are stack simulations.
9. Don’t confuse queue FIFO with priority queue (heap).
10. Parentheses longest valid can be stack of indices or DP.

### 3 pitfalls
1. Comparing values instead of indices in deque expiry.
2. Strict vs non-strict monotonic (`<=` pops equals — needed for max window).
3. Empty-stack access after pop in calculator / path problems.

### 5 re-solve
1. [LC 20](https://leetcode.com/problems/valid-parentheses/)
2. [LC 739](https://leetcode.com/problems/daily-temperatures/)
3. [LC 239](https://leetcode.com/problems/sliding-window-maximum/)
4. [LC 84](https://leetcode.com/problems/largest-rectangle-in-histogram/)
5. [LC 394](https://leetcode.com/problems/decode-string/)

---

## g) Resource Panel

- [Stack Cheatsheet](https://drive.google.com/file/d/1GtEmGU912cF_WGf2wzLl87gyJDJ43D_t/view)
- [Queue Cheatsheet](https://drive.google.com/file/d/19wuChBcx4puSFgryqi-GHqLiGm24vS8q/view)
- [Monotonic stack/queue template — Discuss](https://leetcode.com/discuss/post/2347639/a-comprehensive-guide-and-template-for-m-irii/)
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- Hub: [00_DSA_Overview](00_DSA_Overview.md) · [00_INDEX](../../00_INDEX.md)

_Back:_ [Topics README](../README.md) · [DSA Overview](00_DSA_Overview.md)
