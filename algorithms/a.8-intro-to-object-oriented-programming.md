# A.8: Object-Oriented Programming

![oop meme](../.gitbook/assets/oop_meme.jpeg)

## Introduction

Object-oriented programming \(OOP\) is the concept that data in our apps can be organised in conceptual entities called **"objects"** \(unrelated to JavaScript Objects\), also known as **"classes"**. In an app context, `User` could be 1 such class, where a user could have multiple attributes such as name, email, password, and also multiple **"methods"** \(another word for functions that are part of a class\) that perform functionality on specific user **"instances"**. An "instance" is 1 instantiation of a class, e.g. a `User` instance that represents Akira. 1 example of a method on the `User` class could be `validatePassword`, which might hash an input password and verify if it matches the relevant user's password.

We have already used classes extensively in Coding Bootcamp, perhaps unknowingly. For example, the `push` and `pop` methods on arrays in JavaScript are examples of methods in the `Array` class. The `user.name` attribute and `user.getItems` method on a user retrieved with Sequelize are examples of attributes and methods in the Sequelize `User` class that we define in our model file \(with Sequelize helper functions\).

In the Leetcode context, we will be using classes to define non-built-in data structures in Python to help us solve problems more efficiently. These new data structures will include linked lists, trees, and graphs. All of these data structures will be built on built-in features of Python.

{% hint style="warning" %}
Object Oriented Objects are different from JavaScript objects. We would generally refer to our usage of JavaScript objects so far as "hash maps". JavaScript objects are confusingly named the same but don't bear any resemblance to Object Oriented objects.
{% endhint %}

## Class and Object Syntax Review

### Creating a Class

A class by itself holds no data and does not do anything. It is the abstract representation of data. A class instantiation is an object.

```python
class Cat:
  def __init__(self, name):
    print("making a new cat")
    self.name = name
  
  def get_name(self):
    # Return the .name attribute of the current instance
    return self.name
```

{% hint style="info" %}
Naming convention: Classes are typically named with UpperCamelCase. Instances are typically named with lowerCamelCase. This is the same as we have been doing with Sequelize model classes and instances in Bootcamp.
{% endhint %}

### Objects: Class Instances

Once we have defined a class we can create an instance of the class. An instance is the "_live_" instantiation of a class, made from the mold of the class definition. It has actual data inside, not just the variable names.

![class instance illustration](../.gitbook/assets/factory_gif.gif)

```python
cat1 = Cat("Kai")
cat2 = Cat("Chee Kean")

print(cat1.get_name())
print(cat2.get_name())  
```

#### Constructor

Notice that when a new `Cat` is created the `__init__` constructor method gets called \(and the print function gets called\). The **constructor** is an Object Oriented term that refers to a method that is called when an instance of the class is being created and is used to help set up the values inside of the instance.

#### `self` Keyword

When we write code that is for `cat1` and `cat2` we are going to be calling the instance methods inside the instance. How do we refer to each Cat \(i.e., `cat1` and `cat2`\) itself? The `self` keyword is used in Python to refer to the object from within the instance method. So here, `self.name` refers to the name _**inside**_ the cat when we call `cat1.get_name()` - "Kai" in one case and "Chee Kean" in the other- i.e., the `name` value refers to that instance if we are calling the function for `cat1` or `cat2.`

```python
  def get_name(self):
    # we can write a line to return the name for *any* instance
    return self.name
```

## Four Pillars of OOP Design

