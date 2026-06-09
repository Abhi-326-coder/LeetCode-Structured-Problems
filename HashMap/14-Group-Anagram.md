# Group Anagram

## Problem Link
https://leetcode.com/problems/group-anagrams/description/

## Difficulty
Medium

## Topic
Array | Hash Table | String | Sorting

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a27053f-f27c-8322-8d60-3b56f71cc16e


## Approach 
Create a HashMap.
For each string:
Convert to char array.
Sort it.
Use the sorted string as the key.
Add the original string to the list corresponding to that key.
Return all map values.

## Time and Space Complexity

Time: O(n × k log k)
Space: O(nk)


## Code

```java

class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();

        for (String str : strs) {
            char[] chars = str.toCharArray();
            Arrays.sort(chars);

            String key = new String(chars);

            map.putIfAbsent(key, new ArrayList<>());
            map.get(key).add(str);
        }

        return new ArrayList<>(map.values());
    }
}

```


```java 
Input: strs = ["eat","tea","tan","ate","nat","bat"]

Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```


