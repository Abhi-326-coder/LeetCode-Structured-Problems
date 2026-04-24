# Min Stack

## Problem Link
https://leetcode.com/problems/next-greater-element-i/description/

## Difficulty
Medium

## Topic
Stack | Design

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/69ea5a4c-2254-83e8-9825-4aa72fe5ab6f

## Approach
Maintain:

Main stack → stores all values
Min stack → keeps track of minimums

## Idea
Push to minStack only when:
it's empty OR
new value ≤ current min
While popping:
if popped value == minStack.peek() → pop from minStack too

push() → O(1)
pop() → O(1)
top() → O(1)
getMin() → O(1)

## Code

```java
class MinStack {
    Stack<Integer> stack;
    Stack<Integer> minStack;

    public MinStack() {
        stack = new Stack<>();
        minStack = new Stack<>();
    }
    
    public void push(int val) {
        stack.push(val);
        
        if(minStack.isEmpty() || val <= minStack.peek()) {
            minStack.push(val);
        }
    }
    
    public void pop() {
        if(stack.peek().equals(minStack.peek())) {
            minStack.pop();
        }
        stack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
        return minStack.peek();
    }
}
```

```java
Input
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

Output
[null,null,null,null,-3,null,0,-2]

Explanation
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // return -3
minStack.pop();
minStack.top();    // return 0
minStack.getMin(); // return -2
```
