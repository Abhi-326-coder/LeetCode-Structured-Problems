# Construct Binary Tree from Preorder and Inorder Traversal

## Problem Link
https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/

## Difficulty
Medium

## Topic
Tree | DFS | Binary Tree

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/9D-vP-jcc-Y?si=w2eVxR0TcezC_GCN

## Approach 

Traversal Used: Inorder DFS and PreOrder
DFS Returns: Height of the subtree



## Time and Space Complexity
Time : O(n)

Space: O(n)

## Code

```java
class Solution {

    HashMap<Integer, Integer> map = new HashMap<>();
    int preIndex = 0;

    public TreeNode buildTree(int[] preorder, int[] inorder) {

        // Store inorder value -> index
        for (int i = 0; i < inorder.length; i++) {
            map.put(inorder[i], i);
        }

        return build(preorder, 0, inorder.length - 1);
    }

    public TreeNode build(int[] preorder, int left, int right) {

        // No elements
        if (left > right) {
            return null;
        }

        // First element in preorder is root
        int rootValue = preorder[preIndex++];

        TreeNode root = new TreeNode(rootValue);

        // Find root position in inorder
        int index = map.get(rootValue);

        // Build left subtree
        root.left = build(preorder, left, index - 1);

        // Build right subtree
        root.right = build(preorder, index + 1, right);

        return root;
    }
}

```


```java 
Example 1:


Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
Output: [3,9,20,null,null,15,7]
Example 2:

Input: preorder = [-1], inorder = [-1]
Output: [-1]
```