In Industry there is some disagreement about how to go about doing OOP, or [even to do it at all](https://en.wikipedia.org/wiki/Object-oriented_programming#Criticism). Four generally recognized principles are: _abstraction_, _encapsulation_, _inheritance_ and _polymorphism_. They were  codified at the height of OOP popularity in the 90's by the [Three Amigos](https://wiki.c2.com/?ThreeAmigos) and the [Gang of Four](http://wiki.c2.com/?GangOfFour). We'll see some examples for each below. Note that these kinds of programming design terms are not static nor are the universally agreed upon.

![Dijkstra quote](../.gitbook/assets/dijkstra-oop.jpeg)

{% embed url="https://www.youtube.com/watch?v=pTB0EiLXUC8" %}

## Encapsulation: Data & Methods Together

The main usage of objects when writing code is to take advantage of "_encapsulating_" data into a class  instance, and  using class methods to manipulate that data.

Without OOP we write code "procedurally" or "functionally"- if the following example were written without OOP, each person's variables and functions would be stored independently of each other, resulting in many variables to keep track of, and more context to pass into each function.

### Person Class

```python
'''
Define a class Person, that initializes (constructor) with 3 args: (name, age, is_male)
The object should contain the following attributes
1) name    (str)
2) age     (int)
3) is_male (bool)
4) weight  (int)
'''
class Person:
  # __init__ is the constructor method and used to initialise the class instance. Parameters passed to __init__ need to be passed in when we initialise the instance, for example Person('akira', '38', True)
  def __init__(self, name, age, is_male, weight):
    self.name = name       # set the .name attribute to name
    self.age = age         # set the .age attribute to age
    self.is_male = is_male # set the .is_male attribute to is_male
    self.weight = weight   # set the .weight attribute to weight
    # By the end of __init__, a new Person object is initialised. No need to return self.
  
  def get_name(self):
    # Return the .name attribute of the current instance
    return self.name 
  
  def get_age(self):
    return self.age
    
  def get_weight_pounds(self):
    return self.weight * 2.2
  
  def get_gender(self):
    if self.is_male == True:
      return "Male"
    else:
      return "Female"
```

#### Run the Code

```python
p1 = Person("Koi", 18, True, 60)
p2 = Person("Jan", 21, False, 70)

print(p1.name)    # "Koi"
print(p1.age)     # 18
print(p1.is_male) # True

print(p1.get_name())   # "Koi"
print(p1.get_age())    # 18
print(p1.get_gender()) # "Male"

print(p2.get_gender()) # "Female"
```

#### `get_weight_pounds`

This class instance method accesses data inside the object, makes a calculation and returns a value. Rather than having a separate helper function for conversion, it is built directly into the code representing the entire person. No arguments have to be passed into the method, because it can refer to the data inside itself.

```python
print(p1.get_weight_pounds())    # 132.2
```

## Abstraction

### Worker Class

```python
######################
# 2. Worker and Tool #
######################

class Worker:
  def __init__(self, name):
    self.name = name
    # Initialise self.tools to empty array for every Worker instance
    self.tools = []

  def pickup(self, tool):
    ''' Put tool in self.tools list if tool does not have owner '''
    # Do nothing if tool already has owner
    if not tool.owner:
      self.tools.append(tool)
      # Set tool's owner to the current Worker instance
      tool.owner = self

  def show_tools(self):
    ''' Print all tools in self.tools '''
    result_string = self.name + " has "
    if not self.tools:
      result_string += "nothing"
    else:
      result_string += str(len(self.tools)) + " tools: "
      for tool in self.tools:
        result_string += tool.name + ", "
      result_string = result_string[:-2] # drop off extra ", "
    print(result_string) 
    
  def dropall(self):
    ''' Drop all tools in self.tools list '''
    for tool in self.tools:
      # Reset tool owner to nobody
      tool.owner = None
    self.tools.clear()
```

### Tool Class

```python
class Tool:
  def __init__(self, name):
    # Tool has 2 attributes, name (set on initialisation) and owner (None by default)
    self.name = name
    self.owner = None
```

#### Run the Code

```python
# Study the code execution
tool1 = Tool("Hammer")
tool2 = Tool("Screwdriver")
tool3 = Tool("Drill")
tool4 = Tool("Hammer")

a = Worker("Aly")
b = Worker("Bob")

a.pickup(tool1)
a.show_tools() # Prints "Aly has Hammer"
a.pickup(tool2)
a.pickup(tool3)
a.show_tools() # Prints "Aly has 3 tools: Hammer, Screwdriver, Drill"

b.pickup(tool1) # nothing happens because tool1 is owned by Aly
b.show_tools() # Prints "Bob has nothing"
b.pickup(tool4)
b.show_tools() # Prints "Bob has Hammer"

a.dropall()
a.show_tools() # Prints "Aly has nothing"
b.pickup(tool1)
b.show_tools() # Prints "Bob has 2 tools: Hammer, Hammer"
```

When we call the show\_tools method, we don't need to worry about how the method code implements the string output. The class is abstracting the string manipulation complexities away.

This is the same whenever we use an NPM library- the library is abstracting away programming complexity we don't need to know about.

## Inheritance

Inheritance is a way to refactor the code such that, instead of two classes with similar functionality, we can have one class that gets everything the base class has, but adds on other logic and data. 

```python
class Robot:
    
    def __init__(self, name):
        self.name = name
        
    def say_hi(self):
        print("Hi, I am " + self.name)
        
class PhysicianRobot(Robot):

    def say_hi(self):
        print("Everything will be okay! ") 
        print(self.name + " takes care of you!")

y = PhysicianRobot("James")
y.say_hi()
```

Robot example from here: [https://www.python-course.eu/python3\_inheritance.php](https://www.python-course.eu/python3_inheritance.php)

## Polymorphism

Polymorphism is inheritance where the same base class can be inherited by multiple classes.

From [here](https://www.geeksforgeeks.org/polymorphism-in-python/). 

```python
class Bird:
  def intro(self):
    print("There are many types of birds.")
     
  def flight(self):
    print("Most of the birds can fly but some cannot.")
   
class sparrow(Bird):
  def flight(self):
    print("Sparrows can fly.")
     
class ostrich(Bird):
  def flight(self):
    print("Ostriches cannot fly.")
     
obj_bird = Bird()
obj_spr = sparrow()
obj_ost = ostrich()
 
obj_bird.intro()
obj_bird.flight()
 
obj_spr.intro()
obj_spr.flight()
 
obj_ost.intro()
obj_ost.flight()
```

## In-Class Exercise

Create a command line battle game.

#### Starter Code

```python
from random import randint


class Player:
    def __init__(self):
        self.hit_points = 10

    def take_damage(self, damage):
        self.hit_points -= damage
        if self.hit_points <= 0:
            print("dead!")
            return False
        return True


class Game:
    def __init__(self):
        self.opponents = []
        self.opponent = None
        self.player = Player()

        opponents_count = int(
            input("how many opponents do you want to fight? "))

        for i in range(opponents_count):
            self.opponents.append(Player())

        self.battle()

    def battle(self):
        self.opponent = self.opponents.pop()
        opponent_dice_roll = randint(1, 6)

        while self.opponent.take_damage(opponent_dice_roll):
            print("he's still alive")

        keep_going = input("keep fighting? y/n ")
        if keep_going == 'y':
            self.battle()


game = Game()
```

#### Player Hits

Add to the game so that the player can also take damage. End the game if they die.

#### Random Starting Hit Points

Start each opponent with variable hit points.

#### Monsters

Create a class Monsters that inherits from Player. Monsters can defend an attack a random number of damage between 1 and 3.

#### Player Weapons

The player begins the game with a sword weapon that does 1:1 damage. Every 3rd turn the player replaces their weapon with a brand new weapon  with damage between 1:1 to 1:7.

#### Player Weapon Armory

Create a list of weapons in the game. Use a dictionary: `{"sword":2,"mace":3}`.

The player gets to keep several weapons on hand. When they get a chance to get a new weapon, ask if they want to keep it. Throw away the oldest weapon.

#### Rooms

The player progresses through a series of rooms. The rooms are one after the other. Each room contains a random number of Monsters. Keep an array of rooms in the game.

#### Player Weapon Selection

Ask the player which weapons they want to keep and which they want to discard. Make inherited classes for each weapon.

#### Maze

Create a series of rooms. Players can navigate the rooms by turning left and right. Keep the rooms in a 2-D array. 

## Further Reading

### Helpful Videos

1. [This](https://www.youtube.com/watch?v=pTB0EiLXUC8) video introduces key concepts of OOP \(encapsulation, abstraction, inheritance, and polymorphism\) without getting into much code.
2. [This](https://www.youtube.com/watch?v=7Dai8SJgLkM) video explains the same key concepts of OOP with more code examples.

#### Four Pillars of OOP

[https://www.freecodecamp.org/news/four-pillars-of-object-oriented-programming/](https://www.freecodecamp.org/news/four-pillars-of-object-oriented-programming/)

