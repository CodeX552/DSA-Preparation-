# 📮 Queue — Complete Learning Guide

## 1. Queue Basics

### FIFO — First In First Out
```java
import java.util.*;

// Queue interface — LinkedList ya ArrayDeque se implement
Queue<Integer> queue = new LinkedList<>();
// ya
Queue<Integer> queue2 = new ArrayDeque<>(); // faster

queue.offer(10);          // enqueue — end mein daalo (add bhi chal)
queue.offer(20);
queue.offer(30);          // queue: [10, 20, 30] → front=10

queue.peek();             // 10 — front element dekho
queue.poll();             // 10 — front element nikalo
queue.isEmpty();          // false
queue.size();             // 2
```

### Deque (Double-ended Queue)
```java
Deque<Integer> deque = new ArrayDeque<>();

// Dono ends se add/remove kar sakte ho
deque.offerFirst(10);     // front mein daalo
deque.offerLast(20);      // end mein daalo
deque.pollFirst();        // front se nikalo
deque.pollLast();         // end se nikalo
deque.peekFirst();        // front dekho
deque.peekLast();         // end dekho
```

---

## 2. BFS using Queue

```java
// ✅ BFS Template (Graph/Tree level-order traversal)
// Time: O(V + E), Space: O(V)

public static void bfs(int start, List<List<Integer>> graph, int n) {
    boolean[] visited = new boolean[n];
    Queue<Integer> queue = new LinkedList<>();
    
    queue.offer(start);               // starting node daal do
    visited[start] = true;
    
    while (!queue.isEmpty()) {
        int node = queue.poll();      // front se nikalo
        System.out.print(node + " ");
        
        for (int neighbor : graph.get(node)) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                queue.offer(neighbor); // unvisited neighbors add karo
            }
        }
    }
}
```

---

## 3. Sliding Window Maximum

```java
// ✅ Problem: Window of size K mein maximum element har position pe
// Approach: Monotonic Deque — decreasing order maintain karo
// Time: O(n), Space: O(k)

public static int[] maxSlidingWindow(int[] nums, int k) {
    int n = nums.length;
    int[] result = new int[n - k + 1];
    Deque<Integer> deque = new ArrayDeque<>(); // indices store karo
    
    for (int i = 0; i < n; i++) {
        // Window se bahar chale gaye elements hatao (front se)
        while (!deque.isEmpty() && deque.peekFirst() < i - k + 1) {
            deque.pollFirst();
        }
        
        // Current se chhote elements hatao (back se) — kaam ke nahi
        while (!deque.isEmpty() && nums[deque.peekLast()] < nums[i]) {
            deque.pollLast();
        }
        
        deque.offerLast(i);           // current index add karo
        
        // Window complete hai toh result mein daal do
        if (i >= k - 1) {
            result[i - k + 1] = nums[deque.peekFirst()]; // front = max
        }
    }
    
    return result;
}

// Example: nums=[1,3,-1,-3,5,3,6,7], k=3
// Windows: [1,3,-1]=3, [3,-1,-3]=3, [-1,-3,5]=5, [-3,5,3]=5, [5,3,6]=6, [3,6,7]=7
// Result: [3, 3, 5, 5, 6, 7]
```

---

## 4. Implement Stack using Queues

```java
// ✅ One queue approach
class MyStack {
    Queue<Integer> queue = new LinkedList<>();
    
    public void push(int x) {
        queue.offer(x);
        // Naye element ko front pe lao — baaki sab re-enqueue karo
        for (int i = 0; i < queue.size() - 1; i++) {
            queue.offer(queue.poll()); // front se nikalo, back mein daalo
        }
    }
    
    public int pop() { return queue.poll(); }
    public int top() { return queue.peek(); }
    public boolean empty() { return queue.isEmpty(); }
}
```

---

## 5. First Non-Repeating Character in Stream

```java
// ✅ Problem: Stream mein har point pe first non-repeating character
// Approach: Queue + frequency count
// Time: O(n), Space: O(26)

public static String firstNonRepeating(String stream) {
    Queue<Character> queue = new LinkedList<>();
    int[] count = new int[26];
    StringBuilder result = new StringBuilder();
    
    for (char c : stream.toCharArray()) {
        count[c - 'a']++;
        queue.offer(c);
        
        // Front se repeating characters hatao
        while (!queue.isEmpty() && count[queue.peek() - 'a'] > 1) {
            queue.poll();
        }
        
        result.append(queue.isEmpty() ? '#' : queue.peek());
    }
    
    return result.toString();
}
```

---

## 🎯 Common Mistakes
1. **Queue vs Stack** — Queue=FIFO, Stack=LIFO
2. **offer vs add** — `offer` returns false if full, `add` throws exception
3. **poll vs remove** — `poll` returns null if empty, `remove` throws exception
4. **Deque direction** — First=front, Last=back

---

> **Next:** [PROBLEMS.md](PROBLEMS.md) 💪
