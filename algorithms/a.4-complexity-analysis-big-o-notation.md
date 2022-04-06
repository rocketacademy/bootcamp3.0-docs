# A.3: Complexity Analysis, Big-O Notation

## Learning Objectives

By the end of this lesson, you should:

* be familiar with Big-O
* understand how space and time complexity is calculated
* be familiar with the common complexity functions and their ranking order

## Introduction

After you finish writing some code, how can you describe how fast it is? How can you describe how much memory your code takes up?

In this section we'll begin to describe the way that computer science defines the efficiency of a given set of code.

We'll begin with this simple example and describe its properties.

```javascript
// a function that takes an array as a parameter
// and returns true if the array contains the integer 2
function arrayHasTwo(arr){
    // set a default value of not found
    var found = false;
    for(var i=0; i<arr.length; i++){
        if( arr[i] === 2 ){
            // if 2 is found, set to true
            found = true;
        }
    }
    // return result
    return found;
}
```

## Time Complexity

When we run this code it could take differing amounts of time.

```javascript
var list = [1,2,3,3];

// the function iterates 4 times in the loop
var result = arrayHasTwo(list);

var list2 = [1,2,3,4,5,6,7,8,9,3];

// the function iterates 10 times in the loop
var result2 = arrayHasTwo(list2);
```

Our function runs slower if the input is bigger. What we are working towards is a generic way to describe how long something takes to run. Mathematically we can express this as a (mathematical) function of the length of the parameter array. The longer the array is, the longer it will take the code to run.

We refer to the size of the input array as _**n**_.

![Big-O - linear complexity.](../.gitbook/assets/big-o-notation-linear-algorithm.png)

If we plotted the growth of time and of data in _**n**_ on a graph it would look linear, i.e., a straight line. For each additional item in the input array, the "speed" of the function increases in step. The behaviour of time as _**n**_ grows is the first property of complexity analysis. It assumes an input of varying length, and we can analyze what happens when that input grows or shrinks.

#### What are We Measuring?

