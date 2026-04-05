# Rotate List

## Problem Link
https://leetcode.com/problems/rotate-list/description/

## Difficulty
Medium

## Topic 
Linked List | Two pointer

## Platform
leetcode 

## Video or Solution Link
https://chatgpt.com/c/69d2a1be-1f98-8322-a851-f2d50c5643e1

## Optimal Approach
 Instead of rotating k times, we:

Find the length of list (n)
Reduce rotations: k = k % n
Convert list into a circular linked list
Break at the right position

Time Complexity: ✅ O(n)
Space Complexity: ✅ O(1)
## Code

```java
// Optimal approach I
class Solution {
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null || head.next == null || k == 0) {
            return head;
        }

        // Step 1: Find length
        ListNode temp = head;
        int length = 1;
        
        while (temp.next != null) {
            temp = temp.next;
            length++;
        }

        // Step 2: Make circular
        temp.next = head;

        // Step 3: Reduce k
        k = k % length;

        // Step 4: Find new tail
        int stepsToNewTail = length - k;
        ListNode newTail = temp;

        while (stepsToNewTail-- > 0) {
            newTail = newTail.next;
        }

        // Step 5: Break circle
        ListNode newHead = newTail.next;
        newTail.next = null;

        return newHead;
    }
}
```

## Output Example

```java 
Input: head = [1,2,3,4,5], k = 2
Output: [4,5,1,2,3]

Input: head = [0,1,2], k = 4
Output: [2,0,1]
```