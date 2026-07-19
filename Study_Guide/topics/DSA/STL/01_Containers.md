# STL Containers (interview)

> 🚪 [Start](../../../START_HERE.md) · 🗺️ [Map](../../../README.md) · 🏢 [Companies](../../../companies/README.md) · 📚 [Library](../../../library/README.md) · 🔍 [Find](../../../FIND.md)

Paraphrased from [Striver-TUF-Plus STL](https://github.com/adityanayak20/Striver-TUF-Plus/tree/main/STL) drills (`1. Pair` … `11. MultiMap`). Write the `.cpp` files in that repo; this page is oral + OA cheat sheet only.

## 1. `pair`

```cpp
pair<int,int> p = {1, 2};          // or make_pair(1, 2)
auto [a, b] = p;                   // structured bindings
p.first; p.second;
pair<int,int> q = p;               // copy
p < q;                             // lex compare: first, then second
swap(p, q);
```

**Use:** coordinates, (node, dist), sort keys. **Trap:** nested pairs get hard to read — prefer a small struct in LLD rounds.

## 2. `vector` — O(1) access / back ops

```cpp
vector<int> v = {1, 2, 3};
v.push_back(4);      // amort. O(1)
v.emplace_back(5);   // in-place
v.pop_back();
v.back(); v[i]; v.size(); v.empty(); v.capacity();
for (auto x : v) { /* ... */ }
swap(v, other);
```

**Trap:** mid `insert`/`erase` are O(n). Reallocation invalidates iterators/pointers into the buffer. `capacity()` ≥ `size()`; `shrink_to_fit` is non-binding.

## 3. `list` — O(1) ends, no random access

Doubly linked. `push_front` / `pop_front` / `front` matter. Rarely best in LeetCode OAs vs `deque`/`vector` — know it exists for splice-heavy designs.

## 4. `deque` — O(1) front **and** back

```cpp
deque<int> d;
d.push_back(1); d.push_front(0);
d.front(); d.back(); d.pop_front(); d.pop_back();
```

**Use:** sliding-window max (with indices), BFS when you need both ends. Not guaranteed one contiguous allocation.

## 5. `stack`

`push` / `emplace` · `pop` · `top` · `empty` · `size`. No iterators. Classic: next greater element, valid parentheses, monotonic stack.

## 6. `queue`

`push` / `emplace` · `pop` · `front` · `empty` · `size`. Classic: BFS. For 0-1 BFS prefer `deque`.

## 7. `priority_queue`

```cpp
priority_queue<int> maxh;                                    // largest on top
priority_queue<int, vector<int>, greater<int>> minh;         // smallest on top
maxh.push(3); maxh.top(); maxh.pop();
```

**Use:** Top-K, Dijkstra (with care), merge K lists. **Trap:** default is max-heap — saying “priority queue” in interview without min/max is incomplete. Custom types need `operator<` or comparator.

## 8. `set` / `unordered_set`

```cpp
set<int> s; s.insert(3); s.emplace(4);
s.find(3); s.count(3); s.erase(3);
auto it = s.lower_bound(3);   // first >= 3  (ORDERED only)
auto jt = s.upper_bound(3);   // first > 3
```

| | `set` | `unordered_set` |
|---|---|---|
| Order | Sorted unique | Hash unique |
| Ops | O(log n) | O(1) avg |
| Bounds | Yes | **No** |

## 9. `multiset` / `unordered_multiset`

Duplicates allowed. `equal_range(x)` → [first, last) of equals.

**Critical trap:** `ms.erase(x)` removes **all** `x`. To erase one: `ms.erase(ms.find(x))` (if found).

## 10. `map` / `unordered_map`

```cpp
map<string,int> m;
m.insert({ "a", 1 }); m.emplace("b", 2);
m["c"] = 3;                 // inserts 0 then assigns if new key — careful in probes
if (m.find("a") != m.end()) { /* ... */ }
m.lower_bound("a");         // ordered map only
```

Frequency maps → usually `unordered_map`. Need ordered keys / predecessor → `map`.

## 11. `multimap` / `unordered_multimap`

Same key many times. Prefer when you truly need multi values; else `map<K, vector<V>>` is often clearer in interviews.

## Systems / Tier S note

Firmware / SRIB-style rounds may ban STL or expect you to open-code a ring buffer / list. Still know **how** `vector`/`map` are typically implemented (contiguous growth; tree vs hash) for oral follow-ups — e.g. [vector internals discussion](https://duggal-shweta2010.medium.com/how-are-vectors-implemented-internally-in-c-5787abf1c38f), [set underlying structure](https://stackoverflow.com/questions/2558153/what-is-the-underlying-data-structure-of-a-stl-set-in-c).

## See also

[00 Quick Reference](00_STL_Quick_Reference.md) · [Algorithms & comparators](02_Algorithms_Comparators.md) · [Cpp_Fundamentals](../../Cpp_Fundamentals.md)
