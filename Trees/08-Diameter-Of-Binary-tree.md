# Diameter of Binary Tree

## Problem Link
https://leetcode.com/problems/diameter-of-binary-tree/

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
Global Variable Stores: Maximum diameter
Diameter Through Current Node: leftHeight + rightHeight
Height Returned to Parent: 1 + max(leftHeight, rightHeight)

## Time and Space Complexity
Time Complexity = O(N)

Space Complexity = O(log N)

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

    private int diameter = 0;

    public int diameterOfBinaryTree(TreeNode root) {
        dfs(root);
        return diameter;
    }

    private int dfs(TreeNode node) {

        // Base Case
        if (node == null)
            return 0;

        // Calculate left and right heights
        int leftHeight = dfs(node.left);
        int rightHeight = dfs(node.right);

        // Update maximum diameter
        diameter = Math.max(diameter, leftHeight + rightHeight);

        // Return height of current node
        return 1 + Math.max(leftHeight, rightHeight);
    }
}

```


```java 
Input: root = [1,2,3,4,5]
Output: 3
Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].

Input: root = [1,2]
Output: 1
```
