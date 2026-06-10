# Group Shifted String

## Problem Link
https://leetcode.com/problems/group-shifted-strings/description/ (Premium)

## Difficulty
Medium

## Topic
Array | Hash Table | String | Sorting

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a29849c-d9a4-8321-bc1b-dbf59ce23a45

video Solution : https://youtu.be/Xl9ysqP-yu4?si=x1hgWZA98hjG_4aj

## Approach 
For each string, compute a key using differences between adjacent characters.
Store strings having the same key in a HashMap.
Return all groups from the map.

## Time and Space Complexity

Time Complexity = O(n * k)
Space Complexity = O(n * k)


## Code

```java

class Solution {
    public List<List<String>> groupStrings(String[] strings) {
        Map<String, List<String>> map = new HashMap<>();

        for (String s : strings) {
            String key = getKey(s);

            map.putIfAbsent(key, new ArrayList<>());
            map.get(key).add(s);
        }

        return new ArrayList<>(map.values());
    }

    private String getKey(String s) {
        if (s.length() == 1) {
            return "single";
        }

        StringBuilder key = new StringBuilder();

        for (int i = 1; i < s.length(); i++) {
            int diff = (s.charAt(i) - s.charAt(i - 1) + 26) % 26;
            key.append(diff).append(",");
        }

        return key.toString();
    }
}

```


```java 

```


