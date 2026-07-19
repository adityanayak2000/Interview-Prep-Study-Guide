# STL Algorithms & Comparators

> 🚪 [Start](../../../START_HERE.md) · 🗺️ [Map](../../../README.md) · 🏢 [Companies](../../../companies/README.md) · 📚 [Library](../../../library/README.md) · 🔍 [Find](../../../FIND.md)

Paraphrased from [Striver-TUF-Plus STL / 12. Algorithms](https://github.com/adityanayak20/Striver-TUF-Plus/tree/main/STL/12.%20Algorithms). Prefer writing the repo `.cpp` drills once; keep this for recall.

Headers you’ll name in interviews: `<algorithm>`, `<numeric>` (`accumulate`), `<functional>` (`greater<>`).

## Core algorithms checklist

```cpp
#include <algorithm>
#include <numeric>
#include <vector>
using namespace std;

vector<int> v = {3, 1, 4, 1, 5};

sort(v.begin(), v.end());                    // ascending
sort(v.begin(), v.end(), greater<int>());  // descending

reverse(v.begin(), v.end());

auto mx = *max_element(v.begin(), v.end());
auto mn = *min_element(v.begin(), v.end());

int ones = count(v.begin(), v.end(), 1);
auto it = find(v.begin(), v.end(), 4);       // iterator or end()

int sum = accumulate(v.begin(), v.end(), 0);

// next_permutation: needs sorted ascending first for full tour
sort(v.begin(), v.end());
do {
  // use v
} while (next_permutation(v.begin(), v.end()));
```

**Note:** Interview “power” is usually `1LL *` / binary exponentiation — C `pow` is floating; know integer fast-pow for modular problems.

## Custom comparator

Strict weak ordering: return whether `a` should come **before** `b`. Use `<`, not `<=` (equality loops / undefined behavior risk).

```cpp
// Sort pairs by second ascending; tie-break first descending
sort(p.begin(), p.end(), [](const pair<int,int>& a, const pair<int,int>& b) {
  if (a.second != b.second) return a.second < b.second;
  return a.first > b.first;
});

// Or named function
bool cmp(const pair<int,int>& a, const pair<int,int>& b) {
  return a.first < b.first;
}
sort(p.begin(), p.end(), cmp);
```

For `priority_queue` with custom order, pass the comparator type as the third template argument (not only a lambda in older styles — know both patterns you use locally).

## When interviewers push

| They ask | You say |
|---|---|
| Stable vs unstable sort | `sort` not stable; `stable_sort` preserves equal-key order (slower constant) |
| Why cmp must be strict | `<=` breaks partitioning assumptions |
| `lower_bound` after sort | On a **sorted** vector / on `set`/`map` — binary search position |
| `next_permutation` count | n! permutations if all unique |

## Tie-back to DSA topics

- Sorting patterns → [Sorting.md](../Sorting.md)  
- Heap / Top-K → [Heaps.md](../Heaps.md) + `priority_queue`  
- Sliding window max → often `deque` indices, not `priority_queue` alone  

## Resource Panel

- [Striver-TUF-Plus STL Algorithms folder](https://github.com/adityanayak20/Striver-TUF-Plus/tree/main/STL/12.%20Algorithms)  
- [00 Quick Reference](00_STL_Quick_Reference.md) · [01 Containers](01_Containers.md)  
- [DSA Overview](../00_DSA_Overview.md)
