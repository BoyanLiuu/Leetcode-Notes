# 2. Two Pointer

## Summary:

* A great pattern to **`find a set of elements` that fulfill certain constraints in `sorted arrays`/`Linked Lists`** 
  * Types:  **`balancing values`**,  **`in-place switching`**,
    *  but **don't feel like it's limited to these functionalities**, be creative!
* \*\*\*\*🗝 **Key Points:** ------------------------------------------------------------------
  * Where to place the pointers initially\(or to not place them\)?
  * Under what case should we move the pointers?
  * When and where to update the pointers?
  * **-------------------------------------------------------------------------**

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

* sadsa

## Medium:

* [763. Partition Labels](https://leetcode.com/problems/partition-labels/)

## Difficult:



