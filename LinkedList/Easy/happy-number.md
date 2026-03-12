# Happy Number

## Problem Link
https://leetcode.com/problems/happy-number/description/

## Difficulty
Easy

## Topic
LinkedList(does't Look like One) | Hash Table | Math | Two Pointers

## Platform
LeetCode 

## Video or Solution Link
https://youtu.be/70tx7KcMROc?si=TU895CfXqvtY8Fqo

## Approach
This one doesn't look like Linked list but the approach we have used if ``fast and slow pointer method`` and here at some point the values of findSquare similar basic goes to infinite loop which we call a ``Cycle``

``fast = findSquare(findSquare(fast))``

``slow = findSquare(fast)``

- A ``findSquare(int number)`` function which will return me the square values

- ``isHappy`` function will run the loop till fast and slow equals if equals then its cycle running in a infinite loop or if either value becomes 1 then it's a Happy number


Time Complexity: O(n)

Space Complexity: O(1)

## Code

```java
class Solution {
    public boolean isHappy(int n) {
        int fast = n;
        int slow = n;
        do{
            fast = findSquare(findSquare(fast));
            slow = findSquare(slow);
        }while(fast!=slow);

        if(slow == 1){
            return true;
        }
        return false;
    }
    public int findSquare(int number){
        int ans = 0;
        while(number > 0){
            int rem = number % 10;
            ans = ans + rem*rem;
            number = number / 10;
        }
        return ans;
    }
}
```

## Output Example

```java 
Input: n = 19
Output: true
Explanation:
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```