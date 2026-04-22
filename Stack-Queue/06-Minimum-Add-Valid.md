# Minimum Insertions to Balance a Parentheses String

## Problem Link
https://leetcode.com/problems/minimum-insertions-to-balance-a-parentheses-string/description/

## Difficulty
Medium

## Topic
Staff | String | Stack | Greedy | Biweekly Contest 32

## Platform
LeetCode

## Video or Solution Link
- https://youtu.be/S9LUYztYLu4?si=c2UetgagW9NA0BML

- https://chatgpt.com/c/69e8fb28-db00-83e8-8760-57ce8ec1d5fb

## Approach
- res represents the number of left/right parentheses - already added.
- right represents the number of right parentheses needed.

Time O(N)
Space O(1)

## Code

```java
class Solution {
        public int minInsertions(String s) {
        int res = 0, right = 0;
        for (int i = 0; i < s.length(); ++i) {
            if (s.charAt(i) == '(') {
                if (right % 2 > 0) {
                    right--;
                    res++;
                }
                right += 2;
            } else {
                right--;
                if (right < 0) {
                    right += 2;
                    res++;
                }
            }
        }
        return right + res;
    }
}
```

```java
Input: s = "(()))"
Output: 1
Explanation: The second '(' has two matching '))', but the first '(' has only ')' matching. We need to add one more ')' at the end of the string to be "(())))" which is balanced.

Input: s = "())"
Output: 0
Explanation: The string is already balanced.
```
