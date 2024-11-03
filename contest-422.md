## CONTEST-422

### Check Balanced String --EASY
You are given a string num consisting of only digits. A string of digits is called balanced if the sum of the digits at even indices is equal to the sum of digits at odd indices.
</br>
Return true if num is balanced, otherwise return false.
Example 1:
</br>
Input: num = "1234"
</br>
Output: false
</br>
Explanation:
- The sum of digits at even indices is `1 + 3 == 4`, and the sum of digits at odd indices is `2 + 4 == 6`.
- Since 4 is not equal to 6, num is not balanced.
Example 2:
</br>
Input: num = "24123"
</br>
Output: true
</br>
Explanation:
- The sum of digits at even indices is `2 + 1 + 3 == 6`, and the sum of digits at odd indices is `4 + 2 == 6`.
- Since both are equal the num is balanced
</br>

```java
class Solution {
    public boolean isBalanced(String num) {
        int A1 = 0;
        int B1 = 0;
        for (int C1 = 0; C1 < num.length(); C1++) {
            int D1 = num.charAt(C1) - '0';

            if (C1 % 2 == 0) {
                A1 += D1;
            } else {
                B1 += D1;
            }
        }

        return A1 == B1;
        
    }
}
```
