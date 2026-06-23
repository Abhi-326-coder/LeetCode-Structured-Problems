# Longest Substring Without Repeating Characters

## Problem Link
https://leetcode.com/problems/longest-substring-without-repeating-characters/description/

## Difficulty
Medium

## Topic
Array | Hash Table | Sliding Window 

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a3a5da4-185c-83ee-8c54-77d3a22d1e45

video Solution : https://youtu.be/Rs9jrYjVQEk?si=sx-CR3h9gVzeR-B6

## Approach 
(Sliding Window)
Maintain a window [left, right]
Use a HashMap to store last index of characters
Expand right pointer
If duplicate found → move left

## Time and Space Complexity
Time: O(n) ✅ (each char processed once)
Space: O(min(n, charset))


## Code

```java

class Solution {
    public int lengthOfLongestSubstring(String s) {
        Map<Character, Integer> map = new HashMap<>();

        int right = 0, left = 0;

        int maxLen = 0;

        while(right < s.length()){
            char curChar = s.charAt(right);

            if(map.containsKey(curChar)){
                int curCharIndex = map.get(curChar);

                if(curCharIndex >= left){
                    left = curCharIndex + 1;
                }
            }
            maxLen = Math.max(maxLen, right - left + 1);
            map.put(curChar, right);
            right = right + 1;
        }
        return maxLen;
    }
    
}


```


```java 

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3. Note that "bca" and "cab" are also correct answers.

```
