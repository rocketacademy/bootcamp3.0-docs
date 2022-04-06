# A.5.8.1: Heap Sort

In [D.7](../../a.10-sorting-algorithms) we mentioned heap sort that runs in `O(nlogn) time.` Now that we've covered heaps we can look at this algo again.

### Heap Sort

- Runtime: _**O(nlogn)**_
- Space: _**O(1)**_
- Sort In-Place: Yes
- Stable: Yes

#### Attributes

- good space complexity
- not favored compared to quicksort

{% embed url="https://www.youtube.com/watch?v=onlhnHpGgC4" %}

{% embed url="https://www.youtube.com/watch?v=MtQL_ll5KhQ" %}

{% embed url="https://www.youtube.com/watch?v=2DmK_H7IdTo" %}

{% embed url="https://www.youtube.com/watch?v=k72DtCnY4MU" %}

{% embed url="https://www.youtube.com/watch?v=LbB357_RwlY" %}

```python
def heapify(arr, n, i):
    # Find largest among root and children
    largest = i
    l = 2 * i + 1
    r = 2 * i + 2

    if l < n and arr[i] < arr[l]:
        largest = l

    if r < n and arr[largest] < arr[r]:
        largest = r

    # If root is not largest, swap with largest and continue heapifying
    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)


def heapSort(arr):
    n = len(arr)

    # Build max heap
    for i in range(n//2, -1, -1):
        heapify(arr, n, i)

    for i in range(n-1, 0, -1):
        # Swap
        arr[i], arr[0] = arr[0], arr[i]

        # Heapify root element
        heapify(arr, i, 0)


arr = [1, 12, 9, 5, 6, 10]
heapSort(arr)
n = len(arr)
print("Sorted array is")
for i in range(n):
    print("%d " % arr[i], end='')
```

From: [https://www.programiz.com/dsa/heap-sort](https://www.programiz.com/dsa/heap-sort)
