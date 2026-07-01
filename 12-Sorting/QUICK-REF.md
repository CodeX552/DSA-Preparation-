# 📊 Sorting — Quick Reference
## ⚡ Must Remember
- **Merge Sort**: O(n log n), stable, extra space O(n)
- **Quick Sort**: O(n log n) avg, in-place, not stable
- **Java Arrays.sort()**: Primitives=QuickSort, Objects=TimSort
- **Stable sorting** = equal elements ka order maintain hota hai

## Custom Sorting
```java
Arrays.sort(arr, (a, b) -> a[0] - b[0]); // sort by first element
Arrays.sort(arr, (a, b) -> a[1] - b[1]); // sort by second element
Collections.sort(list, Comparator.reverseOrder()); // reverse
```

---
