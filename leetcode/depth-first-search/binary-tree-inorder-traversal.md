# Binary Tree Inorder Traversal

Given the `root` of a binary tree, return _the inorder traversal of its nodes' values_.

 

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/09/15/inorder\_1.jpg)

```
Input: root = [1,null,2,3]
Output: [1,3,2]
```

**Example 2:**

```
Input: root = []
Output: []
```

**Example 3:**

```
Input: root = [1]
Output: [1]
```

**Example 4:**

![](https://assets.leetcode.com/uploads/2020/09/15/inorder\_5.jpg)

```
Input: root = [1,2]
Output: [2,1]
```

**Example 5:**

![](https://assets.leetcode.com/uploads/2020/09/15/inorder\_4.jpg)

```
Input: root = [1,null,2]
Output: [1,2]
```

 

**Constraints:**

* The number of nodes in the tree is in the range `[0, 100]`.
* `-100 <= Node.val <= 100`

## Solution(DFS)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
    ans = []
    self.dfs(root,ans)
    return ans
def dfs(self,node,ans):
    if node is None:
        return
    self.dfs(node.left,ans)
    ans.append(node.val)    
    self.dfs(node.right,ans)

```
