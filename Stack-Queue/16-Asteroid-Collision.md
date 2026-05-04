# Asteroid Collision

## Problem Link
https://leetcode.com/problems/asteroid-collision/description/

## Difficulty
Medium

## Topic
Stack | Array | Simulation

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/69f8c91d-cc94-8324-937b-c01bc2cac851

## Approach 1
For each asteroid:

If it's moving right → push
If moving left:
While stack top is > 0 (possible collision):
Compare sizes
Handle:
smaller explodes
equal → both removed
larger survives
If it survives → push to stack

Time: O(n) (each asteroid processed once)
Space: O(n) (stack)

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
Input: asteroids = [5,10,-5]
Output: [5,10]
Explanation: The 10 and -5 collide resulting in 10. The 5 and 10 never collide.

Input: asteroids = [3,5,-6,2,-1,4]​​​​​​​
Output: [-6,2,4]
Explanation: The asteroid -6 makes the asteroid 3 and 5 explode, and then continues going left. On the other side, the asteroid 2 makes the asteroid -1 explode and then continues going right, without reaching asteroid 4.
 
```
