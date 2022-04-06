# D.5.2.1: Hash Table Data Structure

![](../../../.gitbook/assets/hash_meme.jpeg)

We've been using dictionaries as built-in Python data structures, but in this section we'll build a hash map class from scratch.

### Hash Functions

From the context of a simpler, older language we'll see just how much complexity there is behind the ability to create a dictionary and access values inside.

```python
dictionary = {
    "age":12,
    "height":25
}

# when you mention the "height" string key, how
# does Python know to give back the value 25?
print(dictionary["height"])
```

Before we can dive into the storing of the data itself we need to talk about the association of the key with the value inside the hash map data structure. We've already seen the idea of "hashing" a value is JavaScript in [Password Hashing 3.5.3](../../../3-backend-applications/3.5-authentication/3.5.3-password-hashing.md). We'll use a very similar algorithm to associate hash map keys with hash map values.

We saw in section 3.5.3 that cryptographic hashing functions have 4 properties:

1. Consistency - always give back the same value
2. Consistent length - in the context of hash maps, "fixed length" hash output
3. Output not related to input
4. Rarely repeat for different inputs

Cryptographic hash algorithms are a superset of normal hash algorithms. We're going to create a similar algorithm that we can use to associate a hash map key with a value, but because we are not doing cryptography we can throw away property #3.

We also need to state one other property which we didn't mention before- that we can consider the complexity of this function to be **O(1)**. (Which isn't true in all cryptographic hash algorithm cases or even all hash map cases.)

```python
def hash_function(input_string: str, size: int):

  for character in input_string:
    # convert the char to an ASCII int using ord
    char_to_int = ord(character)
    # add it to the total
    result += char_to_int

  # return the sum mod size
  # return a num from 0 size
  return result % size
```

```python
# pythonic (idiomatic) version
def hash_function(input_string: str, size: int):
  return sum([ord(ch) for ch in input_string]) % size
```

This function takes any length string value and outputs an integer value.

```python
print(hash_function("happy", 10)) #6
print(hash_function("debit card", 10)) #2
print(hash_function("bad credit", 10)) #2
print(hash_function("dirtyroom", 10)) #1
print(hash_function("dormitory", 10)) #1
```

### Hash Collisions

Note how different inputs can result in the same output. This is referred to as a "_**collision**_". Here it's because two words have the same letters. We can make some simple improvements to the code to make it take letter position into account.

```python
def hash_function(input_string: str, size: int):

  for i, character in enumerate(input_string):
    # convert the char to an ASCII int using ord
    char_to_int = ord(character)
    # add it to the total
    # make an exponent of the char position
    # and the char int
    result += char_to_int ** (i+1)

  # return the sum mod 10
  # return a num from 0 9
  return result % size


print(hash_function("dormitory", 10) == hash_function("dirtyroom", 10)) #false
print(hash_function("debit card", 10) == hash_function("bad credit", 10)) #false
```

### Using the Hash Function to Create a Hash Map

Now we know what a hash function is, let's reimplement the Python dictionary inside a class using the `hash_function` to set and retrieve the key's value.

From [here](https://www.geeksforgeeks.org/hash-map-in-python/).

```python
class HashTable:

    # Create empty bucket list of given size
    def __init__(self, size):
        self.size = size
        self.hash_table = self.create_buckets()

    def create_buckets(self):
        return [[] for _ in range(self.size)]

    # Insert values into hash map
    def set_val(self, key, val):

        # Get the index from the key
        # using hash function
        hashed_key = hash_function(key, self.size)

        # Get the bucket corresponding to index
        bucket = self.hash_table[hashed_key]

        found_key = False
        for index, record in enumerate(bucket):
            record_key, record_val = record

            # check if the bucket has same key as
            # the key to be inserted
            if record_key == key:
                found_key = True
                break

        # If the bucket has same key as the key to be inserted,
        # Update the key value
        # Otherwise append the new key-value pair to the bucket
        if found_key:
            bucket[index] = (key, val)
        else:
            bucket.append((key, val))

    # Return searched value with specific key
    def get_val(self, key):

        # Get the index from the key using
        # hash function
        hashed_key = hash_function(key, self.size)

        # Get the bucket corresponding to index
        bucket = self.hash_table[hashed_key]

        found_key = False
        for index, record in enumerate(bucket):
            record_key, record_val = record

            # check if the bucket has same key as
            # the key being searched
            if record_key == key:
                found_key = True
                break

        # If the bucket has same key as the key being searched,
        # Return the value found
        # Otherwise indicate there was no record found
        if found_key:
            return record_val
        else:
            return "No record found"

    # Remove a value with specific key
    def delete_val(self, key):

        # Get the index from the key using
        # hash function
        hashed_key = hash_function(key, self.size)

        # Get the bucket corresponding to index
        bucket = self.hash_table[hashed_key]

        found_key = False
        for index, record in enumerate(bucket):
            record_key, record_val = record

            # check if the bucket has same key as
            # the key to be deleted
            if record_key == key:
                found_key = True
                break
        if found_key:
            bucket.pop(index)
        return

    # To print the items of hash map
    def __str__(self):
        return "".join(str(item) for item in self.hash_table)
```

Use the class:

```python
hash_table = HashTable(10)

# insert some values
hash_table.set_val('gfg@example.com', 'some value')
print(hash_table)
print()

hash_table.set_val('portal@example.com', 'some other value')
print(hash_table)
print()

# search/access a record with key
print(hash_table.get_val('portal@example.com'))
print()

# delete or remove a value
hash_table.delete_val('portal@example.com')
print(hash_table)
```

#### More Hash Collisions

What happens when two values create the same fixed-length output value?

#### Hash Collision Functions

There are two ways to deal with hash collisions:

1. Open Addressing Algorithm
2. Chaining Algorithm

## Further Reading

{% embed url="https://www.youtube.com/watch?v=sfWyugl4JWA" %}

#### Hash Functions

[https://www.geeksforgeeks.org/what-are-hash-functions-and-how-to-choose-a-good-hash-function/](https://www.geeksforgeeks.org/what-are-hash-functions-and-how-to-choose-a-good-hash-function/)

#### Hash Table Implementation in Python

[http://thepythoncorner.com/dev/hash-tables-understanding-dictionaries/](http://thepythoncorner.com/dev/hash-tables-understanding-dictionaries/)\
[https://www.youtube.com/watch?v=npw4s1QTmPg](https://www.youtube.com/watch?v=npw4s1QTmPg)

#### JavaScript Objects are not Hash Maps

[https://stackoverflow.com/questions/6586670/how-does-javascript-vm-implements-object-property-access-is-it-hashtable](https://stackoverflow.com/questions/6586670/how-does-javascript-vm-implements-object-property-access-is-it-hashtable)

JS object value properties are accessed through hidden classes:

[https://v8.dev/blog/fast-properties](https://v8.dev/blog/fast-properties)\
[https://www.infoq.com/presentations/javascript-objects-spidermonkey/](https://www.infoq.com/presentations/javascript-objects-spidermonkey/)

#### Hash Table Theory

See [this article](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/) for a brief explanation of hash table theory.
