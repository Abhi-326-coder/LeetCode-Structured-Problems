# Shuffle String

## Problem Link
https://leetcode.com/problems/shuffle-string/description/

## Difficulty
Easy

## Topic
Array | String 

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a550557-9bd8-83e8-9b6a-8bfc58153fc7

## Approach 
Suppose

s = "code"
indices = [3,1,2,0]
First Loop
Character    Index

c  -> 3
o  -> 1
d  -> 2
e  -> 0

The map becomes

{
0=e,
1=o,
2=d,
3=c
}
Second Loop
j = 0 -> e
j = 1 -> o
j = 2 -> d
j = 3 -> c

Result:

"eodc"

## Optimal Approach
Initially

ans = [_, _, _, _]

After each iteration

i=0
ans[3]='c'

[_, _, _, c]

i=1
ans[1]='o'

[_, o, _, c]

i=2
ans[2]='d'

[_, o, d, c]

i=3
ans[0]='e'

[e, o, d, c]

## Time and Space Complexity
| Approach                     | Time  | Space | Notes                                     |
| ---------------------------- | ----- | ----- | ----------------------------------------- |
| HashMap (your code)          | O(n)  | O(n)  | Extra hashing overhead                    |
| `char[]`                     | O(n)  | O(n)  | Faster, direct indexing                   |
| `StringBuilder` with inserts | O(n²) | O(n)  | Avoid because inserting shifts characters |


# Which should you use?

Whenever you're building a string inside a loop, prefer StringBuilder. It's the standard, efficient approach in Java because it avoids repeatedly creating and copying immutable String objects.


## Code

```java
// My solution

class Solution {
    public String restoreString(String s, int[] indices) {
        Map<Integer, Character> map = new HashMap<>();
        StringBuilder sb = new StringBuilder();
        int i = 0;

        for(char ch : s.toCharArray()){
            map.put(indices[i++], ch);
        }

        for(int j = 0; j < s.length(); j++){
            sb.append(map.get(j));
        }

        return sb.toString();
    }
}

```
```java
class Solution {
    public String restoreString(String s, int[] indices) {
        char[] ans = new char[s.length()];

        for(int i = 0; i < s.length(); i++){
            ans[indices[i]] = s.charAt(i);
        }

        return new String(ans);
    }
}

```


```java 
Input: s = "codeleet", indices = [4,5,6,7,0,2,1,3]
Output: "leetcode"
Explanation: As shown, "codeleet" becomes "leetcode" after shuffling.

Input: s = "abc", indices = [0,1,2]
Output: "abc"
Explanation: After shuffling, each character remains in its position.
 

```
