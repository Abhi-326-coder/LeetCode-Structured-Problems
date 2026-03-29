#  Remove Nth Node From End of List

## Problem Link
https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/

## Difficulty
Medium 

## Topic 
Linked List | Two pointer

## Platform
LeetCode | HSBC

## Video or Solution Link
https://chatgpt.com/c/69c960c0-acf8-8320-aa29-72ffd8976a40

## Approach 
List: 1 → 2 → 3 → 4 → 5
n = 2

length = 5
position = 5 - 2 + 1 = 4

Remove 4th node → value = 4

| Approach     | Time  | Space |
| ------------ | ----- | ----- |
| Your (fixed) | O(2N) | O(1)  |
| Optimal      | O(N)  | O(1)  |


Space Complexity: O(1)

## Code

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        int length = len(head);
        int pos = length - n + 1;

        // If we need to remove the head
        if (pos == 1) {
            return head.next;
        }

        return deleteNodeFromStart(head, pos);
    }

    public int len(ListNode head){
        int count = 0;
        ListNode temp = head;

        while(temp != null){
            count++;
            temp = temp.next;
        }
        return count;
    }

    public ListNode deleteNodeFromStart(ListNode head, int n){
        ListNode present = head;
        ListNode previous = null;

        while(n > 0){
            previous = present;
            present = present.next;
            n--;
        }

        // delete node
        previous.next = present.next;

        return head;
    }
}
```
```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode fast = head;
        ListNode slow = head;

        // Move fast pointer n steps ahead
        for(int i = 0; i < n; i++){
            fast = fast.next;
        }

        // If removing head
        if(fast == null){
            return head.next;
        }

        // Move both pointers
        while(fast.next != null){
            fast = fast.next;
            slow = slow.next;
        }

        // Delete node
        slow.next = slow.next.next;

        return head;
    }
}
```

## Output Example

```java 
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
Input: head = [1], n = 1
Output: []
```