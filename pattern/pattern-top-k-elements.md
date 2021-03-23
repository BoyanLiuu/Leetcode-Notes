# 8. Two Heaps

## Summary:

In many problems, where we are given a set of elements such that we can divide them into two parts. To solve the problem, we are interested in knowing the smallest element in one part and the biggest element in the other part. This pattern is an efficient approach to solve such problems.

* Good for problems where we are given a set of elements such that we can divide them into two parts. To solve the problem, we are interested in knowing the smallest element in one part and the biggest element in the other part.

This pattern uses two Heaps to solve these problems; A Min Heap to find the smallest element and a Max Heap to find the biggest element.







## Easy:



## Medium:

### [436. Find Right Interval](https://leetcode.com/problems/find-right-interval/)

* The brutal force is O\(N^2\), 
* We can utilize the Two Heaps approach. We can push all intervals into two heaps: one heap to sort the intervals on maximum start time \(let’s call it maxStartHeap\) and the other on maximum end time \(let’s call it maxEndHeap\). We can then iterate through all intervals of the \`maxEndHeap’ to find their next interval. Our algorithm will have the following steps
  * Take out the top \(having highest end\) interval from the maxEndHeap to find its next interval. Let’s call this interval topEnd.
  * Find an interval in the maxStartHeap with the closest start greater than or equal to the start of topEnd. Since maxStartHeap is sorted by ‘start’ of intervals, it is easy to find the interval with the highest ‘start’. Let’s call this interval topStart.
  * Add the index of topStart in the result array as the next interval of topEnd. If we can’t find the next interval, add ‘-1’ in the result array.
  * Put the topStart back in the maxStartHeap, as it could be the next interval of other intervals.



## Hard:

### [295. Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)

* Brutal force: Inserting a number in a sorted list ,It will take O\(N\) time.
* Better Solution: Utilize the fact that we don’t need the fully sorted list - we are only interested in finding the middle element?
* Assume ‘x’ is the median of a list. This means that half of the numbers in the list will be smaller than \(or equal to\) ‘x’ and half will be greater than \(or equal to\) ‘x’. This leads us to an approach where we can divide the list into two halves: one half to store all the smaller numbers \(let’s call it smallNumList\) and one half to store the larger numbers \(let’s call it largNumList\).The median of all the numbers will either be the largest number in the smallNumList or the smallest number in the largNumList. If the total number of elements is even, the median will be the average of these two numbers.
  * `We can store the first half of numbers in a maxHeap as we are interested in knowing the largest number in the first half.`
  * `We can store the second half of numbers (i.e., largeNumList) in a Min Heap, as we are interested in knowing the smallest number in the second half.`
* **Algorithm:**
  * `We decide to have more element in max heap than min heap.`
  * At first we insert value into max Heap. Then in every step, we insert a number in the max heap if the number is smaller than the top number of the heap. 
  * After every iteration, we will balance the number of elements in both heaps, so that they have an equal number of elements
  * We pop from one heap and insert into other heap.
  * If we have even number of elements, the median is the average of the top element of both the heap
  * If we have an odd number of elements , the median will be the top element of Max heap. An odd number of elements also means that the Max Heap will have one extra element than the Min Heap.

```text
class MedianFinder {
    PriorityQueue<Integer> maxHeap; //containing first half of numbers
    PriorityQueue<Integer> minHeap; //containing second half of numbers
    /** initialize your data structure here. */
    public MedianFinder() {
        maxHeap = new PriorityQueue<>((a, b) -> b - a);
        minHeap = new PriorityQueue<>((a, b) -> a - b);
    }
    
    public void addNum(int num) {
            if (maxHeap.isEmpty() || maxHeap.peek() >= num)
      maxHeap.add(num);
    else
      minHeap.add(num);

    // either both the heaps will have equal number of elements or max-heap will have one 
    // more element than the min-heap
    if (maxHeap.size() > minHeap.size() + 1)
      minHeap.add(maxHeap.poll());
    else if (maxHeap.size() < minHeap.size())
      maxHeap.add(minHeap.poll());
        
    }
    
    public double findMedian() {
            if (maxHeap.size() == minHeap.size()) {
      // we have even number of elements, take the average of middle two elements
      return maxHeap.peek() / 2.0 + minHeap.peek() / 2.0;
    }
    // because max-heap will have one more element than the min-heap
    return maxHeap.peek();
    }
}
```

### [480. Sliding Window Median](https://leetcode.com/problems/sliding-window-median/)

* Same idea as Two heap, We just need to remove the pop up element from either max heap or min heap.If the element is smaller than max heap top, then we remove from it, other wise we remove from min heap

### [502. IPO](https://leetcode.com/problems/ipo/)

* While selecting a project, we will do two things:
  * Find all the projects that we can choose with the available capital.
  * From the list of projects in the 1st step, choose the project that gives us a maximum profit.
  * Follow Two heaps approach similar to 295
    * Add all project capitals to a min-heap, so that we can select a project with the smallest capital requirement.
    * Go through the top projects of the min-heap and filter the projects that can be completed within our available capital. Insert the profits of all these projects into a max-heap, so that we can choose a project with the maximum profit.
    * Finally, select the top project of the max-heap for investment.
    * Repeat the 2nd and 3rd steps for the required number of projects.



## The problem I  struggle with:

* All of them are hard





