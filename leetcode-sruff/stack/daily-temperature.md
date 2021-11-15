# Daily temperature



Daily TemperaturesMedium5734145Add to ListShare

Given an array of integers `temperatures` represents the daily temperatures, return _an array_ `answer` _such that_ `answer[i]` _is the number of days you have to wait after the_ `ith` _day to get a warmer temperature_. If there is no future day for which this is possible, keep `answer[i] == 0` instead.

&#x20;

**Example 1:**

```
Input: temperatures = [73,74,75,71,69,72,76,73]
Output: [1,1,4,2,1,1,0,0]
```

**Example 2:**

```
Input: temperatures = [30,40,50,60]
Output: [1,1,1,0]
```

**Example 3:**

```
Input: temperatures = [30,60,90]
Output: [1,1,0]
```

&#x20;

**Constraints:**

* `1 <= temperatures.length <= 105`
* `30 <= temperatures[i] <= 100`

## Solution

```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        
        ans = [0]*len(temperatures)
        stack = deque()
        
        for i,cur_temp in enumerate(temperatures):
            while stack and cur_temp > temperatures[stack[-1]]:
                ans[stack[-1]] = i - stack[-1]
                stack.pop()
            stack.append(i)
                
        return ans
```
