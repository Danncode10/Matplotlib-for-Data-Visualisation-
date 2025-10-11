# Lesson 3: Matplotlib Basics — Plotting with `pyplot`

## **Part 1: What Matplotlib Is and How to Import It**

---

### 🧩 What is Matplotlib?

**Matplotlib** is a **Python library** used to create **visual representations of data**, like line charts, bar graphs, pie charts, and more.
Think of it as Python’s version of Excel charts — but far more flexible and customizable.

It helps you **turn numbers into pictures**, so you can **see trends** and **understand data** more easily.

---

### 💡 Real-Life Example

Imagine you have data about your **daily sales** for a week:

```python
days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
sales = [200, 220, 180, 250, 300, 280, 260]
```

Just looking at the numbers doesn’t show much.
But when you **plot them on a line chart**, you can instantly see when sales go up or down.

That’s exactly what Matplotlib does — it **turns plain data into clear visuals**.

---

### ⚙️ Importing Matplotlib

You usually import the plotting module like this:

```python
import matplotlib.pyplot as plt
```

Here:
* `matplotlib` is the main library
* `.pyplot` is a **module** inside it that gives you easy plotting functions
* `plt` is a short nickname (so you can type less)

Example:

```python
import matplotlib.pyplot as plt
```

That’s it — now you’re ready to start plotting!

---

## **Part 2: Creating Your First Simple Line Plot**

---

### 📊 Step 1: Prepare Your Data

Let’s start with simple numeric data — for example, the relationship between `x` and `y`.

```python
import matplotlib.pyplot as plt

x = [0, 1, 2, 3, 4, 5]
y = [0, 1, 4, 9, 16, 25]
```

Here:

* `x` represents input values (like time or days)
* `y` represents output values (like sales or results)
* In this case, each `y` is the square of `x` (so it’ll form a curve when plotted)

---

### 📈 Step 2: Create a Basic Line Plot

Now, we can visualize it:

```python
plt.plot(x, y)
plt.show()
```

When you run this:

* `plt.plot(x, y)` creates the line connecting all the (x, y) points
* `plt.show()` displays the chart in a new window or notebook output

You’ll see a **simple upward curve** because the values of `y` increase faster than `x`.

---

### 💡 What’s Happening Under the Hood

* Matplotlib automatically connects each pair of (x, y) points with straight lines.
* It also auto-scales the axes so all your data fits nicely inside the chart.
* If you run multiple `plt.plot()` commands before `plt.show()`, they’ll all appear on the same figure — perfect for comparisons later.

---

✅ **Quick Practice**
Try this:

```python
x = [1, 2, 3, 4, 5]
y = [10, 20, 25, 30, 50]

plt.plot(x, y)
plt.show()
```

You’ll get a simple line showing a rise from 10 to 50.

---


## **Part 3: Adding Labels, Title, Legend, and Grid** 
— this is where your plot starts to look professional and understandable!

---

### 🎯 Why This Matters

A graph without labels is like a map without names — you can see shapes, but you don’t know what they mean.
Adding **titles, axis labels, and legends** helps others (and you!) instantly understand the data.

---

### 🧩 Step 1: Adding Labels to the Axes

You can label your x-axis and y-axis using:

```python
plt.xlabel("X Values")
plt.ylabel("Y Values")
```

For example:

```python
import matplotlib.pyplot as plt

x = [0, 1, 2, 3, 4, 5]
y = [0, 1, 4, 9, 16, 25]

plt.plot(x, y)
plt.xlabel("X Values")
plt.ylabel("Y = X Squared")
plt.show()
```

This adds clear descriptions to each axis.

---

### 🏷️ Step 2: Adding a Title

Use:

```python
plt.title("Simple Line Plot Example")
```

Now your chart has a name — making it presentation-ready!

---

### 🧭 Step 3: Adding a Legend (for multiple lines)

If you have more than one line, a **legend** helps identify which line represents what.

Example:

```python
x = [0, 1, 2, 3, 4, 5]
y1 = [0, 1, 4, 9, 16, 25]
y2 = [0, 1, 8, 27, 64, 125]

plt.plot(x, y1, label="y = x²")
plt.plot(x, y2, label="y = x³")

plt.title("Comparison of x² and x³")
plt.xlabel("X Values")
plt.ylabel("Y Values")
plt.legend()  # 👈 This shows the legend box
plt.show()
```

Now both curves have names displayed automatically.

---

### 🧾 Step 4: Adding a Grid

A grid makes it easier to read the values in your graph:

```python
plt.grid(True)
```

It draws faint lines across the chart — especially helpful for comparing data points.

---

### ✅ Complete Example

```python
import matplotlib.pyplot as plt

x = [0, 1, 2, 3, 4, 5]
y = [0, 1, 4, 9, 16, 25]

plt.plot(x, y, label="y = x²")
plt.title("Simple Quadratic Growth")
plt.xlabel("X Axis")
plt.ylabel("Y Axis")
plt.legend()
plt.grid(True)
plt.show()
```

## **Part 4: Customizing Line Styles, Colors, and Saving Your Plot** 
— this is where your charts start looking stylish and polished! 🎨

---

### 🎨 Step 1: Changing Line Color, Style, and Markers

You can customize how your line looks right inside the `plt.plot()` function.

```python
plt.plot(x, y, color='red', linestyle='--', marker='o')
```

Here’s what each option means:

* `color='red'` → sets the line color
* `linestyle='--'` → makes the line dashed (you can also use `'-'`, `':'`, or `'-.'`)
* `marker='o'` → adds a circle marker for each data point

---

### 🎯 Example:

```python
import matplotlib.pyplot as plt

x = [0, 1, 2, 3, 4, 5]
y = [0, 1, 4, 9, 16, 25]

plt.plot(x, y, color='green', linestyle='--', marker='s', label="y = x²")
plt.title("Customized Line Style Example")
plt.xlabel("X Values")
plt.ylabel("Y Values")
plt.legend()
plt.grid(True)
plt.show()
```

✅ **Result:**
A green dashed line with square (`s`) markers — easy to follow and visually clean.

---

### 🧩 Step 2: Common Style Shortcuts

Matplotlib lets you use **format strings** — a shorthand for style:

```python
plt.plot(x, y, 'ro--')
```

This means:

* `'r'` → red
* `'o'` → circle marker
* `'--'` → dashed line

So `'bo-'` would mean a blue line with circle markers and a solid line.

---

### 💾 Step 3: Saving Your Plot

When your chart looks great, you can save it instead of just displaying it.

```python
plt.savefig("my_chart.png")
```

This saves it as a PNG image in your current folder.

You can also change the format and resolution:

```python
plt.savefig("my_chart.pdf", dpi=300)
```

* `dpi` means “dots per inch” — higher values = better quality for printing or presentations.

---

### ✅ Complete Example

```python
import matplotlib.pyplot as plt

x = [0, 1, 2, 3, 4, 5]
y = [0, 1, 4, 9, 16, 25]

plt.plot(x, y, 'ro--', label="y = x²")
plt.title("Styled Line Plot Example")
plt.xlabel("X Axis")
plt.ylabel("Y Axis")
plt.legend()
plt.grid(True)

plt.savefig("styled_plot.png", dpi=300)
plt.show()
```

Now you’ve created, styled, and saved a professional-quality chart! 🖼️

---
