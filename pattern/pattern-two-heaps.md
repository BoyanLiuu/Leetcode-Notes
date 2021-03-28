# 12. Top K elements

## Heap:

Any problem that asks us to find the top/smallest/frequent ‘K’ elements among a given set falls under this pattern.



The best data structure that comes to mind to keep track of ‘K’ elements is Heap. This pattern will make use of the Heap to solve multiple problems dealing with ‘K’ elements at a time from a set of given elements.

* Top K largest: Using min heap,
* Top k smallest : Using max heap

## Some code snippet:

* How to create a heap

```text
PriorityQueue<Map.Entry<String, Integer>> pq = new PriorityQueue<>(
        (a,b) -> a.getValue()==b.getValue() ? b.getKey().compareTo(a.getKey()) : a.getValue()-b.getValue()
);


// Create a map entry priority queue
PriorityQueue<Map.Entry<String, Integer>> pq = new PriorityQueue<>(
         (a,b) -> a.getValue()==b.getValue() ? b.getKey().compareTo(a.getKey()) : a.getValue()-b.getValue()
);

// add map into the max heap
pq.addAll(characterFrequencyMap.entrySet());

Map.Entry<Character, Integer> entry = pq.poll();

```

* 


## Easy:

### [215. Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)

```text
public int findKthLargest(int[] nums, int k) {
         PriorityQueue<Integer> minHeap = new PriorityQueue<Integer>((n1, n2) -> n1 - n2);
        
        for(Integer cur : nums){
            minHeap.add(cur);
            if(minHeap.size() > k)
                minHeap.poll();
        }
        return minHeap.peek(); 
}
```

* The typical problem , in top K elements, 
* we iterate elements in Heap and keep K elements in Heap.
  * We get smallest number in a min-heap in constant time and re construct the heap take O\(logK\), as the heap need to readjust after the removal of an element
  * Total Time complexity: O\(KlogK\), space complexity: O\(K\)

#### [973. K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)

* Same as 215 no variation

#### [347. Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)

* Same as 215 no variation

#### [692. Top K Frequent Words](https://leetcode.com/problems/top-k-frequent-words/)

* Same as 215 no variation

#### [451. Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)

#### [703. Kth Largest Element in a Stream](https://leetcode.com/problems/kth-largest-element-in-a-stream/)

* 略微有变化但是还是 same idea as 215

#### [**658. Find K Closest Elements**](https://leetcode.com/problems/find-k-closest-elements/)\*\*\*\*

## Medium:

### Maximum Distinct Elements 

* [1481. Least Number of Unique Integers after K Removals](https://leetcode.com/problems/least-number-of-unique-integers-after-k-removals/)
* We first find the frequencies of all the numbers
* Then push all numbers that are not distinct in a min Heap based on their frequencies.
* At each step, we try to remove current occurance  - 1, if size of K &gt;=0 then distinct number + 1

### [767. Reorganize String](https://leetcode.com/problems/reorganize-string/)

### [358. Rearrange String k Distance Apart](https://leetcode.com/problems/rearrange-string-k-distance-apart/)

### [621. Task Scheduler](https://leetcode.com/problems/task-scheduler/)

### [895. Maximum Frequency Stack](https://leetcode.com/problems/maximum-frequency-stack/)

### [719. Find K-th Smallest Pair Distance](https://leetcode.com/problems/find-k-th-smallest-pair-distance/)

### 

### 



