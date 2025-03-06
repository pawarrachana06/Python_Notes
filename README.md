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







