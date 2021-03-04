# Array

## Basic:

### Array Initialization

```text
int intArray[]; // declaring array
intArray  = new int[20]; // allocating memory

//When array size is already known:
int [] ary = new int[]{1,2,3,4,5};
```

### Array Clone

```text
int intArray[][] =  {{1,2,3}.{4,5}}
int cloneArray [][] = intArray.clone();
```

### Array Converting:

* How to convert Other data structure to array

```text
// Convert heap to array
maxHeap.toArray(new int[k][2]); 
```

* 
### ArrayDeque in Java

* It apply resizable array, and implementation of the Deque interface
* It allow users to add or remove an element from both the sides of the queue
* They are not thread safe
* Null element are prohibited in the ArrayDeque
* When used as a stack, it is likely to be _faster than stack_
* When used as queue , _it is faster than Linkedlist_

```text
//Initialization
Deque<Integer> de_que = new ArrayDeque<Integer>(10);
de_que.size();
de_que.isEmpty();

//act like stack FILO
de_que.addFirst(100);
de_que.peek() // check head
de_que.poll（）// remove head

//act like queue FIFO
de_que.addLast(100);
de_que.peek() // check head
de_que.poll（） remove head
// loop dequeu
for(Integer cur: de_que){
}
```

## Useful Code snippet:

* Put character existence into array 

```text
int freq [] = new int[256];
for(int i = 0; i < s.length(); i ++)
    freq [s.charAt(i) - 'a'] ++;
    
```



## Populare idea:

* Two pointers
  * 1
  * 88
  * 283
* Sliding Windows
* Prefix Sum

## Easy:

* [1. Two Sum](https://leetcode.com/problems/two-sum/)
* [88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)
* [387. First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)
* [905. Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/)
* [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)

## Medium:

* [189. Rotate Array](https://leetcode.com/problems/rotate-array/)
* [704.Binary Search ](https://leetcode.com/problems/binary-search/)
* [238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)
* [702. Search in a Sorted Array of Unknown Size](https://leetcode.com/problems/search-in-a-sorted-array-of-unknown-size/)
* [33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
* [81. Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)
* [153. Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
* [189. Rotate Array](https://leetcode.com/problems/rotate-array/)
* [34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
* 
  Rearrange an array in maximum minimum form

  * Given an array, can you re-arrange the elements such that the first position will have the largest number, the second will have the smallest, the third will have the second-largest
  * Input: arr = {1, 2, 3, 4, 5}  , output: arr = {5, 1, 4, 2, 3}
  * Solution:
    * Use another array to strore your result and then to copy the result back to original array
    * Better solution:
      * Here, arr\[maxId\] is stored as the multiplier. Whereas, arr\[i\] is stored as the remainder. For example in the array, \[1, 2, 3, 4, 5, 6, 7, 8, 9\], the maxElem which is any element greater than the maximum element in the array, in this case, is 10 and 91 is stored at index 0. With 91, we can get the original element, 1, using the expression 91%10 as well as the new element, 9, using the expression 91/10.

```text
  public static void maxMin(int[] arr) {
    int maxIdx = arr.length - 1;
    int minIdx = 0;
    // store any element that is greater than the maximum element in the array 
    int maxElem = arr[maxIdx] + 1; 
    
    for( int i = 0; i < arr.length; i++) {
      // at even indices we will store maximum elements
      if (i % 2 == 0){  
        arr[i] += (arr[maxIdx] % maxElem ) * maxElem;
        maxIdx -= 1;
      }
      else { // at odd indices we will store minimum elements
        arr[i] += (arr[minIdx] % maxElem ) * maxElem;
        minIdx += 1;
      }
    }
    // dividing with maxElem to get original values.
    for( int i = 0; i < arr.length; i++) {
      arr[i] = arr[i] / maxElem;
    }
  }
```

* [215. Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)
* Best time to buy and sell stock
  * [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
  * [122. Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)
  * [123. Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)
  * [188. Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/)
  * [309. Best Time to Buy and Sell Stock with Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)
* Merge Intervals:
  * sdad
* Sort Array:
  * 

## Hard:

* [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
  * dynamic programming

## 

* 
## The question that I am having trouble:



