# 🔗 Linked List — Practice Problems

## 🟢 Easy
| # | Problem | Platform | Pattern | Hint |
|---|---------|----------|---------|------|
| 1 | [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) | LeetCode | Reverse | prev, curr, next — 3 pointers |
| 2 | [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/) | LeetCode | Merge | Dummy node, compare heads |
| 3 | [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) | LeetCode | Fast-Slow | slow 1 step, fast 2 step |
| 4 | [Middle of Linked List](https://leetcode.com/problems/middle-of-the-linked-list/) | LeetCode | Fast-Slow | Fast end pe → slow middle pe |
| 5 | [Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/) | LeetCode | Fast-Slow + Reverse | Middle → reverse second half → compare |
| 6 | [Intersection of Two LL](https://leetcode.com/problems/intersection-of-two-linked-lists/) | LeetCode | Two Pointer | Switch heads, same distance cover |
| 7 | [Remove Duplicates Sorted](https://leetcode.com/problems/remove-duplicates-from-sorted-list/) | LeetCode | Traversal | curr.val == curr.next.val → skip |

## 🟡 Medium
| # | Problem | Platform | Pattern | Hint |
|---|---------|----------|---------|------|
| 8 | [Remove Nth From End](https://leetcode.com/problems/remove-nth-node-from-end-of-list/) | LeetCode | Two Pointer | Fast ko N step pehle bhejo |
| 9 | [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/) | LeetCode | Math + LL | Carry track karo, new list banao |
| 10 | [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/) | LeetCode | Floyd's | Detect → head se restart → meet = start |
| 11 | [Sort List](https://leetcode.com/problems/sort-list/) | LeetCode | Merge Sort | Middle split, sort, merge |
| 12 | [Reorder List](https://leetcode.com/problems/reorder-list/) | LeetCode | Multiple | Middle → reverse 2nd half → merge alternating |
| 13 | [Copy List Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/) | LeetCode | HashMap | HashMap<original, copy> banao |
| 14 | [Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/) | LeetCode | Two Pointer | Odd nodes, even nodes alag karo, jodo |

## 🔴 Hard
| # | Problem | Platform | Pattern | Hint |
|---|---------|----------|---------|------|
| 15 | [Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/) | LeetCode | Reverse | K nodes check, reverse, recursive call |
| 16 | [Merge K Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) | LeetCode | Heap | PriorityQueue mein heads daal do |

## ✅ Completion Tracker
- [ ] Reverse Linked List
- [ ] Merge Two Sorted Lists
- [ ] Linked List Cycle
- [ ] Middle of Linked List
- [ ] Remove Nth From End
- [ ] Add Two Numbers
- [ ] Sort List

> **Revise:** [QUICK-REF.md](QUICK-REF.md) 📝
