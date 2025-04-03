# Python Notes

### Python Virtual Environment Guide

A **virtual environment** in Python is an isolated environment where dependencies can be installed separately from the system-wide Python packages.  

## **Commands for Creating and Using a Virtual Environment**  

### **Windows (Command Prompt / PowerShell)**
```sh
# Create a virtual environment
python -m venv myenv

# Activate the virtual environment (Command Prompt)
myenv\Scripts\activate

# Activate the virtual environment (PowerShell)
myenv\Scripts\Activate.ps1

# Deactivate the virtual environment
deactivate
```

### **Linux / macOS (Terminal)**
```sh
# Create a virtual environment
python3 -m venv myenv

# Activate the virtual environment
source myenv/bin/activate

# Deactivate the virtual environment
deactivate
```

### **Installing Packages Inside Virtual Environment**
```sh
pip install package_name  # Install a package
pip freeze > requirements.txt  # Save dependencies to a file
pip install -r requirements.txt  # Install dependencies from a file
```

## Syntax and Semantics


- syntax refers to the set of rules that defines the combination of symbols that are considered to be correctly structured programs in a language.

- Semantics refers to the menaing or the interpretation of the symbols,characters,and commends in a language.It is about what the code is supposed to do when it runs.


``` sh
## This is single line comment
'''
this is  a example of multiline comment in python

'''

```

1. Python is case sensitivity. name is different from Name
2. Line Continuation

``` python 

total=1+2+3+4+\
5+6

```

## Variables

Variable are fundamental elements in programming  used to store data that can be referenced and manipulated in a program.

Variable are created when you assign a value to them, and they do not need explicit declaration to reserve memory space.

The declaration happens automatically when you assign a value to a variable.

``` python

a=10 
```

#### Declaring and assigning Variable

``` python 

age=32
height=6.1
name="Krish"
```


## Naming conventions

1.Variable name should be descriptive


2. They must always start with a letter /underscore and contain letter,number and underscores within them


3. variable names are case sensitive.


Following Python's PEP 8 style guide ensures readability and maintainability. 

### **Variables & Function Names**
- Use **snake_case**: `my_variable`, `calculate_total`
- Use lowercase letters with underscores to improve readability.
- Use descriptive names that convey the purpose.

### **Class Names**
- Use **PascalCase**: `MyClass`, `DataProcessor`
- Each word starts with an uppercase letter without underscores.

### **Constants**
- Use **ALL_CAPS**: `MAX_SIZE`, `DEFAULT_TIMEOUT`
- Defined at the module level and should not be modified.

### **Modules & Packages**
- Use **lowercase with underscores**: `data_processing.py`, `utils.py`
- Package names should be short and lowercase: `my_package`

### **Method Names & Instance Variables**
- Use **snake_case**: `get_user_data`, `fetch_records`
- Private variables start with an underscore `_private_var`

### **Special Methods (Dunder Methods)**
- Use **double underscores** before and after: `__init__`, `__str__`

### **Avoiding Conflicts**
- Use a single trailing underscore to avoid conflicts with Python keywords: `class_`, `type_`



## Understanding variable types
1.Python is dynamically typed, type is determined at runtime.

## Type Checking and Conversion
``` python 
age=25
age_str=str(age) # convert the int to str
```

``` python 

name="Hello"
age=int(name) # error not possible ,string cannot be converted to int.
```

``` python

height=5.11
print(int(height)) # prints 5

print (float(int(height))) # prints 5.0
```

### Input from user

``` python

age=input("what is the age?") # user inputed values comes as string.converts it to int 

age=int(input("your age is?"))
```

### Basic Datatypes in python 

Data types are classification of data which tells the complier or interpreter how the programmer intends to use the data.

They determine the type of operations that can be performed on the data,the values that the data can take, and the amount of memory needed to store the data.


### **1. Integer (`int`)**
- Represents whole numbers (positive, negative, or zero) without a decimal point.
- In Python, `int` has arbitrary precision (no fixed size like in some other languages).

```python
x = 10
print(type(x))  # Output: <class 'int'>
```

✅ **Use integers when you need to work with whole numbers, like counting items.**

#### **Types of Integer Representations**
- **Binary (base-2):** `0b1010` (prefix `0b` or `0B` for binary numbers)
- **Octal (base-8):** `0o12` (prefix `0o` or `0O` for octal numbers)
- **Hexadecimal (base-16):** `0xA` (prefix `0x` or `0X` for hexadecimal numbers)

```python
binary_num = 0b1010
hex_num = 0xA
print(binary_num, hex_num)  # Output: 10 10
```

---

### **2. Floating-Point (`float`)**
- Represents real numbers with decimals.
- Equivalent to **double precision (64-bit) floating point** in other languages.

```python
y = 3.14
print(type(y))  # Output: <class 'float'>
```

✅ **Use floats when precision with decimal points is required, such as in measurements.**

#### **Special Float Values:**
- `float('inf')` → Positive infinity
- `float('-inf')` → Negative infinity
- `float('nan')` → Not a Number (NaN)

```python
print(float('inf'), float('-inf'), float('nan'))  # Output: inf -inf nan
```

---

### **3. String (`str`)**
- Represents text enclosed in single (`'`), double (`"`), or triple (`'''` `"""`) quotes.

```python
text = "Hello, Python!"
print(type(text))  # Output: <class 'str'>
```

✅ **Use strings when handling textual data, such as names, messages, or file paths.**

---

### **String Operations**
- **Concatenation:**
```python
new_string = text + " Welcome!"
print(new_string)  # Output: Hello, Python! Welcome!
```
- **Repetition:**
```python
repeated = "Hi! " * 3
print(repeated)  # Output: Hi! Hi! Hi! 
```
- **Accessing Characters:**
```python
print(text[1])  # Output: 'e'
```
- **Slicing:**
```python
print(text[0:5])  # Output: 'Hello'
```
- **Replacing a Substring:**
```python
print(text.replace("Python", "World"))  # Output: Hello, World!
```

✅ **Strings are immutable, meaning their contents cannot be changed after creation.**

---

### **4. Boolean (`bool`)**
- Represents `True` or `False` values.
- Internally, `True` is equivalent to `1` and `False` to `0`.

```python
flag = True
print(type(flag))  # Output: <class 'bool'>
```

✅ **Use booleans for conditions, logic checks, and decision-making in programs.**

```python
print(True + 2)  # Output: 3 (because True is treated as 1)
print(False * 10)  # Output: 0 (because False is treated as 0)
```



### Operators

Python provides various types of operators:

### **1. Arithmetic Operators**
```python
a = 10
b = 3
print(a + b)  # Addition: 13
print(a - b)  # Subtraction: 7
print(a * b)  # Multiplication: 30
print(a / b)  # Division: 3.3333
print(a % b)  # Modulus: 1
print(a ** b) # Exponentiation: 1000
print(a // b) # Floor Division: 3
```

### **2. Comparison (Relational) Operators**
```python
a, b = 10, 20
print(a == b)  # False
print(a != b)  # True
print(a > b)   # False
print(a < b)   # True
print(a >= b)  # False
print(a <= b)  # True
```

### **3. Logical Operators**
```python
x, y = True, False
print(x and y)  # False
print(x or y)   # True
print(not x)    # False
```

### **4. Bitwise Operators**
```python
a, b = 5, 3  # 5 = 101, 3 = 011
print(a & b)  # AND: 1 (001)
print(a | b)  # OR: 7 (111)
print(a ^ b)  # XOR: 6 (110)
print(~a)     # NOT: -6
print(a << 1) # Left Shift: 10
print(a >> 1) # Right Shift: 2
```

**Explanation of Left and Right Shift in Layman Terms:**
- **Left Shift (`<<`)**: Think of it like multiplying by 2. Each shift moves all bits to the left, doubling the number.
  ```python
  a = 5   # Binary: 101
  print(a << 1)  # Moves bits left → Binary: 1010 (Decimal: 10)
  ```
