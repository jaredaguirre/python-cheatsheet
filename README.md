# Jare's Python Cheatsheet

The present cheatsheet is a briefing about the different Python syntax shortcuts and features. It is based on the original cheatsheet from the course 'ZTM: Python Developer' that you can find [here](https://zerotomastery.io/cheatsheets/python-cheat-sheet/#file-io).
However, some of the items were modified for personal understanding. Some of the examples were changed as well to clarify and update concepts. Enjoy!

## Contents

### Python Types:
[Numbers](#), [Strings](#), [Booleans](#), [Lists](#), [Dictionaries](#), [Tuples](#), [Sets](#), [None](#)

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
[Back to top](#)
