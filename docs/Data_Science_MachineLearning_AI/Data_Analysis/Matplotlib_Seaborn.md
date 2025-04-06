
# 📊 Matplotlib & Seaborn Cheatsheet

## 🔹 Introduction
**Matplotlib** and **Seaborn** are powerful Python libraries for data visualization.

- **Matplotlib**: Low-level, flexible plotting API.
- **Seaborn**: High-level interface for drawing attractive and informative statistical graphics built on top of Matplotlib.

Use Seaborn when working with DataFrames and statistical plots. Use Matplotlib for full control and custom layouts.

---

## 🔹 Installing Matplotlib & Seaborn
```sh
pip install matplotlib seaborn
```

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
```

---

## 🔹 Basic Plot with Matplotlib
```python
x = [1, 2, 3, 4, 5]
y = [10, 20, 25, 30, 40]

plt.plot(x, y, marker='o', linestyle='-', color='b', label='Line Plot')
plt.xlabel("X Axis")
plt.ylabel("Y Axis")
plt.title("Basic Line Plot")
plt.legend()
plt.grid(True)
plt.show()
```

---

## 🔹 Scatter Plot
Used to show the relationship between two numeric variables.
```python
plt.scatter(x, y, color='r', edgecolor='black')
plt.xlabel("X Axis")
plt.ylabel("Y Axis")
plt.title("Scatter Plot")
plt.grid(True)
plt.show()
```

---

## 🔹 Bar Chart
```python
categories = ['A', 'B', 'C', 'D']
values = [5, 7, 3, 8]

plt.bar(categories, values, color='skyblue', edgecolor='black')
plt.xlabel("Category")
plt.ylabel("Value")
plt.title("Bar Chart")
plt.tight_layout()
plt.show()
```

---

## 🔹 Histogram
```python
data = [10, 20, 20, 40, 50, 60, 70, 80, 90, 100]

plt.hist(data, bins=5, color='orange', edgecolor='black')
plt.xlabel("Value")
plt.ylabel("Frequency")
plt.title("Histogram")
plt.grid(axis='y')
plt.show()
```

---

## 🔹 Pie Chart (Not Recommended for Complex Data)
```python
labels = ['A', 'B', 'C']
sizes = [30, 40, 30]

plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=140)
plt.axis('equal')
plt.title("Pie Chart")
plt.show()
```

---

## 🔹 Customizing Plots
```python
plt.xticks(rotation=45)
plt.yticks(fontsize=12)
plt.axhline(y=25, color='red', linestyle='--', label='Y=25')
plt.axvline(x=3, color='green', linestyle='-.', label='X=3')
plt.legend()
```

---

## 🔹 Seaborn - Styling & Themes
```python
sns.set_theme(style="darkgrid", palette="muted")
```

- Styles: `"white"`, `"dark"`, `"whitegrid"`, `"darkgrid"`, `"ticks"`
- Palettes: `"deep"`, `"muted"`, `"pastel"`, `"bright"`, `"dark"`, `"colorblind"`

---

### ✅ Line Plot (with DataFrame)
```python
df = pd.DataFrame({'x': x, 'y': y})
sns.lineplot(data=df, x='x', y='y', marker='o')
plt.title("Seaborn Line Plot")
plt.show()
```

---

### ✅ Scatter Plot

```python
sns.scatterplot(x=x, y=y, hue=y, palette='coolwarm')
plt.title("Seaborn Scatter Plot")
plt.show()
```

---

## 🔹 Seaborn - Statistical Visualizations

### ✅ Box Plot
Used to display the distribution, central tendency, and variability of numerical data through quartiles and potential outliers.
```python
sns.boxplot(x=categories, y=values)
plt.title("Box Plot")
plt.show()
```

---

### ✅ Violin Plot
Combines a box plot and a KDE (kernel density estimate) to show both the distribution and probability density of the data.
```python
sns.violinplot(x=categories, y=values)
plt.title("Violin Plot")
plt.show()
```

---

### ✅ Heatmap (Correlation Matrix)
Used to visualize the magnitude of values in a matrix format, often for correlation or similarity between variables.
```python
import numpy as np
corr_matrix = np.random.rand(5, 5)
sns.heatmap(corr_matrix, annot=True, fmt=".2f", cmap='coolwarm', linewidths=0.5)
plt.title("Heatmap")
plt.show()
```

---

### ✅ Count Plot
Used to show the frequency (count) of categories in a categorical feature. Great for bar-like visualizations of value counts.
```python
df = sns.load_dataset("iris")
sns.countplot(x="species", data=df)
plt.title("Count Plot")
plt.show()
```

---

### ✅ Pair Plot
Creates a matrix of scatter plots to visualize pairwise relationships between multiple numeric variables, grouped by category if needed.

```python
df = sns.load_dataset("iris")
sns.pairplot(df, hue="species")
plt.title("Pair Plot")
plt.show()
```

---

### ✅ FacetGrid (Multiple Plots by Category)
Allows you to create multiple plots split by categories, useful for comparing distributions or relationships across groups.
```python
df = sns.load_dataset("iris")
g = sns.FacetGrid(df, col="species")
g.map(sns.histplot, "sepal_length")
```

---

## 🔹 Saving Figures
```python
plt.savefig("plot.png", dpi=300, bbox_inches='tight', transparent=True)
```

> ✅ Always save **before** `plt.show()` to avoid empty plots.

---

## 🔹 Matplotlib vs Seaborn (Quick Comparison)

| Feature        | Matplotlib     | Seaborn             |
|----------------|----------------|----------------------|
| Level          | Low-level      | High-level           |
| Data structure | Lists, Arrays  | Pandas DataFrames    |
| Styling        | Manual         | Built-in themes      |
| Use Case       | Custom control | Statistical plots    |

---

## 🔹 Best Practices
- Use **Seaborn** for high-level statistical plots.
- Use **Matplotlib** for advanced layout, customization, or multi-axes control.
- Set global style early: `sns.set_theme()`.
- For publication, export as **SVG** or **PDF**.
- Use `tight_layout()` or `constrained_layout()` to avoid overlap.
- Avoid 3D plots unless absolutely necessary.
- Use **FacetGrid** for grouped plots.
- Practice with built-in datasets like `iris`, `tips`, `flights`.

---

