# Two Sum

## Problem Link
https://leetcode.com/problems/two-sum/description/

## Difficulty
Easy

## Topic
Array | Hash Table 

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a0ca3e1-4280-8323-a05b-88d34592f981

## Approach 
- HashSet approach, moving across the nums 
- if(set.contains(num)) then return true means have a duplicates
- else add the num into the set

Time complexity : O(n)
Space complexity : O(n)

## Code

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        
        HashMap<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < nums.length; i++) {
            
            int complement = target - nums[i];
            
            // Check if complement already exists
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            
            // Store current number and its index
            map.put(nums[i], i);
        }
        
        return new int[] {};
    }
}
```


```java 
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

Input: nums = [3,2,4], target = 6
Output: [1,2]
```


