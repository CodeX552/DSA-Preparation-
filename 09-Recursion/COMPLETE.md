# 🔄 Recursion & Backtracking — Complete Learning Guide

## 1. Recursion Basics

### Recursion Kya Hai?
Function jo **khud ko call** kare chhote version ke liye. Har recursion mein do cheezein hain:
- **Base Case**: Ruk jao (nahi toh infinite loop)
- **Recursive Case**: Chhota problem bana ke call karo

```java
// ✅ Factorial — n! = n * (n-1)!
public static int factorial(int n) {
    if (n <= 1) return 1;            // base case
    return n * factorial(n - 1);     // recursive case
}
// factorial(4) → 4 * factorial(3) → 4 * 3 * factorial(2) → 4*3*2*1 = 24

// ✅ Fibonacci — fib(n) = fib(n-1) + fib(n-2)
public static int fibonacci(int n) {
    if (n <= 1) return n;            // base case: fib(0)=0, fib(1)=1
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// ✅ Power — x^n
public static double power(double x, int n) {
    if (n == 0) return 1;
    double half = power(x, n / 2);
    if (n % 2 == 0) return half * half;
    else return x * half * half;     // odd power
}
```

## 2. Subsets (Power Set)

```java
// ✅ Problem: Sabhi subsets generate karo
// Time: O(2^n), Space: O(n)

public static List<List<Integer>> subsets(int[] nums) {
    List<List<Integer>> result = new ArrayList<>();
    generateSubsets(nums, 0, new ArrayList<>(), result);
    return result;
}

private static void generateSubsets(int[] nums, int index, List<Integer> current, List<List<Integer>> result) {
    result.add(new ArrayList<>(current)); // current subset add karo
    
    for (int i = index; i < nums.length; i++) {
        current.add(nums[i]);             // include karo
        generateSubsets(nums, i + 1, current, result); // aage badho
        current.remove(current.size() - 1); // backtrack — hatao
    }
}
// nums = [1,2,3] → [[], [1], [1,2], [1,2,3], [1,3], [2], [2,3], [3]]
```

## 3. Permutations

```java
// ✅ Problem: Sabhi permutations generate karo
// Time: O(n! * n)

public static List<List<Integer>> permute(int[] nums) {
    List<List<Integer>> result = new ArrayList<>();
    boolean[] used = new boolean[nums.length];
    generatePerms(nums, used, new ArrayList<>(), result);
    return result;
}

private static void generatePerms(int[] nums, boolean[] used, List<Integer> current, List<List<Integer>> result) {
    if (current.size() == nums.length) {
        result.add(new ArrayList<>(current)); // complete permutation mili!
        return;
    }
    
    for (int i = 0; i < nums.length; i++) {
        if (used[i]) continue;                // already use ho raha hai
        
        used[i] = true;
        current.add(nums[i]);
        generatePerms(nums, used, current, result);
        current.remove(current.size() - 1);   // backtrack
        used[i] = false;                       // backtrack
    }
}
```

## 4. N-Queens

```java
// ✅ Problem: N×N board pe N queens place karo, koi attack na kare
// Time: O(N!)

public static List<List<String>> solveNQueens(int n) {
    List<List<String>> result = new ArrayList<>();
    char[][] board = new char[n][n];
    for (char[] row : board) Arrays.fill(row, '.'); // empty board
    
    placeQueens(board, 0, n, result);
    return result;
}

private static void placeQueens(char[][] board, int row, int n, List<List<String>> result) {
    if (row == n) {
        // Sab queens place ho gayi!
        List<String> solution = new ArrayList<>();
        for (char[] r : board) solution.add(new String(r));
        result.add(solution);
        return;
    }
    
    for (int col = 0; col < n; col++) {
        if (isSafe(board, row, col, n)) {
            board[row][col] = 'Q';             // queen place karo
            placeQueens(board, row + 1, n, result); // next row
            board[row][col] = '.';             // backtrack — hatao
        }
    }
}

private static boolean isSafe(char[][] board, int row, int col, int n) {
    // Upar column check
    for (int i = 0; i < row; i++)
        if (board[i][col] == 'Q') return false;
    // Upper-left diagonal
    for (int i = row-1, j = col-1; i >= 0 && j >= 0; i--, j--)
        if (board[i][j] == 'Q') return false;
    // Upper-right diagonal
    for (int i = row-1, j = col+1; i >= 0 && j < n; i--, j++)
        if (board[i][j] == 'Q') return false;
    return true;
}
```

## 5. Generate Parentheses

```java
// ✅ N pairs of valid parentheses generate karo
public static List<String> generateParenthesis(int n) {
    List<String> result = new ArrayList<>();
    generate(n, 0, 0, new StringBuilder(), result);
    return result;
}

private static void generate(int n, int open, int close, StringBuilder sb, List<String> result) {
    if (sb.length() == 2 * n) {
        result.add(sb.toString());
        return;
    }
    
    if (open < n) {                           // open bracket add kar sakte hain
        sb.append('(');
        generate(n, open + 1, close, sb, result);
        sb.deleteCharAt(sb.length() - 1);     // backtrack
    }
    
    if (close < open) {                       // close bracket add kar sakte hain
        sb.append(')');
        generate(n, open, close + 1, sb, result);
        sb.deleteCharAt(sb.length() - 1);     // backtrack
    }
}
```

## 🎯 Backtracking Template
```java
void backtrack(state, choices) {
    if (base_case) { add to result; return; }
    
    for (choice in choices) {
        if (isValid(choice)) {
            make(choice);             // choose
            backtrack(next_state);    // explore
            undo(choice);             // un-choose (BACKTRACK!)
        }
    }
}
```

---

> **Next:** [PROBLEMS.md](PROBLEMS.md) 💪
