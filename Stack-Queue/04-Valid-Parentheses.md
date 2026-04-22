# Valid Parentheses

## Problem Link
https://leetcode.com/problems/valid-parentheses/description/

## Difficulty
Easy

## Topic
Stack | String

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/S9LUYztYLu4?si=c2UetgagW9NA0BML

## Approach
- if got left bracket the push it and if right simply pop it

Time Complexity	  O(n)
Space Complexity  O(n)

## Code

```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();

        for(char ch : s.toCharArray()){
            if(ch == '(' || ch == '{' || ch == '['){
                stack.push(ch);
            }
            else{
                if(ch == ')'){
                    if(stack.isEmpty() || stack.pop() != '(' ){
                        return false;
                    }
                }
                if(ch == ']'){
                    if(stack.isEmpty() || stack.pop() != '[' ){
                        return false;
                    }
                }
                if(ch == '}'){
                    if(stack.isEmpty() || stack.pop() != '{' ){
                        return false;
                    }
                }
            }
        }
        return stack.isEmpty();
    }
}
```

```java
Input: s = "()"
Output: true

Input: s = "(]"
Output: false
```
