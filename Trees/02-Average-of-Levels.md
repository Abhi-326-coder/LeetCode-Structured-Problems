# Average of Levels in Binary Tree

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
For every level of the binary tree:

Store the number of nodes in the current level using queue.size().
Process exactly those nodes.
Calculate the sum of their values.
Add their left and right children to the queue.
Calculate the average: sum / levelSize.
Add the average to the result.

Use double for sum to safely calculate the average.

Level 0: [3]
Average = 3

Level 1: [9, 20]
Average = (9 + 20) / 2 = 14.5

Level 2: [15, 7]
Average = (15 + 7) / 2 = 11

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
    public List<Double> averageOfLevels(TreeNode root) {
        List<Double> result = new ArrayList<>();

        if(root == null){
            return result;
        }
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while(!queue.isEmpty()){
            int levelSize = queue.size();
            double averageLevel = 0;

            for(int i=0 ; i < levelSize; i++){
                TreeNode currentNode = queue.poll();
                averageLevel += currentNode.val;
                if(currentNode.left != null){
                    queue.offer(currentNode.left);
                }
                if(currentNode.right != null){
                    queue.offer(currentNode.right);
                }
            }
            averageLevel = averageLevel / levelSize;
            result.add(averageLevel);
        }
        return result;
    }
}

```


```java 
Input: root = [3,9,20,null,null,15,7]
Output: [3.00000,14.50000,11.00000]
Explanation: The average value of nodes on level 0 is 3, on level 1 is 14.5, and on level 2 is 11.
Hence return [3, 14.5, 11].


Input: root = [3,9,20,15,7]
Output: [3.00000,14.50000,11.00000]

```
