# Merge Two Sorted Lists

## Problem Link
https://leetcode.com/problems/merge-two-sorted-lists/description/


## Difficulty
Easy

## Topic
LinkedList

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/70tx7KcMROc?si=TU895CfXqvtY8Fqo

## Approach
Traverse one by one and which one is smaller add it to list, when any one of the list becomes empty, add the remaining elements of the list in ans list


Time Complexity: O(n+m)

Space Complexity: O(1)

## Code

```java
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummyHead = new ListNode();
        ListNode tail = dummyHead;
        while(list1 != null && list2 !=null){
            if(list1.val < list2.val){
                tail.next = list1;
                list1 = list1.next;
                tail = tail.next;
            } else {
                tail.next = list2;
                list2 = list2.next;
                tail = tail.next;
            }
        }
        tail.next = (list1 != null) ? list1 : list2;
        return dummyHead.next;
    }
}
```

## Output Example

```java 
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```