- **Right Shift (`>>`)**: Think of it like dividing by 2. Each shift moves all bits to the right, halving the number.

  
  ```python
  a = 5   # Binary: 101
  print(a >> 1)  # Moves bits right → Binary: 10 (Decimal: 2)
  ```



#### **Left Shift (`<<`)**
Think of it like multiplying by 2. Each shift moves all bits to the left, doubling the number.

```
Binary:  00000101  (5 in decimal)
Shift << 1
Result:  00001010  (10 in decimal)
```

```python
a = 5   # Binary: 101
print(a << 1)  # Moves bits left → Binary: 1010 (Decimal: 10)
```

#### **Right Shift (`>>`)**
Think of it like dividing by 2. Each shift moves all bits to the right, halving the number.

```
Binary:  00000101  (5 in decimal)
Shift >> 1
Result:  00000010  (2 in decimal)
```

```python
a = 5   # Binary: 101
print(a >> 1)  # Moves bits right → Binary: 10 (Decimal: 2)
```  

### **5. Assignment Operators**
```python
a = 10
a += 5  # a = a + 5 => 15
a -= 3  # a = a - 3 => 12
a *= 2  # a = a * 2 => 24
a /= 4  # a = a / 4 => 6.0
a %= 5  # a = a % 5 => 1
a **= 3 # a = a ** 3 => 1
```

### **6. Identity Operators**
```python
a = [1, 2, 3]
b = a
c = [1, 2, 3]
print(a is b)    # True (Same object)
print(a is c)    # False (Different objects)
print(a is not c) # True
```

### **7. Membership Operators**
```python
text = "Hello, World!"
print('H' in text)       # True
print('hello' in text)   # False (Case-sensitive)
print('z' not in text)   # True
```

### Control flow

Control flow determines the execution order of statements in Python. It includes:

### **1. Conditional Statements (if, elif, else)**
```python
x = 10
if x > 0:
    print("Positive number")
elif x == 0:
    print("Zero")
else:
    print("Negative number")
```

### **2. Loops (for, while)**
#### **For Loop**
```python
for i in range(5):
    print(i)  # Prints numbers 0 to 4
```

#### **While Loop**
```python
x = 5
while x > 0:
    print(x)
    x -= 1  # Decrement x
```

### **3. Loop Control Statements**
#### **Break Statement** (Exits loop)
```python
for i in range(5):
    if i == 3:
        break  # Stops loop at 3
    print(i)
```

#### **Continue Statement** (Skips current iteration)
```python
for i in range(5):
    if i == 3:
        continue  # Skips 3
    print(i)
```

#### **Pass Statement** (Placeholder for future code)
```python
def my_function():
    pass  # Placeholder for implementation
```
## **Inbuilt Data Structures in Python**

Python provides several built-in data structures to manage and manipulate data efficiently. Each data structure serves a different purpose and is useful in different situations.

### **Indexing in Python**
Python allows accessing elements in sequences like lists, tuples, and strings using **positive** and **negative indexing**.

- **Positive Indexing:** Starts from 0 and moves forward (left to right).
- **Negative Indexing:** Starts from -1 and moves backward (right to left).

#### **Visual Representation of Indexing**
```
  String:   H   e   l   l   o   ,       W   o   r   l   d   !
Positive:   0   1   2   3   4   5   6   7   8   9   10  11  12
Negative: -13 -12 -11 -10 -9  -8  -7  -6  -5  -4  -3  -2  -1
```
---

## **1. List** (Ordered, Mutable, Allows Duplicates)
A list is used to store multiple items in a single variable.

#### **Declaring a List**
```python
my_list = [1, 2, 3, 4, 5]
print(my_list)
```
**Operations:**
- **Appending Elements:** `my_list.append(6)  # Adds 6 to the end`
- **Removing Elements:** `my_list.remove(2)  # Removes 2 from the list,first occurance of 2`
- **Pop Elements:** `my_list.pop()  # Removes and returns the last element`
- **Updating Elements:** `my_list[1] = 10  # Changes second element to 10`
- **Index of Element:** `index=my_list.index(1)  # Returns the index where the element is present`
-  **Count of Element:** `my_list.count(2) # Returns  the no of times the number appears in list`
- **Sorting:** `my_list.sort()  # Sorts the list in ascending order, list.sort(reverse=True) desc`
-  **Reversing:** `my_list.reverse()  # Reverses the list `

**Output:**
```
[1, 2, 3, 4, 5]
```
#### **Slicing a List**


In Python slicing notation [start:stop:step], each part represents:

start – The index where the slice begins (inclusive).

stop – The index where the slice ends (exclusive).

step – The interval between elements (default is 1)


Simple Analogy: Why is print(my_list[1:8:-1]) Empty?

Imagine you're standing on step 1 of a staircase, and someone tells you:

🚶‍♂️ "Walk backward (-1 step) until you reach step 8."

But wait! ❌ You're already at step 1, and step 8 is ahead of you!

How can you move backward to a number that is ahead? You can’t! 😵‍💫

Since the instruction doesn’t make sense, Python just gives up and returns an empty list ([]) instead.

```python
print(my_list[1:4])  # Extracts elements from index 1 to 3
print(my_list[::-1])  # Reverses the list
print(my_list[-4:-1]) # Extracts elements using negative indexes
```
**Output:**
```
[2, 3, 4]
[5, 4, 3, 2, 1]
[2, 3, 4]
```




## **List Traversing, `enumerate()`, and List Comprehension**

### **1️⃣ List Traversing (Looping Through a List)**  
💡 **"Going through each item in a list one by one."**  

#### **Example: Using a `for` loop to print all items**
```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)
```
🔹 **Output:**
```
apple
banana
cherry
```

---

### **2️⃣ `enumerate()`: Looping with Index**  
💡 **"Gives both the index and value of items in a list."**  

#### **Example: Using `enumerate()` to get index + value**
```python
fruits = ["apple", "banana", "cherry"]

for index, fruit in enumerate(fruits):
    print(f"Index {index}: {fruit}")
```
🔹 **Output:**
```
Index 0: apple
Index 1: banana
Index 2: cherry
```

---

### **3️⃣ List Comprehension: A Shortcut for Creating Lists**  
💡 **"A quick way to create a new list in one line!"**  
``` python
# 1️⃣ Basic List Comprehension
[expression for item in iterable]

# 2️⃣ With `if` Condition (Filtering)
[expression for item in iterable if condition]

# 3️⃣ With `if-else` Condition
[expression_if_true if condition else expression_if_false for item in iterable]

# 4️⃣ Nested Loops
[expression for item1 in iterable1 for item2 in iterable2]

# 5️⃣ With Function Calls
[function(item) for item in iterable]

# 6️⃣ String Manipulation
[expression for item in string_list]

# 7️⃣ Flattening a 2D List
[expression for sublist in nested_list for item in sublist]
```

#### **Example: Creating a list of squares**
```python
numbers = [1, 2, 3, 4, 5]
squares = [x * x for x in numbers]
print(squares)
```
🔹 **Output:**
```
[1, 4, 9, 16, 25]
```

#### **Example: Filtering even numbers**
```python
numbers = [1, 2, 3, 4, 5, 6]
evens = [x for x in numbers if x % 2 == 0]
print(evens)
```
🔹 **Output:**
```
[2, 4, 6]
```
---

## **2. Tuple** (Ordered, Immutable, Allows Duplicates, Supports Multiple Types)

Tuples are like lists but immutable (cannot be changed after creation). They can store elements of different data types.

---

### **Declaring a Tuple**
```python
my_tuple = (1, 2.5, "hello", True)
print(my_tuple)
```
✅ **Output:**
```
(1, 2.5, 'hello', True)
```
✅ **Tuples can store multiple data types.**

---

