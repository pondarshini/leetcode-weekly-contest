## CONTEST-397

## Permutation Difference between Two Strings  --Easy

You are given two strings s and t such that every character occurs at most once in s and t is a permutation of s.
The permutation difference between s and t is defined as the sum of the absolute difference between the index of the occurrence of
each character in s and the index of the occurrence of the same character in t.
Return the permutation difference between s and t.
</br>

Example 1:
</br>
Input: s = "abc", t = "bac"
</br>
Output: 2
</br>
Explanation:
</br>
For s = "abc" and t = "bac", the permutation difference of s and t is equal to the sum of:
</br>
The absolute difference between the index of the occurrence of "a" in s and the index of the occurrence of "a" in t.
</br>
The absolute difference between the index of the occurrence of "b" in s and the index of the occurrence of "b" in t.
</br>
The absolute difference between the index of the occurrence of "c" in s and the index of the occurrence of "c" in t.
</br>
That is, the permutation difference between s and t is equal to |0 - 1| + |2 - 2| + |1 - 0| = 2.
</br>

Example 2:
</br>
Input: s = "abcde", t = "edbac"
</br>
Output: 12
</br>
Explanation: The permutation difference between s and t is equal to |0 - 3| + |1 - 2| + |2 - 4| + |3 - 1| + |4 - 0| = 12.

```java
class Solution {
    public int findPermutationDifference(String s, String t) {
        Map<Character, Integer> indexMapS = new HashMap<>();
        Map<Character, Integer> indexMapT = new HashMap<>();
        for (int i = 0; i < s.length(); i++) {
            indexMapS.put(s.charAt(i), i);
            indexMapT.put(t.charAt(i), i);
        }

        int permutationDiff = 0;
        for (char c : s.toCharArray()) {
            permutationDiff += Math.abs(indexMapS.get(c) - indexMapT.get(c));
        }

        return permutationDiff;
        
    }
}
```
----

### Taking Maximum Energy From the Mystic Dungeon     --Medium

In a mystic dungeon, n magicians are standing in a line. Each magician has an attribute that gives you energy. 
Some magicians can give you negative energy, which means taking energy from you.
You have been cursed in such a way that after absorbing energy from magician i, you will be instantly 
transported to magician (i + k). This process will be repeated until you reach the magician where (i + k) does not exist.
In other words, you will choose a starting point and then teleport with k jumps until you reach the end of the magicians' sequence, 
absorbing all the energy during the journey.
You are given an array energy and an integer k. Return the maximum possible energy you can gain.
</br>

Example 1:
</br>
Input: `energy = [5,2,-10,-5,1]`, k = 3
</br>
Output: 3
</br>
Explanation: We can gain a total energy of 3 by starting from magician 1 absorbing 2 + 1 = 3.
</br>

Example 2:
</br>
Input: `energy = [-2,-3,-1]`, k = 2
</br>
Output: -1
</br>
Explanation: We can gain a total energy of -1 by starting from magician 2.

```java
class Solution {
    public int maximumEnergy(int[] energy, int k) {
        int n = energy.length;
        int maxEnergy = Integer.MIN_VALUE;

        for (int i = n - 1; i >= n - k; i--) {
            int currentSum = 0;
            for (int j = i; j >= 0; j -= k) {
                currentSum += energy[j];
                maxEnergy = Math.max(maxEnergy, currentSum);
            }
        }
        
        return maxEnergy;
    }
}
```
