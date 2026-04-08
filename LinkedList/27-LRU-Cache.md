#  LRU Cache

## Problem Link
https://leetcode.com/problems/lru-cache/description/

## Difficulty
Medium

## Topic 
Hash Table | Linked List | Design | Doubly-Linked List


## Platform
leetcode 

## Video or Solution Link
https://chatgpt.com/c/69d5f7b8-80c0-83e8-897d-150331f0e16d

## Optimal Approach (didn't got answer)
get(key)
If key exists:
Move node to front (mark as recently used)
Return value
Else return -1
🔵 put(key, value)
If key exists:
Update value
Move to front
Else:
Create new node
Add to front
If capacity exceeded:
Remove node from tail (LRU)

## Code

```java
// Optimal approach I
import java.util.*;

class LRUCache {

    class Node {
        int key, value;
        Node prev, next;

        Node(int k, int v) {
            key = k;
            value = v;
        }
    }

    private int capacity;
    private HashMap<Integer, Node> map;
    private Node head, tail;

    public LRUCache(int capacity) {
        this.capacity = capacity;
        map = new HashMap<>();

        // Dummy nodes
        head = new Node(0, 0);
        tail = new Node(0, 0);

        head.next = tail;
        tail.prev = head;
    }

    // Remove node from DLL
    private void remove(Node node) {
        node.prev.next = node.next;
        node.next.prev = node.prev;
    }

    // Insert node right after head (MRU position)
    private void insert(Node node) {
        node.next = head.next;
        node.prev = head;

        head.next.prev = node;
        head.next = node;
    }

    public int get(int key) {
        if (!map.containsKey(key)) return -1;

        Node node = map.get(key);
        remove(node);
        insert(node); // move to front

        return node.value;
    }

    public void put(int key, int value) {
        if (map.containsKey(key)) {
            Node node = map.get(key);
            node.value = value;

            remove(node);
            insert(node);
        } else {
            if (map.size() == capacity) {
                // remove LRU (tail.prev)
                Node lru = tail.prev;
                remove(lru);
                map.remove(lru.key);
            }

            Node newNode = new Node(key, value);
            map.put(key, newNode);
            insert(newNode);
        }
    }
}
```

## Output Example

```java 
["LRUCache", "put", "put", "get", "put", "get", "put", "get", "get", "get"]
[[2], [1, 1], [2, 2], [1], [3, 3], [2], [4, 4], [1], [3], [4]]
Output
[null, null, null, 1, null, -1, null, -1, 3, 4]

```