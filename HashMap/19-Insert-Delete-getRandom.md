# Insert Delete GetRandom O(1)

## Problem Link
https://leetcode.com/problems/insert-delete-getrandom-o1/description/

## Difficulty
Medium

## Topic
Array | Hash Table | Design 

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a38e045-2ea8-83ee-8a67-b0873fe9b6fc

video Solution : https://youtu.be/DhWkpltokYM?si=GYaCNRujJO39U233

## Approach 
1. ArrayList → access random element in O(1)
2. HashMap<Integer, Integer> → store value and its index in ArrayList
## Time and Space Complexity

| Operation | Time |
| --------- | ---- |
| Insert    | O(1) |
| Remove    | O(1) |
| GetRandom | O(1) |


## Code

```java

import java.util.*;

class RandomizedSet {

    private ArrayList<Integer> list;
    private HashMap<Integer, Integer> map;
    private Random random;

    public RandomizedSet() {
        list = new ArrayList<>();
        map = new HashMap<>();
        random = new Random();
    }

    public boolean insert(int val) {
        if (map.containsKey(val)) {
            return false;
        }

        list.add(val);
        map.put(val, list.size() - 1);

        return true;
    }

    public boolean remove(int val) {
        if (!map.containsKey(val)) {
            return false;
        }

        int index = map.get(val);
        int lastElement = list.get(list.size() - 1);

        list.set(index, lastElement);
        map.put(lastElement, index);

        list.remove(list.size() - 1);
        map.remove(val);

        return true;
    }

    public int getRandom() {
        int randomIndex = random.nextInt(list.size());
        return list.get(randomIndex);
    }
}

```


```java 
Input
["RandomizedSet", "insert", "remove", "insert", "getRandom", "remove", "insert", "getRandom"]
[[], [1], [2], [2], [], [1], [2], []]
Output
[null, true, false, true, 2, true, false, 2]
```
