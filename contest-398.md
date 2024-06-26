## CONTEST-398

## SPECIAL ARRAY I     -- EASY

An array is considered special if every pair of its adjacent elements contains two numbers with different parity.
You are given an array of integers nums. Return true if nums is a special array, otherwise, return false.
</br>

Example 1:
</br>
Input: `nums = [1]`
</br>
Output: true
</br>
Explanation:
There is only one element. So the answer is true.
</br>

Example 2:
</br>
Input: `nums = [2,1,4]`
</br>
Output: true
</br>
Explanation:
There is only two pairs: (2,1) and (1,4), and both of them contain numbers with different parity. So the answer is true.
</br>

Example 3:
</br>
Input:`nums = [4,3,1,6]`
</br>
Output: false
</br>
Explanation:
nums[1] and nums[2] are both odd. So the answer is false.

```java
class Solution {
    public boolean isArraySpecial(int[] nums) {
        if (nums.length == 1) {
            return true;
        }
        
        for (int i = 0; i < nums.length - 1; i++) {
            if ((nums[i] % 2) == (nums[i + 1] % 2)) {
                return false;
            }
        }
        return true;
        
    }
}
```
---

### Sum of Digit Differences of All Pairs   --MEDIUM

You are given an array nums consisting of positive integers where all integers have the same number of digits.
The digit difference between two integers is the count of different digits that are in the same position in the two integers.
Return the sum of the digit differences between all pairs of integers in nums.
</br>
Example 1:
</br>
Input: `nums = [13,23,12]`
</br>
Output: 4
</br>
Explanation:
</br>
We have the following:
</br>
- The digit difference between 13 and 23 is 1.
- The digit difference between 13 and 12 is 1.
- The digit difference between 23 and 12 is 2.
  </br>
So the total sum of digit differences between all pairs of integers is 1 + 1 + 2 = 4.
</br>

Example 2:
</br>
Input:`nums = [10,10,10,10]`
</br>
Output: 0
</br>
Explanation:
All the integers in the array are the same. So the total sum of digit differences between all pairs of integers will be 0.

```java
class Solution {
    public long sumDigitDifferences(int[] nums) {
        int n = nums.length;
        int nd = String.valueOf(nums[0]).length();
        
        int[][] dc = new int[nd][10];
        for (int num : nums) {
            String ns = String.valueOf(num);
            for (int i = 0; i < nd; i++) {
                int d = ns.charAt(i) - '0';
                dc[i][d]++;
            }
        }
        
        long td = 0;
        for (int i = 0; i < nd; i++) {
            for (int digit1 = 0; digit1 < 10; digit1++) {
                for (int digit2 = 0; digit2 < 10; digit2++) {
                    if (digit1 != digit2) {
                        td += (long) dc[i][digit1] * dc[i][digit2];
                    }
                }
            }
        }
        td /= 2;
        
        return td;
        
    }
}
```
