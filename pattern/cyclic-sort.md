# 5.Cyclic Sort

## Summary:

* This pattern describes an interesting approach to deal with problems involving arrays containing numbers _in a given range._
* \*\*\*\*🗝 **key points when solving similar problems** --------------------------------------------------------
  * Be careful about the relationship between indices and their value when doing cyclic sort
  * ---------------------------------------------------------------------------------------------------------------

## Easy:

### [268. Missing Number](https://leetcode.com/problems/missing-number/)

* Exact same idea as Cyclic Sort 

### [645. Set Mismatch](https://leetcode.com/problems/set-mismatch/)

* Exact same idea as Cyclic Sort

## Cyclic Sort:

**Question:** Given an array containing n objects from 1 to n, Sort the array in-place and in O\(N\) ![](../.gitbook/assets/image%20%2812%29.png) 

**Solution:**

* Since all numbers are unique, we can try placing each number at its correct place, i.e., placing ‘1’ at index ‘0’, placing ‘2’ at index ‘1’, and so on.
* To place a number \(or an object in general\) at its correct index, we first need to find that number. If we first find a number and then place it at its correct place, it will take us O\(N^2\)O\(N  ^2  \), which is not acceptable.
* Instead, what if we iterate the array one number at a time, and if the current number we are iterating is not at the correct index, we swap it with the number at its correct index. This way we will go through all numbers and place them in their correct indices, hence, sorting the whole array.

```text
  public static void sort(int[] nums) {
    int i = 0;
    while (i < nums.length) {
      int j = nums[i] - 1;
      // check if current element is at right index
      if (nums[i] != nums[j])
        swap(nums, i, j);
      else
        i++;
    }
  }

  private static void swap(int[] arr, int i, int j) {
    int temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
  }
```

## Medium:

### [287. Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)

* Exact same idea as Cyclic Sort

```text
  public static int findNumber(int[] nums) {
    int i = 0;
    while (i < nums.length) {
      if (nums[i] != i + 1) {
        if (nums[i] != nums[nums[i] - 1])
          swap(nums, i, nums[i] - 1);
        else // we have found the duplicate
          return nums[i];
      } else {
        i++;
      }
    }

    return -1;
  }

  private static void swap(int[] arr, int i, int j) {
    int temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
  }
```

### [448. Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)

* Exact same idea as Cyclic Sort

### [442. Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/)

* Exact same idea as Cyclic Sort

## Hard:

### [41. First Missing Positive](https://leetcode.com/problems/first-missing-positive/)

* In this example, The numbers are not bound by any range so we can have any number in the input array
* We  place the numbers on their correct indices and ignore all numbers that are out of the range of the array\(i.e., all negative numbers and all numbers greater than or equal to the length of the array\).
* Once we are done with the cyclic sort we will iterate the array and the first index that does not have the correct number will be the smallest missing positive number!

### Find the First K missing positive number:

**Question:** Given an unsorted array containing numbers and a number ‘k’, find the first ‘k’ missing positive numbers in the array.  

![](../.gitbook/assets/image%20%2813%29.png)

  
**Answer:**

* Follow a similar approach as discussed in the 41 ,Once we are done with the cyclic sort, we will iterate through the array to find indices that do not have the correct numbers.
* If we are not able to find ‘k’ missing numbers from the array, we need to add additional numbers to the output array. To find these additional numbers we will use the length of the array. 
* For example, if the length of the array is 4, the next missing numbers will be 4, 5, 6 and so on. One tricky aspect is that any of these additional numbers could be part of the array. Remember, while sorting, we ignored all numbers that are greater than or equal to the length of the array. So all indices that have the missing numbers could possibly have these additional numbers. To handle this, we must keep track of all numbers from those indices that have missing numbers. Let’s understand this with an example:



## Problem I struggle with:

* 41

### 



