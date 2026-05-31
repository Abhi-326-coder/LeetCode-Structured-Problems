# Intersection of Two Arrays II

## Problem Link
https://leetcode.com/problems/first-unique-character-in-a-string/description/

## Difficulty
Easy

## Topic
Array | Hash Table | String


## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a1c6847-833c-8323-af9d-d8bdcbee89db


## Approach 
Iterates through nums1 once.
Time: O(n)
Iterates through nums2 once.
HashMap operations are O(1) on average.
Time: O(m)
Let k be the size of the intersection.
Time: O(k)

Time complexity : O(n + m)
Space complexity(including result) : O(min(n,m) + k)


## Code


```java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        if(nums1.length > nums2.length ){
            return intersect(nums2, nums1);
        }

        List<Integer> result = new ArrayList<>();

        Map<Integer, Integer> counts = new HashMap<>();

        for(int num : nums1){
            counts.put(num, counts.getOrDefault(num, 0) + 1);
        }

        for(int num : nums2){
            if(counts.containsKey(num) && counts.get(num) > 0){
                counts.put(num, counts.get(num) - 1);
                result.add(num);
            }
        }

        int[] ans = new int[result.size()];

        for(int i = 0; i < result.size(); i++){
            ans[i] = result.get(i);
        }

        return ans;
    }
}
```


```java 
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2,2]

```


