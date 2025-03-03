# 📊 Matplotlib & Seaborn Cheatsheet

## 🔹 Introduction
Matplotlib and Seaborn are **Python libraries** for creating **visualizations and plots**. Matplotlib provides **low-level plotting control**, while Seaborn offers **high-level statistical visualization tools**.

---

## 🔹 Installing Matplotlib & Seaborn
```sh
# Install using pip
pip install matplotlib seaborn

# Import libraries
import matplotlib.pyplot as plt
import seaborn as sns
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
plt.show()
```

---

## 🔹 Scatter Plot
```python
plt.scatter(x, y, color='r')
plt.xlabel("X Axis")
plt.ylabel("Y Axis")
plt.title("Scatter Plot Example")
plt.show()
```

---

## 🔹 Bar Chart
```python
categories = ['A', 'B', 'C', 'D']
values = [5, 7, 3, 8]
plt.bar(categories, values, color='g')
plt.xlabel("Categories")
plt.ylabel("Values")
plt.title("Bar Chart Example")
plt.show()
```

---

## 🔹 Histogram
```python
data = [10, 20, 20, 40, 50, 60, 70, 80, 90, 100]
plt.hist(data, bins=5, color='c', edgecolor='black')
plt.xlabel("Value")
plt.ylabel("Frequency")
plt.title("Histogram Example")
plt.show()
```

---

## 🔹 Customizing Plots
```python
plt.grid(True)
plt.xticks(rotation=45)
plt.yticks(fontsize=12)
plt.axhline(y=25, color='r', linestyle='--')
plt.axvline(x=3, color='g', linestyle='-.')
```

---

## 🔹 Seaborn - Basic Styling
```python
sns.set(style="darkgrid")  # Available: whitegrid, dark, ticks
```

### ✅ Line Plot
```python
sns.lineplot(x=x, y=y, marker='o')
plt.title("Seaborn Line Plot")
plt.show()
```

### ✅ Scatter Plot
```python
sns.scatterplot(x=x, y=y, hue=y, palette='coolwarm')
plt.title("Seaborn Scatter Plot")
plt.show()
```

---

## 🔹 Seaborn - Statistical Visualizations
### ✅ Box Plot
```python
sns.boxplot(x=categories, y=values)
plt.title("Seaborn Box Plot")
plt.show()
```

### ✅ Heatmap (Correlation Matrix)
```python
import numpy as np
corr_matrix = np.random.rand(5, 5)
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
plt.title("Seaborn Heatmap")
plt.show()
```

---

## 🔹 Saving Figures
```python
plt.savefig("plot.png", dpi=300, bbox_inches='tight')
```

---

## 🔹 Best Practices
- **Use Seaborn for statistical plots** and Matplotlib for **custom plots**.
- **Customize plot aesthetics** with `sns.set_style()` and `sns.set_palette()`.
- **Use appropriate color palettes** (e.g., `coolwarm`, `viridis`).
- **Save figures** before `plt.show()` to avoid empty images.

---