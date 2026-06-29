# 🔢 Array Patterns — Deep Dive

## Pattern 1: Two Pointer Variations

### Type A: Opposite Direction (left → ← right)
```java
// Use: Pair sum, palindrome, reverse
int left = 0, right = n - 1;
while (left < right) {
    // process arr[left] and arr[right]
    // move based on condition
}
```

### Type B: Same Direction (slow → fast →)
```java
// Use: Remove duplicates, partition
int slow = 0;
for (int fast = 0; fast < n; fast++) {
    if (condition) {
        arr[slow] = arr[fast];
        slow++;
    }
}
```

### Type C: Three Pointer
```java
// Use: 3Sum, Dutch National Flag
// Fix one, two pointer on rest
for (int i = 0; i < n - 2; i++) {
    int left = i + 1, right = n - 1;
    while (left < right) {
        // process
    }
}
```

---

## Pattern 2: Sliding Window Variations

### Fixed Size Window
```java
// Window ka size K fix hai
// Pehle window banao, phir slide karo
for (int i = 0; i < k; i++) windowSum += arr[i];
for (int i = k; i < n; i++) {
    windowSum += arr[i] - arr[i-k]; // add new, remove old
    // process
}
```

### Variable Size Window
```java
// Window ka size condition pe depend karta hai
int left = 0;
for (int right = 0; right < n; right++) {
    // expand: add arr[right] to window
    while (window is invalid) {
        // shrink: remove arr[left] from window
        left++;
    }
    // process valid window
}
```

---

## Pattern 3: Prefix / Suffix Arrays

### Kab Use Karo?
- Range sum queries → Prefix Sum
- Product except self → Left product × Right product
- Min/Max from both sides → Prefix Max, Suffix Max (Trapping Rain Water)

```java
// Prefix Max Array
int[] prefixMax = new int[n];
prefixMax[0] = arr[0];
for (int i = 1; i < n; i++)
    prefixMax[i] = Math.max(prefixMax[i-1], arr[i]);

// Suffix Max Array
int[] suffixMax = new int[n];
suffixMax[n-1] = arr[n-1];
for (int i = n - 2; i >= 0; i--)
    suffixMax[i] = Math.max(suffixMax[i+1], arr[i]);
```

---

## Pattern 4: Sorting-Based Approach

### Kab Use Karo?
- Merge Intervals → sort by start
- 3Sum → sort first, then two pointer
- Meeting Rooms → sort by start/end time

```java
// Sort 2D array by first element
Arrays.sort(intervals, (a, b) -> a[0] - b[0]);

// Sort by second element
Arrays.sort(intervals, (a, b) -> a[1] - b[1]);

// Custom object sorting
Arrays.sort(arr, (a, b) -> Integer.compare(a, b));
```

---

## Pattern 5: Cyclic Sort

### Kab Use Karo?
- Numbers 1 to N range mein hain
- Missing number, duplicate number find karna

```java
// Har number ko uski sahi position pe daal do
int i = 0;
while (i < n) {
    int correctIdx = arr[i] - 1; // number 1 index 0 pe jaayega
    if (arr[i] != arr[correctIdx]) {
        swap(arr, i, correctIdx);
    } else {
        i++;
    }
}
// Ab jo number galat position pe hai woh missing/duplicate hai
```

---

## 🎯 Pattern Identification Guide

| Problem Mein Ye Dikhe | Pattern Use Karo |
|----------------------|------------------|
| "Sorted array" + "find pair" | Two Pointer |
| "Subarray of size K" | Fixed Sliding Window |
| "Longest subarray with condition" | Variable Sliding Window |
| "Maximum subarray sum" | Kadane's Algorithm |
| "Range sum query" | Prefix Sum |
| "Sort 0, 1, 2" | Dutch National Flag |
| "Numbers 1 to N, find missing" | Cyclic Sort |
| "In-place rearrange" | Two Pointer / Swap |
| "Count pairs with sum" | HashMap |

---
