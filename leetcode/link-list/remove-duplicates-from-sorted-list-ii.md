# Remove Duplicates from Sorted List II

Given the `head` of a sorted linked list, _delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list_. Return _the linked list **sorted** as well_.

**Example 1:**![](https://assets.leetcode.com/uploads/2021/01/04/linkedlist1.jpg)

```
Input: head = [1,2,3,3,4,4,5]
Output: [1,2,5]
```

**Example 2:**![](https://assets.leetcode.com/uploads/2021/01/04/linkedlist2.jpg)

```
Input: head = [1,1,1,2,3]
Output: [2,3]
```

**Constraints:**

* The number of nodes in the list is in the range `[0, 300]`.
* `-100 <= Node.val <= 100`
* The list is guaranteed to be **sorted** in ascending order.

## Solution

The link list is already sorted,  so we need a pointer to store last valid element(pre) , and a pointer to store current element under checking (cur)

```python
def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
    #since the list is already sorted
    #we only have to check if cur node equal to next node, also remembering the previous node
    dummy = pre = cur = ListNode(-1)
    dummy.next = cur = head
    #pre is alway one step behind head
    #remember edge case like all node need to be deleted
    while cur and cur.next:
        if cur.val == cur.next.val:
            while cur and cur.next and cur.val == cur.next.val:
                cur = cur.next
            cur = cur.next
            pre.next = cur
        else:
            pre = pre.next
            cur = cur.next

    return dummy.next
```
