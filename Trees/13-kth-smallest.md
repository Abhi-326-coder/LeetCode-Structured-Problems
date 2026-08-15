# Kth Smallest Element in a BST

## Problem Link
https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/

## Difficulty
Medium

## Topic
Tree | DFS | Binary Tree

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/9D-vP-jcc-Y?si=w2eVxR0TcezC_GCN

## Approach 

Traversal Used: Inorder DFS
DFS Returns: Height of the subtree



## Time and Space Complexity

Let H be the height of the tree.

Time: O(H + k)

We may travel down the tree to reach the first node: O(H)
Then visit up to k nodes.

In the worst case, we may visit almost the entire tree:

Worst-case time = O(N)

where N is the number of nodes.

Space: O(H)

## Code

```java
class Solution {
    int count = 0;
    int answer = 0;

    public int kthSmallest(TreeNode root, int k) {
        inorder(root, k);
        return answer;
    }

    public void inorder(TreeNode node, int k) {
        if (node == null) {
            return;
        }

        // Go to left subtree
        inorder(node.left, k);

        // Visit current node
        count++;

        if (count == k) {
            answer = node.val;
            return;
        }

        // Go to right subtree
        inorder(node.right, k);
    }
}

```


```java 
Example 1:


Input: root = [3,1,4,null,2], k = 1
Output: 1
Example 2:


Input: root = [5,3,6,2,4,null,null,1], k = 3
Output: 3
```
