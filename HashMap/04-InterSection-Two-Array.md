# Intersection of Two Arrays

## Problem Link
https://leetcode.com/problems/intersection-of-two-arrays/description/

## Difficulty
Easy

## Topic
Array | Hash Table 

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a0a01d7-aff0-83e8-aeef-75b05c1e8637

## Approach 
- HashSet approach, moving across the nums 
- if(set.contains(num)) then return true means have a duplicates
- else add the num into the set

## Code

```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> ans = new HashSet<>();

        for (int i = 0; i < nums1.length; i++) {

            // avoid duplicate checking
            if (ans.contains(nums1[i])) continue;

            for (int j = 0; j < nums2.length; j++) {
                if (nums1[i] == nums2[j]) {
                    ans.add(nums1[i]);
                    break;
                }
            }
        }

        int[] result = new int[ans.size()];
        int index = 0;

        for (int num : ans) {
            result[index++] = num;
        }

        return result;
    }
}
```


```java 
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
Explanation: [4,9] is also accepted.
```


