# 🌳 Tree — Complete Learning Guide

## 📖 Table of Contents
1. [Tree Basics](#1-tree-basics)
2. [Tree Traversals](#2-tree-traversals)
3. [Binary Search Tree (BST)](#3-binary-search-tree-bst)
4. [Important Tree Patterns](#4-important-tree-patterns)
5. [Solved Problems](#5-solved-problems)

---

## 1. Tree Basics

### Node Structure
```java
class TreeNode {
    int val;
    TreeNode left;       // left child
    TreeNode right;      // right child
    
    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

// Tree banana
//       1
//      / \
//     2   3
//    / \
//   4   5

TreeNode root = new TreeNode(1);
root.left = new TreeNode(2);
root.right = new TreeNode(3);
root.left.left = new TreeNode(4);
root.left.right = new TreeNode(5);
```

### Tree Terminology
- **Root**: Sabse upar wala node (parent nahi hai)
- **Leaf**: Jo node ka koi child nahi hai
- **Height**: Root se sabse neeche tak ka distance
- **Depth**: Root se us node tak ka distance
- **Level**: Depth + 1

---

## 2. Tree Traversals

### DFS (Depth First Search) — 3 Types

#### 1. Inorder Traversal
![Inorder Traversal Animation](https://upload.wikimedia.org/wikipedia/commons/4/48/Inorder-traversal.gif)

#### 2. Preorder Traversal
![Preorder Traversal Animation](https://upload.wikimedia.org/wikipedia/commons/a/ac/Preorder-traversal.gif)

#### 3. Postorder Traversal
![Postorder Traversal Animation](https://upload.wikimedia.org/wikipedia/commons/2/28/Postorder-traversal.gif)

```java
// ✅ Inorder: Left → Root → Right (BST mein sorted order milta hai!)
public static void inorder(TreeNode root) {
    if (root == null) return;         // base case
    inorder(root.left);              // pehle left subtree
    System.out.print(root.val + " "); // phir root
    inorder(root.right);             // phir right subtree
}

// ✅ Preorder: Root → Left → Right (copy/serialize tree)
public static void preorder(TreeNode root) {
    if (root == null) return;
    System.out.print(root.val + " "); // pehle root
    preorder(root.left);             // phir left
    preorder(root.right);            // phir right
}

// ✅ Postorder: Left → Right → Root (delete tree)
public static void postorder(TreeNode root) {
    if (root == null) return;
    postorder(root.left);            // pehle left
    postorder(root.right);           // phir right
    System.out.print(root.val + " "); // phir root (last)
}
```

### Iterative Inorder (Stack se)
```java
// ✅ Iterative Inorder — Stack use karo
// Time: O(n), Space: O(h)

public static List<Integer> inorderIterative(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    Deque<TreeNode> stack = new ArrayDeque<>();
    TreeNode curr = root;
    
    while (curr != null || !stack.isEmpty()) {
        // Sabse left tak jao
        while (curr != null) {
            stack.push(curr);
            curr = curr.left;
        }
        
        curr = stack.pop();           // pop karo — ye inorder next hai
        result.add(curr.val);
        curr = curr.right;            // right subtree pe jao
    }
    
    return result;
}
```

### BFS / Level Order Traversal (Queue se)

![Level Order Traversal Animation](https://upload.wikimedia.org/wikipedia/commons/4/46/Animated_BFS.gif)
```java
// ✅ Level Order Traversal — Queue use karo
// Time: O(n), Space: O(n)

public static List<List<Integer>> levelOrder(TreeNode root) {
    List<List<Integer>> result = new ArrayList<>();
    if (root == null) return result;
    
    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);
    
    while (!queue.isEmpty()) {
        int levelSize = queue.size(); // is level mein kitne nodes
        List<Integer> level = new ArrayList<>();
        
        for (int i = 0; i < levelSize; i++) {
            TreeNode node = queue.poll();
            level.add(node.val);
            
            if (node.left != null) queue.offer(node.left);
            if (node.right != null) queue.offer(node.right);
        }
        
        result.add(level);
    }
    
    return result;
}

//       1          Level 0: [1]
//      / \
//     2   3        Level 1: [2, 3]
//    / \   \
//   4   5   6      Level 2: [4, 5, 6]
// Result: [[1], [2,3], [4,5,6]]
```

---

## 3. Binary Search Tree (BST)

### BST Property
- **Left subtree** ke sab elements root se **chhote**
- **Right subtree** ke sab elements root se **bade**
- **Inorder traversal** = **sorted order**!

![BST Insertion Animation](https://upload.wikimedia.org/wikipedia/commons/8/83/Binary-search-tree-insertion-animation.gif)

```java
// ✅ Search in BST — O(log n) average
public static TreeNode searchBST(TreeNode root, int val) {
    if (root == null || root.val == val) return root;
    
    if (val < root.val) {
        return searchBST(root.left, val);  // left mein dhundho
    } else {
        return searchBST(root.right, val); // right mein dhundho
    }
}

// ✅ Insert in BST — O(log n) average
public static TreeNode insertBST(TreeNode root, int val) {
    if (root == null) return new TreeNode(val); // yahan insert karo
    
    if (val < root.val) {
        root.left = insertBST(root.left, val);   // left mein daalo
    } else {
        root.right = insertBST(root.right, val);  // right mein daalo
    }
    
    return root;
}

// ✅ Validate BST — check karo ki valid BST hai
// Trick: min-max range pass karo
public static boolean isValidBST(TreeNode root) {
    return validate(root, Long.MIN_VALUE, Long.MAX_VALUE);
}

private static boolean validate(TreeNode node, long min, long max) {
    if (node == null) return true;
    if (node.val <= min || node.val >= max) return false;
    
    return validate(node.left, min, node.val) &&    // left: max = node.val
           validate(node.right, node.val, max);     // right: min = node.val
}
```

---

## 4. Important Tree Patterns

### Height / Maximum Depth
```java
// ✅ Tree ki height nikalo
// Time: O(n), Space: O(h)

public static int maxDepth(TreeNode root) {
    if (root == null) return 0;
    
    int leftHeight = maxDepth(root.left);   // left subtree ki height
    int rightHeight = maxDepth(root.right); // right subtree ki height
    
    return 1 + Math.max(leftHeight, rightHeight); // 1 (root) + max of both
}
```

### Diameter of Binary Tree
```java
// ✅ Longest path between any two nodes
// Time: O(n), Space: O(h)

int diameter = 0; // global variable

public int diameterOfBinaryTree(TreeNode root) {
    height(root);
    return diameter;
}

private int height(TreeNode node) {
    if (node == null) return 0;
    
    int left = height(node.left);
    int right = height(node.right);
    
    diameter = Math.max(diameter, left + right); // diameter update karo
    
    return 1 + Math.max(left, right);            // height return karo
}
```

### Lowest Common Ancestor (LCA)
```java
// ✅ Do nodes ka LCA (sabse neeche common parent) dhundho
// Time: O(n), Space: O(h)

public static TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (root == null || root == p || root == q) {
        return root;                  // base case: null ya target mila
    }
    
    TreeNode left = lowestCommonAncestor(root.left, p, q);   // left mein dhundho
    TreeNode right = lowestCommonAncestor(root.right, p, q); // right mein dhundho
    
    if (left != null && right != null) {
        return root;                  // dono sides mein mila → root hi LCA hai
    }
    
    return left != null ? left : right; // jis side mila woh return karo
}
```

### Check if Tree is Balanced
```java
// ✅ Balanced = har node pe left-right height difference <= 1
// Time: O(n), Space: O(h)

public static boolean isBalanced(TreeNode root) {
    return checkHeight(root) != -1;
}

private static int checkHeight(TreeNode node) {
    if (node == null) return 0;
    
    int left = checkHeight(node.left);
    if (left == -1) return -1;        // left unbalanced
    
    int right = checkHeight(node.right);
    if (right == -1) return -1;       // right unbalanced
    
    if (Math.abs(left - right) > 1) return -1; // current node unbalanced
    
    return 1 + Math.max(left, right);
}
```

### Path Sum
```java
// ✅ Root se leaf tak koi path hai jiska sum = target?
public static boolean hasPathSum(TreeNode root, int targetSum) {
    if (root == null) return false;
    
    // Leaf node pe pehunche aur remaining sum = current value
    if (root.left == null && root.right == null) {
        return root.val == targetSum;
    }
    
    int remaining = targetSum - root.val;
    return hasPathSum(root.left, remaining) || hasPathSum(root.right, remaining);
}
```

### Symmetric Tree
```java
// ✅ Tree mirror image hai ya nahi?
public static boolean isSymmetric(TreeNode root) {
    if (root == null) return true;
    return isMirror(root.left, root.right);
}

private static boolean isMirror(TreeNode t1, TreeNode t2) {
    if (t1 == null && t2 == null) return true;
    if (t1 == null || t2 == null) return false;
    
    return (t1.val == t2.val) &&
           isMirror(t1.left, t2.right) &&    // left ka left = right ka right
           isMirror(t1.right, t2.left);       // left ka right = right ka left
}
```

---

## 5. Solved Problems

### Construct Binary Tree from Preorder and Inorder
```java
// ✅ Preorder + Inorder se tree banao
// Time: O(n), Space: O(n)

int preIndex = 0;
Map<Integer, Integer> inorderMap = new HashMap<>();

public TreeNode buildTree(int[] preorder, int[] inorder) {
    for (int i = 0; i < inorder.length; i++) {
        inorderMap.put(inorder[i], i); // value → index map
    }
    return build(preorder, 0, inorder.length - 1);
}

private TreeNode build(int[] preorder, int inStart, int inEnd) {
    if (inStart > inEnd) return null;
    
    int rootVal = preorder[preIndex++]; // preorder ka next = root
    TreeNode root = new TreeNode(rootVal);
    
    int inIndex = inorderMap.get(rootVal); // root ki position inorder mein
    
    root.left = build(preorder, inStart, inIndex - 1);  // left subtree
    root.right = build(preorder, inIndex + 1, inEnd);   // right subtree
    
    return root;
}
```

### Flatten Binary Tree to Linked List
```java
// ✅ Tree ko right-skewed linked list mein convert karo (preorder)
// Time: O(n), Space: O(1)

public static void flatten(TreeNode root) {
    TreeNode curr = root;
    
    while (curr != null) {
        if (curr.left != null) {
            // Left subtree ka rightmost node dhundho
            TreeNode rightmost = curr.left;
            while (rightmost.right != null) {
                rightmost = rightmost.right;
            }
            
            // Right subtree ko rightmost ke right mein attach karo
            rightmost.right = curr.right;
            
            // Left ko right mein move karo
            curr.right = curr.left;
            curr.left = null;
        }
        curr = curr.right;
    }
}
```

---

## 🎯 Tree Problem Solving Tips

1. **Recursion socho pehle** — Tree = recursive structure
2. **Base case**: `if (root == null)` — hamesha handle karo
3. **Return type decide karo** — height return, boolean return, node return
4. **Global variable** — Diameter, max sum type problems mein useful
5. **Level order = BFS = Queue** — Level wise process karna ho toh Queue

---

> **Next:** [PROBLEMS.md](PROBLEMS.md) 💪
