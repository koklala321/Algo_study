# Search in Rotated Sorted Array



There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be rotated at pivot index `3` and become `[4,5,6,7,0,1,2]`.

Given the array `nums` **after** the possible rotation and an integer `target`, return _the index of _`target`_ if it is in _`nums`_, or _`-1`_ if it is not in _`nums`.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

```
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
```

**Example 2:**

```
Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
```

**Example 3:**

```
Input: nums = [1], target = 0
Output: -1
```

**Constraints:**

* `1 <= nums.length <= 5000`
* `-104 <= nums[i] <= 104`
* All values of `nums` are **unique**.
* `nums` is an ascending array that is possibly rotated.
* `-104 <= target <= 104`

## Solution(binary search)

The key to solve this problem, is to analysis the number of situation/cases

if nums\[left]>=nums\[mid] , it means from mid to right it is sorted

else

if num\[left]<=nums\[mid] , then it means from left to mid is sorted

Then we can check if target is in sorted side, if not, then it is on other side and we adjust left/right counter

```python
def search(self, nums: List[int], target: int) -> int:
    left = 0 
    right = len(nums)-1

    if not nums:
        return -1

    while left <= right:
        mid = (left+right)//2
        if nums[mid]==target:
            return mid

        if nums[left]<=nums[mid]:
        #then it mean from left to mid it is sorted
            if nums[left]<=target<=nums[mid]:
                right = mid-1
            else:
                left=mid+1
        else:
            #then it mean mid to right is sorted
            if nums[mid]<=target<=nums[right]:
                left = mid +1
            else:
                right = mid -1

        #print(left,right,mid)

    return -1
```
