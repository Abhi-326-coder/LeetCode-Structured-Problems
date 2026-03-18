# Reorder List

## Problem Link
https://leetcode.com/problems/reorder-list/

## Difficulty
Medium

## Topic
LinkedList | stack | two pointer | recursion

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/70tx7KcMROc?si=TU895CfXqvtY8Fqo

## Approach
We will find the middle node and reverse it and compare the values of head and mid node until either node equals to null we have used two three function
-``middleNode(ListNode head)`` which will get me the middle node 
-``reverseList(ListNode head)`` which will reverse the mid node or say the right part of the main node from the middle node
-``isPalindrome(ListNode head)`` which will return me the boolean values if given LL is palindrome or not

Time Complexity: O(n)

Space Complexity: O(1)

## Code

```java
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;

        while(fast!=null && fast.next!=null){
            fast = fast.next.next;
            slow = slow.next;
        }
        return slow;
    }
    public ListNode reverseList(ListNode head) {
        if(head == null){
            return head;
        }
        ListNode prev = null;
        ListNode present = head;
        ListNode next = present.next;

        while (present != null) { 
            present.next = prev;            // reverse link
            prev = present;                 // move prev
            present = next;    
                if(next != null){
                    next = next.next;
                }           // move pres
            }

            return prev;
        }
    public void reorderList(ListNode head) {
        if(head == null && head.next == null){
            return ;
        }
        ListNode mid = middleNode(head);
        ListNode hs = reverseList(mid);
        ListNode hf = head;

        while(hf != null && hs != null){
            ListNode temp = hf.next;
            hf.next = hs;
            hf = temp;

            temp = hs.next;
            hs.next = hf;
            hs = temp;
        }
        if(hf != null){
            hf.next = null;
        }
    }
}
```

## Output Example

```java 
Input: head = [1,2,3,4]
Output: [1,4,2,3]
Input: head = [1,2,3,4,5]
Output: [1,5,2,4,3]
```