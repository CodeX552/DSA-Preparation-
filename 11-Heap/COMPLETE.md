# ⛰️ Heap — Complete Learning Guide

## 1. Heap Basics

```java
import java.util.PriorityQueue;

// ✅ Min Heap (default in Java) — chhota element pehle
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
minHeap.offer(30);
minHeap.offer(10);
minHeap.offer(20);
minHeap.peek();     // 10 — sabse chhota
minHeap.poll();     // 10 — sabse chhota nikalo

// ✅ Max Heap — bada element pehle
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
// ya: new PriorityQueue<>((a, b) -> b - a);
maxHeap.offer(30);
maxHeap.offer(10);
maxHeap.offer(20);
maxHeap.peek();     // 30 — sabse bada

// Complexity:
// offer/add: O(log n)
// poll/remove: O(log n)
// peek: O(1)
```

## 2. Top-K Pattern

```java
// ✅ Problem: Kth Largest Element
// Approach: Min Heap of size K — top = Kth largest
// Time: O(n log k)

public static int findKthLargest(int[] nums, int k) {
    PriorityQueue<Integer> minHeap = new PriorityQueue<>();
    
    for (int num : nums) {
        minHeap.offer(num);
        if (minHeap.size() > k) {
            minHeap.poll();              // chhota element hatao
        }
    }
    
    return minHeap.peek();              // top = Kth largest!
}

// ✅ Problem: Top K Frequent Elements
// Time: O(n log k)

public static int[] topKFrequent(int[] nums, int k) {
    Map<Integer, Integer> freq = new HashMap<>();
    for (int num : nums) freq.merge(num, 1, Integer::sum);
    
    PriorityQueue<Map.Entry<Integer, Integer>> minHeap =
        new PriorityQueue<>((a, b) -> a.getValue() - b.getValue());
    
    for (Map.Entry<Integer, Integer> entry : freq.entrySet()) {
        minHeap.offer(entry);
        if (minHeap.size() > k) minHeap.poll();
    }
    
    int[] result = new int[k];
    for (int i = 0; i < k; i++) result[i] = minHeap.poll().getKey();
    return result;
}
```

## 3. Merge K Sorted Lists

```java
// ✅ K sorted linked lists ko merge karo
// Time: O(N log K) — N = total nodes

public static ListNode mergeKLists(ListNode[] lists) {
    PriorityQueue<ListNode> pq = new PriorityQueue<>((a, b) -> a.val - b.val);
    
    for (ListNode head : lists) {
        if (head != null) pq.offer(head); // sab heads daal do
    }
    
    ListNode dummy = new ListNode(0);
    ListNode curr = dummy;
    
    while (!pq.isEmpty()) {
        ListNode smallest = pq.poll();     // sabse chhota nikalo
        curr.next = smallest;
        curr = curr.next;
        
        if (smallest.next != null) {
            pq.offer(smallest.next);       // next node daal do
        }
    }
    
    return dummy.next;
}
```

## 4. Find Median from Data Stream

```java
// ✅ Two heaps se running median nikalo
// maxHeap: left half (bade elements), minHeap: right half (chhote elements)

class MedianFinder {
    PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder()); // left half
    PriorityQueue<Integer> minHeap = new PriorityQueue<>(); // right half
    
    public void addNum(int num) {
        maxHeap.offer(num);                // pehle left mein daalo
        minHeap.offer(maxHeap.poll());     // balance karo — left ka max right mein
        
        if (minHeap.size() > maxHeap.size()) {
            maxHeap.offer(minHeap.poll()); // sizes balance karo
        }
    }
    
    public double findMedian() {
        if (maxHeap.size() > minHeap.size()) {
            return maxHeap.peek();         // odd elements — middle
        }
        return (maxHeap.peek() + minHeap.peek()) / 2.0; // even — average
    }
}
```

---

> **Next:** [PROBLEMS.md](PROBLEMS.md) 💪