### **Accessing Elements in a Tuple**
```python
print(my_tuple[2])  # Prints 'hello'
```
✅ Tuples support **zero-based indexing** like lists.

---

### **Tuple Slicing**
```python
print(my_tuple[1:3])  # Extracts (2.5, 'hello')
```
✅ **Slicing returns a new tuple** containing the selected range.

---

### **Tuple Operations**
- **Concatenation:**
```python
new_tuple = my_tuple + (6, 7)
print(new_tuple)  # Output: (1, 2.5, 'hello', True, 6, 7)
```
- **Repetition:**
```python
doubled = my_tuple * 2
print(doubled)  # Output: (1, 2.5, 'hello', True, 1, 2.5, 'hello', True)
```

---

### **Tuples Are Immutable**
```python
my_tuple[0] = 10  # TypeError: 'tuple' object does not support item assignment
```
✅ **Once created, elements cannot be changed.**

---

### **Tuple Methods**
- **Counting occurrences:**
```python
print((1, 2, 3, 1, 1).count(1))  # Output: 3
```
- **Finding index of element:**
```python
print((1, 2, 3).index(2))  # Output: 1
```

---

### **Packing & Unpacking Tuples**
- **Packing:**
```python
tuple1 = 10, "apple", 3.5  # Automatically creates a tuple
```
- **Unpacking:**
```python
a, b, c = tuple1
print(a, b, c)  # Output: 10 apple 3.5
```
✅ Unpacking assigns values **from tuple to variables.**

---

### **Nested Tuples**
```python
nested_tuple = ((1, 2, 3), ("a", "b", "c"))
print(nested_tuple[1][2])  # Output: 'c'
```
✅ Tuples can **contain other tuples**, forming a nested structure.



## **3. Set** (Unordered, Mutable, No Duplicates)
A set is used to store unique values in an unordered way.

#### **Declaring a Set**
```python
my_set = {1, 2, 3, 4, 5}
print(my_set)
```
**Operations:**
- **Adding Elements:** `my_set.add(6)  # Adds 6 to the set`
- **Removing Elements:** `my_set.remove(3)  # Removes 3 from the set, diplayan error if the element is not present.`
- **Discard:** `my_set.discard(3) # Removes the element if present ,if not no error `
- **Union:** `set_a | set_b  # Combines two sets , set_a.union(set_b)`
- **Intersection:** `set_a & set_b  # Finds common elements, set_a.intersection(set_b) || set_a.intersection_update(set_b) set_a will be updated with the result of intersection`
- **Difference:** `set_a.differnece(set_b) # elemen that is there in set a but not in set b `
- **Symmetric difference:** `set_a.symmetric_differnece(set_b) # unqiue elements from both the set `
- **Is Subset:** `set_a.issubset(set_b) # if all elements of  set a are there in  b`

- ❌ You cannot update a set element directly.

  
✅ You can remove an old value and add a new one instead.

❌ Sets are mutable, but they can only store immutable elements.


✅ Frozensets are immutable (unchangeable).

``` python

frozen_set = frozenset({1, 2, 3})
frozen_set.add(4)  # ❌ ERROR: Cannot modify a frozenset

```

✅ Subset (<=) → All elements of A are in B.

✅ Superset (>=) → B contains all elements of A.

✅ Proper Subset (<) → A ⊂ B but A ≠ B.

✅ Proper Superset (>) → B ⊃ A but B ≠ A.

---

## 4. **Dictionary in Python (unordered and mutable)**

A dictionary is a collection of key-value pairs where keys must be unique.

### **Declaring a Dictionary**
```python
my_dict = {"name": "Alice", "age": 25}
print(my_dict)
```

or 

```python
empty_dict = dict()
```

### **Accessing Dictionary Elements**
```python
print(my_dict["name"])  # Output: Alice
print(my_dict.get("age","default value"))  # Output: 25
```

### **Modifying a Dictionary**
- **Adding Key-Value Pairs:**
  ```python
  my_dict["city"] = "New York"
  ```
- **Updating Values:**
  ```python
  my_dict["age"] = 30  # Changes age to 30
  ```
- **Removing Elements:**
  ```python
  del my_dict["age"]  # Deletes age
  my_dict.pop("name")  # Removes 'name' key
  my_dict.clear()  # Removes all elements
  ```

### **Dictionary Methods**
```python
my_dict = {"name": "Alice", "age": 25, "city": "New York"}
```

| Method | Description | Example | Output |
|--------|-------------|-------------|-------------|
| `keys()` | Returns all keys in the dictionary | `my_dict.keys()` | `dict_keys(['name', 'age', 'city'])` |
| `values()` | Returns all values in the dictionary | `my_dict.values()` | `dict_values(['Alice', 25, 'New York'])` |
| `items()` | Returns key-value pairs as tuples | `my_dict.items()` | `dict_items([('name', 'Alice'), ('age', 25), ('city', 'New York')])` |
| `get(key)` | Retrieves a value by key | `my_dict.get("name")` | `Alice` |
| `update()` | Merges another dictionary into current one | `my_dict.update({"gender": "female"})` | `{..., 'gender': 'female'}` |
| `pop(key)` | Removes and returns a value by key | `my_dict.pop("age")` | `25` |
| `clear()` | Removes all key-value pairs | `my_dict.clear()` | `{}` |

### **Dictionary Operators:**
| Operator | Description | Example | Output |
|----------|-------------|-------------|-------------|
| `in` | Checks if a key exists in the dictionary | `'name' in my_dict` | `True` |
| `not in` | Checks if a key is not in the dictionary | `'gender' not in my_dict` | `False` |
| `==` | Checks if two dictionaries are equal | `dict1 == dict2` | `True` or `False` |
| `!=` | Checks if two dictionaries are not equal | `dict1 != dict2` | `True` or `False` |

Dictionaries are powerful for storing and accessing key-value data efficiently in Python.



### **Normal Copy vs Shallow Copy vs Deep Copy in Dictionary**

#### **Normal Copy:**
A **normal copy** creates a new dictionary but does not duplicate nested objects.

##### **Example:**
```python
original = {"name": "Alice", "age": 25}
copied_dict = original  # Normal copy (reference to the same object)
copied_dict["age"] = 30

print(original["age"])  # Output: 30 (Changes reflect in the original dictionary)
```

**Explanation:**
- `copied_dict = original` only assigns a reference, meaning both variables point to the same dictionary.
- Modifications in `copied_dict` affect `original` as well.

#### **Shallow Copy:**
A **shallow copy** creates a new dictionary but still references mutable objects inside it.

##### **Example:**
```python
import copy

original = {"name": "Alice", "details": {"age": 25, "city": "New York"}}
shallow_copy = original.copy()

shallow_copy["details"]["age"] = 30
print(original["details"]["age"])  # Output: 30
```

**Explanation:**
- `copy()` creates a new dictionary, but the nested dictionary inside it is still referenced, not duplicated.
- Changing `shallow_copy["details"]["age"]` also affects `original`.

#### **Deep Copy:**
A **deep copy** creates a completely independent copy, including all nested structures.

##### **Example:**
```python
import copy

deep_copy = copy.deepcopy(original)
deep_copy["details"]["age"] = 35

print(original["details"]["age"])  # Output: 30 (unchanged)
```

**Key Differences:**
| Type | Copy Behavior | Nested Objects Affected? |
|------|--------------|-------------------------|
| Normal Copy | Reference assignment | Yes (Changes reflect in both) |
| Shallow Copy | Creates a new dictionary but keeps references for nested objects | Yes (Changes in nested objects affect both) |
| Deep Copy | Completely duplicates everything | No (Completely independent copy) |



### **Dictionary Comprehension**

Dictionary comprehension allows creating dictionaries in a concise way.

#### **Basic Syntax:**
```python
dict_comp = {key: value for key, value in iterable}
```

