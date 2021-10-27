# Validate Binary Search Tree



Given the `root` of a binary tree, _determine if it is a valid binary search tree (BST)_.

A **valid BST** is defined as follows:

* The left subtree of a node contains only nodes with keys **less than** the node's key.
* The right subtree of a node contains only nodes with keys **greater than** the node's key.
* Both the left and right subtrees must also be binary search trees.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/12/01/tree1.jpg)

```
Input: root = [2,1,3]
Output: true
```

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/12/01/tree2.jpg)

```
Input: root = [5,1,4,null,null,3,6]
Output: false
Explanation: The root node's value is 5 but its right child's value is 4.
```

&#x20;

**Constraints:**

* The number of nodes in the tree is in the range `[1, 104]`.
* `-231 <= Node.val <= 231 - 1`

## Solution(DFS)

\#the trick is to set and +inf and -inf as ceiling and floor for dfs function

```python
#DFS version
    def isValidBST(self, root: Optional[TreeNode]) -> bool:

        def dfs(node,lower,upper):
            if not node:
                return True
            
            if lower<node.val<upper:
                return dfs(node.left,lower,node.val) and dfs(node.right,node.val,upper)
            else:
                return False
            
        return dfs(root,lower = float("-inf"),upper = float("inf"))
        
```

## In order transversal

```python
class Solution:
    #inorder travelsal
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
            ans = []
            
            self.inorder(root,ans)
            
            for i in range(1,len(ans)):
                if ans[i-1]>=ans[i]:
                    return False
            
            return True
            
    def inorder(self,node,ans):
        if not node:
            return
        
        self.inorder(node.left,ans)
        ans.append(node.val)
        self.inorder(node.right,ans)
```
