# 🔍 Binary Search — Complete Learning Guide

## 1. Basic Binary Search

Binary Search ek bohot hi fast searching algorithm hai (Divide & Conquer par based).
Yeh **sirf sorted arrays** par kaam karta hai. Har step mein hum search space ko aadha kar dete hain.
* **Kaise kaam karta hai?** Hum array ke middle element ko check karte hain. Agar target bada hai, toh right half mein dhundhte hain, warna left half mein.

![Binary vs Linear Search Animation](https://blog.penjee.com/wp-content/uploads/2015/04/binary-and-linear-search-animations.gif)

> **Example:**
> - **Input:** `arr = [2, 4, 6, 8, 10, 12]`, `target = 8`
> - **Output:** `3` (Kyunki 8 index 3 par hai)

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

Kabhi kabhi humein sirf array mein search hi nahi karna hota, balki element ki exact position (insert karne ke liye) ya occurrences nikalni hoti hain.
* **Lower Bound**: Woh pehla index jahan value `>= target` ho. (Target ke barabar ya usse bada pehla number).
* **Upper Bound**: Woh pehla index jahan value `> target` ho. (Target se strictly bada pehla number).

> **Example:**
> - **Input:** `arr = [1, 2, 2, 2, 3, 4]`, `target = 2`
> - **Output:** `Lower Bound = 1` (Pehli baar 2 yahan aaya hai), `Upper Bound = 4` (2 se bada pehla number 3 hai, jo index 4 par hai)

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

Jab ek sorted array ko kisi pivot point se rotate kiya jata hai, toh array 2 sorted halves mein bant jata hai. 
Isme hamesha kam se kam ek half (left ya right) **strictly sorted** hota hai. Hum bas yeh check karte hain ki konsa half sorted hai, aur kya hamara target uss sorted range mein aata hai ya nahi.

> **Example:**
> - **Input:** `arr = [4, 5, 6, 7, 0, 1, 2]`, `target = 0`
> - **Output:** `4` (Array rotate hone ke baad bhi 0 ka correct index 4 hai)

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

Yeh advance pattern tab use hota hai jab actual array mein kuch dhundhna nahi hota, balki ek **valid range (jaise 1 se maximum speed tak)** ke andar se minimum ya maximum possible answer nikalna hota hai.
Hum answer ke possibilities par Binary Search lagate hain aur ek `canFinish()` function banate hain jo check karta hai ki `mid` value ek valid answer ban sakti hai ya nahi.

> **Example (Koko Eating Bananas):**
> - **Input:** `piles = [3, 6, 7, 11]`, `h = 8`
> - **Output:** `4` (Agar Koko 4 bananas/hour khayega, toh woh exactly 8 ghante mein sab kha lega. Minimum speed 4 hi hai!)

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

Ek peak element woh hota hai jo apne dono padosiyo (neighbors) se bada hota hai. 
Unsorted array mein bhi Binary Search lag sakta hai! Kaise? Agar `mid` wala element apne agle (right) element se chota hai, toh iska matlab slope upar jaa raha hai, yani ki peak right side mein hi kahin hoga.

> **Example:**
> - **Input:** `arr = [1, 2, 3, 1]`
> - **Output:** `2` (Index 2 par value 3 hai, jo apne padosiyo '2' aur '1' dono se bada hai, isliye yeh ek peak hai!)

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