#### **Examples:**
1. **Creating a dictionary from a list:**
   ```python
   nums = [1, 2, 3, 4]
   squares = {num: num**2 for num in nums}
   print(squares)  # Output: {1: 1, 2: 4, 3: 9, 4: 16}
   ```

2. **Filtering elements:**
   ```python
   nums = range(10)
   even_squares = {num: num**2 for num in nums if num % 2 == 0}
   print(even_squares)  # Output: {0: 0, 2: 4, 4: 16, 6: 36, 8: 64}
   ```

3. **Using `zip()` to combine two lists into a dictionary:**
   ```python
   keys = ["name", "age", "city"]
   values = ["Alice", 25, "New York"]
   merged_dict = {k: v for k, v in zip(keys, values)}
   print(merged_dict)  # Output: {'name': 'Alice', 'age': 25, 'city': 'New York'}
   ```

4. **Nested Dictionary Comprehension:**
   ```python
   matrix = {row: {col: row * col for col in range(1, 6)} for row in range(1, 4)}
   print(matrix)
   # Output: {1: {1: 1, 2: 2, 3: 3, 4: 4, 5: 5}, 2: {1: 2, 2: 4, 3: 6, 4: 8, 5: 10}, 3: {1: 3, 2: 6, 3: 9, 4: 12, 5: 15}}
   ```
- Unordered (Dictionaries, Sets) → No Fixed Position
Elements are stored based on hashing, not index positions.
You cannot access elements using numeric indexes like in lists.



## **Merging Dictionaries in Python**

Python provides multiple ways to **merge dictionaries**, each with different behaviors.  

---

### **1. Using `update()` (Modifies the Original Dictionary)**
```python
 dict1 = {"a": 1, "b": 2}
 dict2 = {"b": 3, "c": 4}

 dict1.update(dict2)  
 print(dict1)  
 # Output: {'a': 1, 'b': 3, 'c': 4}  (Values from dict2 overwrite dict1)
```
✅ **Modifies** `dict1`, updates existing keys, and adds new keys.  

---

### **2. Using `|` Operator (Python 3.9+) (Creates a New Dictionary)**
```python
 dict1 = {"a": 1, "b": 2}
 dict2 = {"b": 3, "c": 4}

 merged_dict = dict1 | dict2  
 print(merged_dict)  
 # Output: {'a': 1, 'b': 3, 'c': 4}
```
✅ **Creates a new dictionary**, leaving `dict1` and `dict2` unchanged.  

---

### **3. Using `{**dict1, **dict2}` (Unpacks Both Dictionaries)**
```python
 dict1 = {"a": 1, "b": 2}
 dict2 = {"b": 3, "c": 4}

 merged_dict = {**dict1, **dict2}  
 print(merged_dict)  
 # Output: {'a': 1, 'b': 3, 'c': 4}
```
✅ **Creates a new dictionary**, similar to `|` but works in Python 3.5+.  

---

 # 5. String Methods and Operations

## 1. String Operations

| Operation       | Description                               | Example         | Output         |
|---------------|--------------------------------|----------------|----------------|
| **Indexing** | Access characters using an index | `s[1]`       | `'e'`           |
| **Slicing** | Extract a substring | `s[1:3]`      | `'el'`     |
| **Concatenation** | Combine strings using `+` | `'Hello' + ' World'` | `'Hello World'`    |
| **Repetition** | Repeat string using `*` | `'Hi' * 3` | `'HiHiHi'` |
| **Membership** | Check if substring exists | `'H' in 'Hello'`     | `True`         |
| **Length** | Get the string length | `len(s)`      | `5`            |

---

## 2. String Methods

| Method       | Description                         | Example                | Output |
|-------------|----------------------------------|-----------------------|--------|
| `lower()`  | Converts string to lowercase | `'Hello'.lower()`  | `'hello'`    |
| `upper()`  | Converts string to uppercase | `'Hello'.upper()` | `'HELLO'`    |
| `title()`  | Converts first letter of each word to uppercase | `'hello world'.title()` | `'Hello World'` |
| `capitalize()` | Capitalizes the first letter of the string | `'hello'.capitalize()` | `'Hello'` |
| `strip()`  | Removes leading/trailing spaces | `'  hello  '.strip()` | `'hello'` |
| `lstrip()`  | Removes leading spaces | `'  hello'.lstrip()` | `'hello'` |
| `rstrip()`  | Removes trailing spaces | `'hello  '.rstrip()` | `'hello'` |
| `replace(a, b)` | Replaces occurrences of `a` with `b` | `'hello'.replace('l', 'x')` | `'hexxo'` |
| `split(x)`  | Splits string into a list by `x` | `'a,b,c'.split(',')` | `['a', 'b', 'c']` |
| `join(iterable)` | Joins elements with a string | `'-'.join(['a', 'b', 'c'])` | `'a-b-c'` |
| `find(x)`   | Returns index of first occurrence of `x` | `'hello'.find('l')` | `2` |
| `rfind(x)`  | Returns index of last occurrence of `x` | `'hello'.rfind('l')` | `3` |
| `count(x)`  | Counts occurrences of `x` | `'hello'.count('l')` | `2` |
| `startswith(x)` | Checks if string starts with `x` | `'hello'.startswith('he')` | `True` |
| `endswith(x)` | Checks if string ends with `x` | `'hello'.endswith('lo')` | `True` |
| `isalpha()` | Returns `True` if all characters are letters | `'hello'.isalpha()` | `True` |
| `isdigit()` | Returns `True` if all characters are digits | `'123'.isdigit()` | `True` |
| `isalnum()` | Returns `True` if all characters are alphanumeric | `'hello123'.isalnum()` | `True` |
| `isspace()` | Returns `True` if all characters are spaces | `'   '.isspace()` | `True` |
| `swapcase()` | Swaps case of each letter | `'Hello'.swapcase()` | `'hELLO'` |
| `zfill(n)` | Pads string with zeros to length `n` | `'42'.zfill(5)` | `'00042'` |
| `format()` | Formats string with placeholders | `"Hello {}".format("World")` | `'Hello World'` |
| `f-strings` | Formats strings using f-prefix | `f"Hello {name}"` | `'Hello Alice'` |

---

## 3. String Immutability

Strings **cannot** be modified directly:
```python
s = "hello"
s[0] = "H"  # ❌ TypeError: 'str' object does not support item assignment
```
Instead, create a new string:
```python
s = "H" + s[1:]  # ✅ 'Hello'
```




## **Comparison of Inbuilt Data Structures in Python**

Python provides several inbuilt data structures, each with its own characteristics and use cases.

| Data Structure | Ordered | Mutable | Allows Duplicates | When to Use |
|---------------|---------|---------|------------------|-------------|
| **List** | ✅ Yes | ✅ Yes | ✅ Yes | When you need an ordered collection that can be modified. Suitable for dynamic data storage. |
| **Tuple** | ✅ Yes | ❌ No | ✅ Yes | When you need an ordered but immutable collection. Suitable for fixed data that should not change. |
| **Set** | ❌ No | ✅ Yes | ❌ No | When you need a collection of unique elements with fast membership checks. Suitable for removing duplicates. |
| **Dictionary** | ❌ No | ✅ Yes | ✅ Yes (for values) | When you need key-value pairs for quick lookups. Suitable for structured data and mappings. |

### **When to Use What?**
- **Use a List** when order matters and you need to modify elements frequently.
- **Use a Tuple** when you need an ordered collection that should remain constant.
- **Use a Set** when you need unique elements and fast membership testing.
- **Use a Dictionary** when you need key-value storage with efficient lookups.

Each structure serves a specific purpose, so choosing the right one depends on the problem you're solving.



