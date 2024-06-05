## CONTEST-392

### Longest Strictly Increasing or Strictly Decreasing Subarray --EASY

You are given an array of integers nums. Return the length of the longest subarray of nums which is either strictly increasing or strictly decreasing.
</br>
Example 1:
</br>
Input:`nums = [1,4,3,3,2]`
</br>
Output: 2
</br>
Explanation:
</br>
The strictly increasing subarrays of nums are [1], [2], [3], [3], [4], and [1,4].
</br>
The strictly decreasing subarrays of nums are [1], [2], [3], [3], [4], [3,2], and [4,3].
</br>
Hence, we return 2.
</br>
Example 2:
</br>
Input:`nums = [3,3,3,3]`
</br>
Output: 1
</br>
Explanation:
</br>
The strictly increasing subarrays of nums are [3], [3], [3], and [3].
</br>
The strictly decreasing subarrays of nums are [3], [3], [3], and [3].
</br>
Hence, we return 1.
</br>
Example 3:
</br>
Input:`nums = [3,2,1]`
</br>
Output: 3
</br>
Explanation:
</br>
The strictly increasing subarrays of nums are [3], [2], and [1].
</br>
The strictly decreasing subarrays of nums are [3], [2], [1], [3,2], [2,1], and [3,2,1].
</br>
Hence, we return 3.

```java
class Solution {
    public int longestMonotonicSubarray(int[] nums) {
          if (nums == null || nums.length == 0) {
            return 0;
        }
        
        int inclen = 1; 
        int declen = 1; 
        int longest = 1;
        
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > nums[i - 1]) {
                inclen++;
                declen = 1;
            } else if (nums[i] < nums[i - 1]) {
                declen++;
                inclen = 1;
            } else {
                inclen = 1;
                declen = 1;
            }
            
            longest = Math.max(longest, Math.max(inclen, declen));
        }
        
        return longest;
        
    }
}
```

Minimum Operations to Make Median of Array Equal to K --MEDIUM

You are given an integer array nums and a non-negative integer k. In one operation, you can increase or decrease any element by 1. 
Return the minimum number of operations needed to make the median of nums equal to k.

Example 1:
Input: nums = [2,5,6,8,5], k = 4
Output: 2
Explanation:
We can subtract one from nums[1] and nums[4] to obtain [2, 4, 6, 8, 4]. The median of the resulting array is equal to k.

Example 2:
Input: nums = [2,5,6,8,5], k = 7
Output: 3
Explanation:
We can add one to nums[1] twice and add one to nums[2] once to obtain [2, 7, 7, 8, 5].

Example 3:
Input: nums = [1,2,3,4,5,6], k = 4
Output: 0
Explanation:
The median of the array is already equal to k

class Solution {
    public long minOperationsToMakeMedianK(int[] nums, int k) {
        Arrays.sort(nums);
        int n = nums.length;
        int j = n / 2;
        long o = 0;
        if (nums[j] == k)
            return 0;
        if (nums[j] > k) {
            for (int i = j; i >= 0; i--) {
                if (nums[i] > k)
                    o += (nums[i] - k);
                else
                    break;
            }
        } 
        else {
            for (int i = j; i < n; i++) {
                if (nums[i] < k)
                    o += (k - nums[i]);
                else
                    break;
            }
        }
        
        return o;

        
    }
}
