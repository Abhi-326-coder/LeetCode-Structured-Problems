# Find All Numbers Disappeared in an Array

## Problem Link
https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/

## Difficulty
Easy

## Topic
Array | Hash Table

## Platform
LeetCode  

## Video or Solution Link
https://chatgpt.com/c/69c2ae5e-499c-83a2-8d0c-9b58971fd819

## Approach 1(My approach)
- Using the ``Cyclic Sort`` place numbers in correct position
- find the missing numbers out of the sorted array and add it to list Result list

Time Complexity: O(n)

Space Complexity: O(1)

## Approach 2
create a hashset ``numSet`` and add the all the values of given nums into it. then create another List ``result`` and we'll use the ``.contains`` to check the i values exist within it or not, if not add it to result 

Time Complexity: O(n)

Space Complexity: O(n)

## Code

```java
// My Approach 
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        int i = 0;

        // Step 1: Place numbers in correct positions
        while (i < nums.length) {
            int correctIndex = nums[i] - 1;

            if (nums[i] != nums[correctIndex]) {
                int temp = nums[i];
                nums[i] = nums[correctIndex];
                nums[correctIndex] = temp;
            } else {
                i++;
            }
        }

        // Step 2: Find missing numbers
        List<Integer> result = new ArrayList<>();
        for (int index = 0; index < nums.length; index++) {
            if (nums[index] != index + 1) {
                result.add(index + 1);
            }
        }

        return result;
    }
}
```

```java
// approach 2
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        Set<Integer> numSet = new HashSet<>();
        for (int num : nums) {
            numSet.add(num);
        }
        
        List<Integer> result = new ArrayList<>();
        for (int i = 1; i <= nums.length; i++) {
            if (!numSet.contains(i)) {
                result.add(i);
            }
        }
        
        return result;        
    }
}
```

## Output Example

```java 
Input: nums = [4,3,2,7,8,2,3,1]
Output: [5,6]

Input: nums = [1,1]
Output: [2]
```