### **Why does `fruits[1:] = "watermelon"` split the word?**
When assigning a string to a slice of a list, Python treats the string as a sequence of characters and inserts each character separately into the list. Example:
```python
fruits = ["apple", "banana", "cherry"]
fruits[1:] = "watermelon"
print(fruits)
```
**Output:**
```
['apple', 'w', 'a', 't', 'e', 'r', 'm', 'e', 'l', 'o', 'n']
```
**Explanation:** Instead of replacing the entire slice with one string, Python breaks the string into its individual characters and inserts them into the list.

These data structures help in different scenarios, such as storing collections of items, ensuring uniqueness, or mapping keys to values.


## **Functions in Python**
Functions in Python help in organizing code into reusable blocks. They improve readability, reduce redundancy, and make programs modular.

### **Why Use Functions?**
- Avoid repetition by reusing code
- Improve readability and maintainability
- Simplify debugging and modifications
- Enable modular programming

---

### **1. Syntax of a Function**
A function is defined using the `def` keyword, followed by its name, parameters (if any), and a colon. The function body is indented.

```python
def function_name(parameters):
    """Optional docstring explaining the function."""
    statement(s)
    return value  # Optional return statement
```

---

### **2. Defining a Function**
A simple function that prints a greeting message.

```python
def greet():
    """This function prints a greeting message."""
    print("Hello, World!")
```

---

### **3. Calling a Function**
To execute a function, call it by its name followed by parentheses `()`.

```python
greet()  # Output: Hello, World!
```

---

### **4. Function Parameters**
Functions can take parameters (input values) to process data.

```python
def greet_user(name):
    """This function greets the user by name."""
    print(f"Hello, {name}!")

greet_user("Alice")  # Output: Hello, Alice!
```

---

### **5. Positional Arguments**
Positional arguments are passed in the order they are defined in the function.

```python
def full_name(first, last):
    """Displays the full name by combining first and last name."""
    print(f"Full Name: {first} {last}")

full_name("John", "Doe")  # Output: Full Name: John Doe
```

---

### **6. Default Parameters**
If a parameter is not provided, a default value is used.

```python
def greet_user(name="Guest"):
    """Greets the user, using 'Guest' as default if no name is provided."""
    print(f"Hello, {name}!")

greet_user()       # Output: Hello, Guest!
greet_user("Bob")  # Output: Hello, Bob!
```

---

### **7. Variable-Length Arguments**
- `*args` allows multiple positional arguments. 
- `**kwargs` allows multiple keyword arguments. (key,value pairs)

NOTE : Positional comes before keyword arguments


```python
def add_numbers(*args):
    """Returns the sum of all provided numbers."""
    return sum(args)

print(add_numbers(1, 2, 3, 4))  # Output: 10
```

```python
def user_info(**kwargs):
    """Prints user information from keyword arguments."""
    for key, value in kwargs.items():
        print(f"{key}: {value}")

user_info(name="Alice", age=25)  
# Output:
# name: Alice
# age: 25
```

---

### **8. Return Statement**
A function can return a value using the `return` keyword.

```python
def square(num):
    """Returns the square of a given number."""
    return num * num

result = square(5)
print(result)  # Output: 25
```

---

### **9. Function with Docstring**
A docstring is a multi-line string that provides documentation for a function.

```python
def multiply(a, b):
    """This function multiplies two numbers and returns the result."""
    return a * b

print(multiply(3, 4))  # Output: 12
```

# **Lambda, Map, and Filter in Python**

## **1. Lambda Functions**
Lambda functions are anonymous functions in Python that can have any number of arguments but only one expression.

### **Syntax:**
```python
lambda arguments: expression
```

### **Example:**
```python
square = lambda x: x * x
print(square(5))  # Output: 25
```

---

## **2. `map()` Function**
The `map()` function applies a given function to all items in an iterable.

### **Syntax:**
```python
map(function, iterable)
```

### **Example:**
```python
numbers = [1, 2, 3, 4]
squared_numbers = list(map(lambda x: x ** 2, numbers))
print(squared_numbers)  # Output: [1, 4, 9, 16]
```

---

## **3. `filter()` Function**
The `filter()` function filters elements based on a condition.

### **Syntax:**
```python
filter(function, iterable)
```

### **Example:**
```python
numbers = [1, 2, 3, 4, 5, 6]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)  # Output: [2, 4, 6]
```

---

## **Conclusion**
- `lambda` is used to create small, one-line anonymous functions.
- `map()` applies a function to all elements in an iterable.
- `filter()` selects elements based on a condition.

These functions help in writing concise and efficient code.

# **Type Conversion in Python**

## **1. Introduction**
Type conversion in Python allows you to change the data type of a variable from one type to another. There are two types of conversions:
- **Implicit Conversion** (Automatic by Python)
- **Explicit Conversion** (Manually using built-in functions)

---

## **2. Implicit Type Conversion**
Python automatically converts one data type to another where necessary, without losing data.

### **Example:**
```python
x = 5  # Integer
y = 2.5  # Float
z = x + y  # Python converts x into float
print(z, type(z))  # Output: 7.5 <class 'float'>
```
---

## **3. Explicit Type Conversion**
Explicit conversion is done using built-in functions like `int()`, `float()`, `str()`, etc.

### **Example:**
```python
num = "123"
num_int = int(num)  # Converts string to integer
print(num_int, type(num_int))  # Output: 123 <class 'int'>
```

### **Common Type Conversion Functions:**
| Function | Description |
|----------|-------------|
| `int(x)` | Converts x to an integer |
| `float(x)` | Converts x to a floating-point number |
| `str(x)` | Converts x to a string |
| `list(x)` | Converts x to a list |
| `tuple(x)` | Converts x to a tuple |
| `dict(x)` | Converts x to a dictionary |
| `set(x)` | Converts x to a set |
| `bool(x)` | Converts x to a boolean |

---

## **4. JSON Conversions**
### **Converting Python Objects to JSON (Serialization)**
Python provides the `json` module to work with JSON.

#### **Example using `json.dumps()`**
```python
import json
data = {"name": "Alice", "age": 25}
json_data = json.dumps(data)  # Convert dictionary to JSON string
print(json_data)  # Output: {"name": "Alice", "age": 25}
```

### **Converting JSON to Python Objects (Deserialization)**
#### **Example using `json.loads()`**
```python
json_string = '{"name": "Alice", "age": 25}'
python_obj = json.loads(json_string)  # Convert JSON string to dictionary
print(python_obj, type(python_obj))  # Output: {'name': 'Alice', 'age': 25} <class 'dict'>
```
---

## **5. Joining and Splitting Strings**

### **Joining a List into a String using `join()`**
```python
words = ["Hello", "World"]
joined_string = " ".join(words)
print(joined_string)  # Output: Hello World
```

### **Splitting a String into a List using `split()`**
```python
text = "Hello,World,Python"
words = text.split(",")
print(words)  # Output: ['Hello', 'World', 'Python']
```
---

## **6. Tuple to List and Vice Versa**

### **Converting Tuple to List**
```python
tuple_data = (1, 2, 3)
list_data = list(tuple_data)
print(list_data, type(list_data))  # Output: [1, 2, 3] <class 'list'>
```

### **Converting List to Tuple**
```python
list_data = [1, 2, 3]
tuple_data = tuple(list_data)
print(tuple_data, type(tuple_data))  # Output: (1, 2, 3) <class 'tuple'>
```
---

## **7. Integer to String and Vice Versa**

### **Converting Integer to String**
```python
num = 100
str_num = str(num)
print(str_num, type(str_num))  # Output: '100' <class 'str'>
```

### **Converting String to Integer**
```python
num_str = "200"
num_int = int(num_str)
print(num_int, type(num_int))  # Output: 200 <class 'int'>
```

---

## **8. Boolean Conversion**
Booleans are converted using `bool()`. Any non-zero value is `True`, zero or empty structures are `False`.

### **Example:**
```python
print(bool(0))  # Output: False
print(bool(5))  # Output: True
print(bool(""))  # Output: False
print(bool("Hello"))  # Output: True
```
---

