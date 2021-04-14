# 17. Classic Sort

## Summary:

* How to write a collection sort 

```text
Collections.sort(letterList, (o1, o2) -> {
    String[] s1 = o1.split(" ");
    String[] s2 = o2.split(" ");
    int len1 = s1.length;
    int len2 = s2.length;
    for (int i = 1; i < Math.min(len1, len2); i++) {
        if (!s1[i].equals(s2[i])) {
            return s1[i].compareTo(s2[i]);
        }
    }
            return 0;
});
```

https://leetcode.com/problems/sort-an-array/discuss/492042/7-Sorting-Algorithms-\(quick-sort-top-downbottom-up-merge-sort-heap-sort-etc.\)/442531/

## All kinds of Sort

### Bubble Sort:

### Insertion Sort:

### Selection Sort:

### Quick Sort:

### Heap Sort:

### Merge Sort:

* Top down Merge Sort:
* Bottom Up Merge Sort



## Additional Question:

### [75. Sort Colors](https://leetcode.com/problems/sort-colors/)

### Count Inversions:

![](../../.gitbook/assets/image%20%2843%29.png)

**Answer:**

### 

### 







