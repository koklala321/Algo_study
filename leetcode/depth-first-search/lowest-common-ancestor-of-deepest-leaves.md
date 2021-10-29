# Lowest Common Ancestor of Deepest Leaves



Lowest Common Ancestor of Deepest LeavesMedium903700Add to ListShare

Given the `root` of a binary tree, return _the lowest common ancestor of its deepest leaves_.

Recall that:

* The node of a binary tree is a leaf if and only if it has no children
* The depth of the root of the tree is `0`. if the depth of a node is `d`, the depth of each of its children is `d + 1`.
* The lowest common ancestor of a set `S` of nodes, is the node `A` with the largest depth such that every node in `S` is in the subtree with root `A`.

&#x20;

**Example 1:**

![](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/01/sketch1.png)

```
Input: root = [3,5,1,6,2,0,8,null,null,7,4]
Output: [2,7,4]
Explanation: We return the node with value 2, colored in yellow in the diagram.
The nodes coloured in blue are the deepest leaf-nodes of the tree.
Note that nodes 6, 0, and 8 are also leaf nodes, but the depth of them is 2, but the depth of nodes 7 and 4 is 3.
```

**Example 2:**

```
Input: root = [1]
Output: [1]
Explanation: The root is the deepest node in the tree, and it's the lca of itself.
```

**Example 3:**

```
Input: root = [0,1,3,null,2]
Output: [2]
Explanation: The deepest leaf node in the tree is 2, the lca of one node is itself.
```

&#x20;

**Constraints:**

* The number of nodes in the tree will be in the range `[1, 1000]`.
* `0 <= Node.val <= 1000`
* The values of the nodes in the tree are **unique**.

## Solution(DFS)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def lcaDeepestLeaves(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
    
        def dfs(node):
            #base case, if node is None it is the bottom, start count from 0
            if not node:
                return (None,0)
            
            #check left side and right side node depth
            l,l_max = dfs(node.left)
            r,r_max = dfs(node.right)
            
            #if left side node is greater than right, use left side node as it is deeper
            if l_max > r_max:
                return (l,l_max+1)
            elif r_max > l_max:
                return (r,r_max+1)
            #***** if left and right depth is same, it is a lcs node
            else:
                return (node,l_max+1)
            
        return dfs(root)[0]

    '''
    this question is very similar to below quesion, use the same mindset
    https://leetcode.com/problems/maximum-depth-of-binary-tree/
    '''
```