## **9. Other Type Conversions**

### **Bytes to String and Vice Versa**
```python
byte_data = b'Hello'
str_data = byte_data.decode('utf-8')
print(str_data)  # Output: Hello
```

```python
str_data = "Hello"
byte_data = str_data.encode('utf-8')
print(byte_data)  # Output: b'Hello'
```

### **Dictionary to List of Tuples and Vice Versa**
```python
d = {'a': 1, 'b': 2}
tuple_list = list(d.items())
print(tuple_list)  # Output: [('a', 1), ('b', 2)]
```

```python
tuple_list = [('a', 1), ('b', 2)]
d = dict(tuple_list)
print(d)  # Output: {'a': 1, 'b': 2}
```
---

## **10. Summary**
- Implicit conversion happens automatically when possible.
- Explicit conversion uses built-in functions like `int()`, `float()`, `str()`, etc.
- JSON conversion is done using `json.dumps()` and `json.loads()`.
- `join()` merges a list into a string, `split()` breaks a string into a list.
- Additional conversions include bytes-string, dictionary-tuple, and vice versa.
- Python provides flexible ways to convert between different data types efficiently.



# **Regular Expressions (Regex) in Python**
Regular Expressions (regex) are patterns used to match and manipulate strings efficiently. They help in searching, extracting, and modifying text data.

## **Why Use Regex?**
- Efficient text searching and pattern matching
- Data validation (e.g., emails, phone numbers)
- Text extraction and replacement
- Splitting text based on patterns

---

## **1. Importing the `re` Module**
Python provides the `re` module to work with regex.
```python
import re
```

---

## **2. Basic Regex Functions**

### **a) `re.match()` - Matches at the beginning of the string**
```python
import re
text = "Hello World"
match = re.match(r"Hello", text)
print(bool(match))  # Output: True
```

### **b) `re.search()` - Searches anywhere in the string**
```python
import re
text = "Welcome to Regex in Python"
search = re.search(r"Regex", text)
print(bool(search))  # Output: True
```

### **c) `re.findall()` - Finds all matches**
```python
import re
text = "123 apple, 456 banana, 789 cherry"
numbers = re.findall(r"\d+", text)
print(numbers)  # Output: ['123', '456', '789']
```

### **d) `re.sub()` - Replaces text using regex**
```python
import re
text = "I love cats. Cats are cute."
new_text = re.sub(r"cats", "dogs", text, flags=re.IGNORECASE)
print(new_text)  # Output: "I love dogs. Dogs are cute."
```

---

## **3. Special Characters in Regex**

| Symbol | Meaning |
|--------|---------|
| `.` | Any character except newline |
| `^` | Start of string |
| `$` | End of string |
| `*` | 0 or more occurrences |
| `+` | 1 or more occurrences |
| `?` | 0 or 1 occurrence |
| `{n}` | Exactly n occurrences |
| `{n,}` | At least n occurrences |
| `{n,m}` | Between n and m occurrences |
| `\d` | Any digit (0-9) |
| `\D` | Any non-digit |
| `\w` | Any alphanumeric character |
| `\W` | Any non-alphanumeric character |
| `\s` | Any whitespace |
| `\S` | Any non-whitespace |

---

## **4. Character Classes & Groups**

### **a) Character Classes (`[]`)**
```python
import re
text = "The price is 500 dollars."
match = re.findall(r"[0-9]+", text)
print(match)  # Output: ['500']
```

### **b) Grouping (`()`)**
```python
import re
text = "My phone number is (123) 456-7890"
match = re.search(r"\((\d{3})\) (\d{3})-(\d{4})", text)
print(match.groups())  # Output: ('123', '456', '7890')
```

---

## **5. Lookaheads & Lookbehinds**
Used to match patterns without including them in the result.

### **a) Positive Lookahead (`?=`)**
```python
import re
text = "apple123 banana456 cherry789"
match = re.findall(r"\w+(?=\d+)", text)
print(match)  # Output: ['apple', 'banana', 'cherry']
```

### **b) Negative Lookahead (`?!`)**
```python
import re
text = "apple123 banana apple456 cherry"
match = re.findall(r"apple(?!\d+)", text)
print(match)  # Output: ['apple']
```

### **c) Positive Lookbehind (`?<=`)**
```python
import re
text = "$10 $20 €30 €40"
match = re.findall(r"(?<=\$)\d+", text)
print(match)  # Output: ['10', '20']
```

### **d) Negative Lookbehind (`?<!`)**
```python
import re
text = "$10 $20 €30 €40"
match = re.findall(r"(?<!\$)\d+", text)
print(match)  # Output: ['30', '40']
```

---

## **6. Splitting Strings with `re.split()`**
```python
import re
text = "apple,banana;cherry|grape"
words = re.split(r"[,;|]", text)
print(words)  # Output: ['apple', 'banana', 'cherry', 'grape']
```

---

## **7. Compiling Regex for Efficiency**
```python
import re
pattern = re.compile(r"\d+")
text = "Order 123, Item 456"
print(pattern.findall(text))  # Output: ['123', '456']
```

---

## **Conclusion**
Regular expressions are powerful tools for handling text efficiently. With `re` module functions like `match()`, `search()`, `findall()`, `sub()`, and `split()`, you can manipulate and extract patterns with ease.


# **Modules and Packages in Python**

## **1. What are Modules?**
A module is a Python file containing reusable code (functions, classes, variables). It helps organize code into separate files for better readability and maintainability.

### **a) Creating a Module**
Save the following code in a file named `my_module.py`:
```python
# my_module.py
def greet(name):
    return f"Hello, {name}!"
```

### **b) Importing a Module**
```python
import my_module
print(my_module.greet("Alice"))  # Output: Hello, Alice!
```

### **c) Importing Specific Functions**
```python
from my_module import greet
print(greet("Bob"))  # Output: Hello, Bob!
```

### **d) Using Aliases**
```python
import my_module as mm
print(mm.greet("Charlie"))  # Output: Hello, Charlie!
```

### **e) Built-in Modules**
Python comes with many built-in modules like `math`, `random`, and `os`.
```python
import math
print(math.sqrt(16))  # Output: 4.0
```

---

## **2. What are Packages?**
A package is a collection of modules organized in directories containing a special `__init__.py` file (optional in Python 3+).

### **a) Creating a Package**
1. Create a directory `my_package/`.
2. Inside `my_package/`, create `__init__.py` (empty or containing package initialization code).
3. Add a module `module1.py`:
```python
# my_package/module1.py
def say_hello():
    return "Hello from module1!"
```

### **b) Importing a Module from a Package**
```python
from my_package import module1
print(module1.say_hello())  # Output: Hello from module1!
```

### **c) Importing Using `from ... import`**
```python
from my_package.module1 import say_hello
print(say_hello())  # Output: Hello from module1!
```

### **d) Nested Packages**
Packages can contain sub-packages:
```
my_package/
    __init__.py
    sub_package/
        __init__.py
        module2.py
```
Importing a sub-package module:
```python
from my_package.sub_package import module2
```

---

## **3. Difference Between Modules and Packages**
| Feature  | Module | Package |
|----------|--------|---------|
| Definition | A single Python file | A collection of modules in a directory |
| Structure | `.py` file | Folder with `__init__.py` |
| Example | `math.py` | `numpy` package |

---

## **4. Installing External Packages**
Use `pip` to install third-party packages from PyPI.
```sh
pip install requests
```
Using the installed package:
```python
import requests
response = requests.get("https://api.github.com")
print(response.status_code)
```

---

- Modules allow code reuse and better organization.
- Packages group related modules into directories.
- Use `import` to access modules and packages.
- Use `pip` to install third-party packages.



# **Standard Python Library**

Python's **Standard Library** is a collection of built-in modules that provide powerful functionalities without needing external dependencies.

---

