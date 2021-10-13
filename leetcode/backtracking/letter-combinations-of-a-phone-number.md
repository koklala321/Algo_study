# Letter Combinations of a Phone Number

```
    if not digits:
        return []

    n = len(digits)
    ans = []
    self.dfs(d,digits,ans,"")
    return ans

def dfs(self,d,digits,ans,path):
    if not digits:
        ans.append(path)
        return

    for character in d[digits[0]]:
        self.dfs(d,digits[1:],ans,path+character)
```

Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent. Return the answer in **any order**.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)

**Example 1:**

```
Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

**Example 2:**

```
Input: digits = ""
Output: []
```

**Example 3:**

```
Input: digits = "2"
Output: ["a","b","c"]
```

**Constraints:**

* `0 <= digits.length <= 4`
* `digits[i]` is a digit in the range `['2', '9']`.

## Solution(Backtracking)

```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        #what if dfs
        d = {"2":"abc","3":"def","4":"ghi","5":"jkl","6":"mno","7":"pqrs","8":"tuv","9":"wxyz"}
        
        #dfs method
        if not digits:
            return []
    
        ans = []
        self.dfs(d,digits,ans,"")
        return ans
        
    def dfs(self,d,digits,ans,path):
        if not digits:
            ans.append(path)
            return
        #recursion
        #remember, the no. of iteration is depend on charcter in dict
        #draw a tree diagram and u will see
        for character in d[digits[0]]:
            self.dfs(d,digits[1:],ans,path+character)
```

## Solution

hash table and list comprehension

```python
def letterCombinations(self, digits: str) -> List[str]:
    l=[]
    if not digits:
        return l

    d = {"2":["a","b","c"],"3":["d","e","f"],"4":["g","h","i"],"5":["j","k","l"],"6":["m","n","o"],"7":["p","q","r","s"],"8":["t","u","v"],"9":["w","x","y","z"]}
    l=[""]
    for c in digits:
        l = [p + q for p in l for q in d[c]]
    return l
```

## Solution(use itertool.product)



```python
def letterCombinations(self, digits: str) -> List[str]:
    l=[]
    d = {"2":["a","b","c"],"3":["d","e","f"],"4":["g","h","i"],"5":["j","k","l"],"6":["m","n","o"],"7":["p","q","r","s"],"8":["t","u","v"],"9":["w","x","y","z"]}
    for c in digits:
        l.append(d[c])

    if len(digits) > 0:
        return list(map(lambda x:"".join(x),product(*l)))
    else:
        return []
```
