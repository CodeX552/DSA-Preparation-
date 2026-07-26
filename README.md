# 📚 DSA Placement Prep - Complete Guide (Java + Hinglish)
## 🎯 Target: Google, Microsoft, Amazon, Walmart, Accenture & Top Product Companies

---

## ⚡ Quick Start (5 Minutes)

### **Ye repository kya hai?**
Ek **complete, professionally-organized DSA preparation guide** jo tumhe placement interviews crack karne mein help karegi. **80+ carefully curated problems** with detailed Hinglish explanations aur Java code.

### **Kahan se shuru karein?**
1. ✅ Ye README padho (5 min) ← **TUM YAHAN HO**
2. 📅 [STUDY-ROADMAP.md](STUDY-ROADMAP.md) dekho timeline ke liye
3. 📂 Koi bhi topic choose karo → Uska `00-START.md` file open karo

---

## 📂 Repository Structure

Har **13 topics** mein exactly **4 files** hain:

```
01-Array/
├── 00-START.md         ← Pehle ye padho!
├── COMPLETE.md         ← Full learning material (2-4 hours)
├── PROBLEMS.md         ← Practice problems (1-2 hours)
├── QUICK-REF.md        ← Cheat sheet (interview se 10 min pehle)
└── Concepts/           ← Deep-dive concept resources
```

**[SAME PATTERN HAR 13 TOPICS MEIN]**

### **4-File System Samjho**

| File | Purpose | Time |
|------|---------|------|
| **00-START.md** | Orientation - kya seekhna hai | 10 min |
| **COMPLETE.md** | Full learning + problems + solutions | 2-4 hours |
| **PROBLEMS.md** | Extra practice (with hints) | 1-2 hours |
| **QUICK-REF.md** | 2-page cheat sheet (interview se pehle revise karo) | 10 min |

---

## 📚 13 Topics - Quick Overview

### **WEEK 1: Foundation (Days 1-7)**
| # | Topic | Folder | Interview Frequency |
|---|-------|--------|-------------------|
| 1 | **Array** | [01-Array](01-Array/00-START.md) | 🔴 95% interviews |
| 2 | **String** | [02-String](02-String/00-START.md) | 🔴 85% interviews |
| 3 | **Linked List** | [03-LinkedList](03-LinkedList/00-START.md) | 🟠 80% interviews |
| 4 | **Sorting** | [12-Sorting](12-Sorting/00-START.md) | 🟠 75% interviews |

### **WEEK 2: Core Data Structures (Days 8-14)**
| # | Topic | Folder | Interview Frequency |
|---|-------|--------|-------------------|
| 5 | **Stack** | [04-Stack](04-Stack/00-START.md) | 🟠 70% interviews |
| 6 | **Queue** | [05-Queue](05-Queue/00-START.md) | 🟡 55% interviews |
| 7 | **Tree** | [06-Tree](06-Tree/00-START.md) | 🔴 95% interviews |
| 8 | **Heap** | [11-Heap](11-Heap/00-START.md) | 🟡 60% interviews |

### **WEEK 3: Advanced (Days 15-21)**
| # | Topic | Folder | Interview Frequency |
|---|-------|--------|-------------------|
| 9 | **Graph** | [07-Graph](07-Graph/00-START.md) | 🔴 85% interviews |
| 10 | **Binary Search** | [08-Binary-Search](08-Binary-Search/00-START.md) | 🟠 75% interviews |
| 11 | **Recursion & Backtracking** | [09-Recursion](09-Recursion/00-START.md) | 🟠 70% interviews |
| 12 | **Dynamic Programming** | [10-DP](10-DP/00-START.md) | 🔴 90% interviews |

### **WEEK 4: Language Mastery (Days 22-28)**
| # | Topic | Folder | Interview Frequency |
|---|-------|--------|-------------------|
| 13 | **Java Collections** | [13-Java-Collections](13-Java-Collections/00-START.md) | 🔴 Har interview mein |

**Full timeline:** [STUDY-ROADMAP.md](STUDY-ROADMAP.md)

---

## 🚀 Kaise Use Karein Ye Repository

### **3 SIMPLE STEPS**

```
Step 1: STUDY-ROADMAP.md padho (15 min) — Timeline samjho
Step 2: Ek topic choose karo (upar table se)
Step 3: Us topic ka 00-START.md open karo — aur shuru ho jao!
```

### **Recommended Study Flow (Har Topic Ke Liye)**

```
00-START.md → COMPLETE.md → PROBLEMS.md → QUICK-REF.md
   (5 min)     (2-4 hrs)     (1-2 hrs)      (10 min)
```

1. **00-START.md** — Topic ka overview, kya seekhna hai
2. **COMPLETE.md** — Theory padho, solved problems karo
3. **PROBLEMS.md** — Khud se practice karo (hints available)
4. **QUICK-REF.md** — Interview se pehle ek baar revise karo

---

## 🏢 Company-Wise Focus

### **Google / Microsoft / Amazon**
- Trees, Graphs, DP — sabse zyada focus
- Binary Search variations — must karo
- System Design basics — bonus

### **Walmart / Accenture**
- Array, String patterns — foundation strong rakho
- Stack, Queue applications — common questions
- Java Collections — definitely puchenge

### **Product Companies (General)**
- Recursion + Backtracking — key hai
- Sliding Window, Two Pointer — patterns yaad karo
- Time/Space complexity analysis — har answer mein batao

---

## ⏱️ Time Commitment

| Phase | Duration | Focus |
|-------|----------|-------|
| **Learning** | 14-20 days | Deep understanding + coding |
| **Revision** | 7-10 days | Practice + speed improvement |
| **Mocks** | 3-5 days | Full interview simulation |
| **Total** | **24-35 days** | Complete preparation |

---

## 📝 Code Style (Har Solution Mein)

```java
// ✅ Problem: Array mein maximum element find karo
// ✅ Approach: Simple traversal - har element check karo
// ✅ Time: O(n), Space: O(1)

public static int findMax(int[] arr) {
    int max = arr[0]; // pehle element ko max maan lo
    for (int i = 1; i < arr.length; i++) { // baaki elements traverse karo
        if (arr[i] > max) { // agar current element bada hai max se
            max = arr[i]; // toh max update kar do
        }
    }
    return max; // final maximum return karo
}
```

**Har code mein milega:**
- ✅ Line-by-line Hinglish comments
- ✅ Multiple approaches (Brute Force → Optimal)
- ✅ Time & Space Complexity
- ✅ Dry Run examples
- ✅ Common mistakes & tips

---

## 💡 Tips for Success

1. **Consistency > Speed** — Roz 2-3 problems karo, ek din mein 20 mat karo
2. **Pattern seekho, problems nahi** — Patterns yaad karo, same pattern 10 jagah lagega
3. **Dry run karo** — Pen paper pe trace karo, code likhne se pehle
4. **Time complexity batao** — Interviewer ye zaroor puchega
5. **Edge cases socho** — Empty array, single element, negative numbers

---

## 🌟 All the best! Placement crack karo! 🚀

> *"DSA sikhne ka sabse acha tarika hai — ek problem solve karo, uska pattern samjho, aur phir 10 aur problems us pattern se solve karo."*

---
