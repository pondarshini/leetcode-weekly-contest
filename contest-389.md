## CONTEST-389

### Existence of a Substring in a String and Its Reverse --EASY
Given a string s, find any substring of length 2 which is also present in the reverse of s.
Return true if such a substring exists, and false otherwise.
</br>
Example 1:
</br>
Input: s = "leetcode"
</br>
Output: true
</br>
Explanation: Substring "ee" is of length 2 which is also present in reverse(s) == "edocteel".
</br>
Example 2:
</br>
Input: s = "abcba"
</br>
Output: true
</br>
Explanation: All of the substrings of length 2 "ab", "bc", "cb", "ba" are also present in reverse(s) == "abcba".
</br> 
```java
class Solution {
    public boolean isSubstringPresent(String s) {
         for (int i = 0; i < s.length() - 1; i++) {
            String substr = s.substring(i, i + 2);
            if (s.contains(new StringBuilder(substr).reverse().toString())) {
                return true;
            }
        }
        return false;
        
    }
}
```
---

### Count Substrings Starting and Ending with Given Character  --MEDIUM
You are given a string s and a character c. Return the total number of substrings of s that start and end with c.
</br>
Example 1:
</br>
Input: s = "abada", c = "a"
</br>
Output: 6
</br>
Explanation: Substrings starting and ending with "a" are: "abada", "abada", "abada", "abada", "abada", "abada".
</br>
Example 2:
</br>
Input: s = "zzz", c = "z"
</br>
Output: 6
</br>
Explanation: There are a total of 6 substrings in s and all start and end with "z".

#### BRUTE FORCE SOLUTION
```java
public class Solution {
    public int countSubstrings(String s, char c) {
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == c) {
                for (int j = i; j < s.length(); j++) {
                    if (s.charAt(j) == c) {
                        count++;
                    }
                }
            }
        }
        return count;
    }
}
```

#### OPTIMAL SOLUTION
```java
class Solution {
    public long countSubstrings(String s, char c) {
        long count = 0;
        long a = 0; 
        for (char ch : s.toCharArray()) {
            if (ch == c) {
                a++;
            }
        }
        for(int i=1;i<=a;i++) count+=i;
        
        return count;
        
    }
}
```
