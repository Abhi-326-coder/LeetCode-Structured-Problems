# Symmetric Tree

## Problem Link
https://leetcode.com/problems/cousins-in-binary-tree/description/

## Difficulty
Easy

## Topic
Tree | BFS | DFS | Binary Tree

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/9D-vP-jcc-Y?si=w2eVxR0TcezC_GCN

## Approach 

```java
if(left == null && right == null){
                continue;
            }
            if(left == null || right == null){
                return false;
            }

            if(left.val != right.val){
                return false;
            }

            queue.add(left.left);
            queue.add(right.right);
            queue.add(left.right);
            queue.add(right.left);
```

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
    public boolean isSymmetric(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<>();

        queue.add(root.left);
        queue.add(root.right);

        while(!queue.isEmpty()){
            TreeNode left = queue.poll();
            TreeNode right = queue.poll();

            if(left == null && right == null){
                continue;
            }
            if(left == null || right == null){
                return false;
            }

            if(left.val != right.val){
                return false;
            }

            queue.add(left.left);
            queue.add(right.right);
            queue.add(left.right);
            queue.add(right.left);
        }
        return true;
    }
}

```


```java 
Example 1:


Input: root = [1,2,2,3,4,4,3]
Output: true

Example 2:


Input: root = [1,2,2,null,3,null,3]
Output: false
```
