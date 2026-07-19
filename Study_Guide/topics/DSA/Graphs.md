# Graphs

> 🚪 [Start](../../START_HERE.md) · 🗺️ [Map](../../README.md) · 🏢 [Companies](../../companies/README.md) · 📚 [Library](../../library/README.md) · 🔍 [Find](../../FIND.md)

**Priority:** High for Flipkart/product; Med for Tier S OA filters

## Why it matters
Product companies (Flipkart, Cred, Walmart) weight graphs heavily. Tier S less so, but BFS/DFS/cycle basics still appear. Commvault OA often hits DP/graphs.

## Concept summary
- Represent: adj list default; matrix for dense/grid.
- BFS = unweighted shortest; DFS = components/topo/cycle.
- Undirected cycle: parent-aware DFS; directed: 3-color or Kahn count.
- Topo: Kahn indegree queue; if processed < n → cycle.
- Dijkstra: min-heap; non-negative weights.
- Union-Find: path compression + union by rank.
- Grid = graph (4/8 dir).

## Pattern guides (external)

Deep-link only — BFS/DFS/topo starters live in the discuss guide; banks below stay the drill list.

- [Graph for Beginners — Discuss](https://leetcode.com/discuss/post/655708/graph-for-beginners-problems-pattern-sam-06fb/)
- Hub: [00_DSA_Overview](00_DSA_Overview.md)

## Most-asked patterns
- [LC 200 — Number of Islands](https://leetcode.com/problems/number-of-islands/)
- [LC 207 — Course Schedule](https://leetcode.com/problems/course-schedule/)
- [LC 210 — Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)
- [LC 743 — Network Delay Time](https://leetcode.com/problems/network-delay-time/)
- [LC 547 — Number of Provinces](https://leetcode.com/problems/number-of-provinces/)
- [LC 994 — Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)

## Question bank
**Easy:** LC 1971 Path Exists, 463 Island Perimeter, 733 Flood Fill, 997 Town Judge, 1791 Find Center  
**Medium:** LC 200, 207, 210, 547, 994, 785 Bipartite, 130 Surrounded, 417 Pacific Atlantic  
**Hard:** LC 127 Word Ladder, 269 Alien Dictionary (premium), 778 Swim Rising Water, 847 Shortest Path Visiting, 1192 Critical Connections  

## C++ — BFS islands
```cpp
int numIslands(vector<vector<char>>& g) {
  int m=g.size(),n=g[0].size(),c=0;
  auto bfs=[&](int i,int j){
    queue<pair<int,int>> q; q.push({i,j}); g[i][j]='0';
    int d[4][2]={{1,0},{-1,0},{0,1},{0,-1}};
    while(!q.empty()){auto [x,y]=q.front();q.pop();
      for(auto&t:d){int nx=x+t[0],ny=y+t[1];
        if(nx>=0&&ny>=0&&nx<m&&ny<n&&g[nx][ny]=='1'){g[nx][ny]='0';q.push({nx,ny});}}}
  };
  for(int i=0;i<m;i++)for(int j=0;j<n;j++)if(g[i][j]=='1'){c++;bfs(i,j);}
  return c;
}
```

## Boss Sheet
**10 facts:** adj list; BFS unweighted; DFS/topo; cycle undirected vs directed; Kahn; Dijkstra; UF; grid; bipartite 2-color; MST awareness.  
**3 pitfalls:** directed/undirected cycle mix-up; Dijkstra + negatives; forgetting visited.  
**5 re-solve:** 200, 207, 210, 743, 547.

## Resource Panel
- [Graph Cheatsheet](https://drive.google.com/file/d/1Oyu009O6X5wKw-ETC-GxsFDjHJTWDNXS/view)
- [Graph for Beginners — Discuss](https://leetcode.com/discuss/post/655708/graph-for-beginners-problems-pattern-sam-06fb/)
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- [Link registry](../../00_INDEX.md)
