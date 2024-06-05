## CONTEST-394

### Count the Number of Special Characters I --Easy

You are given a string word. A letter is called special if it appears both in lowercase and uppercase in word.
Return the number of special letters in word.
</br>
Example 1:
</br>
Input: word = "aaAbcBC"
</br>
Output: 3
</br>
Explanation:
The special characters in word are 'a', 'b', and 'c'.
</br>

Example 2:
</br>
Input: word = "abc"
</br>
Output: 0
</br>
Explanation:
No character in word appears in uppercase.
</br>

Example 3:
</br>
Input: word = "abBCab"
</br>
Output: 1
</br>
Explanation:
The only special character in word is 'b'
</br>
```java
class Solution:
    def numberOfSpecialChars(self, word: str) -> int:
        sp=set()
        for char in word:
            if char.lower() !=char.upper() and char.lower() in word and char.upper() in word:
                sp.add(char.lower())
        return len(sp)
```

---

### Count the Number of Special Characters II  --MEDIUM
You are given a string word. A letter c is called special if it appears both in lowercase and uppercase in word, and every lowercase occurrence of c appears 
before the first uppercase occurrence of c.
Return the number of special letters in word.
</br>
Example 1:
</br>
Input: word = "aaAbcBC"
</br>
Output: 3
</br>
Explanation:
The special characters are 'a', 'b', and 'c'.
</br>

Example 2:
</br>
Input: word = "abc"
</br>
Output: 0
</br>
Explanation:
There are no special characters in word.
</br>

Example 3:
</br>
Input: word = "AbBCab"
</br>
Output: 0
</br>
Explanation:
There are no special characters in word

```java
class Solution(object):
    def numberOfSpecialChars(self, word):
        d = dict()
        for i in range(len(word)):
            if word[i].islower():
                if word[i] in d:
                    d[word[i]].append(i)
                else:
                    d[word[i]] = [i]
        r = 0
        for j, k in d.items():
            if j.upper() in word:
                a = word.index(j.upper())
                if max(k) < a:
                    r += 1
        return r
```
