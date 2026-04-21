# Game of Two Stacks

## Problem Link
https://www.hackerrank.com/challenges/game-of-two-stacks/problem

## Difficulty
Easy

## Topic
Stack | Arrays

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/S9LUYztYLu4?si=c2UetgagW9NA0BML

## Approach
Solve using Recursion
        ``int ans1 = twoStacks(x, Arrays.copyOfRange(a, 1, a.length), b, sum+a[0], count + 1);``
        ``int ans2 = twoStacks(x, b, Arrays.copyOfRange(a, 1, a.length), sum+a[0], count + 1)``


Time Complexity	  O(2^(n + m))
Space Complexity  O((n + m)²)
Recursion Stack	  O(n + m)

## Code

```java
class Solution{
    public static int GameTwoStacks(int x, int int[] a,int[] b){
        return twoStacks(x,a,b,0,0) - 1;
    }

    private static int twoStacks(int x, int[] a, int[] b, int sum, int count ){
            if(sum > x){
                return count;
            }
            if(a.length == 0 || b.length == 0){
                return count;
            }
            int ans1 = twoStacks(x, Arrays.copyOfRange(a, 1, a.length), b, sum+a[0], count + 1);
            int ans2 = twoStacks(x, a, Arrays.copyOfRange(b, 1, b.length), sum + b[0], count + 1);

            return Math.max(ans1, ans2);// ans1 and ans2 are returning the count here we are finding max of count which is what required 
        }
}
```

