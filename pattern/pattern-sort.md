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
* We pick a random element  and partition the array, such that all numbers that are less than the partitioning element come before all elements that are greater than it. The partitioning can be performed efficiently through a series of swaps.
* Since the partitioned element is not guaranteed to be the median , our sorting could be  very slow. This is the reason for the O\(N^2\) worst case runtime

```text
import java.util.*;

class Program {
  public static int[] quickSort(int[] array) {
    quickSort(array,0,array.length -1);
    return array;
  }
	
	public static void quickSort(int[] array, int startIdx, int endIdx){
		if(startIdx >= endIdx)
			return ;
		
		int pivotIdx =  startIdx;
		int leftIdx = startIdx + 1;
		int rightIdx = endIdx;
		
		while(rightIdx >= leftIdx){
			if(array[leftIdx] > array[pivotIdx] && array[rightIdx] < array[pivotIdx]){
				swap(leftIdx,rightIdx,array);
			}
			if(array[leftIdx] <= array[pivotIdx]) leftIdx += 1;
			
			if(array[rightIdx] >= array[pivotIdx]) rightIdx -= 1;
			
		}
			swap(pivotIdx,rightIdx,array);
			boolean leftSubarrayIsSmaller  = rightIdx -1 - startIdx < endIdx - (rightIdx + 1);
			
			if(leftSubarrayIsSmaller ){
				  quickSort(array,startIdx,rightIdx -1 );
				  quickSort(array,rightIdx +1,endIdx );
			}else{
				 quickSort(array,rightIdx +1,endIdx );
				 quickSort(array,startIdx,rightIdx -1 );
				
			}
	}
	
	public static void swap(int i, int j, int[] array){
		int temp = array[j];
		array[j] = array[i];
		array[i] = temp;
	}
}

```

### Heap Sort:

* _Time Complexity:_  O\(Nlog\(N\)\)---&gt; Average and Best case  ,  Worst Case: O\(N^2\)
* _Space Complexity:_ O\(n\):
* Heap information:
  * currentNode --&gt; i ,  childOne --&gt; 2i +1, child Two ---&gt; 2i +2;
  * parent Node --&gt; floor\(\(i -1\)/2\) 
  * Build heap method: turn an array to array representation of Heap
  * Sift Up method:  Once we add to the array we need to sift up to add to correct location
    * It continuously swap the current node with parent node until  it at correct location
    * This is a min heap



![](../.gitbook/assets/image%20%2848%29.png)

* Sift Down method:
  * swap with child element
  * We choose a smallest child node and swap with it
  * Here is implementation for min Heap:

![](../.gitbook/assets/image%20%2845%29.png)

* Remove: 
  * Swap root value with final value of the array
  * Sift  down to rebuild the heap
* Algorithm:
  * Transform entire array into max heap, we do not create extra place to store as heap
  * Take the head number and swap at final value of the unsorted array
  * Then we rebuild max heap 

```text
import java.util.*;

class Program {
  public static int[] heapSort(int[] array) {
		buildMaxHeap(array);
		//swap last index in the heap with the root value and rebuild the heap
    for(int endIdx =  array.length -1; endIdx > 0; endIdx--){
			swap(0,endIdx,array);
			//array is smaller,
			siftDown(0,endIdx -1, array);
			
		}
    return array;
  }
	
	
	public static void siftDown(int currentIdx, int endIdx, int[] heap){
		int childOneIdx = currentIdx * 2 +1;
		while(childOneIdx <= endIdx){
			int childTwoIdx =  currentIdx * 2 +2 <= endIdx ? currentIdx * 2 + 2 : -1;
			int idxToSwap;
			if(childTwoIdx != -1 && heap[childTwoIdx] > heap[childOneIdx]){
				idxToSwap = childTwoIdx;
			}else{
				idxToSwap = childOneIdx;
			}
			
			if(heap[idxToSwap] > heap[currentIdx]){
				swap(currentIdx, idxToSwap,heap);
				currentIdx = idxToSwap;
				childOneIdx = currentIdx * 2 +1;
			}else{
				return;
			}
		}
	}
	public static void  buildMaxHeap(int [] array){
		int firstParentIdx = (array.length - 2) /2;
		
		for(int currentIdx = firstParentIdx; currentIdx >= 0; currentIdx --){
			siftDown(currentIdx,array.length -1, array);
			
		}
		
	}
	public static void swap(int i, int j, int[] array){
		int temp =  array[j];
		array[j] = array[i];
		array[i] = temp;
	}
}

```

### Radix Sort:

* Time  Complexity: O\(d\*\(n+b\)\)  , n is the number of elements and b is base for representing numbers.
* It is a sorting algorithm for integers that takes advantage of the fact that integers have a finite number of bits, In radix sort, we iterate through each digit of the number, grouping numbers by each digit,
*  For example, If we have an array of integers, we might first sort by the first digit, so that the Os are grouped together. Then we sort each of these groupings by the next digit. We repeat this process sorting by each subsequent digit, until finally the whole array is sorted.
* Algorithm:

  * Another is current sorted array
  * One is counts array:
    * We first put the count of digit at each location, , When we put the element to the sorted array based on counts index, we first minus one and that is the target index we need to put.

![](../.gitbook/assets/image%20%2847%29.png)



Then we need to add  i -1  to i and update it value:

![](../.gitbook/assets/image%20%2846%29.png)



### Merge Sort:

* Time Complexity: O\(NlogN\) average and worst case,best case,
* Space Complexity:
* It divides the array in half , sorts each of those halves, and then merges them back together. Each of those halves has the same sorting algorithm applied to it. Eventually, you are merging just two single element arrays. It is the merge part that does all that heavy lifting
* Algorithm:

```text

class Program {
  public static int[] mergeSort(int[] array) {
   if(array.length <= 1)
		 return array;
		
		int middleIdx = array.length /2;
		int [] leftHalf =  Arrays.copyOfRange(array, 0 ,middleIdx);
		int [] rightHalf =  Arrays.copyOfRange(array, middleIdx ,array.length);
    return mergerSortedArrays(mergeSort(leftHalf),mergeSort(rightHalf));
  }
	
	public static int[]  mergerSortedArrays(int[] leftHalf, int [] rightHalf){
		int [] sortedArray = new int[leftHalf.length + rightHalf.length];
		
		int k = 0;
		int i = 0;
		int  j = 0;
		
		while(i < leftHalf.length && j < rightHalf.length){
			if(leftHalf[i] <= rightHalf[j]){
				sortedArray[k++] = leftHalf[i++];
			}else{
				sortedArray[k++] = rightHalf[j++];
			}
		}
		
		while(i < leftHalf.length){
			sortedArray[k++] = leftHalf[i++];
		}
		while(j < rightHalf.length){
			sortedArray[k++] = rightHalf[j++];
		}
		
		return sortedArray;
		
	}
}

```



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
* **quick sort**
* **Heap Sort:**

### 

### 







