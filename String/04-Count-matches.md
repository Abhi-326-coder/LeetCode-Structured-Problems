# Count Items Matching a Rule

## Problem Link
https://leetcode.com/problems/count-items-matching-a-rule/description/

## Difficulty
Easy

## Topic
String | Array

## Platform
LeetCode

## Video or Solution Link


## Approach 
use Switch to map ruleKey with index
```java
// Map ruleKey to index
        switch (ruleKey) {
            case "type":
                index = 0;
                break;
            case "color":
                index = 1;
                break;
            case "name":
                index = 2;
                break;
        }
```

## Time and Space Complexity
Time complexity : O(n)
space complexity : O(n)


## Code

```java
class Solution {
    public int countMatches(List<List<String>> items, String ruleKey, String ruleValue) {
        int ans = 0;
        int index = 0;

        // Map ruleKey to index
        switch (ruleKey) {
            case "type":
                index = 0;
                break;
            case "color":
                index = 1;
                break;
            case "name":
                index = 2;
                break;
        }

        // Loop through items
        for (List<String> item : items) {
            if (item.get(index).equals(ruleValue)) {
                ans++;
            }
        }
        return ans;
    }
}

```


```java 
Input: items = [["phone","blue","pixel"],["computer","silver","lenovo"],["phone","gold","iphone"]], ruleKey = "color", ruleValue = "silver"
Output: 1
Explanation: There is only one item matching the given rule, which is ["computer","silver","lenovo"].

```
