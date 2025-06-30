+++
date = '2025-06-29'
title = 'PyUnit'
+++

# PyUnit

> “Testing leads to failure, and failure leads to understanding.”

---

## What is PyUnit?

PyUnit is the built-in testing framework in Python.

- It is also called `unittest` in Python code.
- It helps you test your code automatically by checking if functions work as expected.

You do not need to install anything to use it. Just import `unittest`.

---

## Advantages of PyUnit

- **Built-in**: No need to install anything. It is included in the Python standard library.
- **Structured**: Class-based organization is ideal for large, complex projects.
- **IDE Compatibility**: Works smoothly with IDEs like PyCharm, VS Code, etc.
- **Secure for Restricted Systems**: Often allowed in environments where third-party libraries are not permitted.

---

## Disadvantages of PyUnit

- **Verbose Syntax**: Requires more lines of code and setup compared to Pytest.
- **Less Pythonic**: Uses Java-style assertions (`self.assertEqual`) instead of Python’s `assert`.
- **Slower Test Writing**: More boilerplate code means slower development of tests.
- **Manual Discovery**: Tests must be manually added or executed via `unittest.main()` unless integrated with a test runner.

---

## What Is the Difference Between Pytest and PyUnit?

PyUnit, also known as `unittest`, is the built-in unit testing framework that comes with Python.  
On the other hand, **Pytest** is a third-party Python testing framework that is more modern, flexible, and concise.

Here is a detailed comparison between the PyUnit and Pytest:

### 🔹 Installation

- **PyUnit**: Does not require any installation as it is part of the Python standard library.
- **Pytest**: Needs to be installed separately using `pip install pytest`.

### 🔹 Syntax Simplicity

- **Pytest**: Uses plain functions and simple `assert` statements, making it easier and quicker to write tests.
- **PyUnit**: More verbose — requires defining test methods within classes and using assertion methods like `self.assertEqual`.

### 🔹 Test Discovery

- **Pytest**: Automatically discovers all test files and functions that follow a naming pattern (e.g., `test_*.py`).
- **PyUnit**: Test discovery is more manual — you need to explicitly call `unittest.main()` or use additional tools to discover and run tests.

### 🔹 Readability and Maintenance

- **Pytest**: Easier to read and maintain due to concise syntax.
- **PyUnit**: Can become bulky, especially for large projects, because of boilerplate code.

### 🔹 Industry Usage

- **Pytest**: More widely used in industry for modern, fast-paced development.
- **PyUnit**: Still used in large enterprises with strict security and software policies, or in academic environments.

---

## Example: PyUnit in Action

Let’s now explain the functionality of PyUnit with the help of an example.

---

###  Step 1: Create a Folder

Create a folder named `PyUnit`.

---

###  Step 2: Create Two Files

Inside the folder, create two Python files:

- One file (`calculator.py`) will store the functions.
- The other (`test_calculator.py`) will store the test cases.

---

###  `calculator.py`

```python
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b
```

---

###  `test_calculator.py`

```python
import unittest
from calculator import add, subtract, multiply, divide

class TestCalculator(unittest.TestCase):

    def test_add(self):
        self.assertEqual(add(3, 2), 5)

    def test_subtract(self):
        self.assertEqual(subtract(5, 2), 3)

    def test_multiply(self):
        self.assertEqual(multiply(4, 3), 12)

    def test_divide(self):
        self.assertEqual(divide(10, 2), 5)

    def test_divide_by_zero(self):
        with self.assertRaises(ValueError):
            divide(10, 0)

# Run all tests
if __name__ == '__main__':
    unittest.main()
```

---

###  Explanation of the Code

- `import unittest`: Imports Python’s built-in unit testing library.
- `from calculator import ...`: Imports functions to be tested.
- `class TestCalculator(unittest.TestCase)`: Test class inheriting from `unittest.TestCase`.
- Methods starting with `test_`: Are discovered and executed as tests.
- `if __name__ == '__main__'`: Ensures the tests run only if the file is executed directly.

---

###  Step 3: Run the Tests

```bash
python3 test_calculator.py
```

---

###  Output

```bash
.....
----------------------------------------------------------------------
Ran 5 tests in 0.000s

OK
```

![Example Image](/images/ex1.pnj)

- Each `.` means a test passed.
- All functions were tested successfully.

---

##  Testing Files with Errors

Let’s introduce bugs and see how PyUnit detects them.

---

###  `calculator.py` (same as before)

```python
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b
```

---

###  `test_calculator.py` (with intentional errors)

```python
import unittest
from calculator import add, subtract, multiply, divide

class TestCalculator(unittest.TestCase):

    def test_add(self):
        self.assertEqual(add(3, 2), 6)  # Incorrect expected result

    def test_subtract(self):
        self.assertEqual(subtract(5, 2), 2)  # Incorrect expected result

    def test_multiply(self):
        self.assertEqual(multiply(4, 3), 12)

    def test_divide(self):
        self.assertEqual(divide(10, 2), 5)

    def test_divide_by_zero(self):
        with self.assertRaises(ValueError):
            divide(10, 0)

# Run all tests
if __name__ == '__main__':
    unittest.main()
```

---

###  Output

```bash
F...F
======================================================================
FAIL: test_add (__main__.TestCalculator)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/home/khansa/PyUnit/test_calculator.py", line 9, in test_add
    self.assertEqual(add(3, 2), 6)
AssertionError: 5 != 6

======================================================================
FAIL: test_subtract (__main__.TestCalculator)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/home/khansa/PyUnit/test_calculator.py", line 12, in test_subtract
    self.assertEqual(subtract(5, 2), 2)
AssertionError: 3 != 2

----------------------------------------------------------------------
Ran 5 tests in 0.000s

FAILED (failures=2)
```

![Example Image](/images/ex2.png)

- The output clearly identifies which tests failed and why.
- This demonstrates PyUnit's ability to catch bugs early.

---

##  Final Thoughts

We explored how PyUnit helps us test our code effectively by writing simple test cases.  
We looked at both passing and failing examples, showing how testing can help catch errors early and improve code quality.

> **"Code without tests is broken by design."**

---

**Thank You!**
