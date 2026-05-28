# Minimum Index Sum of Two Lists

## Problem Link
https://leetcode.com/problems/minimum-index-sum-of-two-lists/description/

## Difficulty
Easy

## Topic
Array | Hash Table | String


## Platform
LeetCode

## Video or Solution Link
https://leetcode.com/problems/minimum-index-sum-of-two-lists/description/


## Approach 

HashMap → store restaurant and its index from list1
Traverse list2
If restaurant exists in map:
calculate index sum
compare with minimum
update answer accordingly

Time complexity : O(n + m)
Space complexity : O(min(n, m))


## Code


```java
class Solution {
    public String[] findRestaurant(String[] list1, String[] list2) {
        List<String> result = new ArrayList<>();
        Map<String, Integer> map = new HashMap<>();

        for(int i = 0; i < list1.length; i++){
            map.put(list1[i], i);
        }

        int minIndex = Integer.MAX_VALUE;

        for(int i = 0; i < list2.length; i++){
            if (map.containsKey(list2[i])){
                if(i + map.get(list2[i]) < minIndex){
                minIndex = i + map.get(list2[i]);
                result  = new ArrayList<>();
                result.add(list2[i]);
                }else if(i + map.get(list2[i]) == minIndex){
                    result.add(list2[i]);
                }
            }
        }

        String[] ans = new String[result.size()] ; 

        for(int i=0; i < result.size(); i++){
            ans[i] = result.get(i);
        }
        return ans;
    }
    
}
```


```java 
Input: list1 = ["Shogun","Tapioca Express","Burger King","KFC"], list2 = ["Piatti","The Grill at Torrey Pines","Hungry Hunter Steakhouse","Shogun"]
Output: ["Shogun"]
Explanation: The only common string is "Shogun".

```


