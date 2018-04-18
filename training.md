# Python Training

---

# Access the interpreter

```python
$ python3.6
Python 3.6 (default, Sep 16 2015, 09:25:04)
[GCC 4.8.2] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
---

# Numbers

```python
>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5*6) / 4
5.0
>>> 8 / 5  # division always returns a floating point number
1.6	
>>> 17 // 3  # floor division discards the fractional part
5
>>> 17 % 3  # the % operator returns the remainder of the division
2
>>> 5 ** 2  # 5 squared
25
```

???
We can use Python to make regular math operations

The order of operations is the same as usual

Pay attention to the difference between the normal division `/` and the floor division `//`

`%` is the modulo operation, returning the remainder of the division

`**` can be use to return the power of a number
--

## Create variables
```python
>>> width = 20
>>> height = 5 * 9
>>> width * height
>>> n  # try to access an undefined variable
```

???
Create a variable is as simple as defining it by choosing a name for it and assign it a value with `=`
If we try to access a variable that doesn't exist, we get an exception
---

# Numbers

## _ Variable

```python
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
>>> price + _
>>> round(_, 2)
```

???
The `_` variable can be used, in the interpreter, to get the value of the last printed expression

---

# Numbers

## Exercises

* What is the result of `\[(10 + 2.5) * 3\]`
* What is the result of `\[(50 * 10)^{1/2}\]`
* How could we verify that a number is even?

???
We just need to use the basic python arithmetic operators to have the results.

To test if a number is even, we can test number % 2 == 0

---

# Strings

```python
>>> 'spam eggs'  # single quotes
>>> 'doesn\'t'  # use \' to escape the single quote...
>>> "doesn't"  # ...or use double quotes instead
>>> '"Yes," he said.'
>>> "\"Yes,\" he said."
>>> '"Isn\'t," she said.'
```

???
This is just to demonstrate the different ways to create strings and to escape some elements

--

```python
>>> s = 'First line.\nSecond line.'  # \n means newline
>>> s  # without print(), \n is included in the output
>>> print(s)  # with print(), \n produces a new line
```

???
Show the difference between the output on the interpreter and the built-in print() function

---

# Strings

```python
>>> print('C:\some\name')  # here \n means newline!
>>> print(r'C:\some\name')  # note the r before the quote
```

???
We can also create raw strings with r""

--

```python
print("""\
Usage: thingy [OPTIONS]
        -h                        Display this usage message
        -H hostname               Hostname to connect to
""")
```

???
Multi-line strings can be obtained with triple simple (double) quotes.

They are also used to document

--

```python
>>> 3 * 'un' + 'ium'
```

???
We can apply multiplication and addition of strings.

---

# Strings

```python
>>> text = ('Put several strings within parentheses '
...         'to have them joined together.')
>>> text
>>> prefix = 'Py'
>>> prefix 'thon'  # can't concatenate a variable and a string literal
>>> ('un' * 3) 'ium'
```

???
Two string litterals can be joined togheter if we use parentheses

We can't concatenate a string litteral with a variable (use +)

We can't concatenate a string litteral and an expression (use +)

--

```python
>>> word = 'Python'
>>> word[0]  # character in position 0
>>> word[-1]  # last character
>>> word[0:2]  # characters from position 0 (included) to 2 (excluded)
>>> word[42]  # the word only has 6 characters
>>> word[4:42]
>>> word[0] = 'J'
>>> s = 'supercalifragilisticexpialidocious'
>>> len(s)
```

???
Strings are indiced

We can create slices [from:to not included]

The complete form of slices is [from:to:step]

We get an error if we use an indice that is out of range

No error for the slices ;)

Strings are immutable!

---

# Strings

## Exercises

* How can we know if `'Python'` is contained **in** `'Python is great'`?
* Show a string slice that represents the whole string
* What slice parameters do we need to use?
```python
>>> a = 'I will never'
>>> b = 'learn Python'
>>> c = a[?] + b[?]
>>> c == 'I will learn Python'
>>> True
```

???

- 'Python' in 'Python is great'
- [:]
- a[:6] + b[:]

---

# Strings

## Exercises

