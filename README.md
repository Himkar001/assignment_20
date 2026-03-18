# Assignment 20 – AM & PM Sessions

## Overview

This repository contains the complete work for Assignment 20, divided into AM and PM sessions. The assignment focuses on strengthening Python fundamentals, object-oriented programming, and statistical concepts with practical implementation and AI-assisted analysis.

---

# AM SESSION

## Part A – Python Implementation

### 1. List Operations using Loops

#### (a) Maximum and Minimum Element

```python
lst = [4, 7, 2, 9, 1, 5]

max_val = lst[0]
min_val = lst[0]

for i in lst:
    if i > max_val:
        max_val = i
    if i < min_val:
        min_val = i

print("Maximum:", max_val)
print("Minimum:", min_val)
```

**Output:**

```
Maximum: 9
Minimum: 1
```

This was implemented without using built-in functions like `max()` or `min()`, helping to understand iteration logic clearly.

---

#### (b) Frequency Count

```python
lst = [1, 2, 2, 3, 1, 4, 2]

freq = {}

for i in lst:
    if i in freq:
        freq[i] = freq[i] + 1
    else:
        freq[i] = 1

print("Frequency:", freq)
```

**Output:**

```
Frequency: {1: 2, 2: 3, 3: 1, 4: 1}
```

This demonstrates manual dictionary construction and counting logic.

---

### 2. While Loop Operations

#### (a) Reverse a Number

```python
num = 123
rev = 0

while num > 0:
    digit = num % 10
    rev = rev * 10 + digit
    num = num // 10

print("Reversed:", rev)
```

**Output:**

```
Reversed: 321
```

---

#### (b) Palindrome Check

```python
num = 121
original = num
rev = 0

while num > 0:
    digit = num % 10
    rev = rev * 10 + digit
    num = num // 10

if original == rev:
    print("Palindrome")
else:
    print("Not Palindrome")
```

**Output:**

```
Palindrome
```

---

### 3. Tuples and Dictionary

#### (a) Convert Tuple List to Dictionary

```python
tuple_list = [("a", 1), ("b", 2), ("c", 3)]

result = {}

for item in tuple_list:
    key = item[0]
    value = item[1]
    result[key] = value

print("Dictionary:", result)
```

**Output:**

```
Dictionary: {'a': 1, 'b': 2, 'c': 3}
```

---

#### (b) Key with Highest Value

```python
d = {"a": 10, "b": 25, "c": 15}

max_key = None
max_val = None

for key in d:
    if max_val is None or d[key] > max_val:
        max_val = d[key]
        max_key = key

print("Highest Value Key:", max_key)
```

**Output:**

```
Highest Value Key: b
```

---

### 4. Function using *args

```python
def calc(*args):
    total = 0
    count = 0

    for i in args:
        total += i
        count += 1

    avg = total / count if count != 0 else 0
    return total, avg

print(calc(10, 20, 30))
```

**Output:**

```
(60, 20.0)
```

---

### 5. Function using **kwargs

```python
def top_student(**kwargs):
    max_name = None
    max_marks = None

    for name in kwargs:
        if max_marks is None or kwargs[name] > max_marks:
            max_marks = kwargs[name]
            max_name = name

    return max_name, max_marks

print(top_student(Aman=85, Ravi=92, Sita=88))
```

**Output:**

```
('Ravi', 92)
```

---

## Part B – Custom Vector Class

```python
class Vector:
    def __init__(self, values):
        self.values = values

    def __add__(self, other):
        result = []
        for i in range(len(self.values)):
            result.append(self.values[i] + other.values[i])
        return Vector(tuple(result))

    def __sub__(self, other):
        result = []
        for i in range(len(self.values)):
            result.append(self.values[i] - other.values[i])
        return Vector(tuple(result))

    def __mul__(self, scalar):
        result = []
        for i in range(len(self.values)):
            result.append(self.values[i] * scalar)
        return Vector(tuple(result))

    def __repr__(self):
        return f"Vector{self.values}"
```

### Test

```python
v1 = Vector((1, 2, 3))
v2 = Vector((4, 5, 6))

print(v1)
print(v2)
print(v1 + v2)
print(v1 - v2)
print(v1 * 3)
```

**Output:**

```
Vector(1, 2, 3)
Vector(4, 5, 6)
Vector(5, 7, 9)
Vector(-3, -3, -3)
Vector(3, 6, 9)
```

---

## Part C – Interview Ready

### Difference between *args and **kwargs

* *args: stores positional arguments as tuple
* **kwargs: stores keyword arguments as dictionary

### Student Class

```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

    def calculate_grade(self):
        if self.marks >= 80:
            return "A"
        elif self.marks >= 60:
            return "B"
        else:
            return "C"

    def __str__(self):
        return f"Name: {self.name}, Marks: {self.marks}, Grade: {self.calculate_grade()}"
```

**Output:**

```
Name: Himkar, Marks: 85, Grade: A
```

---

### Dunder Methods

Dunder methods are special methods used to define object behavior.
Examples include `__init__`, `__str__`, and `__add__`.

---

## Part D – AI Task

Prompt:
Explain Python dunder methods with examples.

Evaluation:

* Explanation was correct
* Code worked properly
* Minor improvement: add error handling

---

# PM SESSION

## Part A – Statistical Implementation

```python
import numpy as np

np.random.seed(42)
data = np.random.normal(loc=50, scale=10, size=1000)

mean = sum(data) / len(data)
variance = sum((x - mean) ** 2 for x in data) / len(data)
std = variance ** 0.5

print(mean, variance, std)
```

**Output:**
Mean ≈ 50, Variance ≈ 100, Std ≈ 10

---

### Z-Score

```python
z_scores = [(x - mean) / std for x in data]
```

Output shows mean ≈ 0 and std ≈ 1 after normalization.

---

### Hypothesis Testing

```python
mu = 50
n = len(data)

z = (mean - mu) / (std / (n ** 0.5))

if abs(z) > 1.96:
    print("Reject H0")
else:
    print("Fail to reject H0")
```

**Result:**
Fail to reject H0

---

## Part B – Concepts

* Normal distribution: mean and std can vary
* Standard normal: mean = 0, std = 1
* Used for comparison and scaling

---

## Part C – Interview Concepts

### Z-Score Function

```python
def z_score(x, mean, std):
    return (x - mean) / std
```

---

### Hypothesis Testing

* H0: no effect
* H1: there is an effect
* p-value determines decision

---

## Part D – AI Task

Prompt:
Explain normal distribution, Z-score and hypothesis testing.

Evaluation:

* Concepts were correct
* Code was runnable
* Minor improvements suggested

---

## Final Conclusion

This assignment combines programming and statistics effectively. The AM session builds strong Python fundamentals, while the PM session focuses on statistical reasoning and data analysis. Together, they provide a well-rounded understanding of both coding and analytical thinking.
