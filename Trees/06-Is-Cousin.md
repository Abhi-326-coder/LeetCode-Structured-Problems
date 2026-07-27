#  Cousins in Binary Tree

## Problem Link
https://leetcode.com/problems/cousins-in-binary-tree/description/

## Difficulty
Medium

## Topic
Tree | BFS | DFS | Binary Tree

## Platform
LeetCode

## Video or Solution Link
https://youtu.be/9D-vP-jcc-Y?si=w2eVxR0TcezC_GCN

## Approach 
If the tree is empty, return false.
Create a queue and insert the root.
Repeat until the queue becomes empty:
Store the current level size.
Initialize:
foundX = false
foundY = false
Traverse every node of that level.
For every node:
If its value is x, set foundX = true.
If its value is y, set foundY = true.
Check whether its left and right child exist.
If one child is x and the other is y, they are siblings.
Return false.
Push children into the queue.
After finishing the level:
If both foundX and foundY are true → return true.
If only one is true → return false.
If traversal finishes, return false.


## Time and Space Complexity
Time Complexity = O(N)

Space Complexity = O(N)

## Code

```java

class Solution {
    public boolean isCousins(TreeNode root, int x, int y) {

        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while (!queue.isEmpty()) {

            int size = queue.size();
            boolean foundX = false;
            boolean foundY = false;

            for (int i = 0; i < size; i++) {

                TreeNode node = queue.poll();

                // Check if current node is x or y
                if (node.val == x)
                    foundX = true;
                if (node.val == y)
                    foundY = true;

                // Check if x and y are siblings
                if (node.left != null && node.right != null) {
                    int left = node.left.val;
                    int right = node.right.val;

                    if ((left == x && right == y) ||
                        (left == y && right == x)) {
                        return false;
                    }
                }

                // Add children to queue
                if (node.left != null)
                    queue.offer(node.left);

                if (node.right != null)
                    queue.offer(node.right);
            }

            // If both found on the same level
            if (foundX && foundY)
                return true;

            // Only one found on this level
            if (foundX || foundY)
                return false;
        }

        return false;
    }
}

```


```java 
Input: root = [1,2,3,4], x = 4, y = 3
Output: false
Example 2:


Input: root = [1,2,3,null,4,null,5], x = 5, y = 4
Output: true
Example 3:


Input: root = [1,2,3,null,4], x = 2, y = 3
Output: false
```
