# Rotate Image



You are given an `n x n` 2D `matrix` representing an image, rotate the image by **90** degrees (clockwise).

You have to rotate the image [**in-place**](https://en.wikipedia.org/wiki/In-place\_algorithm), which means you have to modify the input 2D matrix directly. **DO NOT** allocate another 2D matrix and do the rotation.

&#x20;

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/08/28/mat1.jpg)

```
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [[7,4,1],[8,5,2],[9,6,3]]
```

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/08/28/mat2.jpg)

```
Input: matrix = [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]]
Output: [[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]]
```

**Example 3:**

```
Input: matrix = [[1]]
Output: [[1]]
```

**Example 4:**

```
Input: matrix = [[1,2],[3,4]]
Output: [[3,1],[4,2]]
```

&#x20;

**Constraints:**

* `matrix.length == n`
* `matrix[i].length == n`
* `1 <= n <= 20`
* `-1000 <= matrix[i][j] <= 1000`

## Solution(Rotate and transpose)

one of the very key concept here is how to transpose the array, remember that you only have to loop n! times not n^2 times

```
        for i in range(len(matrix)):
            for j in range(i):
```

```python
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        #Reverse and transpose
        
        #reverse
        start = 0
        end = len(matrix)-1
        while end>start:
            matrix[start],matrix[end] = matrix[end],matrix[start]       
            start+=1
            end -=1
        
        #transpose
        '''
        [[7,8,9],
         [4,5,6],
         [1,2,3]]
        '''
        for i in range(len(matrix)):
            for j in range(i):
                matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]

        
        
        '''
        #zip
        matrix[:] = zip(*matrix[::-1])
        '''
        
        '''
        #assume not in place
        n = len(matrix)
        ans = [[] for _ in range(n)]
        
        for i in range(n-1,-1,-1):
            for j in range(n):
                ans[j].append(matrix[i][j])
                
        print(ans)
        '''
```

