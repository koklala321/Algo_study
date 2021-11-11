# Quick Sort

Quick sort

Choose a pivot from the current list, separate the list in 3 partition, one lower than pivot, one equal to pivot, one larger than pivot. Then recursively process them and select new pivot in new stack,return &#x20;

```python
def quicksort(num:list):
    if len(num) <= 1:
        return num
    pivot = num[0]
    left = [x for x in num if x <pivot]
    mid = [x for x in num if x == pivot]
    right = [x for x in num if x > pivot]
    

    left = quicksort(left)
    right = quicksort(right)
    
    return left+mid+right
```
