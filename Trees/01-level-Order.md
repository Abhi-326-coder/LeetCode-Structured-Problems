# Binary Tree Level Order Traversal

## Problem Link
https://leetcode.com/problems/binary-tree-level-order-traversal/description/

## Difficulty
Medium

## Topic
Tree | BFS | Binary Tree

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/9D-vP-jcc-Y?si=w2eVxR0TcezC_GCN

## Approach 
Put the root into a queue.
While the queue is not empty:
Get queue.size(). This tells us how many nodes belong to the current level.
Process exactly those nodes.
Add their children to the queue for the next level.
Store the current level in result.

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
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();

        if(root == null){
            return result;
        }
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while(!queue.isEmpty()){
            int levelSize = queue.size();

            List<Integer> currentLevel = new ArrayList<>(levelSize);

            for(int i=0 ; i < levelSize; i++){
                TreeNode currentNode = queue.poll();
                currentLevel.add(currentNode.val);
                if(currentNode.left != null){
                    queue.offer(currentNode.left);
                }
                if(currentNode.right != null){
                    queue.offer(currentNode.right);
                }
            }
            result.add(currentLevel);
        }
        return result;
    }
}

```


```java 
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]

Example 2:

Input: root = [1]
Output: [[1]]

Example 3:

Input: root = []
Output: []

```
