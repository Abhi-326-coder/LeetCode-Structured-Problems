# Logger Rate Limiter

## Problem Link
https://leetcode.com/problems/logger-rate-limiter/ (Premium question)

## Difficulty
Easy

## Topic
Array | Hash Table | String


## Platform
LeetCode

## Video or Solution Link
https://youtu.be/orr37fHDNnw?si=9uoEfIv2OVGYj6n1


## Approach 
Logger logger = new Logger();

logger.shouldPrintMessage(1, "foo");   // true
logger.shouldPrintMessage(2, "foo");   // false
logger.shouldPrintMessage(10, "foo");  // false
logger.shouldPrintMessage(11, "foo");  // true

## Time and Space Complexity

Time: O(1) per call
Space: O(n), where n is the number of unique messages stored in the HashMap.


## Code

```java
class Logger {
    HashMap<String, Integer> map;

    public Logger() {
        map = new HashMap<>();
    }

    public boolean shouldPrintMessage(int timestamp, String message) {

        if (!map.containsKey(message)) {
            map.put(message, timestamp);
            return true;
        }

        if (timestamp - map.get(message) >= 10) {
            map.put(message, timestamp);
            return true;
        }

        return false;
    }
}
```


```java 

Logger logger = new Logger();

logger.shouldPrintMessage(1, "foo");   // true
logger.shouldPrintMessage(2, "foo");   // false
logger.shouldPrintMessage(10, "foo");  // false
logger.shouldPrintMessage(11, "foo");  // true

```


