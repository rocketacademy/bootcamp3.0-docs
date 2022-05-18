# A.5.2: Hash Tables

## Learning Objectives

1. Understand pros and cons of using hash tables
2. Understand how a hash table stores and retrieves values
3. Understand how to use hash tables to solve algorithm problems that require calculating frequencies of elements in a collection

## Introduction

A "hash table" is a data structure that stores key-value pairs with constant time (`O(1)`) lookup and insertion. It is also the computer science concept behind JavaScript objects. Every popular programming language has their own implementation of the hash table, such as Python Dictionaries and Java HashMaps.

We will use JS objects in a new way to solve algorithm problems. So far we have used JS objects primarily to store compound data such as playing cards, where it made sense to group card attributes such as name, rank and suit in a single data structure. We will now also use objects as frequency tallies.

## Pros and cons of hash tables

| Pros                               | Cons                    |
| ---------------------------------- | ----------------------- |
| `O(1)` lookup, insertion, deletion | `O(n)` space complexity |

Generally the speed benefits of using a hash table outweigh the impact of additional space required, and when there is algorithmic benefit to using a hash table we should use it.

## How does a hash table work?

Hash tables achieve `O(1)` lookup and insertion by "hashing" keys (typically strings) into array indexes with a constant-time "hash function", such that given a key it knows exactly where to retrieve or insert the relevant data and can access that data in constant time. Hash table implementations typically maintain a larger array size than number of key-value pairs to minimise "collisions" (multiple keys hashing to the same index) and maintain `O(1)` lookup and insertion.

## Common use case: frequency tally

### Example 1: Determine most popular candidate

Given 1000 votes, determine who is the winner

```javascript
const candidates = ["sam", "perry", "eng liang"]
const votes = []

// Create a random sample of 1000 votes
for (let i = 0; i < 1000; i++) {
  votes.push(candidates[Math.floor(Math.random(candidates.length))])
}
  
// Compile tally of how many votes each candidate received
const tally = {}
for (const candidate of votes) {
  if (candidate in tally) {
    tally[candidate] += 1
  } else {
    tally[candidate] = 1  
  }
}
  
// Determine who had most votes in the tally
// Initialise maxVotes to a minimum number
let maxVotes = 0;
let mostPopularCandidate;
Object.keys(tally).forEach((candidate) => {
  if (tally[candidate] > maxVotes) {
    maxVotes = tally[candidate];
    mostPopularCandidate = candidate;
  }
}

// mostPopularCandidate is the candidate with most votes in tally
console.log(`${mostPopularCandidate} wins!`);
```

### Example 2: Determine low-stock items

Given a number of fruits in stock, determine which fruits are low-stock and need replenishment

```javascript
// Generate fruits in a supermarket
fruitTypes = ["apple","pear","banana"]
fruitsInStore = []

// Create a random sample of 1000 fruits
for (let i = 0; i < 1000; i++) {
  fruitsInStore.push(fruitTypes[Math.floor(Math.random(fruitTypes.length))])
}

// Compile tally of how many of each fruit is in store
const tally = {}
for (const fruit of fruitsInStore) {
  if (fruit in tally) {
    tally[fruit] += 1
  } else {
    tally[fruit] = 1  
  }
}

// Determine which fruits are low-stock
LOW_STOCK_THRESHOLD = 300;
lowStockFruits = []
Object.keys(tally).forEach((fruit) => {
  if (tally[fruit] < LOW_STOCK_THRESHOLD) {
    lowStockFruits.push(fruit)
  }
}

// Output fruits with stock below the low stock threshold
console.log(lowStockFruits);
```

## Exercises

After attempting each problem, find solutions in either Solution or Discuss tabs on that problem's page. If you get stuck for more than 15 minutes, review and understand the solutions and move on. Come back and re-attempt the problem after a few days.

### Pre-Class

1. [https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)

### Part 1

1. [https://leetcode.com/problems/unique-number-of-occurrences/](https://leetcode.com/problems/unique-number-of-occurrences/)
2. [https://leetcode.com/problems/sum-of-unique-elements/](https://leetcode.com/problems/sum-of-unique-elements/)
3. [https://leetcode.com/problems/n-repeated-element-in-size-2n-array/](https://leetcode.com/problems/n-repeated-element-in-size-2n-array/)
4. [https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)
   1. Please ignore the constraint to implement this in constant space complexity because that involves a more advanced technique we haven't learned yet.

### Part 2

1. [https://leetcode.com/problems/uncommon-words-from-two-sentences/](https://leetcode.com/problems/uncommon-words-from-two-sentences/)
2. [https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/](https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/)
3. [https://leetcode.com/problems/find-common-characters/](https://leetcode.com/problems/find-common-characters/)
4. [https://leetcode.com/problems/maximum-number-of-balloons/](https://leetcode.com/problems/maximum-number-of-balloons/)
