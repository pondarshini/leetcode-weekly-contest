## CONTEST-400

## Minimum number of chairs in waiting room  --EASY

You are given a string s. Simulate events at each second i:
-- If s[i] == 'E', a person enters the waiting room and takes one of the chairs in it.
-- If s[i] == 'L', a person leaves the waiting room, freeing up a chair.
</br>
Return the minimum number of chairs needed so that a chair is available for every person who enters the waiting room given that it is initially empty.
</br>

Example 1:
</br>
Input: s = "EEEEEEE"
</br>
Output: 7
</br>
Explanation:
After each second, a person enters the waiting room and no person leaves it. Therefore, a minimum of 7 chairs is needed.
</br>

Example 2:
</br>
Input: s = "ELELEEL"
</br>
Output: 2
</br>
Explanation:
</br>
Let's consider that there are 2 chairs in the waiting room. The table below shows the state of the waiting room at each second.
Second	Event	People in the Waiting Room	Available Chairs
</br>

| 0 | Enter	| 1 | 1 |
| 1	| Leave	| 0	| 2 |
| 2 | Enter	| 1 | 1 |
| 3 | Leave	| 0	| 2 |
| 4 | Enter | 1	| 1 |
| 5	| Enter	| 2	| 0 |
| 6	| Leave	| 1	| 1 |

| Month    | Savings |
| -------- | ------- |
| January  | $250    |
| February | $80     |
| March    | $420    |

Example 3:
</br>
Input: s = "ELEELEELLL"
</br>
Output: 3
</br>
Explanation:
</br>
Let's consider that there are 3 chairs in the waiting room. The table below shows the state of the waiting room at each second.
Second	Event	People in the Waiting Room	Available Chairs
</br>
0	Enter	1	2
1	Leave	0	3
2	Enter	1	2
3	Enter	2	1
4	Leave	1	2
5	Enter	2	1
6	Enter	3	0
7	Leave	2	1
8	Leave	1	2
9	Leave	0	3

```java
class Solution {
    public int minimumChairs(String s) {
        int c=0;
        int m=0;
        for(char ch:s.toCharArray()){
            if(ch=='E'){
                c++;
                if(c>m){
                    m=c;
                }
            }
            else if(ch=='L'){
                c--;
            }
        }
        return m;
        
    }
}
```
