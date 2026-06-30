# 📚 Java Collections — Utility Methods & Streams

Java provides powerful utility classes to manipulate arrays and collections efficiently.

## 1. Arrays Class
Used specifically for standard Java arrays (`int[]`, `String[]`, etc.).

```java
int[] arr = {4, 1, 3, 2};

Arrays.sort(arr);                // Sort array in-place -> [1, 2, 3, 4]
Arrays.fill(arr, 0);             // Fill all elements with 0 -> [0, 0, 0, 0]
Arrays.copyOf(arr, 10);          // Create a new array of length 10
Arrays.binarySearch(arr, 3);     // Returns index of 3 if array is SORTED
Arrays.equals(arr1, arr2);       // True if arrays contain same elements in same order
Arrays.toString(arr);            // Print array contents neatly e.g., "[1, 2, 3]"
```

## 2. Collections Class
Used for Java Collections (like `List`, `Set`, etc.).

```java
List<Integer> list = Arrays.asList(4, 1, 3, 2);

Collections.sort(list);              // Sort list in-place
Collections.reverse(list);           // Reverse the elements
Collections.min(list);               // Find minimum element
Collections.max(list);               // Find maximum element
Collections.frequency(list, 1);      // Count occurrences of 1
Collections.swap(list, 0, 2);        // Swap elements at index 0 and 2
```

## 3. Conversions (Array ↔ Collections ↔ Strings)
```java
// String to Char Array
char[] chars = str.toCharArray();
String newStr = new String(chars);

// ArrayList to Array (Primitive)
int[] arr = list.stream().mapToInt(Integer::intValue).toArray();

// Array (Primitive) to ArrayList
List<Integer> list = Arrays.stream(arr).boxed().collect(Collectors.toList());
```

## 4. Streams Basics (Bonus)
Streams provide a declarative way to process collections (great for concise DSA operations).
```java
List<Integer> nums = Arrays.asList(5, 3, 8, 1, 9);

// Filter even numbers
List<Integer> evens = nums.stream().filter(n -> n % 2 == 0).collect(Collectors.toList());

// Sum of all elements
int sum = nums.stream().mapToInt(Integer::intValue).sum();

// Get unique elements
List<Integer> unique = nums.stream().distinct().collect(Collectors.toList());
```
