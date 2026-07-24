# 🧩 DP — Quick Reference

## ⚡ DP Steps
1. **State define karo**: dp[i] kya represent karta hai?
2. **Recurrence likho**: dp[i] = f(dp[i-1], dp[i-2], ...)
3. **Base case**: dp[0] = ?, dp[1] = ?
4. **Order**: Bottom-up fill karo
5. **Answer**: dp[n] ya dp[m][n]

## 🔑 Common Patterns
| Pattern | Example | Recurrence |
|---------|---------|------------|
| **Fibonacci** | Climbing Stairs | dp[i] = dp[i-1] + dp[i-2] |
| **Knapsack 0/1** | Partition Subset | dp[i][w] = max(skip, take) |
| **Unbounded KS** | Coin Change | dp[i] = min(dp[i-coin] + 1) |
| **LCS** | Common Subseq | match: d+1, else max(up,left) |
| **LIS** | Increasing Subseq | dp[i] = max(dp[j]+1) for j<i |
| **Grid** | Unique Paths | dp[i][j] = up + left |

## 📝 Memoization Template
```java
int[] memo = new int[n + 1];
Arrays.fill(memo, -1);
int solve(int i) {
    if (base) return value;
    if (memo[i] != -1) return memo[i];
    memo[i] = /* recurrence */;
    return memo[i];
}
```

---
