# Symmetric Tree

Given the `root` of a binary tree, _check whether it is a mirror of itself_ (i.e., symmetric around its center).

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/02/19/symtree1.jpg)

```
Input: root = [1,2,2,3,4,4,3]
Output: true
```

**Example 2:**

![](https://assets.leetcode.com/uploads/2021/02/19/symtree2.jpg)

```
Input: root = [1,2,2,null,3,null,3]
Output: false
```

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[1, 1000]`.
* `-100 <= Node.val <= 100`

## Solution(DFS)



```python

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        if not root:
            return True
        return self.isMirror(root.left,root.right)
    
    def isMirror(self,left,right):
        if left is None and right is None:
            return True
        if left is None or right is None:
            return False
        
        if left.val == right.val:
            a=self.isMirror(left.left,right.right)
            b=self.isMirror(left.right,right.left)
            return a and b
        else:
            return False
    
```
