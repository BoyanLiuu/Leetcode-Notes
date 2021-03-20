# 5.Cyclic Sort

## Summary:

* This pattern describes an interesting approach to deal with problems involving arrays containing numbers _in a given range._
* \_\_

## Easy:

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

## Hard:



