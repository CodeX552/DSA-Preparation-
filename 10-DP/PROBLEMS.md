# 🧩 DP — Practice Problems

## 🟢 Easy
| # | Problem | Pattern | Hint |
|---|---------|---------|------|
| 1 | [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) | Fibonacci | dp[i] = dp[i-1] + dp[i-2] |
| 2 | [Min Cost Climbing](https://leetcode.com/problems/min-cost-climbing-stairs/) | 1D DP | min(dp[i-1], dp[i-2]) + cost |

## 🟡 Medium
| # | Problem | Pattern | Hint |
|---|---------|---------|------|
| 3 | [House Robber](https://leetcode.com/problems/house-robber/) | 1D DP | max(skip, rob+dp[i-2]) |
| 4 | [Coin Change](https://leetcode.com/problems/coin-change/) | Unbounded Knapsack | min coins for amount |
| 5 | [Longest Common Subseq](https://leetcode.com/problems/longest-common-subsequence/) | 2D DP | Match: diagonal+1, else max |
| 6 | [Longest Increasing Subseq](https://leetcode.com/problems/longest-increasing-subsequence/) | LIS | dp[i] = max(dp[j]+1) for j<i |
| 7 | [Word Break](https://leetcode.com/problems/word-break/) | 1D DP | dp[i] = any word ends at i? |
| 8 | [Unique Paths](https://leetcode.com/problems/unique-paths/) | Grid DP | dp[i][j] = dp[i-1][j] + dp[i][j-1] |
| 9 | [Partition Equal Subset](https://leetcode.com/problems/partition-equal-subset-sum/) | 0/1 Knapsack | Target = totalSum/2 |
| 10 | [Target Sum](https://leetcode.com/problems/target-sum/) | 0/1 Knapsack | Count subsets with sum |
| 11 | [Decode Ways](https://leetcode.com/problems/decode-ways/) | 1D DP | 1 digit + 2 digit decode |

## 🔴 Hard
| # | Problem | Pattern | Hint |
|---|---------|---------|------|
| 12 | [Edit Distance](https://leetcode.com/problems/edit-distance/) | 2D DP | Insert/Delete/Replace |
| 13 | [Regular Expression](https://leetcode.com/problems/regular-expression-matching/) | 2D DP | Match *, . patterns |
| 14 | [Burst Balloons](https://leetcode.com/problems/burst-balloons/) | Interval DP | Last burst = max coins |

## ✅ Tracker
- [ ] Climbing Stairs
- [ ] House Robber
- [ ] Coin Change
- [ ] LCS
- [ ] LIS
- [ ] Edit Distance

> **Revise:** [QUICK-REF.md](QUICK-REF.md) 📝
