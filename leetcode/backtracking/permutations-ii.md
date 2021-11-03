# Permutations II



Given a collection of numbers, `nums`, that might contain duplicates, return _all possible unique permutations **in any order**._

&#x20;

**Example 1:**

```
Input: nums = [1,1,2]
Output:
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

**Example 2:**

```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

&#x20;

**Constraints:**

* `1 <= nums.length <= 8`
* `-10 <= nums[i] <= 10`

## Solution(Backtrack DFS)

Key difference comparing to permutation I

1. Sort the list before making permutation
2. Compare current no with previous no. , if it is same, skip it

```python
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        ans =[]
        
        nums = sorted(nums)
        
        self.dfs([],nums,ans)

        return ans
        
    def dfs(self,path,num,ans):
        #base case
        if not num:
            ans.append(path)
            return

        for i in range(len(num)):
            if i>0 and num[i] == num[i-1]:
                continue
            self.dfs(path+[num[i]], num[:i]+num[i+1:],ans)
```
