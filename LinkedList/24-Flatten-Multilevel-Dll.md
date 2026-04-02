# Flatten a Multilevel Doubly Linked List

## Problem Link
https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/description/

## Difficulty
Medium

## Topic 
Stack | Linked List | Depth-First Search | Doubly-Linked List

## Platform
leetcode 

## Video or Solution Link
https://chatgpt.com/c/69ce9ff8-eb0c-8322-8def-a08131142296

## Optimal Approach I (didn't got answer)
🔥 Key Idea:(In-Place DFS)
If a node has a child:
Store next
Attach child to next
Flatten child
Connect tail of child to stored next

## Optimal Approach II
Idea (Linked List Approach)

Think like this:

Traverse the list normally
If a node has a child:
If next exists → push it to stack
Connect child as next
Remove child pointer
If you reach end and stack is not empty → attach stored nodes

| Complexity | Value            |
| ---------- | ---------------- |
| Time       | **O(n)**         |
| Space      | **O(n)** (stack) |

## Code

```java
// Optimal approach I
class Solution {
    public Node flatten(Node head) {
        dfs(head);
        return head;
    }

    // returns the tail of the flattened list
    public Node dfs(Node head) {
        Node curr = head;
        Node last = null;

        while (curr != null) {
            Node next = curr.next;

            // If child exists
            if (curr.child != null) {
                Node childHead = curr.child;
                Node childTail = dfs(childHead);

                // connect curr -> child
                curr.next = childHead;
                childHead.prev = curr;
                curr.child = null;

                // connect childTail -> next
                if (next != null) {
                    childTail.next = next;
                    next.prev = childTail;
                }

                last = childTail;
            } else {
                last = curr;
            }

            curr = next;
        }

        return last;
    }
}
```
```java

```java
// Stack Approach
class Solution {
    public Node flatten(Node head) {
        if (head == null) return head;

        Stack<Node> st = new Stack<>();
        Node curr = head;

        while (curr != null) {

            // If child exists
            if (curr.child != null) {

                // If next exists, store it
                if (curr.next != null) {
                    st.push(curr.next);
                }

                // Connect child as next
                curr.next = curr.child;
                curr.child.prev = curr;
                curr.child = null;
            }

            // If next is null and stack has nodes
            if (curr.next == null && !st.isEmpty()) {
                Node temp = st.pop();
                curr.next = temp;
                temp.prev = curr;
            }

            curr = curr.next;
        }

        return head;
    }
}
```

## Output Example

```java 
Input: head = [1,2,3,4,5,6,null,null,null,7,8,9,10,null,null,11,12]
Output: [1,2,3,7,8,11,12,9,10,4,5,6]
Explanation: The multilevel linked list in the input is shown.
After flattening the multilevel linked list it 
```