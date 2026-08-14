# Lowest Common Ancestor of a Binary Tree

## Problem Link
https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/

## Difficulty
Medium

## Topic
Tree | DFS | Binary Tree

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/9D-vP-jcc-Y?si=w2eVxR0TcezC_GCN

## Approach 

Traversal Used: Preorder DFS
DFS Returns: Height of the subtree

1. Is this node null?
       ↓
      null

2. Is this node p or q?
       ↓
      return node

3. Search left and right
       ↓
   ┌───────┴───────┐
 left             right

Both found?
   ↓
Yes → current node is LCA

Only one found?
   ↓
Return the one found

## Time and Space Complexity

Time: O(N)
Space: O(H), where H is the height of the tree.
Worst-case space: O(N)
Balanced-tree space: O(log N)

## Code

```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root == null){
            return root;
        }
        // root = 3, p = 5, q = 1
        if(root == p || root == q){
            return root;
        }

        TreeNode left = lowestCommonAncestor(root.left, p, q);
        TreeNode right = lowestCommonAncestor(root.right, p, q);

        if(left != null && right != null){
            return root;
        }

        return left == null ? right : left;
    }
}
```


```java 
Example 1:


Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
Output: 3
Explanation: The LCA of nodes 5 and 1 is 3.
Example 2:


Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
Output: 5
Explanation: The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.
Example 3:

Input: root = [1,2], p = 1, q = 2
Output: 1
```
