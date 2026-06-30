# 📚 Java Collections — Comparable vs Comparator

Sorting custom objects or multi-dimensional arrays requires defining a sorting logic using `Comparable` or `Comparator`.

## 1. Comparable (Natural Ordering)
- Used to define the **default** sorting logic for a class.
- Requires modifying the class itself by implementing `Comparable<T>`.
- Overrides the `compareTo(T o)` method.

```java
class Student implements Comparable<Student> {
    String name; 
    int marks;
    
    @Override
    public int compareTo(Student other) {
        // Ascending by marks
        return this.marks - other.marks; 
    }
}
```

## 2. Comparator (Custom Ordering)
- Used when you need **multiple sorting logics** or you **cannot modify** the class.
- Defined outside the class, usually using lambdas in modern Java.
- Overrides the `compare(T o1, T o2)` method.

```java
List<Student> students = new ArrayList<>();

// Descending by marks
students.sort((a, b) -> b.marks - a.marks); 

// Ascending by name
students.sort(Comparator.comparing(s -> s.name)); 
```

## 3. Sorting 2D Arrays (Very Common in DSA)
Whenever working with intervals or coordinate points, you frequently use a `Comparator`.
```java
int[][] intervals = {{3, 5}, {1, 3}, {2, 4}};

// Sort by the first element of each sub-array ascending
Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
// intervals becomes: [[1, 3], [2, 4], [3, 5]]
```
