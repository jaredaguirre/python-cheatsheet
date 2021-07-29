# Jare's Python Cheatsheet

The present cheatsheet is a briefing about the different Python syntax shortcuts and features. It is based on the original cheatsheet from the course 'ZTM: Python Developer' that you can find [here](https://zerotomastery.io/cheatsheets/python-cheat-sheet/#file-io).
However, some of the items were modified for personal understanding. Some of the examples were changed as well to clarify and update concepts. Enjoy!

## Contents

### Python Types:
[Numbers](#), [Strings](#), [Booleans](#), [Fundamental Data Structures Comparison](#), [Lists](#), [Tuples](#), [Sets](#),[Dictionaries](#), [None](#)

### Python Basics:
[Comparison Operators](#), [Logical](#) [Operators](#), [Loops](#), [Range](#), [Enumerate](#), [Counter](#), [Named Tuple](#), [OrderedDict](#)

### Functions:
[Functions](#), [Lambda](#), [Comprehensions](#), [Map](#), [Filter](#), [Reduce](#), [Ternary](#), [Any](#), [All](#), [Closures](#), [Scope](#)

### Advanced Python:
[Modules](#), [Iterators](#), [Generators](#), [Decorators](#), [Class](#), [Exceptions](#), [Command Line Arguments](#), [File IO](#), [Useful Libraries](#)

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
