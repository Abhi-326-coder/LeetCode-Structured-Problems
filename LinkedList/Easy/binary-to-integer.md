# Convert Binary Number in a Linked List to Integer

## Problem Link
https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/description/


## Difficulty
Easy

## Topic
LinkedList

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/70tx7KcMROc?si=TU895CfXqvtY8Fqo

## Approach
For every new bit:

- Shift the current result left by 1 (equivalent to multiplying by 2).

- Add the current node’s value using bitwise OR.


Time Complexity: O(n)

Space Complexity: O(1)

## Code

```java
class Solution {
    public int getDecimalValue(ListNode head) {
        int num = 0;
        while (head != null) {
            num = (num << 1) | head.val;
            head = head.next;
        }
        return num;
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