# 🔍 Binary Search — Quick Reference

## ⚡ Template
```java
int left = 0, right = n - 1;
while (left <= right) {
    int mid = left + (right - left) / 2;
    if (arr[mid] == target) return mid;
    else if (arr[mid] < target) left = mid + 1;
    else right = mid - 1;
}
```

## 🔑 Variations
| Type | Condition | Loop |
|------|-----------|------|
| **Exact match** | `left <= right` | `return mid` |
| **Lower bound** | `left < right` | `right = mid` |
| **Upper bound** | `left < right` | `left = mid + 1` |
| **BS on answer** | `left < right` | `if (feasible) right=mid else left=mid+1` |

## ⚠️ Common Mistakes
- `left <= right` vs `left < right` — problem ke hisaab se choose karo
- `mid = left + (right - left) / 2` — overflow safe
- Off-by-one — dry run karo chhote example pe

## 🧠 Identification
"Sorted" + "Search" → Binary Search
"Minimum X such that..." → BS on Answer
"First/Last occurrence" → Modified BS

---
