# 🔗 Linked List — Quick Reference

## ⚡ Templates

### Reverse (Iterative) — MOST IMPORTANT
```java
ListNode prev = null, curr = head;
while (curr != null) {
    ListNode next = curr.next; // save
    curr.next = prev;          // reverse
    prev = curr;               // advance
    curr = next;               // advance
}
return prev; // new head
```

### Fast-Slow (Middle / Cycle)
```java
ListNode slow = head, fast = head;
while (fast != null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;
}
// slow = middle (cycle detect: if slow==fast → cycle)
```

### Dummy Node Pattern
```java
ListNode dummy = new ListNode(0);
dummy.next = head;
// ... operations ...
return dummy.next; // handles head deletion edge case
```

### Merge Two Sorted
```java
ListNode dummy = new ListNode(0), curr = dummy;
while (l1 != null && l2 != null) {
    if (l1.val <= l2.val) { curr.next = l1; l1 = l1.next; }
    else { curr.next = l2; l2 = l2.next; }
    curr = curr.next;
}
curr.next = (l1 != null) ? l1 : l2;
return dummy.next;
```

## ⚠️ Common Mistakes
1. `NullPointerException` — null check pehle karo
2. Head update bhoolna → dummy node use karo
3. Pointer lose karna → next save karo reverse mein
4. Infinite loop → cycle detection use karo

## ⏱️ Complexities
| Operation | Time |
|-----------|------|
| Access by index | O(n) |
| Insert at head | O(1) |
| Insert at tail | O(n) |
| Delete (known node) | O(1) |
| Search | O(n) |
| Reverse | O(n) |
| Sort (Merge Sort) | O(n log n) |

---
