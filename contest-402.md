## CONTEST 402
## Count Pairs That Form a Complete Day 

Given an integer array hours representing times in hours, return an integer denoting the number of pairs i, j where i < j and hours[i] + hours[j] forms a complete day. 
</br>
A complete day is defined as a time duration that is an exact multiple of 24 hours.
</br>
For example, 1 day is 24 hours, 2 days is 48 hours, 3 days is 72 hours, and so on.
</br>

Input: `hours = [12,12,30,24,24]`
</br>
Output: 2
</br>
Explanation: The pairs of indices that form a complete day are (0, 1) and (3, 4)
</br>

### Brute force
``` java
class Solution {
    public int countCompleteDayPairs(int[] hours) {
        int c=0;
        for(int i=0;i<hours.length;i++){
            for(int j=0;j<hours.length;j++){
            int a = hours[i]+hours[j];
            if(a%24 == 0 && i<j){
                c++;
            }
        }
        }
        return c;
    }
}
```
### Optimal 
``` java
class Solution {
    public long countCompleteDayPairs(int[] hours) {
        int[] rem =new int[24];
        long p=0;
        for(int i:hours){
            int r=i%24;
            int c=(24-r)%24;
            p+=rem[c];
            rem[r]++;
        }
        return p;
        }
        
    }
```
