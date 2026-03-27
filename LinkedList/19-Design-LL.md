#  Design Linked List

## Problem Link
https://leetcode.com/problems/design-linked-list/description/

## Difficulty
Medium 


## Topic 
Linked List | Design

## Platform
LeetCode 

## Video or Solution Link
https://chatgpt.com/c/69c55dc7-246c-8320-80ce-8402ece9c555

## Approach 
The approach was to build a class which would perform all the operation using linked list (custom Linked list class)

Operation	Time Complexity
get	            O(n)
addAtHead	    O(1)
addAtTail	    O(n)
addAtIndex	    O(n)
deleteAtIndex	O(n)

Space Complexity: O(n)

## Code

```java
class MyLinkedList {

    class Node {
        int data;
        Node prev;
        Node next;

        Node(int val) {
            this.data = val;
        }
    }

    Node head;
    int size;

    public MyLinkedList() {
        head = null;
        size = 0;
    }

    public int get(int index) {
        if (index < 0 || index >= size) return -1;

        Node temp = head;
        for (int i = 0; i < index; i++) {
            temp = temp.next;
        }
        return temp.data;
    }

    public void addAtHead(int val) {
        Node newNode = new Node(val);

        if (head != null) {
            newNode.next = head;
            head.prev = newNode;
        }

        head = newNode;
        size++;
    }

    public void addAtTail(int val) {
        Node newNode = new Node(val);

        if (head == null) {
            head = newNode;
        } else {
            Node temp = head;
            while (temp.next != null) {
                temp = temp.next;
            }
            temp.next = newNode;
            newNode.prev = temp;
        }

        size++;
    }

    public void addAtIndex(int index, int val) {
        if (index < 0 || index > size) return;

        if (index == 0) {
            addAtHead(val);
            return;
        }

        Node temp = head;
        for (int i = 0; i < index - 1; i++) {
            temp = temp.next;
        }

        Node newNode = new Node(val);
        newNode.next = temp.next;
        newNode.prev = temp;

        if (temp.next != null) {
            temp.next.prev = newNode;
        }

        temp.next = newNode;
        size++;
    }

    public void deleteAtIndex(int index) {
        if (index < 0 || index >= size) return;

        if (index == 0) {
            head = head.next;
            if (head != null) head.prev = null;
        } else {
            Node temp = head;
            for (int i = 0; i < index - 1; i++) {
                temp = temp.next;
            }

            Node toDelete = temp.next;
            temp.next = toDelete.next;

            if (toDelete.next != null) {
                toDelete.next.prev = temp;
            }
        }

        size--;
    }
}
```

## Output Example

```java 
Input
["MyLinkedList", "addAtHead", "addAtTail", "addAtIndex", "get", "deleteAtIndex", "get"]
[[], [1], [3], [1, 2], [1], [1], [1]]
Output
[null, null, null, null, 2, null, 3]
```