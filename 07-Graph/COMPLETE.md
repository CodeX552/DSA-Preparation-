# 🕸️ Graph — Complete Learning Guide

## 1. Graph Representation

```java
// ✅ Adjacency List (sabse common — interviews mein ye use karo)
List<List<Integer>> graph = new ArrayList<>();
int n = 5; // 5 nodes (0 to 4)
for (int i = 0; i < n; i++) graph.add(new ArrayList<>());

// Edge add karo (undirected)
graph.get(0).add(1); graph.get(1).add(0);
graph.get(0).add(2); graph.get(2).add(0);
graph.get(1).add(3); graph.get(3).add(1);

// Weighted graph ke liye: List<int[]> — {neighbor, weight}
List<List<int[]>> weightedGraph = new ArrayList<>();
```

## 2. BFS (Breadth First Search)

```java
// ✅ BFS — Level by level explore karo (Queue use)
// Time: O(V + E), Space: O(V)

public static void bfs(List<List<Integer>> graph, int start, int n) {
    boolean[] visited = new boolean[n];
    Queue<Integer> queue = new LinkedList<>();
    
    visited[start] = true;
    queue.offer(start);
    
    while (!queue.isEmpty()) {
        int node = queue.poll();          // front se nikalo
        System.out.print(node + " ");
        
        for (int neighbor : graph.get(node)) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                queue.offer(neighbor);     // unvisited neighbors add karo
            }
        }
    }
}
```

## 3. DFS (Depth First Search)

```java
// ✅ DFS — Depth mein jao pehle (Stack/Recursion use)
// Time: O(V + E), Space: O(V)

public static void dfs(List<List<Integer>> graph, int node, boolean[] visited) {
    visited[node] = true;
    System.out.print(node + " ");
    
    for (int neighbor : graph.get(node)) {
        if (!visited[neighbor]) {
            dfs(graph, neighbor, visited); // recursive call
        }
    }
}
```

## 4. Number of Islands (Grid BFS/DFS)

```java
// ✅ Problem: Grid mein kitne islands hain (connected '1' groups)
// Time: O(m * n), Space: O(m * n)

public static int numIslands(char[][] grid) {
    int count = 0;
    int m = grid.length, n = grid[0].length;
    
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            if (grid[i][j] == '1') {
                count++;                   // naya island mila!
                dfsGrid(grid, i, j, m, n); // poora island mark karo
            }
        }
    }
    return count;
}

private static void dfsGrid(char[][] grid, int i, int j, int m, int n) {
    if (i < 0 || i >= m || j < 0 || j >= n || grid[i][j] != '1') return;
    
    grid[i][j] = '0';                     // visited mark karo
    dfsGrid(grid, i + 1, j, m, n);        // neeche
    dfsGrid(grid, i - 1, j, m, n);        // upar
    dfsGrid(grid, i, j + 1, m, n);        // right
    dfsGrid(grid, i, j - 1, m, n);        // left
}
```

## 5. Cycle Detection

```java
// ✅ Undirected Graph mein cycle detect karo
public static boolean hasCycleUndirected(List<List<Integer>> graph, int n) {
    boolean[] visited = new boolean[n];
    for (int i = 0; i < n; i++) {
        if (!visited[i]) {
            if (dfsCycle(graph, i, -1, visited)) return true;
        }
    }
    return false;
}

private static boolean dfsCycle(List<List<Integer>> graph, int node, int parent, boolean[] visited) {
    visited[node] = true;
    for (int neighbor : graph.get(node)) {
        if (!visited[neighbor]) {
            if (dfsCycle(graph, neighbor, node, visited)) return true;
        } else if (neighbor != parent) {
            return true; // visited hai aur parent nahi → cycle!
        }
    }
    return false;
}
```

## 6. Topological Sort (DAG)

```java
// ✅ Topological Sort — BFS (Kahn's Algorithm)
// Directed Acyclic Graph (DAG) ke liye — dependency ordering
// Time: O(V + E)

public static List<Integer> topologicalSort(List<List<Integer>> graph, int n) {
    int[] inDegree = new int[n];
    for (int i = 0; i < n; i++)
        for (int neighbor : graph.get(i))
            inDegree[neighbor]++;           // incoming edges count karo
    
    Queue<Integer> queue = new LinkedList<>();
    for (int i = 0; i < n; i++)
        if (inDegree[i] == 0) queue.offer(i); // 0 indegree wale pehle
    
    List<Integer> result = new ArrayList<>();
    while (!queue.isEmpty()) {
        int node = queue.poll();
        result.add(node);
        for (int neighbor : graph.get(node)) {
            inDegree[neighbor]--;
            if (inDegree[neighbor] == 0) queue.offer(neighbor);
        }
    }
    
    return result.size() == n ? result : new ArrayList<>(); // cycle check
}
```

## 7. Dijkstra's Algorithm (Shortest Path)

```java
// ✅ Dijkstra — Weighted graph mein shortest path
// Time: O((V + E) log V), Space: O(V)

public static int[] dijkstra(List<List<int[]>> graph, int src, int n) {
    int[] dist = new int[n];
    Arrays.fill(dist, Integer.MAX_VALUE);
    dist[src] = 0;
    
    // Min-heap: {distance, node}
    PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> a[0] - b[0]);
    pq.offer(new int[]{0, src});
    
    while (!pq.isEmpty()) {
        int[] curr = pq.poll();
        int d = curr[0], u = curr[1];
        
        if (d > dist[u]) continue;         // already better path mila
        
        for (int[] edge : graph.get(u)) {
            int v = edge[0], w = edge[1];   // neighbor, weight
            if (dist[u] + w < dist[v]) {
                dist[v] = dist[u] + w;     // shorter path mila!
                pq.offer(new int[]{dist[v], v});
            }
        }
    }
    
    return dist;
}
```

---

## 🎯 Graph Problem Identification
| Keyword | Approach |
|---------|----------|
| "shortest path" (unweighted) | BFS |
| "shortest path" (weighted) | Dijkstra |
| "connected components" | DFS/BFS |
| "cycle detection" | DFS with parent / colors |
| "dependency order" | Topological Sort |
| "grid traversal" | DFS/BFS on 2D array |
| "minimum spanning tree" | Kruskal / Prim |

---

> **Next:** [PROBLEMS.md](PROBLEMS.md) 💪
