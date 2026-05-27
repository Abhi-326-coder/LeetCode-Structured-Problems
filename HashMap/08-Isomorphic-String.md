# Isomorphic String

## Problem Link
https://leetcode.com/problems/isomorphic-strings/description/

## Difficulty
Easy

## Topic
String | Hash Table 


## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a1717cd-0600-8322-8b36-6deb5624a19f


## Approach 

Maintain:

mapping from s -> t
mapping from t -> s

This ensures:

one-to-one mapping
no duplicate mappings

Time complexity : O(n)
Space complexity : O(1)


## Code


```java
class Solution {
    public boolean isIsomorphic(String s, String t) {

        if(s.length() != t.length()) return false;

        HashMap<Character, Character> mapST = new HashMap<>();
        HashMap<Character, Character> mapTS = new HashMap<>();

        for(int i = 0; i < s.length(); i++) {

            char ch1 = s.charAt(i);
            char ch2 = t.charAt(i);

            // check s -> t
            if(mapST.containsKey(ch1)) {
                if(mapST.get(ch1) != ch2) {
                    return false;
                }
            } else {
                mapST.put(ch1, ch2);
            }

            // check t -> s
            if(mapTS.containsKey(ch2)) {
                if(mapTS.get(ch2) != ch1) {
                    return false;
                }
            } else {
                mapTS.put(ch2, ch1);
            }
        }

        return true;
    }
}
```


```java 
Input: s = "f11", t = "b23"

Output: false

Explanation:

The strings s and t can not be made identical as '1' needs to be mapped to both '2' and '3'.

```