The Computer Science analysis of this speed / complexity makes no assumptions about the properties of this data, so it always assumes that the input data to the function can be zero to infinity length, as opposed to real-world data, which is very dependant on the specific case. The code that looks for a letter in the alphabet needs to be very different from the code that looks for a name amongst millions of users. Also note the lack of graph axis units in the figure above. The kind of measurement we're doing is called [asymptotic analysis.](https://en.wikipedia.org/wiki/Asymptotic_analysis) It also assumes a theoretical "unit" of computation where the absolute time in seconds or hours doesn't matter. When we use Big-O to analyze code a naive approach would be to count  each line of code and count each loop iteration or if a function is called that has a loop in it. Sometimes we'll count built-in functions such as `Array.unshift` because we'll know that the built-in function already has some inherent run-time complexity. (We'll note each of these special cases when they come up.)

## Big-O

So generally speaking, we measure the speed of a function or given section of code by counting the:

* number of lines of code
* iterations in a loop
* also count functions that we know contain loops

In Computer Science, the definition of speed is more specific than that. There are several specific measures of speed, [including Big Theta and Big Omega](https://en.wikipedia.org/wiki/Big_O_notation#Related_asymptotic_notations), but we'll only be talking about Big-O. All of these notations define a mathematical expression for the speed behaviour of a function. We won't really be concerned with the mathematical definition of these, since for non-theoretical programs, Big-O is the most  useful.

### Worst Case

When talking about Big-O we always talk about the worst-case performance of the function. That is, we don't consider what happens when the input data happens to be formatted in our favor- e.g., what happens if 2 is randomly at the beginning of some of our arrays? Big-O isn't concerned with these probabilities. 

If we edit our function above we can see how it becomes more efficient, but that the Big-O remians the same. We can get rid of line 5, and just return true if and when two is found.

```javascript
// a function that takes an array as a parameter
// and returns true if the array contains the integer 2
function arrayHasTwo(arr){
    // set a default value of not found
    // var found = false;
    for(var i=0; i<arr.length; i++){
        if( arr[i] === 2 ){
            // if 2 is found, set to true
            return true;
        }
    }
    // return result
    return false;
}
```

Then we can run our function:

```javascript
var list = [1,2,4,4];

// the function iterates 4 times in the loop
var result = arrayHasTwo(list);

var list2 = [1,2,3,4,5,6,7,8,0,3];

// the function iterates 10 times in the loop
var result2 = arrayHasTwo(list2);
```

With the early return statement we've actually saved 2 iterations for `list` and 8 for `list2`!  But Computer Science doesn't care- we haven't defined anywhere in our `arrayHasTwo` function or anywhere else about where the 2 might fall inside the array. The worst case performance of this function is still O(n).

Big-O doesn't care about any specific set of data, it also doesn't care about if the data is sorted.

Note that when calculating Big-O, if the problem statement itself defines the input array as always being sorted then this would be taken into account. If, given the above code it was stated that _**the input array is always sorted and starts with a value of zero**_, then the Big-O of the above code would be **O(3) **(and thus** O(1)**)- the worst case performance is that the loop runs 3 times from zero to 2.

### Coefficients

When expressing Big-O notation, we only consider the variable with the largest order of complexity, and remove any summed variables of lower complexity. When evaluating the variable of largest order of complexity, we also remove any coefficients attached to that variable, since those coefficients make minimal difference in the complexity when we consider large numbers where the complexity matters. For example, if I determined that my algorithm ran in complexity of _**2n² + c**_ time, I would remove the **c** because it is of lower complexity than **n²**, and I would remove the 2 in _**2n²**_ because it is a coefficient. I would then be left with _**O(n²)**_.

#### What is _c_?

When calculating the Big-O of a function we would consider whether the _iterations_ of a loop are constant or if they increase with the size of _**n**_. In this example where _**n**_ is the size of the larger input array, an increase in the size of the input arrays do not change the fact that there are 2 loops in the function. Changing the size of _**n**_ only increases the number of times the loops run- not the number of loops running.

```javascript
// a function that takes an array as a parameter
// and returns true if the array contains the integer 2
function arraysHaveTwo(arr1, arr2){
    // set a default value of not found
    var found1 = false;
    for(let i=0; i<arr.length; i++){
        if( arr[i] === 2 ){
            // if 2 is found, set to true
            found1 = true;
        }
    }
    
    var found2 = false;

    for(let i=0; i<arr.length; i++){
        if( arr[i] === 2 ){
            // if 2 is found, set to true
            found2 = true;
        }
    }
    return found1 && found2;
}
```

Run the code:

```javascript
var list = [1,2,4,4];
var list2 = [1,2,3,4,5,6,7,8,0,3];

var result = arraysHaveTwo(list1,list2);
```

Nor does _**n**_ necessarily increase if the loops are nested. In this example the loop will only ever run twice. So _**c**_ is 2, and for Big-O we would reduce **O(2**_**n**_**)** to **O(**_**n**_**)**.

```javascript
// a function that takes an array as a parameter
// and returns true if the array contains the integer 2
function arrayHasZeroOrOne(arr){
    var found = false;
    // run the array search twice
    // once for zero, once for 1
    for(let i=0; i<2; i++){
        // set the value we want to find
        var find = i;
        
        // look through the array
        for(let i=0; i<arr.length; i++){
            if( arr[i] === find ){
                // if 2 is found, set to true
                found = true;
            }
        }        
    }
    
    return found;
}
```

Run the code:

```javascript
var list = [1,2,3,4,5,6,7,8,0,3];

var result = arraysHaveTwo(list);
```

{% hint style="info" %}
**Vocabulary**

We'll be describing code (Python and JavaScript) functions and the mathematical definition of a function interchangeably when discussing Big-O. For our purposes here they behave equivalently.

Although technically incorrect, we'll talk about _time, speed and complexity_ interchangeably, because, in the end, Big-O is telling us about the amount of time our code runs in. We don't need to worry about the theoretical distinction between these three words.

The "O" in Big-O [apparently stands for "Order".](https://en.wikipedia.org/wiki/Big_O_notation#History_\(Bachmann%E2%80%93Landau,\_Hardy,\_and_Vinogradov_notations\))
{% endhint %}

### Space Complexity

The other thing we can measure with Big-O is the amount of space, or memory a function takes up.

```javascript
// a function that takes an array as a parameter
// and returns true if the array contains the integer 2
function buildArray(count){
    // set a default value of not found
    var result = [];
    for(var i=0; i<count; i++){
        result.push(Math.random());
    }
    return result
}
```

We can say that this function has **O(**_**n**_**)** complexity and also takes up **O(**_**n**_**)** space. When this function runs the result variable will take up n space. (Note that it doesn't matter whether or not we return anything at the end, just that a growing array existed while the function was running.)

#### Reference vs. Value Space Complexity

Manipulating an array is also not the same as "taking up space". In the following code, although we create new variables for each loop iteration, we are not allocating any new space with this function. Thus it has a space complexity of **O(1)**.

```javascript
function shuffleArray(array){
    for(var i=0; i<array.length; i++){
        // save the first element value
        var temp = array[0];
        var tempIndex = Math.floor( Math.random() * array.length );
        // switch a random location into the first element
        array[0] = array[tempIndex];
        // replace the value in that random location
        array[tempIndex] = temp;
    }
    // no need to return bc we did not allocate a
    // new array- we manipulated this array by value.
    //return array;
}
```

When we call this function we don't need to capture the return value- we manipulated the array by reference- running the function hasn't taken any new space.

```javascript
var list = [1,2,3,4,5,6,7,8,0,3];
console.log(list); //this is the original version of the array.
shuffleArray(list);
console.log(list); // this will be the shuffled array. 
```

## Big-O Order of Complexity

From the following chart by [Geeks for Geeks](https://www.geeksforgeeks.org/analysis-algorithms-big-o-analysis/), we can visualise the differences in complexity for various Big-O values from **O(1)** to **O(**_**n**_**!)**. This shows us that there is indeed a large difference between each level of Big-O complexity.

![](<../.gitbook/assets/image (4).png>)

## What is a "good" algorithm?

![](../.gitbook/assets/travelling_salesman_problem.png)

As defined above, the Big-O of a given function may seem like it's unviable or a "wrong" solution. However, many algorithms in the real-world run in "_bad_" or "_worst_" time complexity. The nature of the problem itself dictates the complexity of the solution, and there is no correct or incorrect solution to a problem.

One of the most classically intractable Computer Science algorithm problems, the [Travelling Salesman Problem](https://en.wikipedia.org/wiki/Travelling_salesman_problem) is a kind of problem that has to be solved constantly in real life. [There is no perfect work-around](https://shotl.com/news/the-travelling-salesman-problem-in-the-modern-era) for the fact that it runs in a minimum of exponential time. 

## Big-O Common Functions

### Constant Time: `O(1)`

#### Description

Also known as constant time, **O(1)** time complexity means that regardless of how big the input of an algorithm is, the algorithm will still be able to complete in a fixed number of iterations.

**O(1)** space complexity means regardless of input size, the algorithm can complete using a fixed amount of additional space, e.g. a fixed number of variables or data structure size excluding the input data.

#### Example: Find the median element in a sorted array

Given a sorted input array of length _**n**_, find the median element of the array. Median refers to the element that is ranked _**n**_**/2 **in the sorting order. One might be tempted to do a for loop over the array and return when the index is _**n**_**/2**, but this would be an **O(**_**n**_**)** algorithm because the number of iterations is linear based on _**n**_. Instead, since the array is sorted, we can access the middle element directly with `arr[len(arr)/2]`. This operation does not depend on the size of _**n**_, since the array length is readily available and accessing elements in an array by index is a single operation. This algorithm that immediately retrieves the middle element by index runs in **O(1)** time.

The above algorithm also runs in **O(1)** space complexity because it does not require additional variables other than the input array.

### Log Time: `O(logn)`

#### Description

Also known as logarithmic or logn ("log n") time, **O(**_**logn**_**)** complexity means that the algorithm will need to perform a number of operations proportional to the log of the size of the input. Without getting into too much math, **log(**_**n**_**)** represents the exponent necessary to raise a constant number (typically 2 or 10, the exact number doesn't matter in Big-O) to the value of _**n**_. For example, assuming a log of base 2, _**log**_**(2) **would be 1, and _**log**_**(1024)** would be 10. Notice how even though the value of `n` increased by 1000+ between the 2 examples, the value of _**log**_**(**_**n**_**)** only increased by roughly 10. Thus _**log**_**(**_**n**_**)** is significantly less than _**n**_ at large numbers. 

#### Example: Find the element with value `x` in a sorted array

Given a sorted input array of length _**n**_, find the position of an element with value **x**. A naïve solution would be to iterate over every element in the array until we find **x**, but this would run in **O(**_**n**_**) **or linear time because we would need to search through n elements at most, in the event that **x** were at the end of the array. A more optimal solution would be to perform binary search over the array, which runs in **O(log**_**n**_**) **time. Binary search works by splitting a sorted array into halves recursively until it finds the relevant element. This would require us to compare at most on the order of **log(**_**n**_**) **elements. For example, if my input array were numbers from 1 to 1000, e.g. \[1, 2, ..., 1000], to perform binary search on this array, I would first look for the middle element at index _**n**_**/2,** and compare it with **x**. If `x == arr[n/2]`, return `n/2` as the index of x. If `x > arr[n/2]`, repeat the same process on the right half of arr. If `x < arr[n/2]`, repeat the same process on the left half of `arr`. Read more about binary search [here](https://www.geeksforgeeks.org/binary-search/).

The above algorithm runs in **O(1)** space because it does not require additional variables beyond the input elements.

### Linear Time: _`O(n)`_

#### Description

Known as linear time, **O(**_**n**_**)** complexity means that the algorithm needs to inspect at most each element of the input a constant number of times. 

#### Example: Find the largest number in an unsorted array

Given an unsorted input array of numbers of length n, find the position of the largest number. We cannot perform binary search on this array because it is unsorted and we do not know the value of the largest number. If the array were sorted, we could extract the last element of the array which would be the largest number in **O(1)** time. The fastest sorting algorithms take **O(**_**nl**_**og**_**n**_**)** time complexity. Thus the best method we have is to iterate over each element of the array linearly (i.e. a for loop) until we reach the end of the array and confirm the largest number, which would take **O(**_**n**_**) **time complexity.

The above algorithm runs in **O(1)** space because it does not require additional variables beyond the input elements.

### Loglinear Time: `O(nlogn)`

#### Description

**O(**_**n**_**log**_**n**_**)** complexity typically involves performing a binary-search-like operation for every element in the input.

#### Example: Sort an unsorted array of numbers

It's rare to invent a sorting algorithm from scratch. Computer scientists have been working on efficient sorting algorithms since the start of the field, and so far they have concluded that [Merge Sort](https://en.wikipedia.org/wiki/Merge_sort) is the fastest sorting algorithm (in the worst case) that exists today, and it runs in **O(**_**n**_**log**_**n**_**)** time. Thus whenever we are given a problem to sort an unordered list, our first instinct should be to think that this could run in **O(**_**n**_**log**_**n**_**)** time.

Companies rarely ask candidates to implement sorting algorithms such as merge sort in interviews because it's the kind of answer that can be memorised. It doesn't hurt to memorise how common sorting algorithms such as merge sort work, but there's no need to spend too much time on them other than to understand how they work.

The above Merge Sort algorithm runs in **O(**_**n**_**)** space because at any given time it requires temporary storage space on the order of n elements in addition to the input data.

### **Quadratic Time:** `O(n²)`

#### Description

_**O(n²)**_ complexity typically involves nested loops over an input collection. 

#### Example: Find all pairs of numbers in an array

Given an array of numbers, find all unordered pairs of those numbers. This problem requires us to loop through each element of the array, and for each element of the array, loop through each other element of the array. This is a classic _**O(n²)**_ -complexity algorithm.

The above algorithm requires **O(**_**n**_**)** space during calculation, but its output will require space proportional to the size of the output, roughly _**n**_**C2** or "_**n**_ choose 2".

### Exponential Time: `O(2ⁿ)`

#### Description

Also known as exponential complexity, **`O(2ⁿ)`** complexity (and any **`O(Cⁿ)`** complexity where **C** is a constant) is the highest order of complexity (without combining it with itself or others above) and typically bad. If you find that your algorithm runs in exponential complexity in a DS\&A interview, there is probably a more efficient algorithm to solve the problem.

#### Example: Calculate the n-th Fibonacci Number

The Fibonacci sequence is defined as **Fib(**_**n**_**) = Fib(**_**n**_**-1) + Fib(**_**n**_**-2)**, where** Fib(0) == 1** and **Fib(1) == 1**. The naïve way to solve Fibonacci is to write a recursive algorithm that calculates **Fib(**_**n**_**)** by calling **Fib(**_**n**_**-1)** and **Fib(**_**n**_**-2)**. However, this results in 2 operations per Fib operation, and because each Fib operation runs recursively, we end up with **2ⁿ** operations because it would take n levels of Fib operations to reach the base cases of **Fib(0) **and **Fib(1)**. Interestingly, this problem can be solved in **O(**_**n**_**) **time complexity. See [here](https://stackoverflow.com/questions/18172257/efficient-calculation-of-fibonacci-series) for solution. 

The **O(2ⁿ) **time complexity algorithm above also requires **O(2ⁿ)** space complexity because at any given time, there will be up to **O(2ⁿ) **simultaneous function calls, thus **O(2ⁿ)** intermediate Fib calculations in memory. However, the optimal** O(n)** time complexity solution only requires **O(1)** space complexity because it only uses a finite number of variables to calculate **Fib(n)**, regardless of _**n**_.

### Factorial Time: `O(n!)`

A naive solution to finding all permutations of an array:

```
permutations([1, 2, 3])
```

where the solution would be:

```
[1, 2, 3]
[1, 3, 2]
[2, 1, 3]
[2, 3, 1]
[3, 1, 2]
[3, 2, 1]
```

is an example of a factorial complexity algorithm.

The Travelling Salesman algorithm referenced above is also an example of a problem that can be written naively as _**n**_**!**.

## Further Reading

{% embed url="https://www.youtube.com/watch?v=D6xkbGLQesk" %}

