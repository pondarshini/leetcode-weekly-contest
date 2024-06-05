## CONTEST-395

### Find the Integer Added to Array I --EASY

You are given two arrays of equal length, nums1 and nums2.
Each element in nums1 has been increased (or decreased in the case of negative) by an integer, represented by the variable x.
As a result, nums1 becomes equal to nums2. Two arrays are considered equal when they contain the same integers with the same frequencies.
Return the integer x.
</br>

Example 1:
</br>
Input:`nums1 = [2,6,4]` , `nums2 = [9,7,5]`
</br>
Output: 3
</br>
Explanation:
The integer added to each element of nums1 is 3.
</br>

Example 2:
</br>
Input: `nums1 = [10]`, `nums2 = [5]`
</br>
Output: -5
</br>
Explanation:
The integer added to each element of nums1 is -5.
</br>

Example 3:
</br>
Input:`nums1 = [1,1,1,1]`, `nums2 = [1,1,1,1]`
</br>
Output: 0
</br>
Explanation:
The integer added to each element of nums1 is 0.

```java
class Solution {
    public int addedInteger(int[] nums1, int[] nums2) {
        Arrays.sort(nums1);
        Arrays.sort(nums2);
        for(int i=0;i<nums2.length;i++){
            return (nums2[i]-nums1[i]);
        }
        return -1;
        
    }
}
```
