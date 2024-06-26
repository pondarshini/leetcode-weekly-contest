## CONTEST-399

## Find the Number of Good Pairs I    -- EASY

You are given 2 integer arrays nums1 and nums2 of lengths n and m respectively. You are also given a positive integer k.
A pair (i, j) is called good if nums1[i] is divisible by nums2[j] * k (0 <= i <= n - 1, 0 <= j <= m - 1).
Return the total number of good pairs.
</br>
Example 1:
</br>
Input: `nums1 = [1,3,4]`, `nums2 = [1,3,4]`, k = 1
</br>
Output: 5
</br>
Explanation:
The 5 good pairs are (0, 0), (1, 0), (1, 1), (2, 0), and (2, 2).
</br>

Example 2:
</br>
Input: `nums1 = [1,2,4,12]` , `nums2 = [2,4]` , k = 3
</br>
Output: 2
</br>
Explanation:
The 2 good pairs are (3, 0) and (3, 1)

```java
class Solution {
    public int numberOfPairs(int[] nums1, int[] nums2, int k) {
        int c=0;
        for(int i=0;i<nums1.length;i++){
            for(int j=0;j<nums2.length;j++){
                int a=nums2[j]*k;
                if(nums1[i]%a==0){
                    c++;
                }
            }
        }
        return c;
        
    }
}
```
---

### String compression III  --MEDIUM

Given a string word, compress it using the following algorithm:
Begin with an empty string comp. While word is not empty, use the following operation:
<ul>
</br>
<li>Remove a maximum length prefix of <code>word</code> made of a <em>single character</em> <code>c</code> repeating <strong>at most</strong> 9 times.</li>
</br>
<li>Append the length of the prefix followed by <code>c</code> to <code>comp</code>.</li>
</ul>
</li>
Return the string comp.
</br>

Example 1:
</br>
Input: word = "abcde"
</br>
Output: "1a1b1c1d1e"
</br>
Explanation:
Initially, comp = "". Apply the operation 5 times, choosing "a", "b", "c", "d", and "e" as the prefix in each operation.
For each prefix, append "1" followed by the character to comp.
</br>

Example 2:
</br>
Input: word = "aaaaaaaaaaaaaabb"
</br>
Output: "9a5a2b"
</br>
Explanation:
</br>
Initially, comp = "". Apply the operation 3 times, choosing "aaaaaaaaa", "aaaaa", and "bb" as the prefix in each operation.
</br>
For prefix "aaaaaaaaa", append "9" followed by "a" to comp.
</br>
For prefix "aaaaa", append "5" followed by "a" to comp.
</br>
For prefix "bb", append "2" followed by "b" to comp

```java
class Solution {
    public String compressedString(String word) {
         if (word == null || word.isEmpty()) {
            return "";
        }
        StringBuilder xyz = new StringBuilder(word.length());
        int i = 0;
        while (i < word.length()) {
            char abc = word.charAt(i);
            int c = 0;
            while (i < word.length() && word.charAt(i) == abc && c< 9) {
                i++;
                c++;
            }
            
            xyz.append(c).append(abc);
        }
      
        return xyz.toString();

        
    }
}
```
