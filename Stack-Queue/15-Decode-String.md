# Decode String

## Problem Link
https://leetcode.com/problems/decode-string/description/

## Difficulty
Medium

## Topic
Stack | Array | Recursion

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/69f62020-8e00-83e8-8ba6-3c81a5e61b66

## Approach 1
Use a stack to store:
previous strings
repeat counts
Traverse the string:
If digit → build number
If [ → push current state
If ] → pop & repeat
If char → append to current string

Time: O(n × k) (k = max repeat)
Space: O(n) (stack usage)

## Code

```java
class Solution {
    public String decodeString(String s) {
        Stack<Integer> countStack = new Stack<>();
        Stack<String> stringStack = new Stack<>();
        
        String currentString = "";
        int currentNum = 0;
        
        for (char ch : s.toCharArray()) {
            
            if (Character.isDigit(ch)) {
                currentNum = currentNum * 10 + (ch - '0');
            }
            
            else if (ch == '[') {
                countStack.push(currentNum);
                stringStack.push(currentString);
                
                currentNum = 0;
                currentString = "";
            }
            
            else if (ch == ']') {
                int repeat = countStack.pop();
                String prevString = stringStack.pop();
                
                StringBuilder temp = new StringBuilder(prevString);
                for (int i = 0; i < repeat; i++) {
                    temp.append(currentString);
                }
                
                currentString = temp.toString();
            }
            
            else {
                currentString += ch;
            }
        }
        
        return currentString;
    }
}
```

```java
Input
Input: s = "3[a]2[bc]"
Output: "aaabcbc"
```
