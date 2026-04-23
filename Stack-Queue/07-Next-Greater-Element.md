# Next Greater Element I

## Problem Link
https://leetcode.com/problems/next-greater-element-i/description/

## Difficulty
Easy

## Topic
Mid Level | Array | Hash Table | Stack | Monotonic Stack

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/69ea5a4c-2254-83e8-9825-4aa72fe5ab6f

## Approach
-We solve it in O(n + m) using:

-Traverse nums2
-Use a stack to find next greater elements
-Store results in a map
-Answer queries for nums1

Time O(n + m)
Space O(m)

## Code

```java


class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        Map<Integer, Integer> map = new HashMap<>();
        Stack<Integer> stack = new Stack<>();

        // Build next greater for nums2
        for (int num : nums2) {
            while (!stack.isEmpty() && stack.peek() < num) {
                map.put(stack.pop(), num);
            }
            stack.push(num);
        }

        // Elements left → no next greater
        while (!stack.isEmpty()) {
            map.put(stack.pop(), -1);
        }

        // Build result for nums1
        int[] result = new int[nums1.length];
        for (int i = 0; i < nums1.length; i++) {
            result[i] = map.get(nums1[i]);
        }

        return result;
    }
}
```

```java
Input: nums1 = [4,1,2], nums2 = [1,3,4,2]
Output: [-1,3,-1]
Explanation: The next greater element for each value of nums1 is as follows:
- 4 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.
- 1 is underlined in nums2 = [1,3,4,2]. The next greater element is 3.
- 2 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.
```
