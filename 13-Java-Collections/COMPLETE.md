# ☕ Java Collections — Complete Learning Guide

## 1. List (Ordered, Duplicates Allowed)

```java
// ✅ ArrayList — Dynamic array, fast access O(1)
List<Integer> list = new ArrayList<>();
list.add(10);                    // end mein add — O(1)
list.add(0, 5);                  // index pe insert — O(n)
list.get(0);                     // access — O(1)
list.set(0, 20);                 // update — O(1)
list.remove(0);                  // index se remove — O(n)
list.remove(Integer.valueOf(10)); // value se remove
list.contains(10);               // search — O(n)
list.size();                     // size
list.isEmpty();                  // empty check
list.indexOf(10);                // first occurrence
Collections.sort(list);         // sort — O(n log n)
Collections.reverse(list);      // reverse

// ✅ ArrayList to Array & vice versa
int[] arr = list.stream().mapToInt(Integer::intValue).toArray();
List<Integer> list2 = new ArrayList<>(Arrays.asList(1, 2, 3));

// ✅ LinkedList — Node based, fast insert/delete
List<Integer> ll = new LinkedList<>();
// Same methods, but O(1) add/remove at head & tail
```

## 2. Set (No Duplicates)

```java
// ✅ HashSet — Unordered, O(1) operations
Set<Integer> set = new HashSet<>();
set.add(10);                     // add — O(1)
set.contains(10);                // check — O(1)
set.remove(10);                  // remove — O(1)
set.size();

// ✅ TreeSet — Sorted order, O(log n) operations
TreeSet<Integer> treeSet = new TreeSet<>();
treeSet.add(30); treeSet.add(10); treeSet.add(20);
// treeSet = [10, 20, 30] — sorted!
treeSet.first();                 // 10 — smallest
treeSet.last();                  // 30 — largest
treeSet.floor(25);               // 20 — <= 25 sabse bada
treeSet.ceiling(15);             // 20 — >= 15 sabse chhota

// ✅ LinkedHashSet — Insertion order maintain karta hai
Set<Integer> lhs = new LinkedHashSet<>();
```

### Set Comparison
| Feature | HashSet | TreeSet | LinkedHashSet |
|---------|---------|---------|---------------|
| Order | ❌ None | ✅ Sorted | ✅ Insertion |
| Add/Contains | O(1) | O(log n) | O(1) |
| Use case | Fast lookup | Sorted data | Order + fast |

## 3. Map (Key-Value Pairs)

```java
// ✅ HashMap — Most used, O(1) average
Map<String, Integer> map = new HashMap<>();
map.put("apple", 3);            // add/update
map.get("apple");                // 3 — value get karo
map.getOrDefault("banana", 0);  // default value agar key nahi hai
map.containsKey("apple");       // true — key exists?
map.containsValue(3);           // true — value exists?
map.remove("apple");            // remove
map.size();
map.isEmpty();

// Iterate karo
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}
for (String key : map.keySet()) { /* keys */ }
for (int val : map.values()) { /* values */ }

// ✅ Frequency counting pattern (BAHUT COMMON!)
Map<Integer, Integer> freq = new HashMap<>();
for (int num : arr) {
    freq.put(num, freq.getOrDefault(num, 0) + 1);
    // ya: freq.merge(num, 1, Integer::sum);
}

// ✅ TreeMap — Sorted by key
TreeMap<Integer, String> tm = new TreeMap<>();
tm.firstKey();                   // smallest key
tm.lastKey();                    // largest key
tm.floorKey(5);                  // <= 5 largest key
tm.ceilingKey(5);                // >= 5 smallest key

// ✅ LinkedHashMap — Insertion order maintain
Map<String, Integer> lhm = new LinkedHashMap<>();
```

## 4. Queue & Deque

```java
// ✅ Queue — FIFO
Queue<Integer> queue = new LinkedList<>();
queue.offer(10);  queue.poll();  queue.peek();

// ✅ Deque — Both ends
Deque<Integer> deque = new ArrayDeque<>();
deque.offerFirst(10); deque.offerLast(20);
deque.pollFirst();    deque.pollLast();

// ✅ PriorityQueue — Heap-based
PriorityQueue<Integer> pq = new PriorityQueue<>(); // min heap
PriorityQueue<Integer> maxPq = new PriorityQueue<>(Collections.reverseOrder());
```

## 5. Comparable vs Comparator

```java
// ✅ Comparable — class ke andar define karo (natural ordering)
class Student implements Comparable<Student> {
    String name; int marks;
    
    @Override
    public int compareTo(Student other) {
        return this.marks - other.marks; // ascending by marks
    }
}

// ✅ Comparator — bahar se sorting logic do
List<Student> students = new ArrayList<>();
students.sort((a, b) -> b.marks - a.marks);  // descending by marks
students.sort(Comparator.comparing(s -> s.name)); // by name

// ✅ 2D Array Sort
int[][] intervals = {{3,5},{1,3},{2,4}};
Arrays.sort(intervals, (a, b) -> a[0] - b[0]); // sort by first element
```

## 6. Useful Utility Methods

```java
// ✅ Arrays class
Arrays.sort(arr);                // sort
Arrays.fill(arr, 0);            // sab 0 bhar do
Arrays.copyOf(arr, newLen);     // copy
Arrays.binarySearch(arr, key);  // sorted array mein search
Arrays.equals(arr1, arr2);      // compare
Arrays.toString(arr);           // print friendly

// ✅ Collections class
Collections.sort(list);
Collections.reverse(list);
Collections.min(list);
Collections.max(list);
Collections.frequency(list, obj);
Collections.swap(list, i, j);
Collections.unmodifiableList(list); // read-only

// ✅ String ↔ Char Array
char[] chars = str.toCharArray();
String str = new String(chars);
String str = String.valueOf(chars);

// ✅ Integer conversions
int x = Integer.parseInt("123");
String s = String.valueOf(123);
int maxVal = Integer.MAX_VALUE;  // 2^31 - 1
int minVal = Integer.MIN_VALUE;  // -2^31
```

## 7. Streams Basics (Bonus)

```java
// ✅ Common Stream operations
List<Integer> nums = Arrays.asList(5, 3, 8, 1, 9);

// Filter
List<Integer> even = nums.stream().filter(n -> n % 2 == 0).collect(Collectors.toList());

// Map (transform)
List<Integer> doubled = nums.stream().map(n -> n * 2).collect(Collectors.toList());

// Sum, Min, Max
int sum = nums.stream().mapToInt(Integer::intValue).sum();
int min = nums.stream().min(Integer::compareTo).orElse(0);

// Sort
List<Integer> sorted = nums.stream().sorted().collect(Collectors.toList());

// Distinct
List<Integer> unique = nums.stream().distinct().collect(Collectors.toList());
```

---

## 🎯 DSA Mein Kya Use Karo?

| Problem Type | Collection |
|-------------|------------|
| Duplicate check | HashSet |
| Frequency count | HashMap |
| Sorted unique | TreeSet |
| LIFO (undo) | ArrayDeque (Stack) |
| FIFO (BFS) | LinkedList (Queue) |
| Top-K | PriorityQueue |
| LRU Cache | LinkedHashMap |
| Graph adjacency | List<List<Integer>> |

---

> **Next:** [PROBLEMS.md](PROBLEMS.md) 💪
