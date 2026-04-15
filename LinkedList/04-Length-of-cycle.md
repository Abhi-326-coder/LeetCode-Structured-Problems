# Length of cycle in Linked List

## Problem Link
https://www.geeksforgeeks.org/dsa/find-length-of-loop-in-linked-list/

## Difficulty
Easy

## Topic
LinkedList

## Platform
GFG Assingment Amazon Microsoft

## Video or Solution Link
https://youtu.be/70tx7KcMROc?si=TU895CfXqvtY8Fqo

## Approach
We have used the `Fast and Slow pointer method` in which fast node moves 2x time then the slow node which moves 1 times and if they meet fast = slow then it has the cycle

``fast = fast.next.next;``

``slow = slow.next;``

After ``slow == fast`` then run loop again once with slow to till they meet again


Time Complexity: O(n)

Space Complexity: O(1)

## Code

```java
public class Solution {
    public int hasCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while(fast != null && fast.next != null){
            fast = fast.next.next;
            slow = slow.next;
            if(fast == slow){
                ListNode temp = slow;
                int length = 0;
                do{
                    temp = temp.next;
                    length++;
                }while(temp != slow);
                return length;
            }
        }
        return 0;
    }
}
```

## Output Example

```java 
Input: head = [1,2,4,5], pos = 0
Output: 4
Explanation: There is a cycle in the linked list, where the tail connects to the 0th node.
```