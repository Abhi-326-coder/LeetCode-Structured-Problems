# Design Front Middle Back Queue

## Problem Link
https://leetcode.com/problems/design-front-middle-back-queue/description/

## Difficulty
Medium

## Topic
Stack | Queue | Design

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a020597-9f00-83e8-91f0-95b748ae9626

## Approach 1 (My Approach)
O(n) because you're moving all elements between:

queue → stack1 → stack2 → queue

So overall:

pushFront → O(n)
pushMiddle → O(n)
popMiddle → O(n)
popBack → O(n)

## Approach 2 (Optimal)
Using Dequeue

| Operation  | Complexity |
| ---------- | ---------- |
| pushFront  | O(1)       |
| pushMiddle | O(1)       |
| pushBack   | O(1)       |
| popFront   | O(1)       |
| popMiddle  | O(1)       |
| popBack    | O(1)       |


## Code

```java

// Optimal Approach
import java.util.*;

class FrontMiddleBackQueue {

    Deque<Integer> front;
    Deque<Integer> back;

    public FrontMiddleBackQueue() {
        front = new LinkedList<>();
        back = new LinkedList<>();
    }

    // Balance both halves
    private void balance() {

        // front can have only 1 extra element
        if (front.size() > back.size() + 1) {
            back.addFirst(front.removeLast());
        }

        // back should never have more elements
        else if (front.size() < back.size()) {
            front.addLast(back.removeFirst());
        }
    }

    public void pushFront(int val) {
        front.addFirst(val);
        balance();
    }

    public void pushMiddle(int val) {

        // if front has extra element
        // move one to back first
        if (front.size() > back.size()) {
            back.addFirst(front.removeLast());
        }

        front.addLast(val);
    }

    public void pushBack(int val) {
        back.addLast(val);
        balance();
    }

    public int popFront() {

        if (front.isEmpty() && back.isEmpty()) {
            return -1;
        }

        int val;

        if (!front.isEmpty()) {
            val = front.removeFirst();
        } else {
            val = back.removeFirst();
        }

        balance();

        return val;
    }

    public int popMiddle() {

        if (front.isEmpty() && back.isEmpty()) {
            return -1;
        }

        int val = front.removeLast();

        balance();

        return val;
    }

    public int popBack() {

        if (front.isEmpty() && back.isEmpty()) {
            return -1;
        }

        int val;

        if (!back.isEmpty()) {
            val = back.removeLast();
        } else {
            val = front.removeLast();
        }

        balance();

        return val;
    }
}
```

```java
// My approach have some issue

import java.util.*;

class FrontMiddleBackQueue {

    Stack<Integer> stack1;
    Stack<Integer> stack2;

    public FrontMiddleBackQueue() {
        stack1 = new Stack<>();
        stack2 = new Stack<>();
    }

    // Move all elements from stack1 -> stack2
    private void transfer(Stack<Integer> s1, Stack<Integer> s2) {
        while (!s1.isEmpty()) {
            s2.push(s1.pop());
        }
    }

    public void pushFront(int val) {

        // Reverse current order
        transfer(stack1, stack2);

        // Add at front
        stack1.push(val);

        // Restore elements
        transfer(stack2, stack1);
    }

    public void pushMiddle(int val) {

        int n = stack1.size();

        // Move top half to stack2
        for (int i = 0; i < n / 2; i++) {
            stack2.push(stack1.pop());
        }

        // Insert middle
        stack1.push(val);

        // Restore
        while (!stack2.isEmpty()) {
            stack1.push(stack2.pop());
        }
    }

    public void pushBack(int val) {
        stack1.push(val);
    }

    public int popFront() {

        if (stack1.isEmpty()) {
            return -1;
        }

        // Reverse
        transfer(stack1, stack2);

        int val = stack2.pop();

        // Restore
        transfer(stack2, stack1);

        return val;
    }

    public int popMiddle() {

        if (stack1.isEmpty()) {
            return -1;
        }

        int n = stack1.size();

        // Front-middle for even size
        int moves = n / 2;

        for (int i = 0; i < moves; i++) {
            stack2.push(stack1.pop());
        }

        int val = stack1.pop();

        while (!stack2.isEmpty()) {
            stack1.push(stack2.pop());
        }

        return val;
    }

    public int popBack() {

        if (stack1.isEmpty()) {
            return -1;
        }

        return stack1.pop();
    }
}
```


```java 
["FrontMiddleBackQueue", "pushFront", "pushBack", "pushMiddle", "pushMiddle", "popFront", "popMiddle", "popMiddle", "popBack", "popFront"]
[[], [1], [2], [3], [4], [], [], [], [], []]
Output:
[null, null, null, null, null, 1, 3, 4, 2, -1]
```


