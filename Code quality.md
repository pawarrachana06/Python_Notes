# 🧹 Python Code Quality Tools

This markdown file explains commonly used Python code quality tools — `black`, `pylint`, and `ruff`. Learn what they do, how to install them, and how to use them in your projects.

---

## 1. `black` — The Uncompromising Code Formatter

### ✅ What It Does

* Reformats your code to a standard style automatically
* Opinionated: you don’t get to choose formatting rules
* Only handles **style**, not logic errors

### 📦 Installation

```bash
pip install black
```

### ⚙️ Usage

```bash
black script.py
```

Format all `.py` files in a folder:

```bash
black .
```

### 🛠 Example

Input:

```python
def add(x,y):return x+y
```

After `black`:

```python
def add(x, y):
    return x + y
```

---

## 2. `pylint` — The Code Inspector

### ✅ What It Does

* Analyzes Python code for bugs, errors, unused variables
* Gives a score out of 10
* Doesn't modify code, only gives warnings

### 📦 Installation

```bash
pip install pylint
```

### ⚙️ Usage

```bash
pylint script.py
```

### 🛠 Example Output

```
************* Module script
script.py:1:0: C0114: Missing module docstring (missing-module-docstring)
script.py:1:0: C0103: Function name "add" doesn't conform to snake_case naming style (invalid-name)
...
Your code has been rated at 7.50/10
```

### 🔧 Configuration

Generate a `.pylintrc` file:

```bash
pylint --generate-rcfile > .pylintrc
```

You can then customize options like ignored modules, max line length, naming conventions, etc.

---

## 3. `ruff` — The Fast All-in-One Tool

### ✅ What It Does

* Acts as both a **linter** and a **formatter**
* Super fast (written in Rust)
* Can auto-fix many issues
* Compatible with `black`, `flake8`, `pylint`, `mccabe`, `pyflakes`, etc.

### 📦 Installation

```bash
pip install ruff
```

### ⚙️ Usage

Lint only:

```bash
ruff script.py
```

Auto-fix:

```bash
ruff --fix script.py
```

### 🔧 Configuration

Create a `pyproject.toml` for custom settings:

```toml
[tool.ruff]
line-length = 88
select = ["E", "F", "W"]
ignore = ["E501"]
target-version = "py310"
```

You can also use `.ruff.toml` if preferred.

---

## 4. `flake8` — Traditional Linter

### ✅ What It Does

* Checks for errors, unused imports, styling violations
* Often used in older codebases

### 📦 Installation

```bash
pip install flake8
```

### ⚙️ Usage

```bash
flake8 script.py
```

### 🔧 Configuration

Use `.flake8` or include settings in `setup.cfg`

```ini
[flake8]
max-line-length = 88
exclude = .git,__pycache__,docs
```

---

## 5. `isort` — Import Sorter

### ✅ What It Does

* Automatically sorts imports into standard groups
* Keeps imports clean, deduplicated, and PEP8-compliant

### 📦 Installation

```bash
pip install isort
```

### ⚙️ Usage

```bash
isort script.py
```

### 🔧 Configuration

Add to `pyproject.toml`:

```toml
[tool.isort]
profile = "black"
```

---

## 📊 Tool Comparison

| Tool     | Type               | Auto-fix | Linting | Formatting | Speed        |
| -------- | ------------------ | -------- | ------- | ---------- | ------------ |
| `black`  | Formatter          | ✅ Yes    | ❌ No    | ✅ Yes      | ⚡ Fast       |
| `pylint` | Linter             | ❌ No     | ✅ Yes   | ❌ No       | 🐢 Slower    |
| `ruff`   | Linter + Formatter | ✅ Yes    | ✅ Yes   | ✅ Yes      | 🚀 Very Fast |
| `flake8` | Linter             | ❌ No     | ✅ Yes   | ❌ No       | ⚡ Fast       |
| `isort`  | Import Formatter   | ✅ Yes    | ❌ No    | ✅ Yes      | ⚡ Fast       |

---

## 🔁 Bonus: Using with Pre-Commit Hooks

### 📦 Installation

```bash
pip install pre-commit
```

### 📄 Create `.pre-commit-config.yaml`

```yaml
repos:
  - repo: https://github.com/psf/black
    rev: stable
    hooks:
      - id: black

  - repo: https://github.com/pre-commit/mirrors-pylint
    rev: v3.1.0
    hooks:
      - id: pylint

  - repo: https://github.com/charliermarsh/ruff-pre-commit
    rev: v0.4.0
    hooks:
      - id: ruff

  - repo: https://github.com/pre-commit/mirrors-isort
    rev: v5.12.0
    hooks:
      - id: isort
```

### 🔧 Usage

```bash
pre-commit install
pre-commit run --all-files
```

---

## 📘 Best Practices

* Use `black` for consistent formatting
* Use `ruff` for both linting and formatting in fast projects
* Use `pylint` when you need deep code analysis and scoring
* Combine with `pre-commit` to enforce standards before pushing code
* Use `isort` alongside `black` to keep imports clean

> ✅ Pick the tools that match your workflow and team preferences!
