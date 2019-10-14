<script type="text/javascript"
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
# Introduction to Python

## Computational Python

KTH

---

layout: false

# Python Basics


## Running

### Interactively

* `python` without arguments starts up  the Python interpreter 
* The interpreter reads lines one by one in the Python programming language and executes them
* The interpreter prints prompt `>>>` when it is waiting for input

~~~
$ python
>>> print("Hello world")
Hello world
>>>
~~~

* A read-evaluate-print-loop (REPL)
    - reads a Python expression
    - evaluates the expression
    - prints the value to the screen
    - starting over (loop)

---

## Creating Python scripts

### Text editors

To enter code into files you need to use a text editor (not a word processor
like Microsoft Word). A text editor is good for programming if it automatically
colors special keywords for the programming language of that file. A simple 
editor that fulfills this is `nano`.

<img src="nano.png" height="250">

Developers survey on 
<a href="https://insights.stackoverflow.com/survey/2018/#development-environments-and-tools">
most popular programming editor
</a>: 
normally lists editors like vim, emacs, atom, sublime.
Spending time to learn one well is worth the investment.

---

### IDE:s

IDE = Integrated development environment

~~~
$ pip install mu-editor
$ mu-editor hello.py
~~~

<img src="mu.png" height="350">

---

### Visual Studio Code

* Microsoft open source project

<img src="vsc.png" height="400">

---

### Pycharm

* Community and Professional editions from JetBrains

<img src="pycharm.png" height="400">

* see https://www.jetbrains.com/student/

---

### Notebooks

* work/develop in browser
* mix documentation and code
~~~
$ jupyter notebook
~~~
<img src='jupyter.png' height="350" >
* good for exploration/experimentation/demonstration
* not good for writing large structured programs


---

## Some Python types

Values in Python have a type
A type determines the range of possible values and operations that can be
performed

###  Numerical

* whole numbers (`int`): e.g. `-1, 7, 2000`
* decimal numbers (`float`): `3.14, 1.0 -7.25`
* complex numbers (`complex`): `1j, 7+5j`
* logical (`bool`): `True`, `False`

---

###  String: `str`

- sequence of characters
- literal strings are written within quotation marks
- single `'` and double `"` quotation marks have the same status
- three quotation marks limit strings that can span several lines


~~~
>>> print("It's time")
It's time
~~~


~~~
>>> print('Our boss is "nice". 😀')
Our boss is "nice". 😀
~~~

~~~
>>> print("""Hello
... world""")
Hello
world
~~~

---

## Variables

* To save the value of an object it is assigned to a *variable*
* The assignment operator is `=`
* Assignment is to bind a name to an object
* Python has so called free typing 

### Example
~~~
>>> x = 8*9
>>> print(x)
72
~~~

* Right-side is evaluated
* An `int` object with value 72 is created in memory
* An association is created with this object and the name `x`

---

## Container types

* Lists
* Tuples
* Dictionaries

---

### Lists

* A list is a ordered sequence of elements 
* Notation: square brackets , comma-separated
* List can have objects of different types
* List members are referenced with `[n]` where `n=0, 1, 2...`
* A list can be empty, `[]`

~~~
>>> colours = ['hearts', 'spades', 'diamonds', 'clubs']
>>> values = [2, 3, 4, 5, 6, 7, 8, 9, 10, 'knight', 'queen', 'king', 'ace']
~~~

---

### Tuples

* An immutable (unchangeable) sequence of objects
* Similar to lists
* () is the empty tuple
* (1,)  contains 1 element -note the comma

Handy packing and unpacking

```
>>> t = 1, 2 #packing
>>> x, y = t #unpacking
>>> x, y
(1, 2)
>>> x, y = y, x #swapping
>>> x, y
(2, 1)


```
---

### Dictionaries

* Sets of key-value pairs
* The key can be any immutable object
* Very useful for complex structures
* Efficient and highly optimized

```
empty =  {} # empty dict
newdict = {'a':1, 'b':2}
```

---

### Repetition (iteration, looping)

* The `for ... in` statement is used repeat the same operation for all elements of a
sequence

* A loop variable will reference the elements of the sequence, one at a time


```python
>>> for e in [1, 2, 3]: 
...    print(e)
1
2
3

```

```python
>>> for c in 'hello':
...     print(c)
h
e
l
l
o

```



```python
>>> for k, v in {'a': 1, 'b': 2}.items():                                       
...    print(k, v)
a 1
b 2

```


