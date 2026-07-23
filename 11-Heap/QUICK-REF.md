# ⛰️ Heap — Quick Reference

## ⚡ Java PriorityQueue
```java
PriorityQueue<Integer> minHeap = new PriorityQueue<>();           // min first
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder()); // max first
PriorityQueue<int[]> pq = new PriorityQueue<>((a,b) -> a[0]-b[0]); // custom comparator

// Operations: offer O(logn), poll O(logn), peek O(1)
```

## 🔑 Patterns
| Pattern | Approach |
|---------|----------|
| **Top-K** | Min heap of size K |
| **Kth largest** | Min heap size K → peek |
| **Kth smallest** | Max heap size K → peek |
| **Merge K sorted** | Min heap of K heads |
| **Running median** | Max heap (left) + Min heap (right) |
| **Closest K** | Max heap with distance |

---
