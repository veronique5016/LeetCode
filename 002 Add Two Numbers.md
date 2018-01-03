# Add Two Numbers
You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order** and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.
You may assume the two numbers do not contain any leading zero, except the number 0 itself.

## Example
> Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)

> Output: 7 -> 0 -> 8

> Explanation: 342 + 465 = 807.

## Hint
- There is no need to calculate the sum of two ListNode
## Solution
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode ret = new ListNode(0);
        ListNode cur = ret;
        int init = 0;
        while(l1 != null || l2 != null){
            int sum1 = (l1 != null)? l1.val : 0;
            int sum2 = (l2 != null)? l2.val : 0;
            int sum = init + sum1 + sum2;
            init = sum / 10;
            cur.next = new ListNode(sum % 10);
            cur = cur.next;
            if(l1 != null) 
                l1 = l1.next;
            if(l2 != null)
                l2 = l2.next;
        }
        if(init>0)
            cur.next = new ListNode(init);
        return ret.next;
    }
}
```
