# Linked List Cycle

## Problem Link
https://leetcode.com/problems/linked-list-cycle/description/

## Difficulty
Easy

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


Time Complexity: O(n)

Space Complexity: O(1)

## Code

```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;
        while(fast != null && fast.next != null){
            fast = fast.next.next;
            slow = slow.next;
            if(fast == slow){
                return true;
            }
        }
        return false;
    }
}
```

## Output Example

```java 
Input: 
head = [1,0,1]
Output: 5
Explanation: (101) in base 2 = (5) in base 10
```