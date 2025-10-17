# Lesson 5: Common Plot Types

## **Part 1: Bar Chart** with **NumPy**.

---

### Step 1 — Our Raw Data

```python
import numpy as np

# Each row = [Category ID, Amount spent]
# Category IDs: 0 = Groceries, 1 = Clothing, 2 = Electronics
data = np.array([
    [0, 150], [1, 200], [2, 300],
    [0, 100], [1, 150], [2, 400],
    [0, 200], [1, 100], [2, 100]
])

categories = np.array(['Groceries', 'Clothing', 'Electronics'])
```

So our `data` looks like this:

| Category | Amount |
| -------- | ------ |
| 0        | 150    |
| 1        | 200    |
| 2        | 300    |
| 0        | 100    |
| 1        | 150    |
| 2        | 400    |
| 0        | 200    |
| 1        | 100    |
| 2        | 100    |

We want **total spending per category**.

---

### Step 2 — Calculate Totals **Step by Step**

Instead of a one-liner, let’s do it **slowly**:

```python
# Step 2a: Create an array to store totals, one for each category
totals = np.zeros(len(categories))  # [0, 0, 0]

# Step 2b: Go through each category
for i in range(len(categories)):
    # Find all rows in 'data' where category matches i
    category_rows = data[data[:,0] == i]
    
    # Take the second column (Amount) and sum it
    category_total = category_rows[:,1].sum()
    
    # Store in totals
    totals[i] = category_total

print(totals)
```

**Explanation of each line:**

1. `totals = np.zeros(len(categories))` → Make an array `[0,0,0]` to store totals.
2. `for i in range(len(categories)):` → Loop over category IDs `0,1,2`.
3. `category_rows = data[data[:,0] == i]` → **Filter rows** where category ID equals `i`.

   * `data[:,0]` → All category IDs
   * `data[:,0] == i` → Boolean array: True for rows with category `i`
   * `data[...]` → Select only those rows
4. `category_total = category_rows[:,1].sum()` → Take the **Amount column** (column 1) and sum it.
5. `totals[i] = category_total` → Save total for this category.

✅ Output:

```
[450. 450. 800.]
```

* 450 spent on Groceries
* 450 spent on Clothing
* 800 spent on Electronics


## Loop Explained in details
---

### Step 1 — What is `data`?

```python
data = np.array([
    [0, 150],
    [1, 200],
    [2, 300],
    [0, 100],
    [1, 150],
    [2, 400],
    [0, 200],
    [1, 100],
    [2, 100]
])
```

* Column 0 → Category ID (0=Groceries, 1=Clothing, 2=Electronics)
* Column 1 → Amount spent

Think of it as a **table**:

| Category | Amount |
| -------- | ------ |
| 0        | 150    |
| 1        | 200    |
| 2        | 300    |
| 0        | 100    |
| 1        | 150    |
| 2        | 400    |
| 0        | 200    |
| 1        | 100    |
| 2        | 100    |

We want to **sum amounts for each category**.

---

### Step 2 — What `data[:,0] == i` does

* `data[:,0]` → Take **all rows** from column 0 (category IDs):

  ```
  [0, 1, 2, 0, 1, 2, 0, 1, 2]
  ```
* `data[:,0] == i` → Compare every value to the current category `i`.
  For example, if `i = 0` (Groceries), we get:

  ```
  [True, False, False, True, False, False, True, False, False]
  ```
* This is called a **Boolean array** — True where the row belongs to category `i`.

---

### Step 3 — Selecting rows with `data[...]`

```python
category_rows = data[data[:,0] == i]
```

* This says: “Give me **all rows of `data`** where the category is `i`.”
* Using our example (`i = 0`), `category_rows` becomes:

```
[[0, 150],
 [0, 100],
 [0, 200]]
```

✅ These are all the purchases for **Groceries**.

---

### Step 4 — Sum the amounts

```python
category_total = category_rows[:,1].sum()
```

* `category_rows[:,1]` → Take **all amounts** (column 1) for this category:

  ```
  [150, 100, 200]
  ```
* `.sum()` → Add them together: `150 + 100 + 200 = 450`

---

### Step 5 — Store in totals

```python
totals[i] = category_total
```

* Saves the sum for category `i` in the `totals` array.

After looping through all categories, `totals` becomes:

```
[450, 450, 800]
```

* 450 = Groceries
* 450 = Clothing
* 800 = Electronics


---

### Step 3 — Plot Bar Chart

