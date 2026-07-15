# 🔄 Recursion — Quick Reference
## ⚡ Backtracking Template
```java
void backtrack(state) {
    if (complete) { result.add(copy); return; }
    for (choice : choices) {
        if (valid(choice)) {
            make(choice);
            backtrack(next);
            undo(choice); // BACKTRACK
        }
    }
}
```
## 🔑 Key Problems
- Subsets → include/exclude, index+1
- Permutations → used[] array
- Combinations → like subsets, fixed size k
- N-Queens → row-by-row, isSafe check

## ⚠️ Yaad Rakho
- Base case ZAROOR likho
- Backtrack = undo karo jo kiya
- Copy banao result mein add karne se pehle

---
