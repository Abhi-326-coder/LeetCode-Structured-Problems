# Remove All Adjacent Duplicates In String

## Problem Link
https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/description/

## Difficulty
Easy

## Topic
Stack | String

## Platform
LeetCode

## Video or Solution Link (Solved)
https://chatgpt.com/c/69ee3ebb-a8b8-83e8-bbc5-7e1c1330efcc

## Approach 
- You iterate through the string once → O(n)
- Each operation inside (push, pop, peek) is O(1)

Time: O(n**2)
Space: O(n) 


## Code

```java
class Solution {
    public String removeDuplicates(String s) {
        Stack<Character> stack = new Stack<>();
        String ans = "";
        for(char ch : s.toCharArray()){
            if( !stack.isEmpty() && stack.peek() == ch){
                stack.pop();
            }else{
                stack.push(ch);
            }
        }
        while(!stack.isEmpty()){
            ans = stack.pop() + ans;
        }
        
        return ans;
    }
}
```

```java
public String removeDuplicates(String s) {
    Stack<Character> stack = new Stack<>();
    
    for(char ch : s.toCharArray()){
        if(!stack.isEmpty() && stack.peek() == ch){
            stack.pop();
        } else {
            stack.push(ch);
        }
    }

    StringBuilder sb = new StringBuilder();
    while(!stack.isEmpty()){
        sb.append(stack.pop());
    }

    return sb.reverse().toString();
}
```


```java

Input: s = "abbaca"
Output: "ca"
Explanation: 
For example, in "abbaca" we could remove "bb" since the letters are adjacent and equal, and this is the only possible move.  The result of this move is that the string is "aaca", of which only "aa" is possible, so the final string is "ca".

```
