# Validate Binary Search Tree

## Problem Link
https://leetcode.com/problems/validate-binary-search-tree/description/

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

For every node, maintain a valid range:

low = smallest value the node is allowed to have
high = largest value the node is allowed to have

For the root:
```java
helper(root, null, null)
```

## Time and Space Complexity
Time Complexity = O(N)

Space Complexity = O(h) or O(log(n))

## Code

```java
class Solution {
    public boolean isValidBST(TreeNode root) {
        return helper(root, null, null);
    }

    public boolean helper(TreeNode node, Integer low, Integer high) {
        if (node == null) {
            return true;
        }

        if (low != null && node.val <= low) {
            return false;
        }

        if (high != null && node.val >= high) {
            return false;
        }

        boolean leftTree = helper(node.left, low, node.val);
        boolean rightTree = helper(node.right, node.val, high);

        return leftTree && rightTree;
    }
}
```


```java 
Example 1:


Input: root = [2,1,3]
Output: true
Example 2:


Input: root = [5,1,4,null,null,3,6]
Output: false
Explanation: The root node's value is 5 but its right child's value is 4.
 

```
