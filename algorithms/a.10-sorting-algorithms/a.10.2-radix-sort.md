# A.10.2: Radix Sort

## Non-Comparison Sorting Algorithms

Non-comparison sorting algorithms are interesting because if all the avlues in the array are integers we can sort them in less than _**O(nlogn)**_ time.

# Counting Sort

* Runtime: _**O(kn)**_

**k** is the highest integer in the array.

```
def countingSort(inputArray):
    # Find the maximum element in the inputArray
    maxEl = max(inputArray)

    countArrayLength = maxEl+1

    # Initialize the countArray with (max+1) zeros
    countArray = [0] * countArrayLength

    # Step 1 -> Traverse the inputArray and increase
    # the corresponding count for every element by 1
    for el in inputArray:
        countArray[el] += 1

    # Step 2 -> For each element in the countArray,
    # sum up its value with the value of the previous
    # element, and then store that value
    # as the value of the current element
    for i in range(1, countArrayLength):
        countArray[i] += countArray[i-1]

    # Step 3 -> Calculate element position
    # based on the countArray values
    outputArray = [0] * len(inputArray)
    i = len(inputArray) - 1
    while i >= 0:
        currentEl = inputArray[i]
        countArray[currentEl] -= 1
        newPosition = countArray[currentEl]
        outputArray[newPosition] = currentEl
        i -= 1

    return outputArray

inputArray = [2,2,0,6,1,9,9,7]
print("Input array = ", inputArray)

sortedArray = countingSort(inputArray)
print("Counting sort result = ", sortedArray)
```

# Radix Sort

* Runtime: _**O(dkn)**_

**d** is the number of times counting sort is run.

Use the numbers in each "radix" or place to know how to sort the array.

```
def countingSortForRadix(inputArray, placeValue):
    # We can assume that the number of digits used to represent
    # all numbers on the placeValue position is not grater than 10
    countArray = [0] * 10
    inputSize = len(inputArray)

    # placeElement is the value of the current place value
    # of the current element, e.g. if the current element is
    # 123, and the place value is 10, the placeElement is
    # equal to 2
    for i in range(inputSize):
        placeElement = (inputArray[i] // placeValue) % 10
        countArray[placeElement] += 1

    for i in range(1, 10):
        countArray[i] += countArray[i-1]

    # Reconstructing the output array
    outputArray = [0] * inputSize
    i = inputSize - 1
    while i >= 0:
        currentEl = inputArray[i]
        placeElement = (inputArray[i] // placeValue) % 10
        countArray[placeElement] -= 1
        newPosition = countArray[placeElement]
        outputArray[newPosition] = currentEl
        i -= 1

    return outputArray

def radixSort(inputArray):
    # Step 1 -> Find the maximum element in the input array
    maxEl = max(inputArray)

    # Step 2 -> Find the number of digits in the `max` element
    D = 1
    while maxEl > 0:
        maxEl /= 10
        D += 1

    # Step 3 -> Initialize the place value to the least significant place
    placeVal = 1

    # Step 4
    outputArray = inputArray
    while D > 0:
        outputArray = countingSortForRadix(outputArray, placeVal)
        placeVal *= 10
        D -= 1

    return outputArray

input = [2,20,61,997,1,619]
print(input)
sorted = radixSort(input)
print(sorted)
```

From: [https://stackabuse.com/radix-sort-in-python/](https://stackabuse.com/radix-sort-in-python/)ello 2
