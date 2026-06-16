# Valid Sudoko

## Problem Link
https://leetcode.com/problems/valid-sudoku/

## Difficulty
Medium

## Topic
Array | Hash Table | Matrix

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a3182b6-6cbc-83ee-a05d-e907e19cfd5e

video Solution : https://youtu.be/j1Cs6rF6wYs?si=0OPTr0vQKTrsvZMi

## Approach 
Create:
rows[9] → stores digits seen in each row.
cols[9] → stores digits seen in each column.
boxes[9] → stores digits seen in each 3×3 sub-box.
Traverse every cell (r, c):
Skip if the cell contains '.'.

Calculate the box index:

int boxIndex = (r / 3) * 3 + (c / 3);
If the digit already exists in the corresponding row, column, or box set, return false.
Otherwise, add it to all three sets.
If traversal completes without duplicates, return true.

## Time and Space Complexity

Time Complexity = O(n²)
Space Complexity = O(n²)


## Code

```java

class Solution {
    public boolean isValidSudoku(char[][] board) {
        HashSet<Character>[] rows = new HashSet[9];
        HashSet<Character>[] cols = new HashSet[9];
        HashSet<Character>[] boxes = new HashSet[9];

        for (int i = 0; i < 9; i++) {
            rows[i] = new HashSet<>();
            cols[i] = new HashSet<>();
            boxes[i] = new HashSet<>();
        }

        for (int r = 0; r < 9; r++) {
            for (int c = 0; c < 9; c++) {
                if (board[r][c] == '.') {
                    continue;
                }

                char value = board[r][c];
                int boxIndex = (r / 3) * 3 + (c / 3);

                if (rows[r].contains(value) || cols[c].contains(value) || boxes[boxIndex].contains(value)) {
                    return false;
                }

                rows[r].add(value);
                cols[c].add(value);
                boxes[boxIndex].add(value);
            }
        }

        return true;        
    }
}

```


```java 

Input: board = 
[["5","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
Output: true

```


