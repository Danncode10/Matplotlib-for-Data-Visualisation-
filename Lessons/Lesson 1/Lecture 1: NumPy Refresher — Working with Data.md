# Lesson 1: NumPy Refresher — Working with Data

### 📘 Lesson 1 Breakdown:

**Part 1:** What NumPy is and why it’s important for working with data
**Part 2:** Creating arrays — `np.array()`, `np.arange()`, and `np.linspace()`
**Part 3:** Array operations — performing math, finding mean, standard deviation, etc.
**Part 4:** Indexing, slicing, reshaping, and generating random data

At the end, we’ll do the **Practice Tasks**:

* Create `x` from 0 to 10 and compute `y = x²`
* Generate 100 random values and calculate their mean and standard deviation

---

### 🧩 Part 1: Understanding NumPy

**NumPy** stands for **Numerical Python** — it’s a library that helps you work with **numbers and large sets of data efficiently**.
In short, it’s like a super-powered version of Python lists, specially made for **math and data operations**.

---

### 🧠 Why NumPy is Important

Let’s look at it step-by-step:

1. **Python lists are slow** for heavy numerical work.

   * If you try to add or multiply thousands of numbers using lists, Python does it one-by-one.
   * NumPy, on the other hand, performs these operations **in bulk**, directly at the hardware (C-level) speed.

2. **NumPy arrays** are more efficient.

   * A **NumPy array** stores data in a continuous block of memory, which makes calculations faster and smoother.
   * This is crucial when working with datasets, scientific calculations, or preparing data for visualization.

3. **Foundation for data tools.**

   * Libraries like **Pandas**, **Matplotlib**, and **Scikit-learn** are all built on top of NumPy.
   * So, understanding NumPy gives you a strong foundation for almost every data-related task.

---

### 💡 Real-life Analogy

Imagine you’re a chef preparing food:

* A **Python list** is like cooking each dish separately — slow but simple.
* A **NumPy array** is like using a big industrial machine that cooks everything at once — fast, efficient, and scalable.

---

So, in simple terms:

> NumPy = speed + efficiency + foundation for data analysis.

---

### 🧱 Part 2: Creating Arrays in NumPy

Before you can do any data visualization or calculations, you first need **data** — and that’s where **arrays** come in.

An **array** in NumPy is like a **grid or list of numbers** that can be one-dimensional (like a line of numbers) or multi-dimensional (like a table or matrix).

---

### 🧩 1. `np.array()` – Convert lists into arrays

This is the simplest way to create a NumPy array.

```python
import numpy as np

data = [1, 2, 3, 4, 5]
arr = np.array(data)

print(arr)
```

**Output:**

```
[1 2 3 4 5]
```

✅ This takes a normal Python list and turns it into a **NumPy array**, allowing you to perform fast math operations later.

---

### 🧩 2. `np.arange()` – Create sequences of numbers

This function works like Python’s `range()`, but it creates a **NumPy array** instead.

```python
arr = np.arange(0, 10, 2)
print(arr)
```

**Output:**

```
[0 2 4 6 8]
```

Here:

* `0` → start
* `10` → stop (exclusive)
* `2` → step size

So, it gives you evenly spaced numbers from 0 to 8 with a step of 2.

---

### 🧩 3. `np.linspace()` – Create evenly spaced values

This is useful when you want a specific **number of points** between two numbers.

```python
arr = np.linspace(0, 10, 5)
print(arr)
```

**Output:**

```
[ 0.   2.5  5.   7.5 10. ]
```

It divides the range from **0 to 10** into **5 equal parts**.
This is often used in **plotting**, because it gives smooth, evenly spaced x-values.

---

### 🧠 Summary

| Function                        | Purpose                 | Example Output          |
| ------------------------------- | ----------------------- | ----------------------- |
| `np.array()`                    | Convert list to array   | `[1 2 3 4 5]`           |
| `np.arange(start, stop, step)`  | Sequence with step size | `[0 2 4 6 8]`           |
| `np.linspace(start, stop, num)` | Evenly spaced values    | `[0.  2.5 5.  7.5 10.]` |

---

## ⚙️ Part 3: Array Operations — Doing Math the Easy Way

NumPy arrays let you perform **math operations on entire sets of numbers at once** — no need for loops!

Let’s see how this works.

---

### 🧮 1. Basic Math Operations

