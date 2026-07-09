# 🌳 Tree — Quick Reference

## ⚡ Traversal Summary
```
Inorder:   Left → Root → Right  (BST → sorted)
Preorder:  Root → Left → Right  (copy tree)
Postorder: Left → Right → Root  (delete tree)
Level:     Level by level (BFS + Queue)
```

## 📝 Key Templates

### DFS Recursive
```java
void dfs(TreeNode root) {
    if (root == null) return;
    // preorder: process here
    dfs(root.left);
    // inorder: process here
    dfs(root.right);
    // postorder: process here
}
```

### BFS Level Order
```java
Queue<TreeNode> q = new LinkedList<>();
q.offer(root);
while (!q.isEmpty()) {
    int size = q.size();
    for (int i = 0; i < size; i++) {
        TreeNode node = q.poll();
        if (node.left != null) q.offer(node.left);
        if (node.right != null) q.offer(node.right);
    }
}
```

### Height
```java
int height(TreeNode root) {
    if (root == null) return 0;
    return 1 + Math.max(height(root.left), height(root.right));
}
```

### LCA
```java
TreeNode lca(TreeNode root, TreeNode p, TreeNode q) {
    if (root == null || root == p || root == q) return root;
    TreeNode left = lca(root.left, p, q);
    TreeNode right = lca(root.right, p, q);
    if (left != null && right != null) return root;
    return left != null ? left : right;
}
```

## ⏱️ BST Complexities
| Op | Average | Worst (skewed) |
|----|---------|----------------|
| Search | O(log n) | O(n) |
| Insert | O(log n) | O(n) |
| Delete | O(log n) | O(n) |

## 🧠 Tips
- Tree = Recursion (90% problems)
- BST Inorder = Sorted array
- Level order = BFS + Queue
- Height problems = return int
- Path problems = pass sum down

---
