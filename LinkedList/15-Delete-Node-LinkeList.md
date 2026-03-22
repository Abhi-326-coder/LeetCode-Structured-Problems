# Delete Node in a Linked List

## Problem Link
https://leetcode.com/problems/delete-node-in-a-linked-list/description/

## Difficulty
Medium

## Topic
LinkedList

## Platform
LeetCode | Google | Microsoft 

## Video or Solution Link
https://youtu.be/70tx7KcMROc?si=TU895CfXqvtY8Fqo

## Approach
Instead of deleting the node…

👉 Copy next node’s data into current node
👉 Then delete the next node

Time Complexity: O(1)

Space Complexity: O(1)

## Code

```java
class Solution {

    public void deleteNode(ListNode node) {
        node.val = node.next.val;
        node.next = node.next.next;
    }
}
```

## Output Example

```java 
Input: head = [4,5,1,9], node = 5
Output: [4,1,9]
Explanation: You are given the second node with value 5, the linked list should become 4 -> 1 -> 9 after calling your function.
```