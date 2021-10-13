---
description: >-
  Advanced version of two sum, this time with one more number, also worth to
  notice that the question demand no duplicate answer
---

# 3Sum

## Question

Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

**Example 1:**

```
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
```

**Example 2:**

```
Input: nums = []
Output: []
```

**Example 3:**

```
Input: nums = [0]
Output: []
```

**Constraints:**

* `0 <= nums.length <= 3000`
* `-105 <= nums[i] <= 105`

## Two pointer

Similar to two sum, but this time if we sort it we can try two pointer

point to note:

* to avoid duplicate ans , we need to check if the current num has been looped` (nums[i] == nums[i-1])`
* when moving the pointer, to avoid duplicate ans, we have to check if current num equal to previous num

```python
#check if current num under pointer is equal to previous one
                while k>j and nums[k] == nums[k+1]:
                    k-=1
                while k>j and nums[j] == nums[j-1]:
                    j+=1
```

```python
def threeSum(self, nums):
    n = len(nums)
    ans = []
    if n < 3:
        return ans
    #sorting it so we can use its sorted structure to avoud duplicate ans later
    nums = sorted(nums)
    #print(nums)
    for i in range(n):
        remain = 0-nums[i]
        #print(remain)
        #we need to avoid duplicate ans, for example [-1,-1,0,1] can return two [-1,0,1] , so we have to skip the first one
        if i>0 and nums[i] == nums[i-1]:
            continue
        #since it is sorted, we now only have to look for 
        j = i+1
        k = n-1
        while k>j:
            if nums[j]+nums[k] == remain:
                ans.append([nums[i],nums[j],nums[k]])
                k-=1
                j+=1
                #avoid duplicate ans
                while k>j and nums[k] == nums[k+1]:
                    k-=1
                while k>j and nums[j] == nums[j-1]:
                    j+=1
            elif nums[j]+nums[k]>remain:
                k-=1
            else:
                j+=1
        
    return ans
```
