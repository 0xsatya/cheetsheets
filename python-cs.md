# 🐍 Python Cheat Sheet

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

> A comprehensive Python reference guide covering syntax, data structures, functions, and advanced concepts.

## 📋 Table of Contents

- [Variables & Data Types](#-variables--data-types)
- [Built-in Functions](#-built-in-functions)
- [Strings](#-strings)
- [Lists](#-lists)
- [Tuples](#-tuples)
- [Dictionaries](#-dictionaries)
- [Sets](#-sets)
- [Control Flow](#-control-flow)
- [Functions](#-functions)
- [Classes & OOP](#-classes--oop)
- [File Operations](#-file-operations)
- [Exception Handling](#-exception-handling)
- [Advanced Topics](#-advanced-topics)

---

## 🔤 Variables & Data Types

### Variable Assignment
```python
# Multiple assignment
a = b = c = 1
a, b, c = 1, 2, "john"

# Variable deletion
del var
del var_a, var_b

# Augmented assignment
x += 2
x -= 1
x *= 3
x /= 2
```

### Python Data Types (8 types)
```python
# Numeric types
int_var = 42
float_var = 3.14
complex_var = 3 + 4j

# Boolean
bool_var = True

# Text type
str_var = "Hello World"

# Sequence types
list_var = [1, 2, 3]
tuple_var = (1, 2, 3)

# Set types
set_var = {1, 2, 3}
frozen_set = frozenset([1, 2, 3])

# Mapping type
dict_var = {"key": "value"}
```

### Variable Naming Conventions
- Use `snake_case` for variables and functions
- Use `PascalCase` for classes
- Case sensitive
- Don't overwrite Python keywords
- Use descriptive names

### Variable Scope
1. **Local** - Inside function
2. **Enclosing** - In nested functions
3. **Global** - At module level
4. **Built-in** - Python's built-in names

---

## 🛠️ Built-in Functions

### Type Conversion
```python
# Convert to different types
str(42)          # "42"
int("42")        # 42
float("3.14")    # 3.14
bool(1)          # True
bool(0)          # False
bool("")         # False
bool("hello")    # True

# Container conversions
list("hello")    # ['h', 'e', 'l', 'l', 'o']
tuple([1, 2, 3]) # (1, 2, 3)
set([1, 1, 2])   # {1, 2}
dict([('a', 1)]) # {'a': 1}
```

### Utility Functions
```python
# Basic operations
print("Hello World")
len([1, 2, 3])           # 3
id(variable)             # Memory address
type(variable)           # Data type
isinstance(obj, type)    # Type checking

# Math functions
abs(-20)                 # 20
round(4.5)              # 4
round(4.6)              # 5
min([1, 2, 3])          # 1
max([1, 2, 3])          # 3
sum([1, 2, 3])          # 6

# Character functions
chr(65)                  # 'A'
ord('A')                 # 65

# Binary operations
bin(5)                   # '0b101'
int('0b101', 2)         # 5
hex(255)                # '0xff'
oct(64)                 # '0o100'
```

### String Representation
```python
# String representations
repr("hello")           # "'hello'"
str("hello")            # "hello"
eval("2 + 3")           # 5 (use with caution!)

# Raw strings
print(r'C:\\nowhere')   # C:\\nowhere
```

---

## 📝 Strings

### String Basics
```python
# String creation
str_var = 'Hello World!'
str_var = "Hello World!"
str_var = """Multi-line
string"""

# String slicing [start:stop:step]
text = "Hello World!"
print(text[0])        # H
print(text[2:5])      # llo
print(text[2:])       # llo World!
print(text[:5])       # Hello
print(text[-1])       # !
print(text[::-1])     # !dlroW olleH (reverse)

# String operations
print(text * 2)       # Hello World!Hello World!
print(text + "TEST")  # Hello World!TEST
```

### String Methods
```python
text = "  hello world  "

# Case methods
text.upper()          # "  HELLO WORLD  "
text.lower()          # "  hello world  "
text.capitalize()     # "  Hello world  "
text.title()          # "  Hello World  "
text.swapcase()       # "  HELLO WORLD  "

# Whitespace methods
text.strip()          # "hello world"
text.lstrip()         # "hello world  "
text.rstrip()         # "  hello world"

# Search methods
text.find("world")    # 9
text.index("world")   # 9
text.count("l")       # 3
text.startswith("he") # False
text.endswith("ld")   # False

# Replace and split
text.replace("world", "Python")  # "  hello Python  "
text.split()          # ['hello', 'world']
text.split("l")       # ['  he', '', 'o wor', 'd  ']

# Join
words = ['hello', 'world']
" ".join(words)       # "hello world"
"-".join(words)       # "hello-world"

# Check methods
text.isalnum()        # False
text.isalpha()        # False
text.isdigit()        # False
text.isspace()        # False
text.islower()        # True
text.isupper()        # False

# Format methods
text.center(20)       # "   hello world    "
text.ljust(20)        # "hello world         "
text.rjust(20)        # "         hello world"
text.zfill(20)        # "0000000hello world"

# Encoding
text.encode('utf-8')  # b'  hello world  '
```

### String Formatting
```python
# f-strings (Python 3.6+) - RECOMMENDED
name = "Alice"
age = 30
f"Hello, {name}! You are {age} years old."

# f-strings with expressions
f"Next year you'll be {age + 1} years old"
f"Name length: {len(name)}"

# f-strings with formatting
price = 19.99
f"Price: ${price:.2f}"  # Price: $19.99
f"Percentage: {0.25:.1%}"  # Percentage: 25.0%

# .format() method
"Hello, {}! You are {} years old.".format(name, age)
"Hello, {name}! You are {age} years old.".format(name=name, age=age)

# % formatting (legacy - avoid in new code)
"Hello, %s! You are %d years old." % (name, age)

# Raw strings
path = r"C:\Users\Name\Documents"  # Raw string
```

### Why Use F-Strings?
F-strings were introduced in Python 3.6 and are the **preferred** way to format strings because:

1. **Performance**: F-strings are faster than `.format()` and `%` formatting
2. **Readability**: More concise and readable syntax
3. **Expression Support**: Can include any Python expression inside `{}`
4. **Less Error-Prone**: No need to match positional arguments
5. **IDE Support**: Better autocomplete and syntax highlighting

```python
# Performance comparison
import timeit

# f-string (fastest)
timeit.timeit('f"Hello {name}"', setup='name="World"', number=1000000)
# ~0.1 seconds

# .format() (slower)
timeit.timeit('"Hello {}".format(name)', setup='name="World"', number=1000000)
# ~0.15 seconds

# % formatting (slowest)
timeit.timeit('"Hello %s" % name', setup='name="World"', number=1000000)
# ~0.2 seconds
```

### String Properties
- **Immutable**: Strings cannot be modified in place
- **Indexed**: Access characters by position
- **Iterable**: Can loop through characters
- **Hashable**: Can be used as dictionary keys


---

## 🔄 Control Flow

### While Loops
```python
# Basic while loop
count = 0
while count < 5:
    print(count)
    count += 1

# While with else (executes if loop completes normally)
count = 0
while count < 3:
    print(count)
    count += 1
else:
    print("Loop completed!")

# Break and continue
count = 0
while count < 10:
    if count == 3:
        break  # Exit loop
    if count == 1:
        count += 1
        continue  # Skip to next iteration
    print(count)
    count += 1
```

### For Loops
```python
# Loop through list
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# Loop through string
for char in "banana":
    print(char)

# Loop through range
for i in range(6):        # 0 to 5
    print(i)

for i in range(2, 6):     # 2 to 5
    print(i)

for i in range(2, 30, 3): # 2 to 29, step 3
    print(i)

# For with else
for i in range(3):
    print(i)
else:
    print("Loop finished!")

# Pass statement (do nothing)
for i in [0, 1, 2]:
    pass  # Placeholder for future code
```

### Using Underscore (_) in Loops
The underscore `_` is a conventional variable name used when you don't need the actual value:

```python
# When you don't need the loop variable
for _ in range(5):
    print("Hello")  # Prints "Hello" 5 times

# When you need index but not value
for i, _ in enumerate(["a", "b", "c"]):
    print(f"Index: {i}")  # Only prints index

# When unpacking but ignoring some values
data = [(1, 2, 3), (4, 5, 6), (7, 8, 9)]
for x, _, z in data:  # Ignore middle value
    print(f"First: {x}, Last: {z}")

# Multiple underscores for multiple ignored values
for _, _, value in data:
    print(f"Value: {value}")
```

**Why use `_`?**
1. **Convention**: Signals to other developers that the value is intentionally ignored
2. **Readability**: Makes code intent clear
3. **Linting**: Many linters won't warn about unused `_` variables
4. **Performance**: Slight memory savings (though minimal)

### Range Function
```python
# Range basics
range(10)        # 0 to 9
range(1, 11)     # 1 to 10
range(0, 30, 5)  # 0, 5, 10, 15, 20, 25

# Convert to list
list(range(5))   # [0, 1, 2, 3, 4]

# Enumerate (get index and value)
for i, char in enumerate("hello"):
    print(i, char)  # 0 h, 1 e, 2 l, 3 l, 4 o
```

### Conditional Statements
```python
# If-elif-else
age = 18
if age < 13:
    print("Child")
elif age < 20:
    print("Teenager")
    else:
    print("Adult")

# Ternary operator
status = "adult" if age >= 18 else "minor"

# Logical operators
if age >= 18 and age <= 65:
    print("Working age")

if age < 18 or age > 65:
    print("Not working age")

if not age < 18:
    print("Adult")

# Membership operators
if "apple" in fruits:
    print("Found apple")

if "orange" not in fruits:
    print("No orange")

# Identity operators
x = [1, 2, 3]
y = x
z = [1, 2, 3]

print(x is y)      # True (same object)
print(x is z)      # False (different objects)
print(x == z)      # True (same values)
```

### Filter Function
```python
# Filter with function
def is_even(n):
    return n % 2 == 0

numbers = [1, 2, 3, 4, 5, 6]
even_numbers = list(filter(is_even, numbers))  # [2, 4, 6]

# Filter with lambda
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))

# Filter strings
words = ['hi', 'this', 'is', 'a', 'very', 'simple', 'string']
short_words = list(filter(lambda x: len(x) <= 2, words))  # ['hi', 'is', 'a']
```
 
---

## 📋 Lists

### List Basics
```python
# List creation
my_list = ['abcd', 786, 2.23, 'john', 70.2]
tiny_list = [123, 'john']

# List access and slicing
print(my_list)        # ['abcd', 786, 2.23, 'john', 70.2]
print(my_list[0])     # abcd
print(my_list[1:3])   # [786, 2.23]
print(my_list[2:])    # [2.23, 'john', 70.2]
print(my_list[-1])    # 70.2 (last element)
print(my_list[::-1])  # [70.2, 'john', 2.23, 786, 'abcd'] (reverse)

# List operations
print(tiny_list * 2)           # [123, 'john', 123, 'john']
print(my_list + tiny_list)     # ['abcd', 786, 2.23, 'john', 70.2, 123, 'john']
print(len(my_list))            # 5
print(786 in my_list)          # True
```

### List Methods
```python
numbers = [1, 2, 3, 4, 5]

# Adding elements
numbers.append(6)              # [1, 2, 3, 4, 5, 6]
numbers.insert(0, 0)           # [0, 1, 2, 3, 4, 5, 6]
numbers.extend([7, 8, 9])      # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Removing elements
numbers.remove(0)              # [1, 2, 3, 4, 5, 6, 7, 8, 9]
popped = numbers.pop()         # popped = 9, numbers = [1, 2, 3, 4, 5, 6, 7, 8]
popped = numbers.pop(0)        # popped = 1, numbers = [2, 3, 4, 5, 6, 7, 8]
del numbers[0]                 # [3, 4, 5, 6, 7, 8]

# List information
numbers.count(4)               # 1
numbers.index(4)               # 1
numbers.index(4, 0, 3)         # 1 (search between indices 0-3)

# List modification
numbers.reverse()              # [8, 7, 6, 5, 4, 3]
numbers.sort()                 # [3, 4, 5, 6, 7, 8]
numbers.sort(reverse=True)     # [8, 7, 6, 5, 4, 3]

# List copying
new_list = numbers.copy()      # Shallow copy
new_list = numbers[:]          # Slice copy
new_list = list(numbers)       # Constructor copy
```

### List Functions
```python
numbers = [3, 1, 4, 1, 5, 9, 2, 6]

# Built-in functions
len(numbers)                   # 8
max(numbers)                   # 9
min(numbers)                   # 1
sum(numbers)                   # 31
sorted(numbers)                # [1, 1, 2, 3, 4, 5, 6, 9] (new list)
sorted(numbers, reverse=True)  # [9, 6, 5, 4, 3, 2, 1, 1]

# List comprehension
squares = [x**2 for x in range(10)]           # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
evens = [x for x in range(20) if x % 2 == 0]  # [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# List unpacking
a, b, c, *other, d = [1, 2, 3, 4, 5, 6, 7, 8, 9, 11]
# a=1, b=2, c=3, other=[4, 5, 6, 7, 8, 9], d=11

# Join list to string
words = ['hello', 'world', 'python']
' '.join(words)                # "hello world python"
'-'.join(words)                # "hello-world-python"
```

### List Properties
- **Mutable**: Can be modified after creation
- **Ordered**: Elements maintain their order
- **Indexed**: Access elements by position
- **Duplicates**: Can contain duplicate elements
- **Heterogeneous**: Can contain different data types

<details>
<summary>🔬 In-Depth for Advanced Devs: List Internal Implementation</summary>

### How Lists Work Internally in Python

**Memory Layout:**
- Lists are implemented as **dynamic arrays** (not linked lists)
- They use a **contiguous block of memory** for better cache performance
- Each list object contains:
  - Pointer to the array of object references
  - Current size (number of elements)
  - Allocated size (capacity)

```python
import sys

# Memory usage analysis
my_list = [1, 2, 3, 4, 5]
print(f"List size: {sys.getsizeof(my_list)} bytes")
print(f"List length: {len(my_list)}")

# Memory growth pattern
for i in range(10):
    my_list.append(i)
    print(f"Length: {len(my_list)}, Size: {sys.getsizeof(my_list)} bytes")
```

**Dynamic Resizing:**
- When list grows beyond capacity, Python allocates a new larger array
- Growth factor is typically **1.125x** (25% increase)
- Old array is copied to new array, then old array is freed
- This is why `append()` is O(1) amortized time

```python
# Demonstrating growth pattern
def analyze_list_growth():
    lst = []
    prev_size = 0
    
    for i in range(100):
        lst.append(i)
        current_size = sys.getsizeof(lst)
        if current_size != prev_size:
            print(f"Length: {len(lst)}, Size: {current_size} bytes")
            prev_size = current_size

analyze_list_growth()
```

**Time Complexities:**
- **Access**: O(1) - direct array indexing
- **Append**: O(1) amortized - may trigger resize
- **Insert**: O(n) - elements must be shifted
- **Delete**: O(n) - elements must be shifted
- **Search**: O(n) - linear search

**Memory Overhead:**
- Each list object: ~56 bytes (Python 3.8+)
- Each element reference: 8 bytes (64-bit system)
- Total overhead = 56 + (8 × number_of_elements)

```python
# Memory overhead calculation
def calculate_list_overhead(n):
    lst = [None] * n
    total_size = sys.getsizeof(lst)
    element_size = 8  # 8 bytes per reference
    overhead = total_size - (element_size * n)
    return overhead

print(f"Overhead for 1000 elements: {calculate_list_overhead(1000)} bytes")
```

**Optimization Tips:**
1. **Pre-allocate** when you know the size: `lst = [None] * n`
2. **Use list comprehensions** for better performance
3. **Avoid frequent insertions** at the beginning
4. **Consider `collections.deque`** for frequent insertions/deletions at both ends

</details>


---

## 📦 Tuples

### Tuple Basics
```python
# Tuple creation
my_tuple = ('abcd', 786, 2.23, 'john', 70.2)
tiny_tuple = (123, 'john')

# Tuple access and slicing
print(my_tuple)        # ('abcd', 786, 2.23, 'john', 70.2)
print(my_tuple[0])     # abcd
print(my_tuple[1:3])   # (786, 2.23)
print(my_tuple[2:])    # (2.23, 'john', 70.2)
print(my_tuple[-1])    # 70.2 (last element)
print(my_tuple[::-1])  # (70.2, 'john', 2.23, 786, 'abcd') (reverse)

# Tuple operations
print(tiny_tuple * 2)           # (123, 'john', 123, 'john')
print(my_tuple + tiny_tuple)    # ('abcd', 786, 2.23, 'john', 70.2, 123, 'john')
print(len(my_tuple))            # 5
print(786 in my_tuple)          # True
```

### Tuple Operations
```python
# Empty tuple
empty_tuple = ()

# Single element tuple (note the comma!)
single_tuple = (50,)

# Tuple concatenation
tup1 = (1, 2, 3)
tup2 = (4, 5, 6)
tup3 = tup1 + tup2  # (1, 2, 3, 4, 5, 6)

# Tuple deletion (entire tuple only)
del tup1  # Deletes the entire tuple

# Tuple indexing and slicing
T = ('C++', 'Java', 'Python')
print(T[2])    # 'Python' (offsets start at zero)
print(T[-2])   # 'Java' (negative: count from the right)
print(T[1:])   # ('Java', 'Python') (slicing fetches sections)
```

### Tuple Functions
```python
numbers = (3, 1, 4, 1, 5, 9, 2, 6)

# Built-in functions
len(numbers)                   # 8
max(numbers)                   # 9
min(numbers)                   # 1
sum(numbers)                   # 31
sorted(numbers)                # [1, 1, 2, 3, 4, 5, 6, 9] (returns list)

# Convert to tuple
list_to_tuple = tuple([1, 2, 3])  # (1, 2, 3)
string_to_tuple = tuple("hello")  # ('h', 'e', 'l', 'l', 'o')
```

### Tuple Methods
```python
numbers = (1, 2, 3, 2, 4, 2)

# Count occurrences
numbers.count(2)               # 3

# Find index
numbers.index(2)               # 1
numbers.index(2, 2)            # 3 (start searching from index 2)
numbers.index(2, 2, 5)         # 3 (search between indices 2-5)
```

### Tuple Properties
- **Immutable**: Cannot be modified after creation
- **Ordered**: Elements maintain their order
- **Indexed**: Access elements by position
- **Duplicates**: Can contain duplicate elements
- **Heterogeneous**: Can contain different data types
- **Faster**: Generally faster than lists for read operations
- **Hashable**: Can be used as dictionary keys

### When to Use Tuples
- When data should not be changed
- As dictionary keys
- Function return values
- Coordinates, RGB values, etc.
- Performance-critical code

<details>
<summary>🔬 In-Depth for Advanced Devs: Tuple Internal Implementation</summary>

### How Tuples Work Internally in Python

**Memory Layout:**
- Tuples are implemented as **fixed-size arrays**
- They use **contiguous memory** like lists but are immutable
- Each tuple object contains:
  - Pointer to the array of object references
  - Fixed size (cannot be changed)
  - No capacity field (unlike lists)

```python
import sys

# Memory usage analysis
my_tuple = (1, 2, 3, 4, 5)
print(f"Tuple size: {sys.getsizeof(my_tuple)} bytes")
print(f"Tuple length: {len(my_tuple)}")

# Memory comparison with list
my_list = [1, 2, 3, 4, 5]
print(f"List size: {sys.getsizeof(my_list)} bytes")
print(f"Tuple is {sys.getsizeof(my_tuple) - sys.getsizeof(my_list)} bytes smaller")
```

**Immutability Benefits:**
- **Hashable**: Can be used as dictionary keys
- **Memory efficient**: No need for capacity tracking
- **Thread-safe**: Cannot be modified by other threads
- **Optimized**: Python can optimize tuple operations

```python
# Hashability demonstration
point1 = (3, 4)
point2 = (5, 6)
point_dict = {point1: "Point A", point2: "Point B"}
print(point_dict[(3, 4)])  # "Point A"

# This would fail with lists
# point_list = [3, 4]
# point_dict[point_list]  # TypeError: unhashable type: 'list'
```

**Time Complexities:**
- **Access**: O(1) - direct array indexing
- **Creation**: O(n) - must copy all elements
- **Concatenation**: O(n) - creates new tuple
- **Search**: O(n) - linear search
- **Hash calculation**: O(n) - must hash all elements

**Memory Overhead:**
- Each tuple object: ~40 bytes (Python 3.8+)
- Each element reference: 8 bytes (64-bit system)
- Total overhead = 40 + (8 × number_of_elements)

```python
# Memory overhead calculation
def calculate_tuple_overhead(n):
    tup = tuple(range(n))
    total_size = sys.getsizeof(tup)
    element_size = 8  # 8 bytes per reference
    overhead = total_size - (element_size * n)
    return overhead

print(f"Overhead for 1000 elements: {calculate_tuple_overhead(1000)} bytes")
```

**Performance Characteristics:**
- **Faster creation** than lists (no capacity management)
- **Faster access** than lists (no bounds checking for modifications)
- **Slower concatenation** than lists (creates new object)
- **Memory efficient** for small collections

```python
import timeit

# Performance comparison
def create_list(n):
    return [i for i in range(n)]

def create_tuple(n):
    return tuple(i for i in range(n))

# Time creation
n = 1000
list_time = timeit.timeit(lambda: create_list(n), number=10000)
tuple_time = timeit.timeit(lambda: create_tuple(n), number=10000)

print(f"List creation: {list_time:.4f}s")
print(f"Tuple creation: {tuple_time:.4f}s")
```

**Optimization Tips:**
1. **Use tuples** for small, fixed collections
2. **Use tuples** as dictionary keys when possible
3. **Use tuples** for function return values
4. **Avoid large tuples** (consider named tuples or dataclasses)

</details>



---

## 📚 Dictionaries

### Dictionary Basics
```python
# Dictionary creation
my_dict = {}
my_dict['one'] = "This is one"
my_dict[2] = "This is two"

# Dictionary literal
tiny_dict = {'name': 'john', 'code': 6734, 'dept': 'sales'}

# Dictionary access
print(my_dict['one'])        # "This is one"
print(my_dict[2])            # "This is two"
print(tiny_dict)             # {'name': 'john', 'code': 6734, 'dept': 'sales'}
print(tiny_dict.keys())      # dict_keys(['name', 'code', 'dept'])
print(tiny_dict.values())    # dict_values(['john', 6734, 'sales'])
print(tiny_dict.items())     # dict_items([('name', 'john'), ('code', 6734), ('dept', 'sales')])

# Safe access
print(tiny_dict.get('name'))     # 'john'
print(tiny_dict.get('age'))      # None
print(tiny_dict.get('age', 0))   # 0 (default value)
```

### Dictionary Operations
```python
# Updating dictionary
person = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}
person['Age'] = 8              # Update existing entry
person['School'] = "DPS School"  # Add new entry

# Deleting from dictionary
del person['Name']             # Remove entry with key 'Name'
person.clear()                 # Remove all entries
del person                     # Delete entire dictionary

# Dictionary comprehension
squares = {x: x**2 for x in range(5)}  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
evens = {x: x*2 for x in range(5) if x % 2 == 0}  # {0: 0, 2: 4, 4: 8}
```

### Dictionary Methods
```python
person = {'name': 'Alice', 'age': 30, 'city': 'New York'}

# Dictionary methods
person.clear()                 # Remove all elements
person.copy()                  # Shallow copy
person.fromkeys(['a', 'b'], 0)  # {'a': 0, 'b': 0}
person.get('name')             # 'Alice'
person.get('salary', 0)        # 0 (default value)
person.items()                 # dict_items([('name', 'Alice'), ('age', 30), ('city', 'New York')])
person.keys()                  # dict_keys(['name', 'age', 'city'])
person.values()                # dict_values(['Alice', 30, 'New York'])
person.pop('age')              # 30 (removes and returns value)
person.popitem()               # ('city', 'New York') (removes last item)
person.setdefault('salary', 50000)  # 50000 (sets default if key doesn't exist)
person.update({'job': 'Engineer'})  # Adds new key-value pair
```

### Dictionary Functions
```python
person = {'name': 'Alice', 'age': 30, 'city': 'New York'}

# Built-in functions
len(person)                    # 3
str(person)                    # "{'name': 'Alice', 'age': 30, 'city': 'New York'}"
type(person)                   # <class 'dict'>

# Dictionary operations
'name' in person              # True
'name' not in person          # False
```

### Dictionary Properties
- **Mutable**: Can be modified after creation
- **Unordered**: Elements don't maintain order (Python 3.7+ maintains insertion order)
- **Indexed by keys**: Access values by keys, not position
- **No duplicates**: Keys must be unique
- **Keys must be immutable**: Strings, numbers, tuples can be keys
- **Values can be any type**: Including other dictionaries

### Dictionary Use Cases
- Storing related data
- Fast lookups by key
- Counting occurrences
- Caching/memoization
- Configuration settings
- JSON-like data structures

<details>
<summary>🔬 In-Depth for Advanced Devs: Dictionary Internal Implementation</summary>

### How Dictionaries Work Internally in Python

**Hash Table Implementation:**
- Dictionaries are implemented as **hash tables** (hash maps)
- They use **open addressing** with **quadratic probing** for collision resolution
- Each dictionary object contains:
  - Array of hash table entries
  - Number of used entries
  - Number of total entries
  - Hash function

```python
import sys

# Memory usage analysis
my_dict = {'a': 1, 'b': 2, 'c': 3}
print(f"Dictionary size: {sys.getsizeof(my_dict)} bytes")
print(f"Dictionary length: {len(my_dict)}")

# Memory growth pattern
for i in range(10):
    my_dict[f'key_{i}'] = i
    print(f"Length: {len(my_dict)}, Size: {sys.getsizeof(my_dict)} bytes")
```

**Hash Table Structure:**
- **Hash function**: Converts keys to array indices
- **Collision resolution**: Quadratic probing when hash collision occurs
- **Load factor**: When 2/3 full, table is resized
- **Resizing**: New table is 4x larger, all entries rehashed

```python
# Demonstrating hash table behavior
def analyze_dict_growth():
    d = {}
    prev_size = 0
    
    for i in range(100):
        d[f'key_{i}'] = i
        current_size = sys.getsizeof(d)
        if current_size != prev_size:
            print(f"Length: {len(d)}, Size: {current_size} bytes")
            prev_size = current_size

analyze_dict_growth()
```

**Time Complexities:**
- **Access**: O(1) average, O(n) worst case
- **Insert**: O(1) average, O(n) worst case
- **Delete**: O(1) average, O(n) worst case
- **Search**: O(1) average, O(n) worst case

**Memory Overhead:**
- Each dictionary object: ~232 bytes (Python 3.8+)
- Each key-value pair: ~24 bytes overhead
- Hash table overhead: ~8 bytes per slot

```python
# Memory overhead calculation
def calculate_dict_overhead(n):
    d = {f'key_{i}': i for i in range(n)}
    total_size = sys.getsizeof(d)
    # Rough estimate: 24 bytes per key-value pair
    estimated_data = 24 * n
    overhead = total_size - estimated_data
    return overhead

print(f"Overhead for 1000 pairs: {calculate_dict_overhead(1000)} bytes")
```

**Hash Collisions:**
- **Hash function**: Built-in `hash()` function
- **Collision resolution**: Quadratic probing
- **Load factor**: Resizes when 2/3 full
- **Performance**: Degrades with many collisions

```python
# Hash collision demonstration
def demonstrate_collisions():
    # Create keys that might collide
    keys = ['a', 'b', 'c', 'd', 'e']
    for key in keys:
        print(f"Key: {key}, Hash: {hash(key)}")
    
    # Show dictionary internals
    d = {key: i for i, key in enumerate(keys)}
    print(f"Dictionary: {d}")

demonstrate_collisions()
```

**Optimization Tips:**
1. **Use immutable keys** (strings, numbers, tuples)
2. **Pre-allocate** when you know the size
3. **Use `collections.defaultdict`** for default values
4. **Use `collections.OrderedDict`** for insertion order
5. **Consider `collections.Counter`** for counting

```python
# Performance comparison
import timeit

def create_dict(n):
    return {i: i**2 for i in range(n)}

def create_list(n):
    return [i**2 for i in range(n)]

# Time creation
n = 1000
dict_time = timeit.timeit(lambda: create_dict(n), number=1000)
list_time = timeit.timeit(lambda: create_list(n), number=1000)

print(f"Dictionary creation: {dict_time:.4f}s")
print(f"List creation: {list_time:.4f}s")
```

</details>

---

## 🎯 Sets

### Set Basics
```python
# Set creation
my_set = {1, 2, 3, 4, 5}  # Unique values only
empty_set = set()          # Empty set (not {} - that's a dict)

# Convert list to set (removes duplicates)
new_list = [1, 2, 3, 3, 3, 4, 4, 5, 6, 1]
unique_set = set(new_list)  # {1, 2, 3, 4, 5, 6}

# Set operations
print(len(my_set))         # 5
print(3 in my_set)         # True
print(10 in my_set)        # False
```

### Set Methods
```python
my_set = set()

# Adding elements
my_set.add(1)              # {1}
my_set.add(100)            # {1, 100}
my_set.add(100)            # {1, 100} (no duplicates!)
my_set.update([2, 3, 4])   # {1, 100, 2, 3, 4}

# Removing elements
my_set.remove(100)         # {1, 2, 3, 4} (raises KeyError if not found)
my_set.discard(100)        # {1, 2, 3, 4} (no error if not found)
popped = my_set.pop()      # Removes and returns arbitrary element
my_set.clear()             # {} (clears all values)

# Set copying
new_set = {1, 2, 3}.copy() # {1, 2, 3}
```

### Set Operations
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# Union (all elements from both sets)
union_set = set1.union(set2)           # {1, 2, 3, 4, 5}
union_set = set1 | set2                # {1, 2, 3, 4, 5}

# Intersection (common elements)
intersection_set = set1.intersection(set2)  # {3}
intersection_set = set1 & set2              # {3}

# Difference (elements in set1 but not in set2)
difference_set = set1.difference(set2)      # {1, 2}
difference_set = set1 - set2                # {1, 2}

# Symmetric difference (elements in either set but not both)
symmetric_diff = set1.symmetric_difference(set2)  # {1, 2, 4, 5}
symmetric_diff = set1 ^ set2                      # {1, 2, 4, 5}
```

### Set Comparison
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
set3 = {1, 2, 3, 4, 5}

# Set relationships
set1.issubset(set3)        # True (all elements of set1 are in set3)
set1 <= set3               # True
set1 < set3                # True (proper subset)

set3.issuperset(set1)      # True (set3 contains all elements of set1)
set3 >= set1               # True
set3 > set1                # True (proper superset)

set1.isdisjoint(set2)      # False (they have common elements)
```

### Set Properties
- **Unique elements**: No duplicates allowed
- **Unordered**: Elements don't maintain order
- **Mutable**: Can be modified after creation
- **No indexing**: Cannot access elements by position
- **Hashable elements**: All elements must be immutable
- **Fast membership testing**: O(1) average case

### Set Use Cases
- Removing duplicates from lists
- Membership testing
- Mathematical set operations
- Finding unique elements
- Database-like operations (union, intersection, etc.)

<details>
<summary>🔬 In-Depth for Advanced Devs: Set Internal Implementation</summary>

### How Sets Work Internally in Python

**Hash Table Implementation:**
- Sets are implemented as **hash tables** similar to dictionaries
- They use **open addressing** with **quadratic probing** for collision resolution
- Each set object contains:
  - Array of hash table entries (storing only keys, no values)
  - Number of used entries
  - Number of total entries
  - Hash function

```python
import sys

# Memory usage analysis
my_set = {1, 2, 3, 4, 5}
print(f"Set size: {sys.getsizeof(my_set)} bytes")
print(f"Set length: {len(my_set)}")

# Memory growth pattern
for i in range(10):
    my_set.add(i)
    print(f"Length: {len(my_set)}, Size: {sys.getsizeof(my_set)} bytes")
```

**Hash Table Structure:**
- **Hash function**: Same as dictionaries, uses `hash()` function
- **Collision resolution**: Quadratic probing
- **Load factor**: Resizes when 2/3 full
- **Resizing**: New table is 4x larger, all entries rehashed

```python
# Demonstrating set growth
def analyze_set_growth():
    s = set()
    prev_size = 0
    
    for i in range(100):
        s.add(i)
        current_size = sys.getsizeof(s)
        if current_size != prev_size:
            print(f"Length: {len(s)}, Size: {current_size} bytes")
            prev_size = current_size

analyze_set_growth()
```

**Time Complexities:**
- **Access**: O(1) average, O(n) worst case
- **Insert**: O(1) average, O(n) worst case
- **Delete**: O(1) average, O(n) worst case
- **Membership test**: O(1) average, O(n) worst case
- **Set operations**: O(min(len(s), len(t))) for intersection

**Memory Overhead:**
- Each set object: ~200 bytes (Python 3.8+)
- Each element: ~8 bytes (64-bit system)
- Hash table overhead: ~8 bytes per slot

```python
# Memory overhead calculation
def calculate_set_overhead(n):
    s = set(range(n))
    total_size = sys.getsizeof(s)
    element_size = 8  # 8 bytes per element
    overhead = total_size - (element_size * n)
    return overhead

print(f"Overhead for 1000 elements: {calculate_set_overhead(1000)} bytes")
```

**Set Operations Performance:**
- **Union**: O(len(s) + len(t))
- **Intersection**: O(min(len(s), len(t)))
- **Difference**: O(len(s))
- **Symmetric difference**: O(len(s) + len(t))

```python
# Performance comparison
import timeit

def create_set(n):
    return set(range(n))

def create_list(n):
    return list(range(n))

# Time creation
n = 1000
set_time = timeit.timeit(lambda: create_set(n), number=1000)
list_time = timeit.timeit(lambda: create_list(n), number=1000)

print(f"Set creation: {set_time:.4f}s")
print(f"List creation: {list_time:.4f}s")

# Membership test performance
test_set = set(range(1000))
test_list = list(range(1000))

set_membership = timeit.timeit(lambda: 500 in test_set, number=10000)
list_membership = timeit.timeit(lambda: 500 in test_list, number=10000)

print(f"Set membership: {set_membership:.4f}s")
print(f"List membership: {list_membership:.4f}s")
```

**Optimization Tips:**
1. **Use sets** for membership testing
2. **Use sets** to remove duplicates
3. **Use sets** for mathematical operations
4. **Consider `frozenset`** for immutable sets
5. **Use set comprehensions** for better performance

</details>

---

## ⚡ Functions

### Function Definition
```python
# Basic function
def greet(name):
    return f"Hello, {name}!"

# Function with default parameters
def greet_with_title(name, title="Mr."):
    return f"Hello, {title} {name}!"

# Function with multiple parameters
def add_numbers(a, b, c=0):
    return a + b + c

# Function with *args (variable arguments)
def sum_all(*args):
    return sum(args)

# Function with **kwargs (keyword arguments)
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

# Function with both *args and **kwargs
def flexible_function(*args, **kwargs):
    print("Positional arguments:", args)
    print("Keyword arguments:", kwargs)
```

### Methods vs Functions - In-Depth

**Functions** are standalone blocks of code that can be called independently:

```python
# Function - standalone
def calculate_area(length, width):
    return length * width

# Can be called directly
area = calculate_area(5, 3)  # 15
```

**Methods** are functions that belong to a class and are called on instances:

```python
class Rectangle:
    def __init__(self, length, width):
        self.length = length
        self.width = width
    
    # Method - belongs to class
    def calculate_area(self):
        return self.length * self.width
    
    # Method with parameters
    def scale(self, factor):
        self.length *= factor
        self.width *= factor

# Methods are called on instances
rect = Rectangle(5, 3)
area = rect.calculate_area()  # Method call
rect.scale(2)  # Method call
```

**Key Differences:**

| Aspect | Functions | Methods |
|--------|-----------|---------|
| **Definition** | `def func_name():` | `def method_name(self):` |
| **Calling** | `func_name()` | `instance.method_name()` |
| **Context** | Standalone | Belongs to class |
| **Self Parameter** | No | Yes (for instance methods) |
| **Access to Data** | Through parameters | Through `self` |
| **Inheritance** | Not applicable | Can be overridden |

**Types of Methods:**

```python
class MyClass:
    class_var = "I'm a class variable"
    
    def __init__(self, value):
        self.instance_var = value
    
    # Instance method - most common
    def instance_method(self):
        return f"Instance: {self.instance_var}"
    
    # Class method - works with class
    @classmethod
    def class_method(cls):
        return f"Class: {cls.class_var}"
    
    # Static method - utility function
    @staticmethod
    def static_method(x, y):
        return x + y

# Usage
obj = MyClass("test")

# Instance method
print(obj.instance_method())  # Instance: test

# Class method
print(MyClass.class_method())  # Class: I'm a class variable
print(obj.class_method())      # Same result

# Static method
print(MyClass.static_method(5, 3))  # 8
print(obj.static_method(5, 3))      # 8
```

### Lambda Functions
```python
# Basic lambda
square = lambda x: x ** 2
print(square(5))  # 25

# Lambda with multiple parameters
add = lambda x, y: x + y
print(add(3, 4))  # 7

# Lambda in higher-order functions
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))  # [1, 4, 9, 16, 25]
evens = list(filter(lambda x: x % 2 == 0, numbers))  # [2, 4]

# Lambda with conditional
max_value = lambda x, y: x if x > y else y
print(max_value(10, 20))  # 20
```

### Why Use Lambda Functions?
Lambda functions are **anonymous functions** that are useful for:

1. **Short, Simple Operations**: Perfect for one-liner functions
2. **Higher-Order Functions**: Used with `map()`, `filter()`, `reduce()`
3. **Functional Programming**: Enables functional programming style
4. **Inline Functions**: No need to define separate functions

```python
# Lambda vs Regular Function
# Lambda (concise)
squares = list(map(lambda x: x**2, range(10)))

# Regular function (more verbose)
def square(x):
    return x**2
squares = list(map(square, range(10)))

# When NOT to use lambda
# Complex logic - use regular function instead
def complex_calculation(x, y, z):
    if x > 0:
        result = (x * y) + z
        return result ** 2
    else:
        return abs(x) + y + z

# Lambda limitations
# Can't have multiple statements
# Can't have assignments
# Can't have return statements (implicit)
```

### Lambda vs Regular Functions

| Feature | Lambda | Regular Function |
|---------|--------|------------------|
| **Syntax** | `lambda x: x**2` | `def square(x): return x**2` |
| **Name** | Anonymous | Named |
| **Statements** | Single expression only | Multiple statements |
| **Return** | Implicit | Explicit |
| **Documentation** | No docstring | Can have docstring |
| **Complexity** | Simple operations only | Any complexity |
| **Reusability** | Limited | Highly reusable |

### Function Scope and Closures
```python
# Global and local scope
global_var = "I'm global"

def my_function():
    local_var = "I'm local"
    print(global_var)  # Can access global
    print(local_var)   # Can access local

# Modifying global variables
counter = 0

def increment():
    global counter
    counter += 1

# Closures
def outer_function(x):
    def inner_function(y):
        return x + y
    return inner_function

add_five = outer_function(5)
print(add_five(3))  # 8
```

### Decorators
```python
# Basic decorator
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print("Before function call")
        result = func(*args, **kwargs)
        print("After function call")
        return result
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

# Decorator with parameters
def repeat(times):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello, {name}!")
```

### Generators
```python
# Generator function
def count_up_to(max_count):
    count = 1
    while count <= max_count:
        yield count
        count += 1

# Using generator
counter = count_up_to(5)
for num in counter:
    print(num)  # 1, 2, 3, 4, 5

# Generator expression
squares = (x**2 for x in range(10))
print(list(squares))  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

### Built-in Functions for Functions
```python
# map() - Apply function to all items
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))  # [1, 4, 9, 16, 25]

# filter() - Filter items based on condition
evens = list(filter(lambda x: x % 2 == 0, numbers))  # [2, 4]

# reduce() - Reduce sequence to single value
from functools import reduce
sum_all = reduce(lambda x, y: x + y, numbers)  # 15

# zip() - Combine multiple iterables
names = ['Alice', 'Bob', 'Charlie']
ages = [25, 30, 35]
combined = list(zip(names, ages))  # [('Alice', 25), ('Bob', 30), ('Charlie', 35)]

# enumerate() - Get index and value
for i, name in enumerate(names):
    print(f"{i}: {name}")  # 0: Alice, 1: Bob, 2: Charlie
```


---

## 🏗️ Classes & OOP

### Class Definition
```python
class Employee:
    """Common base class for all employees"""
    emp_count = 0  # Class variable
    
    def __init__(self, name, salary):
        self.name = name      # Instance variable
        self.salary = salary  # Instance variable
        Employee.emp_count += 1
    
    def display_count(self):
        print(f"Total Employee {Employee.emp_count}")
    
    def display_employee(self):
        print(f"Name: {self.name}, Salary: {self.salary}")

# Creating instances
emp1 = Employee("Zara", 2000)
emp2 = Employee("Manni", 5000)
```

### Class Attributes and Methods
```python
class Person:
    species = "Homo sapiens"  # Class attribute
    
    def __init__(self, name, age):
        self.name = name      # Instance attribute
        self.age = age        # Instance attribute
    
    def greet(self):          # Instance method
        return f"Hello, I'm {self.name}"
    
    @classmethod
    def get_species(cls):     # Class method
        return cls.species
    
    @staticmethod
    def is_adult(age):        # Static method
        return age >= 18

# Using the class
person = Person("Alice", 25)
print(person.greet())         # "Hello, I'm Alice"
print(Person.get_species())   # "Homo sapiens"
print(Person.is_adult(25))    # True
```

### Class Methods vs Static Methods - In-Depth

**Class Methods (`@classmethod`):**
- First parameter is `cls` (the class itself)
- Can access class attributes and methods
- Can create new instances of the class
- Inherited by subclasses

```python
class Date:
    def __init__(self, year, month, day):
        self.year = year
        self.month = month
        self.day = day
    
    @classmethod
    def from_string(cls, date_string):
        """Create Date from string like '2023-12-25'"""
        year, month, day = map(int, date_string.split('-'))
        return cls(year, month, day)
    
    @classmethod
    def today(cls):
        """Create Date for today"""
        import datetime
        today = datetime.date.today()
        return cls(today.year, today.month, today.day)

# Usage
date1 = Date.from_string("2023-12-25")
date2 = Date.today()
```

**Static Methods (`@staticmethod`):**
- No special first parameter
- Cannot access class or instance attributes
- Like a regular function but belongs to the class
- Useful for utility functions related to the class

```python
class MathUtils:
    @staticmethod
    def add(x, y):
        return x + y
    
    @staticmethod
    def is_even(number):
        return number % 2 == 0
    
    @staticmethod
    def factorial(n):
        if n <= 1:
            return 1
        return n * MathUtils.factorial(n - 1)

# Usage
result = MathUtils.add(5, 3)  # 8
print(MathUtils.is_even(4))   # True
print(MathUtils.factorial(5)) # 120
```

**When to Use Each:**

| Use Case | Method Type | Example |
|----------|-------------|---------|
| **Access instance data** | Instance method | `person.get_age()` |
| **Access class data** | Class method | `Person.get_species()` |
| **Create alternative constructors** | Class method | `Date.from_string()` |
| **Utility functions** | Static method | `MathUtils.add()` |
| **Functions that don't need class/instance** | Static method | `StringUtils.is_valid_email()` |

### Inheritance
```python
# Parent class
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        return "Some generic animal sound"

# Child class
class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)  # Call parent constructor
        self.breed = breed
    
    def speak(self):  # Method overriding
        return "Woof!"

# Multiple inheritance
class Bird(Animal):
    def speak(self):
        return "Tweet!"

class FlyingDog(Dog, Bird):  # Multiple inheritance
    def speak(self):
        return "Flying woof!"

# Using inheritance
dog = Dog("Buddy", "Golden Retriever")
print(dog.speak())  # "Woof!"
print(dog.name)     # "Buddy"
```

### Special Methods (Magic Methods)
```python
class Vector:
    def __init__(self, a, b):
        self.a = a
        self.b = b
    
    def __str__(self):  # String representation
        return f'Vector ({self.a}, {self.b})'
    
    def __repr__(self):  # Developer representation
        return f'Vector({self.a}, {self.b})'
    
    def __add__(self, other):  # Addition operator
        return Vector(self.a + other.a, self.b + other.b)
    
    def __eq__(self, other):  # Equality operator
        return self.a == other.a and self.b == other.b
    
    def __len__(self):  # Length
        return 2

# Using special methods
v1 = Vector(2, 10)
v2 = Vector(5, -2)
print(v1 + v2)  # Vector (7, 8)
print(v1 == v2)  # False
print(len(v1))   # 2
```

### Property Decorators
```python
class Circle:
    def __init__(self, radius):
        self._radius = radius
    
    @property
    def radius(self):
        return self._radius
    
    @radius.setter
    def radius(self, value):
        if value < 0:
            raise ValueError("Radius cannot be negative")
        self._radius = value
    
    @property
    def area(self):
        return 3.14159 * self._radius ** 2

# Using properties
circle = Circle(5)
print(circle.radius)  # 5
print(circle.area)    # 78.53975
circle.radius = 10
print(circle.area)    # 314.159
```

### Data Hiding and Encapsulation
```python
class BankAccount:
    def __init__(self, initial_balance):
        self.__balance = initial_balance  # Private attribute
    
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
    
    def withdraw(self, amount):
        if 0 < amount <= self.__balance:
            self.__balance -= amount
            return True
        return False
    
    def get_balance(self):
        return self.__balance

# Using encapsulation
account = BankAccount(1000)
account.deposit(500)
print(account.get_balance())  # 1500
# account.__balance  # This would raise an AttributeError
```

### Built-in Class Functions
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

person = Person("Alice", 30)

# Built-in functions
hasattr(person, 'name')        # True
getattr(person, 'name')        # 'Alice'
setattr(person, 'name', 'Bob') # Sets name to 'Bob'
delattr(person, 'age')         # Deletes age attribute

# Built-in class attributes
print(Person.__doc__)          # Class documentation
print(Person.__name__)         # 'Person'
print(Person.__module__)       # '__main__'
print(Person.__bases__)        # (<class 'object'>,)
print(Person.__dict__)         # Class dictionary
```

### Abstract Base Classes
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass
    
    @abstractmethod
    def perimeter(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height
    
    def perimeter(self):
        return 2 * (self.width + self.height)

# Using abstract classes
rect = Rectangle(5, 3)
print(rect.area())      # 15
print(rect.perimeter()) # 16
```



---

## 📁 File Operations

### File Reading and Writing
```python
# Writing to a file
with open("example.txt", "w") as file:
    file.write("Hello, World!\n")
    file.write("This is a test file.\n")

# Reading from a file
with open("example.txt", "r") as file:
    content = file.read()
    print(content)

# Reading line by line
with open("example.txt", "r") as file:
    for line in file:
        print(line.strip())

# Reading all lines into a list
with open("example.txt", "r") as file:
    lines = file.readlines()
    print(lines)
```

### File Modes
```python
# File modes
"r"   # Read (default)
"w"   # Write (overwrites existing file)
"a"   # Append
"x"   # Create (fails if file exists)
"b"   # Binary mode
"t"   # Text mode (default)
"+"   # Read and write

# Examples
open("file.txt", "r")    # Read text file
open("file.txt", "w")    # Write text file
open("file.txt", "a")    # Append to text file
open("file.bin", "rb")   # Read binary file
open("file.bin", "wb")   # Write binary file
```

### File Operations
```python
import os

# File information
file_path = "example.txt"
print(os.path.exists(file_path))    # True if file exists
print(os.path.getsize(file_path))   # File size in bytes
print(os.path.isfile(file_path))    # True if it's a file
print(os.path.isdir(file_path))     # True if it's a directory

# File operations
os.rename("old_name.txt", "new_name.txt")  # Rename file
os.remove("file_to_delete.txt")            # Delete file
os.mkdir("new_directory")                  # Create directory
os.rmdir("empty_directory")                # Remove empty directory
os.getcwd()                                # Get current working directory
os.chdir("/path/to/directory")             # Change directory
```

### Context Managers
```python
# Using with statement (recommended)
with open("example.txt", "r") as file:
    content = file.read()
# File is automatically closed here

# Manual file handling (not recommended)
file = open("example.txt", "r")
try:
    content = file.read()
finally:
    file.close()  # Must close manually
```

---

## 🚨 Exception Handling

### Basic Exception Handling
```python
# Try-except block
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Multiple exceptions
try:
    value = int("not_a_number")
    result = 10 / value
except ValueError:
    print("Invalid number!")
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Catch all exceptions
try:
    risky_operation()
except Exception as e:
    print(f"An error occurred: {e}")
```

### Exception Types
```python
# Common built-in exceptions
try:
    # ZeroDivisionError
    result = 10 / 0
except ZeroDivisionError:
    print("Division by zero")

try:
    # ValueError
    int("not_a_number")
except ValueError:
    print("Invalid value")

try:
    # TypeError
    "string" + 5
except TypeError:
    print("Type error")

try:
    # IndexError
    my_list = [1, 2, 3]
    print(my_list[10])
except IndexError:
    print("Index out of range")

try:
    # KeyError
    my_dict = {"a": 1}
    print(my_dict["b"])
except KeyError:
    print("Key not found")

try:
    # FileNotFoundError
    with open("nonexistent.txt", "r") as file:
        content = file.read()
except FileNotFoundError:
    print("File not found")
```

### Try-Except-Else-Finally
```python
def divide_numbers(a, b):
    try:
        result = a / b
    except ZeroDivisionError:
        print("Cannot divide by zero!")
        return None
    except TypeError:
        print("Invalid input types!")
        return None
    else:
        print("Division successful!")
        return result
    finally:
        print("This always executes!")

# Using the function
result = divide_numbers(10, 2)   # 5.0
result = divide_numbers(10, 0)   # None
```

### Custom Exceptions
```python
class CustomError(Exception):
    """Custom exception class"""
    pass

class ValidationError(Exception):
    """Validation error with message"""
    def __init__(self, message):
        self.message = message
        super().__init__(self.message)

def validate_age(age):
    if age < 0:
        raise ValidationError("Age cannot be negative")
    if age > 150:
        raise ValidationError("Age cannot be greater than 150")
    return True

# Using custom exceptions
try:
    validate_age(-5)
except ValidationError as e:
    print(f"Validation error: {e.message}")
```

### Raising Exceptions
```python
def check_positive(number):
    if number < 0:
        raise ValueError("Number must be positive")
    return number

# Using raise
try:
    check_positive(-5)
except ValueError as e:
    print(f"Error: {e}")

# Re-raising exceptions
def process_data(data):
    try:
        # Some processing
        result = data / 0
    except ZeroDivisionError:
        print("Error in processing")
        raise  # Re-raise the exception
```

---

## 📦 Modules and Imports

### Importing Modules
```python
# Import entire module
import math
print(math.pi)  # 3.141592653589793

# Import specific functions
from math import pi, sqrt
print(pi)       # 3.141592653589793
print(sqrt(16)) # 4.0

# Import with alias
import numpy as np
import pandas as pd

# Import all (not recommended)
from math import *

# Import with custom name
from math import pi as PI
print(PI)  # 3.141592653589793
```

### Creating Modules
```python
# mymodule.py
def greet(name):
    return f"Hello, {name}!"

def add(a, b):
    return a + b

class Calculator:
    def multiply(self, a, b):
        return a * b

# Using the module
import mymodule
print(mymodule.greet("Alice"))  # Hello, Alice!

from mymodule import Calculator
calc = Calculator()
print(calc.multiply(3, 4))  # 12
```

### Module Search Path
```python
import sys
print(sys.path)  # List of directories Python searches for modules

# Adding to path
sys.path.append("/path/to/your/modules")

# PYTHONPATH environment variable
# Windows: set PYTHONPATH=c:\python34\lib;
# Unix/Linux: export PYTHONPATH=/usr/local/lib/python
```

### Built-in Module Functions
```python
import mymodule

# Module information
print(dir(mymodule))           # List all names in module
print(mymodule.__name__)       # Module name
print(mymodule.__file__)       # Module file path
print(mymodule.__doc__)        # Module documentation

# Namespace functions
print(globals())               # Global namespace
print(locals())                # Local namespace

# Reloading modules (Python 2 only)
# reload(mymodule)  # Not available in Python 3
```

---

## 🚀 Advanced Topics

### List Comprehensions
```python
# Basic list comprehension
squares = [x**2 for x in range(10)]  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# With condition
evens = [x for x in range(20) if x % 2 == 0]  # [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# Nested list comprehension
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [item for row in matrix for item in row]  # [1, 2, 3, 4, 5, 6, 7, 8, 9]

# Dictionary comprehension
squares_dict = {x: x**2 for x in range(5)}  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# Set comprehension
unique_lengths = {len(word) for word in ["hello", "world", "python"]}  # {5, 6}
```

### Generators and Iterators
```python
# Generator function
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

# Using generator
fib_gen = fibonacci(10)
for num in fib_gen:
    print(num)  # 0, 1, 1, 2, 3, 5, 8, 13, 21, 34

# Generator expression
squares_gen = (x**2 for x in range(10))
print(list(squares_gen))  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# Iterator protocol
class CountDown:
    def __init__(self, start):
        self.start = start
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.start <= 0:
            raise StopIteration
        self.start -= 1
        return self.start + 1

# Using custom iterator
countdown = CountDown(5)
for num in countdown:
    print(num)  # 5, 4, 3, 2, 1
```

### Custom Iterators - In-Depth

**Creating Custom Iterators:**

```python
# Method 1: Using __iter__ and __next__
class NumberRange:
    def __init__(self, start, end, step=1):
        self.start = start
        self.end = end
        self.step = step
        self.current = start
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.current >= self.end:
            raise StopIteration
        value = self.current
        self.current += self.step
        return value

# Usage
for num in NumberRange(1, 10, 2):
    print(num)  # 1, 3, 5, 7, 9

# Method 2: Using generator function
def number_range(start, end, step=1):
    current = start
    while current < end:
        yield current
        current += step

# Usage
for num in number_range(1, 10, 2):
    print(num)  # 1, 3, 5, 7, 9

# Method 3: Using generator expression
numbers = (x for x in range(1, 10, 2))
for num in numbers:
    print(num)  # 1, 3, 5, 7, 9
```

**Advanced Iterator Examples:**

```python
# File line iterator
class FileLineIterator:
    def __init__(self, filename):
        self.filename = filename
        self.file = None
    
    def __iter__(self):
        self.file = open(self.filename, 'r')
        return self
    
    def __next__(self):
        line = self.file.readline()
        if not line:
            self.file.close()
            raise StopIteration
        return line.strip()

# Usage
for line in FileLineIterator('data.txt'):
    print(line)

# Infinite iterator
class InfiniteCounter:
    def __init__(self, start=0, step=1):
        self.current = start
        self.step = step
    
    def __iter__(self):
        return self
    
    def __next__(self):
        value = self.current
        self.current += self.step
        return value

# Usage (be careful with infinite iterators!)
counter = InfiniteCounter(0, 2)
for i, num in enumerate(counter):
    if i >= 5:  # Limit to 5 iterations
        break
    print(num)  # 0, 2, 4, 6, 8
```

**Iterator vs Generator:**

| Feature | Iterator | Generator |
|---------|----------|-----------|
| **Definition** | Class with `__iter__` and `__next__` | Function with `yield` |
| **Memory** | Can store state | Minimal memory usage |
| **Complexity** | More complex | Simpler |
| **State Management** | Manual | Automatic |
| **Performance** | Good | Excellent |
| **Use Case** | Complex iteration logic | Simple iteration |

### Context Managers
```python
# Custom context manager
class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None
    
    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()

# Using custom context manager
with FileManager("test.txt", "w") as f:
    f.write("Hello, World!")

# Using contextlib
from contextlib import contextmanager

@contextmanager
def file_manager(filename, mode):
    file = open(filename, mode)
    try:
        yield file
    finally:
        file.close()

# Using the context manager
with file_manager("test.txt", "r") as f:
    content = f.read()
```

### Decorators
```python
# Function decorator
def timer(func):
    import time
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(1)
    return "Done"

# Class decorator
def singleton(cls):
    instances = {}
    def get_instance(*args, **kwargs):
        if cls not in instances:
            instances[cls] = cls(*args, **kwargs)
        return instances[cls]
    return get_instance

@singleton
class Database:
    def __init__(self):
        print("Database initialized")

# Using the singleton
db1 = Database()  # Database initialized
db2 = Database()  # No output (same instance)
print(db1 is db2)  # True
```

### Metaclasses
```python
# Custom metaclass
class SingletonMeta(type):
    _instances = {}
    
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super().__call__(*args, **kwargs)
        return cls._instances[cls]

class Singleton(metaclass=SingletonMeta):
    def __init__(self, value):
        self.value = value

# Using metaclass
s1 = Singleton("first")
s2 = Singleton("second")
print(s1 is s2)  # True
print(s1.value)  # first
```

### Regular Expressions
```python
import re

# Basic pattern matching
text = "The quick brown fox jumps over the lazy dog"
pattern = r"fox"
match = re.search(pattern, text)
if match:
    print(f"Found: {match.group()}")  # Found: fox

# Finding all matches
pattern = r"\b\w{4}\b"  # 4-letter words
matches = re.findall(pattern, text)
print(matches)  # ['quick', 'brown', 'jumps', 'over', 'lazy']

# Substitution
new_text = re.sub(r"fox", "cat", text)
print(new_text)  # The quick brown cat jumps over the lazy dog

# Compiling patterns for reuse
pattern = re.compile(r"\b\w{5}\b")  # 5-letter words
matches = pattern.findall(text)
print(matches)  # ['quick', 'brown', 'jumps']
```

### Threading
```python
import threading
import time

# Basic threading
def worker(name, delay):
    for i in range(3):
        time.sleep(delay)
        print(f"Worker {name}: {i}")

# Create threads
thread1 = threading.Thread(target=worker, args=("A", 1))
thread2 = threading.Thread(target=worker, args=("B", 2))

# Start threads
thread1.start()
thread2.start()

# Wait for threads to complete
thread1.join()
thread2.join()

# Thread-safe operations
import queue
q = queue.Queue()

def producer():
    for i in range(5):
        q.put(i)
        time.sleep(0.1)

def consumer():
    while True:
        item = q.get()
        if item is None:
            break
        print(f"Consumed: {item}")
        q.task_done()

# Using thread-safe queue
producer_thread = threading.Thread(target=producer)
consumer_thread = threading.Thread(target=consumer)

producer_thread.start()
consumer_thread.start()

producer_thread.join()
q.put(None)  # Signal consumer to stop
consumer_thread.join()
```

### Networking
```python
import socket

# Simple server
def start_server():
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind(('localhost', 9999))
    server_socket.listen(5)
    
    print("Server listening on port 9999...")
    
    while True:
        client_socket, addr = server_socket.accept()
        print(f"Connection from {addr}")
        
        message = "Hello, Client!"
        client_socket.send(message.encode('ascii'))
        client_socket.close()

# Simple client
def start_client():
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect(('localhost', 9999))
    
    message = client_socket.recv(1024)
    print(f"Received: {message.decode('ascii')}")
    
    client_socket.close()
```

---

## 📚 Additional Resources

### Useful Built-in Modules
```python
# Collections
from collections import Counter, defaultdict, namedtuple

# Counter
counter = Counter(['a', 'b', 'a', 'c', 'b', 'a'])
print(counter)  # Counter({'a': 3, 'b': 2, 'c': 1})

# Defaultdict
dd = defaultdict(list)
dd['key'].append('value')  # No KeyError

# Namedtuple
Point = namedtuple('Point', ['x', 'y'])
p = Point(1, 2)
print(p.x, p.y)  # 1 2

# Datetime
from datetime import datetime, timedelta
now = datetime.now()
tomorrow = now + timedelta(days=1)

# JSON
import json
data = {'name': 'Alice', 'age': 30}
json_str = json.dumps(data)
parsed_data = json.loads(json_str)

# Random
import random
random_number = random.randint(1, 10)
random_choice = random.choice(['a', 'b', 'c'])

# Math
import math
print(math.sqrt(16))  # 4.0
print(math.pi)        # 3.141592653589793
```

### Best Practices
1. **PEP 8**: Follow Python style guide
2. **Docstrings**: Document your functions and classes
3. **Type hints**: Use type annotations (Python 3.5+)
4. **Virtual environments**: Use venv or conda
5. **Testing**: Write unit tests with unittest or pytest
6. **Error handling**: Use specific exceptions
7. **Performance**: Profile your code when needed
8. **Security**: Be careful with eval() and exec()

### Python Version Features
- **Python 3.8+**: Walrus operator (`:=`), positional-only parameters
- **Python 3.9+**: Dictionary merge operators (`|`, `|=`)
- **Python 3.10+**: Structural pattern matching (`match`/`case`)
- **Python 3.11+**: Exception groups, tomllib module

---

## 🎯 Conclusion

This cheat sheet covers the essential Python concepts and syntax. Remember:

- **Practice regularly** to reinforce your learning
- **Read other people's code** to learn best practices
- **Build projects** to apply your knowledge
- **Stay updated** with Python releases and new features
- **Use the Python documentation** as your reference

Happy coding! 🐍✨

---

## 🚨 Exception Handling

### Basic Exception Handling
```python
# Try-except block
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Multiple exceptions
try:
    value = int("not_a_number")
    result = 10 / value
except ValueError:
    print("Invalid number!")
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Catch all exceptions
try:
    risky_operation()
except Exception as e:
    print(f"An error occurred: {e}")
```

### Exception Types
```python
# Common built-in exceptions
try:
    # ZeroDivisionError
    result = 10 / 0
except ZeroDivisionError:
    print("Division by zero")

try:
    # ValueError
    int("not_a_number")
except ValueError:
    print("Invalid value")

try:
    # TypeError
    "string" + 5
except TypeError:
    print("Type error")

try:
    # IndexError
    my_list = [1, 2, 3]
    print(my_list[10])
except IndexError:
    print("Index out of range")

try:
    # KeyError
    my_dict = {"a": 1}
    print(my_dict["b"])
except KeyError:
    print("Key not found")

try:
    # FileNotFoundError
    with open("nonexistent.txt", "r") as file:
        content = file.read()
except FileNotFoundError:
    print("File not found")
```

### Try-Except-Else-Finally
```python
def divide_numbers(a, b):
    try:
        result = a / b
    except ZeroDivisionError:
        print("Cannot divide by zero!")
        return None
    except TypeError:
        print("Invalid input types!")
        return None
    else:
        print("Division successful!")
        return result
    finally:
        print("This always executes!")

# Using the function
result = divide_numbers(10, 2)   # 5.0
result = divide_numbers(10, 0)   # None
```

### Custom Exceptions
```python
class CustomError(Exception):
    """Custom exception class"""
    pass

class ValidationError(Exception):
    """Validation error with message"""
    def __init__(self, message):
        self.message = message
        super().__init__(self.message)

def validate_age(age):
    if age < 0:
        raise ValidationError("Age cannot be negative")
    if age > 150:
        raise ValidationError("Age cannot be greater than 150")
    return True

# Using custom exceptions
try:
    validate_age(-5)
except ValidationError as e:
    print(f"Validation error: {e.message}")
```

### Raising Exceptions
```python
def check_positive(number):
    if number < 0:
        raise ValueError("Number must be positive")
    return number

# Using raise
try:
    check_positive(-5)
except ValueError as e:
    print(f"Error: {e}")

# Re-raising exceptions
def process_data(data):
    try:
        # Some processing
        result = data / 0
    except ZeroDivisionError:
        print("Error in processing")
        raise  # Re-raise the exception
```

---

## 📦 Modules and Imports

### Importing Modules
```python
# Import entire module
import math
print(math.pi)  # 3.141592653589793

# Import specific functions
from math import pi, sqrt
print(pi)       # 3.141592653589793
print(sqrt(16)) # 4.0

# Import with alias
import numpy as np
import pandas as pd

# Import all (not recommended)
from math import *

# Import with custom name
from math import pi as PI
print(PI)  # 3.141592653589793
```

### Creating Modules
```python
# mymodule.py
def greet(name):
    return f"Hello, {name}!"

def add(a, b):
    return a + b

class Calculator:
    def multiply(self, a, b):
        return a * b

# Using the module
import mymodule
print(mymodule.greet("Alice"))  # Hello, Alice!

from mymodule import Calculator
calc = Calculator()
print(calc.multiply(3, 4))  # 12
```

### Module Search Path
```python
import sys
print(sys.path)  # List of directories Python searches for modules

# Adding to path
sys.path.append("/path/to/your/modules")

# PYTHONPATH environment variable
# Windows: set PYTHONPATH=c:\python34\lib;
# Unix/Linux: export PYTHONPATH=/usr/local/lib/python
```

### Built-in Module Functions
```python
import mymodule

# Module information
print(dir(mymodule))           # List all names in module
print(mymodule.__name__)       # Module name
print(mymodule.__file__)       # Module file path
print(mymodule.__doc__)        # Module documentation

# Namespace functions
print(globals())               # Global namespace
print(locals())                # Local namespace

# Reloading modules (Python 2 only)
# reload(mymodule)  # Not available in Python 3
```

---

## 📁 File Operations

### File Reading and Writing
```python
# Writing to a file
with open("example.txt", "w") as file:
    file.write("Hello, World!\n")
    file.write("This is a test file.\n")

# Reading from a file
with open("example.txt", "r") as file:
    content = file.read()
    print(content)

# Reading line by line
with open("example.txt", "r") as file:
    for line in file:
        print(line.strip())

# Reading all lines into a list
with open("example.txt", "r") as file:
    lines = file.readlines()
    print(lines)
```

### File Modes
```python
# File modes
"r"   # Read (default)
"w"   # Write (overwrites existing file)
"a"   # Append
"x"   # Create (fails if file exists)
"b"   # Binary mode
"t"   # Text mode (default)
"+"   # Read and write

# Examples
open("file.txt", "r")    # Read text file
open("file.txt", "w")    # Write text file
open("file.txt", "a")    # Append to text file
open("file.bin", "rb")   # Read binary file
open("file.bin", "wb")   # Write binary file
```

### File Operations
```python
import os

# File information
file_path = "example.txt"
print(os.path.exists(file_path))    # True if file exists
print(os.path.getsize(file_path))   # File size in bytes
print(os.path.isfile(file_path))    # True if it's a file
print(os.path.isdir(file_path))     # True if it's a directory

# File operations
os.rename("old_name.txt", "new_name.txt")  # Rename file
os.remove("file_to_delete.txt")            # Delete file
os.mkdir("new_directory")                  # Create directory
os.rmdir("empty_directory")                # Remove empty directory
os.getcwd()                                # Get current working directory
os.chdir("/path/to/directory")             # Change directory
```

### Context Managers
```python
# Using with statement (recommended)
with open("example.txt", "r") as file:
    content = file.read()
# File is automatically closed here

# Manual file handling (not recommended)
file = open("example.txt", "r")
try:
    content = file.read()
finally:
    file.close()  # Must close manually
```

---

## 🧵 Threading and Concurrency

### Basic Threading
```python
import threading
import time

# Basic threading
def worker(name, delay):
    for i in range(3):
        time.sleep(delay)
        print(f"Worker {name}: {i}")

# Create threads
thread1 = threading.Thread(target=worker, args=("A", 1))
thread2 = threading.Thread(target=worker, args=("B", 2))

# Start threads
thread1.start()
thread2.start()

# Wait for threads to complete
thread1.join()
thread2.join()
```

### Thread-Safe Operations
```python
import queue
import threading

# Thread-safe queue
q = queue.Queue()

def producer():
    for i in range(5):
        q.put(i)
        time.sleep(0.1)

def consumer():
    while True:
        item = q.get()
        if item is None:
            break
        print(f"Consumed: {item}")
        q.task_done()

# Using thread-safe queue
producer_thread = threading.Thread(target=producer)
consumer_thread = threading.Thread(target=consumer)

producer_thread.start()
consumer_thread.start()

producer_thread.join()
q.put(None)  # Signal consumer to stop
consumer_thread.join()
```

### Thread Synchronization
```python
import threading

# Lock for synchronization
lock = threading.Lock()
shared_data = 0

def increment():
    global shared_data
    with lock:
        shared_data += 1

# Create multiple threads
threads = []
for i in range(10):
    t = threading.Thread(target=increment)
    threads.append(t)
    t.start()

# Wait for all threads
for t in threads:
    t.join()

print(f"Final value: {shared_data}")  # Should be 10
```

---

## 🌐 Networking

### Simple Server
```python
import socket

def start_server():
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind(('localhost', 9999))
    server_socket.listen(5)
    
    print("Server listening on port 9999...")
    
    while True:
        client_socket, addr = server_socket.accept()
        print(f"Connection from {addr}")
        
        message = "Hello, Client!"
        client_socket.send(message.encode('ascii'))
        client_socket.close()

# Usage
# start_server()
```

### Simple Client
```python
import socket

def start_client():
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect(('localhost', 9999))
    
    message = client_socket.recv(1024)
    print(f"Received: {message.decode('ascii')}")
    
    client_socket.close()

# Usage
# start_client()
```

---

## 🗄️ Database Operations

### SQLite Database
```python
import sqlite3

# Connect to database
conn = sqlite3.connect('example.db')
cursor = conn.cursor()

# Create table
cursor.execute('''
    CREATE TABLE IF NOT EXISTS users (
        id INTEGER PRIMARY KEY,
        name TEXT NOT NULL,
        email TEXT UNIQUE
    )
''')

# Insert data
cursor.execute("INSERT INTO users (name, email) VALUES (?, ?)", 
               ("Alice", "alice@example.com"))
conn.commit()

# Query data
cursor.execute("SELECT * FROM users")
rows = cursor.fetchall()
for row in rows:
    print(row)

# Close connection
conn.close()
```

### MySQL Database
```python
import pymysql

# Connect to MySQL database
db = pymysql.connect(
    host="localhost",
    user="username",
    password="password",
    database="testdb"
)

cursor = db.cursor()

# Execute query
cursor.execute("SELECT VERSION()")
data = cursor.fetchone()
print(f"Database version: {data[0]}")

# Close connection
db.close()
```

---

## 🔧 Regular Expressions

### Basic Pattern Matching
```python
import re

# Basic pattern matching
text = "The quick brown fox jumps over the lazy dog"
pattern = r"fox"
match = re.search(pattern, text)
if match:
    print(f"Found: {match.group()}")  # Found: fox

# Finding all matches
pattern = r"\b\w{4}\b"  # 4-letter words
matches = re.findall(pattern, text)
print(matches)  # ['quick', 'brown', 'jumps', 'over', 'lazy']

# Substitution
new_text = re.sub(r"fox", "cat", text)
print(new_text)  # The quick brown cat jumps over the lazy dog

# Compiling patterns for reuse
pattern = re.compile(r"\b\w{5}\b")  # 5-letter words
matches = pattern.findall(text)
print(matches)  # ['quick', 'brown', 'jumps']
```

### Common Regex Patterns
```python
import re

# Email validation
email_pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
email = "user@example.com"
if re.match(email_pattern, email):
    print("Valid email")

# Phone number validation
phone_pattern = r'^\+?1?[-.\s]?\(?[0-9]{3}\)?[-.\s]?[0-9]{3}[-.\s]?[0-9]{4}$'
phone = "+1-555-123-4567"
if re.match(phone_pattern, phone):
    print("Valid phone number")

# URL validation
url_pattern = r'^https?://(?:[-\w.])+(?:[:\d]+)?(?:/(?:[\w/_.])*(?:\?(?:[\w&=%.])*)?(?:#(?:[\w.])*)?)?$'
url = "https://www.example.com"
if re.match(url_pattern, url):
    print("Valid URL")
```

---

## 📊 Data Processing

### Working with JSON
```python
import json

# Python object to JSON
data = {
    "name": "Alice",
    "age": 30,
    "city": "New York",
    "hobbies": ["reading", "swimming"]
}

json_string = json.dumps(data, indent=2)
print(json_string)

# JSON to Python object
json_data = '{"name": "Bob", "age": 25}'
python_obj = json.loads(json_data)
print(python_obj)

# Working with JSON files
with open('data.json', 'w') as f:
    json.dump(data, f, indent=2)

with open('data.json', 'r') as f:
    loaded_data = json.load(f)
    print(loaded_data)
```

### Working with CSV
```python
import csv

# Writing CSV
data = [
    ['Name', 'Age', 'City'],
    ['Alice', 30, 'New York'],
    ['Bob', 25, 'Boston'],
    ['Charlie', 35, 'Chicago']
]

with open('data.csv', 'w', newline='') as f:
    writer = csv.writer(f)
    writer.writerows(data)

# Reading CSV
with open('data.csv', 'r') as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)

# Using DictReader
with open('data.csv', 'r') as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(f"{row['Name']} is {row['Age']} years old")
```

---

## 🎯 Conclusion

This comprehensive Python cheat sheet covers:

- **Fundamentals**: Variables, data types, control flow
- **Data Structures**: Lists, tuples, dictionaries, sets
- **Functions**: Regular functions, lambda, decorators, generators
- **Object-Oriented Programming**: Classes, inheritance, methods
- **Advanced Topics**: Iterators, context managers, metaclasses
- **File Operations**: Reading, writing, file management
- **Exception Handling**: Try-except, custom exceptions
- **Modules and Imports**: Creating and using modules
- **Concurrency**: Threading, synchronization
- **Networking**: Socket programming
- **Database Operations**: SQLite, MySQL
- **Regular Expressions**: Pattern matching
- **Data Processing**: JSON, CSV

### Key Takeaways:
1. **Practice regularly** to reinforce your learning
2. **Read other people's code** to learn best practices
3. **Build projects** to apply your knowledge
4. **Stay updated** with Python releases and new features
5. **Use the Python documentation** as your reference
6. **Understand the internals** for better performance optimization

### Next Steps:
- Explore Python frameworks (Django, Flask, FastAPI)
- Learn about testing (pytest, unittest)
- Study design patterns in Python
- Contribute to open-source Python projects
- Join Python communities and forums

Remember: Python is not just a language, it's a philosophy. Embrace the Zen of Python and write beautiful, readable code! 🐍✨
