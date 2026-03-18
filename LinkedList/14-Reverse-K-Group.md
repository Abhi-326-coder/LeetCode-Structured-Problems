# Reverse Nodes in k-Group

## Problem Link
https://leetcode.com/problems/reverse-nodes-in-k-group/description/

## Difficulty
Hard

## Topic
LinkedList

## Platform
LeetCode | Google | Microsoft 

## Video or Solution Link
https://youtu.be/70tx7KcMROc?si=TU895CfXqvtY8Fqo

## Approach
Take three pointer ``pres == head``, ``prev == null`` and ``second == head.next``. Move them till ``pres == null``
- First part is to take the values of current and prev to point where we want to start the reversing the list which is left and run the Linked list till we reach right point

-Second part is reversing the list by taking the three pointer and like solved in problem ``Reverse Linked list `` and pointing the end to node before the left node.

Time Complexity: O(n)

Space Complexity: O(1)

## Code

```java
class Solution {
    public ListNode reverseKGroup(ListNode head, int k) {
        if (head == null) return null;

        ListNode tail = head;
        for (int i = 0; i < k; i++) {
            if (tail == null) return head;
            tail = tail.next;
        }

        ListNode newHead = reverse(head, tail);
        head.next = reverseKGroup(tail, k);
        return newHead;
    }

    private ListNode reverse(ListNode cur, ListNode end) {
        ListNode prev = null;
        while (cur != end) {
            ListNode next = cur.next;
            cur.next = prev;
            prev = cur;
            cur = next;
        }
        return prev;
    }
}
```

## Output Example

```java 
Input: head = [1,2,3,4,5], left = 2, right = 4
Output: [1,4,3,2,5]
```