## **1. Built-in Functions**
Python provides several built-in functions such as:
- `print()`, `len()`, `type()`, `input()`
- `max()`, `min()`, `sum()`
- `sorted()`, `enumerate()`, `zip()`

Example:
```python
print(len("Hello"))  # Output: 5
```

---

## **2. OS Module** *(Interacting with the Operating System)*
```python
import os
print(os.name)  # Returns OS name
```

---

## **3. Sys Module** *(System-Specific Parameters & Functions)*
```python
import sys
print(sys.version)  # Outputs Python version
```

---

## **4. Math Module** *(Mathematical Functions)*
```python
import math
print(math.sqrt(25))  # Output: 5.0
```

---

## **5. Random Module** *(Generating Random Numbers)*
```python
import random
print(random.randint(1, 10))  # Outputs a random number between 1-10
```

---

## **6. Datetime Module** *(Working with Dates & Time)*
```python
from datetime import datetime
print(datetime.now())  # Outputs current date & time
```

---

## **7. JSON Module** *(Handling JSON Data)*
```python
import json
my_dict = {"name": "Alice", "age": 25}
json_data = json.dumps(my_dict)  # Convert dictionary to JSON string
print(json_data)
```

---

## **8. Collections Module** *(Advanced Data Structures)*
```python
from collections import Counter
print(Counter("banana"))  # Counts occurrences of elements
```

---

## **9. RE (Regular Expressions) Module** *(Pattern Matching)*
```python
import re
match = re.search(r"\d+", "Order 123")  # Finds numbers in text
print(match.group())  # Output: 123
```

---

## **10. OS Path Module** *(File Path Handling)*
```python
import os
print(os.path.exists("file.txt"))  # Checks if file exists
```

---

## **11. Urllib Module** *(Handling URLs & HTTP Requests)*
```python
import urllib.request
response = urllib.request.urlopen("https://www.google.com")
print(response.status)  # Output: 200 (OK)
```

---

## **12. Logging Module** *(Logging Messages)*
```python
import logging
logging.warning("This is a warning!")  # Logs a warning message
```

---

## **13. CSV Module** *(Reading & Writing CSV Files)*
```python
import csv
with open("data.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerow(["Name", "Age"])
    writer.writerow(["Alice", 25])
```

---

## **14. Time Module** *(Handling Time-Related Tasks)*
```python
import time
time.sleep(2)  # Pauses execution for 2 seconds
print("Done!")
```

---

## **15. Statistics Module** *(Performing Statistical Calculations)*
```python
import statistics
print(statistics.mean([1, 2, 3, 4, 5]))  # Output: 3.0
```

# **File Operations in Python**

## **1. Opening a File**
Python provides the `open()` function to open files in different modes.
```python
file = open("example.txt", "r")  # Opens a file in read mode
```

## **2. File Modes**
| Mode  | Description |
|------|-------------|
| `r`  | Read (default) – Opens a file for reading (error if file doesn’t exist) |
| `w`  | Write – Creates a new file or overwrites existing file |
| `a`  | Append – Opens file for appending new content |
| `x`  | Create – Creates a new file (error if file exists) |
| `b`  | Binary mode (used with other modes like `rb`, `wb`) |
| `t`  | Text mode (default, used with `r`, `w`, etc.) |
| `r+` | Read & Write – Reads and updates a file (error if file doesn’t exist) |
| `w+` | Write & Read – Overwrites file if exists, otherwise creates a new one |
| `a+` | Append & Read – Appends data to file and allows reading |

## **3. Reading a File (`r` Mode)**
```python
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

## **4. Writing to a File (`w` Mode)**
```python
with open("example.txt", "w") as file:
    file.write("Hello, World!")
```
**Note:** This will overwrite existing content.

## **5. Appending to a File (`a` Mode)**
```python
with open("example.txt", "a") as file:
    file.write("\nAppending new line")
```

## **6. Writing and Reading (`w+` Mode)**
```python
with open("example.txt", "w+") as file:
    file.write("New content")
    file.seek(0)  # Move cursor to beginning
    print(file.read())
```

## **7. Reading and Writing (`r+` Mode)**
```python
with open("example.txt", "r+") as file:
    print(file.read())  # Read existing content
    file.write("New Line")  # Append new content
```

## **8. Appending and Reading (`a+` Mode)**
```python
with open("example.txt", "a+") as file:
    file.write("\nMore data")
    file.seek(0)
    print(file.read())
```

## **9. Deleting a File**
```python
import os
os.remove("example.txt")  # Deletes the file
```

## **10. Checking if a File Exists Before Deleting**
```python
if os.path.exists("example.txt"):
    os.remove("example.txt")
else:
    print("File does not exist")
```

## **11. Best Practices**
- Always use `with open()` to handle files to avoid manual closing.
- Use `try-except` blocks to handle errors gracefully.
- Ensure file existence before performing delete operations.

---
This guide covers essential file operations in Python for reading, writing, appending, and handling files efficiently.



# **Exception Handling in Python**

## **1. Understanding Exceptions**
Exceptions are runtime errors that disrupt the normal flow of a program. Unlike syntax errors, exceptions occur when the code is syntactically correct but an operation fails during execution.

## **2. Difference Between Errors and Exceptions**
- **Errors**: Irrecoverable issues like syntax errors (e.g., missing colons, incorrect indentation).
- **Exceptions**: Recoverable issues that can be handled using exception-handling mechanisms (e.g., division by zero, accessing an undefined variable).

## **3. Common Types of Exceptions**
| Exception | Description |
|-----------|-------------|
| `ZeroDivisionError` | Division by zero error |
| `ValueError` | Invalid value (e.g., converting letters to integers) |
| `TypeError` | Incompatible operation between types |
| `IndexError` | Accessing an index out of range in lists/tuples |
| `KeyError` | Accessing a non-existent dictionary key |
| `FileNotFoundError` | Trying to open a file that doesn't exist |
| `AttributeError` | Accessing an invalid attribute of an object |

## **4. Basic Exception Handling**
```python
try:
    x = 10 / 0  # Division by zero error
except ZeroDivisionError:
    print("Cannot divide by zero!")
```
### **Output:**
```
Cannot divide by zero!
```

## **5. Handling Multiple Exceptions**
```python
try:
    num = int("abc")  # Invalid conversion
except (ValueError, TypeError):
    print("Invalid input type!")
```
### **Output:**
```
Invalid input type!
```

## **6. Using `else` with `try-except`**
The `else` block executes only if no exception occurs in the `try` block.
```python
try:
    num = int("42")
except ValueError:
    print("Invalid number!")
else:
    print("Conversion successful!", num)
```
### **Output:**
```
Conversion successful! 42
```

## **7. Using `finally` Block**
The `finally` block always executes, regardless of an exception occurring or not.
```python
try:
    file = open("test.txt", "w")
    file.write("Hello!")
except IOError:
    print("File error!")
finally:
    file.close()
    print("File closed.")
```
### **Output:**
```
File closed.
```

## **8. Difference Between `else` and `finally`**
- `else` executes only if no exception occurs.
- `finally` executes no matter what (whether an exception occurs or not).

## **9. Raising Custom Exceptions**
```python
try:
    age = -5
    if age < 0:
        raise ValueError("Age cannot be negative!")
except ValueError as e:
    print("Error:", e)
```
### **Output:**
```
Error: Age cannot be negative!
```

## **10. Defining Custom Exceptions**
```python
class CustomError(Exception):
    """A custom exception class."""
    def __init__(self, message):
        super().__init__(message)

try:
    raise CustomError("This is a custom error!")
except CustomError as e:
    print("Caught Exception:", e)
```
### **Output:**
```
Caught Exception: This is a custom error!
```

## **11. More Examples of Custom Exceptions**
### **Custom Exception with Additional Attributes**
```python
class AgeError(Exception):
    """Exception raised for invalid age."""
    def __init__(self, age, message="Age must be between 0 and 120"):
        self.age = age
        self.message = message
        super().__init__(self.message)

