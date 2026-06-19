# 4Sum II

## Problem Link
https://leetcode.com/problems/4sum-ii/description/

## Difficulty
Medium

## Topic
Array | Hash Table | Principle

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a356e33-9f58-83ee-89ff-12022a03dec2

video Solution : https://youtu.be/GWYPi8cuc5w?si=YyAcfgBHanW80oBV
## Approach 
Instead of checking all quadruplets:

Store all sums of nums1[i] + nums2[j] in a HashMap.
For every sum nums3[k] + nums4[l], look for its complement -(sum) in the map.
Add the frequency.

## Time and Space Complexity

Time Complexity = O(n²)
Space Complexity = O(n²)
Time Complexity for searching complements = O(n²)


## Code

```java

class Solution {
    public int fourSumCount(int[] nums1, int[] nums2,
                            int[] nums3, int[] nums4) {

        HashMap<Integer, Integer> map = new HashMap<>();

        // Store all sums of nums1 and nums2
        for (int a : nums1) {
            for (int b : nums2) {
                map.put(a + b, map.getOrDefault(a + b, 0) + 1);
            }
        }

        int count = 0;

        // Find complements from nums3 and nums4
        for (int c : nums3) {
            for (int d : nums4) {
                count += map.getOrDefault(-(c + d), 0);
            }
        }

        return count;
    }
}

```


```java 

Input: nums1 = [1,2], nums2 = [-2,-1], nums3 = [-1,2], nums4 = [0,2]
Output: 2
Explanation:
The two tuples are:
1. (0, 0, 0, 1) -> nums1[0] + nums2[0] + nums3[0] + nums4[1] = 1 + (-2) + (-1) + 2 = 0
2. (1, 1, 0, 0) -> nums1[1] + nums2[1] + nums3[0] + nums4[0] = 2 + (-1) + (-1) + 0 = 0

```


