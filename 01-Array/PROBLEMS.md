# 🔢 Array — Practice Problems

## 📝 Problem List (Difficulty Order)

### 🟢 Easy (Pehle ye karo)

| # | Problem | Platform | Pattern | Hint |
|---|---------|----------|---------|------|
| 1 | [Two Sum](https://leetcode.com/problems/two-sum/) | LeetCode | HashMap | HashMap mein store karo, complement check karo |
| 2 | [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) | LeetCode | Greedy | Minimum price track karo, har din profit calculate karo |
| 3 | [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) | LeetCode | Two Pointer | Slow-fast pointer use karo, unique elements overwrite karo |
| 4 | [Move Zeroes](https://leetcode.com/problems/move-zeroes/) | LeetCode | Two Pointer | Non-zero elements aage le jao, baaki mein 0 bhar do |
| 5 | [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) | LeetCode | HashSet | HashSet mein dalo, agar pehle se hai toh duplicate! |
| 6 | [Single Number](https://leetcode.com/problems/single-number/) | LeetCode | Bit Manipulation | XOR use karo — a^a=0, a^0=a |
| 7 | [Missing Number](https://leetcode.com/problems/missing-number/) | LeetCode | Math | Sum formula: n*(n+1)/2 - actual_sum = missing |
| 8 | [Majority Element](https://leetcode.com/problems/majority-element/) | LeetCode | Boyer-Moore | Voting algorithm — count maintain karo |

---

### 🟡 Medium (Ye important hain)

| # | Problem | Platform | Pattern | Hint |
|---|---------|----------|---------|------|
| 9 | [3Sum](https://leetcode.com/problems/3sum/) | LeetCode | Two Pointer | Sort karo, fix ek element, baaki do ke liye two pointer |
| 10 | [Container With Most Water](https://leetcode.com/problems/container-with-most-water/) | LeetCode | Two Pointer | Left-right se start, chhota pointer move karo |
| 11 | [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) | LeetCode | Prefix/Suffix | Left products × Right products |
| 12 | [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) | LeetCode | Kadane's | extend ya restart — har element pe decide karo |
| 13 | [Merge Intervals](https://leetcode.com/problems/merge-intervals/) | LeetCode | Sorting | Sort by start, overlap check karo |
| 14 | [Sort Colors](https://leetcode.com/problems/sort-colors/) | LeetCode | Dutch Flag | 3 pointers: low, mid, high |
| 15 | [Rotate Array](https://leetcode.com/problems/rotate-array/) | LeetCode | Reverse | Pura reverse, pehle k reverse, baaki reverse |
| 16 | [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) | LeetCode | Prefix Sum | HashMap mein prefix sum store karo |
| 17 | [Next Permutation](https://leetcode.com/problems/next-permutation/) | LeetCode | Pattern | Dip dhundho, swap karo, reverse karo |
| 18 | [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/) | LeetCode | Matrix | 4 boundaries maintain karo, spiral mein ghoom |

---

### 🔴 Hard (Ye crack kar liya toh boss ho)

| # | Problem | Platform | Pattern | Hint |
|---|---------|----------|---------|------|
| 19 | [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/) | LeetCode | Two Pointer | Left max, right max track karo, chhoti side se calculate |
| 20 | [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/) | LeetCode | Binary Search | Chhote array pe binary search karo |
| 21 | [First Missing Positive](https://leetcode.com/problems/first-missing-positive/) | LeetCode | Index Mapping | Array ko hi HashMap ki tarah use karo |

---

## 🎯 Pattern-Wise Grouping

### Two Pointer Problems
- Two Sum (Sorted) → #1
- 3Sum → #9
- Container With Most Water → #10
- Trapping Rain Water → #19
- Remove Duplicates → #3

### Sliding Window Problems
- Maximum Subarray → #12
- Subarray Sum Equals K → #16

### Sorting + Greedy
- Merge Intervals → #13
- Sort Colors → #14
- Next Permutation → #17

### HashMap/HashSet Based
- Two Sum → #1
- Contains Duplicate → #5
- Subarray Sum Equals K → #16

---

## ✅ Completion Tracker

Solve karke tick karo:
- [ ] Two Sum
- [ ] Best Time to Buy and Sell Stock
- [ ] Remove Duplicates
- [ ] Move Zeroes
- [ ] Contains Duplicate
- [ ] Maximum Subarray
- [ ] 3Sum
- [ ] Container With Most Water
- [ ] Product of Array Except Self
- [ ] Sort Colors
- [ ] Trapping Rain Water

---

> **Revise:** [QUICK-REF.md](QUICK-REF.md) — interview se pehle ek baar zaroor padho! 📝