try:
    age = 150
    if age > 120:
        raise AgeError(age)
except AgeError as e:
    print(f"Invalid age {e.age}: {e.message}")
```
### **Output:**
```
Invalid age 150: Age must be between 0 and 120
```

### **Custom Exception for File Handling**
```python
class FileExtensionError(Exception):
    """Raised when the file extension is not allowed."""
    def __init__(self, filename, allowed_extensions):
        self.filename = filename
        self.allowed_extensions = allowed_extensions
        super().__init__(f"Invalid file type: {filename}. Allowed extensions are {allowed_extensions}.")

try:
    filename = "document.exe"
    if not filename.endswith((".txt", ".csv")):
        raise FileExtensionError(filename, [".txt", ".csv"])
except FileExtensionError as e:
    print(e)
```
### **Output:**
```
Invalid file type: document.exe. Allowed extensions are ['.txt', '.csv'].
```

## **12. More Custom Exception Examples**
### **Custom Exception for Negative Bank Balance**
```python
class NegativeBalanceError(Exception):
    """Raised when an account balance goes negative."""
    def __init__(self, balance):
        self.balance = balance
        super().__init__(f"Balance cannot be negative: {balance}")

try:
    balance = -100
    if balance < 0:
        raise NegativeBalanceError(balance)
except NegativeBalanceError as e:
    print(e)
```
### **Output:**
```
Balance cannot be negative: -100
```

### **Custom Exception for Invalid Email Format**
```python
import re

class InvalidEmailError(Exception):
    """Raised when an email format is invalid."""
    def __init__(self, email):
        self.email = email
        super().__init__(f"Invalid email format: {email}")

def validate_email(email):
    pattern = r"^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$"
    if not re.match(pattern, email):
        raise InvalidEmailError(email)

try:
    validate_email("invalid-email")
except InvalidEmailError as e:
    print(e)
```
### **Output:**
```
Invalid email format: invalid-email
```

## **13. Best Practices for Exception Handling**
- Always handle exceptions gracefully to prevent program crashes.
- Use specific exception types rather than a generic `except:` clause.
- Keep error messages meaningful to improve debugging.
- Use `finally` to release resources (e.g., closing files, database connections).
- Avoid using exceptions for normal control flow.
- Create custom exceptions when built-in exceptions are not enough.


# **Object-Oriented Programming (OOP) in Python**

## **1. Introduction to OOP**
Object-Oriented Programming (OOP) is a programming paradigm based on objects that contain both data (attributes) and behavior (methods). It helps in organizing code efficiently and makes it more reusable and scalable.

## **2. Key OOP Concepts**
### **1. Class and Object**
- **Class**: A blueprint for creating objects.
- **Object**: An instance of a class with unique values.

#### **Example:**
```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

my_car = Car("Toyota", "Corolla")  # Object creation
print(my_car.brand, my_car.model)
```
**Output:**
```
Toyota Corolla
```

---
### **2. Instance Variables and Methods**
- **Instance Variable**: A variable that is associated with an instance of a class.
- **Instance Method**: A method that operates on instance variables.

#### **Example:**
```python
class Person:
    def __init__(self, name, age):
        self.name = name  # Instance variable
        self.age = age  # Instance variable
    
    def greet(self):
        return f"Hello, my name is {self.name} and I am {self.age} years old."

person1 = Person("Alice", 30)
print(person1.greet())
```
**Output:**
```
Hello, my name is Alice and I am 30 years old.
```

---
### **3. Encapsulation and Access Modifiers**
Encapsulation is the practice of restricting direct access to some of an object's attributes and methods. It is achieved using access modifiers.

#### **Access Modifiers:**
- **Public (`var`)**: Accessible from anywhere.
- **Protected (`_var`)**: Should not be accessed directly but still accessible within subclasses.
- **Private (`__var`)**: Only accessible within the class.

#### **Example:**
```python
class Employee:
    def __init__(self, name, salary):
        self.name = name         # Public variable
        self._department = "IT"  # Protected variable
        self.__salary = salary   # Private variable
    
    def get_salary(self):
        return self.__salary  # Accessing private variable via method
    
    def set_salary(self, amount):
        if amount >= 0:
            self.__salary = amount
        else:
            print("Salary cannot be negative")

# Creating an instance
emp = Employee("John", 50000)
print(emp.name)         # Accessible (Public)
print(emp._department)  # Accessible but discouraged (Protected)
print(emp.get_salary()) # Accessing private variable via method
emp.set_salary(60000)
print(emp.get_salary())
```
**Output:**
```
John
IT
50000
60000
```

---
### **4. Inheritance**
#### **Definition:**
Inheritance is a mechanism where a child class acquires the properties and behaviors of a parent class.

#### **Types of Inheritance & Visualization:**
##### **Single Inheritance**
```
      Animal
        |
      Dog
```
```python
class Animal:
    def speak(self):
        return "Some sound"

class Dog(Animal):
    def speak(self):
        return "Bark"

dog = Dog()
print(dog.speak())
```
**Output:**
```
Bark
```

##### **Multiple Inheritance**
```
    Parent1      Parent2
        \         /
         \       /
          \     /
           Child
```
```python
class Parent1:
    def show(self):
        print("This is Parent1")

class Parent2:
    def display(self):
        print("This is Parent2")

class Child(Parent1, Parent2):
    pass

obj = Child()
obj.show()
obj.display()
```
**Output:**
```
This is Parent1
This is Parent2
```

##### **Multilevel Inheritance**
```
  Grandparent
      |
   Parent
      |
   Child
```
```python
class Grandparent:
    def greet(self):
        return "Hello from Grandparent"

class Parent(Grandparent):
    pass

class Child(Parent):
    pass

obj = Child()
print(obj.greet())
```
**Output:**
```
Hello from Grandparent
```

##### **Hierarchical Inheritance**
```
      Parent
      /    \
  Child1  Child2
```
```python
class Parent:
    def show(self):
        return "Hello from Parent"

class Child1(Parent):
    pass

class Child2(Parent):
    pass

obj1 = Child1()
obj2 = Child2()
print(obj1.show())
print(obj2.show())
```
**Output:**
```
Hello from Parent
Hello from Parent
```

##### **Hybrid Inheritance**
```
      A
     / \
    B   C
     \ /
      D
```
```python
class A:
    def show(self):
        return "Class A"

class B(A):
    pass

class C(A):
    pass

class D(B, C):
    pass

obj = D()
print(obj.show())
```
**Output:**
```
Class A
```

---
### **5. Polymorphism and Method Overriding**
```python
class Parent:
    def show(self):
        print("This is the Parent class")

class Child(Parent):
    def show(self):
        print("This is the Child class")

obj = Child()
obj.show()
```
**Output:**
```
This is the Child class
```

---
### **6. Abstraction & Abstract Classes**
```python
from abc import ABC, abstractmethod

class Vehicle(ABC):
    @abstractmethod
    def start(self):
        pass

class Car(Vehicle):
    def start(self):
        return "Car is starting"

car = Car()
print(car.start())
```
**Output:**
```
Car is starting
```

---
### **7. Dunder Methods & Operator Overloading**
```python
class CustomList:
    def __init__(self, items):
        self.items = items

    def __getitem__(self, index):
        return self.items[index]
    
    def __repr__(self):
        return f"CustomList({self.items})"
    
    def __add__(self, other):
        return CustomList(self.items + other.items)

cl1 = CustomList([1, 2])
cl2 = CustomList([3, 4])
cl3 = cl1 + cl2
print(cl3)
```
**Output:**
```
CustomList([1, 2, 3, 4])
```




# **Recursion**



# **Data Analysis**



# **Working with sqlite and python**


# **Introduction to Multi Threading**


# **Logging**


