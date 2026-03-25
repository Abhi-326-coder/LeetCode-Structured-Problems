# Design Twitter

## Problem Link
https://leetcode.com/problems/design-twitter/description/

## Difficulty
Medium

## Topic 
Hash Table | Linked List | Design | Heap (Priority Queue) | OOPs

## Platform
LeetCode 

## Video or Solution Link
https://chatgpt.com/c/69c40442-fcf4-8324-b786-56fbe45f71a3

## Approach
Instead of deleting the node…

👉 Copy next node’s data into current node
👉 Then delete the next node

Time Complexity: 
- postTweet() - O(1)
- follow() or unfollow() - O(1)
- getNewsFeed() - O((F × T) log (F × T))

Space Complexity: O(1)

## Code

```java
class Twitter {

    private Map<Integer, Set<Integer>> followMap;
    private Map<Integer, List<int[]>> tweetMap;
    private int time;

    public Twitter() {
        followMap = new HashMap<>();
        tweetMap = new HashMap<>();
        time = 0;
    }
    
    public void postTweet(int userId, int tweetId) {
        tweetMap.putIfAbsent(userId, new ArrayList<>());
        tweetMap.get(userId).add(new int[]{time++, tweetId});
    }
    
    public List<Integer> getNewsFeed(int userId) {
        PriorityQueue<int[]> maxHeap = new PriorityQueue<>(
            (a, b) -> b[0] - a[0]
        );

        followMap.putIfAbsent(userId, new HashSet<>());
        followMap.get(userId).add(userId);

        for (int followee : followMap.get(userId)) {
            if (tweetMap.containsKey(followee)) {
                for (int[] tweet : tweetMap.get(followee)) {
                    maxHeap.add(tweet);
                }
            }
        }

        List<Integer> result = new ArrayList<>();
        int count = 10;

        while (!maxHeap.isEmpty() && count-- > 0) {
            result.add(maxHeap.poll()[1]);
        }

        return result;
    }
    
    public void follow(int followerId, int followeeId) {
        followMap.putIfAbsent(followerId, new HashSet<>());
        followMap.get(followerId).add(followeeId);
    }
    
    public void unfollow(int followerId, int followeeId) {
        if (followMap.containsKey(followerId)) {
            followMap.get(followerId).remove(followeeId);
        }
    }
}
```

## Output Example

```java 
Input
["Twitter", "postTweet", "getNewsFeed", "follow", "postTweet", "getNewsFeed", "unfollow", "getNewsFeed"]
[[], [1, 5], [1], [1, 2], [2, 6], [1], [1, 2], [1]]
Output
[null, null, [5], null, null, [6, 5], null, [5]]
```