```python
import matplotlib.pyplot as plt

plt.bar(categories, totals, color='skyblue')
plt.xlabel('Category')
plt.ylabel('Total Spending ($)')
plt.title('Total Spending per Category')
plt.show()
```

### **Basic Syntax**

```python
plt.bar(x, height, color='blue', width=0.8)
```

**Parameters explained clearly:**

1. **`x`** → The labels for each bar (categories on the x-axis)

   * Example: `['Groceries', 'Clothing', 'Electronics']`
   * Each label gets **one bar**.

2. **`height`** → The value for each bar (how tall the bar is)

   * Example: `[450, 450, 800]`
   * Higher numbers → taller bars.

3. **`color`** *(optional)* → The color of the bars

   * Example: `'skyblue'`, `'red'`, `'#FF5733'`
   * Default is blue if not specified.

4. **`width`** *(optional)* → Width of each bar

   * Default = 0.8 (80% of the space allocated for each bar)
   * Can make bars thinner (`0.5`) or thicker (`1.0`).


## 🥧 Part 2: Pie Charts

### 🎯 **Goal**

Learn how to make a simple **pie chart** using Matplotlib, with clean NumPy data behind it — no confusing parts, just the essentials.

---

### **1. What a Pie Chart Is**

A **pie chart** shows **parts of a whole** — like how your total spending is split between categories.

Think of it like a pizza 🍕:

* The whole pizza = 100% (your total spending)
* Each slice = one category’s share of that total

---

### **2. Basic Syntax**

```python
plt.pie(x, labels=None, colors=None, autopct=None)
```

Let’s explain each part **simply**:

| Parameter | Meaning                               | Example                                    |
| --------- | ------------------------------------- | ------------------------------------------ |
| `x`       | The values (numbers) for each slice   | `[450, 450, 800]`                          |
| `labels`  | The names of each slice               | `['Groceries', 'Clothing', 'Electronics']` |
| `colors`  | Optional — pick colors for each slice | `['gold', 'skyblue', 'lightgreen']`        |
| `autopct` | Optional — show % on slices           | `'%1.1f%%'` (one decimal place)            |

---

### **3. Simple Example (with NumPy)**

```python
import numpy as np
import matplotlib.pyplot as plt

# Data
categories = np.array(['Groceries', 'Clothing', 'Electronics'])
totals = np.array([450, 450, 800])

# Create pie chart
plt.pie(
    totals,                    # Values for slices
    labels=categories,         # Names
    colors=['gold', 'skyblue', 'lightgreen'],  # Slice colors
    autopct='%1.1f%%'          # Show percent values
)

plt.title('Spending Breakdown by Category')
plt.show()
```

✅ **What happens here:**

* Each value in `totals` becomes a slice of the circle.
* Matplotlib automatically calculates each slice’s percentage.
* The numbers you see (like “30.0%”) are created by `autopct='%1.1f%%'`.

---

### **4. Key Tips**

* **Use pie charts only** when comparing a few categories (2–6). Too many slices make it messy.
* Always **make sure total values are positive** — pie charts can’t show negative or zero values.
* You can add a small **highlight** using the `explode` parameter (optional):

```python
explode = [0, 0, 0.1]  # Pop out the 3rd slice slightly
plt.pie(totals, labels=categories, explode=explode, autopct='%1.1f%%')
```

---

✅ **Summary:**

* `x` = values
* `labels` = names
* `colors` = slice colors (optional)
* `autopct` = show percentages (optional)

---

## 📊 Part 3: Histograms

### 🎯 **Goal**

Understand what a **histogram** is and how to create one using **Matplotlib + NumPy** — keeping it simple and practical.

---

### **1. What is a Histogram?**

A **histogram** shows **how data is distributed** — it groups values into *ranges* (called **bins**) and counts how many fall into each range.

🧠 Think of it like:

> Sorting people into boxes based on their age.
>
> Example bins:
>
> * 0–10 years → 4 people
> * 11–20 years → 7 people
> * 21–30 years → 12 people

Each bar represents **how many data points fall in that range**.

---

### **2. Basic Syntax**

```python
plt.hist(x, bins=None, color=None, edgecolor=None)
```

| Parameter   | Meaning                    | Example                                         |
| ----------- | -------------------------- | ----------------------------------------------- |
| `x`         | The data you want to group | `[10000, 25000, 30000, 50000, 60000]`           |
| `bins`      | Number of groups (ranges)  | `5` or `[0, 10000, 20000, 30000, 40000, 50000]` |
| `color`     | Color of bars              | `'skyblue'`                                     |
| `edgecolor` | Outline color for bars     | `'black'`                                       |

