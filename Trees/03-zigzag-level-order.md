# Binary Tree Zigzag Level Order Traversal

## Problem Link
https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/

## Difficulty
Medium

## Topic
Tree | BFS | Binary Tree 


## Platform
LeetCode

## Video or Solution Link
https://youtu.be/9D-vP-jcc-Y?si=w2eVxR0TcezC_GCN

## Approach 
For every level:

Find the number of nodes in the current level using queue.size().
Process exactly those nodes.
If leftToRight == true, add values normally at the end.
Otherwise, add values at the beginning.
After completing the level, reverse the direction.

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
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();

        if(root == null){
            return result;
        }
        Deque<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        boolean reverse = false;

        while(!queue.isEmpty()){
            int levelSize = queue.size();

            List<Integer> currentLevel = new ArrayList<>(levelSize);

            for(int i=0 ; i < levelSize; i++){
                if(!reverse){
                    TreeNode currentNode = queue.pollFirst();
                    currentLevel.add(currentNode.val);
                    
                    if(currentNode.left != null){
                        queue.addLast(currentNode.left);
                    }
                    if(currentNode.right != null){
                        queue.addLast(currentNode.right);
                    }
                }else{
                    TreeNode currentNode = queue.pollLast();
                    currentLevel.add(currentNode.val);
                    
                    if(currentNode.right != null){
                        queue.addFirst(currentNode.right);
                    }
                    if(currentNode.left != null){
                        queue.addFirst(currentNode.left);
                    }
                    
                }
            }
            reverse = !reverse;
            result.add(currentLevel);
        }
        return result;
    }
}

```


```java 

Example 1:

Input: root = [3,9,20,null,null,15,7]
Output: [[3],[20,9],[15,7]]
Example 2:

Input: root = [1]
Output: [[1]]

```
