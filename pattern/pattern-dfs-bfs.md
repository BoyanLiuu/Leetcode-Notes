# 7. DFS/BFS

## Summary:

### BFS:

* Any problem involving the traversal of a tree in a level-by-level order can be efficiently solved using this approach. We will use a **Queue** to keep track of all the nodes of a level before we jump onto the next level.
* This also means that the space complexity of the algorithm will be **O\(W\)**, where ‘W’ is the maximum number of nodes on any level.

### DFS:

* We will be using recursion \(or we can also use a stack for the iterative approach\) to keep track of all the previous \(parent\) nodes while traversing. This also means that the space complexity of the algorithm will be O\(H\), where ‘H’ is the maximum height of the tree
* There are three different orders for traversing a tree using DFS
  * Preorder Traversal: root -&gt; left-&gt;right
  * Inorder Traversal_: left-&gt;root-&gt;right_
  * Postorder Traversal： left-&gt;right-&gt;root
* Space complexity and Time complexity:
  * _Time Complexity_: we visit each node exactly once, thus the time complexity is O\(N\), where N is the number of nodes.
  * _Space Complexity_: in the worst case, the tree is completely unbalanced, e.g. each node has only one child node, the recursion call would occur NN times \(the height of the tree\), therefore the storage to keep the call stack would be O\(N\). But in the best case \(the tree is completely balanced\), the height of the tree would be log\(N\). Therefore, the space complexity in this case would be O\(log\(N\)\).
* 通常是使用 Recursion DFS，    _Remember remove the current node from the path to backtrack,  we need to remove the current node while we are going up the recursive call stack._

#### Preorder Traversal:

_Iterative:， This is similar with BFS , just change stack_



```text
public void traversePreOrderWithoutRecursion() {
    Stack<Node> stack = new Stack<Node>();
    Node current = root;
    stack.push(root);
    while(!stack.isEmpty()) {
        current = stack.pop();
        visit(current.value);
        
        if(current.right != null) {
            stack.push(current.right);
        }    
        if(current.left != null) {
            stack.push(current.left);
        }
    }        
}
```

_Recursive：_

```text
public void traversePreOrder(Node node) {
    if (node != null) {
        visit(node.value);
        traversePreOrder(node.left);
        traversePreOrder(node.right);
    }
}
```

\_\_

#### Inorder Traversal:

_Iterative:_

```text
public void traverseInOrderWithoutRecursion() {
    Stack<Node> stack = new Stack<Node>();
    Node current = root;
    stack.push(root);
    while(! stack.isEmpty()) {
        // traverse left
        while(current.left != null) {
            current = current.left;                
            stack.push(current);                
        }
        //traverse root
        current = stack.pop();
        visit(current.value);
        //traverse right
        if(current.right != null) {
            current = current.right;                
            stack.push(current);
        }
    }
}
```

_Recursive:_

```text
public void traverseInOrder(Node node) {
    if (node != null) {
        traverseInOrder(node.left);
        visit(node.value);
        traverseInOrder(node.right);
    }
}
```

\_\_

#### Postorder Traversal:

_Iterative:_

* Push root node in stack
* While stack is not empty
  * Check if we already traversed left and right subtree
  * If not then push right child and left child onto stack

__

```text
public void traversePostOrderWithoutRecursion() {
    Stack<Node> stack = new Stack<Node>();
    Node prev = root;
    Node current = root;
    stack.push(root);

    while (!stack.isEmpty()) {
        current = stack.peek();
        boolean hasChild = (current.left != null || current.right != null);
        boolean isPrevLastChild = (prev == current.right || 
          (prev == current.left && current.right == null));

        if (!hasChild || isPrevLastChild) {
            current = stack.pop();
            visit(current.value);
            prev = current;
        } else {
            if (current.right != null) {
                stack.push(current.right);
            }
            if (current.left != null) {
                stack.push(current.left);
            }
        }
    }   
}
```

_Recursive:_

```text
public void traversePostOrder(Node node) {
    if (node != null) {
        traversePostOrder(node.left);
        traversePostOrder(node.right);
        visit(node.value);
    }
}
```

### DFS VS BFS:

**Why we sometimes choose DFS over BFS?**

For example , 113 path sum II

 However, note that the problem statement actually asks us to return a list of all the paths that add up to a particular sum. Breadth first search moves one level at a time. That means, we would have to maintain the pathNodes lists for all the paths till a particular level/depth at the same time.



Say we are at the level 10 in the tree and that level has e.g. 20 nodes. BFS uses a queue for processing the nodes. Along with 20 nodes in the queue, we would also need to maintain 20 different pathNodes lists since there is no backtracking here. That is too much of a space overhead.



_The good thing about depth first search is that it uses recursion for processing one branch at a time and once we are done processing the nodes of a particular branch, we pop them from the pathNodes list thus saving on space._ At a time, this list would only contain all the nodes in a single branch of the tree and nothing more. Had the problem statement asked us the total number of paths that add up to a particular sum \(root to leaf\), then breadth first search would be an equally viable approach.

