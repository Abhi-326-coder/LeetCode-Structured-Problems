# Contains Duplicate II

## Problem Link
https://leetcode.com/problems/contains-duplicate-ii/description/

## Difficulty
Easy

## Topic
Array | Hash Table | String


## Platform
LeetCode

## Video or Solution Link
https://youtu.be/O2HRsifRfnc?si=xhypb-eSekiR1vfg


## Approach 
Traverse the array.
For each element nums[i]:
Check if it already exists in the map.
If it exists, calculate the distance between the current index and the previous index.
If the distance is <= k, return true.
Otherwise, update the index of that number in the map.
If no such pair is found, return false.

## Time and Space Complexity

Time Complexity
Loop runs n times.
containsKey(), get(), and put() are O(1) on average.

Time Complexity: O(n)

Space Complexity
In the worst case, all elements are distinct.
HashMap stores n entries.

Space Complexity: O(n)


## Code

```java
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();

        int count = 0;
        // 1,2,3,1
        for(int num : nums){ 
            // 1 2 3 1
            if(map.containsKey(num) && Math.abs(map.get(num) - count) <= k){
                // true && (0 - 3)=3<=3 true
                return true;
            }else{
                // (1,0)
                // (2,1)
                // (3,2) 
                map.put(num, count);
                count++;            
                }
        }
        return false;
    }
}
```


```java 

Input: nums = [1,2,3,1], k = 3
Output: true

Input: nums = [1,0,1,1], k = 1
Output: true

```


