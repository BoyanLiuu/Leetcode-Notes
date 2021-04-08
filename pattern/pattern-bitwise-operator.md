# 11. Bitwise Operator

## Summary:

* XOR: 

  * It is true if one and only one input bit is true

  ![](../.gitbook/assets/image%20%2833%29.png) 

  * It is Associative &  Commutative ![](../.gitbook/assets/image%20%2832%29.png) 

* * 






## Easy:

### [268. Missing Number](https://leetcode.com/problems/missing-number/)

* Space Complexity: O\(1\)
* Time Complexity: O\(N\)

```text
    public int missingNumber(int[] nums) {
        int sum = 0;
        // find sum of all numbers from 0 to n.
        for(int i =0; i<= nums.length; i++)
            sum = sum ^ i;
        
        int sum2 =0;
        // sum2 represents XOR of all values in nums
        for(int num: nums)
            sum2 = sum2 ^ num;
        
        // missing number is the xor of sum2 and sum
        return sum ^ sum2;   
    }
```

### [136. Single Number](https://leetcode.com/problems/single-number/)

### [1009. Complement of Base 10 Integer](https://leetcode.com/problems/complement-of-base-10-integer/)

### 

### 

额外的题目

### [169. Majority Element](https://leetcode.com/problems/majority-element/)

### [191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)

### [476. Number Complement](https://leetcode.com/problems/number-complement/)

### [389. Find the Difference](https://leetcode.com/problems/find-the-difference/)

## Medium:

### [137. Single Number II](https://leetcode.com/problems/single-number-ii/)

### [260. Single Number III](https://leetcode.com/problems/single-number-iii/)

### Two Single Numbers:

**Question:** In a non-empty array of numbers, every number appears exactly twice except two numbers that appear only once. Find the two numbers that appear only once.



### 

额外的题目:

### [1256. Encode Number](https://leetcode.com/problems/encode-number/)

### [338. Counting Bits](https://leetcode.com/problems/counting-bits/)

### [201. Bitwise AND of Numbers Range](https://leetcode.com/problems/bitwise-and-of-numbers-range/)

### [477. Total Hamming Distance](https://leetcode.com/problems/total-hamming-distance/)



## Hard:



## The problem I  struggle with:

* * * 




