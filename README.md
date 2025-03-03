# Python--Notes

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


- syntax refers to the set of rules that defines the combination of symbols that are considered to be correctly strcutured programs in a language.

- Semantics refers to the menaing or the imterpretation of the symbols,characters,and commends in a language.It is about what the code is supposed to do when it runs.


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






