# Middle of the Linkedlist

## Problem Link
https://leetcode.com/problems/middle-of-the-linked-list/description/

## Difficulty
Easy

## Topic
LinkedList | Two pointer 

## Platform
LeetCode and Google question

## Video or Solution Link
https://youtu.be/70tx7KcMROc?si=TU895CfXqvtY8Fqo

## Approach
The approach we have used if ``fast and slow pointer method`` and When fast reach at the end node or say tail then slow will be at the center or middle and return the middle

``fast = fast.next.next``

``slow = slow.next``


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
}
```

## Output Example

```java 
Input: head = [1,2,3,4,5]
Output: [3,4,5]
Explanation: The middle node of the list is node 3.
```