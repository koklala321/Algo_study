# Unique path



A robot is located at the top-left corner of a `m x n` grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2018/10/22/robot\_maze.png)

```
Input: m = 3, n = 7
Output: 28
```

**Example 2:**

```
Input: m = 3, n = 2
Output: 3
Explanation:
From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Down -> Down
2. Down -> Down -> Right
3. Down -> Right -> Down
```

**Example 3:**

```
Input: m = 7, n = 3
Output: 28
```

**Example 4:**

```
Input: m = 3, n = 3
Output: 6
```

&#x20;

**Constraints:**

* `1 <= m, n <= 100`
* It's guaranteed that the answer will be less than or equal to `2 * 109`.

## Solution

```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        dp = [[1] * n for _ in range(m)]
        for i in range(1,m):
            for j in range(1,n):
                dp[i][j] = dp[i-1][j] + dp[i][j-1]            
        return dp[-1][-1]
        
    
        '''
        dfs -- time limit exceed
        
        self.total = 0
        
        def dfs(x,y,m,n):
            if x == m-1 and y==n-1:
                self.total+=1
                return
            if x < m:
                dfs(x+1,y,m,n)
            if y < n:
                dfs(x,y+1,m,n)
                
            return
        
        dfs(0,0,m,n)
               
        return self.total
        '''
```
