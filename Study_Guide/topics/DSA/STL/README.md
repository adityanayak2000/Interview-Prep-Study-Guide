# C++ STL — Quick reference (Study Guide)

Interview-oriented notes distilled from the maintainer Striver / TUF-plus practice tree:

**Source practice repo:** [adityanayak20/Striver-TUF-Plus — STL](https://github.com/adityanayak20/Striver-TUF-Plus/tree/main/STL)

| Doc | Use when |
|---|---|
| [00_STL_Quick_Reference.md](00_STL_Quick_Reference.md) | Day-before: pick the container + big-O |
| [01_Containers.md](01_Containers.md) | Pair → MultiMap ops & traps |
| [02_Algorithms_Comparators.md](02_Algorithms_Comparators.md) | `sort`, perms, custom comparators |

## Caveats

- **Samsung SRIB / some platform OAs forbid STL** — practice manual arrays, recursion, and your own DS before those OAs. See [Samsung_RD](../../../companies/tier_S_semiconductor/Samsung_RD.md).
- These MDs are **quick-refs**, not a substitute for writing the `.cpp` drills in the GitHub STL folder.
- Prefer `emplace_*` when constructing in place; know when `unordered_*` loses `lower_bound` / order.

## Related

- [C++ Fundamentals](../Cpp_Fundamentals.md) · [DSA Overview](../00_DSA_Overview.md) · [Heaps](../Heaps.md) · [Stacks & Queues](../Stacks_Queues.md)
