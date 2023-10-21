# Python

Mathematical, Logical and Comparison Operators

and needs all opertator to be true
or needs at least one to be true
not needs it to be false

## Match Statement

With the *match* statement allows to make massive *if-elif* more readable.

``` python

http_status = 200

match http_status:
	case 200 | 201:
		print('success')
	case 400:
		print('Bad Request')
	case 500 | 501:
		print('Server Error')
	case _:
		print('unknown')
```

## For loop

``` python
str = 'Looping'

for item in str:
	print(item)

# Goes from 0 to 9
for i in range(10):
	print(i)
	
favorites = ['Malina', 'Max', 'Peter', 'Freddy', 'Johann', 'Tenma']

# Prints each item in favorites individually
for item in favorites:
	print(item)
	
for index, item in enumerate(favorites):
	print(index, item)

```

## While loop

``` python
count = 0
favorites = ['Malina', 'Max', 'Peter', 'Freddy', 'Johann', 'Tenma']

while count < len(favorites):
	print(favorites[count])
```

## Break, Continue, Pass

### break
This stops the inner most current loop that is running and escapes out of it

### continue
Skips the rest of the code in this loop iteration and go directly to the next iteration of the loop. This does not exit the loop.

### pass
Basically just don't do anything


## Measure Time

``` python
import time

start_time = time.time()

# DO SOMETHING

end_time = time.time()
print(round((end_time - start_time), 2))
```


## Isinstance()

``` python
x = isinstance(5, int)
```

## Function Syntax

``` python
def <function name>(<params>):
	<task to complete>

def sum(a, b):
	return a + b
```

## Variable Scopes

Variable scope exists to control who can modify variables.

The scopes are *local-, enclosing-, global- and built-in scope*. 
**LEGB**


### Global Scope

* Accessible from within anywhere in the Code
* Generally speaking good to avoid global scope

### Built-in Scope

* Accessible from within anywhere in the Code
* Keywords like print


### Example
``` python
# Global scope
my_global = 10

def fn1():
	enclosed_v = 8
	
	def fn2():
		local_v = 5
		print('Access to Global', my_global)
		print('Access to Enclosed', enclosed_v)
	
	fn2()

fn1()
# Accessing the local variable here does not work. 
print(local_v) 
```


# Data Structures

Allows to organize and arrange data to perform operations on them. 

Python has the built-in data structures: **List**, **Dictionary**, **Tuple** and **Set**. They are **non-primitive** data structures. They are classed as *objects*.

With these the User can create his own data structures like **Stack**, **Queue** or **Tree**

Data structures can be **mutable** or **immutable**. Mutable data structures allow for the content of itself to change. A list for example is mutable. Its content can be deleted, changed things can be added to it. Immutable data structures do not allow their contents to change. Once they have been set they stay that way. Tuples are an example of immutable data structures in Python. 

## Lists

Lists are mutable. Their contents can be changed. The same value can be inside a list multiple times. 

``` python

list1 = [1, 2, 3, 4, 5]
list2 = ['A', 'B', 'C']
list3 = ['hello', 1, True, 40.22]
list4 = [1, [1, 2, 3], 3]

print(*list1) # Prints just the elements of the list
print(list1) # Prints the list as seen in the code
```


### Insert

``` python
list1 = [1, 2, 3, 4, 5]

# Inserts the element at the given index
# list.insert(index, obj)
list1.insert(len(list1), 6)

# Inserts the element at the end of the list
list1.append(6)

# Add a list to another list's end
list1.extend([6, 7, 8, 9])

# Removes and returnes the 5th element. I.e. the element at index 4
list1.pop(4)

# Delete the 3rd item in the list
del list1[2]

```

## Tuples

Tuples are immutable. The contents can not be changed.

``` python
my_tuple = (1, 'strings', 4.5, True)

# Prints 'strings'
print(my_tuple[1])

# Counts how often the value 'strings' appears in the tuple 
my_tuple.count('strings')

# Return the index of the value 4.5 in the tuple
# Can crash if not in list
my_tuple.index(4.5)

```

## Sets

Sets are mutable. Their contents can be changed. A value can only ever be contained once inside a set. The same value can never be contained twice within a set.

Sets are also not ordered. They **cannot** be accessed by index. Sets are not sequences like lists or strings.

``` python
set_a = {1, 2, 3, 4, 5}

# Adds the value 6 to the set. 
# Nothing changes if the value is already contained in the set
set_a.add(6)

# Removes a value from the set
set_a.remove(2)
set_a.discard(2)

set_a = {1, 2, 3, 4, 5}
set_b = {4, 5, 6, 7, 8}

# Combines two sets into one set - UNION
# Result will be {1, 2, 3, 4, 5, 6, 7, 8}
set_c = set_a.union(set_b)
set_c = set_a | set_b

# Gets all the elements that are in both sets - INTERSECTION
# Result will be {4, 5}
set_c = set_a.intersection(set_b)
set_c = set_a & set_b


# Returns all elements in set_a without the ones contained in set_b
# Result will be {1, 2, 3}
set_c = set_a.difference(set_b)
set_c = set_a - set_b

# Returns all elements that are not in both.
# Result will be {1, 2, 3, 6, 7, 8}
set_c = set_a.symmetric_difference(set_b)
set_c = set_a ^ set_b

```

## Dictionaries

In dictionaries **values** are assigned to **keys**. Accessing this is easier than in a List. In a list you have to keep track of the index for an element you want. In a dictionary you only need it's key to access a value.

You cannot have multiple values with the same key.

``` python
dict_a = {1: 'coffee', 2: 'tea', 3: 'juice'}

# Gets the value 'coffee'
dict_a[1]

# Changes the value for 2 to 'mint tea'
dict_a[2] = 'mint tea'

# Deletes 'juice' from the dictionary
del dict_a[3]

# Sets the value for the key 'test' to 3
# Result will be {1: 'coffee', 2: 'tea', 3: 'juice', 'test': 3}
dict_a['test'] = 3

```

## More...

