# 10. Modified Binary Search

## Summary:

whenever we are given a _sorted Array_ or _LinkedList_ or _Matrix_, and we are asked to find a certain element, the best algorithm we can use is the Binary Search.

* Use \(low + high\) &gt;&gt;&gt;1 avoid integer overflow, or use low + \(high-low\)/2
* When to use low &lt;=high and low &lt; high 
  * We use while \(low &lt;= hi\) if we are returning the match from inside the loop. The searching should be terminated only when the array is empty. At each step, our searching array is \[low, high\], when low = high, the array still contains 1 element and we need to check it.
  * We use while \(low &lt; hi\) when we want to exit the loop first and then use the result of lo or hi to return the match.



## EASY:

### [704. Binary Search](https://leetcode.com/problems/binary-search/)

* _基础模板_

```text
    public int search(int[] nums, int target) {
        int low = 0;
        int high = nums.length - 1;
        
        while(low <= high){
            int mid =  low + ((high-low) /2);
            if (nums[mid] == target) return mid;
            
            if(target > nums[mid])  low = mid +1;  
            else{
                high =mid -1;  
              
            } 
        }
        return -1;
        
    }
```

### `Ceiling of a Number`

**Question**: Given an array of numbers sorted in an ascending order, find the ceiling of a given number ‘key’. The ceiling of the ‘key’ will be the smallest element in the given array greater than or equal to the ‘key’

![](../.gitbook/assets/image%20%2828%29.png)

**Answer:**

\*\*\*\*

### [744. Find Smallest Letter Greater Than Target](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)

### 

## MEDIUM:

### [34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

### Search in a Sorted Infinite Array

### Minimum Difference Element

### [162. Find Peak Element](https://leetcode.com/problems/find-peak-element/)

### Bitonic Array Maximum

### Search Bitonic Array

### [33 Search in Rotated Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)

### Rotation Count

额外从 这个 tag 里找的的题目

### [981	Time Based Key-Value Store](https://leetcode.com/problems/time-based-key-value-store/)

### [528. Random Pick with Weight](https://leetcode.com/problems/random-pick-with-weight/)

### [287. Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)

### [240. Search a 2D Matrix I](https://leetcode.com/problems/search-a-2d-matrix-ii/)

### [300. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)

### [50. Pow\(x, n\)](https://leetcode.com/problems/powx-n/)

### [1283. Find the Smallest Divisor Given a Threshold](https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/)

### [718. Maximum Length of Repeated Subarray](https://leetcode.com/problems/maximum-length-of-repeated-subarray/)

### [74. Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)

### [209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)

### [29. Divide Two Integers](https://leetcode.com/problems/divide-two-integers/)

### [540. Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/)

### 

### 

### 

## HARD:



## The problem I struggle with:



