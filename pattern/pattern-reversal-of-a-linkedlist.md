# 6. Reversal of A LinkedList

## Summary:

In-place Reversal of a LinkedList pattern describes an efficient way to solve the problem.

* Use dummy node for easy manipulation







## Easy:

### [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

Time complexity： O\(N\) . Space Complexity: O\(1\)

```text
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode cur = head;
        
        while(cur != null){
            //store next pointer
            ListNode next = cur.next;
            //connect cur pointer with prev pointer
            cur.next = prev;
            prev = cur;
            cur = next; 
        }
        return prev;
    }
}
```

### 



## Medium:

### [92. Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/)

### [24. Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)

### [1721. Swapping Nodes in a Linked List](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/)

### [61. Rotate List](https://leetcode.com/problems/rotate-list/)

### Reverse alternating K-element Sub-list \(medium\) :

**Question:** Given the head of a LinkedList and a number ‘k’, reverse every alternating ‘k’ sized sub-list starting from the head.

If, in the end, you are left with a sub-list with less than ‘k’ elements, reverse it too.  


**Answer:**





## Hard:

### [25. Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)

### 



## The problem I  struggle with:

* 92
* 24， 写出来了 但是不是很熟悉
* 