\_\_





## Easy:

### BFS: None

### DFS: 

#### [112. Path Sum](https://leetcode.com/problems/path-sum/)

* DFS题型 基本模板

#### [104: Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

#### 

#### 



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
  * Level Order Successor:
    * Question: Given a binary tree and a node, find the level order successor of the given node in the tree. The level order successor is the node that appears right after the given node in the level order traversal.
  * [116. Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)
  * \*\*\*\*[117. Populating Next Right Pointers in Each Node II](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/)
    * 116的答案可以解答117。。
  * Connect Level Order Siblings
  * \_\_[_199 Binary Tree Right Side View_](https://leetcode.com/problems/binary-tree-right-side-view/)\_\_
* 还有一种题型不知道算不算 bfs 或者是额外的题型
  * 200 Number of Island:
  * 994:Rotting Oranges:
  * Tree Boundary:

#### 

#### 





### DFS:

#### [113. Path Sum II](https://leetcode.com/problems/path-sum-ii/)

```text
class Solution {
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        List<List<Integer>> allPaths = new ArrayList<>();
        List<Integer> currentPath = new ArrayList<Integer>();
        helper(root, sum, currentPath, allPaths);
        return allPaths;
        
    }
  private static void helper(TreeNode currentNode, int sum, List<Integer> currentPath,
      List<List<Integer>> allPaths) {
    if (currentNode == null)
      return;

    // add the current node to the path
    currentPath.add(currentNode.val);

    // if the current node is a leaf and its value is equal to sum, save the current path
    if (currentNode.val == sum && currentNode.left == null && currentNode.right == null) {
      allPaths.add(new ArrayList<Integer>(currentPath));
    } else {
      // traverse the left sub-tree
     helper(currentNode.left, sum - currentNode.val, currentPath, allPaths);
      // traverse the right sub-tree
      helper(currentNode.right, sum - currentNode.val, currentPath, allPaths);
    }

    // remove the current node from the path to backtrack, 
    // we need to remove the current node while we are going up the recursive call stack.
    currentPath.remove(currentPath.size() - 1);
  }
}
```

* _Time Complexity:_ O\(N^2\),where ‘N’ is the total number of nodes in the tree. This is due to the fact that we traverse each node once \(which will take O\(N\)\), and for every leaf node, we might have to store its path \(by making a copy of the current path\) which will take O\(N\). The tighter time complexity is O\(NLOGN\). From a balanced binary tree, The depth is O\(log N\) so 
* _Space Complexity:If we ignore the space required for the allPaths list, the space complexity of the above algorithm will be O\(N\) in the worst case. This space will be used to store the recursion stack. The worst-case will happen when the given tree is a linked list \(i.e., every node has only one child\). If we do not ignore allPaths list, The space complexity is O\(NlogN\)_

\_\_

#### [129. Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/)

**Question:** Given a binary tree where each node can only have a digit \(0-9\) value, each root-to-leaf path will represent a number. Find the total sum of all the numbers represented by all paths.

![](../.gitbook/assets/image%20%2827%29.png)

**Answer:** 

Time complexity: O\(N\), Space Complexity: O\(N\)

```text
  public static int findSumOfPathNumbers(TreeNode root) {
    return findRootToLeafPathNumbers(root, 0);
  }

  private static int findRootToLeafPathNumbers(TreeNode currentNode, int pathSum) {
    if (currentNode == null)
      return 0;

    // calculate the path number of the current node
    pathSum = 10 * pathSum + currentNode.val;

    // if the current node is a leaf, return the current path sum.
    if (currentNode.left == null && currentNode.right == null) {
      return pathSum;
    }

    // traverse the left and the right sub-tree
    return findRootToLeafPathNumbers(currentNode.left, pathSum) +
           findRootToLeafPathNumbers(currentNode.right, pathSum);
  }
```

#### Path With Given Sequence

**Question:** Given a binary tree and a number sequence, find if the sequence is present as a root-to-leaf path in the given tree. ![](../.gitbook/assets/image%20%2826%29.png) 

#### 

#### [437. Path Sum III](https://leetcode.com/problems/path-sum-iii/)  

* There will be four differences than the  112 
  * We will keep track of the current path in a list which will be passed to every recursive call.
  * Whenever we traverse a node we will do two things:
    * Add the current node to the current path.
    * As we added a new node to the current path, we should find the sums of all sub-paths ending at the current node. If the sum of any sub-path is equal to ‘S’ we will increment our path count.
  * We will traverse all paths and will not stop processing after finding the first path.
  * Remove the current node from the current path before returning from the function. This is needed to Backtrack while we are going up the recursive call stack to process other paths.

#### [543：Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)

#### 



### Hard:

#### [124. Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)

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





## Problem I struggle with:

* 199 
* 112
* 437

