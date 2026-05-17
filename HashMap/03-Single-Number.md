# Single Number

## Problem Link
https://leetcode.com/problems/single-number/description/

## Difficulty
Easy

## Topic
Array | Hash Table 

## Platform
LeetCode

## Video or Solution Link


## Approach 
- HashSet approach, moving across the nums 
- if(set.contains(num)) then return true means have a duplicates
- else add the num into the set

## Code

```java
class Solution {
    public int singleNumber(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        
        for(int num : nums){
            if(!map.containsKey(num)){
                map.put(num, 0);
            }
            map.put(num, map.get(num) + 1);
        }

        for(int num : nums){
            if(map.get(num) == 1){
                return num;
            }
        }
        return -1;
    }
}
```


```java 
Input: nums = [2,2,1]

Output: 1

Input: nums = [4,1,2,1,2]

Output: 4
```


