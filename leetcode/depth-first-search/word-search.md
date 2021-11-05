# Word Search

Given an `m x n` grid of characters `board` and a string `word`, return `true` _if_ `word` _exists in the grid_.

The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/11/04/word2.jpg)

```
Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
Output: true
```

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/11/04/word-1.jpg)

```
Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "SEE"
Output: true
```

**Example 3:**

![](https://assets.leetcode.com/uploads/2020/10/15/word3.jpg)

```
Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCB"
Output: false
```

&#x20;

**Constraints:**

* `m == board.length`
* `n = board[i].length`
* `1 <= m, n <= 6`
* `1 <= word.length <= 15`
* `board` and `word` consists of only lowercase and uppercase English letters.

## Solution(DFS)

think of the matrix as a tree with many possible root, and the tree can extend in direction

now we can make a dfs method, that recursively call itself to extend in 4 direction, and if any direction return True, there is a solution

The base case is when current index of word is last index and match with current grid

We have to terminate when current grid != word\[index]

\*\*\* One key point is when searching in 4 direction we want to avoid search on searched/used grid, one way to do so is to make a used array to store used grid, or , just flip searched grid to "#" and put it back later

```python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        
    #Huge thanks to DBabichev for his trick to mark visited grid "#" and put it back later, which save the use of visited array and extra comparison
    
        max_row = len(board)
        max_col = len(board[0])
        
        def dfs(r,c,index):
            #terminate if not match
            if word[index] != board[r][c]:
                return False
            else:
                tmp = board[r][c]
                board[r][c] = "#"
                #if it is the last index we are checking and it is right then we have a solution
                if index == len(word)-1:
                    return True
                if r-1 >=0 :
                    if dfs(r-1,c,index+1):
                        return True
                if r+1 < max_row :
                    if dfs(r+1,c,index+1):
                        return True
                if c+1 < max_col :
                    if dfs(r,c+1,index+1):
                        return True
                if c-1 >=0 :
                    if dfs(r,c-1,index+1):
                        return True
                board[r][c] = tmp
  
        for row in range(max_row):
            for col in range(max_col):
                if dfs(row,col,0):
                    return True       
                
        return False
```

&#x20;
