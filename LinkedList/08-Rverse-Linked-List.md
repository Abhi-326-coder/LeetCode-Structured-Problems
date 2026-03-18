# Reverse Linked List

## Problem Link
https://leetcode.com/problems/reverse-linked-list/submissions/1950281836/

## Difficulty
Easy

## Topic
LinkedList

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/70tx7KcMROc?si=TU895CfXqvtY8Fqo

## Approach
Take three pointer ``pres == head``, ``prev == null`` and ``second == head.next``. Move them till ``pres == null``

Time Complexity: O(n)

Space Complexity: O(1)

## Code

```java
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode pres = head;

        while (pres != null) {
            ListNode second = pres.next; // store next node
            pres.next = prev;            // reverse link
            prev = pres;                 // move prev
            pres = second;               // move pres
        }

        return prev;
    }
}
```

## Output Example

```java 
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```