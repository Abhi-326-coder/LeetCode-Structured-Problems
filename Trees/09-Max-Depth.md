# Maximum Depth of Binary Tree

## Problem Link
https://leetcode.com/problems/maximum-depth-of-binary-tree/description/

## Difficulty
Easy

## Topic
Tree | BFS | DFS | Binary Tree

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/9D-vP-jcc-Y?si=w2eVxR0TcezC_GCN

## Approach 

Traversal Used: Postorder DFS
DFS Returns: Height of the subtree
``int depth = Math.max(left, right) + 1;``

## Time and Space Complexity
Time Complexity = O(N)

Space Complexity = O(N)

## Code

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {

    public int maxDepth(TreeNode root) {

        if(root == null){
            return 0;
        }

        int left = maxDepth(root.left);

        int right = maxDepth(root.right);

        int depth = Math.max(left, right) + 1;

        return depth;
    }

}

```


```java 
Input: root = [3,9,20,null,null,15,7]
Output: 3
Example 2:

Input: root = [1,null,2]
Output: 2

```
