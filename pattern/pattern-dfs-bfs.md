# Pattern DFS/BFS

## Easy:

## Medium:

* [994. Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)
  * We use a delimiter \(i.e. \(row=-1, col=-1\)\) in the queue to separate cells on different levels.
* 200. Number of Islands

## Code snippets:

* How to traverse 4 direction in array

```text
int[][] directions = { {-1, 0}, {0, 1}, {1, 0}, {0, -1}};
        
for(int[] d : directions){
    int neighborRow = row + d[0];
    int neighborCol = col + d[1];
    if (neighborRow >= 0 && neighborRow < rows && 
       neighborCol >= 0 && neighborCol < cols) {
       //do work
       dfs(grid,neighborRow,neighborCol);

}       
}
```



* 
