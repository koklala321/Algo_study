# Remove Linked List Elements



Given the `head` of a linked list and an integer `val`, remove all the nodes of the linked list that has `Node.val == val`, and return _the new head_.

**Example 1:**![](https://assets.leetcode.com/uploads/2021/03/06/removelinked-list.jpg)

```
Input: head = [1,2,6,3,4,5,6], val = 6
Output: [1,2,3,4,5]
```

**Example 2:**

```
Input: head = [], val = 1
Output: []
```

**Example 3:**

```
Input: head = [7,7,7,7], val = 7
Output: []
```

**Constraints:**

* The number of nodes in the list is in the range `[0, 104]`.
* `1 <= Node.val <= 50`
* `0 <= val <= 50`

## Solution(while loop)

```python
def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]: 
       #go through link list
    #if current node value 
    #create a dummy node?
    dummy= ListNode(0,next=head)
    cur = dummy
    while cur.next !=None:
        if cur.next.val == val:
            cur.next=cur.next.next
        else:
            cur=cur.next

    return dummy.next
```

## Solution(Recursion)

```python
def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
    #if current node is none, return none
    if not head:
        return head

    head.next = self.removeElements(head.next, val)
    #skip node
    if head.val == val:
        head = head.next

    return head
```
