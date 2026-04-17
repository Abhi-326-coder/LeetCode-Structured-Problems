# Implement Queue using Stacks

## Problem Link
https://leetcode.com/problems/implement-queue-using-stacks/description/

## Difficulty
Easy

## Topic
Stack | Design | Queue

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/S9LUYztYLu4?si=c2UetgagW9NA0BML

## Approach
Take two Stacks 
        ``first = new Stack<>();``
        ``second = new Stack<>();``
-Push is same in both Stacks and Queues
-Remove is different so first we add all the popped items from first to second and pop the item once to remove the required item and again add all the popped items from second to first

Time Complexity: O(n)

Space Complexity: O(1)

## Code

```java
class MyQueue {
    Stack<Integer> first ;
    Stack<Integer> second ;

    public MyQueue() {
        first = new Stack<>();
        second = new Stack<>();
    }
    
    public void push(int x) {
        first.push(x);
    }
    
    public int pop() {
        while(!first.isEmpty()){
            second.push(first.pop());
        }
        int removed = second.pop();
        while(!second.isEmpty()){
            first.push(second.pop());
        }
        return removed;
    }
    
    public int peek() {
        while(!first.isEmpty()){
            second.push(first.pop());
        }
        int peeked = second.peek();

        while(!second.isEmpty()){
            first.push(second.pop());
        }
        return peeked;
    }
    
    public boolean empty() {
        return first.isEmpty();
    }
}
```

## Output Example

```java 
Input
["MyQueue", "push", "push", "peek", "pop", "empty"]
[[], [1], [2], [], [], []]
Output
[null, null, null, 1, 1, false]
```