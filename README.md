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




## **2. Tuple** (Ordered, Immutable, Allows Duplicates)
Tuples are like lists but immutable (cannot be changed after creation).

#### **Declaring a Tuple**
```python
my_tuple = (1, 2, 3, 4, 5)
print(my_tuple)
```
**Operations:**
- **Accessing Elements:** `print(my_tuple[2])  # Prints 3`
- **Slicing:** `print(my_tuple[1:3])  # Extracts (2,3)`
- **Concatenation:** `new_tuple = my_tuple + (6, 7)  # Adds new elements`

**Output:**
```
(1, 2, 3, 4, 5)
```
---

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

## **Dictionary in Python (unordered and mutable)**

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


## **5. String** (Immutable, Ordered Sequence of Characters)
A string is a sequence of characters enclosed in quotes.

#### **Slicing a String**
```python
my_string = "Hello, World!"
print(my_string[0:5])  # Extracts 'Hello'
print(my_string[::-1])  # Reverses the string
print(my_string[-6:-1]) # Extracts 'World'
```
**Operations:**
- **Concatenation:** `new_string = my_string + " Python"  # Adds new text`
- **Replacing Substrings:** `new_string.replace("Hello", "Hi")`
- **Splitting:** `words = new_string.split(" ")  # Splits by space`
- **Changing Case:** `print(my_string.upper())`, `print(my_string.lower())`

**Output:**
```
Hello
!dlroW ,olleH
World
```
---

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
