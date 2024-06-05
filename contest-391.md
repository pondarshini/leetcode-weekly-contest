## CONTEST- 391

### HARSHAD NUMBER -- EASY

An integer divisible by the sum of its digits is said to be a Harshad number. You are given an integer x. 
Return the sum of the digits of x if x is a Harshad number, otherwise, return -1.
</br>
Example 1:
</br>
Input: x = 18
</br>
Output: 9
</br>
Explanation:
The sum of digits of x is 9. 18 is divisible by 9. So 18 is a Harshad number and the answer is 9.
</br>
Example 2:
</br>
Input: x = 23
</br>
Output: -1
</br>
Explanation:
The sum of digits of x is 5. 23 is not divisible by 5. So 23 is not a Harshad number and the answer is -1.
```java
class Solution {
    public int sumOfTheDigitsOfHarshadNumber(int x) {
        int original = x; 
        int sum = 0;
        while (x != 0) {
            int a = x % 10;
            sum += a;
            x = x / 10;
        }
        if (original % sum == 0) { 
            return sum;
        } else {
            return -1;
        }
        
    }
}
```

### COUNT ALTERNATING SUBARRAYS --MEDIUM

You are given a binary array nums. We call a subarray alternating if no two adjacent elements in the subarray have the same value.
Return the number of alternating subarrays in nums.
</br>
Example 1:
</br>
Input:`nums = [0,1,1,1]`
</br>
Output: 5
</br>
Explanation:
The following subarrays are alternating: [0], [1], [1], [1], and [0,1].

```java
class Solution {
    public long countAlternatingSubarrays(int[] nums) {
        long c=0;
        long a=0;
        for(int i=0;i<nums.length;i++){
            if(i>0 && nums[i]==nums[i-1]){
                a=i;
            }
            c+=(i-a+1);
        }
        return c;
        
    }
}
```