---

### Branching (if statements)

Conditional execution of code blocks depending on whether an expression
evaluates to True or not:

```
>>> if True:
...     print("Yes")
... else:
...     print("No")
Yes

```

```
>>> i = j = 0
>>> if i > j:
...     print(i, " is larger than ", j)
... else:
...     print(i, "is smaller than or equal to", j)
0 is smaller than or equal to 0

```

Most object types have some truthiness. Empty lists in a logical context
evaluate to False, non-empty to True

```
>>> if []:
...     print("Non-empty list")
... else:
...     print("Empty list")
Empty list

```

---


### Functions

* Functions are objects that can take some input and return some output.
Functions are the primary way of grouping code into independent units, that can be tested and reused

* Function definitions start `def`, a name,  parentheses with or without
arguments (comma-separated) and a colon.
The body of the function is indented with respect to the `def` keyword.
The last line of a function definition is normally a `return` statement and determines the value of a function call

```
>>> def square(x):
...    x2 = x * x
...    return x2

```

* Functions are called with function name and an actual parameter. 

```
>>> square(2)
4

```

* Inside the function the formal parameter `x` becomes a reference to the actual
parameter `2`.


---

### Modules


* a file with python source 
   - name is the filename without the ``.py`` extension
* `import` modules to reuse code
* members of module referenced with dot notation `module.member`

Commonly used Python modules

* ``sys``
* ``os``
* ``math``

---

#### `sys`

* system modules
* needed e.g. for arguments to a script
* `sys.argv` is a list of string arguments
* `sys.argv [0]` is the file name

~~~
import sys
infile = sys.argv[1]
~~~

#### `os`

* Interaction with operating system
* Example: execute a unix command 

```
    import os
    os.system('/bin/date')
```


#### `math`

* all basic elementary functions
* fundamental constants

```
    import math
    print(math.sin(math.pi/2))
```

#### Tip

Many use the math modules as a desktop calculator

    $ python
    >>> from math import *
    >>> print(pi/2)
    1.5707963267948966
    >>>

---

### Writing/using your own modules

* Suppose you have written file ``hello.py`` with function ``say_hello``

~~~
#hello.py
def say_hello():
    return "Hello world!"
~~~

* To access the same function in other code, import the module

~~~
>>> import hello
>>> message = hello.say_hello()
>>> print(message)
Hello world!
~~~

---

### Sample code: multiplication table

Version 1: if we only know print
~~~
print(1 * 7)
print(2 * 7)
print(3 * 7)
~~~

Version 2: extract the varying data to a variable
~~~
i = 1
print(i * 7)
i = 2
print(i * 7)
i = 3
print(i * 7)
~~~

Version 3: introduction the for loop, indented blocks
~~~
for i in (1, 2, 3, 4, 5, 6, 7, 8 , 9, 10):
    print(i * 7)
~~~

Version 4: the `range` function
~~~
n = 7
for i in range(1, 11):
    print(i * n)
~~~

---

Version 5: define as a function
~~~
def print_mult_table(n):
    for i in range(1, 11):
        print(i * n)
~~~

Version 6: call the function from the command line
~~~
def print_mult_table(n):
    for i in range(1, 11):
        print(i * n)

if __name__ == "__main__":
    
    import sys
    print_mult_table(int(sys.argv[1]))
~~~

* the system variable `__name__` has the value `"__main__"` (double underscores)
when the file is executed as a program
* it has the value equal to the file name when it is imported as a module
* command-line argments appear in the system variable `sys.argv`, a Python list
which has the file name as the first member (of index zero)

A common pattern when a file is used both as an independent script and as a
module imported by other programs

---

### Summary

* Basic syntax - indentation
* Basic built in variable types
* Scalar and container types
* Functions
* Modules

### Standard documentation
* https://docs.python.org/3

### On-line books
* Jake van der Plas: 
<a href="http://nbviewer.jupyter.org/github/jakevdp/WhirlwindTourOfPython/blob/master/Index.ipynb"> A Worldwind Tour of Python</a>
* Jake van der Plas: <a href="https://jakevdp.github.io/PythonDataScienceHandbook/">Data Science Handbook</a>
* Al Sweigart: <a href="https://automatetheboringstuff.com">Automate the Boring Stuff with Python</a>

### On-line tutorials
* https://docs.python.org/3/tutorial/
* https://realpython.com
