# 10. Modified Binary Search

## Summary:

whenever we are given a _sorted Array_ or _LinkedList_ or _Matrix_, and we are asked to find a certain element, the best algorithm we can use is the Binary Search.

* Use \(low + high\) &gt;&gt;&gt;1 avoid integer overflow, or use low + \(high-low\)/2
* When to use low &lt;=high and low &lt; high 
  * We use while \(low &lt;= hi\) if we are returning the match from inside the loop. The searching should be terminated only when the array is empty. At each step, our searching array is \[low, high\], when low = high, the array still contains 1 element and we need to check it.
  * We use while \(low &lt; hi\) when we want to exit the loop first and then use the result of lo or hi to return the match.



## EASY:

### [704. Binary Search](https://leetcode.com/problems/binary-search/)

* _**基础模板**_
  * _**Minimum Difference Element**_

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

* _**基础模板变种， return left**_ 
* \*\*\*\*[744. Find Smallest Letter Greater Than Target](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)

Since we are always adjusting our range to find the ‘key’, when we exit the loop, the start of our range will point to the smallest number greater than the ‘key’ as shown in the above picture.

```text
  public static int searchCeilingOfANumber(int[] arr, int key) {
    if (key > arr[arr.length - 1]) // if the 'key' is bigger than the biggest element
      return -1;

    int start = 0, end = arr.length - 1;
    while (start <= end) {
      int mid = start + (end - start) / 2;
      if (key < arr[mid]) {
        end = mid - 1;
      } else if (key > arr[mid]) {
        start = mid + 1;
      } else { // found the key
        return mid;
      }
    }
    // since the loop is running until 'start <= end', so at the end of the while loop, 'start == end+1'
    // we are not able to find the element in the given array, so the next big number will be arr[start]
    return start;
  }
```

\*\*\*\*

### 

### 

## MEDIUM:

### [34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

* 有两种方法 第一种是使用binary search 找到mid 然后 找left 和 right
* 另外一种是只使用 **binary search：**_**变种题型 细微差别**_
  * When trying to find the first position of the ‘key’, we can update end = middle - 1 to see if the key is present before middle.
  * When trying to find the last position of the ‘key’, we can update start = middle + 1 to see if the key is present after middle.

```text

public int[] searchRange(int[] nums, int target) {
    int[] result = new int[2];
    result[0] = findFirst(nums, target);
    result[1] = findLast(nums, target);
    return result;
}

private int findFirst(int[] nums, int target){
    int idx = -1;
    int start = 0;
    int end = nums.length - 1;
    while(start <= end){
        int mid = start + (end - start)/2;
        if(nums[mid] == target) idx = mid;
        if(nums[mid] >= target){
            end = mid - 1;
        }else{
            start = mid + 1;
        }
        
    }
    return idx;
}

private int findLast(int[] nums, int target){
    int idx = -1;
    int start = 0;
    int end = nums.length - 1;
    while(start <= end){
        int mid = start + (end - start)/2;
        if(nums[mid] == target) idx = mid;
        if(nums[mid] <= target){
            start = mid + 1;
        }else{
            end = mid - 1;
        }
   
    }
    return idx;
}
```



### Search in a Sorted Infinite Array

**Question:** Given an infinite sorted array \(or an array with unknown size\), find if a given number ‘key’ is present in the array. Write a function to return the index of the ‘key’ if it is present in the array, otherwise return -1.Since it is not possible to define an array with infinite \(unknown\) size, you will be provided with an interface ArrayReader to read elements of the array. ArrayReader.get\(index\) will return the number at index; if the array’s size is smaller than the index, it will return Integer.MAX\_VALUE

Answer: 

![](../.gitbook/assets/image%20%2829%29.png)

* _**基础模板变种题型**_
* The only issue with applying binary search in this problem is that we don’t know the bounds of the array. To handle this situation, we will first find the proper bounds of the array where we can perform a binary search
* An efficient way to find the proper bounds is to start at the beginning of the array with the bound’s size as ‘1’ and exponentially increase the bound’s size \(i.e., double it\) until we find the bounds that can have the key.



