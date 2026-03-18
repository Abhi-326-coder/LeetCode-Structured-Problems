# Sort List

## Problem Link
https://leetcode.com/problems/sort-list/description/

## Difficulty
Medium

## Topic
LinkedList

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/70tx7KcMROc?si=TU895CfXqvtY8Fqo

## Approach
We have used the merge Sorting method having two main function merge function, Sortlist and get mid functions 

also second approach is the bubble sort method 

Time Complexity: O(n)

Space Complexity: O(1)

## Code

```java
// Merge Sort method approach
class Solution {
    public ListNode sortList(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }

        ListNode mid = getMid(head);
        ListNode left = sortList(head);
        ListNode right = sortList(mid);

        return merge(left, right);
    }

    ListNode merge(ListNode list1, ListNode list2) {
        ListNode dummyHead = new ListNode();
        ListNode tail = dummyHead;
        while (list1 != null && list2 != null) {
            if (list1.val < list2.val) {
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

    ListNode getMid(ListNode head) {
        ListNode midPrev = null;
        while (head != null && head.next != null) {
            midPrev = (midPrev == null) ? head : midPrev.next;
            head = head.next.next;
        }
        ListNode mid = midPrev.next;
        midPrev.next = null;
        return mid;
    }
}
```
```java
// Using the bubble sort Method
private void bubbleSort(int row ,int col){
    if(row == 0){
        return ;
    }
    if(col < row){
        Node first = get(col);
        Node second = get(col + 1);

        if(first.value > second.value){
            head = second;
            first.next = second.next;
            second.next = first;
        }else if(second == tail){
            Node prev = get(col - 1);
            prev.next = second;
            tail = first;
            first.next = null;
            second.next = tail;
        } else{
            Node prev = get(col - 1);
            prev.next = second;
            first.next = second.next;
            second.next = first;
        }
    bubbleSort(row, col + 1);
    }else{
        bubbleSort(row - 1,0);
    }
}
```

## Output Example

```java 
Input: head = [4,2,1,3]
Output: [1,2,3,4]
```