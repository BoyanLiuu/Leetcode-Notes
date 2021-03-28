# 12. Top K elements

## Heap:

Any problem that asks us to find the top/smallest/frequent ‘K’ elements among a given set falls under this pattern.



The best data structure that comes to mind to keep track of ‘K’ elements is Heap. This pattern will make use of the Heap to solve multiple problems dealing with ‘K’ elements at a time from a set of given elements.

* Top K largest: Using min heap,
* Top K smallest : Using max heap

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
* At each step, we try to remove current occurrence  - 1, if size of K &gt;=0 then distinct number + 1

### [767. Reorganize String](https://leetcode.com/problems/reorganize-string/)

*  In each step, we should append one occurrence of the highest frequency character to the output string. We will not put this character back in the heap to ensure that no two same characters are adjacent to each other. In the next step, we should process the next most frequent character from the heap in the same way and then, at the end of this step, insert the character from the previous step back to the heap after decrementing its frequency.

## **Hard**

### [358. Rearrange String k Distance Apart](https://leetcode.com/problems/rearrange-string-k-distance-apart/)

* Quite similar to rearrange String, we will re-insert the character after K iterations, We can keep track of previous characters in a queue to insert them back in the heap after K  iterations
* we add the character back when the queue size is same as 
* Time complexity: O\(NlogN\), Space complexity: O\(N\)

### [621. Task Scheduler](https://leetcode.com/problems/task-scheduler/)

*  we will use a Max Heap to execute the highest frequency task first. After executing a task we decrease its frequency and put it in a waiting list. In each iteration, we will try to execute as many as k+1 tasks. For the next iteration, we will put all the waiting tasks back in the Max Heap. If, for any iteration, we are not able to execute k+1 tasks, the CPU has to remain idle for the remaining time in the next iteration.

```text
class Solution {
    public int leastInterval(char[] tasks, int k) {
        int intervalCount = 0;
        Map<Character, Integer> taskFrequencyMap = new HashMap<>();
        for (char chr : tasks)
            taskFrequencyMap.put(chr, taskFrequencyMap.getOrDefault(chr, 0) + 1);

        PriorityQueue<Map.Entry<Character, Integer>> maxHeap = new PriorityQueue<Map.Entry<Character, Integer>>(
        (e1, e2) -> e2.getValue() - e1.getValue());

        // add all tasks to the max heap
        maxHeap.addAll(taskFrequencyMap.entrySet());

        while (!maxHeap.isEmpty()) {
          List<Map.Entry<Character, Integer>> waitList = new ArrayList<>();
          int n = k + 1; // try to execute as many as 'k+1' tasks from the max-heap
          for (; n > 0 && !maxHeap.isEmpty(); n--) {
            intervalCount++;
            Map.Entry<Character, Integer> currentEntry = maxHeap.poll();
            if (currentEntry.getValue() > 1) {
              currentEntry.setValue(currentEntry.getValue() - 1);
              waitList.add(currentEntry);
            }
          }
          maxHeap.addAll(waitList); // put all the waiting list back on the heap
          if (!maxHeap.isEmpty())
            intervalCount += n; // we'll be having 'n' idle intervals for the next iteration
        }

        return intervalCount;
    }
}
```

### [895. Maximum Frequency Stack](https://leetcode.com/problems/maximum-frequency-stack/)

* Problem we need to solve:
  * How can we keep track of the frequencies of numbers in the heap? 
    * Use hashmap
  * How do we know which one  to pop if two elements have same frequencies
    * To resolve this, we need to attach a sequence number to every number to know which number came first.

![](../.gitbook/assets/image%20%2823%29.png)

* 
\*\*\*\*

## The Problem I  struggle:

* 767
* 358
* 621
* 895



### 

### 



