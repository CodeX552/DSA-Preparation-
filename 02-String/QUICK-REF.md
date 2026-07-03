# 📝 String — Quick Reference (Cheat Sheet)

## ⚡ Interview Se 10 Min Pehle Ye Padho!

---

## 🔑 Key Methods

```java
s.length()                    // length
s.charAt(i)                   // character at index
s.substring(start, end)       // exclusive end
s.indexOf("abc")              // first occurrence, -1 if not found
s.contains("abc")             // boolean check
s.equals(other)               // content compare (NEVER use ==)
s.compareTo(other)            // lexicographic compare
s.toCharArray()               // String → char[]
String.valueOf(charArr)       // char[] → String
s.split("\\s+")               // split by regex
s.trim()                      // remove leading/trailing spaces
Character.isLetterOrDigit(c)  // alphanumeric check
Character.toLowerCase(c)      // lowercase convert
```

---

## 🔑 Key Patterns

| Pattern | Kab Use Karo | Template |
|---------|-------------|----------|
| **Two Pointer** | Palindrome, reverse | `left=0, right=n-1` |
| **Sliding Window** | Substring with condition | `set + left/right pointers` |
| **Frequency Count** | Anagram, unique chars | `int[26]` ya `HashMap` |
| **Expand Center** | Palindromic substring | `expand(s, i, i)` + `expand(s, i, i+1)` |
| **StringBuilder** | String building in loop | `sb.append()` |

---

## 📝 Templates

### Palindrome Check
```java
int l = 0, r = s.length() - 1;
while (l < r) {
    if (s.charAt(l++) != s.charAt(r--)) return false;
}
return true;
```

### Anagram Check
```java
int[] count = new int[26];
for (char c : s.toCharArray()) count[c - 'a']++;
for (char c : t.toCharArray()) count[c - 'a']--;
for (int c : count) if (c != 0) return false;
return true;
```

### Sliding Window (Variable)
```java
Set<Character> set = new HashSet<>();
int left = 0, maxLen = 0;
for (int right = 0; right < n; right++) {
    while (set.contains(s.charAt(right)))
        set.remove(s.charAt(left++));
    set.add(s.charAt(right));
    maxLen = Math.max(maxLen, right - left + 1);
}
```

---

## ⚠️ Common Mistakes

| Mistake | Correct Way |
|---------|-------------|
| `s1 == s2` | `s1.equals(s2)` |
| Loop mein `s += ...` | `StringBuilder` use karo |
| `s.length` | `s.length()` — parentheses lagao! |
| Modifying String | Strings immutable hain, nayi String banti hai |

---

## 🧠 Character Math

```java
'a' - 'a' = 0    // character to index
'z' - 'a' = 25
'A' - 'A' = 0
'0' - '0' = 0    // digit character to int
(char)('a' + 5) = 'f'  // index to character
```

---
