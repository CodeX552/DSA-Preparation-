# Top Tree Patterns
## 1. Height/Depth → return 1 + max(left, right)
## 2. Diameter → left + right at each node, track global max
## 3. LCA → search both sides, if both found = current node
## 4. Path Sum → subtract val, check at leaf
## 5. Symmetric → isMirror(left.left, right.right)
## 6. Views (left/right/top/bottom) → BFS with column/level tracking
## 7. Serialize/Deserialize → preorder + null markers
## 8. Construct → preorder[0] = root, split inorder
