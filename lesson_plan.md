# 🧠 Lesson Plan: Data Visualization with NumPy, Pandas & Matplotlib 

### **Goal:**

Learn how to visualize real-world data using Matplotlib and Pandas, starting from numerical operations (NumPy) to creating business-style insights with charts.

---

### **Lesson 1: NumPy Refresher — Working with Data**

**Objective:** Master numerical operations and data generation for visualization.
**Topics:**

* What is NumPy and why it’s used for numerical data
* Creating arrays: `np.array()`, `np.arange()`, `np.linspace()`
* Array operations: addition, subtraction, mean, std, etc.
* Indexing, slicing, reshaping
* Generating random data: `np.random.randn()`, `np.random.randint()`

**Practice:**

* Create an array of x values from 0 to 10 and compute y = x²
* Generate 100 random values and calculate mean & std deviation

---

### **Lesson 2: Pandas Basics — Working with Real Tabular Data**

**Objective:** Learn to load, explore, and prepare business datasets for visualization.
**Topics:**

* What is Pandas and why it’s used with Matplotlib
* Series and DataFrames
* Loading data from CSV: `pd.read_csv()`
* Inspecting data: `.head()`, `.info()`, `.describe()`
* Selecting columns and rows (`.loc`, `.iloc`)
* Basic statistics: `.mean()`, `.max()`, `.min()`

**Practice Dataset (from Kaggle):**
🔹 **Dataset:** *Sales Data Analysis*
📍 **Search:** “Supermarket Sales Dataset” or “Retail Sales Dataset”
👉 Example: [Supermarket Sales - Kaggle](https://www.kaggle.com/datasets/aungpyaeap/supermarket-sales)
**Tasks:**

* Load the CSV with Pandas
* View first few rows and summary statistics
* Find the top 5 cities by total sales

---

### **Lesson 3: Matplotlib Basics — Plotting with `pyplot`**

**Objective:** Create and customize basic line charts for trend visualization.
**Topics:**

* `import matplotlib.pyplot as plt`
* Basic line plot: `plt.plot(x, y)`
* Labels, title, legend, grid
* Changing line style, color, and markers
* Displaying and saving plots (`plt.show()`, `plt.savefig()`)

**Practice Dataset (from Kaggle):**
🔹 **Dataset:** *Stock Prices or Business Trends*
📍 **Search:** “Apple Stock Data”, “Tesla Stock Price”, or “Amazon Stock History”
👉 Example: [Apple Stock Data - Kaggle](https://www.kaggle.com/datasets/henriqueferreira/stock-prices)
**Tasks:**

* Load the CSV and plot `Date` vs. `Close` price
* Add labels, title, and grid
* Highlight trends with colors or markers

---

### **Lesson 4: Multiple & Subplots**

**Objective:** Compare multiple visualizations in one figure.
**Topics:**

* `plt.subplot(rows, cols, index)`
* `plt.subplots()` and axes objects
* Adjusting layout: `plt.tight_layout()`

**Practice Dataset (from Kaggle):**
🔹 **Dataset:** *Sales Data by Product or Category*
📍 **Search:** “E-commerce Sales Dataset”
👉 Example: [E-commerce Data - Kaggle](https://www.kaggle.com/datasets/carrie1/ecommerce-data)
**Tasks:**

* Create a 2x2 grid comparing monthly sales, profits, quantity, and customer count

---

### **Lesson 5: Common Plot Types**

**Objective:** Master key visualization types for business insights.
**Topics:**

* **Bar chart:** `plt.bar()`
* **Scatter plot:** `plt.scatter()`
* **Pie chart:** `plt.pie()`
* **Histogram:** `plt.hist()`

**Practice Dataset (from Kaggle):**
🔹 **Dataset:** *Marketing or Customer Analysis*
📍 **Search:** “Customer Personality Analysis”
👉 Example: [Customer Personality Analysis - Kaggle](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)
**Tasks:**

* Bar chart: total spending per category
* Pie chart: customer types by region
* Histogram: income distribution
* Scatter plot: income vs. spending score

---

### **Lesson 6: Styling & Presentation**

**Objective:** Make your charts clean, readable, and presentation-ready.
**Topics:**

* Figure size & DPI (`plt.figure(figsize=(w,h))`)
* Colors, transparency (`alpha`), annotations (`plt.text()`)
* Grid lines, limits, tick customization (`plt.xlim`, `plt.xticks`)
* Adding company logo or brand colors (optional)

**Practice:**

* Recreate one of your earlier business charts with improved styling and annotations (e.g., “Monthly Sales Trend”)

---

### **Lesson 7: Mini Project — Business Insights Dashboard**

**Objective:** Combine Pandas, NumPy, and Matplotlib to analyze a real business dataset.
**Dataset (Kaggle):**
🔹 [Supermarket Sales Dataset](https://www.kaggle.com/datasets/aungpyaeap/supermarket-sales)

**Project Tasks:**

* Load and clean data
* Use NumPy to calculate averages, max/min sales, and growth rate
* Plot:

  * Line chart: monthly sales trend
  * Bar chart: top 5 products
  * Pie chart: sales by city
* Add annotations for key insights (e.g., “Highest Sales in March”)
* Save the figure as a professional report image or PDF