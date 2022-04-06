# A.13: Open Practice

## Introduction

The following is a list of curated Leetcode problems we can work on daily after learning algorithms fundamentals. The problems are taken from the [Top Interview Questions list in Leetcode](https://leetcode.com/problemset/all/?listId=wpwgkgt\&page=1\&sorting=W3sic29ydE9yZGVyIjoiREVTQ0VORElORyIsIm9yZGVyQnkiOiJBQ19SQVRFIn1d), sorted in decreasing acceptance rate, i.e. % of submissions that were accepted on Leetcode.

The majority of algorithms interviews Rocket grads have encountered have focused on arrays and hash tables. If you find yourself stuck on a problem focusing on a different data structure, feel free to skip and focus on the array and hash tables problems first.

## Exercises

### Day 1

1. [https://leetcode.com/problems/reverse-string/](https://leetcode.com/problems/reverse-string/)
2. [https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
3. [https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)

### Day 2

1. [https://leetcode.com/problems/binary-tree-inorder-traversal/](https://leetcode.com/problems/binary-tree-inorder-traversal/)
   1. Feel free to skip the follow up question to implement this traversal iteratively. The iterative implementation is challenging and unlikely to appear in coding interviews.
2. [https://leetcode.com/problems/reverse-linked-list/](https://leetcode.com/problems/reverse-linked-list/)
   1. FTBC3 strategy video: [https://youtu.be/a5fTAdAv3\_A?t=3101](https://youtu.be/a5fTAdAv3\_A?t=3101)
3. [https://leetcode.com/problems/subsets/](https://leetcode.com/problems/subsets/)

### Day 3

1. [https://leetcode.com/problems/fizz-buzz/](https://leetcode.com/problems/fizz-buzz/)
2. [https://leetcode.com/problems/kth-smallest-element-in-a-bst/](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)
   1. Hint: How can we traverse a BST in sorted order?
3. [https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)
   1. Hint: Recall our solution to the kth-largest element in a stream problem: [https://leetcode.com/problems/kth-largest-element-in-a-stream/](https://leetcode.com/problems/kth-largest-element-in-a-stream/)

### Day 4

1. [https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)
   1. Hint: To instantiate a `TreeNode` class, the syntax is `new_node = TreeNode(...)`, replacing `...` with the initialisation parameters.
2. [https://leetcode.com/problems/product-of-array-except-self/](https://leetcode.com/problems/product-of-array-except-self/)
   1. Hint: Solving this in O(n) without division is a bit of a trick. Feel free to solve it with division and move on.
   2. If you're keen on solving it without division: Can we pre-process the data and create intermediate data structures in O(n) time such that we can then fill in the `answer` array with a single loop?

### Day 5

1. [https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)
2. [https://leetcode.com/problems/group-anagrams/](https://leetcode.com/problems/group-anagrams/)
   1. Hint: What combination of arrays and hash tables can we use to group anagrams?
   2. Rocket solution code: [https://pastebin.com/pfM6JiTx](https://pastebin.com/pfM6JiTx)
   3. Rocket solution video: [https://youtu.be/yVCKfkJWHfQ?t=5281](https://youtu.be/yVCKfkJWHfQ?t=5281)

### Day 6

1. [https://leetcode.com/problems/kth-largest-element-in-an-array/](https://leetcode.com/problems/kth-largest-element-in-an-array/)
2. [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

### Day 7

1. [https://leetcode.com/problems/move-zeroes/](https://leetcode.com/problems/move-zeroes/)
2. [https://leetcode.com/problems/odd-even-linked-list/](https://leetcode.com/problems/odd-even-linked-list/)
3. \[REMOVE] [https://leetcode.com/problems/excel-sheet-column-number/](https://leetcode.com/problems/excel-sheet-column-number/)
   1. Hint: This is a base-26 numbering system. Requires a more math background to understand how numbers and exponents work. Feel free to skip.

### Day 8

1. [https://leetcode.com/problems/roman-to-integer/](https://leetcode.com/problems/roman-to-integer/)
2. [https://leetcode.com/problems/binary-tree-level-order-traversal/](https://leetcode.com/problems/binary-tree-level-order-traversal/)
   1. Rocket solution code: [https://pastebin.com/P6qJZfux](https://pastebin.com/P6qJZfux)
   2. FTBC3 solution video: [https://youtu.be/J0gohhbwN0w?t=6464](https://youtu.be/J0gohhbwN0w?t=6464)
3. [https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)

### Day 9

1. [https://leetcode.com/problems/merge-two-sorted-lists/](https://leetcode.com/problems/merge-two-sorted-lists/)
   1. Rocket solution code: [https://pastebin.com/GFxESn8Q](https://pastebin.com/GFxESn8Q)
   2. FTBC3 solution video: [https://youtu.be/3mFkTJ1vvyA?t=2492](https://youtu.be/3mFkTJ1vvyA?t=2492)
2. [https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)

### Day 10

1. [https://leetcode.com/problems/pascals-triangle/](https://leetcode.com/problems/pascals-triangle/)
2. [https://leetcode.com/problems/unique-paths/](https://leetcode.com/problems/unique-paths/)

### Day 11

1. [https://leetcode.com/problems/flatten-nested-list-iterator/](https://leetcode.com/problems/flatten-nested-list-iterator/)
   1. Completing this problem will help us understand how to use and implement classes in Python.
   2. Hint: An iterator works like this: Each time we call `next()` on the iterator it will return the next element in the collection. When the iterator is "exhausted", i.e. we have reached the end of the collection, `next()` will return `None`.
   3. Hint: For a refresher on how to use and implement classes in Python, see [code examples from RA's OOP module](https://bootcamp.rocketacademy.co/data-structures-and-algorithms/d.8-intro-to-object-oriented-programming#code-examples).
2. [https://leetcode.com/problems/4sum-ii/](https://leetcode.com/problems/4sum-ii/)

### Day 12

1. [https://leetcode.com/problems/number-of-1-bits/](https://leetcode.com/problems/number-of-1-bits/)
2. [https://leetcode.com/problems/first-unique-character-in-a-string/](https://leetcode.com/problems/first-unique-character-in-a-string/)

### Day 13

1. [https://leetcode.com/problems/container-with-most-water/](https://leetcode.com/problems/container-with-most-water/)
2. [https://leetcode.com/problems/palindrome-partitioning/](https://leetcode.com/problems/palindrome-partitioning/)

### Day 14

1. [https://leetcode.com/problems/implement-trie-prefix-tree/](https://leetcode.com/problems/implement-trie-prefix-tree/)
2. [https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

### Day 15

1. [https://leetcode.com/problems/intersection-of-two-arrays-ii/](https://leetcode.com/problems/intersection-of-two-arrays-ii/)
2. [https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

### Day 16

1. [https://leetcode.com/problems/trapping-rain-water/](https://leetcode.com/problems/trapping-rain-water/)

### Day 17

1. [https://leetcode.com/problems/happy-number/](https://leetcode.com/problems/happy-number/)
2. [https://leetcode.com/problems/valid-sudoku/](https://leetcode.com/problems/valid-sudoku/)

### Day 18

1. [https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)
2. [https://leetcode.com/problems/populating-next-right-pointers-in-each-node/](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

### Day 19

1. [https://leetcode.com/problems/serialize-and-deserialize-binary-tree/](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)

### Day 20

1. [https://leetcode.com/problems/letter-combinations-of-a-phone-number/](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)
   1. FTBC3 solution video: [https://youtu.be/Ha4iqs1ze2E?t=2831](https://youtu.be/Ha4iqs1ze2E?t=2831)
2. [https://leetcode.com/problems/number-of-islands/](https://leetcode.com/problems/number-of-islands/)

### Day 21

1. [https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)
2. [https://leetcode.com/problems/perfect-squares/](https://leetcode.com/problems/perfect-squares/)

### Day 22

1. [https://leetcode.com/problems/insert-delete-getrandom-o1/](https://leetcode.com/problems/insert-delete-getrandom-o1/)

### Day 23

1. [https://leetcode.com/problems/climbing-stairs/](https://leetcode.com/problems/climbing-stairs/)
2. [https://leetcode.com/problems/symmetric-tree/](https://leetcode.com/problems/symmetric-tree/)
3. [https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)

### Day 24

1. [https://leetcode.com/problems/find-median-from-data-stream/](https://leetcode.com/problems/find-median-from-data-stream/)

### Day 25

1. [https://leetcode.com/problems/min-stack/](https://leetcode.com/problems/min-stack/)
2. [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

### Day 26

1. [https://leetcode.com/problems/sort-list/](https://leetcode.com/problems/sort-list/)
2. [https://leetcode.com/problems/longest-consecutive-sequence/](https://leetcode.com/problems/longest-consecutive-sequence/)

### Day 27

1. [https://leetcode.com/problems/search-a-2d-matrix-ii/](https://leetcode.com/problems/search-a-2d-matrix-ii/)
2. [https://leetcode.com/problems/sliding-window-maximum/](https://leetcode.com/problems/sliding-window-maximum/)

### Day 28

1. [https://leetcode.com/problems/longest-increasing-path-in-a-matrix/](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/)

### Day 29

1. [https://leetcode.com/problems/set-matrix-zeroes/](https://leetcode.com/problems/set-matrix-zeroes/)
2. [https://leetcode.com/problems/course-schedule/](https://leetcode.com/problems/course-schedule/)

### Day 30

1. [https://leetcode.com/problems/intersection-of-two-linked-lists/](https://leetcode.com/problems/intersection-of-two-linked-lists/)
2. [https://leetcode.com/problems/longest-increasing-subsequence/](https://leetcode.com/problems/longest-increasing-subsequence/)

### Day 31

1. [https://leetcode.com/problems/linked-list-cycle/](https://leetcode.com/problems/linked-list-cycle/)
2. [https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/](https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/)

### Day 32

1. [https://leetcode.com/problems/house-robber/](https://leetcode.com/problems/house-robber/)
2. [https://leetcode.com/problems/course-schedule-ii/](https://leetcode.com/problems/course-schedule-ii/)

### Day 33

1. [https://leetcode.com/problems/merge-k-sorted-lists/](https://leetcode.com/problems/merge-k-sorted-lists/)
2. [https://leetcode.com/problems/reverse-bits/](https://leetcode.com/problems/reverse-bits/)

### Day 34

1. [https://leetcode.com/problems/count-of-smaller-numbers-after-self/](https://leetcode.com/problems/count-of-smaller-numbers-after-self/)

### Day 35

1. [https://leetcode.com/problems/word-break/](https://leetcode.com/problems/word-break/)
2. [https://leetcode.com/problems/gas-station/](https://leetcode.com/problems/gas-station/)

### Day 36

1. [https://leetcode.com/problems/palindrome-linked-list/](https://leetcode.com/problems/palindrome-linked-list/)
2. [https://leetcode.com/problems/merge-intervals/](https://leetcode.com/problems/merge-intervals/)

### Day 37

1. [https://leetcode.com/problems/copy-list-with-random-pointer/](https://leetcode.com/problems/copy-list-with-random-pointer/)

### Day 38

1. [https://leetcode.com/problems/valid-parentheses/](https://leetcode.com/problems/valid-parentheses/)
2. [https://leetcode.com/problems/merge-sorted-array/](https://leetcode.com/problems/merge-sorted-array/)
   1. FTBC3 solution video: [https://youtu.be/qRgOAQlNhVE?t=4814](https://youtu.be/qRgOAQlNhVE?t=4814)
3. [https://leetcode.com/problems/increasing-triplet-subsequence/](https://leetcode.com/problems/increasing-triplet-subsequence/)

### Day 39

1. [https://leetcode.com/problems/basic-calculator-ii/](https://leetcode.com/problems/basic-calculator-ii/)
2. [https://leetcode.com/problems/evaluate-reverse-polish-notation/](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

### Day 40

1. [https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
2. [https://leetcode.com/problems/coin-change/](https://leetcode.com/problems/coin-change/)
