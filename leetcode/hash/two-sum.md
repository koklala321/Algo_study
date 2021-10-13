---
description: most famous LeetCode question, two sum
---

# Two Sum

## Solving with hash table

Solving with hash table (dictionary in Python) , allow a o(n) time complexity

```python
def twoSum(self, nums: List[int], target: int) -> List[int]:
    #use dict to store num and its index that has shown up
    d = {}
    #use enumerate to show index
    for i,j in enumerate(nums):
        diff = target - j
        if diff in d:
            return [d[diff],i]
        #if diff is not found, store current num as key and index as value to be searcherd later
        d[j]=i 
```

{% hint style="info" %}
 hash table provide o(n) lookup time
{% endhint %}

