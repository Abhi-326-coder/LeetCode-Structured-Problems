# Find Duplicate Subtrees

## Problem Link
https://leetcode.com/problems/find-duplicate-subtrees/description/

## Difficulty
Medium

## Topic
Tree | Hash Table |Binary Tree | Depth-First Search

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a3eb1b9-839c-83ee-8611-a762c140ff8a

video Solution : https://youtu.be/JHh6-B7VwsM?si=EqNfv_Gps8mqqfrk

## Approach 
Postorder Traversal

Process:

Serialize left subtree.
Serialize right subtree.
Create current subtree serialization.
Store serialization frequency in a HashMap.
When frequency becomes 2, add the node to answer.

## Time and Space Complexity
Time: O(n) 
Space: O(n)


## Code

```java

class Solution {
    Map<String, Integer> map = new HashMap<>();
    List<TreeNode> result = new ArrayList<>();

    public List<TreeNode> findDuplicateSubtrees(TreeNode root) {
        serialize(root);
        return result;
    }

    private String serialize(TreeNode node) {
        if (node == null) {
            return "#";
        }

        String serial = node.val + "," +
                        serialize(node.left) + "," +
                        serialize(node.right);

        int freq = map.getOrDefault(serial, 0);

        if (freq == 1) { // duplicate found
            result.add(node);
        }

        map.put(serial, freq + 1);

        return serial;
    }
}


```


```java 

Input: root = [1,2,3,4,null,2,4,null,null,4]
Output: [[2,4],[4]]

Input: root = [2,1,1]
Output: [[1]]

```
