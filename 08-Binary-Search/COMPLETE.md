# 🔍 Binary Search — Complete Learning Guide

## 1. Basic Binary Search
```java
// ✅ Sorted array mein element dhundho
// Time: O(log n), Space: O(1)

public static int binarySearch(int[] arr, int target) {
    int left = 0, right = arr.length - 1;
    
    while (left <= right) {                    // <= hai, < nahi!
        int mid = left + (right - left) / 2;   // overflow safe mid
        
        if (arr[mid] == target) {
            return mid;                        // mil gaya!
        } else if (arr[mid] < target) {
            left = mid + 1;                    // right half mein dhundho
        } else {
            right = mid - 1;                   // left half mein dhundho
        }
    }
    
    return -1;                                 // nahi mila
}
```

## 2. Lower Bound / Upper Bound
```java
// ✅ Lower Bound: pehla index jahan arr[i] >= target
public static int lowerBound(int[] arr, int target) {
    int left = 0, right = arr.length;
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] < target) left = mid + 1;
        else right = mid;
    }
    return left;
}

// ✅ Upper Bound: pehla index jahan arr[i] > target
public static int upperBound(int[] arr, int target) {
    int left = 0, right = arr.length;
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] <= target) left = mid + 1;
        else right = mid;
    }
    return left;
}
```

## 3. Search in Rotated Sorted Array
```java
// ✅ Rotated sorted array mein search
// Time: O(log n)

public static int searchRotated(int[] nums, int target) {
    int left = 0, right = nums.length - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] == target) return mid;
        
        // Left half sorted hai
        if (nums[left] <= nums[mid]) {
            if (target >= nums[left] && target < nums[mid]) {
                right = mid - 1;               // left half mein hai
            } else {
                left = mid + 1;                // right half mein hai
            }
        }
        // Right half sorted hai
        else {
            if (target > nums[mid] && target <= nums[right]) {
                left = mid + 1;                // right half mein hai
            } else {
                right = mid - 1;               // left half mein hai
            }
        }
    }
    return -1;
}
```

## 4. Binary Search on Answer
```java
// ✅ Problem: Koko Eating Bananas — minimum speed K se sab kele kha lo H hours mein
// Approach: Answer pe binary search karo (speed 1 se max tak)
// Time: O(n * log(max))

public static int minEatingSpeed(int[] piles, int h) {
    int left = 1, right = Arrays.stream(piles).max().getAsInt();
    
    while (left < right) {
        int mid = left + (right - left) / 2;
        
        if (canFinish(piles, mid, h)) {
            right = mid;                       // ho sakta hai, aur kam try karo
        } else {
            left = mid + 1;                    // nahi ho sakta, speed badhao
        }
    }
    
    return left;
}

private static boolean canFinish(int[] piles, int speed, int h) {
    int hours = 0;
    for (int pile : piles) {
        hours += (pile + speed - 1) / speed;   // ceil division
    }
    return hours <= h;
}
```

## 5. Find Peak Element
```java
// ✅ Array mein koi bhi peak element dhundho
// Time: O(log n)

public static int findPeakElement(int[] nums) {
    int left = 0, right = nums.length - 1;
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] > nums[mid + 1]) {
            right = mid;                       // peak left side mein
        } else {
            left = mid + 1;                    // peak right side mein
        }
    }
    return left;
}
```

## 🎯 Binary Search Kab Use Karo?
- **Sorted array** mein search → Direct BS
- **"Minimum value such that condition is true"** → BS on Answer
- **Monotonic function** pe search → BS on Answer
- **"Find first/last occurrence"** → Modified BS with bounds

---

> **Next:** [PROBLEMS.md](PROBLEMS.md) 💪
