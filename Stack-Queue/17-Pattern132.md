# 132 Pattern

## Problem Link
https://leetcode.com/problems/132-pattern/description/

## Difficulty
Medium

## Topic
Stack | Array | Simulation

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/69fa1f5d-2ac0-8321-ad1a-9719a4757125

## Approach 1
Think like this:

We try to fix:
nums[i] → smallest (1)
second → middle (2)
stack → largest (3)
Flow:
Move from right → left
Keep stack decreasing
When popping:
popped value becomes candidate for "2"

If we ever find:

nums[i] < second

→ we found 1 < 2 < 3 ✔

Time: O(n) 
Space: O(n) (stack)

## Code

```java

class Solution {
    public boolean find132pattern(int[] nums) {
        int n = nums.length;
        Stack<Integer> stack = new Stack<>();
        int second = Integer.MIN_VALUE; // this will act as "2"

        for (int i = n - 1; i >= 0; i--) {
            // If we find nums[i] < second → 132 pattern found
            if (nums[i] < second) {
                return true;
            }

            // Maintain decreasing stack
            while (!stack.isEmpty() && nums[i] > stack.peek()) {
                second = stack.pop(); // update "2"
            }

            stack.push(nums[i]);
        }

        return false;
    }
}
```

```java
Input: nums = [1,2,3,4]
Output: false
Explanation: There is no 132 pattern in the sequence.
 
```
