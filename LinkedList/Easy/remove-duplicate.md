# Remove Duplicates from Sorted List

## Problem Link
https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/

## Difficulty
Easy

## Topic
LinkedList

## Platform
LeetCode

## Approach
Run the Loop and check if the, node.value == next node value if not then point the node to next.next node

Time Complexity: O(n)

Space Complexity: O(1)

## Code

```java
class Solution {
    public ListNode deleteDuplicates(ListNode node) {
        if(node == null){
            return node;
        }
        ListNode head = node;
        while(node.next != null){
            if(node.val == node.next.val){
                node.next = node.next.next ;
            }else{
                node = node.next;
            }
        }
        return head;
    }
}
```

## Output Example

```java 
Input: head = [1,1,2]
Output: [1,2]
```