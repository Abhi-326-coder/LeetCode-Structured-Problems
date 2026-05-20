# Design HashSet

## Problem Link
https://leetcode.com/problems/design-hashset/description/

## Difficulty
Easy

## Topic
Array | Hash Table | Linked List | Design | Hash Function


## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a0df852-d464-8320-b2c1-39ecf1ccc65e

## Approach 
- Using ArrayList of Linkedlist of entity/pair
- ``LinkedList<Integer>[] buckets``
- Use an array of buckets
- Each bucket stores values having same hash
- Collision handling using linked list (or dynamic list)

So overall:

Assume:

n = total keys
k = bucket size
add() → O(n)
remove() → O(n)
contains() → O(n)

Space Complexity

O(n + buckets)
Usually written as O(n)

## Code


```java
class MyHashSet {

    private int size = 1000;
    private LinkedList<Integer>[] buckets;

    public MyHashSet() {
        buckets = new LinkedList[size];
    }

    private int hash(int key) {
        return key % size;
    }

    public void add(int key) {
        int index = hash(key);

        if (buckets[index] == null) {
            buckets[index] = new LinkedList<>();
        }

        if (!buckets[index].contains(key)) {
            buckets[index].add(key);
        }
    }

    public void remove(int key) {
        int index = hash(key);

        if (buckets[index] != null) {
            buckets[index].remove(Integer.valueOf(key));
        }
    }

    public boolean contains(int key) {
        int index = hash(key);

        return buckets[index] != null &&
               buckets[index].contains(key);
    }
}
```


```java 
["MyHashSet", "add", "add", "contains", "contains", "add", "contains", "remove", "contains"]
[[], [1], [2], [1], [3], [2], [2], [2], [2]]
```


