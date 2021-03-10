# 1. Sliding Window

## Summary:

* It is usually dealing with an **`array`** or a **`linked list`** with its **`subarray`**.
* A problem can be solved by two pointers forming a range/window to help us **reduce the total cases we need to consider**, such that the corresponding **time complexity will reduce** too.
* **Rules** that holds a sliding window: 
  * TL;DR: every narrower area within the window is valid, the wider scope is invalid.
    * If a wider scope of the window is valid, the narrower scope of the window must be valid
    * If a narrower scope of the window is invalid, the wider scope of that window must be invalid
* When we finding no repeating character, we record its last index, When we finding K distinct characters, We record its occurrence.



* **Sliding window types:**
  * Fixed Window Size \(easy\) :
    * Iteration time through n sized data structure:
      * **`(Length - K +1)`, K = window size**
    * **Start & end move at the same rate**
  * Varied Window Size \(complex\):
    * Key Points:       **----------------------------------------------------**
      * Determining the **requirement of window movement** 
      * Determining **new starting/ending index**
      *  **----------------------------------------------------------------**
    * Behavior \(snail movement\)
      * Increment starting index **when exceeding** the requirement \(**shrink**\)
      * Increment ending index **when** the requirement is **not fulfilled \(expand\)**

## Easy:

### [643. Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/) 

* 变种题目： 
  * Maximum Sum Subarray of Size K
  * [209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)
* The brutal force is to calculate the sum of every 5 elements contiguous subarray of the given array and divide the sum by 5 to find the average.  O\(N\*K\)
* The inefficiency is that for any two consecutive subarrays of size ‘5’, the overlapping part \(which will contain four elements\) will be evaluated twice. There are four overlapping elements between the subarray.
* The efficient way to solve this problem would be to visualize each contiguous subarray as a sliding window of ‘5’ elements. This means that we will slide the window by one element when we move on to the next subarray. To reuse the sum from the previous subarray, we will subtract the element going out of the window and add the element now being included in the sliding window. This will save us from going through the whole subarray to find the sum and, as a result, the algorithm complexity will reduce to **O\(N\)**

![](../.gitbook/assets/image%20%282%29.png)

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

* Use hashmap to track the occurrence of each character

### [904. Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/)

* Same as finding the longest substring with at most 2 distinct characters

## Medium:

### [3.longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

* We can use a HashMap to remember the **last index of each character** we have processed. Whenever we get a repeating character, we will shrink our sliding window to ensure that we always have distinct characters in the sliding window

### [424. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)

* We’ll iterate through the string to add one letter at a time in the window.
* We’ll also keep track of the count of the maximum repeating letter in any window \(let’s call it maxRepeatLetterCount\).
* So, at any time, we know that we can have a window that has one letter repeating maxRepeatLetterCount times; this means we should try to replace the remaining letters.
* If we have more than `k` remaining letters, we should shrink the window as we are not allowed to replace more than `k` letters.

```text
class Solution {
    public int characterReplacement(String s, int k) {
        int windowStart =0, maxLength  = 0, maxRepeatLetterCount = 0;
        HashMap<Character,Integer> map =  new HashMap<>();
        
        for(int windowEnd = 0; windowEnd< s.length(); windowEnd++){
            char rightChar = s.charAt(windowEnd);
            map.put(rightChar,map.getOrDefault(rightChar,0)+1);
            maxRepeatLetterCount =  Math.max(maxRepeatLetterCount, map.get(rightChar));
            
            // in the range,we have more than k element need to swap, then we shrink window
            if(windowEnd - windowStart -maxRepeatLetterCount +1 > k){
                char leftChar =  s.charAt(windowStart);
                map.put(leftChar, map.get(leftChar) - 1);
                windowStart ++;
                
            }
            maxLength = Math.max(maxLength,windowEnd - windowStart +1 );
            
        }
        return maxLength;
    }
}
```

### [487. Max Consecutive Ones II](https://leetcode.com/problems/max-consecutive-ones/)

* 424 with k equal to 1



### [1004. Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)

* exact same idea as 424

### [1100. Find K-Length Substrings With No Repeated Characters](https://leetcode.com/problems/find-k-length-substrings-with-no-repeated-characters/)

* We need to worry about repeated character and keep track of window range
* Use hash map to record character last index 

### [1438. Longest Continuous Subarray With Absolute Diff Less Than or Equal to Limit ](https://leetcode.com/problems/longest-continuous-subarray-with-absolute-diff-less-than-or-equal-to-limit/)

### [1151. Minimum Swaps to Group All 1's Together](https://leetcode.com/problems/minimum-swaps-to-group-all-1s-together/)

### [395. Longest Substring with At Least K Repeating Characters](https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/)

### [1423. Maximum Points You Can Obtain from Cards](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)

## Hard:

### [567. Permutation in String](https://leetcode.com/problems/permutation-in-string/)

### [438. Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

### [76. Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)

### [30. Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)





## Ivy's Marked Problems w/ Notes:

 



## Boyan's Marked Problems:

* Trouble List:
  * 3
  * 424
  * 487
  * 1100

