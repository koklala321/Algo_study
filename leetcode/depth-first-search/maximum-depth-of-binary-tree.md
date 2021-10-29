# Maximum Depth of Binary Tree



Given the `root` of a binary tree, return _its maximum depth_.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/11/26/tmp-tree.jpg)

```
Input: root = [3,9,20,null,null,15,7]
Output: 3
```

**Example 2:**

```
Input: root = [1,null,2]
Output: 2
```

**Example 3:**

```
Input: root = []
Output: 0
```

**Example 4:**

```
Input: root = [0]
Output: 1
```

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[0, 104]`.
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
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        ans = self.dfs(root)
        return ans
        
    def dfs(self,node):
        l,r = 0,0
        
        if node.left is not None:
            l = self.dfs(node.left)
            
        if node.right is not None:
            r = self.dfs(node.right)
        
        #print(f"l is {l},r is {r}, node is {node}")
        if l >= r and node is not None:
            return 1+l
        elif r>l and node is not None:
            return 1+r
```
