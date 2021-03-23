# 8. Two Heaps

## Summary:

In many problems, where we are given a set of elements such that we can divide them into two parts. To solve the problem, we are interested in knowing the smallest element in one part and the biggest element in the other part. This pattern is an efficient approach to solve such problems.

* Good for problems where we are given a set of elements such that we can divide them into two parts. To solve the problem, we are interested in knowing the smallest element in one part and the biggest element in the other part.

This pattern uses two Heaps to solve these problems; A Min Heap to find the smallest element and a Max Heap to find the biggest element.







## Easy:



## Medium:

### [436. Find Right Interval](https://leetcode.com/problems/find-right-interval/)



## Hard:

### [295. Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)

* Brutal force: Inserting a number in a sorted list ,It will take O\(N\) time.
* Better Solution: Utilize the fact that we don’t need the fully sorted list - we are only interested in finding the middle element?
* Assume ‘x’ is the median of a list. This means that half of the numbers in the list will be smaller than \(or equal to\) ‘x’ and half will be greater than \(or equal to\) ‘x’. This leads us to an approach where we can divide the list into two halves: one half to store all the smaller numbers \(let’s call it smallNumList\) and one half to store the larger numbers \(let’s call it largNumList\).The median of all the numbers will either be the largest number in the smallNumList or the smallest number in the largNumList. If the total number of elements is even, the median will be the average of these two numbers.
  * We can store the first half of numbers in a maxHeap as we are interested in knowing the largest number in the first half.
  * We can store the second half of numbers \(i.e., largeNumList\) in a Min Heap, as we are interested in knowing the smallest number in the second half.
* **Algorithm:**
  * `We decide to have more element in max heap than min heap.`
  * At first we insert value into max Heap. Then in every step, we insert a number in the max heap if the number is smaller than the top number of the heap. 
  * After every iteration, we will balance the number of elements in both heaps, so that they have an equal number of elements
  * We pop from one heap and insert into other heap.
  * If we have even number of elements, the median is the average of the top element of both the heap
  * If we have an odd number of elements , the median will be the top element of Max heap. An odd number of elements also means that the Max Heap will have one extra element than the Min Heap.

### [480. Sliding Window Median](https://leetcode.com/problems/sliding-window-median/)

### [502. IPO](https://leetcode.com/problems/ipo/)



## The problem I  struggle with:

* * * 




