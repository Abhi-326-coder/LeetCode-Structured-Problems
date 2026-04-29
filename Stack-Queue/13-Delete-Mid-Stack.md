# Delete Mid of a Stack

## Problem Link
https://www.geeksforgeeks.org/problems/delete-middle-element-of-a-stack/1

## Difficulty
Easy

## Topic
Stack | Recursion

## Platform
GFG

## Video or Solution Link
https://chatgpt.com/c/69f22c38-ab6c-83e8-85cf-7808a8d8f11a

## Approach 
Correct Approach (Using Auxiliary Stack)

Steps:

Pop elements until reaching the middle.
Skip (remove) the middle element.
Push everything back.

Time: O(n)
Space: O(n)


## Code

```java
import java.util.*;

class Solution {
    public void deleteMid(Stack<Integer> s) {
        int size = s.size();
        int mid = size / 2;   // 0-based index

        Stack<Integer> temp = new Stack<>();

        // Step 1: Move top elements to temp until mid
        for (int i = 0; i < mid; i++) {
            temp.push(s.pop());
        }

        // Step 2: Remove middle element
        s.pop();

        // Step 3: Push back remaining elements
        while (!temp.isEmpty()) {
            s.push(temp.pop());
        }
    }
}
```
```java
import java.util.*;

class Solution {

    public void deleteMid(Stack<Integer> s) {
        int size = s.size();
        delete(s, size, 0);
    }

    private void delete(Stack<Integer> s, int size, int current) {
        // Base case: reached middle
        if (current == size / 2) {
            s.pop();  // remove middle
            return;
        }

        int x = s.pop();

        // Recursive call
        delete(s, size, current + 1);

        // Push back after recursion
        s.push(x);
    }
}
```

```java
Input: s = [10, 20, 30, 40, 50]
Output: [50, 40, 20, 10]
Explanation: The bottom-most element will be 10 and the top-most element will be 50. Middle element will be element at index 3 from bottom, which is 30. Deleting 30, stack will look like {10 20 40 50}.

```
