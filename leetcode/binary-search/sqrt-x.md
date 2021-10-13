# Sqrt(x)

Given a non-negative integer `x`, compute and return _the square root of_ `x`.

Since the return type is an integer, the decimal digits are **truncated**, and only **the integer part** of the result is returned.

**Note: **You are not allowed to use any built-in exponent function or operator, such as `pow(x, 0.5)` or `x ** 0.5`.

**Example 1:**

```
Input: x = 4
Output: 2
```

**Example 2:**

```
Input: x = 8
Output: 2
Explanation: The square root of 8 is 2.82842..., and since the decimal part is truncated, 2 is returned.
```

**Constraints:**

* `0 <= x <= 231 - 1`

## Solution(binary search)

use binary search to search through 1 to x. The key is the part

```python
if mid*mid <= x <(mid+1) *(mid+1):
```

as we need to consider the case where x can not return integer square root (i.e. x=13)

```python
def mySqrt(self, x: int) -> int:
    left = 1
    right = x

    if x == 1:
        return 1
    if x == 0:
        return 0

    while right>=left:
        mid = (right+left)//2
        if mid*mid <= x <(mid+1) *(mid+1):
            return mid
        elif mid*mid > x:
            right =mid
        else:
            left = mid
```
