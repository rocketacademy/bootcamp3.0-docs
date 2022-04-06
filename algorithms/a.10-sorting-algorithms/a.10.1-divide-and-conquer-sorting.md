# A.10.1: Divide and Conquer Sorting

## Merge Sort

* Runtime: _**O(nlogn)**_
* Space: _**O(n)**_
* Sort In-Place: No
* Stable: Yes

**Attributes**

* fast
* usually implemented recursively

**Divide and Conquer**

Merge sort is a divide and conquer sorting algorithm, which just means that the sorting happens by splitting up the original array into smaller and smaller pieces until it's completely broken apart _before_ sorting. The sorting happens each time the pieces are combined back together.

**Merge Sort Pseudo Code**

```
Divide the array into half

Give each half to the merge_sort function

The recurence relation is that the array parameter has one or less items in it.

Capture the return value of the merge_sort function.

Once a return value has been captured the merge_sort function can begin recursing up.

Run the merge function. Give the merge function the two arrays.

The merge function will combine and sort them.

For every value in returned left_array, compare it to returned right_array
  if a value in left_array is less than a value in right_array
    put the left_array value in the output array
  else if the value in left_array is more than a value in right_array
    put the right_array value in the output array
```

**Merge Sort**

```
from pprint import pprint

A = [64, 25, 12, 22, 11]

def merge_sort(arr):
    if len(arr) > 1:

         # Finding the middle of the array
        mid = len(arr)//2

        # Dividing the array elements
        L = arr[:mid]

        # into 2 halves
        R = arr[mid:]

        # Sorting the first half
        leftResult = merge_sort(L)

        # Sorting the second half
        rightResult = merge_sort(R)

        # merge the results of the recursive merge_sort calls
        return merge(leftResult,rightResult)
    else:
        return arr

def merge(L,R):

    # create an empty array
    arr = [None] * (len(L) + len(R))

    i = j = k = 0

    # Copy data to temp arrays L[] and R[]
    while i < len(L) and j < len(R):
        if L[i] < R[j]:
            arr[k] = L[i]
            i += 1
        else:
            arr[k] = R[j]
            j += 1
        k += 1

    # Checking if any element was left
    while i < len(L):
        arr[k] = L[i]
        i += 1
        k += 1

    while j < len(R):
        arr[k] = R[j]
        j += 1
        k += 1

    return arr


result = merge_sort(A)
print ("Sorted array")
pprint( result)
```

**Further Reading**

{% embed url="https://www.youtube.com/watch?v=JSceec-wEyw" %}

{% embed url="https://www.youtube.com/watch?v=4VqmGXwpLqc" %}

{% embed url="https://www.youtube.com/watch?v=1sdEchFsL0Y" %}

{% embed url="https://www.youtube.com/watch?v=Ns7tGNbtvV4" %}

