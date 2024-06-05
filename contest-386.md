## CONTEST-386

### Split the array -- Easy
You are given an integer array nums of even length. You have to split the array into two parts nums1 and nums2 such that:
</br>
- nums1.length == nums2.length == nums.length / 2.
- nums1 should contain distinct elements.
- nums2 should also contain distinct elements.

Return true if it is possible to split the array, and false otherwise.

Input: nums = [1,1,2,2,3,4]
</br>
Output: true
</br>
Explanation: One of the possible ways to split nums is nums1 = [1,2,3] and nums2 = [1,2,4].
</br>
Input: nums = [1,1,1,1]
</br>
Output: false
</br>
Explanation: The only possible way to split nums is nums1 = [1,1] and nums2 = [1,1]. Both nums1 and nums2 do not contain distinct elements.

```java
public class SplitPossible {

    public static boolean possibleToSplit(int[] nums) {
        HashMap<Integer, Integer> count = new HashMap<>(); // Store element frequencies
        for (int num : nums) {
            count.put(num, count.getOrDefault(num, 0) + 1);
        }
        // Check impossible cases
        for (int freq : count.values()) {
            if (freq > 2) {
                return false;
            }
        }
        if (count.size() < nums.length / 2) {
            return false;
        }

        return true;
    }
}
```
