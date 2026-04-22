# Minimum Add to Make Parentheses Valid

## Problem Link
https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/description/

## Difficulty
Medium

## Topic
Staff | String | Stack | Greedy | Biweekly Contest 32

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/S9LUYztYLu4?si=c2UetgagW9NA0BML

## Approach
- Take a stack and push if ch == '(' or else pop it 
- return size as that many right parentheses required to balance those bracket left in stack

Time O(n)
Space O(n)

## Code

```java
class Solution {
    public int minAddToMakeValid(String s) {
        Stack<Character> stack = new Stack<>();

        for(char ch : s.toCharArray()){
            if( ch == ')'){
                if(!stack.isEmpty() && stack.peek() == '('){
                    stack.pop();
                }else{
                    stack.push(ch);
                }
            }else{
                stack.push(ch);
            }
        }
        return stack.size();
    }
}
```

```java
// Example 1:

Input: s = "())"
Output: 1

// Example 2:

Input: s = "((("
Output: 3
```
