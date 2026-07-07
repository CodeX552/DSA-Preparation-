# 📚 Stack — Complete Learning Guide

## 📖 Table of Contents
1. [Stack Basics](#1-stack-basics)
2. [Parenthesis Problems](#2-parenthesis-problems)
3. [Monotonic Stack (NGE/NSE)](#3-monotonic-stack-ngense)
4. [Min Stack Design](#4-min-stack-design)
5. [Expression Problems](#5-expression-problems)
6. [Solved Problems](#6-solved-problems)

---

## 1. Stack Basics

### Stack Kya Hai?
**LIFO** — Last In, First Out. Socho plate ka stack — upar se rakhte ho (push), upar se uthate ho (pop).

```java
import java.util.Stack;

// Java mein Stack use karna
Stack<Integer> stack = new Stack<>();

stack.push(10);          // element daal do
stack.push(20);
stack.push(30);          // stack: [10, 20, 30] ← top

stack.peek();            // 30 — top element dekho (hatao nahi)
stack.pop();             // 30 — top element nikalo
stack.isEmpty();         // false — empty hai?
stack.size();            // 2

// ✅ Better alternative: Deque use karo (Stack is legacy)
Deque<Integer> stack2 = new ArrayDeque<>();
stack2.push(10);         // addFirst
stack2.pop();            // removeFirst
stack2.peek();           // peekFirst
```

### Stack Operations Complexity
| Operation | Time |
|-----------|------|
| push | O(1) |
| pop | O(1) |
| peek | O(1) |
| isEmpty | O(1) |
| search | O(n) |

---

## 2. Parenthesis Problems

```java
// ✅ Problem: Valid Parentheses — brackets balanced hain?
// Approach: Opening bracket push, closing bracket pe check & pop
// Time: O(n), Space: O(n)

public static boolean isValid(String s) {
    Deque<Character> stack = new ArrayDeque<>();
    
    for (char c : s.toCharArray()) {
        if (c == '(' || c == '{' || c == '[') {
            stack.push(c);            // opening bracket → push karo
        } else {
            if (stack.isEmpty()) return false; // closing bracket but stack empty
            
            char top = stack.pop();   // top element nikalo
            // Check matching
            if (c == ')' && top != '(') return false;
            if (c == '}' && top != '{') return false;
            if (c == ']' && top != '[') return false;
        }
    }
    
    return stack.isEmpty();           // stack empty = sab balanced ✅
}

// Example: "({[]})" → true
// Push (, push {, push [
// ] → pop [ → match ✅
// } → pop { → match ✅
// ) → pop ( → match ✅
// Stack empty → true
```

---

## 3. Monotonic Stack (NGE/NSE)

### Concept Kya Hai?
**Monotonic Stack** ek aisa stack hai jo hamesha sorted rehta hai (increasing ya decreasing). Ye **Next Greater Element (NGE)**, **Next Smaller Element (NSE)** type problems mein use hota hai.

```java
// ✅ Problem: Next Greater Element — har element ke liye right mein pehla bada element
// Approach: Right se left traverse, stack mein decreasing order maintain karo
// Time: O(n), Space: O(n)

public static int[] nextGreaterElement(int[] arr) {
    int n = arr.length;
    int[] result = new int[n];
    Deque<Integer> stack = new ArrayDeque<>(); // monotonic decreasing stack
    
    // Right se left traverse karo
    for (int i = n - 1; i >= 0; i--) {
        // Stack se chhote elements hatao (kaam ke nahi)
        while (!stack.isEmpty() && stack.peek() <= arr[i]) {
            stack.pop();              // ye chhota hai, kisi ke kaam ka nahi
        }
        
        // Stack ka top = next greater element
        result[i] = stack.isEmpty() ? -1 : stack.peek();
        
        // Current element push karo
        stack.push(arr[i]);
    }
    
    return result;
}

// Dry Run: arr = [4, 5, 2, 10, 8]
// i=4: stack=[], result[4]=-1, push 8 → stack=[8]
// i=3: pop 8 (8<10), stack=[], result[3]=-1, push 10 → stack=[10]
// i=2: stack=[10], 10>2, result[2]=10, push 2 → stack=[10,2]
// i=1: pop 2 (2<5), stack=[10], 10>5, result[1]=10, push 5 → stack=[10,5]
// i=0: pop 5 (5>4? no, 5>4), stack=[10,5], result[0]=5, push 4
// Result: [5, 10, 10, -1, -1]
```

```java
// ✅ Problem: Daily Temperatures — kitne din baad garam hoga?
// Approach: Monotonic decreasing stack (indices store karo)
// Time: O(n), Space: O(n)

public static int[] dailyTemperatures(int[] temperatures) {
    int n = temperatures.length;
    int[] result = new int[n];
    Deque<Integer> stack = new ArrayDeque<>(); // indices store karo
    
    for (int i = 0; i < n; i++) {
        // Jab tak stack ka top chhota hai current se
        while (!stack.isEmpty() && temperatures[stack.peek()] < temperatures[i]) {
            int prevDay = stack.pop();
            result[prevDay] = i - prevDay; // kitne din ka gap
        }
        stack.push(i);                    // current day push karo
    }
    
    return result;
}

// Example: [73, 74, 75, 71, 69, 72, 76, 73]
// Result: [1,  1,  4,  2,  1,  1,  0,  0]
```

```java
// ✅ Problem: Largest Rectangle in Histogram
// Approach: Monotonic stack — har bar ka left & right boundary dhundho
// Time: O(n), Space: O(n)

public static int largestRectangleArea(int[] heights) {
    int n = heights.length;
    Deque<Integer> stack = new ArrayDeque<>();
    int maxArea = 0;
    
    for (int i = 0; i <= n; i++) {
        int currentHeight = (i == n) ? 0 : heights[i]; // dummy 0 at end
        
        while (!stack.isEmpty() && currentHeight < heights[stack.peek()]) {
            int height = heights[stack.pop()];    // bar ki height
            int width = stack.isEmpty() ? i : (i - stack.peek() - 1); // width
            maxArea = Math.max(maxArea, height * width);
        }
        
        stack.push(i);
    }
    
    return maxArea;
}
```

---

## 4. Min Stack Design

```java
// ✅ Problem: Stack banao jo O(1) mein minimum de
// Approach: Do stacks — ek normal, ek min track kare
// Time: O(1) for all operations

class MinStack {
    Deque<Integer> stack;
    Deque<Integer> minStack; // minimum values track karo
    
    public MinStack() {
        stack = new ArrayDeque<>();
        minStack = new ArrayDeque<>();
    }
    
    public void push(int val) {
        stack.push(val);
        // MinStack mein push karo agar current val <= current min
        if (minStack.isEmpty() || val <= minStack.peek()) {
            minStack.push(val);
        }
    }
    
    public void pop() {
        int val = stack.pop();
        // Agar popped value current min thi, toh minStack se bhi hatao
        if (val == minStack.peek()) {
            minStack.pop();
        }
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
        return minStack.peek();      // O(1) mein minimum!
    }
}
```

---

## 5. Expression Problems

```java
// ✅ Problem: Evaluate Reverse Polish Notation (Postfix)
// Approach: Number push, operator pop two + calculate + push result
// Time: O(n), Space: O(n)

public static int evalRPN(String[] tokens) {
    Deque<Integer> stack = new ArrayDeque<>();
    
    for (String token : tokens) {
        if (isOperator(token)) {
            int b = stack.pop();      // second operand (pehle pop hoga)
            int a = stack.pop();      // first operand
            
            switch (token) {
                case "+": stack.push(a + b); break;
                case "-": stack.push(a - b); break;
                case "*": stack.push(a * b); break;
                case "/": stack.push(a / b); break; // integer division
            }
        } else {
            stack.push(Integer.parseInt(token)); // number push karo
        }
    }
    
    return stack.pop();               // final result
}

private static boolean isOperator(String s) {
    return s.equals("+") || s.equals("-") || s.equals("*") || s.equals("/");
}

// Example: ["2","1","+","3","*"] = (2+1)*3 = 9
```

---

## 6. Solved Problems

### Stock Span Problem 🟡 Medium
```java
// ✅ Problem: Har din ke liye kitne consecutive din price <= aaj ka price
// Approach: Monotonic decreasing stack (indices store karo)
// Time: O(n), Space: O(n)

public static int[] stockSpan(int[] prices) {
    int n = prices.length;
    int[] span = new int[n];
    Deque<Integer> stack = new ArrayDeque<>(); // indices
    
    for (int i = 0; i < n; i++) {
        // Pop karo jab tak stack ka top <= current price
        while (!stack.isEmpty() && prices[stack.peek()] <= prices[i]) {
            stack.pop();
        }
        
        span[i] = stack.isEmpty() ? (i + 1) : (i - stack.peek());
        stack.push(i);
    }
    
    return span;
}

// Example: [100, 80, 60, 70, 60, 75, 85]
// Span:    [1,   1,  1,  2,  1,  4,  6]
```

### Implement Queue using Stacks 🟢 Easy
```java
// ✅ Two stacks se Queue banao
class MyQueue {
    Deque<Integer> pushStack;  // yahan push karo
    Deque<Integer> popStack;   // yahan se pop karo
    
    public MyQueue() {
        pushStack = new ArrayDeque<>();
        popStack = new ArrayDeque<>();
    }
    
    public void push(int x) {
        pushStack.push(x);            // hamesha pushStack mein dalo
    }
    
    public int pop() {
        if (popStack.isEmpty()) {
            // popStack empty hai → pushStack se sab transfer karo
            while (!pushStack.isEmpty()) {
                popStack.push(pushStack.pop());
            }
        }
        return popStack.pop();        // FIFO order mein milega
    }
    
    public int peek() {
        if (popStack.isEmpty()) {
            while (!pushStack.isEmpty()) {
                popStack.push(pushStack.pop());
            }
        }
        return popStack.peek();
    }
    
    public boolean empty() {
        return pushStack.isEmpty() && popStack.isEmpty();
    }
}
```

---

## 🎯 Common Mistakes
1. **Empty stack pe pop/peek** — pehle `isEmpty()` check karo
2. **Stack vs Queue confuse** — Stack=LIFO, Queue=FIFO
3. **Monotonic stack direction** — NGE right se left, ya left se right — dhyan se socho
4. **Index vs Value** — Stack mein kya store kar rahe ho, index ya value?

---

> **Next:** [PROBLEMS.md](PROBLEMS.md) mein practice karo! 💪
