# 5. Merge Intervals

## Summary:

This pattern describes an efficient technique to deal with overlapping intervals. In a lot of problems involving intervals, we either need to find overlapping intervals or merge intervals if they overlap.

Given two intervals \(‘a’ and ‘b’\), there will be six different ways the two intervals can relate to each other:

![](../.gitbook/assets/image%20%2810%29.png)







## Easy:

### [252. Meeting Rooms](https://leetcode.com/problems/meeting-rooms/)

* Sort by start time, just like merge intervals idea
* Or sort by end time, 



## Medium:

### [56. Merge Intervals](https://leetcode.com/problems/merge-intervals/)

* Sort the intervals on the start time to ensure a.start &lt;= b.start
* If ‘a’ overlaps ‘b’ \(i.e. b.start &lt;= a.end\), we need to merge them into a new interval ‘c’ such that:

```text
c.start = a.start
c.end = max(a.end, b.end)
```

* We will keep repeating the above two steps to merge ‘c’ with the next interval if it overlaps with ‘c’.

```text
class Solution {
	public int[][] merge(int[][] intervals) {
		if (intervals.length <= 1)
			return intervals;

		// Sort by ascending starting point
		Arrays.sort(intervals, (i1, i2) -> i1[0] - i2[0]);

		List<int[]> result = new ArrayList<>();
		int[] newInterval = intervals[0];
		result.add(newInterval);
		for (int[] interval : intervals) {
			if (interval[0] <= newInterval[1])
                //adjust the end.
				newInterval[1] = Math.max(newInterval[1], interval[1]);
			else { // Disjoint intervals, add the new interval to the list      
				newInterval = interval;
                  result.add(newInterval);
	
			}
		}

		return result.toArray(new int[result.size()][]);
	}
}
```

### [986. Interval List Intersections](https://leetcode.com/problems/interval-list-intersections/)

* find   `start = max(a.start, b.start)    end = min(a.end, b.end)` 
* If start &gt; end , then we do not have overlapping interval, 
* move pointer where we have smallest end point.

### [57. Insert Interval](https://leetcode.com/problems/insert-interval/)

* When inserting a new interval in a sorted list, we need to first find the correct index where the new interval can be placed. In other words, we need to skip all the intervals which end before the start of the new interval.   `intervals[i].end < newInterval.start`
* Then follow an approach similar to Merge intervals to insert or merge new interval

### [435. Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)

### [253. Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/)

* A good test case: `[[4,5], [2,3], [2,4], [3,5]]`
* Algorithm:
  * Sort all the meetings on their start time.
  * Create a min-heap to store all the active meetings. This min-heap will also be used to find the active meeting with the smallest end time.
  * Iterate through all the meetings one by one to add them in the min-heap. Let’s say we are trying to schedule the meeting m1.
  * Since the min-heap contains all the active meetings, so before scheduling m1 we can remove all meetings from the heap that have ended before m1, i.e., remove all meetings from the heap that have an end time smaller than or equal to the start time of m1.
  * Now add m1 to the heap.
  * The heap will always have all the overlapping meetings, so we will need rooms for all of them. Keep a counter to remember the maximum size of the heap at any time which will be the minimum number of rooms needed.

### [452 Minimum Number of Arrows to burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)

### 

### 

### 

### 



## Hard:

### [759. Employee Free Time](https://leetcode.com/problems/employee-free-time/)

### Maximum CPU Load

Question: We are given a list of Jobs. Each job has a Start time, an End time, and a CPU load when it is running. Our goal is to find the maximum CPU load at any time if all the jobs are running on the same machine.

![](../.gitbook/assets/image%20%287%29.png)

![](../.gitbook/assets/image%20%289%29.png)

Solution:



## The problem I  struggle with:

* 57
* 986
* 252
* 253





