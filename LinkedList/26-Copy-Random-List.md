#  Copy List with Random Pointer

## Problem Link
https://leetcode.com/problems/copy-list-with-random-pointer/description/

## Difficulty
Medium

## Topic 
Hash table | Linked List

## Platform
leetcode 

## Video or Solution Link
https://chatgpt.com/c/69d3f579-0978-8321-869e-350e9b1dc78a

## Optimal Approach I (didn't got answer)
-Insert copied nodes in between original nodes
-Assign random pointers
-Separate both lists

| Approach               | Time | Space |
| ---------------------- | ---- | ----- |
| Optimal (interweaving) | O(n) | O(1)  |
| HashMap                | O(n) | O(n)  |

## Code

```java
// Optimal approach I
class Solution {
    public Node copyRandomList(Node head) {
        if (head == null) return null;

        Node temp = head;

        // Step 1: Create new nodes in between
        while (temp != null) {
            Node next = temp.next;
            Node copy = new Node(temp.val);
            temp.next = copy;
            copy.next = next;
            temp = next;
        }

        // Step 2: Assign random pointers
        temp = head;
        while (temp != null) {
            if (temp.random != null) {
                temp.next.random = temp.random.next;
            }
            temp = temp.next.next;
        }

        // Step 3: Separate the lists
        temp = head;
        Node dummy = new Node(0);
        Node copyTail = dummy;

        while (temp != null) {
            Node copy = temp.next;
            temp.next = copy.next;

            copyTail.next = copy;
            copyTail = copy;

            temp = temp.next;
        }

        return dummy.next;
    }
}
```

```java
// hashmap Approach
class Solution {
    public Node copyRandomList(Node head) {
        if (head == null) return null;

        HashMap<Node, Node> map = new HashMap<>();

        Node temp = head;

        // Step 1: Create all nodes
        while (temp != null) {
            map.put(temp, new Node(temp.val));
            temp = temp.next;
        }

        // Step 2: Assign next & random
        temp = head;
        while (temp != null) {
            Node copy = map.get(temp);
            copy.next = map.get(temp.next);
            copy.random = map.get(temp.random);
            temp = temp.next;
        }

        return map.get(head);
    }
}
```

## Output Example

```java 
Input: head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
Output: [[7,null],[13,0],[11,4],[10,2],[1,0]]


```