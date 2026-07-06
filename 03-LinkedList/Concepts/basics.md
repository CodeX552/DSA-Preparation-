# 🔗 Linked List Concepts — Basics

## Node Structure
```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) { this.val = val; this.next = null; }
}

// Doubly Linked List Node
class DLLNode {
    int val;
    DLLNode prev, next;
    DLLNode(int val) { this.val = val; }
}
```

## Singly vs Doubly Linked List
| Feature | Singly | Doubly |
|---------|--------|--------|
| Memory | Less (1 pointer) | More (2 pointers) |
| Traverse | Forward only | Both directions |
| Delete (given node) | O(n) — prev chahiye | O(1) — prev available |
| Use case | Stack, Queue | LRU Cache, Browser history |

## When to Use Linked List vs Array?
- **Linked List**: Frequent insertions/deletions at beginning
- **Array**: Frequent random access by index
- **Linked List**: Size unknown/dynamic
- **Array**: Size known/fixed

---
