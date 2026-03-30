#  Swapping Nodes in a Linked List

## Problem Link
https://leetcode.com/problems/swapping-nodes-in-a-linked-list/description/

## Difficulty
Medium 

## Topic 
Linked List | Two pointer | Weekly Contest 223 | fast and Slow pointer method

## Platform
LeetCode 

## Video or Solution Link
https://chatgpt.com/c/69cab304-4380-8324-93e0-6bbba4847c4a

## My Approach 
- A get function which will get me kth node from start and end
- A length function which will return me the length of the Linked list
- swapping the node1 and node2 or overwriting the values 

## Better approach
Move fast pointer to kth node → that's node1
Start slow from head
Move both until fast reaches end → slow becomes kth from end

| Approach         | Time                   | Space |
| ---------------- | ---------------------- | ----- |
| Your version     | O(n) (multiple passes) | O(1)  |
| Optimized (mine) | **O(n) single pass**   | O(1)  |


## Code

```java
class Solution {
    public ListNode swapNodes(ListNode head, int k) {
        int l = len(head);

        ListNode node1 = getKthNode(head, k);
        ListNode node2 = getKthNode(head, l - k + 1);

        // swap values directly
        int temp = node1.val;
        node1.val = node2.val;
        node2.val = temp;

        return head;
    }

    public int len(ListNode head){
        int count = 0;
        while(head != null){
            count++;
            head = head.next;
        }
        return count;
    }

    public ListNode getKthNode(ListNode head, int k) {
        int count = 1;
        while (head != null) {
            if (count == k) return head;
            head = head.next;
            count++;
        }
        return null;
    }
}
```
```java
// Optimal Solution
class Solution {
    public ListNode swapNodes(ListNode head, int k) {
        ListNode fast = head;
        ListNode slow = head;

        // Move fast to kth node
        for (int i = 1; i < k; i++) {
            fast = fast.next;
        }

        ListNode node1 = fast;

        // Move fast to end, slow will reach kth from end
        while (fast.next != null) {
            fast = fast.next;
            slow = slow.next;
        }

        ListNode node2 = slow;

        // swap values
        int temp = node1.val;
        node1.val = node2.val;
        node2.val = temp;

        return head;
    }
}
```

## Output Example

```java 
Input: head = [1,2,3,4,5], k = 2
Output: [1,4,3,2,5]

Input: head = [7,9,6,6,7,8,3,0,9,5], k = 5
Output: [7,9,6,6,8,7,3,0,9,5]

```