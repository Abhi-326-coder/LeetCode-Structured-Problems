# Largest Rectangle in Histogram

## Problem Link
https://leetcode.com/problems/largest-rectangle-in-histogram/description/

## Difficulty
Hard

## Topic
Stack | Arrays

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/S9LUYztYLu4?si=c2UetgagW9NA0BML

## Approach
- Finding the Max Area till the ith height
- Main funciton is to find the max area till and  ``int getMax(int[] arr, Stack<Integer> stack, int max, int i )`` this function get me maxArea till ith


Time Complexity	  O(height * height)
Space Complexity  O(1)

## Code

```java
class Solution {
    public int largestRectangleArea(int[] heights) {
        Stack<Integer> stack = new Stack<>();
        int max = 0;

        stack.push(0);

        for(int i = 1; i < heights.length; i++){
            while(!stack.isEmpty() && heights[i] < heights[stack.peek()]){
                max = getMax(heights,stack, max, i);
            }
            stack.push(i);
        }
        int i = heights.length;
        while(!stack.isEmpty()){
            max = getMax(heights,stack, max, i);
        }
        return max;
    }
    private int getMax(int[] arr, Stack<Integer> stack, int max, int i ){
        int area;
        int popped = stack.pop();
        if(stack.isEmpty()){
            area = arr[popped] * i;
        }else{
            area = arr[popped] * (i - 1 - stack.peek());
        }
        return Math.max(max, area);
    }
}
```

```java
Input: heights = [2,1,5,6,2,3]
Output: 10
Explanation: The above is a histogram where width of each bar is 1.
The largest rectangle is shown in the red area, which has an area = 10 units.
```
