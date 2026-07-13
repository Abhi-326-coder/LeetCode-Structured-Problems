# Defanging an IP Address

## Problem Link
https://leetcode.com/problems/defanging-an-ip-address/description/

## Difficulty
Easy

## Topic
String

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a550557-9bd8-83e8-9b6a-8bfc58153fc7

## Approach 
""        create new string
"1"       create new string
"12"      create new string
"123"     create new string
"1234"    create new string

## Optimal Approach
Create new StringBuilder
↓
Copy "Hello"
↓
Append '!'
↓
Create new String "Hello!"
↓
Destroy old builder

## Time and Space Complexity
Approach	Time	Space	Reason
StringBuilder.append()	O(n)	O(n)	One mutable buffer
String += inside loop	O(n²)	O(n²) temporary allocations	New StringBuilder and String every iteration

# Which should you use?

Whenever you're building a string inside a loop, prefer StringBuilder. It's the standard, efficient approach in Java because it avoids repeatedly creating and copying immutable String objects.


## Code

```java
class Solution {
    public String defangIPaddr(String address) {
        String ans = "";
        for(char ch : address.toCharArray()){
            if(ch == '.'){
                ans += "[.]";
            }else{
                ans += ch;
            }
        }
        return ans;
    }
}

```
```java
class Solution {
    public String defangIPaddr(String s) {
        StringBuilder sb = new StringBuilder();

        for(int i = 0 ; i < s.length(); i++){
            if(s.charAt(i) == '.'){
                sb.append("[.]");
                // i++;
            }
            else{
                sb.append(s.charAt(i));
            }
        }
        return sb.toString();
        
    }
}

```


```java 

Input: address = "1.1.1.1"
Output: "1[.]1[.]1[.]1"

Input: address = "255.100.50.0"
Output: "255[.]100[.]50[.]0"

```
