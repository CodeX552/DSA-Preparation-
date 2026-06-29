# 🔢 Array — Quick Reference (Cheat Sheet)

## ⚡ Interview Se 10 Min Pehle Ye Padho!

---

## 🔑 Key Patterns at a Glance

| Pattern | Kab Use Karo | Time | Template |
|---------|-------------|------|----------|
| **Two Pointer** | Sorted array, pair finding | O(n) | `left=0, right=n-1, move based on condition` |
| **Sliding Window** | Subarray of fixed/variable size | O(n) | `expand right, shrink left` |
| **Kadane's** | Max subarray sum | O(n) | `max(arr[i], currentSum + arr[i])` |
| **Prefix Sum** | Range sum queries | O(n) build, O(1) query | `prefix[i] = prefix[i-1] + arr[i]` |
| **Dutch Flag** | 3-way partition (0,1,2) | O(n) | `low, mid, high pointers` |
| **HashMap** | Count, frequency, pairs | O(n) | `map.getOrDefault(key, 0) + 1` |

---

## 📝 Templates

### Two Pointer (Sorted Array)
```java
int left = 0, right = arr.length - 1;
while (left < right) {
    int sum = arr[left] + arr[right];
    if (sum == target) return result;
    else if (sum < target) left++;
    else right--;
}
```

### Sliding Window (Fixed Size K)
```java
int windowSum = 0;
for (int i = 0; i < k; i++) windowSum += arr[i]; // pehli window
int maxSum = windowSum;
for (int i = k; i < n; i++) {
    windowSum += arr[i] - arr[i - k]; // slide karo
    maxSum = Math.max(maxSum, windowSum);
}
```

### Kadane's Algorithm
```java
int curr = arr[0], max = arr[0];
for (int i = 1; i < n; i++) {
    curr = Math.max(arr[i], curr + arr[i]);
    max = Math.max(max, curr);
}
```

### Prefix Sum
```java
int[] prefix = new int[n];
prefix[0] = arr[0];
for (int i = 1; i < n; i++) prefix[i] = prefix[i-1] + arr[i];
// Range sum [l, r] = prefix[r] - (l > 0 ? prefix[l-1] : 0);
```

---

## ⏱️ Time Complexity Quick Guide

| Operation | Array | ArrayList |
|-----------|-------|-----------|
| Access by index | O(1) | O(1) |
| Search (unsorted) | O(n) | O(n) |
| Search (sorted) | O(log n) | O(log n) |
| Insert at end | N/A | O(1)* |
| Insert at beginning | O(n) | O(n) |
| Delete | O(n) | O(n) |
| Sort | O(n log n) | O(n log n) |

*Amortized

---

## ⚠️ Common Mistakes

1. **Off-by-one**: `i < arr.length` ✅ vs `i <= arr.length` ❌
2. **Null check**: `if (arr == null || arr.length == 0)` — always karo
3. **Integer overflow**: `(left + right) / 2` → `left + (right - left) / 2`
4. **Modifying while iterating**: Iterator use karo ya reverse iterate karo
5. **Edge cases**: Empty array, single element, all same elements

---

## 🧠 Interview Tips

1. **Pehle brute force batao** → phir optimize karo
2. **Time complexity bolke batao** — "Ye O(n) hai kyunki..."
3. **Edge cases mention karo** — empty, single, negative numbers
4. **Dry run dikhaao** — chhota example pe trace karo
5. **Space complexity bhi batao** — in-place vs extra space

---

## 📌 Must-Remember Formulas

```
Array sum = n * (n + 1) / 2
Missing number = expected_sum - actual_sum
XOR trick: a ^ a = 0, a ^ 0 = a
Rotate right by k: reverse all → reverse first k → reverse rest
Mid index: left + (right - left) / 2  (overflow safe)
```

---