### 

### [162. Find Peak Element](https://leetcode.com/problems/find-peak-element/)

* Bitonic Array Maximum
* _**基础模板变种题型**_
* If arr\[middle\] &gt; arr\[middle + 1\], we are in the second \(descending\) part of the bitonic array. Therefore, our required number could either be pointed out by middle or will be before middle. This means we will be doing: end = middle.
* If arr\[middle\] &lt; arr\[middle + 1\], we are in the first \(ascending\) part of the bitonic array. Therefore, the required number will be after middle. This means we will be doing: start = middle + 1.
* We can break when start == end. Due to the two points mentioned above, both start and end will be pointing at the maximum number of the bitonic array.

### Search element in bitonic array:

* First, we can find the index of the maximum value of the bitonic array, similar to Bitonic Array Maximum. Let’s call the index of the maximum number maxIndex
* Now, we can break the array into two sub-arrays

  * Array from index ‘0’ to maxIndex, sorted in ascending order.
  * Array from index maxIndex+1 to array\_length-1, sorted in descending order.

  We can then call Binary Search separately in these two arrays to search the ‘key’

```text
  //binary search for both ascending or descending
  private static int binarySearch(int[] arr, int key, int start, int end) {
    while (start <= end) {
      int mid = start + (end - start) / 2;

      if (key == arr[mid])
        return mid;

      if (arr[start] < arr[end]) { // ascending order
        if (key < arr[mid]) {
          end = mid - 1;
        } else { // key > arr[mid]
          start = mid + 1;
        }
      } else { // descending order        
        if (key > arr[mid]) {
          end = mid - 1;
        } else { // key < arr[mid]
          start = mid + 1;
        }
      }
    }
    return -1; // element is not found
  }
```

### [33 Search in Rotated Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)

* If arr\[start\] &lt;= arr\[middle\], the numbers from start to middle are sorted in ascending order.
* Else, the numbers from middle+1 to end are sorted in ascending order.
* By comparing the ‘key’ with the numbers at index start and middle we can easily find out if the ‘key’ lies between indices start and middle; if it does, we can skip the second part =&gt; end = middle -1.
* Else, we can skip the first part =&gt; start = middle + 1.

![](../.gitbook/assets/image%20%2831%29.png)

### Rotation Count:

![](../.gitbook/assets/image%20%2830%29.png)

* After calculating the middle
  * If arr\[middle\] &gt; arr\[middle + 1\], then the element at middle + 1 is the smallest.
  * If arr\[middle - 1\] &gt; arr\[middle\], then the element at middle is the smallest.
*  Comparing the numbers at indices start and middle will give us two options:
  * If arr\[start\] &lt; arr\[middle\], the numbers from start to middle are sorted.
  * Else, the numbers from middle + 1 to end are sorted.
* \[10,5,3\]   we can see mid &lt; end && arr\[mid\] &gt; arr\[mid + 1\]
* \[10,-1,2\] we find out mid &gt; start && arr\[mid - 1\] &gt; arr\[mid\]

```text
  public static int countRotations(int[] arr) {
    int start = 0, end = arr.length - 1;
    while (start < end) {
      int mid = start + (end - start) / 2;

      if (mid < end && arr[mid] > arr[mid + 1]) // if mid is greater than the next element
        return mid + 1;
      if (mid > start && arr[mid - 1] > arr[mid]) // if mid is smaller than the previous element
        return mid;

      if (arr[start] < arr[mid]) { // left side is sorted, so the pivot is on right side
        start = mid + 1;
      } else { // right side is sorted, so the pivot is on the left side     
        end = mid - 1;
      }
    }

    return 0; // the array has not been rotated
  }
```

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

* 34
* Search in a Sorted Infinite Array
* 162
* Search Bitonic Array
* 33 very close to figure out the answer
* Rotation Count



