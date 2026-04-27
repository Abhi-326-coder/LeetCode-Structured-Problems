# Number of Recent Calls

## Problem Link
https://leetcode.com/problems/number-of-recent-calls/description/

## Difficulty
Easy

## Topic
Queue | Arrays

## Platform
LeetCode

## Video or Solution Link (Solved)
https://chatgpt.com/c/69ef912c-b480-83e8-aaca-c11729977a95

## My Approach 
- to use the ArrayList and solve it

Time: O(n**2)

## Optimal approach
This problem is designed for a sliding window using Queue

Idea:
- Store timestamps
- Remove all values < t - 3000
- Remaining size = answer

Time: O(1) amortized per ping
Space: O(n)

## Code

```java
// My approach
public int ping(int t) {
    request.add(t);
    int count = 0;

    for(int i = 0; i < request.size(); i++){
        if(request.get(i) >= t - 3000 && request.get(i) <= t){
            count++;
        }
    }

    return count;
}
```

```java
// Optimal approach
import java.util.*;

class RecentCounter {
    Queue<Integer> q;

    public RecentCounter() {
        q = new LinkedList<>();
    }
    
    public int ping(int t) {
        q.add(t);
        
        while(q.peek() < t - 3000){
            q.poll();
        }
        
        return q.size();
    }
}
```


```java

Input
["RecentCounter", "ping", "ping", "ping", "ping"]
[[], [1], [100], [3001], [3002]]
Output
[null, 1, 2, 3, 3]

Explanation
RecentCounter recentCounter = new RecentCounter();
recentCounter.ping(1);     // requests = [1], range is [-2999,1], return 1
recentCounter.ping(100);   // requests = [1, 100], range is [-2900,100], return 2
recentCounter.ping(3001);  // requests = [1, 100, 3001], range is [1,3001], return 3
recentCounter.ping(3002);  // requests = [1, 100, 3001, 3002], range is [2,3002], return 3

```
