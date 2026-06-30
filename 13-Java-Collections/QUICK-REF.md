# ☕ Java Collections — Quick Reference

## ⚡ Cheat Sheet

### List
```java
List<Integer> list = new ArrayList<>(); // dynamic array
list.add(x); list.get(i); list.set(i,x); list.remove(i); list.size();
```

### Set
```java
Set<Integer> set = new HashSet<>();     // O(1), unordered
TreeSet<Integer> ts = new TreeSet<>();  // O(logn), sorted
set.add(x); set.contains(x); set.remove(x);
```

### Map
```java
Map<K,V> map = new HashMap<>();
map.put(k,v); map.get(k); map.getOrDefault(k,def);
map.containsKey(k); map.remove(k);
map.entrySet(); map.keySet(); map.values();
```

### Frequency Count
```java
Map<Integer,Integer> freq = new HashMap<>();
for (int x : arr) freq.merge(x, 1, Integer::sum);
```

### Sort Custom
```java
Arrays.sort(arr, (a,b) -> a[0] - b[0]);       // 2D array
list.sort(Comparator.comparingInt(a -> a.val)); // objects
Collections.sort(list, Collections.reverseOrder());
```

### Queue/Stack
```java
Queue<Integer> q = new LinkedList<>(); // FIFO: offer, poll, peek
Deque<Integer> s = new ArrayDeque<>(); // LIFO: push, pop, peek
PriorityQueue<Integer> pq = new PriorityQueue<>(); // min heap
```

## ⏱️ Complexity Table
| | ArrayList | LinkedList | HashSet | HashMap | TreeSet | TreeMap |
|-|-----------|------------|---------|---------|---------|---------|
| Add | O(1)* | O(1) | O(1) | O(1) | O(logn) | O(logn) |
| Get | O(1) | O(n) | - | O(1) | - | O(logn) |
| Contains | O(n) | O(n) | O(1) | O(1) | O(logn) | O(logn) |
| Remove | O(n) | O(1)† | O(1) | O(1) | O(logn) | O(logn) |

*amortized, †if node known

---
