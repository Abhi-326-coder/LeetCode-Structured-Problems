# Design a Stack With Increment Operation

## Problem Link
https://leetcode.com/problems/design-a-stack-with-increment-operation/

## Difficulty
Medium

## Topic
Stack | Array | Design

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/69f38885-3d3c-83e8-a280-4c95f69aae98

## Approach 1
Use:

stack[] → to store values
inc[] → to store lazy increments

💡 Key idea:
Instead of updating k elements immediately, store increment at index k-1 and apply later during pop.

Operation	Your Code	Optimized
push        O(1)	O(1)
pop	        O(1)	O(1)
increment	O(n)	O(1)



## Code

```java
class CustomStack {
    int[] stack;
    int[] inc;
    int top;
    int maxSize;

    public CustomStack(int maxSize) {
        this.maxSize = maxSize;
        stack = new int[maxSize];
        inc = new int[maxSize];
        top = -1;
    }
    
    public void push(int x) {
        if (top + 1 < maxSize) {
            top++;
            stack[top] = x;
        }
    }
    
    public int pop() {
        if (top == -1) return -1;
        
        int res = stack[top] + inc[top];
        
        if (top > 0) {
            inc[top - 1] += inc[top];
        }
        
        inc[top] = 0;
        top--;
        
        return res;
    }
    
    public void increment(int k, int val) {
        int idx = Math.min(k - 1, top);
        if (idx >= 0) {
            inc[idx] += val;
        }
    }
}
```

```java
Input
["CustomStack","push","push","pop","push","push","push","increment","increment","pop","pop","pop","pop"]
[[3],[1],[2],[],[2],[3],[4],[5,100],[2,100],[],[],[],[]]
Output
[null,null,null,2,null,null,null,null,null,103,202,201,-1]
```
