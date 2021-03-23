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
* 
### [480. Sliding Window Median](https://leetcode.com/problems/sliding-window-median/)

### [502. IPO](https://leetcode.com/problems/ipo/)



## The problem I  struggle with:

* * * 