* How can we know if a string contains only alpha-numeric characters?
* What does the following code prints?
```python
>>> a = 'Today we have {0} hours of course left together'.format(2)
>>> print(a)
```

For more information, see:

[String methods](https://docs.python.org/3/library/stdtypes.html#textseq)

[Format Strings](https://docs.python.org/3/library/string.html#formatstrings)

???
- 'test'.isalnum()
- Just try...

---

# Lists

```python
>>> squares = [0, 1, 4, 9, 16, 20]
>>> squares[0]  # indexing returns the item
>>> squares[-1]
>>> squares[:]
>>> squares + [ 36, 49 ]
>>> sqares[5] = 25
>>> squares.append(8**2)
>>> squares[3:] = []
>>> squares[:] = []
```

???
Lists are an ensemble of indiced values.

They can be of different types.

We can also get slices

They are mutable

To append: list.append()

To insert: list.insert(ind, elt)

--

```python
>>> a = ['a', 'b', 'c']
>>> n = [1, 2, 3]
>>> x = [a, n]
>>> x[0]
>>> x[0][1]
```

???
We can nest lists together

It is possible then to have multi-dimensional lists/arrays (even if those are not arrays) 

--

```python
>>> a = [1, 2, 3]
>>> for elt in a:
...	print(elt)
```

???
We can simply loop over all elements with for ... in

Behind the scenes, it will use the list and generate iterators

---

# Lists

## Exercises

* Given the following list:
```python
>>> a = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] 
```
Add 1 to all the items and print them
* Using the same list, print the sum of all the elements
* Using the same list, print the multiplication of all the elements

???
- for elt in a: print(a + 1)
- tot = 0

for elt in a: tot += elt

- tot *= elt

---

# Control Flow

## if Statements

```python
>>> x = int(input("Please enter an integer: "))
>>> if x < 0:
...     x = 0
...     print('Negative changed to zero')
... elif x == 0:
...     print('Zero')
... elif x == 1:
...     print('Single')
... else:
...     print('More')
```

???
We can make conditions with if .. elif (else if) and else.

If the first condition is not match, we pass to the second, until we reach the last, default one (else)

The comparison operators are == != > < >= <=

---

# Control Flow

## for Statement

```python
words = ['cat', 'window', 'defenestrate']
>>> for w in words:
...     print(w, len(w))
>>> for w in words[:]:  # Loop over a slice copy of the entire list.
...     if len(w) > 6:
...         words.insert(0, w)
```

???
Remark the difference between looping on the list or on a copy (slice)

---

# Control Flow

## while Statement

```python
>>> i = 0
>>> while i <= 10:
... 	print(i)
```
???
We will face an error here...

For while, we have to specify a condition. It could also be used to iterate on lists with the indices

--

```python
>>> i = 0
>>> while i <= 10:
... 	print(i)
... 	i += 1
```

---

# Control Flow

## range Function

```python
>>> for i in range(5):
...     print(i)
>>> range(5, 10)
>>> range(1, 10, 3)
>>> a = ['Mary', 'had', 'a', 'little', 'lamb']
>>> for i in range(len(a)):
...     print(i, a[i])
```

???
Range will give a range of elements from 0 to the last elt not included

Another option to loop on lists with the indices

---

# Control Flow

## break and continue Statements, and else Clauses on Loops

```python
>>> for num in range(2, 10):
...     if num % 2 == 0:
...         print("Found an even number", num)
...         continue
...     print("Found a number", num)

>>> for n in range(2, 10):
...     for x in range(2, n):
...         if n % x == 0:
...             print(n, 'equals', x, '*', n//x)
...             break
...     else:
...         # loop fell through without finding a factor
...         print(n, 'is a prime number')
```

???
Break will stop the loop that it is within (in this case, the inner loop)

Continue will go to the next iteration

---

# Control Flow

# pass Statements

```python
>>> while True:
...     pass
```

???
Pass does nothing ... at all

It can be used to create short classes or to not implement yet some functions.

raise NotImplementedError is a way better solution

Ignoring errors... No!

Create classes that are inheriting but do not add new functions/attributes

---

# Control Flow

## Exercises

* Write code that prints all the odd numbers in a list
* Write code that removes all the duplicates in a list 
* Write code that prints the greatest number in a list
* Write code that sort the numbers in a list

???


---

# Functions

## Defining functions without arguments

```python
>>> def useless():
...     print("Hey, I'm a function!")
```

---

# Functions

## Defining functions with arguments

```python
>>> def fib(n):    # write Fibonacci series up to n
...     """Print a Fibonacci series up to n."""
...     a, b = 0, 1
...     while a < n:
...         print(a, end=' ')
...         a, b = b, a+b
...     print()
>>> fib
>>> f = fib
>>> f(100)
>>> fib(0)
>>> print(fib(0))
```

---

# Functions

## Defining functions

```python
>>> def fib2(n):  # return Fibonacci series up to n
...     """Return a list containing the Fibonacci series up to n."""
...     result = []
...     a, b = 0, 1
...     while a < n:
...         result.append(a)    # see below
...         a, b = b, a+b
...     return result
```

---

# Functions

## Default Argument Values

```python
def ask_ok(prompt, retries=4, reminder='Please try again!'):
    while True:
        ok = input(prompt)
        if ok in ('y', 'ye', 'yes'):
            return True
        if ok in ('n', 'no', 'nop', 'nope'):
            return False
        retries = retries - 1
        if retries < 0:
            raise ValueError('invalid user response')
        print(reminder)
```

---

# Functions

## Default Argument Values

```python
i = 5

def f(arg=i):
    print(arg)

i = 6
f()
```

---

# Functions

## Default Argument Values

```python
def f(a, L=[]):
    L.append(a)
    return L

print(f(1))
print(f(2))
print(f(3))
```

---

# Functions

## Keyword Arguments

```python
def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
    print("-- This parrot wouldn't", action, end=' ')
    print("if you put", voltage, "volts through it.")
    print("-- Lovely plumage, the", type)
    print("-- It's", state, "!")

parrot(1000)                                          # 1 positional argument
parrot(voltage=1000)                                  # 1 keyword argument
parrot(voltage=1000000, action='VOOOOOM')             # 2 keyword arguments
parrot(action='VOOOOOM', voltage=1000000)             # 2 keyword arguments
parrot('a million', 'bereft of life', 'jump')         # 3 positional arguments
parrot('a thousand', state='pushing up the daisies')  # 1 positional, 1 keyword

parrot()                     # required argument missing
parrot(voltage=5.0, 'dead')  # non-keyword argument after a keyword argument
parrot(110, voltage=220)     # duplicate value for the same argument
parrot(actor='John Cleese')  # unknown keyword argument

d = {"voltage": "four million", "state": "bleedin' demised", "action": "VOOM"}
parrot(**d)
```

---

# Functions

## Functions with undefined number of positional arguments

```python
def say_hello(*args):
    for arg in args:
        print('Hello, {0}'.format(arg))

say_hello('Marc', 'Sebastian', 'Muriel')

l = ['Marc', 'Sebastian', 'Muriel']
say_hello(l)
say_hello(*l)
```

---

# Functions

## Functions with undefined number of keyword arguments

```python
def say_hello(**keywords):
    for kw in keywords:
        print('Hello ', kw, ':', keywords[kw])

say_hello(dog='Rufus', parrot='Achile')
animals = {'monkey': 'Lucas', 'lion': 'Thomas'}
say_hello(animals)
say_hello(**animals)
```

---

# Functions

## Lambda Expressions

```python
>>> def make_incrementor(n):
...     return lambda x: x + n
...
>>> f = make_incrementor(42)
>>> f(0)

>>> pairs = [(1, 'one'), (2, 'two'), (3, 'three'), (4, 'four')]
>>> pairs.sort(key=lambda pair: pair[1])
>>> pairs
```

---

# Functions

## Documentation Strings

```python
>>> def my_function():
...     """Do nothing, but document it.
...
...     No, really, it doesn't do anything.
...     """
...     pass
...
>>> print(my_function.__doc__)
```

More information about the [attributes of functions](https://docs.python.org/3/reference/datamodel.html)

---

# Functions

## Exercises

* Write a function that reverses a string received as input
* Write a function that returns the factorial of a number (non-negative)
* Write a function that takes a number as parameter and returns if it is a prime number

---

# Intermezzo

## Zen of Python

Beautifull is better than ugly.

Explicit is better than implicit.

Simple is better than complex.

Complex is better than complicated.

Flat is better than nested.

Sparse is better than dense.

Readability counts.

Special cases aren't special enough to break the rules.

Although practicality beats purity.

Errors should never pass silently.

---

# Intermezzo

## Zen of Python


Unless explicitly silenced.

In the face of ambiguity, refuse the temptation to guess.

There should be one-- and preferably only one --obvious way to do it.

Although that way may not be obvious at first unless you're Dutch.

Now is better than never.

Although never is often better than *right* now.

If the implementation is hard to explain, it's a bad idea.

If the implementation is easy to explain, it may be a good idea.

Namespaces are one honking great idea -- let's do more of those!

---

# Intermezzo

## Coding Style Guide

[PEP8](https://www.python.org/dev/peps/pep-0008/)

---

# Tests

## Basic Example
```python
import unittest

class TestStringMethods(unittest.TestCase):
    def test_upper(self):
        self.assertEqual('foo'.upper(), 'FOO')

    def test_isupper(self):
        self.assertTrue('FOO'.isupper())
        self.assertFalse('Foo'.isupper())

    def test_split(self):
        s = 'hello world'
        self.assertEqual(s.split(), ['hello', 'world'])

    def will_not_run(self):
        self.assertTrue(false)

if __name__ == '__main__':
    unittest.main()
```

---

# Tests

## Exercises

The exercises are available [Test Exercises](https://github.com/n-pochet/python-training-exercises/tree/master/tests)

---

# Data Structures

## More on Lists

```python
>>> products = ['modem', 'computer', 'memory', 'modem']
>>> products.count('modem')
>>> products.index('modem')
>>> products.reverse()
>>> products.sort()
>>> products.append('laptop')
```

[Documentation](https://docs.python.org/3/library/stdtypes.html#list)

---

# Data Structures

## List Comprehensions

```python
squares = []
for x in range(10):
    squares.append(x**2)
```

```python
squares = list(map(lambda x: x**2, range(10)))
```

```python
squares = [x**2 for x in range(10)]
```

```python
squares_of_even = [x**2 for x in range(10) if x % 2 == 0]
```

```python
vec = [[1,2,3], [4,5,6], [7,8,9]]
[num for elem in vec for num in elem]
```
---

# Data Structures

## Nested List Comprehensions

```python
points = [[0,0], [0,1], [1,3]]
doubled_points = [[p * 2 for p in point] for point in points] 
```

--

## The `del` statetement

```python
a = [1, 2, 3, 4, 5]
del a[0]
del a[2:4]
del a[:]
```

---

# Data Structures

## Tuples

```python
t = 1, 2, 'Hello'
u = t, (3, 4)
t[0] = 5
one, two, hello = t
```

---

# Data Structures

## Sets

```python
numbers = { 1, 2, 1, 2 }
print(numbers)
1 in numbers
3 in numbers
a = set('abracadabra')
b = set('alacazam')
a - b # letters in a but not in b
a | b # letters in a or b or both
a & b # letters in both a and b
a ^ b # letters in a or b but not both
```

---

# Data Structures

## Dictionaries

```python
products = {'modem': 15, 'laptop': 2}
products['laptop']
products['memory'] = 3
products['PC']
products.get('PC', 0)
```

```python
squares = {x: x**2 for x in range(10)}
```

```python
products = {'modem': 15, 'laptop': 2}
for k, v in products.items():
    print(k, v)
```
---

# Data Structures

## Exercises

[Exercises](https://github.com/n-pochet/python-training-exercises/tree/master/data_structures)

---

# Modules

```python
# Fibonacci numbers module

def fib(n):    # write Fibonacci series up to n
    a, b = 0, 1
    while b < n:
        print(b, end=' ')
        a, b = b, a+b
    print()

def fib2(n):   # return Fibonacci series up to n
    result = []
    a, b = 0, 1
    while b < n:
        result.append(b)
        a, b = b, a+b
    return result
```

```bash
tree .
fibo.py
```

---

# Modules

```python
import fibo
>>> fibo.fib(10)
>>> fibo.fib2(10)
>>> fibo.__name__
```

```python
from fibo import fib, fib2
fib(10)
```

```python
from fibo import *
fib(10)
```

```python
import fibo as fib
fib.fib(10)
from fibo import fib as fibonacci
fibonacci(10)
```

---

# Modules

```bash
python fibo.py <arguments>
```

```python
if __name__ == "__main__":
    import sys
    fib(int(sys.argv[1]))
```

```bash
python fibo.py 10
```

---

# Modules

## The `dir()` Function

```python
>>> import fibo
>>> dir(fibo)
```

```python
>>> import builtins
>>> dir(builtins)
```

---

# Packages

```bash
tree game/
game
├── __init__.py
├── monster
│   ├── fight.py
│   ├── __init__.py
│   └── move.py
└── player
    ├── fight.py
    ├── __init__.py
    └── move.py
```

[Source](https://github.com/n-pochet/python-training-slides/tree/master/game)

---

# Packages

```python
import game
dir(game)
import game.monster as monster
from game.monster.fight import fight as monster_fight
```

```python
from game.player import *
fight.fight()
```

```python
from game.monster import *
fight.fight() # Error. Compare monster/__init__.py and player/__init__.py
```

---

# Input and Output

## `str()` and `repr()`

```python
>>> s = "Hello world\n"
>>> str(s)
>>> repr(s)
```

## Fancier Output Formatting

See [Fancier Output Formatting](https://docs.python.org/3/tutorial/inputoutput.html#fancier-output-formatting)

---

# Input and Output

## Reading and Writing Files

```python
>>> f = open('demo-file', 'w')
>>> f.write('Hello file!\n)
>>> f.close()
```

```python
>>> with open('demo-file', 'a') as f:
...    f.write('Another line\n')
>>> f.closed
>>> with open('demo-file', 'r+') as f:
...    f.write('Third line\n')
...    f.readlines()
```

---

# Input and Output

## Reading and Writing Files

```python
>>> with open('demo-file') as f:
...    f.read()
>>> with open('demo-file') as f:
...    f.readline()
...    f.readline()
...    f.readline()
>>> with open('demo-file') as f:
...    f.readlines()
>>> with open('demo-file', 'rb+') as f:
...    f.write(b'0123456789abcdef')
...    f.seek(5) # Go to 6th byte in the file
...    f.read(1)
...    f.seek(-3, 2) # 3rd byte from the end of file
...    # 0 (begin of file), 1 (current position)
...    # 2 (end of file)
...    f.read(1)
```

---

# Input and Output

## Dump to JSON

```python
>>> import json
>>> l = [1, 'simple', 'list']
>>> json.dumps(l)
>>> with open('demo-file', 'r+') as f:
...    json.dump(l, f)
...    f.seek(0)
...    loaded_list = json.load(f)
```

---

# Input and Output

## Exercises

[Exercises](https://github.com/n-pochet/python-training-exercises/tree/master/input_output)

---

# Errors and Exceptions

## Syntax Errors

```python
>>> while True print('Hello world')
```

---

# Errors and Exceptions

## Exceptions

```python
>>> 10 * (1/0)
>>> 4 + spam * 3
>>> '2' + 2
```

See [Built-in Exceptions](https://docs.python.org/3/library/exceptions.html#bltin-exceptions)

---

# Errors and Exceptions

## Handling Exceptions

```python
>>> 1/0
```

--

```python
try:
    x = 1/0
    print("I will not be printed")
except ZeroDivisionError:
    print("1/0 raises a ZeroDivisionError")
```

--

```python
try:
    do_something()
except Exception:
    print("Catch any exception")
```

--

```python
try:
    do_something()
except (ZeroDivisionError, RuntimeError):
    pass
```

---

# Errors and Exceptions

## Handling Exceptions

```python
try:
    f = open('test')
    s = f.readline()
    i = int(s.strip())
    raise Exception("Hey, I'm an exception")
except OSError as err:
    print("OS error: {}".format(err))
except ValueError:
    print("Could not convert data to int")
except:
    print("Unexpected error")
    raise
```

---

# Errors and Exceptions

## Handling Exceptions

```python
def divide(x, y):
    try:
        z = x/y
    except ZeroDivisionError:
        print("Division by zero")
    else:
        return z
```

---

# Errors and Exceptions

## Handling Exceptions

```python
>>> try:
...     raise Exception('spam', 'eggs')
... except Exception as inst:
...     print(type(inst))    # the exception instance
...     print(inst.args)     # arguments stored in .args
...     print(inst)          # __str__ allows args to be printed directly,
...                          # but may be overridden in exception subclasses
...     x, y = inst.args     # unpack args
...     print('x =', x)
...     print('y =', y)
```

---

# Errors and Exceptions

## Raising Exceptions

```python
>>> try:
...     raise Exception('spam', 'eggs')
... except Exception as inst:
...     print(type(inst))    # the exception instance
...     print(inst.args)     # arguments stored in .args
...     print(inst)          # __str__ allows args to be printed directly,
...                          # but may be overridden in exception subclasses
...     x, y = inst.args     # unpack args
...     print('x =', x)
...     print('y =', y)
```

---

# Errors and Exceptions

## Defining Clean-up Actions

```python
def print_file(filename):
    try:
        f = open(filename)
        s = f.read()
    except OSError as err:
        print("OS error: {}".format(err))
    else:
        print(s)
        f.close()
    finally:
        print("Tried to open {}".format(filename))
```

---

# Classes

## Why?

```python
point = (0, 0)
def add(a, b):
    c = (a[0] + b[0], a[1] + b[1])
    return c
print(point)
```

Problems:

* A new `point` involves using a `tuple`
* To access `x` and `y` coordinates is not obvious. Is it p[0] or p[1]?
* What is the representation of `point`?
* ... 

How can we improve our `point`?

---

# Classes

## First try on Point

```python
class Point():

    def __init__(self, x, y):
        self.x = x
        self.y = y
```

```python
p = Point(0, 0)
p.x = 1
p.y = 2
print(p)
```

---

# Classes

## How to represent Point?

```python
class Point():
    def __repr__(self):
        return "Point(x: {}, y: {})".format(self.x, self.y)
    
    def __str__(self):
        return "({}, {})".format(self.x, self.y)
```

```python
p = Point(0, 1)
p
print(p)
```

---

# Classes

## How to add `Point`s?

```python
class Point():
    def add(self, other):
        x = self.x + other.x
        y = self.y + other.y
        return Point(x, y)
```

```python
class Point():
    def __add__(self, other):
        x = self.x + other.x
        y = self.y + other.y
        return Point(x, y)
```

```python
p1 = Point(1, 2)
p2 = Point(1, 1)
p3 = p1 + p2
```

[More info](https://docs.python.org/3/reference/datamodel.html#emulating-numeric-types)

---

# Classes
## Create a `Circle`

```python
circle = (Point(1, 1), 1)
```

```python
class Circle(Point):
    def __init__(self, x, y, r):
        super().__init__(x, y)
        self.r = r
```

```python
c = Circle(1, 1, 1)
```

---

# Classes

## Create a `Line`

```python
class Line():
    def __init__(self, *points):
        self.points = list(points)
```

---

# Classes

## More information

[Python Tutorial](https://docs.python.org/3/tutorial/classes.html)

---

# Classes

## Exercises

[Exercises](https://github.com/n-pochet/python-training-exercises/tree/master/classes)

---

# Virtualenv

```bash
python3 -m venv myvenv
```

* Unix

```bash
source myvenv/bin/activate
```

* Windows

```powershell
myvenv\Scripts\activate.bat
```

---

# Install packages

```bash
pip search requests
```

```bash
pip install requests
pip install requests==2.6.0
pip install --upgrade requests
```

```bash
pip show pkg_name
pip list
pip freeze > requirements.txt
pip install -r requirements.txt
```