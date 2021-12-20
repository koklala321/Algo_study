# Decode String



Given an encoded string, return its decoded string.

The encoding rule is: `k[encoded_string]`, where the `encoded_string` inside the square brackets is being repeated exactly `k` times. Note that `k` is guaranteed to be a positive integer.

You may assume that the input string is always valid; No extra white spaces, square brackets are well-formed, etc.

Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, `k`. For example, there won't be input like `3a` or `2[4]`.

&#x20;

**Example 1:**

```
Input: s = "3[a]2[bc]"
Output: "aaabcbc"
```

**Example 2:**

```
Input: s = "3[a2[c]]"
Output: "accaccacc"
```

**Example 3:**

```
Input: s = "2[abc]3[cd]ef"
Output: "abcabccdcdcdef"
```

**Example 4:**

```
Input: s = "abc3[cd]xyz"
Output: "abccdcdcdxyz"
```

&#x20;

**Constraints:**

* `1 <= s.length <= 30`
* `s` consists of lowercase English letters, digits, and square brackets `'[]'`.
* `s` is guaranteed to be **a valid** input.
* All the integers in `s` are in the range `[1, 300]`.

## Solution(stack)

```python
class Solution:
    def decodeString(self, s: str) -> str:
        #stack way
        stack = []
        idx = 0
        mul = 0
        ans = ""
        
        for c in s:
            if c.isdigit():
                mul = mul *10 + int(c)
            elif c == "[":
                stack.append(mul)
                stack.append(ans)
                mul = 0
                ans = ""
            elif c == "]":
                prev_str = stack.pop()
                prev_mul = stack.pop()
                ans = prev_str + prev_mul * ans
            else:
                ans += c
                
        
        return ans
        
```





## Solution(recursive DFS)

```python
 class Solution:
    def decodeString(self, s: str) -> str:   
        def dfs(s,idx):
            ans = ""
            mul,pos = 0,idx
            while idx < len(s):
                if s[idx].isdigit():
                    mul = mul*10 + int(s[idx])
                elif s[idx] == "[":
                    temp,pos = dfs(s,idx+1)
                    ans += mul * temp
                    idx = pos
                    mul = 0
                elif s[idx] == "]":
                    return ans,idx
                else:
                    ans+=s[idx]
                
                idx+=1
            return ans,idx
        
        return dfs(s,0)[0]
```
