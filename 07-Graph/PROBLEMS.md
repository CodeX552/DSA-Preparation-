# 🕸️ Graph — Practice Problems

## 🟢 Easy
| # | Problem | Pattern | Hint |
|---|---------|---------|------|
| 1 | [Flood Fill](https://leetcode.com/problems/flood-fill/) | DFS/BFS | Grid DFS, change color |

## 🟡 Medium
| # | Problem | Pattern | Hint |
|---|---------|---------|------|
| 2 | [Number of Islands](https://leetcode.com/problems/number-of-islands/) | DFS/BFS | Connected components in grid |
| 3 | [Clone Graph](https://leetcode.com/problems/clone-graph/) | BFS + HashMap | Map old→new, BFS traverse |
| 4 | [Course Schedule](https://leetcode.com/problems/course-schedule/) | Topological Sort | Cycle detection in DAG |
| 5 | [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/) | Topological Sort | Kahn's BFS, return order |
| 6 | [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/) | Multi-source BFS | All rotten = sources, BFS |
| 7 | [Pacific Atlantic Water](https://leetcode.com/problems/pacific-atlantic-water-flow/) | DFS | DFS from borders inward |
| 8 | [Graph Valid Tree](https://leetcode.com/problems/graph-valid-tree/) | DFS/Union-Find | n-1 edges + connected + no cycle |
| 9 | [Network Delay Time](https://leetcode.com/problems/network-delay-time/) | Dijkstra | Shortest path from source |
| 10 | [Surrounded Regions](https://leetcode.com/problems/surrounded-regions/) | DFS | Mark border O's, flip rest |

## 🔴 Hard
| # | Problem | Pattern | Hint |
|---|---------|---------|------|
| 11 | [Word Ladder](https://leetcode.com/problems/word-ladder/) | BFS | Each word = node, 1 char diff = edge |
| 12 | [Alien Dictionary](https://leetcode.com/problems/alien-dictionary/) | Topological Sort | Compare adjacent words for ordering |

## ✅ Tracker
- [ ] Number of Islands
- [ ] Course Schedule
- [ ] Rotting Oranges
- [ ] Dijkstra (Network Delay Time)

> **Revise:** [QUICK-REF.md](QUICK-REF.md) 📝
