# Binary Tree Right Side View

## Problem Link
https://leetcode.com/problems/binary-tree-right-side-view/

## Difficulty
Medium

## Topic
Tree | BFS | Binary Tree

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/9D-vP-jcc-Y?si=w2eVxR0TcezC_GCN

## Approach 
- Similar to Binary tree level order traversal but need to ``if(i == levelSize - 1){result.add(currentNode.val)}`` 


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
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> result = new ArrayList<>();

        if(root == null){
            return result;
        }
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while(!queue.isEmpty()){
            int levelSize = queue.size();
            // List<Integer> currentLevel = new ArrayList<>(levelSize);

            for(int i=0 ; i < levelSize; i++){
                TreeNode currentNode = queue.poll();
                // currentLevel.add(currentNode.val);
                if(i == levelSize - 1){
                    result.add(currentNode.val);
                }
                
                if(currentNode.left != null){
                    queue.offer(currentNode.left);
                }
                if(currentNode.right != null){
                    queue.offer(currentNode.right);
                }
            }
        }
        return result;
    }
}

```


```java 
Input: root = [1,2,3,null,5,null,4]

Output: [1,3,4]

Explanation:



Example 2:

Input: root = [1,2,3,4,null,null,null,5]

Output: [1,3,4,5]

Explanation:



Example 3:

Input: root = [1,null,3]

Output: [1,3]

Example 4:

Input: root = []

Output: []
```
