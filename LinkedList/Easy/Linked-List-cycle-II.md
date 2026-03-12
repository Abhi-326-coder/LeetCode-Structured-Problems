# Linked List Cycle II

## Problem Link
https://leetcode.com/problems/linked-list-cycle-ii/

## Difficulty
Medium

## Topic
LinkedList

## Platform
LeetCode 

## Video or Solution Link
https://youtu.be/70tx7KcMROc?si=TU895CfXqvtY8Fqo

## Approach
We have used the `Fast and Slow pointer method` in which fast node moves 2x time then the slow node which moves 1 times and if they meet fast = slow then it has the cycle

``fast = fast.next.next;``

``slow = slow.next;``

- Check if it has cycle and if it does then calculate the length of the cycle 

- take first(f) and second(s) node and move the second to length of the cycle times and then run a loop till second and first becomes equal and return either one 


Time Complexity: O(n)

Space Complexity: O(1)

## Code

```java
public class Solution {
    public int lengthCycle(ListNode head){
        ListNode fast = head;
        ListNode slow = head;

        // Checking if it is a cycle and length of cycle
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

    public ListNode detectCycle(ListNode head) {
        int length = 0;

        ListNode fast = head;
        ListNode slow = head;

        // Checking if it is a cycle and length of cycle
        while(fast != null && fast.next != null){
            fast = fast.next.next;
            slow = slow.next;

            if(fast == slow){
                length = lengthCycle(slow);
                break;
            }
        }
        if(length == 0) return null;

        // find the start node

        ListNode f = head;
        ListNode s = head;

        while(length > 0){
            s = s.next;
            length--;
        }
        while(s != f){
            s = s.next;
            f = f.next;
        }
        return s;
    }
}
```

## Output Example

```java 
Input: head = [1,2], pos = 0
Output: tail connects to node index 0
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```