---

### **3. Example (Income Distribution)**

```python
import numpy as np
import matplotlib.pyplot as plt

# Simulate income data for 100 people
income = np.random.randint(10000, 100000, 100)

plt.hist(
    income, 
    bins=10,               # Split into 10 ranges
    color='skyblue', 
    edgecolor='black'
)

plt.xlabel('Income Range ($)')
plt.ylabel('Number of People')
plt.title('Income Distribution')
plt.show()
```

✅ **What’s happening:**

* NumPy creates 100 random income values between **10,000 and 100,000**.
* `plt.hist()` automatically counts how many incomes fall into each range (bin).
* `bins=10` means the data is grouped into 10 ranges.
* Taller bars = more people in that income range.

---

### **4. Tips**

* Increasing `bins` makes the chart **more detailed**, decreasing makes it **simpler**.
* Use histograms to understand **data patterns** (e.g., are most people low income, middle, or high?).
* You can use `.mean()` or `.median()` (NumPy functions) to compare where most data lies.

Example:

```python
print("Average income:", income.mean())
```

---

✅ **Summary:**

* **Histogram = data frequency visualization**
* **Key parameters:**

  * `x` → the data
  * `bins` → how many groups
  * `color` / `edgecolor` → visuals

---

## 🔵 Part 4: Scatter Plots

### 🎯 **Goal**

Understand how to use **scatter plots** to show the **relationship between two variables** — for example, income vs. spending score.

---

### **1. What is a Scatter Plot?**

A **scatter plot** displays data points on a **2D plane**, using:

* The **x-axis** for one variable
* The **y-axis** for another

Each point shows how those two variables relate.

🧠 Example analogy:
Imagine each person in your dataset as a **dot**.

* The x-axis = their **income**
* The y-axis = their **spending score**

If richer people tend to spend more, the dots will rise diagonally upwards.
If there’s no pattern, the dots are scattered randomly.

---

### **2. Basic Syntax**

```python
plt.scatter(x, y, color=None, marker=None)
```

| Parameter | Description                  | Example                                      |
| --------- | ---------------------------- | -------------------------------------------- |
| `x`       | Data for the horizontal axis | `income`                                     |
| `y`       | Data for the vertical axis   | `spending_score`                             |
| `color`   | Color of the dots            | `'blue'`, `'green'`, etc.                    |
| `marker`  | Shape of each point          | `'o'` (circle), `'s'` (square), `'*'` (star) |

---

### **3. Example (Income vs Spending Score)**

```python
import numpy as np
import matplotlib.pyplot as plt

# Generate sample data for 50 customers
income = np.random.randint(20000, 100000, 50)
spending_score = np.random.randint(1, 100, 50)

plt.scatter(income, spending_score, color='purple', marker='o')

plt.xlabel('Income ($)')
plt.ylabel('Spending Score')
plt.title('Income vs Spending Score')
plt.show()
```

✅ **What’s happening:**

* Each dot = one customer.
* `x` = income, `y` = spending score.
* We can observe trends:

  * If dots go upward from left to right → higher income = higher spending.
  * If dots are random → no clear relationship.

---

### **4. Bonus Tip — Adding More Information**

You can make scatter plots more insightful by using:

* **`s`** (size) to represent another variable
* **`c`** (color) to show categories

Example:

```python
ages = np.random.randint(18, 65, 50)

plt.scatter(income, spending_score, c=ages, s=ages, cmap='viridis')
plt.colorbar(label='Age')
plt.xlabel('Income ($)')
plt.ylabel('Spending Score')
plt.title('Income vs Spending Score (Colored by Age)')
plt.show()
```

Now the **color** and **size** also show each person’s age — making it a richer visualization.

---

✅ **Summary:**

* **Scatter plots** help visualize *relationships* between variables.
* **Key parameters:**

  * `x` = data on the x-axis
  * `y` = data on the y-axis
  * `color`, `marker`, `s`, `cmap` = for better visuals
* Great for **finding patterns or correlations** in business data.

---

🎓 **✅ Lesson 5: Common Plot Types is finished!**
You now know:

1. **Bar Charts** — compare categories
2. **Pie Charts** — show proportions
3. **Histograms** — show data distribution
4. **Scatter Plots** — show relationships

