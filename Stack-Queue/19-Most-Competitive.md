# Find the Most Competitive Subsequence

## Problem Link
https://leetcode.com/problems/find-the-most-competitive-subsequence/description/

## Difficulty
Medium

## Topic
Stack | Array | Monotonic Stack

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/69fcb9fd-3e18-8324-b124-0ca26e868812

## Approach 1
| Element | Stack              |
| ------- | ------------------ |
| 3       | [3]                |
| 5       | [3,5]              |
| 2       | pop 5, pop 3 → [2] |
| 6       | [2,6]              |


Time Complexity = O(n)
Space Complexity = O(k)

## Code

```java
class Solution {
    public int[] mostCompetitive(int[] nums, int k) {
        Stack<Integer> stack = new Stack<>();
        int n = nums.length;

        for (int i = 0; i < n; i++) {

            // Remove bigger elements if we can still fill k elements later
            while (!stack.isEmpty() &&
                   stack.peek() > nums[i] &&
                   stack.size() - 1 + (n - i) >= k) {

                stack.pop();
            }

            // Add current element if stack size is less than k
            if (stack.size() < k) {
                stack.push(nums[i]);
            }
        }

        // Convert stack to array
        int[] result = new int[k];

        for (int i = k - 1; i >= 0; i--) {
            result[i] = stack.pop();
        }

        return result;
    }
}

```

```java 
Input: nums = [3,5,2,6], k = 2
Output: [2,6]
Explanation: Among the set of every possible subsequence: {[3,5], [3,2], [3,6], [5,2], [5,6], [2,6]}, [2,6] is the most competitive.
```


