# Sorting the Sentence

## Problem Link
https://leetcode.com/problems/sorting-the-sentence/description/

## Difficulty
Easy

## Topic
String | Array

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a58f9d1-3600-83ee-b0aa-4b7501519c76

## Approach 
Each word has a number at the end indicating its correct position.

Example:

```
Input:  "is2 sentence4 This1 a3"

This1    → position 1
is2      → position 2
a3       → position 3
sentence4 → position 4

Output: "This is a sentence"
```

We can:

Split the sentence using spaces.
Create a result array of the same size.
For each word:
Get the last character, which represents its position.
Convert it from char to int.
Remove the last character from the word.
Store the word at the correct index.
Join all words with spaces.


## Time and Space Complexity
Time complexity : O(n)
space complexity : O(n)


## Code

```java
class Solution {
    public String sortSentence(String s) {
        String[] words = s.split(" ");
        String[] result = new String[words.length];

        for (String word : words) {
            int position = word.charAt(word.length() - 1) - '0';

            String actualWord = word.substring(0, word.length() - 1);

            result[position - 1] = actualWord;
        }

        return String.join(" ", result);
    }
}
```


```java 
Example 1:

Input: s = "is2 sentence4 This1 a3"
Output: "This is a sentence"
Explanation: Sort the words in s to their original positions "This1 is2 a3 sentence4", then remove the numbers.
Example 2:

Input: s = "Myself2 Me1 I4 and3"
Output: "Me Myself and I"
Explanation: Sort the words in s to their original positions "Me1 Myself2 and3 I4", then remove the numbers.
 
```
