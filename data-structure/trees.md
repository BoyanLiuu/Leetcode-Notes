# Trees

## Notes:

### 怎么找出来 inorder Successor:

* [https://leetcode.com/problems/inorder-successor-in-bst/](https://leetcode.com/problems/inorder-successor-in-bst/)

1. 使用 inorder array找出来数值
2. binary tree 里包含parent field 的情况下
   1. 如果当前node 的right tree 存在， 我们就找 right tree 的 left most node
   2. 如果当前node right tree 不存在， 我们就找 getRightmostParent·

```
public BinaryTree findSuccessor(BinaryTree tree, BinaryTree node) {
		System.out.println(node.right != null);
    if(node.right != null) return getLeftmostChild(node.right);
    return getRightmostParent(node);
  }
	
	
	public BinaryTree getLeftmostChild(BinaryTree node){
		BinaryTree currentNode =  node;
		
		while(currentNode.left != null){
			currentNode =  currentNode.left;
		}
		
		return currentNode;
	}
	
		public BinaryTree getRightmostParent(BinaryTree node){
			BinaryTree currentNode =  node;

			while(currentNode.parent != null && currentNode.parent.right == currentNode){
				currentNode =  currentNode.parent;
			}

			return currentNode.parent;
		}
```

## Medium

* [572. Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/)

