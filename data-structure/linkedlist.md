# LinkedList

## 



## Medium:

* [2. Add Two Numbers](https://leetcode.com/problems/lru-cache/)
* [138. Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)





## Good code snippet:

* A concise way to write add number in linkedlist

```text
    ListNode dummyHead = new ListNode(0);
    ListNode p = l1, q = l2, curr = dummyHead;
    int carry = 0;
    while (p != null || q != null) {
        int x = (p != null) ? p.val : 0;
        int y = (q != null) ? q.val : 0;
        int sum = carry + x + y;
        carry = sum / 10;
        curr.next = new ListNode(sum % 10);
        curr = curr.next;
        if (p != null) p = p.next;
        if (q != null) q = q.next;
    }
    if (carry > 0) {
        curr.next = new ListNode(carry);
    }
```

* 


