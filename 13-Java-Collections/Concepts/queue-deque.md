# 📚 Java Collections — Queue & Deque

## 1. Queue (FIFO - First In First Out)
Queues are typically used for BFS (Breadth-First Search) or level-order traversal.

### Key Implementations
- **LinkedList**: Can be used as a standard Queue.
- **PriorityQueue**: A Min-Heap (by default) where the smallest element is at the head. Used for Top-K elements or Dijkstra's algorithm.

### Queue Methods
```java
Queue<Integer> queue = new LinkedList<>();
queue.offer(10); // Enqueue — adds to end
queue.poll();    // Dequeue — removes from front
queue.peek();    // View front element
```

## 2. PriorityQueue (Heap)
By default, it's a Min-Heap.
```java
// Min Heap (Smallest at top)
PriorityQueue<Integer> minHeap = new PriorityQueue<>();

// Max Heap (Largest at top)
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
```

## 3. Deque (Double Ended Queue)
Supports insertion and removal from both ends. Can be used as both Stack (LIFO) and Queue (FIFO).
- **ArrayDeque**: The most efficient Deque implementation in Java (faster than Stack and LinkedList).

### Deque Methods
```java
Deque<Integer> deque = new ArrayDeque<>();
deque.offerFirst(10); // Add to front
deque.offerLast(20);  // Add to end
deque.pollFirst();    // Remove from front
deque.pollLast();     // Remove from end
```
