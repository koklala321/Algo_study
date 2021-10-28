# Binary Tree Level Order Traversal



Given the `root` of a binary tree, return _the level order traversal of its nodes' values_. (i.e., from left to right, level by level).

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg)

```
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]
```

**Example 2:**

```
Input: root = [1]
Output: [[1]]
```

**Example 3:**

```
Input: root = []
Output: []
```

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[0, 2000]`.
* `-1000 <= Node.val <= 1000`

## Solution(BFS)

BFS key : make a deque (queue) , always start from the head of queue (FIFO)

```python
// Some code# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
import collections
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        
        output = []
        queue = collections.deque([root])
        
        
        while queue:
            temp = []
            #note to myself, the len(queue) is recalculated everytime when entering while loop
            for i in range(len(queue)):
                node = queue.popleft()
                temp.append(node.val)
                if node.left:
                    queue.append(node.left)
                if node.right:    
                    queue.append(node.right)
            output.append(temp)
        
        return output
    
```
