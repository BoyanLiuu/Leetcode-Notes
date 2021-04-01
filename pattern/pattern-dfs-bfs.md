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

\_\_

\_\_





## Easy:

### BFS: None

### DFS: 

#### [112. Path Sum](https://leetcode.com/problems/path-sum/)

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

#### [437. Path Sum III](https://leetcode.com/problems/path-sum-iii/)

#### [666. Path Sum IV](https://leetcode.com/problems/path-sum-iv/)

#### [129. Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/)

#### Path With Given Sequence

Question: Given a binary tree and a number sequence, find if the sequence is present as a root-to-leaf path in the given tree. ![](../.gitbook/assets/image%20%2826%29.png) 

Answer:

#### [543：Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)

#### [687. Longest Univalue Path](https://leetcode.com/problems/longest-univalue-path/)



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

