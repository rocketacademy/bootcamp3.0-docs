# A.5.2: Hash Tables

## Learning Objectives

1. Understand pros and cons of using hash tables
2. Understand common use cases of hash tables in algorithm problems

## Introduction

A "hash table" is a data structure that stores key-value pairs with constant time (`O(1)`) lookup and insertion. It is also the computer science concept behind JavaScript objects. Every popular programming language has their own implementation of the hash table, such as Python Dictionaries and Java HashMaps.

We will use JS objects in new ways to solve algorithm problems. So far we have used JS objects primarily to store compound data such as playing cards, where it made sense to group card attributes such as name, rank and suit in a single data structure. We will now also use objects as frequency tallies and maps between multiple data formats.&#x20;

## Pros and cons of hash tables

| Pros                               | Cons                    |
| ---------------------------------- | ----------------------- |
| `O(1)` lookup, insertion, deletion | `O(n)` space complexity |

Generally the speed benefits of using a hash table outweigh the impact of additional space required, and when there is algorithmic benefit to using a hash table we should use it.

## How does a hash table work?

Hash tables achieve `O(1)` lookup and insertion by "hashing" keys (typically strings) into array indexes with a constant-time "hash function", such that given a key it knows exactly where to retrieve or insert the relevant data and can access that data in constant time. Hash table implementations typically maintain a larger array size than number of key-value pairs to minimise "collisions" (multiple keys hashing to the same index) and maintain `O(1)` lookup and insertion.

## Common uses of hash tables for algorithms

Hash tables are typically used for 1 of 2 reasons in algorithm problems.

1. Tally frequencies of elements in a collection
2. Create mappings between values and relevant metadata, e.g. between values in an array and their corresponding indexes

### Tally Frequencies

In the following example we count the frequency of each playing card name in a 5-card hand. This can help us determine what kind of poker hand this player has.

```javascript
// Create shuffled deck
var deck = shuffleCards(makeDeck());

// Create hand array of 5 cards
var hand = [];
for (let i = 0; i < 5; i += 1) {
  hand.push(deck.pop());
}

// Create object as tally
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
