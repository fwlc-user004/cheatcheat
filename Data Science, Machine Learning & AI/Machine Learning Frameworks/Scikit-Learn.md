# 🤖 Scikit-Learn Cheatsheet

## 🔹 Introduction
Scikit-Learn is a powerful **machine learning library** in Python, providing tools for **classification, regression, clustering, and model evaluation**.

---

## 🔹 Installing Scikit-Learn
```sh
# Install using pip
pip install scikit-learn

# Import the library
import sklearn
```

---

## 🔹 Loading Data
### ✅ Sample Datasets
```python
from sklearn import datasets

# Load the Iris dataset
iris = datasets.load_iris()
X, y = iris.data, iris.target
```

### ✅ Load Data from CSV
```python
import pandas as pd

df = pd.read_csv("data.csv")
X = df.drop("target", axis=1)
y = df["target"]
```

---

## 🔹 Data Preprocessing
### ✅ Train/Test Split
```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

### ✅ Feature Scaling
```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

---

## 🔹 Supervised Learning
### ✅ Linear Regression
```python
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

### ✅ Logistic Regression
```python
from sklearn.linear_model import LogisticRegression
model = LogisticRegression()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

### ✅ Decision Trees
```python
from sklearn.tree import DecisionTreeClassifier
model = DecisionTreeClassifier()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

### ✅ Random Forest
```python
from sklearn.ensemble import RandomForestClassifier
model = RandomForestClassifier(n_estimators=100)
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

### ✅ Support Vector Machines (SVM)
```python
from sklearn.svm import SVC
model = SVC()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

---

## 🔹 Unsupervised Learning
### ✅ K-Means Clustering
```python
from sklearn.cluster import KMeans
model = KMeans(n_clusters=3)
model.fit(X)
labels = model.predict(X)
```

### ✅ Principal Component Analysis (PCA)
```python
from sklearn.decomposition import PCA
pca = PCA(n_components=2)
X_pca = pca.fit_transform(X)
```

---

## 🔹 Model Evaluation
### ✅ Accuracy, Precision, Recall, F1-Score
```python
from sklearn.metrics import accuracy_score, classification_report
print("Accuracy:", accuracy_score(y_test, predictions))
print(classification_report(y_test, predictions))
```

### ✅ Confusion Matrix
```python
from sklearn.metrics import confusion_matrix
print(confusion_matrix(y_test, predictions))
```

### ✅ Cross-Validation
```python
from sklearn.model_selection import cross_val_score
scores = cross_val_score(model, X, y, cv=5)
print("Cross-validation scores:", scores)
```

---

## 🔹 Hyperparameter Tuning
### ✅ Grid Search
```python
from sklearn.model_selection import GridSearchCV
params = {'C': [0.1, 1, 10]}
grid = GridSearchCV(SVC(), params, cv=5)
grid.fit(X_train, y_train)
print("Best Parameters:", grid.best_params_)
```

### ✅ Random Search
```python
from sklearn.model_selection import RandomizedSearchCV
params = {'n_estimators': [10, 50, 100]}
random_search = RandomizedSearchCV(RandomForestClassifier(), params, cv=5)
random_search.fit(X_train, y_train)
print("Best Parameters:", random_search.best_params_)
```

---

## 🔹 Best Practices
- **Preprocess data properly** (scaling, encoding, handling missing values).
- **Use train/test splits** to avoid overfitting.
- **Hyperparameter tuning improves model performance**.
- **Evaluate models using multiple metrics** (not just accuracy).
- **Use cross-validation for robust performance measurement**.

---