# Remove Duplicates from Sorted Array II

## Question



Given an integer array `nums` sorted in **non-decreasing order**, remove some duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) such that each unique element appears **at most twice**. The **relative order** of the elements should be kept the **same**.

Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the **first part** of the array `nums`. More formally, if there are `k` elements after removing the duplicates, then the first `k` elements of `nums` should hold the final result. It does not matter what you leave beyond the first `k` elements.

Return `k`_ after placing the final result in the first _`k`_ slots of _`nums`.

Do **not** allocate extra space for another array. You must do this by **modifying the input array **[**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) with O(1) extra memory.

**Custom Judge:**

The judge will test your solution with the following code:

```
int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```

If all assertions pass, then your solution will be **accepted**.

**Example 1:**

```
Input: nums = [1,1,1,2,2,3]
Output: 5, nums = [1,1,2,2,3,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 1, 1, 2, 2 and 3 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

**Example 2:**

```
Input: nums = [0,0,1,1,1,1,2,3,3]
Output: 7, nums = [0,0,1,1,2,3,3,_,_]
Explanation: Your function should return k = 7, with the first seven elements of nums being 0, 0, 1, 1, 2, 3 and 3 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

**Constraints:**

* `1 <= nums.length <= 3 * 104`
* `-104 <= nums[i] <= 104`
* `nums` is sorted in **non-decreasing** order.

## Solution(two pointer)

for two pointer solution, create one fast pointer, one slow pointer

Fast is always two index ahead of slow

fast and slow start from index 2 , first two index can be skipped when replacing num

```python
def removeDuplicates(self, nums: List[int]) -> int:
    if len(nums) < 2: 
        return len(nums)
    slow, fast = 2, 2

    while fast < len(nums):
        if nums[slow - 2] != nums[fast]:
            nums[slow] = nums[fast]
            slow += 1
        fast += 1
    return slow
```

## Solution(Hash table)

simply create a hash table when going through array, use index to keep track of current num, pop it when value count >=2 (also reduce the index by 1 to balance )

```python
def removeDuplicates(self, nums: List[int]) -> int:
    #create a dict to stored each number occurance
    d = {}
    n = len(nums)
    index = 0

    for i in range(n):
        if nums[index] not in d:
            d[nums[index]]=0    
        elif d[nums[index]] >= 2:
            nums.pop(index)
            #reduce index by 1 to counter the reduction of total number in array
            index-=1
        #add occurance by 1
        d[nums[index]]+=1
        #add index to shift by 1
        index+=1

    return index
```
