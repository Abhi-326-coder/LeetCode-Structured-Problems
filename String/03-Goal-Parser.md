# Goal Parser Interpretation

## Problem Link
https://leetcode.com/problems/goal-parser-interpretation/

## Difficulty
Easy

## Topic
String 

## Platform
LeetCode

## Video or Solution Link


## Approach 


## Time and Space Complexity
Time complexity : O(n)
space complexity : O(n)


# Which should you use?

Whenever you're building a string inside a loop, prefer StringBuilder. It's the standard, efficient approach in Java because it avoids repeatedly creating and copying immutable String objects.


## Code

```java
class Solution {
    public String interpret(String command) {
        StringBuilder sb = new StringBuilder();

        for (int i = 0; i < command.length(); i++) {
            if (command.charAt(i) == 'G') {
                sb.append('G');
            } else if (command.charAt(i) == '(' && command.charAt(i + 1) == ')') {
                sb.append('o');
                i++; // Skip ')'
            } else {
                sb.append("al");
                i += 3; // Skip "al)"
            }
        }

        return sb.toString();
    }
}

```


```java 
Input: command = "G()(al)"
Output: "Goal"
Explanation: The Goal Parser interprets the command as follows:
G -> G
() -> o
(al) -> al
The final concatenated result is "Goal".
```
