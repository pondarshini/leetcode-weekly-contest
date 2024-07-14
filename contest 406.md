## CONTEST-406

### Lexicographically Smallest String After a Swap --EASY
Given a string s containing only digits, return the  lexicographically smallest string that can be obtained after swapping adjacent digits in s with the same parity at most once. Digits have the same parity if both are odd or both are even. For example, 5 and 9, as well as 2 and 4, have the same parity, while 6 and 9 do not.
</br>
Example 1:
</br>
Input: s =  s = "45320"
</br>
Output: "43520"
</br>
Explanation: `s[1] == '5'` and `s[2] == '3'` both have the same parity, and swapping them results in the lexicographically smallest string.
</br>
Example 2:
</br>
Input: s = "001"
</br>
Output: "001"
</br>
There is no need to perform a swap because s is already the lexicographically smallest.
</br> 
```java
class Solution {
    public String getSmallestString(String s) {
        char[] arr = s.toCharArray();
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            if ((arr[i] - '0') % 2 == (arr[i + 1] - '0') % 2 && arr[i] > arr[i + 1]) {
                char temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
                break;
            }
        }

        return new String(arr);
        
    }
}
```
---

### Delete Nodes from linked list from array  --MEDIUM
You are given an array of integers nums and the head of a linked list. Return the head of the modified linked list after removing all nodes from the linked list that have a value that exists in nums.
</br>
Example 1:
</br>
Input: nums = [1,2,3], head = [1,2,3,4,5]
</br>
Output: [4,5]
</br>
Example 2:
</br>
Input: nums = [1], head = [1,2,1,2,1,2]
</br>
Output: [2,2,2]

```java
class Solution {
    public ListNode modifiedList(int[] nums, ListNode head) {
        Set<Integer> list = new HashSet<>();
        for(int i:nums){
            list.add(i);
        }
        ListNode dummy=new ListNode(0);
        dummy.next = head;
        ListNode curr =dummy;
        while(curr.next!=null){
            if(list.contains(curr.next.val)){
                curr.next=curr.next.next;
            }
            else{
                curr=curr.next;
            }
        }
    return dummy.next;
    }
}
```