[https://www.programiz.com/dsa/merge-sort](https://www.programiz.com/dsa/merge-sort)

[https://www.algostructure.com/sorting/mergesort.php](https://www.algostructure.com/sorting/mergesort.php)

[https://www.geeksforgeeks.org/merge-sort/](https://www.geeksforgeeks.org/merge-sort/)

## Quick Sort

* Runtime: _**O(nlogn)**_
* Space: _**O(1)**_
* Sort In-Place: Yes
* Stable: Yes

**Attributes**

* fast
* good space complexity
* was used for the `sort` method in JavaScript

```
from pprint import pprint

A = [64, 25, 12, 22, 11]
def partition(array, begin_idx, end_idx):

    # the least found value location
    # so we know where in the subarray
    # to place the pivot
    least_idx = begin_idx

    # pivot is at the end, find where it goes in the array
    pivot = array[end_idx]

    # find where in the array to put the pivot
    # j looks through the array
    for j in range(begin_idx, end_idx):

        # current element is less than pivot
        if array[j] <= pivot:
            # swap j with this least item
            array[least_idx], array[j] =  array[j], array[least_idx]
            # advance least_idx
            least_idx = least_idx + 1
            

    # put the pivot one ahead of the last least item found
    array[least_idx],array[end_idx] = array[end_idx],array[least_idx]

    # return an index that hasn't been sorted
    # yet, the index to the left of the location where we put the pivot
    return (least_idx)

def quick_sort(array, begin_idx, end_idx):

    # we moved the end past the beginning
    # or the beginning past the end
    if begin_idx >= end_idx:
        return

    # find the next pivot
    pivot = partition(array, begin_idx, end_idx)

    # recurse left
    quick_sort(array, begin_idx, pivot-1)

    # recurse right
    quick_sort(array, pivot+1, end_idx)

quick_sort(A,0,len(A) - 1)
print ("Sorted array")
print(A)
```

**Quick Sort with Comments**

```
from pprint import pprint

A = [64, 25, 12, 22, 11]
def partition(array, begin_idx, end_idx):

    least_idx = begin_idx

    # pivot is at the end, find where it goes in the array
    pivot = array[end_idx]
    pprint(f'curr subarray: {array[begin_idx:end_idx]}')

    # find where in the array to put the pivot
    # j looks through the array
    for j in range(begin_idx, end_idx):

        print(f'{array[j]} <= pivot|{pivot}|')
        # current element is less than pivot
        if array[j] <= pivot:
            
            # swap j with this least item
            array[least_idx], array[j] =  array[j], array[least_idx]
            # advance least_idx bc we are about to put something there
            least_idx = least_idx + 1
            if j != least_idx:
                pprint(f'*after swap* subarray: {array[begin_idx:end_idx]}')

    # put the pivot one ahead of the last least item found
    array[least_idx],array[end_idx] = array[end_idx],array[least_idx]
    pprint(f'*final swap* subarray: {array[begin_idx:end_idx]}')

    # return an index that hasn't been sorted
    # yet, the index to the left of the location where we put the pivot
    return (least_idx)

def quick_sort(array, begin_idx, end_idx):


    # we moved the end past the beginning
    # or the beginning past the end
    if begin_idx >= end_idx:
        print('end')
        return


    # find the next pivot
    pivot_idx = partition(array, begin_idx, end_idx)
    print(f'pivot idx: {pivot_idx}')

    # recurse left
    print(f'recurse left: {begin_idx} to {pivot_idx-1}')
    quick_sort(array, begin_idx, pivot_idx-1)

    # recurse right
    print(f'recurse right: {pivot_idx+1} to {end_idx}')
    quick_sort(array, pivot_idx+1, end_idx)

quick_sort(A,0,len(A) - 1)
print ("Sorted array")
print(A)
```

**Further Reading**

{% embed url="https://youtu.be/ZHVk2blR45Q" %}

{% embed url="https://www.youtube.com/watch?v=Hoixgm4-P4M" %}

{% embed url="https://www.youtube.com/watch?v=0SkOjNaO1XY" %}

{% embed url="https://www.youtube.com/watch?v=PgBzjlCcFvc" %}

{% embed url="https://www.youtube.com/watch?v=kUon6854joI" %}

[https://www.programiz.com/dsa/quick-sort](https://www.programiz.com/dsa/quick-sort)

[https://www.geeksforgeeks.org/quick-sort/](https://www.geeksforgeeks.org/quick-sort/)

**Quick Sort in JavaScript**

[https://v8.dev/blog/array-sort](https://v8.dev/blog/array-sort)

#### Heap Sort

* Runtime: _**O(nlogn)**_
* Space: _**O(1)**_
* Sort In-Place: Yes
* Stable: Yes

Heap sort is on average slower and less commonly used than Merge Sort and Quick Sort

[https://www.geeksforgeeks.org/heap-sort/](https://www.geeksforgeeks.org/heap-sort/)

{% hint style="warning" %}
No need to cover this code right now- we haven't seen the heap data structure yet. We'll look at this again when we cover heaps, but this is another example of a sorting algorithm that runs in `O(nlogn)` time.
{% endhint %}
