# Top K Frequent Elements

## Problem Link
https://leetcode.com/problems/top-k-frequent-elements/

## Difficulty
Medium

## Topic
Array | Hash Table | Heap(Priority Queue) | Bucket Sort

## Platform
LeetCode

## Video or Solution Link
https://chatgpt.com/c/6a3630fc-9164-83e9-8a0e-3ed6ba0e82ee

video Solution : https://youtu.be/OY4_PcEvZvY?si=79CgqOrlUDnEVhTf
## Approach 
Create a min heap where elements are ordered by their frequency.

`` PriorityQueue<Integer> heap =
    new PriorityQueue<>((a, b) -> map.get(a) - map.get(b));
    ``
The top of the heap always contains the element with the smallest frequency among the current top k elements.
Insert each unique number into the heap.
If the heap size becomes greater than k, remove the top element.

This ensures that:

Low-frequency elements are discarded.
Only the k most frequent elements remain in the heap.
## Time and Space Complexity

Time Complexity : O(n + m log k)
n = total elements
m = unique elements
Space Complexity: O(m + k)


## Code

```java

class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>();

        for(int num : nums){
            map.put(num, map.getOrDefault(num, 0)+1);
        }

        PriorityQueue<Integer> heap = new PriorityQueue<>((e1, e2)-> map.get(e1)-map.get(e2));

        for(int num : map.keySet()){
            heap.add(num);

            if(heap.size() > k){
                heap.poll();
            }
        }
        int[] res = new int[k];

        for(int i = 0; i < k; i++){
            res[i] = heap.poll();
        }

        return res;

    }
}

```


```java 
Example 1:

Input: nums = [1,1,1,2,2,3], k = 2

Output: [1,2]

Example 2:

Input: nums = [1], k = 1

Output: [1]

Example 3:

Input: nums = [1,2,1,2,1,2,3,1,3,2], k = 2

Output: [1,2]
```


