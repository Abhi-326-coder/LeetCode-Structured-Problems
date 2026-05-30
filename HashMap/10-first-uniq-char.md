# First Unique Character in a String

## Problem Link
https://leetcode.com/problems/first-unique-character-in-a-string/description/

## Difficulty
Easy

## Topic
Array | Hash Table | String


## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a1b1bef-1864-8323-b180-9d258005a360


## Approach 
s = "leetcode"

Frequency Map:
l -> 1
e -> 3
t -> 1
c -> 1
o -> 1
d -> 1

Time complexity : O(n)
Space complexity : O(1)


## Code


```java
class Solution {
    public int firstUniqChar(String s) {
        Map<Character, Integer> map = new HashMap<>();

        for(char ch : s.toCharArray()){
            map.put(ch, map.getOrDefault(ch,0) + 1);
        }

        for(int i=0; i < s.length(); i++){
            if(map.get(s.charAt(i)) == 1){
                return i;
            }
        }
        return -1;
    }
}
```


```java 
Input: s = "leetcode"

Output: 0

Explanation:

The character 'l' at index 0 is the first character that does not occur at any other index.

```


