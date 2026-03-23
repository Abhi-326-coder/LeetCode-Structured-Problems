# Intersection of Two Linked Lists

## Problem Link
https://leetcode.com/problems/intersection-of-two-linked-lists/description/

## Difficulty
Easy

## Topic
Hash Table | Linked List | Two Pointers

## Platform
LeetCode  

## Video or Solution Link
https://chatgpt.com/c/69c16d2e-9cc8-8320-a592-62a8a096a0f9

## Approach 1
My approach was to run a nested while by comparing each element of the headA to headB, but time complexity was not efficient

Time Complexity: O(m x n)

Space Complexity: O(1)

## Approach 2(Optimal solution)
here only one while loop is used and main part is:
- ``a = (a == null) ? headB : a.next;``
- ``b = (b == null) ? headA : b.next;``
when the a becomes null it will starts to point from headA to headB so both a and b will run lenA + lenB

Time Complexity: O(m + n)

Space Complexity: O(1)

## Code

```java
class Solution {
    // initial and my approach
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
    ListNode tempA = headA;

    while (tempA != null) {
        ListNode tempB = headB; // reset every time

        while (tempB != null) {
            if (tempA == tempB) {
                return tempA;
            }
            tempB = tempB.next;
        }
        tempA = tempA.next;
    }
    return null;
}
}
```
```java
class Solution {
    // Optimal solution 
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
    ListNode a = headA;
    ListNode b = headB;

    while (a != b) {
        a = (a == null) ? headB : a.next;
        b = (b == null) ? headA : b.next;
    }

    return a; // intersection node or null
    }
}
```

## Output Example

```java 
Input: intersectVal = 8, listA = [4,1,8,4,5], listB = [5,6,1,8,4,5], skipA = 2, skipB = 3
Output: Intersected at '8'

Input: intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
Output: No intersection
```