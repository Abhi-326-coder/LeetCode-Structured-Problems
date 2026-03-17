# Reverse Linked List II

## Problem Link
https://leetcode.com/problems/reverse-linked-list-ii/description/

## Difficulty
Medium

## Topic
LinkedList

## Platform
LeetCode

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
    public ListNode reverseBetween(ListNode head, int left, int right) {
        if(left == right){
            return head;
        }
        ListNode current = head;
        ListNode prev = null;
        for(int i=0; current != null && i<left-1; i++){
            prev = current;
            current = current.next;
        }
        ListNode last = prev; 
        ListNode newEnd = current;
        
        ListNode next = current.next;
        for(int i=0; current !=null && i<right-left+1;i++){
            current.next = prev;
            prev = current;
            current = next;
            if(next != null){
                next = next.next;
            }
        }
        if(last != null){
            last.next = prev;
        }else{
            head = prev;
        }
        newEnd.next = current;
        return head;
        
    }
}
```

## Output Example

```java 
Input: head = [1,2,3,4,5], left = 2, right = 4
Output: [1,4,3,2,5]
```