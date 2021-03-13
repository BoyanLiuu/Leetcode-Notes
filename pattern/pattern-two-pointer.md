# 2. Two Pointer

## Summary:

* A great pattern to **`find a set of elements` that fulfill certain constraints in `sorted arrays`/`Linked Lists`** 
  * Types:  **`balancing values`**,  **`in-place switching`**,
    *  but **don't feel like it's limited to these functionalities**, be creative!
* \*\*\*\*🗝 **Key Points:** ------------------------------------------------------------------
  * Where to place the pointers initially\(or to not place them\)?
  * Under what case should we move the pointers?
  * When and where to update the pointers?
  * **-------------------------------------------------------------------------------**

## Types:

* **`In-place switching`:**
  * **\[Main idea\]**: use two pointers to mark the locations for data to be switched in-place
  * **Example questions:**
    * **\#26** [Remove Duplicates \(easy\)](https://www.educative.io/courses/grokking-the-coding-interview/mEEA22L5mNA)
      * one pointer for marking the location to place unduplicated data
      * another for marking the index of unduplicated data 
      * switching happens when two pointers are placed correctly

![](../.gitbook/assets/image%20%284%29.png)

* **`Balancing values`:**
  * **\[Main idea\]**: finding two values that **balancing their calculated value, \(usually sum?\)**, the very basic operation of this pattern is first to **sort the data structure**.
  * **Example questions:**
    * [Pair with Target Sum \(easy\)](https://www.educative.io/courses/grokking-the-coding-interview/xog6q15W9GP)

## Easy:

### [1. Two Sum](https://leetcode.com/problems/two-sum/)

* use map, key is current element, and value is its complement, at every step we check whether the complement exist  or not.  Time Complexity: O\(N\). Space Complexity: O\(N\)

### [167. Two Sum II - Input array is sorted](https://leetcode.com/problems/two-sum-iii-data-structure-design/)

* Sort array 
* At every step, we will see if the numbers pointed by the two pointers add up to the target sum. If they do, we have found our pair; otherwise, we will do one of two things:
  * If the sum of the two numbers pointed by the two pointers is greater than the target sum, this means that we need a pair with a smaller sum. So, to try more pairs, we can decrement the end-pointer.
  * If the sum of the two numbers pointed by the two pointers is smaller than the target sum, this means that we need a pair with a larger sum. So, to try more pairs, we can increment the start-pointe
* Time Complexity: O\(N\). Space Complexity: O\(1\)

### [1099. Two Sum Less Than K](https://leetcode.com/problems/two-sum-less-than-k/)

* Same idea as Two Sum



### 



## Medium:

### [1711. Count Good Meals](https://leetcode.com/problems/count-good-meals/)

### 

### [15. 3Sum](https://leetcode.com/problems/3sum/)

* a + b + c = 0   which means a + b = -c
* we need to find all the unique triplets. To handle this, we have to skip any duplicate number. Since we will be sorting the array, so all the duplicate numbers will be next to each other and are easier to skip.
* In the main function , we need to skip duplicate before searching 
* In the helper function, we need to keep finding other target even if we already got the target, we also need to skip same element

```text
 if(tempSum == target){
                 res.add(Arrays.asList(-target, nums[left],nums[right]));
                left++;
                right --;
                // skip same element
                 while (left < right && nums[left] == nums[left - 1])
                        left++;
                
                while (left < right && nums[right] == nums[right + 1])
                        right--;
  }
```

### [16. 3Sum Closest](https://leetcode.com/problems/3sum-closest/)

* Same idea as 3 Sum
* Note:    `comparing the sum of three numbers to the 'targetSum' can cause overflow so, we will try to find a target difference`

### [259. 3Sum Smaller](https://leetcode.com/problems/3sum-smaller/)

* Let’s say during our iteration we are at number ‘X’, so we need to find ‘Y’ and ‘Z’ such that X + Y + Z &lt; target. At this stage, our problem translates into finding a pair whose sum is less than “target −X” \(as from the above equation Y + Z == target−X\). 
* `If left + right < target , then all the element in between meet our criteria`

```text
class Solution {
      public int threeSumSmaller(int[] nums, int target) {
    Arrays.sort(nums);
    int sum = 0;
    for (int i = 0; i < nums.length - 1; i++) {
        sum += twoSumSmaller(nums, i + 1, target - nums[i]);
    }
    return sum;
}

private int twoSumSmaller(int[] nums, int startIndex, int target) {
    int sum = 0;
    int left = startIndex;
    int right = nums.length - 1;
    while (left < right) {
        if (nums[left] + nums[right] < target) {
            sum += right - left;
            left++;
        } else {
            right--;
        }
    }
    return sum;
}
}
```

### [18. 4Sum](https://leetcode.com/problems/4sum/)

### [763. Partition Labels](https://leetcode.com/problems/partition-labels/)

## Hard:



## Problem I struggle:

* 15
* 1711
* 259



