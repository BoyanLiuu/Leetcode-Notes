# 7. DFS/BFS

## Summary:

### BFS:

* Any problem involving the traversal of a tree in a level-by-level order can be efficiently solved using this approach. We will use a **Queue** to keep track of all the nodes of a level before we jump onto the next level.
* This also means that the space complexity of the algorithm will be **O\(W\)**, where ‘W’ is the maximum number of nodes on any level.

## Easy:

### BFS:

#### Level Order Successor:

**Question:** Given a binary tree and a node, find the level order successor of the given node in the tree. The level order successor is the node that appears right after the given node in the level order traversal.

![](../.gitbook/assets/image%20%2824%29.png)

**Answer:**

#### Connect Level Order Siblings



#### 







#### 



## Medium:

### BFS:

#### [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)

```text
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> levels = new ArrayList<List<Integer>>();
        if (root == null) return levels;
        
       Deque<TreeNode> queue = new ArrayDeque<>();
       queue.offer(root);
        
        while (!queue.isEmpty()) {
            int size =  queue.size();
            List<Integer> temp = new ArrayList<>();
            for (int i = 0; i <size; i++) {
                TreeNode node = queue.poll();
                temp.add(node.val);
                // process child nodes for the next level
                if (node.left != null) 
                    queue.offer(node.left);    
                if (node.right != null) 
                    queue.offer(node.right);
            }   
            levels.add(temp);
        }
        return levels;
    }
```

* Time complexity: O\(N\),where ‘N’ is the total number of nodes in the tree. This is due to the fact that we traverse each node once.
* **完全类似的题目**
  * [637. Average of Levels in Binary Tree](https://leetcode.com/problems/average-of-levels-in-binary-tree/)
  * \*\*\*\*[107. Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)
  * [103. Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)
  * \*\*\*\*[111. Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/)
    * very similar idea, Since we are using bfs, so the first time we meet a leaf, we could just return that level. So we using additional queue to keep track of levels

#### [116. Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

#### [117. Populating Next Right Pointers in Each Node II](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/)

#### [199 Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)





### DFS:



#### 

#### 

#### 



















* [994. Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)
  * We use a delimiter \(i.e. \(row=-1, col=-1\)\) in the queue to separate cells on different levels.
* 200. Number of Islands
* [139. Word Break](https://leetcode.com/problems/word-break/)
* [103. Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

## Code snippets:

* How to traverse 4 direction in an array

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
