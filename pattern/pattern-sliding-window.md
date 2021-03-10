# Pattern Sliding Window

## Introduction:

* It is usually dealing with array or LinkedList. We are asked to find or calculate something among all the contiguous subarrays of a given size.
* A problem can be solved by two pointers when two pointers come into place to help us reduce the total cases we need to consider, such that the corresponding time complexity will reduce too.
* How to determine whether we can use sliding window: 
  * If a wider scope of the sliding window is valid, the narrower scope of that wider scope is valid must hold
  * If a narrower scope of the sliding window is invalid, the wider scope of that wider scope is invalid must hold

## Easy:

### [643. Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/) 

* 变种题目： 
  * Maximum Sum Subarray of Size K
  * [209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)
* The brutal force is to calculate the sum of every 5 element contiguous subarray of the given array and divide the sum by 5 to find the average.  O\(N\*K\)
* The inefficiency is that for any two consecutive subarrays of size ‘5’, the overlapping part \(which will contain four elements\) will be evaluated twice ![](../.gitbook/assets/image%20%282%29.png) .There are four overlapping elements between the subarray.
* The efficient way to solve this problem would be to visualize each contiguous subarray as a sliding window of ‘5’ elements. This means that we will slide the window by one element when we move on to the next subarray. To reuse the sum from the previous subarray, we will subtract the element going out of the window and add the element now being included in the sliding window. This will save us from going through the whole subarray to find the sum and, as a result, the algorithm complexity will reduce to **O\(N\)**

```text
    public double findMaxAverage(int[] nums, int k) {
        double  maxAverage = Integer.MIN_VALUE *1.0;
        int windowStart =0;
        double sum = 0;
        
        for(int windowEnd = 0;windowEnd < nums.length; windowEnd++){
            sum += nums[windowEnd];//add the element
            
            //when we reach to the limit
            if(windowEnd - windowStart + 1 == k){
                //calculate the average
                double temp =  (sum*1.0) / k;
                maxAverage =  Math.max(temp,maxAverage);
                //subtract the element going out
                sum -= nums[windowStart];
                //slide the window adhead
                windowStart ++;
            }
            
           
            
        }
        
        return maxAverage;
    }
```

### [209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)

* We keep adding element till the sum &gt;= target
* We will shrink the window until the window’s sum is smaller than ‘S’ again. This is needed as we intend to find the smallest window. This shrinking will also happen in multiple steps; in each step, we will do two things:
  * Check if the current window length is the smallest so far, and if so, remember its length.
  * Subtract the first element of the window from the running sum to shrink the sliding window.

```text
 public int minSubArrayLen(int target, int[] nums) {
        int sum =0;
        int minimum = Integer.MAX_VALUE;
        
        int windowStart =0;
        
        for(int windowEnd =0; windowEnd < nums.length; windowEnd++){
            
            sum += nums[windowEnd];
            
            while(sum >= target){
                int length = windowEnd -windowStart +1;
                minimum = Math.min(length,minimum);
                sum -= nums[windowStart];
                windowStart++;
            }
            
            
        }
        return minimum == Integer.MAX_VALUE ? 0 : minimum;
        
    }
```

### [340. Longest Substring with At Most K Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)



## Medium:

* 
