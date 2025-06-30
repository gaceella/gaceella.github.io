
+++
date = '2025-06-29'
title = 'Python Unit Testing'
+++


# Python Unit Testing

> "Unit testing in Python isn't just about finding bugs—it's about building confidence in your code, one test at a time."

## What is unit testing in Python?

Unit testing means testing small parts (units) of your code like functions or methods to make sure they work correctly.

**Example**: If you write a function that adds two numbers, unit testing checks if the function gives the correct result when you test it with different inputs.

If there is an error, it will be shown in the output along with a message indicating that the test has failed. We can then check the code, fix the issue, and run the test again. When there are no more issues, the output will show that the test has passed, confirming the code is correct.

## Why do we introduce unit testing?

We introduce unit testing to:

- Catch bugs early (before the code is used).
- Automatically test the code again and again.
- Save time when updating or fixing the code.
- Make sure each function does what it’s supposed to do.

## What are its advantages?

- It finds problems early.
- It makes code easier to maintain.
- It helps when adding new features.
- It saves time during future changes.
- It works well in team projects.

## What are its disadvantages?

- Takes extra time to write tests.
- Might miss problems between functions (only tests parts).
- You need to update tests when the code changes.
- Not good for testing user interfaces or full apps alone.

## What is pytest?

`pytest` is a Python tool that helps you:

- Write unit tests easily.
- Run all your tests quickly.
- See which tests pass or fail.
- Get clear error messages.

It is one of the most popular tools for testing Python code.

## Why do we use pytest in Python?

We use pytest because:

- It is easy to write.
- It automatically finds and runs tests.
- It shows good error messages.
- You can test small or large projects with it.

## Can we do unit testing in other languages?

Yes. Almost all programming languages have their own unit testing tools.

| Language   | Tool (Framework) |
| ---------- | ---------------- |
| Python     | pytest, unittest |
| Java       | JUnit            |
| JavaScript | Jest, Mocha      |
| C++        | Google Test      |
| C#         | NUnit, xUnit     |

---

## Now we understand the concept of Python Unit Testing with the help of an example.

### STEP 1:

Create a folder named `Python_testing`.

### STEP 2:

Now create two files inside the folder:

1. `math_functions.py` (contains function definitions)
2. `test_math_functions.py` (contains unit tests)

> When creating a test file, always start the name with `test_` to help pytest recognize it.

### `math_functions.py`:

```python
# math_functions.py

def add(a, b):
    return a + b

def sub(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        return "Cannot divide by zero"
    return a / b
```

#### Explanation of the Code:

| Function | What it does                          |
| -------- | ------------------------------------- |
| add      | Adds two numbers                      |
| subtract | Subtracts second number from first    |
| multiply | Multiplies two numbers                |
| divide   | Divides first by second, handles zero |

### `test_math_functions.py` (with intentional errors):

```python
# test_math_functions.py

from math_functions import add, sub, multiply, divide

def test_add():
    assert add(2, 1) == 3
    assert add(4, 2) == 5    # correct from 5 to 6

def test_sub():
    assert sub(2, 3) == -1
    assert sub(5, 2) == 3
    assert sub(4, 3) == 2  # correct from 2 to 1

def test_multiply():
    assert multiply(2, 4) == 8
    assert multiply(9, 0) == 9  # correct from 9 to 0

def test_divide():
    assert divide(4, 2) == 2
    assert divide(7, 3) == 7 / 3     
    assert divide(5, 0) == "Cannot divide by zero"
```

#### Explanation of the Code:

| Test Function  | What it checks                          |
| -------------- | --------------------------------------- |
| test\_add      | Checks if add() gives correct results   |
| test\_subtract | Checks subtraction results              |
| test\_multiply | Checks multiplication, including by 0   |
| test\_divide   | Checks division and divide-by-zero case |

### STEP 3:

Install `pytest`:

```bash
pip3 install pytest
```



### STEP 4:

Navigate to the folder:

```bash
cd /home/khansa/Python_testing
```

or

```bash
cd path/to/name_of_folder
```

Replace the `path/to/...` with your actual path.



### STEP 5:

Run the tests:

```bash
pytest
```

### STEP 6:

Example Output:

```bash
========================================================================= test session starts ==========================================================================
platform linux -- Python 3.10.12, pytest-8.4.0, pluggy-1.6.0
rootdir: /home/khansa/Python_testing
collected 4 items                                                                                                                                                      

test_math_functions.py FFF.                                                                                                                                      [100%]

=============================================================================== FAILURES ===============================================================================
_______________________________________________________________________________ test_add _______________________________________________________________________________

def test_add():
    assert add(2, 1) == 3
>   assert add(4, 2) == 5     #correct from 5  to 6
E   assert 6 == 5
E    +  where 6 = add(4, 2)

test_math_functions.py:8: AssertionError
_______________________________________________________________________________ test_sub _______________________________________________________________________________

def test_sub():
    assert sub(2, 3) == -1
    assert sub(5, 2) == 3
>   assert sub(4, 3) == 2    #correct from 2 to 1
E   assert 1 == 2
E    +  where 1 = sub(4, 3)

test_math_functions.py:13: AssertionError
____________________________________________________________________________ test_multiply _____________________________________________________________________________

def test_multiply():
    assert multiply(2, 4) == 8
>   assert multiply(9, 0) == 9   #correct from 9 to 0
E   assert 0 == 9
E    +  where 0 = multiply(9, 0)

test_math_functions.py:17: AssertionError
======================================================================= short test summary info ========================================================================
FAILED test_math_functions.py::test_add - assert 6 == 5
FAILED test_math_functions.py::test_sub - assert 1 == 2
FAILED test_math_functions.py::test_multiply - assert 0 == 9
===================================================================== 3 failed, 1 passed in 0.08s ======================================================================
```



The output shows that there are issues in three functions: `add`, `sub`, and `multiply`. It also gives the actual output so we can fix it.

---

Now, correct the code and re-run the test.

### Updated `test_math_functions.py` (corrected):

```python
# test_math_functions.py

from math_functions import add, sub, multiply, divide

def test_add():
    assert add(2, 1) == 3
    assert add(4, 2) == 6   #correct from 5  to 6

def test_sub():
    assert sub(2, 3) == -1
    assert sub(5, 2) == 3
    assert sub(4, 3) == 1  #correct from 2 to 1

def test_multiply():
    assert multiply(2, 4) == 8
    assert multiply(9, 0) == 0  #correct from 9 to 0

def test_divide():
    assert divide(4, 2) == 2
    assert divide(7, 3) == 7 / 3     
    assert divide(5, 0) == "Cannot divide by zero"
```

### Output:

```bash
========================================================================= test session starts ==========================================================================
platform linux -- Python 3.10.12, pytest-8.4.0, pluggy-1.6.0
rootdir: /home/khansa/Python_testing
collected 4 items                                                                                                                                                      

test_math_functions.py ....                                                                                                                                      [100%]

========================================================================== 4 passed in 0.01s ===========================================================================
```



All tests passed successfully. 

---

Unit testing helps us catch bugs early and ensures that our code works as expected during development. With tools like `pytest`, writing and running tests becomes simple, efficient, and beginner-friendly.

> “Tests are not just a safety net — they’re a guide for writing better, more reliable Python code.”

**Thank You!**

