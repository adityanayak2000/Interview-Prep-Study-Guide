# Trees

> 🚪 [Start](../../START_HERE.md) · 🗺️ [Map](../../README.md) · 🏢 [Companies](../../companies/README.md) · 📚 [Library](../../library/README.md) · 🔍 [Find](../../FIND.md)

**Priority:** High for product + Tier S coding rounds

## Why it matters
Asked across [Qualcomm](../../companies/tier_S_semiconductor/Qualcomm.md), [Intel](../../companies/tier_S_semiconductor/Intel.md), [AMD](../../companies/tier_S_semiconductor/AMD.md), and product companies. MediaTek OA sometimes includes tree-traversal MCQs.

## Concept summary
- Traversals: pre/in/post (DFS), level-order (BFS queue).
- BST: inorder sorted; validate with (min,max) range — not only local compares.
- Height vs depth; diameter = max leftHeight+rightHeight over nodes (careful return values).
- LCA: recurse; split subtrees → root is LCA.
- Path sum / root-to-leaf; construct from pre+in using index map.
- Serialize with null markers.

## Pattern guides (external)

Deep-link only — use for pattern catalogs; keep solving from the bank below.

- [Master Tree Patterns — Discuss](https://leetcode.com/discuss/post/5020529/master-tree-patterns-by-mercer80-8b0z/)
- Hub: [00_DSA_Overview](00_DSA_Overview.md)

## Most-asked patterns
- [LC 104 — Max Depth](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
- [LC 102 — Level Order](https://leetcode.com/problems/binary-tree-level-order-traversal/)
- [LC 236 — LCA](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)
- [LC 543 — Diameter](https://leetcode.com/problems/diameter-of-binary-tree/)
- [LC 98 — Validate BST](https://leetcode.com/problems/validate-binary-search-tree/)
- [LC 105 — Construct from Pre+In](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)
- [LC 124 — Binary Tree Max Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)

## Question bank
**Easy:** LC 104, 226 Invert, 101 Symmetric, 112 Path Sum, 144 Preorder  
**Medium:** LC 102, 236, 98, 105, 199 Right Side View, 230 Kth Smallest BST, 437 Path Sum III, 114 Flatten  
**Hard:** LC 124, 297 Serialize, 968 Camera, 99 Recover BST, 337 House Robber III  

## C++ — diameter sketch
```cpp
int ans = 0;
int height(TreeNode* n) {
  if (!n) return 0;
  int L = height(n->left), R = height(n->right);
  ans = max(ans, L + R);
  return 1 + max(L, R);
}
```

## Boss Sheet
**10 facts:** traversals; BST inorder; LCA split rule; diameter pitfalls; path sum DFS; construct hashmap; validate range; BFS level; balanced −1 height; Morris rare.  
**3 pitfalls:** diameter return confusion; BST local-only check; null bases.  
**5 re-solve:** 104, 236, 543, 98, 105.

## Resource Panel
- [Binary Tree Cheatsheet](https://drive.google.com/file/d/1hHBgLeTgRiQsmy_3OrcvOXZSJogl2zdQ/view)
- [Master Tree Patterns — Discuss](https://leetcode.com/discuss/post/5020529/master-tree-patterns-by-mercer80-8b0z/)
- [DSA Roadmap](https://drive.google.com/file/d/10e8Q1yVymwxWhz9LgcWxwrkpW9eMxRla/view)
- [Link registry](../../00_INDEX.md)
