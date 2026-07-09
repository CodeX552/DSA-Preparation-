# 🌳 Tree — Practice Problems

## 🟢 Easy
| # | Problem | Pattern | Hint |
|---|---------|---------|------|
| 1 | [Maximum Depth](https://leetcode.com/problems/maximum-depth-of-binary-tree/) | Recursion | 1 + max(left, right) |
| 2 | [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/) | Recursion | Swap left & right recursively |
| 3 | [Same Tree](https://leetcode.com/problems/same-tree/) | Recursion | Both null=true, compare val+subtrees |
| 4 | [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/) | Recursion | isMirror(left, right) |
| 5 | [Path Sum](https://leetcode.com/problems/path-sum/) | DFS | Subtract val, check at leaf |
| 6 | [Subtree of Another](https://leetcode.com/problems/subtree-of-another-tree/) | Recursion | isIdentical check at each node |

## 🟡 Medium
| # | Problem | Pattern | Hint |
|---|---------|---------|------|
| 7 | [Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/) | BFS | Queue, process level by level |
| 8 | [Validate BST](https://leetcode.com/problems/validate-binary-search-tree/) | DFS | min-max range pass karo |
| 9 | [Kth Smallest in BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/) | Inorder | Inorder = sorted, count to K |
| 10 | [LCA of Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/) | DFS | Both sides mein dhundho |
| 11 | [Construct from Pre+In](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/) | Divide | Pre[0]=root, split inorder |
| 12 | [Diameter](https://leetcode.com/problems/diameter-of-binary-tree/) | DFS | left+right at each node |
| 13 | [Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/) | BFS | Last element of each level |
| 14 | [Flatten to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/) | DFS | Morris-like approach |
| 15 | [Binary Tree Zigzag](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/) | BFS | Alternate direction per level |

## 🔴 Hard
| # | Problem | Pattern | Hint |
|---|---------|---------|------|
| 16 | [Max Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/) | DFS | Global max, return single path |
| 17 | [Serialize/Deserialize](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/) | BFS/DFS | Preorder + null markers |

## ✅ Tracker
- [ ] Maximum Depth
- [ ] Level Order Traversal
- [ ] Validate BST
- [ ] LCA
- [ ] Diameter
- [ ] Construct from Pre+In

> **Revise:** [QUICK-REF.md](QUICK-REF.md) 📝