Suppose we have this array:

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])
```

Now look what you can do:

```python
print(arr + 2)   # Add 2 to each element
print(arr * 3)   # Multiply each element by 3
print(arr ** 2)  # Square each element
```

**Output:**

```
[3 4 5 6 7]
[ 3  6  9 12 15]
[ 1  4  9 16 25]
```

➡️ You didn’t have to use any loops — NumPy handles everything at once.
This is called **vectorized computation** — it’s one of NumPy’s superpowers.

---

### 🧠 2. Array-to-Array Operations

You can also perform operations between two arrays **element by element**:

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(a + b)
print(a * b)
```

**Output:**

```
[5 7 9]
[ 4 10 18]
```

So, NumPy automatically adds or multiplies corresponding elements together.

---

### 📊 3. Useful Statistical Functions

NumPy also has built-in math tools — no need to write formulas yourself!

```python
arr = np.array([10, 20, 30, 40, 50])

print(np.mean(arr))   # Average value
print(np.std(arr))    # Standard deviation
print(np.min(arr))    # Minimum value
print(np.max(arr))    # Maximum value
```

**Output:**

```
30.0
14.1421356237
10
50
```

✅ These functions are extremely helpful when you start working with **real-world data** later.

---

### 🧩 4. Example — Quick Practice

Let’s say we have monthly sales:

```python
sales = np.array([120, 150, 100, 180, 200])
```

You can instantly get insights like:

```python
print("Average Sales:", np.mean(sales))
print("Best Month Sales:", np.max(sales))
print("Worst Month Sales:", np.min(sales))
```

---

💡 **Takeaway:**
NumPy lets you do in **one line** what would take **many lines** with normal Python lists — fast and clean!

---

## 🧩 Part 4: Indexing, Slicing, Reshaping & Random Data

When you start handling large datasets, you often need to **pick specific values**, **reshape data**, or **generate random samples**.
NumPy makes this incredibly easy.

---

### 🔹 1. Indexing — Accessing Specific Elements

Just like lists, arrays use **zero-based indexing**:

```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50])
print(arr[0])   # First element
print(arr[3])   # Fourth element
```

**Output:**

```
10
40
```

For **2D arrays**, use two indices: `[row, column]`.

```python
matrix = np.array([[1, 2, 3],
                   [4, 5, 6],
                   [7, 8, 9]])

print(matrix[1, 2])  # Row 1, Column 2 → 6
```

---

### 🔹 2. Slicing — Extracting a Range

You can grab parts of an array using slicing:
`array[start:end]` (end is *exclusive*)

```python
arr = np.array([0, 1, 2, 3, 4, 5, 6])
print(arr[2:5])  # Elements from index 2 to 4
```

**Output:**

```
[2 3 4]
```

You can even skip values:

```python
print(arr[::2])  # Every 2nd element
```

**Output:**

```
[0 2 4 6]
```

---

### 🔹 3. Reshaping — Changing the Structure

You can turn a 1D array into a 2D array (and vice versa).

```python
arr = np.arange(1, 7)
reshaped = arr.reshape(2, 3)
print(reshaped)
```

**Output:**

```
[[1 2 3]
 [4 5 6]]
```

💡 Very useful when you’re preparing data for machine learning or visualizations.

---

### 🎲 4. Generating Random Data

NumPy can create random numbers for testing, simulations, or charts.

**a. Random integers:**

```python
random_ints = np.random.randint(1, 10, size=5)
print(random_ints)
```

Output might be:

```
[4 1 9 2 7]
```

**b. Random normal distribution (useful for charts):**

```python
random_normal = np.random.randn(5)
print(random_normal)
```

Output example:

```
[ 0.45 -1.23  0.67  0.12  -0.89]
```

✅ `randn()` generates values centered around **0**, often used to simulate *real-world noise* in data.

---

### 🧠 Summary

| Concept  | Description          | Example              |
| -------- | -------------------- | -------------------- |
| Indexing | Access elements      | `arr[1] → 20`        |
| Slicing  | Extract ranges       | `arr[2:5] → [2 3 4]` |
| Reshape  | Change shape         | `arr.reshape(2,3)`   |
| Random   | Generate random data | `np.random.randn(5)` |

---

### 🧮 Practice Time

Try these mini-tasks:

1. Create an array `x` from 0 to 10 and compute `y = x**2`
2. Generate 100 random values using `np.random.randn(100)`
3. Compute their **mean** and **standard deviation**
