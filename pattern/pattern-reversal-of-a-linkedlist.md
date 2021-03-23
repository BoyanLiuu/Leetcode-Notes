# 6. Reversal of A LinkedList

## Summary:

In-place Reversal of a LinkedList pattern describes an efficient way to solve the problem.

* Use dummy node for easy manipulation







## Easy:

### [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

Time complexity: O\(N\). Space Complexity: O\(1\)

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

stunning  recursive  solution:

```text
public ListNode reverseList(ListNode head) {
    if (head == null || head.next == null) return head;
    
    ListNode p = reverseList(head.next); // passing back head pointer using p
    head.next.next = head; // turning the pointer direction
    head.next = null; // cutoff current.next, necessary for tail pointer.
    return p;
}
```



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

*  It  similar to Reverse a Sub-list. The only difference is that we have to reverse all the sub-lists. We can use the same approach, starting with the first sub-list \(i.e. p=1, q=k\) and keep reversing all the sublists of size ‘k’.

### 



## The problem I  struggle with:

* 92
* 24， 写出来了 但是不是很熟悉
* Reverse alternating K-element Sub-list





