
+++
date = '2025-06-29'
title = 'Basics of Logging'
+++



# Basics of Logging

> “Logs are like fossils: they tell the story of what happened,  
> but only if you know how to read them.”

---

## What is a Log?

A **log** is a record (like a note or message) that shows what a program or system did.  
**Example:** _User opened app at 3:00 PM._

It’s just like notifications.

---

## What is Logging?

**Logging** is the process of writing logs (messages) to a file, screen, or system to keep track of what’s happening in your program.

---

## Why Do We Use Logging?

- To debug problems (what went wrong and when?)
- To track activity (who used it and what they did)
- To monitor apps/systems (check if things are working)
- To record errors and warnings

---

## Disadvantages of Logging

- Too much logging can slow down your app
- Sensitive info (like passwords) might accidentally get logged
- Logs can take disk space if not managed
- If logs are not clear, they are hard to understand

---

## Do All Systems Have Logs by Default?

Yes, most operating systems (like Linux, Windows, macOS) automatically create logs.  
In Linux, you can check logs in your system using the command:

```bash
cd /var/log
ls
```

This folder contains information like login attempts, authentication messages, etc.

---

## Logging in Python

We can check logs with the help of the **Python `logging` module** by writing a script and running it in the terminal.  
Other languages support logging too:

- C: `syslog()`
- JavaScript: `console.log()`

If we use Python, we must use the Python Logging System.

---

## Basic Logging Example

### Step 1: Create a File

```bash
nano logging_example.py
```

### Step 2: Write and Save Code

Inside `logging_example.py`, write the following code:

```python
import logging

logging.basicConfig(
    filename='myapp.log',               
    level=logging.DEBUG,                
    format='%(asctime)s - %(levelname)s - %(message)s'  
)

logging.debug("This is a debug message.")
logging.info("The script is running fine.")
logging.warning("This is a warning.")
logging.error("Oops! Something went wrong.")
logging.critical("Critical error! Immediate attention needed.")
```

Save and exit: `Ctrl+O`, `Enter`, then `Ctrl+X`

### Step 3: Run the Script

```bash
python3 logging_example.py
```

### Step 4: View the Logs

```bash
cat myapp.log
```

### Output

```text
2025-06-12 23:58:31,099 - DEBUG - This is a debug message.
2025-06-12 23:58:31,100 - INFO - The script is running fine.
2025-06-12 23:58:31,100 - WARNING - This is a warning.
2025-06-12 23:58:31,100 - ERROR - Oops! Something went wrong.
2025-06-12 23:58:31,100 - CRITICAL - Critical error! Immediate attention needed.
```

---

## Script Explanation

### `import logging`

- Brings in Python’s built-in logging module

### `logging.basicConfig()`

Configures how logging will work:

| Setting                        | Meaning                                      |
|-------------------------------|----------------------------------------------|
| `filename='myapp.log'`        | Logs are saved to this file                  |
| `level=logging.DEBUG`         | Logs everything from DEBUG and above         |
| `format='...'`                | Each log entry includes time, level, message |

### Format Fields

- `%(asctime)s`: Date & time of the log
- `%(levelname)s`: Type of log (INFO, ERROR, etc.)
- `%(message)s`: Your custom message

### Log Levels

| Line                        | Purpose                                |
|----------------------------|----------------------------------------|
| `logging.debug(...)`       | Debugging; least severe                |
| `logging.info(...)`        | General info                           |
| `logging.warning(...)`     | Something unusual                      |
| `logging.error(...)`       | Something went wrong                   |
| `logging.critical(...)`    | Critical error needing urgent fix      |

---

## Calculator with Logging

This example demonstrates logging in a basic calculator that performs:

- Addition
- Subtraction
- Multiplication
- Division

### Calculator Script

```python
import logging

logging.basicConfig(
    filename='calc.log',          
    level=logging.INFO,            
    format='%(asctime)s - %(message)s'  
)

# Addition
def add(a, b):
    result = a + b
    logging.info(f"Added {a} + {b} = {result}")
    return result

# Subtraction
def subtract(a, b):
    result = a - b
    logging.info(f"Subtracted {a} - {b} = {result}")
    return result

# Multiplication
def multiply(a, b):
    result = a * b
    logging.info(f"Multiplied {a} * {b} = {result}")
    return result

# Division
def divide(a, b):
    if b != 0:
        result = a / b
        logging.info(f"Divided {a} / {b} = {result}")
        return result
    else:
        logging.error("Attempted division by zero")
        return "Error: Division by zero"

# Function calls
add(5, 3)
subtract(10, 4)
multiply(6, 2)
divide(8, 0)      # Logs error
divide(8, 2)
```

### Step 1: Save and Run the Script

Save the file as `calculator_logger.py`, then run:

```bash
python3 calculator_logger.py
```

### Step 2: Check the Log Output

```bash
cat calc.log
```

### Output

```text
2025-06-12 21:00:01 - Added 5 + 3 = 8  
2025-06-12 21:00:01 - Subtracted 10 - 4 = 6  
2025-06-12 21:00:01 - Multiplied 6 * 2 = 12  
2025-06-12 21:00:01 - Attempted division by zero  
2025-06-12 21:00:01 - Divided 8 / 2 = 4.0
```

---

## Conclusion

Logging records what your code does. It helps:

- Track errors
- Understand behavior
- Debug problems

Even in simple projects, **logging builds habits** that are vital in real-world development.

> “Logging is like a journal for your code — it tells the story when things go right, and explains the mystery when they don’t.”

**Thank you!**
