# 🔗 Linked List — Complete Learning Guide

## 📖 Table of Contents
1. [Node & Linked List Basics](#1-node--linked-list-basics)
2. [Basic Operations](#2-basic-operations)
3. [Reverse Linked List](#3-reverse-linked-list)
4. [Fast-Slow Pointer (Floyd's)](#4-fast-slow-pointer-floyds)
5. [Merge Operations](#5-merge-operations)
6. [Solved Problems](#6-solved-problems)

---

## 1. Node & Linked List Basics

### Node Kya Hai?
Linked List ka har element ek **Node** hai. Node mein 2 cheezein hain — **data** (value) aur **next** (agla node ka reference).

```java
// Node class — Linked List ka building block
class ListNode {
    int val;           // data store hota hai
    ListNode next;     // next node ka pointer/reference
    
    ListNode(int val) {
        this.val = val;
        this.next = null; // initially kisi ko point nahi karta
    }
}

// Linked List banana
// 1 → 2 → 3 → null
ListNode head = new ListNode(1);     // pehla node (head)
head.next = new ListNode(2);         // doosra node
head.next.next = new ListNode(3);    // teesra node

// Traverse karna (print all elements)
ListNode current = head;            // start from head
while (current != null) {           // jab tak null nahi aa jata
    System.out.print(current.val + " → ");
    current = current.next;          // agla node pe jao
}
System.out.println("null");
// Output: 1 → 2 → 3 → null
```

### Array vs Linked List
| Feature | Array | Linked List |
|---------|-------|-------------|
| Access | O(1) index se | O(n) traverse karna padta |
| Insert (beginning) | O(n) shift karna padta | O(1) sirf pointer change |
| Insert (end) | O(1) amortized | O(n) traverse + O(1) insert |
| Delete | O(n) shift karna padta | O(1) agar node mila |
| Memory | Contiguous | Non-contiguous |
| Size | Fixed | Dynamic |

---

## 2. Basic Operations

```java
// ✅ Insert at beginning — O(1)
public static ListNode insertAtHead(ListNode head, int val) {
    ListNode newNode = new ListNode(val); // naya node banao
    newNode.next = head;                  // naya node head ko point kare
    return newNode;                       // naya node ab head hai
}

// ✅ Insert at end — O(n)
public static ListNode insertAtTail(ListNode head, int val) {
    ListNode newNode = new ListNode(val);
    if (head == null) return newNode;     // list empty hai toh newNode hi head
    
    ListNode current = head;
    while (current.next != null) {        // last node tak jao
        current = current.next;
    }
    current.next = newNode;              // last node ke next mein newNode daal do
    return head;
}

// ✅ Delete node with value — O(n)
public static ListNode deleteNode(ListNode head, int val) {
    if (head == null) return null;
    if (head.val == val) return head.next; // head hi delete karna hai
    
    ListNode current = head;
    while (current.next != null) {
        if (current.next.val == val) {    // agla node delete karna hai
            current.next = current.next.next; // skip karo us node ko
            return head;
        }
        current = current.next;
    }
    return head;
}

// ✅ Length of Linked List — O(n)
public static int length(ListNode head) {
    int count = 0;
    ListNode current = head;
    while (current != null) {
        count++;
        current = current.next;
    }
    return count;
}
```

---

## 3. Reverse Linked List

### Iterative Approach (MUST KNOW!)
```java
// ✅ Problem: Linked List ko reverse karo
// Approach: 3 pointers — prev, current, next
// Time: O(n), Space: O(1)

public static ListNode reverseList(ListNode head) {
    ListNode prev = null;            // previous node (initially null)
    ListNode current = head;         // current node (start from head)
    
    while (current != null) {
        ListNode nextNode = current.next; // next node save karo (warna kho jayega)
        current.next = prev;              // current ka pointer ulta karo ← 
        prev = current;                   // prev ko aage badhao
        current = nextNode;               // current ko aage badhao
    }
    
    return prev;                     // prev ab naya head hai
}

// Dry Run: 1 → 2 → 3 → null
// Step 1: prev=null, curr=1 → next=2, 1→null, prev=1, curr=2
// Step 2: prev=1, curr=2 → next=3, 2→1, prev=2, curr=3
// Step 3: prev=2, curr=3 → next=null, 3→2, prev=3, curr=null
// STOP! Result: 3 → 2 → 1 → null, return prev=3 ✅
```

### Recursive Approach
```java
// ✅ Recursive reverse
// Time: O(n), Space: O(n) — recursion stack

public static ListNode reverseListRecursive(ListNode head) {
    // Base case: empty list ya single node
    if (head == null || head.next == null) {
        return head;
    }
    
    // Recursive call: baaki list ko reverse karo
    ListNode newHead = reverseListRecursive(head.next);
    
    // Current node ko end mein lagao
    head.next.next = head;           // next node mera pointer point kare mujhe
    head.next = null;                // mera pointer null kar do (naya tail)
    
    return newHead;                  // naya head return karo
}
```

### Reverse K nodes at a time
```java
// ✅ Problem: K nodes ke groups mein reverse karo
// Time: O(n), Space: O(1)

public static ListNode reverseKGroup(ListNode head, int k) {
    // Pehle check karo K nodes available hain ya nahi
    ListNode check = head;
    for (int i = 0; i < k; i++) {
        if (check == null) return head; // K nodes nahi hain, mat reverse karo
        check = check.next;
    }
    
    // K nodes reverse karo (same as normal reverse, k times)
    ListNode prev = null, curr = head;
    for (int i = 0; i < k; i++) {
        ListNode next = curr.next;
        curr.next = prev;
        prev = curr;
        curr = next;
    }
    
    // head ab last node hai is group ka — isko next group se jodo
    head.next = reverseKGroup(curr, k); // recursive call for remaining
    
    return prev; // prev is new head of this group
}
```

---

## 4. Fast-Slow Pointer (Floyd's)

### Concept
Do pointers rakh lo — **slow** ek step chalega, **fast** do step chalega. Ye technique cycle detection, middle element, aur nth node se end problems mein kaam aati hai.

```java
// ✅ Problem: Middle of Linked List
// Approach: Slow 1 step, Fast 2 step — jab fast end pe, slow middle pe
// Time: O(n), Space: O(1)

public static ListNode findMiddle(ListNode head) {
    ListNode slow = head;            // 1 step chalega
    ListNode fast = head;            // 2 step chalega
    
    while (fast != null && fast.next != null) {
        slow = slow.next;            // ek step
        fast = fast.next.next;       // do step
    }
    
    return slow;                     // slow middle pe hai!
}

// Example: 1→2→3→4→5
// slow: 1→2→3, fast: 1→3→5→null
// slow = 3 (middle) ✅

// Example: 1→2→3→4→5→6 (even length)
// slow: 1→2→3→4, fast: 1→3→5→null
// slow = 4 (second middle) ✅
```

```java
// ✅ Problem: Detect Cycle in Linked List (Floyd's Cycle Detection)
// Approach: Fast-Slow pointer — agar cycle hai toh dono milenge
// Time: O(n), Space: O(1)

public static boolean hasCycle(ListNode head) {
    ListNode slow = head;
    ListNode fast = head;
    
    while (fast != null && fast.next != null) {
        slow = slow.next;            // 1 step
        fast = fast.next.next;       // 2 step
        
        if (slow == fast) {          // dono mil gaye!
            return true;             // cycle hai!
        }
    }
    
    return false;                    // fast null pe pahunch gaya — no cycle
}
```

```java
// ✅ Problem: Find starting node of cycle
// Approach: Pehle detect karo, phir ek pointer head pe rakho, dono 1-1 step
// Time: O(n), Space: O(1)

public static ListNode detectCycleStart(ListNode head) {
    ListNode slow = head, fast = head;
    
    // Step 1: Detect cycle — meeting point dhundho
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow == fast) break;     // cycle detected, meeting point
    }
    
    if (fast == null || fast.next == null) return null; // no cycle
    
    // Step 2: Ek pointer head pe, doosra meeting pe — dono 1-1 step
    slow = head;
    while (slow != fast) {
        slow = slow.next;
        fast = fast.next;            // dono 1-1 step
    }
    
    return slow;                     // cycle ka starting node!
}
```

```java
// ✅ Problem: Remove Nth Node From End of List
// Approach: Fast pointer N steps pehle bhejo, phir dono saath chalao
// Time: O(n), Space: O(1)

public static ListNode removeNthFromEnd(ListNode head, int n) {
    ListNode dummy = new ListNode(0); // dummy node — edge cases handle karta hai
    dummy.next = head;
    ListNode fast = dummy;
    ListNode slow = dummy;
    
    // Fast ko N+1 step aage bhejo
    for (int i = 0; i <= n; i++) {
        fast = fast.next;
    }
    
    // Ab dono saath chalao — jab fast null pe, slow target se pehle hoga
    while (fast != null) {
        slow = slow.next;
        fast = fast.next;
    }
    
    // slow.next = delete karne wala node
    slow.next = slow.next.next;       // skip karo
    
    return dummy.next;                // head return karo (dummy se)
}
```

---

## 5. Merge Operations

```java
// ✅ Problem: Merge Two Sorted Linked Lists
// Approach: Compare heads, chhota wala pehle
// Time: O(n + m), Space: O(1)

public static ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    ListNode dummy = new ListNode(0); // dummy node — result build karo
    ListNode current = dummy;         // current pointer
    
    while (l1 != null && l2 != null) {
        if (l1.val <= l2.val) {
            current.next = l1;        // l1 ka node jodo
            l1 = l1.next;            // l1 aage badhao
        } else {
            current.next = l2;        // l2 ka node jodo
            l2 = l2.next;            // l2 aage badhao
        }
        current = current.next;       // result aage badhao
    }
    
    // Jo list bacha usko jod do
    current.next = (l1 != null) ? l1 : l2;
    
    return dummy.next;                // dummy ke next se result shuru hai
}
```

```java
// ✅ Problem: Check if Linked List is Palindrome
// Approach: Middle dhundho → second half reverse karo → compare karo
// Time: O(n), Space: O(1)

public static boolean isPalindrome(ListNode head) {
    if (head == null || head.next == null) return true;
    
    // Step 1: Middle dhundho
    ListNode slow = head, fast = head;
    while (fast.next != null && fast.next.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    
    // Step 2: Second half reverse karo
    ListNode secondHalf = reverseList(slow.next);
    
    // Step 3: Compare karo
    ListNode firstHalf = head;
    while (secondHalf != null) {
        if (firstHalf.val != secondHalf.val) return false;
        firstHalf = firstHalf.next;
        secondHalf = secondHalf.next;
    }
    
    return true;
}
```

---

## 6. Solved Problems

### Sort Linked List 🟡 Medium
```java
// ✅ Problem: Linked List ko sort karo
// Approach: Merge Sort — middle se divide, sort, merge
// Time: O(n log n), Space: O(log n)

public static ListNode sortList(ListNode head) {
    if (head == null || head.next == null) return head;
    
    // Step 1: Middle dhundho
    ListNode slow = head, fast = head.next;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    
    // Step 2: Do halves mein tod do
    ListNode secondHalf = slow.next;
    slow.next = null;                 // pehli half ka end
    
    // Step 3: Recursively sort karo dono halves
    ListNode left = sortList(head);
    ListNode right = sortList(secondHalf);
    
    // Step 4: Merge sorted halves
    return mergeTwoLists(left, right);
}
```

### Intersection of Two Linked Lists 🟢 Easy
```java
// ✅ Problem: Do linked lists ka intersection point dhundho
// Approach: Dono pointers — jab ek end pe aaye toh doosre ka head pe bhejo
// Time: O(n + m), Space: O(1)

public static ListNode getIntersectionNode(ListNode headA, ListNode headB) {
    ListNode a = headA, b = headB;
    
    // Dono pointers chalao — jab ek khatam ho toh doosre ke head pe bhejo
    // Agar intersection hai toh dono wahan milenge
    while (a != b) {
        a = (a == null) ? headB : a.next;
        b = (b == null) ? headA : b.next;
    }
    
    return a; // intersection node ya null
}
// Trick: Dono same total distance cover karenge (lengthA + lengthB)
```

---

## 🎯 Common Mistakes

1. **Null check bhoolna** — `current.next` access karne se pehle check karo `current != null`
2. **Head update bhoolna** — Jab head delete ho toh naya head return karo
3. **Dummy node na use karna** — Dummy node edge cases handle karta hai
4. **Next pointer lose karna** — Reverse mein `next` save karo pehle
5. **Cycle mein infinite loop** — Fast-Slow technique use karo

---

> **Next:** [PROBLEMS.md](PROBLEMS.md) mein practice karo! 💪
