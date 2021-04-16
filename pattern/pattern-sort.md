# 17. Classic Sort

## Summary:

* In place sort: A sort that do not require extra space:
  * 
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

* _Time Complexity:_  O\(N^2\)---&gt; Average and worst case  , Best case: O\(N\)
* _Space Complexity:_ O\(1\):
* We start at the beginning of the array and swap the first two elements if the first is greater than the second, Then we go to the next pair, and so on

```text
  public static int[] bubbleSort(int[] array) {
    for(int i =0; i < array.length; i++){
			for(int j  =i+1; j < array.length;j++){
				if(array[j] <array[i]){
					int temp = array[i];
					array[i] =array[j];
					array[j] =temp;
				}
				
			}
			
		}
    return array;
  }
```

### Insertion Sort:

* Time Complexity:  O\(N^2\)---&gt; Average and worst case  , Best case: O\(N\)
* _Space Complexity_: O\(1\):
* Compare the current element to its predecessor, If the  key is smaller than the predecessor, compare it to the elements before. Move the greater elements one position up to make space for the swapped element

```text


public static int[] insertionSort(int[] array) {
		if(array.length == 0)
			return array;
		for(int i = 1; i < array.length; i++){
				int j = i;
			while(j > 0 && array[j] < array[j -1]){
				 swap(j,j-1,array);
				j -= 1;
			}
			
		}
		return array;
  }
	
	public static void swap (int i, int j, int[] array){
		int temp =  array[j];
		array[j] = array[i];
		array[i] = temp;
	}


```

### Selection Sort:

* _Time Complexity:_  O\(N^2\)---&gt; Average and worst case  , Best case
* _Space Complexity:_ O\(1\):
* It is the child's algorithm: simple , but inefficient, Find the smallest element using a linear scan and move it to the front. Then find the second smallest and move it again doing a linear scan. Continue doing this until all the elements are in places

```text
  public static int[] selectionSort(int[] array) {
		int startIdx =0;

		while(startIdx != array.length -1 ){
					int smallest = array[startIdx];
					int smallestIndex = startIdx;
					for(int i =startIdx+1; i < array.length; i++){
						if(array[i] < smallest){
							smallest =array[i] ;
							smallestIndex = i;
						}
					}
				//swap 
			  swap(startIdx,smallestIndex,array);
			  startIdx += 1;
		}

    return array;
  }
	
		public static void swap (int i, int j, int[] array){
		int temp =  array[j];
		array[j] = array[i];
		array[i] = temp;
	}
```

### Quick Sort:

* _Time Complexity:_  O\(Nlog\(N\)\)---&gt; Average and Best case  ,  Worst Case: O\(N^2\)
* _Space Complexity:_ O\(n\):

### Heap Sort:

* _Time Complexity:_  O\(Nlog\(N\)\)---&gt; Average and Best case  ,  Worst Case: O\(N^2\)
* _Space Complexity:_ O\(n\):

### Radix Sort:



### Merge Sort:

* Top down Merge Sort:
* Bottom Up Merge Sort



## Additional Question:

### [75. Sort Colors](https://leetcode.com/problems/sort-colors/)

### Count Inversions:

![](../.gitbook/assets/image%20%2843%29.png)

**Answer:**

\*\*\*\*

\*\*\*\*

\*\*\*\*

## **Problem I struggle**

* **Insertion Sort**

### 

### 







