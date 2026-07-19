# STL Quick Reference (day-before)

> 🚪 [Start](../../../START_HERE.md) · 🗺️ [Map](../../../README.md) · 🏢 [Companies](../../../companies/README.md) · 📚 [Library](../../../library/README.md) · 🔍 [Find](../../../FIND.md)

**Source:** [Striver-TUF-Plus / STL](https://github.com/adityanayak20/Striver-TUF-Plus/tree/main/STL) (`stl.txt` + container drills) · Full notes: [01_Containers](01_Containers.md) · [02_Algorithms](02_Algorithms_Comparators.md)

> Some campus OAs (esp. Samsung-style) are **no-STL**. Confirm the platform rules before relying on these.

## Pick a container (30 seconds)

| Need | Reach for | Avoid trap |
|---|---|---|
| Dynamic array, random access | `vector` | Mid inserts are O(n); iterators invalidate on reallocation |
| Fast front+back | `deque` | Not contiguous like `vector` for &v[0] assumptions |
| LIFO | `stack` | No iterators; only `top` |
| FIFO | `queue` | No random access |
| Top-K / extreme | `priority_queue` | Default is **max-heap**; min-heap needs greater<> |
| Unique sorted keys | `set` | `unordered_set` = faster average, **no** lower_bound/order |
| Unique keys → values | `map` | `unordered_map` same unordered caveat |
| Duplicates allowed | `multiset` / `multimap` | `erase(key)` removes **all** equals — erase one via iterator |
| First/second fields | `pair` / structured bindings | Lexicographic `<` compares first then second |

## Complexities (interview table)

| | Access | Insert/erase ends | Search | Notes |
|---|---|---|---|---|
| `vector` | O(1) idx | O(1) amort. back | O(n) | Continuous |
| `deque` | O(1) idx | O(1) front&back | O(n) | Blocks |
| `list` | O(n) | O(1) ends | O(n) | Rarely needed in OA |
| `stack`/`queue` | — | O(1) | — | Adapters |
| `priority_queue` | O(1) top | O(log n) | — | Heap |
| `set`/`map` | — | O(log n) | O(log n) | Tree (RB) |
| `unordered_set`/`map` | — | O(1) avg | O(1) avg | Hash; worst O(n) |

## Must-know Algorithms checklist

- `sort(v.begin(), v.end())` · custom `bool cmp(a,b)` or lambda  
- `reverse` · `next_permutation` · `max_element` / `min_element`  
- `count` · `find` · `accumulate` (header `<numeric>`)  
- Iterators: `begin`/`end`, `rbegin`/`rend`  

## 10 oral bullets

1. `vector::size` vs `capacity` — capacity ≥ size; `push_back` may reallocate.  
2. `emplace_back` constructs in place; `push_back` may copy/move a temporary.  
3. Default `priority_queue` is max-heap; for min-heap use `priority_queue<int, vector<int>, greater<int>>`.  
4. `set`/`map` are ordered; unordered siblings trade order and `lower_bound` for average speed.  
5. `lower_bound` = first ≥ x; `upper_bound` = first > x (ordered containers only).  
6. `multiset::erase(x)` wipes every `x` — erase `ms.find(x)` once if you need one.  
7. `map[k]` **inserts default** if missing — use `find`/`count` when probing.  
8. Comparator for sort must be strict weak ordering (`<`, not `<=`).  
9. Prefer `unordered_map` for frequency maps when order does not matter.  
10. Know when **not** to use STL (SRIB / custom online judges).

## Mini practice

- Design: [LRU Cache](https://leetcode.com/problems/lru-cache/) · [LFU Cache](https://leetcode.com/problems/lfu-cache/) · [Insert Delete GetRandom O(1)](https://leetcode.com/problems/insert-delete-getrandom-o1/)  
- Hash wrappers: [Design HashMap](https://leetcode.com/problems/design-hashmap/) · [Design HashSet](https://leetcode.com/problems/design-hashset/)

## Boss Sheet (STL — 10 · 3 · 5)

**10:** size/capacity · emplace vs push · max vs min heap · set vs unordered · lower/upper bound · multiset erase · map[] insert · comparator rules · when no-STL · pair lex order  

**3 sketches:** frequency with `unordered_map` · Top-K with `priority_queue` · custom `sort` lambda  

**5 traps:** assuming unordered has bounds · multiset erase-all · forgetting min-heap typedef · iterator invalidation after `push_back` · using STL on a no-STL OA
