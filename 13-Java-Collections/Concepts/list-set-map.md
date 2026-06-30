# 📚 Java Collections — List, Set, & Map

## 1. List (Ordered, Duplicates Allowed)
- **ArrayList**: Dynamic array. Fast access `O(1)`. Slow inserts/deletes in middle `O(n)`. Best for read-heavy operations.
- **LinkedList**: Node-based structure. Fast inserts/deletes at ends `O(1)`. Slow random access `O(n)`. Best for queues or stacks.

### Key Methods
```java
List<Integer> list = new ArrayList<>();
list.add(10);        // O(1)
list.add(0, 5);      // O(n)
list.get(0);         // O(1)
list.set(0, 20);     // O(1)
list.remove(0);      // O(n)
```

## 2. Set (No Duplicates)
| Feature | HashSet | TreeSet | LinkedHashSet |
|---------|---------|---------|---------------|
| Order | ❌ None | ✅ Sorted (Ascending) | ✅ Insertion Order |
| Time Complexity (Add/Contains) | `O(1)` Average | `O(log n)` | `O(1)` Average |
| Use Case | Fast lookup / Duplicate check | Sorted data requirement | Preserve insertion order |

### Key Methods
```java
Set<Integer> set = new HashSet<>();
set.add(10);
set.contains(10);

TreeSet<Integer> treeSet = new TreeSet<>();
treeSet.first();       // smallest
treeSet.last();        // largest
treeSet.floor(25);     // <= 25 (greatest element)
treeSet.ceiling(15);   // >= 15 (smallest element)
```

## 3. Map (Key-Value Pairs)
| Feature | HashMap | TreeMap | LinkedHashMap |
|---------|---------|---------|---------------|
| Order | ❌ None | ✅ Sorted by Key | ✅ Insertion Order |
| Time Complexity (Get/Put) | `O(1)` Average | `O(log n)` | `O(1)` Average |
| Use Case | Fast access / Frequency Count | Sorted keys needed | LRU Cache pattern |

### Key Methods
```java
Map<String, Integer> map = new HashMap<>();
map.put("apple", 3);
map.getOrDefault("banana", 0);
map.containsKey("apple");

// Iterate over Map
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " : " + entry.getValue());
}
```