[Python Data Structures](https://realpython.com/python-data-structures/)

## Args and Kwargs

If the number of inputs to a function can vary *args* can be used. These can be any number of *non keyword* arguments.

``` python
def sum_of(*args):
	sum = 0
	for x in args:
		sum += x
	return sum

sum_of(4, 5, 6)
sum_of(1, 2, 3, 4, 5)
sum_of(8)
```

With ***kwargs* any number of *keyword arguments* can be passed to a function

``` python
def sum_of(**kwargs):
	sum = 0
	for k, v in kwargs:
		sum += v
	return sum

sum_of(coffee=4.99, cake=5.00, juice=3.49)
```



# Exceptions

Exceptions need to be handled by the developer.

The base class for Exceptions is **Exception**

## Try & Except

``` python
def divide_by(a, b):
	return a / b

try:
	ans = divide_by(40, 0)
except ZeroDivisionError as e:
	# This only gets triggered if a divide-by-zero happens
	print(e, "we cannot divide by zero")
except Exception as e:
	# Any other exception will trigger this
	print(e, "something went wrong")
	
```

# File handling

## Open and Close

The mode describe how the file should be openend

* 'r' to open and read
* 'rb' to open and read in binary
* 'r+' to open for reading and writing
* 'w' to open for writing
* 'a' to open for edition or appending data

Opening a file as text makes it easy for a human to understand. The binary format is more compact and efficient. The default is the *text* format. If the binary format is needed a *'b'* has to be appended to the mode. 

``` python
file = open('test.txt', mode = 'r')
data = file.readine()
print(data)
file.close()


# This way the file is closed automatically
with open('testing.txt', 'r') as file:
	data = file.readline()
	print(data)
```

## Creating files and writing
When opening a file with writing permissions that does not yet exist, the file will be created.

*writelines()* accepts a list of strings that will be written to the file. New lines must be manually specified with the newline character \n

``` python
# Exception handling is missing here
with open('my_new_file.txt', 'w') as file:
	file.write("This will be in the new file")
	file.writelines(["Multiple lines can be written", "\nlike so!"])
```

This way each time this is run the text will be replaced rather than added to the file. If run with the mode "a" the text will be appended. 

``` python
try:
	with open('my_new_file.txt', 'w') as file:
		file.write("This will be in the new file")
except FileNotFoundError as e:
	print("ERROR", e)
```

## Reading

``` python
with open('file.txt', 'r') as file:
	print(file.read()) # Reads entire file
	print(file.read(42)) # Reads only 40 characters
	print(file.readline()) # Reads only the next line
	print(file.readline(10)) # Reads first 10 chars of the first line
	
	lines = file.readlines() # Reaturns list of all lines
```

``` python
file = open('file.txt', 'r')

f_contet = f.read()

# Splits the read file each new line and returns it as a list
f_content_list = f_content.split("\n")
```

### Random

Its possible to pick a random element from a list.

``` python
import random 

my_list = [1, 2, 3, 4, 5, 6]
rand_element = random.choice(my_list)
```

## More

[Exceptions in Python](https://docs.python.org/3/library/exceptions.html)
[File handling](https://pynative.com/python/file-handling/)


# Procedural Programming
Structure code into procedures/subroutines. 

**DRY** - Don't Repeat Yourself

Can be hard to maintain, does not always realte well to real world and data is exposed to the entire program.

# Algorithmic Complexity

## Big O notation

Describes the upper bound/worst case scenario for the time complexity of an algorithm.

Written as *O(f(n))*

<table>
	<tr>
		<td>Horrible</td>
		<td>Bad</td>
		<td>Fair</td>
		<td>Good</td>
		<td>Excellent</td>
	</tr>
</table>

### Constant time
Always takes the same amount of time. I.e accessing a dictionary.

**O(1)** - The runtime of such an algorithm does not depend on it's input size. Accessing an array/list with it's index is an example. *(searching through a list is not!)*

### Linear time
The bigger the input, the longer it takes. I.e finding something in an unordered list.

**O(n)** - The runtime of the algorithm depends on the input data and scales linearly with it. This means that if the input size doubles the runtime also doubles. Searching for a specific element in an unordered list is an example for this. 

### Logarithmic time
Binary Search

**O(log(n))** - This is considered very efficient. More so than Linear. Binary Search in an ordered list. 

### Quadratic time
Nested For Loops

**O(n^2)** - The runtime of such an algorithm grows with the square of the input size. If the input is twice as big the runtime will be 2^2 i.e. 4 times as long. Bubble sort a simple sorting algorithm has quadratic runtime.

### Exponential time
Doubles with every bigger input. Fibonacci

**O(2^n)** - Very inefficient


### Factorial time
Basically unusable for anything medium-large. Runtime explodes.

**O(n!)**

[Indorcution to Big O](https://dev.to/sarah_chima/the-big-o-notation-an-introduction-34f7)


# Functional programming

Functions take an input and produce an output.

Functions can be given as an input to other functions and also returned as a result of a function. Functions can be assigned to variables. 

## Pure functions
Pure functions do not have effects on any data outside it's own scope. It only ever changes data within itself. 

# Recursion
A function that calls itself over and over. Gives neat code and makes it possible to break down a problem into smaller subproblems. But it can be hard to understand and is not memory efficient as well as being hard to debug. 

# Slicing

``` python
# str[start:stop:step]

trial = 'reversal'
new_trial = trial[::-1]

```

# Map & Filter

## Map

``` python
# map(<function name>, <articles to process>)

menu = ['espresso', 'mocha', 'latte', 'capuccino', 'cortado', 'americano']

def find_coffee(coffe):
	if coffee[0] == 'c':
		return coffee

# Takes the function and runs it with the elements of menu one by one
map_coffee = map(find_coffee, menu)

for x in map_coffee:
	print(x)
	
# Result will be 'None', 'None', 'None', 'cappucino', 'cortado', 'None'
```

## Filter

``` python

menu = ['espresso', 'mocha', 'latte', 'capuccino', 'cortado', 'americano']

def find_coffee(coffe):
	if coffee[0] == 'c':
		return coffee

# Does the same as map but only returns values that evaluate to true
filter_coffee = filter(find_coffee, menu)

for x in filter_coffee:
	print(x)

# Result will be just 'cappucino' and 'cortado'
```

# Comprehensions

A way to create new sequences out of exisiting ones.

There are 4 main types:

* List comprehension
* Dictionary comprehension
* Set comprehension
* Generator comprehension

**List Comprehension**

The Sytax for list comprehension is the following:

`[ <expression> for x in <sequence> if <condition> ]`

``` python
data = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Adds 3 to every element in data and stores it in the same var
data = [x+3 for x in data]

# Multiplies each element and stores the new list in a new var
new_data = [x*2 for x in data]

# -1 on each x in new_data that is devisble by 4
fouxsub = [x-1 for x in new_data if x%4 == 0]
```

**Dictionary Comprehension**

The Sytax for list comprehension is the following:

`{ <key>:<value> for <key>, <value> in <sequence> if <condition> }`

``` python
months = ["Jan", "Feb", "Mar", "Apr", "May", "June", "July", "Aug", "Sept", "Oct", "Nov", "Dec"]
number = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10 , 11, 12]

# Creates a dict {1: 1, 2: 4, 3: 9, ... }
numdict = {x:x**2 for x in number}

# Uses two lists to create {1: "Jan", 2: "Feb", ... }
months_dict = { key : value for key, value in zip(number, months)}
```
In this example *zip()* is used to combine two lists. If the lists are not of equal lenght the final length will be that of the shorter input's lenth.

**Set comprehension**
The Sytax is the same as with *list comprehension* with the only difference being that instead of [] for lists, {} will be used for sets.

## Map vs. Comprehensions

Comprehensions are very easy to understand and read. However map still has advantages for big sequences.

## MORE

[Map vs List Comprehension](https://www.knowledgehut.com/blog/programming/python-map-list-comprehension)

# Object Orientied Programming (OOP)

## Classes
Attributes 

``` python
class MyClass():
	a = 5
	
	def hello(self):
		print('Hello World!')

myc = MyClass()
myc.hello()

```

Object is an instance of a class

## Inheritance

Creation of new class based on another class

The clss that is inherited from is called *parent, super or base class* the class that inherits is called *child, sub or derived class*.

``` python
class P():
	def __init__(self):
		self.a = 7
		
class C(P):
	pass
	
c = C() # Instance of the child class
print(c.a) # Will print 7
```

The functions *issubclass(class A, class B)* and *isinstance(object, class A)* can be useful. 

A class in python can inherit from multiple classes. This is called *multiple inheritance*. 



## Polymorhism

Same function can behave differently depending on the object calling it. I.e. plus with strings and ints.

## Encapsulation

Limit access of values to a space (class).

**Protected** values are marked with an underscore *_* before them. They can be accessed from within a class and all of it's subclasses.

**Private** values are marked with a double underscore *__* before them. They can only be accessed from within the class. 

``` python
class Alpha:
	def __init__(self):
		self._a = 2
		self.__b = 2
```

## Abstraction

Hide implementation details. Python uses inheritance to achieve this, as the language does not support it directly.

Abstract classes cannot be instantiated but can be inherited from. Methods need to be defined before they are implemented in abstract classes.

**A Decorator** is a function that takes another function as input and returns a new function as output. They are marked with the *@* sign. 

``` python
from abc import ABC, abstractmethod

class SomeAbstractClass(abc):
	@abstractmethod
	def someabstractmethod(self):
		pass
```

There can be no instantiated object of *SomeAbstractClass*. Other classes can inherit from it though. For it to be possible to instantiate a child class that inherits from an abstract class all of the abstract methods have to be implemented by the child class. 

## Instantiation

The variable test in the folowing class is called a class variable. Dish1 is an object and Recipe() is the class.

``` python
class Recipe():

	test = 4
	
	def __init__(self, dish, items, time) -> None:
		self.dish = dish
		self.items = items
		self.time = time
	
	def contents(self):
		print('The ' + str(self.dish) + ' has ' + str(self.items) + \
		' ingredients and takes ' + str(self.time) + ' min to prepare')
		
dish1 = Recipe(...)
```

``` python
class Employee():
	def __init__(self, name, last) -> None:
		self.name = name
		self.last = last

class Supervisor(Employee):
	def __init__(self, name, last, password) -> None:
		super().__init__(name, last)
		self.password = password
		
class Chefs(Employee):
	def leave_request(self, days):
		return "May I take a leave for " + str(days) + " days?"

adrian = Supervisor("Adrian", "A", "apple")
		
emily = Chefs("Emily", "E")
juno = Chefs("Juno", "J")

print(emily.leave_request(12))
```

## Method Resolution Order (MRO)

Determines the order in which a method or attribute is searched for. The order is called linearization. In python this is done **bottom to top and left to right**


If we have a class *Z* that inherits from both *X* and *Y* then MRO will first search in *Z*, then in *X* and then in *Y*.

``` python
class X():
	def test():
		print('mytest')
		
class Y():
	def test():
		print('This is another test')

class Z(X, Y):
	res = 5

z = Z()
# This will call the test method of X.
z.test()

```

The *MRO* can be viewed for a class with *<className>.mro()*. ALternatively with the *help(<Class Name>)* function it is possible to see more information about it. 

* [OOP Concepts](https://www.geeksforgeeks.org/python-oops-concepts/)
* [MRO In-Depth](https://www.python.org/download/releases/2.3/mro/)
* [OOP PRinciples](https://realpython.com/python3-object-oriented-programming/)


# Modules in Python

Modules create different namespaces so that different modules can have the same function names. 

Any python file can be a module. When importing a module, the current directory is searched first, then the builtin modules and after that modules on PYTHONPATH (environment variable)

## import statements

If there is a file in a subdirectory it is possible to add it to the list of paths where python looks for imports.

This code will import the entire sys module, add a new path to look for modules and then import a module from that path.

``` python
import sys

sys.path.isner(1, r'/path/to/dir/with/module')

import module_from_path
```

In order not to overload the interpreter one can also only import certain functions from a module instead of the entire thing.

``` python
from math import sqrt

root = sqrt(9)
print(root)
```

When importing modules can be given an *alias*

``` python
import math as m
from math import factorial as f


root = m.sqrt(9)
print(root)

factorial_10 = f(10)
print(factorial_10)
```


## Namespaces and Scopes

* Namespace - Mapping from name to object
* Scope - Textual region in a program where a namespace is directly accessible

## Reload

Makes it possible to reload a module that has been loaded previously

## PIP (Package Installer for Python)

A package is a folder than can contain subpackages (subfolders). And a module is typically a file.

``` bash
python -m ensurepip --upgrade

python3 -m pip install "SomeProject"
python3 -m pip install requests


```

## MORE

* [How to import Modules in Python3](https://www.digitalocean.com/community/tutorials/how-to-import-modules-in-python-3)
* [Python Packages](https://realpython.com/python-modules-packages/#python-packages)
* [Python Modules](https://www.programiz.com/python-programming/modules)


# Testing

Selenium is a popular testing framework for Web Applications

Types of Testing

* Unit
* System
* Integration
* Acceptance

**Unit**, **Regression** and **Integration** tests can be automated. 

White and Black Box Test. With white box tests the tester knows about the code that is to be tested and it's implementation. With black box testing the tester does not know anything about the code that shall be tested. 

* Functional - Do the required features work as planned?
* Non-Functional - Test overall performance and quality
* Maintenance Test - 


## Unit/Component testing

Test specific, individual components by isolating them. Closer to the code itself. Usually test should be written while the code is being written.

Can be written with **pytest**. Allows for parameterized tests, can run 

``` python
# addition.py

def add(a, b):
    return a + b

def sub(a, b):
    return a - b
```

``` python
# test_addition.py

import addition
import pytest

def test_add():
    assert addition.add(4, 5) == 9

def test_sub():
    assert addition.sub(4, 5) == -1
```

To run the tests you have to type the following into the terminal:

`python3 -m pytest test_addition.py`

If just one of the test functions should be run that can be achieved by appending the name of the test function with to colons

`python3 -m pytest test_addition.py::test_sub`

## Integration testing

Combine unit tests and test flow between components. Top-down, bottom-up or sandwhich approaches.



## System testing

Test the final software to make sure that it operates as specifier by the customer. Also test if it performs well on the operating sytem targeted for deployment. 

## Acceptance testing

Alpha, Beta and Regression testing. 


# TDD - Test Driven Development 

Write the tests first and the code later to pass the tests. Avoids writing code and then not having time for the tests.





