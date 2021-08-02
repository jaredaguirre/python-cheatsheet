# Jare's Python Cheatsheet

The present cheatsheet is a briefing about the different Python syntax shortcuts and features. It is based on the original cheatsheet from the course 'ZTM: Python Developer' that you can find [here](https://zerotomastery.io/cheatsheets/python-cheat-sheet/#file-io).
However, some of the items were modified for personal understanding. Some of the examples were changed as well to clarify and update concepts. Enjoy!

## Contents

### Python Types:
[Numbers](#numbers), [Strings](#strings), [Booleans](#booleans), [Fundamental Data Structures Comparison](#fundamental-data-structures-comparison), [Lists](#lists), [Tuples](#tuples), [Sets](#sets), [Dictionaries](#dictionaries), [None](#none)

### Python Basics:
[Comparison Operators](#comparison-operators), [Logical Operators](#logical-operators), [Loops](#loops), [Range](#range), [Enumerate](#enumerate), [Counter](#counter), [Named Tuple](#named-tuple)

### Functions:
[Functions](#functions), [Lambda](#lambda), [Comprehensions](#comprehensions), [Map/Filter/Reduce](#map--filter--reduce), [Ternary](#ternary-condition), [Any/All](#any--all), [Closures](#closures), [Scope](#scope)

### Advanced Python:
[Modules](#modules), [Iterators](#iterators), [Generators](#generators), [Decorators](#decorators), [Class](#classes), [Exceptions](#exceptions-and-error-handling), [Command Line Arguments](#command-line-arguments), [File IO](#file-io)

### Useful Built-in Libraries:
[CSV](#csv), [JSON](#json), [Pickle](#pickle), [Time](#time), [Math](#math), [Statictics](#statictics), [Datetime](#datetime), [Regex](#regex), [Unittest](#unittest)

### Cool Libraries:
[Pillow](https://pillow.readthedocs.io/en/stable/handbook/overview.html), [pprint](https://docs.python.org/3/library/pprint.html)

### Concepts
[Virtual Environments](#virtual-environments)

## Numbers
Python's 2 main types for Numbers are integers and floating point numbers

```python
type(1)   # int 
type(-10) # int
type(0)   # int
type(0.0) # float
type(2.2) # float
type(4E2) # float --> 4 * (10^2)
```

```python
# Arithmetic
10 + 3  # 13
10 - 3  # 7
10 * 3  # 30
10 ** 3 # 1000
10 / 3  # 3.3333333333333335
10 // 3 # 3 --> floor division: no decimals and returns an int
10 % 3  # 1 --> modulo operator: return the reminder. Good for deciding if number is even or odd
```

```python
# Basic Functions
pow(5, 2)      # 25 --> like doing 5**2
abs(-50)       # 50
round(5.46)    # 5
round(5.468, 2)# 5.47 --> round to nth digit
bin(512)       # '0b1000000000' -->  binary format
hex(512)       # '0x200' --> hexadecimal format
```

```python
# Converting Strings to Numbers
age = input("How old are you?")
age = int(age)
pi = input("What is the value of pi?")
pi = float(pi)
```
[Back to top](#jares-python-cheatsheet)

## Strings
Strings in python are stored as sequences of non-mutable letters in memory

```python
type('Buenaaaardooo') # str

'I\'m thirsty'
"I'm thirsty"
"\n" # new line
"\t" # adds a tab

'Hey you!'[4]   # y
name = 'Jared Aguirre'
name[4]         # d
name[:]         # Jared Aguirre
name[1:]        # ared Aguirre
name[:1]        # J
name[-1]        # e
name[::1]       # Jared Aguirre
name[::-1]      # erriugA deraJ
name[0:10:2]    # JrdAu
# : is called slicing and has the format [ start : end : step ]

'Hi there ' + 'Timmy' # 'Hi there Timmy' --> This is called string concatenation
'*'*10 # **********
```

```python
# Basic Functions
len('turtle') # 6

# Basic Methods
'  I am alone '.strip()               # 'I am alone' --> Strips all whitespace characters from both ends.
'On an island'.strip('d')             # 'On an islan' --> # Strips all passed characters from both ends.
'but life is good!'.split()           # ['but', 'life', 'is', 'good!']
'Help me'.replace('me', 'you')        # 'Help you' --> Replaces first with second param
'Need to make fire'.startswith('Need')# True
'and cook rice'.endswith('rice')      # True
'bye bye'.index('e')                  # 2
'still there?'.upper()                # STILL THERE?
'HELLO?!'.lower()                     # hello?!
'ok, I am done.'.capitalize()         # 'Ok, I am done.'
'oh hi there'.find('i')               # 4 --> returns the starting index position of the first occurrence
'oh hi there'.count('e')              # 2
```

```python
# String Formatting
name1 = 'Jared'
name2 = 'Pamela'
print(f'Hello there {name1} and {name2}')           # Hello there Jared and Pamela
print('Hello there {} and {}'.format(name1, name2)) # Hello there Jared and Pamela
print('Hello there %s and %s' %(name1, name2))      # Hello there Jared and Pamela --> you can also use %d, %f, %r for integers, floats, string representations of objects respectively
```
```python
# Palindrome check
word = 'reviver'
pal = bool(word.find(word[::-1]) + 1)
print(pal) # True
```
[Back to top](#jares-python-cheatsheet)

## Booleans
Logical values (True or False). Used for comparison and logical operations in Python

```python
bool(True)    # True
bool(False)   # False

# all of the below statements are considered as False. Everything else will return True in Python.
print(bool(None))
print(bool(False))
print(bool(0))
print(bool(0.0))
print(bool([]))
print(bool({}))
print(bool(()))
print(bool(''))
print(bool(range(0)))
print(bool(set()))

# See Logical Operators and Comparison Operators section for more on booleans.
```

[Back to top](#jares-python-cheatsheet)

## Fundamental Data Structures Comparison
|                         | List          | Tuple       | Set      | Dictionary                                |
| ----------------------- |:-------------:|:-----------:|:--------:|:-----------------------------------------:|
| Ordered / Indexed       | Yes           | Yes         | No       | Yes, but converting it into a list first  |
| Mutable                 | Yes           | No          | Yes      | Yes                                       |
| Allow Duplicates        | Yes           | Yes         | No       | Not for keys                              |

[Back to top](#jares-python-cheatsheet)


## Lists
Unlike strings, lists are mutable sequences in python

```python
my_list = [1, 2, '3', True]# We assume this list won't mutate for each example below
len(my_list)               # 4
my_list.index('3')         # 2
my_list.count(2)           # 1 --> count how many times the number 2 appears

my_list[3]                 # True
my_list[1:]                # [2, '3', True]
my_list[:1]                # [1]
my_list[-1]                # True
my_list[::1]               # [1, 2, '3', True]
my_list[::-1]              # [True, '3', 2, 1]
my_list[0:3:2]             # [1, '3']

# : is called slicing and has the format [ start : end : step ]
```

```python
# Add to List
my_list * 2                # [1, 2, '3', True, 1, 2, '3', True]
my_list + [100]            # [1, 2, '3', True, 100] --> doesn't mutate original list, creates new one
my_list.append(100)        # None --> Mutates original list to [1, 2, '3', True, 100]          # Or: <list> += [<el>]
my_list.extend([100, 200]) # None --> Mutates original list to [1, 2, '3', True, 100, 200]
my_list.insert(2, '!!!')   # None -->  [1, 2, '!!!', '3', True] - Inserts item at index and moves the rest to the right.

' '.join(['Hello','There'])# 'Hello There' --> Joins elements using string as separator.
```

```python
# Copy a List
basket = ['apples', 'pears', 'oranges']
new_basket = basket.copy()
new_basket2 = basket[:]
```

```python
# Remove from List
[1,2,3].pop()    # 3 --> mutates original list, default index in the pop method is -1 (the last item)
[1,2,3].pop(1)   # 2 --> mutates original list
[1,2,3].remove(2)# None --> [1,3] Removes first occurrence of item or raises ValueError.
[1,2,3].clear()  # None --> mutates original list and removes all items: []
del [1,2,3][0] # 
```
```python
# Ordering
[1,2,5,3].sort()         # None --> Mutates list to [1, 2, 3, 5]
[1,2,5,3].sort(reverse=True) # None --> Mutates list to [5, 3, 2, 1]
[1,2,5,3].reverse()      # None --> Mutates list to [3, 5, 2, 1]
sorted([1,2,5,3])        # [1, 2, 3, 5] --> new list created
list(reversed([1,2,5,3]))# [3, 5, 2, 1] --> reversed() returns an iterator
```
```python
# Useful operations
1 in [1,2,5,3]  # True
min([1,2,3,4,5])# 1
max([1,2,3,4,5])# 5
sum([1,2,3,4,5])# 15
```

```python
# Get First and Last element of a list
mList = [63, 21, 30, 14, 35, 26, 77, 18, 49, 10]
first, *x, last = mList
print(first) #63
print(last) #10
```
```python
# Get First and Last element of a list
mList = [63, 21, 30, 14, 35, 26, 77, 18, 49, 10]
first, *x, last = mList
print(first) #63
print(last) #10
```
```python
# Matrix
matrix = [[1,2,3], [4,5,6], [7,8,9]]
matrix[2][0] # 7 --> Grab first first of the third item in the matrix object

# Looping through a matrix by rows:
mx = [[1,2,3],[4,5,6]]
for row in range(len(mx)):
	for col in range(len(mx[0])):
		print(mx[row][col]) # 1 2 3 4 5 6

# Transform into a list:
[mx[row][col] for row in range(len(mx)) for col in range(len(mx[0]))] # [1,2,3,4,5,6]

# Combine columns with zip and *:
[x for x in zip(*mx)] # [(1, 3), (2, 4)]
```
```python
# List Comprehensions
# new_list[<action> for <item> in <iterator> if <some condition>]
a = [i for i in 'hello']                  # ['h', 'e', 'l', 'l', '0']
b = [i*2 for i in [1,2,3]]                # [2, 4, 6]
c = [i for i in range(0,10) if i % 2 == 0]# [0, 2, 4, 6, 8]
```

```python
# Advanced Functions
list_of_chars = list('Helloooo')                                   # ['H', 'e', 'l', 'l', 'o', 'o', 'o', 'o']
sum_of_elements = sum([1,2,3,4,5])                                 # 15
element_sum = [sum(pair) for pair in zip([1,2,3],[4,5,6])]         # [5, 7, 9]
sorted_by_second = sorted(['hi','you','man'], key=lambda el: el[1])# ['man', 'hi', 'you']
sorted_by_key = sorted([
                       {'name': 'Bina', 'age': 30},
                       {'name':'Andy', 'age': 18},
                       {'name': 'Zoey', 'age': 55}],
                       key=lambda el: (el['name']))# [{'name': 'Andy', 'age': 18}, {'name': 'Bina', 'age': 30}, {'name': 'Zoey', 'age': 55}]
```
```python
# Read line of a file into a list
with open("myfile.txt") as f:
  lines = [line.strip() for line in f]
```
[Back to top](#jares-python-cheatsheet)

## Tuples
Like lists, but they are used for immutable things (that don't change)

```python
my_tuple = ('apple','grapes','mango', 'grapes')
apple, grapes, mango, grapes = my_tuple# Tuple unpacking
len(my_tuple)                          # 4
my_tuple[2]                            # mango
my_tuple[-1]                           # 'grapes'
```
```python
# Immutability
my_tuple[1] = 'donuts'  # TypeError
my_tuple.append('candy')# AttributeError
```
```python
# Methods
my_tuple.index('grapes') # 1
my_tuple.count('grapes') # 2
```
```python
# Zip
list(zip([1,2,3], [4,5,6])) # [(1, 4), (2, 5), (3, 6)]

# unzip
z = [(1, 2), (3, 4), (5, 6), (7, 8)] # Some output of zip() function
unzip = lambda z: list(zip(*z))
unzip(z)
```

[Back to top](#jares-python-cheatsheet)


## Sets
Unordered collection of unique elements (Very useful for discrete maths)

```python
my_set = set()
my_set.add(1)  # {1}
my_set.add(100)# {1, 100}
my_set.add(100)# {1, 100} --> no duplicates!
```
```python
new_list = [1,2,3,3,3,4,4,5,6,1]
set(new_list)           # {1, 2, 3, 4, 5, 6}

my_set.remove(100)      # {1} --> Raises KeyError if element not found
my_set.discard(100)     # {1} --> Doesn't raise an error if element not found
my_set.clear()          # {}
new_set = {1,2,3}.copy()# {1,2,3}
```
```python
set1 = {1,2,3}
set2 = {3,4,5}
set3 = set1.union(set2)               # {1,2,3,4,5}
set4 = set1.intersection(set2)        # {3}
set5 = set1.difference(set2)          # {1, 2}
set6 = set1.symmetric_difference(set2)# {1, 2, 4, 5}
set1.issubset(set2)                   # False
set1.issuperset(set2)                 # False
set1.isdisjoint(set2)                 # False --> return True if two sets have a null intersection
```
```python
# Frozenset
# hashable --> it can be used as a key in a dictionary or as an element in a set.
<frozenset> = frozenset(<collection>)
```
[Back to top](#jares-python-cheatsheet)


## Dictionaries
Also known as mappings or hash tables. They are key value pairs that are guaranteed to retain order of insertion

```python
my_dict = {'name': 'Andrei Neagoie', 'age': 30, 'magic_power': False}
my_dict['name']                      # Andrei Neagoie
len(my_dict)                         # 3
list(my_dict.keys())                 # ['name', 'age', 'magic_power']
list(my_dict.values())               # ['Andrei Neagoie', 30, False]
list(my_dict.items())                # [('name', 'Andrei Neagoie'), ('age', 30), ('magic_power', False)]
my_dict['favourite_snack'] = 'Grapes'# {'name': 'Andrei Neagoie', 'age': 30, 'magic_power': False, 'favourite_snack': 'Grapes'}
my_dict.get('age')                   # 30 --> Returns None if key does not exist.
my_dict.get('ages', 0 )              # 0 --> Returns default (2nd param) if key is not found

#Remove key
del my_dict['name']
my_dict.pop('name', None)
```

```python
my_dict.update({'cool': True})                                         # {'name': 'Andrei Neagoie', 'age': 30, 'magic_power': False, 'favourite_snack': 'Grapes', 'cool': True}
{**my_dict, **{'cool': True} }                                         # {'name': 'Andrei Neagoie', 'age': 30, 'magic_power': False, 'favourite_snack': 'Grapes', 'cool': True}
new_dict = dict([['name','Andrei'],['age',32],['magic_power',False]])  # Creates a dict from collection of key-value pairs.
new_dict = dict(zip(['name','age','magic_power'],['Andrei',32, False]))# Creates a dict from two collections.
new_dict = my_dict.pop('favourite_snack')                              # Removes item from dictionary.
```
```python
# How to index a dictionary
my_dictionary = {"a": 1, "b": 2}

keys_list = list(my_dictionary)

a_key = keys_list[0]  #a_key = 'a'
```

```python
# Dictionary Comprehension
{key: value for key, value in new_dict.items() if key == 'age' or key == 'name'} # {'name': 'Andrei', 'age': 32} --> Filter dict by keys
```

```python
# Retain order of insertion
programmers = dict()
programmers['Tim'] = ['python', 'javascript']
programmers['Sarah'] = ['C++']
programmers['Bia'] = ['Ruby', 'Python', 'Go']

for name, langs in programmers.items():
    print(name + '-->')
    for lang in langs:
      print('\t' + lang)
      
#Tim-->
#       python
#       javascript
#Sarah-->
#       C++
#Bia-->
#       Ruby
#       Python
#       Go
```
[Back to top](#jares-python-cheatsheet)

## None
Absence of a value (*Void* in another languages). Can be used to show nothing has been assigned to an object

```python
type(None) # NoneType
a = None
```

[Back to top](#jares-python-cheatsheet)


## Comparison Operators
Some therms first: *Operator* is the symbol that compares two *operands*
```python
==                   # equal values
!=                   # not equal
>                    # left operand is greater than right operand
<                    # left operand is less than right operand
>=                   # left operand is greater than or equal to right operand
<=                   # left operand is less than or equal to right operand
<element> is <element> # check if two operands refer to same object in memory
```

[Back to top](#jares-python-cheatsheet)

## Logical Operators
```python
1 < 2 and 4 > 1 # True
1 > 3 or 4 > 1  # True
1 is not 4      # True
not True        # False
1 not in [2,3,4]# True

if <condition that evaluates to boolean>:
  # perform action1
elif <condition that evaluates to boolean>:
  # perform action2
else:
  # perform action3
```

[Back to top](#jares-python-cheatsheet)

## Loops

```python
my_list = [1,2,3]
my_tuple = (1,2,3)
my_list2 = [(1,2), (3,4), (5,6)]
my_dict = {'a': 1, 'b': 2. 'c': 3}

for num in my_list:
    print(num) # 1, 2, 3

for num in my_tuple:
    print(num) # 1, 2, 3

for num in my_list2:
    print(num) # (1,2), (3,4), (5,6)

for num in '123':
    print(num) # 1, 2, 3

for k,v in my_dict.items(): # Dictionary Unpacking
    print(k) # 'a', 'b', 'c'
    print(v) # 1, 2, 3

while <condition that returns boolean>:
  # action
  if <condition that returns boolean>:
    break     # break out of while loop
  if <condition that returns boolean>:
    continue  # continue to the next line in the block
 ```
 ```python
 # waiting until user quits
msg = ''
while msg != 'quit':
    msg = input("What should I do?")
    print(msg)
```
[Back to top](#jares-python-cheatsheet)

## Range
```python
range(10)          # range(0, 10) --> 0 to 9
range(1,10)        # range(1, 10)
list(range(0,10,2))# [0, 2, 4, 6, 8]
```

[Back to top](#jares-python-cheatsheet)

## Enumerate

```python
for i, el in enumerate('helloo'):
  print(f'{i}, {el}')
# 0, h
# 1, e
# 2, l
# 3, l
# 4, o
# 5, o
```
[Back to top](#jares-python-cheatsheet)

## Counter
```python
from collections import Counter
colors = ['red', 'blue', 'yellow', 'blue', 'red', 'blue']
counter = Counter(colors)# Counter({'blue': 3, 'red': 2, 'yellow': 1})
counter.most_common()[0] # ('blue', 3)
```
[Back to top](#jares-python-cheatsheet)

## Named Tuple
Tuple is an immutable and hashable list. Named tuple is its subclass with named elements.

```python
from collections import namedtuple
Point = namedtuple('Point', 'x y')
p = Point(1, y=2)# Point(x=1, y=2)
p[0]             # 1
p.x              # 1
getattr(p, 'y')  # 2
p._fields        # Or: Point._fields #('x', 'y')
```
```python
from collections import namedtuple
Person = namedtuple('Person', 'name height')
person = Person('Jean-Luc', 187)
f'{person.height}'           # '187'
'{p.height}'.format(p=person)# '187'
```

[Back to top](#jares-python-cheatsheet)

## Functions
\*args and \*\*kwargs
Splat (\*) expands a collection into positional arguments, while splatty-splat (\*\*) expands a dictionary into keyword arguments

```python
args   = (1, 2)
kwargs = {'x': 3, 'y': 4, 'z': 5}
some_func(*args, **kwargs) # same as some_func(1, 2, x=3, y=4, z=5)
```

\* Inside Function Definition
Splat combines zero or more positional arguments into a tuple, while splatty-splat combines zero or more keyword arguments into a dictionary.
```python
def add(*a):
    return sum(a)

add(1, 2, 3) # 6
```
Ordering of parameters
```python
def f(*args):                  # f(1, 2, 3)
def f(x, *args):               # f(1, 2, 3)
def f(*args, z):               # f(1, 2, z=3)
def f(x, *args, z):            # f(1, 2, z=3)

def f(**kwargs):               # f(x=1, y=2, z=3)
def f(x, **kwargs):            # f(x=1, y=2, z=3) | f(1, y=2, z=3)

def f(*args, **kwargs):        # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3) | f(1, 2, 3)
def f(x, *args, **kwargs):     # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3) | f(1, 2, 3)
def f(*args, y, **kwargs):     # f(x=1, y=2, z=3) | f(1, y=2, z=3)
def f(x, *args, z, **kwargs):  # f(x=1, y=2, z=3) | f(1, y=2, z=3) | f(1, 2, z=3)
```
Other uses of (\*)
```python
[*[1,2,3], *[4]]                # [1, 2, 3, 4]
{*[1,2,3], *[4]}                # {1, 2, 3, 4}
(*[1,2,3], *[4])                # (1, 2, 3, 4)
{**{'a': 1, 'b': 2}, **{'c': 3}}# {'a': 1, 'b': 2, 'c': 3}

head, *body, tail = [1,2,3,4,5] # head=1, body=[2, 3, 4], tail=5
```

[Back to top](#jares-python-cheatsheet)


## Lambda
```python
# lambda: <return_value>
# lambda <argument1>, <argument2>: <return_value>
```
```python
# Factorial
from functools import reduce
n = 3
factorial = reduce(lambda x, y: x*y, range(1, n+1))
print(factorial) #6

# Fibonacci
fib = lambda n : n if n <= 1 else fib(n-1) + fib(n-2)
result = fib(10)
print(result) #55
```

[Back to top](#jares-python-cheatsheet)

## Comprehension
```python
<list> = [i+1 for i in range(10)]         # [1, 2, ..., 10]
<set>  = {i for i in range(10) if i > 5}  # {6, 7, 8, 9}
<iter> = (i+5 for i in range(10))         # (5, 6, ..., 14)
<dict> = {i: i*2 for i in range(10)}      # {0: 0, 1: 2, ..., 9: 18}
```

```python
output = [i+j for i in range(3) for j in range(3)] # [0, 1, 2, 1, 2, 3, 2, 3, 4]

# Is the same as:
output = []
for i in range(3):
  for j in range(3):
    output.append(i+j)
```

[Back to top](#jares-python-cheatsheet)

## Ternary Condition
```python
# <expression_if_true> if <condition> else <expression_if_false>

[a if a else 'zero' for a in [0, 1, 0, 3]] # ['zero', 1, 'zero', 3]
```
[Back to top](#jares-python-cheatsheet)

## Map / Filter / Reduce
```python
from functools import reduce
list(map(lambda x: x + 1, range(10)))            # [1, 2, 3, 4, 5, 6, 7, 8, 9,10]
list(filter(lambda x: x > 5, range(10)))         # (6, 7, 8, 9)
reduce(lambda acc, x: acc + x, range(10))        # 45
```
[Back to top](#jares-python-cheatsheet)

## Any / All
```python
any([False, True, False])# True if at least one item in collection is truthy, False if empty.
all([True,1,3,True])     # True if all items in collection are true
```
[Back to top](#jares-python-cheatsheet)

## Closures

We have a closure in Python when:

- A nested function references a value of its enclosing function and then
- the enclosing function returns the nested function.

```python
def get_multiplier(a):
    def out(b):
        return a * b
    return out

multiply_by_3 = get_multiplier(3)
multiply_by_3(10)       #30
```

- If multiple nested functions within enclosing function reference the same value, that value gets shared.
- To dynamically access function's first free variable use `<function>.__closure__[0].cell_contents`.

[Back to top](#jares-python-cheatsheet)

## Scope
If variable is being assigned to anywhere in the scope, it is regarded as a local variable, unless it is declared as a 'global' or a 'nonlocal'.

```python
def get_counter():
    i = 0
    def out():
        nonlocal i
        i += 1
        return i
    return out

counter = get_counter()
counter()           #1
counter()           #2
counter()           #3
```
[Back to top](#jares-python-cheatsheet)

## Modules

```python
if __name__ == '__main__': # Runs main() if file wasn't imported.
    main()
```

```python
import <module_name>
from <module_name> import <function_name>
import <module_name> as m
from <module_name> import <function_name> as m_function
from <module_name> import *
```


[Back to top](#jares-python-cheatsheet)

## Iterators
In this cheatsheet `<collection>` can also mean an iterator.
```python
<iter> = iter(<collection>)
<iter> = iter(<function>, to_exclusive)     # Sequence of return values until 'to_exclusive'.
<el>   = next(<iter> [, default])           # Raises StopIteration or returns 'default' on end.
```

[Back to top](#jares-python-cheatsheet)


## Generators
Convenient way to implement the iterator protocol.

```python
def count(start, step):
    while True:
        yield start
        start += step

counter = count(10, 2)

next(counter)       #10
next(counter)       #12
next(counter)       #14
```

[Back to top](#jares-python-cheatsheet)

## Decorators
A decorator takes a function, adds some functionality and returns it.

```python
# Performance decorator example:
from time import time

def performance(func, *args, **kwargs):

    def wrapper(*args, **kwargs):
        start = time()
        result = func(*args, **kwargs)
        end = time()
        print(f'---Time to execute: {end-start}ms---')
        return result
    return wrapper

@performance
def da_loop():
    print('Function starting!')
    for _ in range(0, 10000):
        pass
    print('Function ending!')

da_loop()

#output:
# Function starting!
# Function ending!
# ---Time to execute: 0.0002567768096923828ms---
```
```python
# Debugging decorator example:
from functools import wraps

def debug(func):
    @wraps(func)
    def out(*args, **kwargs):
        print(func.__name__)
        return func(*args, **kwargs)
    return out

@debug
def add(x, y):
    return x + y
```
- Wraps is a helper decorator that copies metadata of function add() to function out().
- Without it `add.__name__` would return 'out'.


[Back to top](#jares-python-cheatsheet)


## Classes
User defined objects are created using the class keyword

```python
class <name>:
    age = 80 # Class Object Attribute
    def __init__(self, a):
        self.a = a # Object Attribute

    @classmethod
    def get_class_name(cls):
        return cls.__name__
```
[Back to top](#jares-python-cheatsheet)
## Inheritance
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age  = age

class Employee(Person):
    def __init__(self, name, age, staff_num):
        super().__init__(name, age)
        self.staff_num = staff_num
```
[Back to top](#jares-python-cheatsheet)
## Multiple Inheritance
Important therm: MRO determines the order in which parent classes are traversed when searching for a method:
```python
class A: pass
class B: pass
class C(A, B): pass

C.mro()   #[<class '__main__.C'>, <class '__main__.A'>, <class '__main__.B'>, <class 'object'>]
```
[Back to top](#jares-python-cheatsheet)


## Exceptions and Error Handling
```python
try:
  5/0
except ZeroDivisionError:
  print("No division by zero!")
```
```python
while True:
  try:
    x = int(input('Enter your age: '))
  except ValueError:
    print('Oops!  That was no valid number.  Try again...')
  else: # code that depends on the try block running successfully should be placed in the else block.
    print('Carry on!')
    break
```
[Back to top](#jares-python-cheatsheet)

## Raising Exception
```python
raise ValueError('some error message')
```

## Finally
```python
try:
  raise KeyboardInterrupt
except:
  print('oops')
finally:
  print('All done!')
```
[Back to top](#jares-python-cheatsheet)

## Command Line Arguments
```python
# If this is a file called 'main.py' and we open it by using on terminal:
# $python3 main.py some_value

import sys
script_name = sys.argv[0]   #script_name = 'main.py'
arguments   = sys.argv[1:]  #arguments = ['some_value']

```
[Back to top](#jares-python-cheatsheet)

## File I/O
### Opening Modes:
| Mode | Meaning                                  |
| :--: |------------------------------------------|
| 'r'  | Read (default)                           |
| 'w'  | Write (truncate)                         |
| 'x'  | Write or fail if the file already exists |
| 'a'  | Append                                   |
| 'w+' | Read and write (truncate)                |
| 'r+' | Read and write from the start            |
| 'a+' | Read and write from the end              |
| 't'  | Text mode (default)                      |
| 'b'  | Binary mode                              |


```python

<file> = open('<path>', mode='r', encoding=None)  # Opens a file and returns a corresponding file object.

<file>.seek(0)                      # Moves to the start of the file.
<str/bytes> = <file>.readline()     # Returns a line.
<list>      = <file>.readlines()    # Returns a list of lines.
<file>.write(<str/bytes>)           # Writes a string or bytes object.
<file>.writelines(<list>)           # Writes a list of strings or bytes objects.
```
Methods do not add or strip trailing newlines.

```python

# Read text from a file
def read_file(filename):
    with open(filename, encoding='utf-8') as file:
        return file.readlines() # or read()

for line in read_file(filename):
  print(line)
```

```python
# Write text to a file
def write_to_file(filename, text):
    with open(filename, 'w', encoding='utf-8') as file:
        file.write(text)
```

```python

# Append text to file
def append_to_file(filename, text):
    with open(filename, 'a', encoding='utf-8') as file:
        file.write(text)
```
[Back to top](#jares-python-cheatsheet)

## Useful Built-in Libraries

### CSV
```python
import csv

# Read rows from a CSV file
def read_csv_file(filename):
    with open(filename, encoding='utf-8') as file:
        return csv.reader(file, delimiter=';')

# Write rows to a CSV file
def write_to_csv_file(filename, rows):
    with open(filename, 'w', encoding='utf-8') as file:
        writer = csv.writer(file, delimiter=';')
        writer.writerows(rows)
```
[Back to top](#jares-python-cheatsheet)

### JSON
```python
import json
<str>    = json.dumps(<object>, ensure_ascii=True, indent=None)
<object> = json.loads(<str>)

# Read object from a JSON file
def read_json_file(filename):
    with open(filename, encoding='utf-8') as file:
        return json.load(file)
        
# Write object to a JSON file
def write_to_json_file(filename, an_object):
    with open(filename, 'w', encoding='utf-8') as file:
        json.dump(an_object, file, ensure_ascii=False, indent=2)

```

[Back to top](#jares-python-cheatsheet)
### Pickle

```python
import pickle
<bytes>  = pickle.dumps(<object>)
<object> = pickle.loads(<bytes>)

# Read object from a file
def read_pickle_file(filename):
    with open(filename, 'rb') as file:
        return pickle.load(file)
        
# Write object to a file
def write_to_pickle_file(filename, an_object):
    with open(filename, 'wb') as file:
        pickle.dump(an_object, file)
        
```

[Back to top](#jares-python-cheatsheet)

### Time
```python
from time import time
start_time = time()  # Seconds since
...
duration = time() - start_time
```

[Back to top](#jares-python-cheatsheet)


### Math
```python
from math import e, pi
from math import cos, acos, sin, asin, tan, atan, degrees, radians
from math import log, log10, log2
from math import inf, nan, isinf, isnan
```

[Back to top](#jares-python-cheatsheet)


### Statictics
```python
from statistics import mean, median, variance, pvariance, pstdev
```

[Back to top](#jares-python-cheatsheet)


### Random
```python
from random import random, randint, choice, shuffle
random() # random float between 0 and 1
randint(0, 100) # random integer between 0 and 100
random_el = choice([1,2,3,4]) # select a random element from list
shuffle([1,2,3,4]) # shuffles a list
```


[Back to top](#jares-python-cheatsheet)


### Datetime
Module 'datetime' provides 'date' \<D>, 'time' \<T>, 'datetime' \<DT> and 'timedelta' \<TD> classes. All are immutable and hashable.
Time and datetime can be 'aware' \<a>, meaning they have defined timezone, or 'naive' \<n>, meaning they don't.
If object is naive it is presumed to be in system's timezone.
```python
from datetime import date, time, datetime, timedelta
from dateutil.tz import UTC, tzlocal, gettz
```

Constructors
```python
<D>  = date(year, month, day)
<T>  = time(hour=0, minute=0, second=0, microsecond=0, tzinfo=None, fold=0)
<DT> = datetime(year, month, day, hour=0, minute=0, second=0, ...)
<TD> = timedelta(days=0, seconds=0, microseconds=0, milliseconds=0,
                 minutes=0, hours=0, weeks=0)
```
Use '\<D/DT>.weekday()' to get the day of the week (Mon == 0).
'fold=1' means second pass in case of time jumping back for one hour.

Now
```python
<D/DTn>  = D/DT.today()                     # Current local date or naive datetime.
<DTn>    = DT.utcnow()                      # Naive datetime from current UTC time.
<DTa>    = DT.now(<tz>)                     # Aware datetime from current tz time.
```

Timezone
```python
<tz>     = UTC                              # UTC timezone.
<tz>     = tzlocal()                        # Local timezone.
<tz>     = gettz('<Cont.>/<City>')          # Timezone from 'Continent/City_Name' str.
```
```python
<DTa>    = <DT>.astimezone(<tz>)            # Datetime, converted to passed timezone.
<Ta/DTa> = <T/DT>.replace(tzinfo=<tz>)      # Unconverted object with new timezone.
```

[Back to top](#jares-python-cheatsheet)


### Regex
Regex stands for 'Regular Expression', and in Python you have to write it by anticipating a "r" before the expression `r"(<regex>)"`
Example: `r"([a-zA-Z])"`

```python
import re
<str>   = re.sub(<regex>, new, text, count=0)  # Substitutes all occurrences.
<list>  = re.findall(<regex>, text)            # Returns all occurrences.
<list>  = re.split(<regex>, text, maxsplit=0)  # Use brackets in regex to keep the matches.
<Match> = re.search(<regex>, text)             # Searches for first occurrence of pattern.
<Match> = re.match(<regex>, text)              # Searches only at the beginning of the text.
```

```python
#IP regex example
import re

pattern = re.compile(r"([0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3})")

string_a = "120.0.0.1 Baby Yoda was here 180.34.55.101"
string_b = "101.23.24.90"

pattern.search(string_a)       # <re.Match object; span=(0, 9), match='120.0.0.1'>
pattern.findall(string_a)      # ['120.0.0.1', '180.34.55.101']
pattern.fullmatch(string_a)    # None
pattern.match(string_a)        # <re.Match object; span=(0, 9), match='120.0.0.1'>

pattern.search(string_b)       # <re.Match object; span=(0, 12), match='101.23.24.90'>
pattern.findall(string_b)      # ['101.23.24.90']
pattern.fullmatch(string_b)    # <re.Match object; span=(0, 12), match='101.23.24.90'>
pattern.match(string_b)        # <re.Match object; span=(0, 12), match='101.23.24.90'>
```
```python
# Groups and subgroups example
m = re.match(r"(\w+) (\w+)", "Isaac Newton, physicist")

m.group(0)      # 'Isaac Newton' --> The entire match
m.group(1)      # 'Isaac'        --> The first parenthesized subgroup.
m.group(2)      # 'Newton'       --> The second parenthesized subgroup.
m.group(1, 2)   # ('Isaac', 'Newton') --> Multiple arguments give us a tuple.
```
Match Object
```python
<str>   = <Match>.group()   # Whole match.
<str>   = <Match>.group(1)  # Part in first bracket.
<tuple> = <Match>.groups()  # All bracketed parts.
<int>   = <Match>.start()   # Start index of a match.
<int>   = <Match>.end()     # Exclusive end index of a match.
```

Special Sequences: Expressions below hold true for strings that contain only ASCII characters. Use capital letters for negation.
```python
'\d' == '[0-9]'          # Digit
'\s' == '[ \t\n\r\f\v]'  # Whitespace
'\w' == '[a-zA-Z0-9_]'   # Alphanumeric
```
By the way, [here](https://regex101.com/) you have a great site to test your regular expressions

[Back to top](#jares-python-cheatsheet)

## Unittest
Testing is a way to compare how a program should ideally respond towards an error, and how it actually does. You can see the whole documentation through [here](https://docs.python.org/3/library/unittest.html)
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
        # check that s.split fails when the separator is not a string
        with self.assertRaises(TypeError):
            s.split(2)

if __name__ == '__main__':
    unittest.main()
```
Some features on the command line:
```
python -m unittest -v
```

## Virtual Environments
A Virtual Environment is like a separated world inside your machine, that you can create in order to set different versions of already-installed libraries. Because it's a separate world, you may use it as a blank sheet to start installing anything your program needs, without affecting the rest of your computer.

See more at: [https://docs.python.org/3/library/venv.html]

Create the venv
```
$ python3 -m venv /path/to/new/virtual/environment
```
Then activate it
```
$ source <venv>/bin/activate
```
Now you will see the name of your environment at the beginning of the terminal. And you can install whatever you want. For example:
Screen Shot 2021-08-02 at 02.26.27.png<img width="799" alt="Screen Shot 2021-08-02 at 02 26 27" src="https://user-images.githubusercontent.com/64754731/127808472-62a10eae-d02d-479c-855c-16060db42cf5.png">


*More info at https://github.com/gto76/python-cheatsheet*


  
