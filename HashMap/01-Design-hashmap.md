# Design HashMap

## Problem Link
https://leetcode.com/problems/design-hashmap/description/

## Difficulty
Easy

## Topic
Array | Hash Table | Linked List | Design | Hash Function


## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a0362cd-fd40-8322-80dc-c04fd4592b13

## Approach 1 (My Approach)
-Using ArrayList of Linkedlist of entity/pair
- ``Iterator<Pair<Integer, Integer>> it = list.iterator();``

So overall:

Assume:

n = total keys
k = bucket size
put()
Average: O(1)
Worst: O(n)
get()
Average: O(1)
Worst: O(n)
remove()
Average: O(1)
Worst: O(n)

Space Complexity

O(n+k)

## Code


```java
class Pair<U, V> {
    U first;
    V second;

    public Pair(U f, V s) {
        first = f;
        second = s;
    }
}

class Bucket {
    List<Pair<Integer, Integer>> list;

    public Bucket() {
        list = new LinkedList<>();
    }

    public void put(int key, int value) {
        for (Pair<Integer, Integer> p : list) {
            if (p.first == key) {
                p.second = value;
                return;
            }
        }

        list.add(new Pair<>(key, value));
    }

    public int get(int key) {
        for (Pair<Integer, Integer> p : list) {
            if (p.first == key) {
                return p.second;
            }
        }
        return -1;
    }

    public void remove(int key) {
        Iterator<Pair<Integer, Integer>> it = list.iterator();

        while (it.hasNext()) {
            Pair<Integer, Integer> p = it.next();

            if (p.first == key) {
                it.remove();
                return;
            }
        }
    }
}

class MyHashMap {

    Bucket[] buckets;
    int keyRange = 769;

    public MyHashMap() {
        buckets = new Bucket[keyRange];

        for (int i = 0; i < keyRange; i++) {
            buckets[i] = new Bucket();
        }
    }

    public int getBucketIndex(int key) {
        return key % keyRange;
    }

    public void put(int key, int value) {
        int bucketIdx = getBucketIndex(key);
        buckets[bucketIdx].put(key, value);
    }

    public int get(int key) {
        int bucketIdx = getBucketIndex(key);
        return buckets[bucketIdx].get(key);
    }

    public void remove(int key) {
        int bucketIdx = getBucketIndex(key);
        buckets[bucketIdx].remove(key);
    }
}
```


```java 
Input
["MyHashMap", "put", "put", "get", "get", "put", "get", "remove", "get"]
[[], [1, 1], [2, 2], [1], [3], [2, 1], [2], [2], [2]]
Output
[null, null, null, 1, -1, null, 1, null, -1]
```


