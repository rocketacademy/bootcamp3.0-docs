# A.5.2: Hash Tables

![hash browns](../../../.gitbook/assets/hashbrowns.png)

## Learning Objectives

By the end of this lesson, you should:

* be familiar with hash functionality time and space complexity
* understand some basic python algorithm techniques with hashes

## Introduction

This section will eventually discuss the Hash Table, which is an abstract computer science data structure.

### Hash Table as Object / Dictionary

The first simple implementation we'll work with is a Python dictionary, which is an implementation of a hash map.

#### Keys and Values

Access to data given the crucial behavior of a hash table / Python dictionary / JavaScript object. Access to a value through a key is an **O(1)** operation, so it is a good way to store and retrieve data.

```javascript
var obj = {
  age: 12,
  height: 25,
};
// access a value
console.log(obj['height']);
```

```python
dictionary = {
    "age":12,
    "height":25
}
# access a value
print(dictionary["height"])
```

#### Why isn't a dictionary called a Hash Map?

The Python dictionary data structure is way to access a value through a key in **O(1)** time. In the easy Leetcode problems below we can assume that dictionary and hash map are synonymous because we are only thinking about the key/value access behaviour of the hash map data structure.

In a computer science context the importance of the hash map data structure references a point in the history of the field and in programming languages where such a key/value store did not exist by default- you had to create your own or use a library (for example in the C programming language). At the end of this section we'll have rebuilt everything needed for a dictionary using only primitive types like lists, strings and integers. This will also be similar for other very basic data structures we'll see where things like stacks, queues and linked lists, which do have more modern Python equivalents but for DS\&A we are more concerned with conceptual understanding rather than easy to write code. Also [see D.5.2.1](a.5.2.1-hash-table-data-structure.md) for how Python dictionaries and JavaScript objects work under the hood.

## Hash Table Usage Examples

In DSA problems, we don't need to implement a hash map class. _**We are normally just going to use Python's built-in dictionary.**_ They are typically used for 1 of 2 purposes.

1. Tally frequencies of elements in a collection
2. Creating mappings between values and relevant metadata, for example between values in an array and their corresponding indices.

### Tallying Frequencies:

Example card frequencies from module [0.4: JS Object as Tally](../../../0-language-and-tooling/0.4-js-object-as-tally.md):

```javascript
// Create shuffled deck
var deck = shuffleCards(makeDeck());

// Create hand array of 5 cards
var hand = [];
for (let i = 0; i < 5; i += 1) {
  hand.push(deck.pop());
}

// Create Object as tally
var cardNameTally = {};

// Loop over hand
for (let i = 0; i < hand.length; i += 1) {
  var cardName = hand[i].name;
  // If we have seen the card name before, increment its count
  if (cardName in cardNameTally) {
    cardNameTally[cardName] += 1;
  }
  // Else, initialise count of this card name to 1
  else {
    cardNameTally[cardName] = 1;
  }
}
```

#### Count Votes

Given a random set of votes:

```javascript
from random import choice

# Generate votes
candidates = ["sam", "perry", "eng liang"]
votes = []
for _ in range(1000):
  # Append 1000 random (of 3 choices) candidates to votes array
  votes.append(choice(candidates))
```

```javascript
# Compile a tally of how many times an element appears in an array
# The tally is stored in a dictionary.
def get_winner(votes):
  # Compile tally
  tally = {}
  for person in votes:
    if person not in tally:
      tally[person] = 0
    tally[person] += 1

  # Return the person with max votes as the winner
  max_votes = max(tally.values())
  for person, vote_count in tally.items():
    if vote_count == max_votes:
      return person

# Output winner
print(get_winner(votes))
```

#### Determine Low-Stock Items

```javascript
"""Example 2: Determine low-stock items"""

# Generate fruits in a supermarket
fruit_types = ["apple","pear","banana"]
fruits = [choice(fruit_types) for _ in range(1000)]

# Compile a tally of how many times an element appears in an array
def get_low_stock(ls_of_fruits, threshold):
  ''' Return names of stock that are low (below threshold, an int) '''
  # Compile tally
  tally = {}
  for fruit in fruits:
    if fruit not in tally:
      tally[fruit] = 1
    else:
      tally[fruit] += 1

  # Compile elements in tally that have a count below a threshold
  result = []
  for fruit, count in tally.items():
    if count < threshold:
      result.append(fruit)
  return result

# Output low-stock items
print(get_low_stock(fruits, 330))
```

### Create Mapping / References

Be able to look up a string given an index, but also an index given a string.

```python
# Create a map from name to index
def name_to_index(list_of_names):
  d = {}
  for index, name in enumerate(list_of_names):
    d[name] = index
  return d

# Create a map from index to name
def index_to_name(list_of_names):
  d = {}
  for index, name in enumerate(list_of_names):
    d[index] = name
  return d
```

Create data for a tournament. We want to be able to get the finishers and also their results.

```python
tournament_finishers = ["eng liang", "perry", "sam"]
nti = name_to_index(tournament_finishers)
itn = index_to_name(tournament_finishers)

# given a name, get their place in the tournament
nti["perry"] # 1 ==> perry got 2nd

# given a place, get the name of that person
itn[1] # perry was in 2nd place
```

## Exercises

Once you've attempted each problem, find solutions in the Discuss tab on that problem's page.

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
