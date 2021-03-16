# 8. Top K elements

## Heap:

## Some code snippet:

* How to create a heap

```text
PriorityQueue<Map.Entry<String, Integer>> pq = new PriorityQueue<>(
        (a,b) -> a.getValue()==b.getValue() ? b.getKey().compareTo(a.getKey()) : a.getValue()-b.getValue()
);
```

* 


## Easy:

* [692. Top K Frequent Words](https://leetcode.com/problems/top-k-frequent-words/)
* [973. K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)

## Medium:



