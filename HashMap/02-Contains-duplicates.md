# Contains Duplicate

## Problem Link
https://leetcode.com/problems/contains-duplicate/description/

## Difficulty
Easy

## Topic
Array | Hash Table 

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a04aa10-3c2c-8324-bad6-0292462c2044

## Approach (My Approach)
- using ``Arrays.Sort`` and check adjacent element if they are equal

## Approach 
- HashSet approach, moving across the nums 
- if(set.contains(num)) then return true means have a duplicates
- else add the num into the set

## Code

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> set = new HashSet<>();

        for(int num : nums){
            if(set.contains(num)){
                return true; 
            }
            set.add(num);
        }
        return false;
    }
}

```


```java 
Input: nums = [1,2,3,1]

Output: true

Explanation:

The element 1 occurs at the indices 0 and 3.
```


