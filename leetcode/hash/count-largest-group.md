# Count Largest Group



Given an integer `n`. Each number from `1` to `n` is grouped according to the sum of its digits. 

Return how many groups have the largest size.

**Example 1:**

```
Input: n = 13
Output: 4
Explanation: There are 9 groups in total, they are grouped according sum of its digits of numbers from 1 to 13:
[1,10], [2,11], [3,12], [4,13], [5], [6], [7], [8], [9]. There are 4 groups with largest size.
```

**Example 2:**

```
Input: n = 2
Output: 2
Explanation: There are 2 groups [1], [2] of size 1.
```

**Example 3:**

```
Input: n = 15
Output: 6
```

**Example 4:**

```
Input: n = 24
Output: 5
```

**Constraints:**

* `1 <= n <= 10^4`

## Solution(Hash table)

```python
def countLargestGroup(self, n: int) -> int:d = {}
    for i in range(1,n+1):
        s = sum(map(int,str(i)))
        if s not in d:
            d[s] =1
        else:
            d[s]+=1
    
    m = max(d.values())
    
    return sum(1 for i in d.values() if i==m)
```

## Solution(Dynamic programming)



```python
def countLargestGroup(self, n: int) -> int:
    #dynamic programming
    #idea is, we start from 1, so every number later must have some part exist before, i.e. divmod(9999) = 999,9  , and we should have processed 999 before.
    #So we use a dict to store all previously processed number and it ans
    #dp must intiate with {0:0} because 1-9 will use it in calculation
    dp ={0:0}
    #count have 36 space as max sum of digit is 36 (9999)
    counts = [0]*(4*9)

    for i in range(1,n+1):
        quotient, remainder= divmod(i,10)
        dp[i] = dp[quotient] + remainder
        #need to be dp[i]-1 as count[0] is count of 1, etc.
        counts[dp[i]-1]+=1

    return counts.count(max(counts)) 
```
