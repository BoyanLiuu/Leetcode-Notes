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

## Populare idea:

* Two pointers
  * 88
  * 1
* Sliding Windows
* Prefix Sum

## Easy:

* [88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)
* [1. Two Sum](https://leetcode.com/problems/two-sum/)
* [387. First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)

## Medium:

* [704.Binary Search ](https://leetcode.com/problems/binary-search/)
* [238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)
* [702. Search in a Sorted Array of Unknown Size](https://leetcode.com/problems/search-in-a-sorted-array-of-unknown-size/)
* [33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
* [81. Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)
* [153. Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
* [189. Rotate Array](https://leetcode.com/problems/rotate-array/)
* [34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
* [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)
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

## The question that I am having trouble:



