# 3. Fast, Slow Pointer

## Summary:

* This approach is quite useful when dealing with Linked List or arrays.
* The fast pointer should catch the slow pointer once both the pointers are in a cyclic loop





## Easy:

### [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

* Imagine we have a slow and a fast pointer to traverse the LinkedList. In each iteration, the slow pointer moves one step and the fast pointer moves two steps. This gives us two conclusions:
  * If the LinkedList doesn’t have a cycle in it, the fast pointer will reach the end of the LinkedList before the slow pointer to reveal that there is no cycle in the LinkedList.
  * The slow pointer will never be able to catch up to the fast pointer if there is no cycle in the LinkedList.

### [876. Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

* Because we return the second middle node. So we use  `fast !=null && fast.next != null`

### [234. Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)

* First solution, copy into arraylist and use two pointer
* Second Solution, Reverse second part
  * Find head of second part
  * Reverse second part 
    *     `private ListNode reverseList(ListNode head) {`

              `ListNode prev = null;`

              `ListNode curr = head;`

              `while (curr != null) {`

                  `ListNode nextTemp = curr.next;`

                  `curr.next = prev;`

                  `prev = curr;`

                  `curr = nextTemp;`

              `}`

              `return prev;`

          `}`
  * Then in the end, we need to reverse back and get original linkedlist back

### 

## Medium:

### [142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)

* Once we find out the intersection point, we start iterateing from that point and head . When we meet , that is the node we return.

### [143. Reorder List](https://leetcode.com/problems/reorder-list/)

### [202. Happy Number](https://leetcode.com/problems/happy-number/)

### [457. Circular Array Loop](https://leetcode.com/problems/circular-array-loop/)

### [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

* use a while loop to move fast pointer at n step
* then when fast pointer move till null, the slow pointer represent the Node we want to remove. We can use a prev node to remove slow pointer

## Hard:



