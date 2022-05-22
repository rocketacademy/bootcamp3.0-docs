# A.3: Object-Oriented Programming

## Learning Objectives

1. Object-oriented programming (OOP) is the concept behind JavaScript classes (and classes in other languages)
2. We will use OOP to model non-built-in data structures such as linked lists, trees, graphs and heaps with relevant classes for each data structure
3. OOP helps us group related data and functions together, potentially simplifying code logic

## Introduction

Object-oriented programming (OOP) is the concept that data in our apps can be organised into conceptual entities called **"objects"** (unrelated to JavaScript objects), also known as **"classes"**. In an app context, `User` could be 1 such class, where a user could have multiple attributes such as name, email, password, and also multiple **"methods"** (another word for functions that are part of a class) that perform functionality on specific user **"instances"**. An "instance" is 1 instantiation of a class, e.g. a `User` instance that represents Kai. 1 example of a method on the `User` class could be `validatePassword`, which might hash an input password and verify if it matches the user's hashed password in the database.

We have already used classes extensively in Coding Bootcamp, perhaps unknowingly. For example, the `push` and `pop` methods on arrays in JavaScript are examples of methods in the `Array` class.  Refer to [0.4.4: JavaScript classes](../0-foundations/0.4-javascript/0.4.4-classes.md) for a refresher on class syntax.

OOP is a controversial design pattern and is used in some places and not others. Classes are optional in languages like JavaScript and Python; classes are the only way to write code in languages like Java.

In the algorithm context, we will use OOP to work with non-built-in data structures to help us solve problems more efficiently. These new data structures include linked lists, trees, graphs and heaps.

## 4 Benefits of OOP

The following knowledge is for context and not strictly necessary for solving algorithm problems.

Below are the 4 primary benefits of OOP to help us get a sense of why OOP can be helpful.

{% embed url="https://www.youtube.com/watch?v=pTB0EiLXUC8" %}
Visual explanation of the 4 benefits of OOP. Source: Coding with Mosh
{% endembed %}

### 1) Encapsulation: Data and methods together

One of the primary benefits of classes is to "encapsulate" data into a class instance, and use class methods to manipulate that data. Without OOP we would write code "procedurally" or "functionally", resulting in more variables to keep track of, and more context to pass into each function.

### 2) Abstraction: Simplify interfaces

We can think of classes as libraries that we import: We do not need to know how library functions are implemented, we only need to know what they do and how to use them.&#x20;

### 3) Inheritance

Inheritance is a way to re-use code such that instead of multiple classes re-using the same or similar functionality, we can have 1 base class that implements the shared functionality and "child" or "inherited" classes that "inherit" the base class' functionality before adding their own.

### 4) Polymorphism

Polymorphism means the same method can be implemented differently for different classes. For example, a hypothetical `greeting` method could produce different results between instances of `AmericanPerson` and `ChinesePerson` classes.

## Additional Resources

[Here is freeCodeCamp's introduction to OOP](https://www.freecodecamp.org/news/four-pillars-of-object-oriented-programming/) with more details.
