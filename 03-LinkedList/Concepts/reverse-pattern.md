# 🔗 Reverse Pattern on Linked List

## 3 Types of Reverse

### 1. Full Reverse
```java
ListNode prev = null, curr = head;
while (curr != null) {
    ListNode next = curr.next;
    curr.next = prev;
    prev = curr; curr = next;
}
return prev;
```

### 2. Reverse between positions m and n
- m se pehle tak normally traverse karo
- m se n tak reverse karo
- Connections fix karo

### 3. Reverse in K-groups
- K nodes available check karo
- K nodes reverse karo
- Recursive call baaki ke liye
- Connect groups

## Pro Tip
Reverse problems mein hamesha **dry run karo** pen paper pe. Pointers ka diagram banao — bahut clarity milegi!

---
