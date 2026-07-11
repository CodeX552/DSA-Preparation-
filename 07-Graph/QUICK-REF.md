# 🕸️ Graph — Quick Reference

## 📝 Templates
### BFS
```java
Queue<Integer> q = new LinkedList<>();
boolean[] visited = new boolean[n];
q.offer(start); visited[start] = true;
while (!q.isEmpty()) {
    int node = q.poll();
    for (int nei : graph.get(node))
        if (!visited[nei]) { visited[nei] = true; q.offer(nei); }
}
```
### DFS
```java
void dfs(int node, boolean[] visited) {
    visited[node] = true;
    for (int nei : graph.get(node))
        if (!visited[nei]) dfs(nei, visited);
}
```
### Dijkstra
```java
PriorityQueue<int[]> pq = new PriorityQueue<>((a,b)->a[0]-b[0]);
int[] dist = new int[n]; Arrays.fill(dist, INF); dist[src]=0;
pq.offer(new int[]{0, src});
// poll, skip stale, relax edges
```

## 🔑 When to Use What
| Problem Type | Algorithm |
|-------------|-----------|
| Shortest (unweighted) | BFS |
| Shortest (weighted, positive) | Dijkstra |
| Shortest (negative weights) | Bellman-Ford |
| Dependency ordering | Topological Sort |
| Connected components | DFS/BFS/Union-Find |
| Cycle (undirected) | DFS with parent |
| Cycle (directed) | DFS with colors (white/gray/black) |
| MST | Kruskal / Prim |

---
