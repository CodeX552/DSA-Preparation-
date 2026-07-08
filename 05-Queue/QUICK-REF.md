# 📮 Queue — Quick Reference

## ⚡ Java Queue Usage
```java
Queue<Integer> q = new LinkedList<>(); // ya ArrayDeque
q.offer(val);  // enqueue
q.poll();      // dequeue (null if empty)
q.peek();      // front (null if empty)
q.isEmpty();
q.size();

Deque<Integer> dq = new ArrayDeque<>();
dq.offerFirst(val); dq.offerLast(val);
dq.pollFirst();     dq.pollLast();
dq.peekFirst();     dq.peekLast();
```

## 🔑 Patterns
| Pattern | Use Case |
|---------|----------|
| **BFS** | Level-order, shortest path (unweighted) |
| **Monotonic Deque** | Sliding window min/max |
| **Multi-source BFS** | Rotting oranges, walls & gates |

## ⏱️ Complexities
All operations: O(1)

---
