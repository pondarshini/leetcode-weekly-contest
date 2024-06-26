## CONTEST- 393

### Latest Time You Can Obtain After Replacing Characters --EASY

You are given a string s representing a 12-hour format time where some of the digits (possibly none) are replaced with a "?".
12-hour times are formatted as "HH:MM", where HH is between 00 and 11, and MM is between 00 and 59. The earliest 12-hour time is 00:00, and the latest is 11:59.
You have to replace all the "?" characters in s with digits such that the time we obtain by the resulting string is a valid 12-hour format time and is the latest possible.
Return the resulting string.
</br>

Example 1:
</br>
Input: s = "1?:?4"
</br>
Output: "11:54"
</br>
Explanation: The latest 12-hour format time we can achieve by replacing "?" characters is "11:54".
</br>

Example 2:
</br>
Input: s = "0?:5?"
</br>
Output: "09:59"
</br>
Explanation: The latest 12-hour format time we can achieve by replacing "?" characters is "09:59"
</br>

```java
class Solution {
    public String findLatestTime(String s) {
        char[] result = s.toCharArray();

        if (result[0] == '?') {
            if (result[1] == '?' || ('0' <= result[1] && result[1] <= '9')) {
                result[0] = (result[1] <= '1' || result[1] == '?') ? '1' : '0';
            }
        }

        if (result[1] == '?') {
            result[1] = (result[0] == '1') ? '1' : '9';
        }

        if (result[3] == '?') {
            result[3] = '5';
        }

        if (result[4] == '?') {
            result[4] = '9';
        }

        return new String(result);
        
    }
}
```

---

### Maximum Prime Difference   --MEDIUM
You are given an integer array nums.Return an integer that is the maximum distance between the indices of two (not necessarily different) prime numbers in nums.
</br>

Example 1:
</br>
Input:`nums = [4,2,9,5,3]`
</br>
Output: 3
</br>
Explanation: nums[1], nums[3], and nums[4] are prime. So the answer is |4 - 1| = 3.
</br>

Example 2:
</br>
Input: nums = [4,8,2,8]
</br>
Output: 0
</br>
Explanation: nums[2] is prime. Because there is just one prime number, the answer is |2 - 2| = 0.

```java
class Solution {
    public int maximumPrimeDifference(int[] nums) {
        int maxDistance = 0;
        int firstPrimeIndex = -1;
        
        for (int i = 0; i < nums.length; i++) {
            if (isPrime(nums[i])) {
                if (firstPrimeIndex != -1) {
                    maxDistance = Math.max(maxDistance, i - firstPrimeIndex);
                } else {
                    firstPrimeIndex = i;
                }
            }
        }
        
        return maxDistance;
    }
    private boolean isPrime(int num) {
        if (num <= 1) {
            return false;
        }
        for (int i = 2; i * i <= num; i++) {
            if (num % i == 0) {
                return false;
            }
        }
        return true;
        
    }
}
```
