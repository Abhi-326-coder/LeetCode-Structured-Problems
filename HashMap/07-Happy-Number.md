# Happy Number

## Problem Link
https://leetcode.com/problems/happy-number/

## Difficulty
Easy

## Topic
Array | Hash Table | Linked List | Design | Hash Function


## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a147518-328c-8320-903a-f97d6379f5eb 


## Approach 
The loop continues until:

n == 1 (happy number), or
a cycle is detected using HashSet.

For any integer, the sequence quickly reduces to a small range.

| Complexity       | Value                                |
| ---------------- | ------------------------------------ |
| Time Complexity  | (O(\log n))                          |
| Space Complexity | (O(1)) practical, (O(\log n)) formal |


## Code


```java
class Solution {
    public boolean isHappy(int n) {
        Set<Integer> ans = new HashSet<>();
        while(n != 1){
            if(ans.contains(n)){
                return false;
            }
            ans.add(n);
            n = getSquareSum(n);
        }
        return true;
    }
    public int getSquareSum(int n){
        int ans = 0;
        while(n != 0){
            int rem = n % 10 ;
            n = n /10 ;
            ans = ans + rem*rem;
        }
        return ans;
    }
}
```


```java 
Input: n = 19
Output: true
Explanation:
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```


