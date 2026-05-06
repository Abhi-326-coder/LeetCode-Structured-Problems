# Design Circular Queue

## Problem Link
https://leetcode.com/problems/design-circular-queue/description/

## Difficulty
Medium

## Topic
Stack | Array | Design

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/69fb6444-180c-83e8-9006-4f44de0c8815

## Approach 1
``rear = (rear + 1) % size``

| Operation | Complexity |
| --------- | ---------- |
| enQueue   | O(1)       |
| deQueue   | O(1)       |
| Front     | O(1)       |
| Rear      | O(1)       | 

## Code

```java

class MyCircularQueue {

    int[] queue;
    int size;
    int front;
    int rear;
    int count;

    public MyCircularQueue(int k) {
        queue = new int[k];
        size = k;
        front = 0;
        rear = -1;
        count = 0;
    }

    public boolean enQueue(int value) {
        if (isFull()) {
            return false;
        }

        rear = (rear + 1) % size;
        queue[rear] = value;
        count++;

        return true;
    }

    public boolean deQueue() {
        if (isEmpty()) {
            return false;
        }

        front = (front + 1) % size;
        count--;

        return true;
    }

    public int Front() {
        if (isEmpty()) {
            return -1;
        }

        return queue[front];
    }

    public int Rear() {
        if (isEmpty()) {
            return -1;
        }

        return queue[rear];
    }

    public boolean isEmpty() {
        return count == 0;
    }

    public boolean isFull() {
        return count == size;
    }
}time
```


