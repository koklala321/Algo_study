# Next greater element

The **next greater element** of some element `x` in an array is the **first greater** element that is **to the right** of `x` in the same array.

You are given two **distinct 0-indexed** integer arrays `nums1` and `nums2`, where `nums1` is a subset of `nums2`.

For each `0 <= i < nums1.length`, find the index `j` such that `nums1[i] == nums2[j]` and determine the **next greater element** of `nums2[j]` in `nums2`. If there is no next greater element, then the answer for this query is `-1`.

Return _an array _`ans`_ of length _`nums1.length`_ such that _`ans[i]`_ is the **next greater element** as described above._

&#x20;

**Example 1:**

```
Input: nums1 = [4,1,2], nums2 = [1,3,4,2]
Output: [-1,3,-1]
Explanation: The next greater element for each value of nums1 is as follows:
- 4 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.
- 1 is underlined in nums2 = [1,3,4,2]. The next greater element is 3.
- 2 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.
```

**Example 2:**

```
Input: nums1 = [2,4], nums2 = [1,2,3,4]
Output: [3,-1]
Explanation: The next greater element for each value of nums1 is as follows:
- 2 is underlined in nums2 = [1,2,3,4]. The next greater element is 3.
- 4 is underlined in nums2 = [1,2,3,4]. There is no next greater element, so the answer is -1.
```

&#x20;

**Constraints:**

* `1 <= nums1.length <= nums2.length <= 1000`
* `0 <= nums1[i], nums2[i] <= 104`
* All integers in `nums1` and `nums2` are **unique**.
* All the integers of `nums1` also appear in `nums2`.

&#x20;

**Follow up:** Could you find an `O(nums1.length + nums2.length)` solution?

## Solution

Next greater element problem can always be solved with stack,&#x20;

we first create a stack , everytime there is a new element, we compare it with last element in stack, if it is greater than it, the next greater element for last element in stack is the new element, we then pop the last element and store the result in somewhere else.

If the new element is not greater than last element in stack, it must be smaller than every element in stack, we continue to append it in stack.



```python
class Solution:
    def nextGreaterElement(self, nums1: List[int], nums2: List[int]) -> List[int]:
        table = {}            
        #fill next greater element
        stack = []
        
        for i in range(len(nums2)):
            while stack and nums2[i]>stack[-1]:
                table[stack[-1]] = nums2[i]
                stack.pop()
                
            stack.append(nums2[i])
            
        for ele in stack:
            table[ele] = -1
            
        ans = [table[num] for num in nums1]   
        
        return ans
```





