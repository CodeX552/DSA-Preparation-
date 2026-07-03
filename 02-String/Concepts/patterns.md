# 📝 String Patterns — Deep Dive

## Pattern 1: Character Frequency
```java
// int[26] for lowercase only
int[] freq = new int[26];
for (char c : s.toCharArray()) freq[c - 'a']++;

// int[128] for all ASCII
int[] freq = new int[128];
for (char c : s.toCharArray()) freq[c]++;

// HashMap for Unicode
Map<Character, Integer> map = new HashMap<>();
for (char c : s.toCharArray())
    map.merge(c, 1, Integer::sum);
```

## Pattern 2: Expand Around Center (Palindromes)
```java
// Har index center maan ke expand karo
for (int i = 0; i < n; i++) {
    expand(s, i, i);     // odd length: "aba"
    expand(s, i, i + 1); // even length: "abba"
}

int expand(String s, int l, int r) {
    while (l >= 0 && r < s.length() && s.charAt(l) == s.charAt(r)) {
        l--; r++;
    }
    return r - l - 1;
}
```

## Pattern 3: Pattern Identification
| Problem Mein Ye Dikhe | Pattern |
|----------------------|---------|
| "Palindrome" | Two Pointer / Expand Center |
| "Anagram" | Frequency Count (int[26]) |
| "Substring with condition" | Sliding Window |
| "Build string" | StringBuilder |
| "Compare strings" | .equals(), int[26] |
| "Permutation of" | Same as Anagram |

---
