# Pattern Sliding Window

## Introduction:

* It is usually dealing with array or LinkedList. We are asked to find or calculate something among all the contiguous subarrays of a given size.
* A problem can be solved by two pointers when two pointers come into place to help us reduce the total cases we need to consider, such that the corresponding time complexity will reduce too.
* How to determine whether we can use sliding window: 
  * If a wider scope of the sliding window is valid, the narrower scope of that wider scope is valid must hold
  * If a narrower scope of the sliding window is invalid, the wider scope of that wider scope is invalid must hold

## Leetcode Number:

* [643. Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)

  * The brutal force is to calculate the sum of every 5 element contiguous subarray of the given array and divide the sum by 5 to find the average.  O\(N\*K\)
  * The inefficiency is that for any two consecutive subarrays of size ‘5’, the overlapping part \(which will contain four elements\) will be evaluated twice ![](../.gitbook/assets/image%20%282%29.png) 



  * SADSADSAD





