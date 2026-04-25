# Remove Outermost Parentheses

## Problem Link
https://leetcode.com/problems/remove-outermost-parentheses/description/

## Difficulty
Easy

## Topic
Stack | String

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/69ed0080-dee8-83e8-82ae-e6da56324616

## Approach 1
Instead of using a stack, just track the depth (balance):

( → increase depth
) → decrease depth
Only add parentheses when depth > 0 (after processing)

Time: O(n)
Space: O(n) (for output)

## Approach 2 (using Stack)
We simulate the process using a stack:

Push ( into stack
Pop when ) comes
Only add characters to result when stack is NOT empty after operation

👉 Why?
Because:

When stack becomes empty, it means we just closed a primitive outer layer, so we skip it.


## Code

```java
// Approach using Stringbuilder
class Solution {
    public String removeOuterParentheses(String s) {
        StringBuilder result = new StringBuilder();
        int depth = 0;

        for (char ch : s.toCharArray()) {
            if (ch == '(') {
                if (depth > 0) result.append(ch);
                depth++;
            } else {
                depth--;
                if (depth > 0) result.append(ch);
            }
        }

        return result.toString();
    }
}
```
```java
// Approach using stack
import java.util.Stack;

class Solution {
    public String removeOuterParentheses(String s) {
        Stack<Character> stack = new Stack<>();
        StringBuilder result = new StringBuilder();

        for (char ch : s.toCharArray()) {
            if (ch == '(') {
                if (!stack.isEmpty()) {
                    result.append(ch); // not outer
                }
                stack.push(ch);
            } else {
                stack.pop();
                if (!stack.isEmpty()) {
                    result.append(ch); // not outer
                }
            }
        }

        return result.toString();
    }
}

```

```java
Input: s = "(()())(())"
Output: "()()()"
Explanation: 
The input string is "(()())(())", with primitive decomposition "(()())" + "(())".
After removing outer parentheses of each part, this is "()()" + "()" = "()()()".
```
