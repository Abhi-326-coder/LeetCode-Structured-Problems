# Add Two Numbers II

## Problem Link
https://leetcode.com/problems/add-two-numbers-ii/description/

## Difficulty
Medium

## Topic 
Stack | Linked List | Math | Recursion

## Platform
leetcode 

## Video or Solution Link
https://chatgpt.com/c/69cd45bd-4090-8321-a01f-d21944851e50

## My Approach 
-Reverse lists
-Convert to number
-Add
-Convert back
almost reached the ans part but my output was {0,1,2,3} and original ans was {1,2,3} and my approach is risky for large inputs

## Optimal approach
We simulate how addition works manually taking sum and carry:
- Reverse both lists
- Add like normal (LeetCode 2)
- Reverse the result
  342
+ 465
------
  807

Time Complexity: O(n + m)

Space Complexity: O(1) excluding output

## Code

```java
// Optimal approach
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        l1 = reverse(l1);
        l2 = reverse(l2);

        ListNode dummy = new ListNode(0);
        ListNode curr = dummy;

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

            curr.next = new ListNode(sum % 10);
            curr = curr.next;

            carry = sum / 10;
        }

        return reverse(dummy.next);
    }

    private ListNode reverse(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;

        while (curr != null) {
            ListNode next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }

        return prev;
    }
}
```
```java
// Recursion Approach
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int len1 = length(l1);
        int len2 = length(l2);

        if (len1 < len2) {
            ListNode temp = l1;
            l1 = l2;
            l2 = temp;
        }

        int diff = Math.abs(len1 - len2);

        Result res = helper(l1, l2, diff);

        if (res.carry != 0) {
            ListNode head = new ListNode(res.carry);
            head.next = res.node;
            return head;
        }

        return res.node;
    }

    class Result {
        ListNode node;
        int carry;
        Result(ListNode node, int carry) {
            this.node = node;
            this.carry = carry;
        }
    }

    private Result helper(ListNode l1, ListNode l2, int diff) {
        if (l1 == null) return new Result(null, 0);

        Result res;

        if (diff > 0) {
            res = helper(l1.next, l2, diff - 1);
            int sum = l1.val + res.carry;
            ListNode node = new ListNode(sum % 10);
            node.next = res.node;
            return new Result(node, sum / 10);
        } else {
            res = helper(l1.next, l2.next, 0);
            int sum = l1.val + l2.val + res.carry;
            ListNode node = new ListNode(sum % 10);
            node.next = res.node;
            return new Result(node, sum / 10);
        }
    }

    private int length(ListNode head) {
        int len = 0;
        while (head != null) {
            len++;
            head = head.next;
        }
        return len;
    }
}
```
```java
// Stack Approach
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        Stack<Integer> s1 = new Stack<>();
        Stack<Integer> s2 = new Stack<>();
        
        // Push values into stacks
        while (l1 != null) {
            s1.push(l1.val);
            l1 = l1.next;
        }
        
        while (l2 != null) {
            s2.push(l2.val);
            l2 = l2.next;
        }
        
        int carry = 0;
        ListNode head = null;
        
        // Add values
        while (!s1.isEmpty() || !s2.isEmpty() || carry != 0) {
            int sum = carry;
            
            if (!s1.isEmpty()) sum += s1.pop();
            if (!s2.isEmpty()) sum += s2.pop();
            
            // Create new node
            ListNode node = new ListNode(sum % 10);
            node.next = head;
            head = node;
            
            carry = sum / 10;
        }
        
        return head;
    }
}
```

## Output Example

```java 
Input: l1 = [7,2,4,3], l2 = [5,6,4]
Output: [7,8,0,7]

Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [8,0,7]
```