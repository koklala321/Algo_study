# Heap

H**eap** is a specialized tree-based data structure&#x20;

In a _max heap_, for any given node C, if P is a parent node of C, then the _key_ (the _value_) of P is greater than or equal to the key of C. In a _min heap_, the key of P is less than or equal to the key of C.

`heap[k] <= heap[2*k+1]` 和 `heap[k] <= heap[2*k+2]`&#x20;



In python, heap can be implemented with heapq library.

Document link:

{% embed url="https://docs.python.org/3/library/heapq.html" %}

Most common heap operation

`heapq.heappush`(_heap_, _item_)

Push the value _item_ onto the _heap_, maintaining the heap invariant.

`heapq.heappop`(_heap_)

Pop and return the smallest item from the _heap_, maintaining the heap invariant. If the heap is empty, [`IndexError`](https://docs.python.org/3/library/exceptions.html#IndexError) is raised. To access the smallest item without popping it, use `heap[0]`.

`heapq.heapify`(_x_)

Transform list _x_ into a heap, in-place, in linear time.



