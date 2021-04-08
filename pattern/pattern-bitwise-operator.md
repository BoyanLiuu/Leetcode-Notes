# 11. Bitwise Operator

## Summary:

* _**Use Bit manipulation to avoid Integer overflow**_
* How to move bit:
  * &lt;&lt;   double it,  &gt;&gt; divide it

```text
int rightmostSetBit =1;
rightmostSetBit = rightmostSetBit << 1;
```

* How to get all the bit for an base -10 integer

```text
        int temp =1;
        while( N  > 0){
            System.out.println(N & temp);
            N = N >>1;
        }
```

* How to convert base-10 number into bits string
  * `Integer.toBinaryString`
* XOR: 

  * It is true if one and only one input bit is true

  ![](../.gitbook/assets/image%20%2833%29.png) 

  * It is Associative &  Commutative ![](../.gitbook/assets/image%20%2832%29.png) 

* OR:    A \| B
* NOT: flips the input bit   ~ 0 = 1;
  * a ^\(~a\)    =1
  * ~0 :  0000   ===&gt; 1111, all ones
  * 









## Easy:

### [268. Missing Number](https://leetcode.com/problems/missing-number/)

* Space Complexity: O\(1\)
* Time Complexity: O\(N\)
* 类似的题目：
  * \*\*\*\*[**136. Single Number**](https://leetcode.com/problems/single-number/)\*\*\*\*

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

### 

### [1009. Complement of Base 10 Integer](https://leetcode.com/problems/complement-of-base-10-integer/)

* number ^ complement = all\_bits\_set
* number ^ number ^ complement = number ^ all\_bits\_set
* 0 ^ complement = number ^ all\_bits\_set  ====&gt; complement = number ^ all\_bits\_set
* So How do we get all bit set..
  * for example, number is 5 which is  0101  , all bits set  is 1111, 
  * We get 1111 from 2 ^3 -1 which is 7

```text
    public int bitwiseComplement(int N) {
        if(N==0){
            return 1;
        }
    // count number of total bits in 'num'
    int bitCount = 0;
    int n =N;
    while (n > 0) {
      bitCount++;
      n = n >> 1;
    }

    int all_bits_set = (int) Math.pow(2, bitCount) - 1;
    // from the solution description: complement = number ^ all_bits_set
    return N ^ all_bits_set;
    }
```

额外的题目

### [169. Majority Element](https://leetcode.com/problems/majority-element/)

### [191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)

### [476. Number Complement](https://leetcode.com/problems/number-complement/)

### [389. Find the Difference](https://leetcode.com/problems/find-the-difference/)

## Medium:

### [260. Single Number III](https://leetcode.com/problems/single-number-iii/)

* As we know that num1 and num2 are two different numbers, therefore, they should have at least one bit different between them. If a bit in n1xn2 is ‘1’, this means that num1 and num2 have different bits in that place, as we know that we can get ‘1’ only when we do XOR of two different bits, i.e.,
* We can take any bit which is ‘1’ in n1xn2 and partition all numbers in the given array into two groups based on that bit. One group will have all those numbers with that bit set to ‘0’ and the other with the bit set to ‘1’. This will ensure that num1 will be in one group and num2 will be in the other

```text
    public int[] singleNumber(int[] nums) {
         // get the XOR of the all the numbers
        int n1xn2 = 0;
        for (int num : nums) {
          n1xn2 ^= num;
        }

        // get the rightmost bit that is '1'
        int rightmostSetBit = 1;
        while ((rightmostSetBit & n1xn2) == 0) {
          rightmostSetBit = rightmostSetBit << 1;
        }
        int num1 = 0, num2 = 0;
        for (int num : nums) {
          if ((num & rightmostSetBit) != 0) // the bit is set
            num1 ^= num;
          else // the bit is not set
            num2 ^= num;
        }
        return new int[] { num1, num2 };
    }
```

额外的题目:

### [1256. Encode Number](https://leetcode.com/problems/encode-number/)

### [338. Counting Bits](https://leetcode.com/problems/counting-bits/)

### [201. Bitwise AND of Numbers Range](https://leetcode.com/problems/bitwise-and-of-numbers-range/)

### [477. Total Hamming Distance](https://leetcode.com/problems/total-hamming-distance/)

### [137. Single Number II](https://leetcode.com/problems/single-number-ii/)



## Hard:



## The problem I  struggle with:

* 137. Single Number II
* 1009. Complement of Base 10 Integer
* 




