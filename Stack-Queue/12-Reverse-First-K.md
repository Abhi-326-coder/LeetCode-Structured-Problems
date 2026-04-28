# Reverse first K of a Queue

## Problem Link
https://www.geeksforgeeks.org/problems/reverse-first-k-elements-of-queue/1

## Difficulty
Easy

## Topic
Stack | String

## Platform
GFG

## Video or Solution Link
https://chatgpt.com/c/69f0dbb0-3710-83e8-9c86-5006db9e5db9

## Approach 
✅ Optimal Approach (Stack-based)
Remove first k elements from queue → push into stack
Pop from stack → add back to queue (this reverses order)
Move remaining (n - k) elements to back to maintain order

Time: O(n)
Space: O(n) (for output)


## Code

```java
import java.util.*;

class Solution {
    public Queue<Integer> reverseFirstK(Queue<Integer> q, int k) {
        
        if (k > q.size() || k <= 0) return q;

        Stack<Integer> stack = new Stack<>();

        // Step 1: Push first k elements into stack
        for (int i = 0; i < k; i++) {
            stack.push(q.poll());
        }

        // Step 2: Add back to queue (reversed)
        while (!stack.isEmpty()) {
            q.add(stack.pop());
        }

        // Step 3: Move remaining elements to back
        int remaining = q.size() - k;
        for (int i = 0; i < remaining; i++) {
            q.add(q.poll());
        }

        return q;
    }
}
```


```java
Input: q = [1, 2, 3, 4, 5], k = 3
Output: [3, 2, 1, 4, 5]
Explanation: After reversing the first 3 elements from the given queue the resultant queue will be 3 2 1 4 5

```
