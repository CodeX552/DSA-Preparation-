# 📚 Stack — Quick Reference

## ⚡ Java Stack Usage
```java
Deque<Integer> stack = new ArrayDeque<>(); // prefer over Stack class
stack.push(val);     // add to top
stack.pop();         // remove from top
stack.peek();        // see top (don't remove)
stack.isEmpty();     // check empty
```

## 🔑 Patterns
| Pattern | Use Case | Template |
|---------|----------|----------|
| **Matching** | Parentheses | Open push, close match pop |
| **Monotonic Decreasing** | NGE, Stock Span | Pop smaller, push current |
| **Monotonic Increasing** | NSE, Histogram | Pop larger, push current |
| **Two Stacks** | Queue, Min Stack | Transfer between stacks |

## 📝 NGE Template
```java
Deque<Integer> stack = new ArrayDeque<>();
for (int i = n - 1; i >= 0; i--) {
    while (!stack.isEmpty() && stack.peek() <= arr[i]) stack.pop();
    result[i] = stack.isEmpty() ? -1 : stack.peek();
    stack.push(arr[i]);
}
```

## ⚠️ Edge Cases
- Empty stack pe pop/peek → Exception
- Single element
- All same elements
- Already sorted (ascending/descending)

---
