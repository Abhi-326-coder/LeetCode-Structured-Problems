# Add Two Numbers

## Problem Link
https://leetcode.com/problems/add-two-numbers/description/

## Difficulty
Medium

## Topic 
Principal | Linked List | Math | Recursion

## Platform
leetcode | TCS | Amazon | Microsoft | Facebook | Qualcomm 

## Video or Solution Link
https://chatgpt.com/c/69cbf6f0-883c-8323-b143-8281964b61bf

## My Approach 
-Reverse lists
-Convert to number
-Add
-Convert back
almost reached the ans part but my output was {0,1,2,3} and original ans was {1,2,3} and my approach is risky for large inputs

## Optimal approach
We simulate how addition works manually taking sum and carry:

  342
+ 465
------
  807

Time Complexity: O(n)

Space Complexity: O(1) excluding output

## Code

```java
// Optimal approach
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode temp = dummy;

        int carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            int sum = carry;

            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }

            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }

            carry = sum / 10;

            temp.next = new ListNode(sum % 10);
            temp = temp.next;
        }

        return dummy.next;
    }
}
```

## Output Example

```java 
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.

Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
```