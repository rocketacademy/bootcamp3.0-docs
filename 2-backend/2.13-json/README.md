# 2.13: JSON

## Why JSON?

So far we have successfully stored data in raw files. This is fine for small amounts of data, but can get messy for larger amounts of more complex data that we will encounter. JSON is a commonly-used file format to store data in a more structured way, that we can parse more efficiently using our programs, e.g. as arrays or JS Objects.

We will use JSON as a temporary form of database while we first learn other aspects of building applications. Once we're more familiar with app building, we will learn a more common database language and framework called SQL. Despite the popularity of SQL, JSON-like "NoSQL" databases continue to be a popular form of database regularly used in modern applications for performance and space reasons.

## What is JSON?

JSON stands for JavaScript Object Notation. JSON can be used with any language, but is named after JS because of its syntactic similarity to JS Objects. We will use JSON to store data in files such that our programs can read the data as JS Objects instead of raw lines of text. The following is an example.

```javascript
{
  "firstName": "John",
  "lastName": "Smith",
  "isAlive": true,
  "age": 27
}
```

The following are fundamental JSON formatting rules.

1. Keys must be strings surrounded by quotes.
2. All strings must use double quotes, not single quotes.
3. No trailing commas allowed, i.e. the last key-value pair in a list should not have a trailing comma.

JSON allows us to nest array and JS Object-like data structures like in the following example. Typical uses of JSON almost always consist of nested data structures, such as arrays of objects.

```javascript
{
  "firstName": "John",
  "lastName": "Smith",
  "isAlive": true,
  "age": 27,
  "address": {
    "streetAddress": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postalCode": "10021-3100"
  },
  "phoneNumbers": [
    {
      "type": "home",
      "number": "212 555-1234"
    },
    {
      "type": "office",
      "number": "646 555-4567"
    }
  ],
  "children": [],
  "spouse": null
}
```

## How to Use JSON?

### `JSON.parse`

JS has a built-in `JSON` library to handle JSON, not unlike the `Math` library that we've used in Basics. In the following example, we show how a string containing JSON \(e.g. one that might be read from a JSON file\) can be converted to a JS Object with the built-in `JSON.parse` method. Once converted, we can access the JSON data using regular JS Object syntax. If the outer-most data structure in the JSON string were an array, `JSON.parse` would return an array data structure instead.

```javascript
// We can't do: myUserJson.name
const myUserJson = '{"name":"kai","height":4}'; 
// We can do: myUserObj.name
const myUserObj = JSON.parse(myUserJson); 
```

### `JSON.stringify`

The opposite of `parse` is `stringify`. `stringify` takes an array or JS Object and turns it into a JSON string. This is useful for saving data to disk, because there is no way to directly write an array or JS Object to a file without first converting it to string format.

```javascript
const myUserObj = {
  name: 'kai',
  age: 21,
};
// While our data is in a JS Object, we can modify its values easily.
myUserObj.age = Math.random(); 
// Once ready to save data, convert to string before writing to disk.
const myUserJson = JSON.stringify(myUserObj);
```

## Exercise

1. Try out JSON `parse` and `stringify` methods in the Chrome DevTools console. Verify they do what you expect.

