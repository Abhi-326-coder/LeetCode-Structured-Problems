#  Remove Duplicates from Sorted List II

## Problem Link
https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/description/

## Difficulty
Medium

## Topic 
Two pointers | Linked List


## Platform
leetcode 

## Video or Solution Link
https://chatgpt.com/c/69dd1492-5de0-83e8-8366-dd5550daffe3

## Optimal Approach (didn't got answer)
Create a dummy node pointing to head
If current node has duplicates:
Skip all nodes with that value
Else:
Move prev forward
Return dummy.next

## Code

```java
// Optimal approach I
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        // Dummy node
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        
        ListNode prev = dummy; // last node before duplicate sequence
        
        while (head != null) {
            // Detect duplicates
            if (head.next != null && head.val == head.next.val) {
                
                // Skip all nodes with same value
                while (head.next != null && head.val == head.next.val) {
                    head = head.next;
                }
                
                // Remove duplicates
                prev.next = head.next;
            } else {
                // Move prev only if no duplicate
                prev = prev.next;
            }
            
            // Move head
            head = head.next;
        }
        
        return dummy.next;
    }
}
```

## Output Example

```java 
Input: head = [1,2,3,3,4,4,5]
Output: [1,2,5]

Input: head = [1,1,1,2,3]
Output: [2,3]

```