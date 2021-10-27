# Surrounded Regions



Given an `m x n` matrix `board` containing `'X'` and `'O'`, _capture all regions that are 4-directionally surrounded by_ `'X'`.

A region is **captured** by flipping all `'O'`s into `'X'`s in that surrounded region.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/02/19/xogrid.jpg)

```
Input: board = [["X","X","X","X"],["X","O","O","X"],["X","X","O","X"],["X","O","X","X"]]
Output: [["X","X","X","X"],["X","X","X","X"],["X","X","X","X"],["X","O","X","X"]]
Explanation: Surrounded regions should not be on the border, which means that any 'O' on the border of the board are not flipped to 'X'. Any 'O' that is not on the border and it is not connected to an 'O' on the border will be flipped to 'X'. Two cells are connected if they are adjacent cells connected horizontally or vertically.
```

**Example 2:**

```
Input: board = [["X"]]
Output: [["X"]]
```

&#x20;

**Constraints:**

* `m == board.length`
* `n == board[i].length`
* `1 <= m, n <= 200`
* `board[i][j]` is `'X'` or `'O'`.

## Solution(DFS)

\#the trick of this question is to mark any O tile, and its adjacent O tile with a marker. The walk through whole 2d list and flip the remaining O tiles, and flip the marked tile back to X.

```python
class Solution:
    def solve(self, board: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        #credit to DBabichev, instead of figuring out how to validate if a cell is full surrouded by x without touch boarder, we can figure out all  O cell starting from boarder
        self.mrow,self.mcol,self.board = len(board),len(board[0]),board
        
        for i in range(self.mrow):
            self.dfs(i,0)
            self.dfs(i,self.mcol-1)
            
        for j in range(self.mcol):
            self.dfs(0,j)
            self.dfs(self.mrow-1,j)
        
        for i in range(self.mrow):
            for j in range(self.mcol):
                if self.board[i][j] =="T":
                    self.board[i][j] = "O"
                else:
                    self.board[i][j] = "X"
        
        
    def dfs(self,row,col):
        if row <0 or col <0 or row>=self.mrow or col>=self.mcol or self.board[row][col] != "O":
            return
        
        self.board[row][col] = "T"
        
        self.dfs(row+1,col)
        self.dfs(row-1,col)
        self.dfs(row,col+1)
        self.dfs(row,col-1)
                
```

## Solution(BFS)

use the deque data type to store the next tile to be processed

```python
import collections
class Solution:
    def solve(self, board: List[List[str]]) -> None:
        max_row = len(board)
        max_col = len(board[0])
        
        queue = collections.deque([])
        for r in range(max_row):
            for c in range(max_col):
                if (r in (0,max_row-1) or c in (0,max_col-1)) and board[r][c] == "O":
                    queue.append((r,c))
                    
        #print(queue)
        while queue:
            row,col = queue.popleft()
            #check sure next loop row/col is within range
            if 0<=row<max_row and 0<=col<max_col and board[row][col] == "O":
                board[row][col] = "T"
                queue.extend([(row-1,col),(row+1,col),(row,col-1),(row,col+1)]) 
        #print(board)       
        for r in range(max_row):
            for c in range(max_col):
                if board[r][c] != "T":
                    board[r][c] = "X"
                else:
                    board[r][c] = "O" 
```
