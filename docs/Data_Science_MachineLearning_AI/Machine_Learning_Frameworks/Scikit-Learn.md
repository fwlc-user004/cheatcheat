# 🤖 Scikit-Learn Cheatsheet

## 🔹 Introduction
Scikit-Learn is a powerful and widely-used **machine learning library** in Python. It provides efficient tools for:

- **Supervised learning** (e.g., classification, regression)
- **Unsupervised learning** (e.g., clustering, dimensionality reduction)
- **Model evaluation** and **hyperparameter tuning**

---

## 🔹 Installing Scikit-Learn
```bash
# Install using pip
pip install scikit-learn
```

---

## 🔹 Loading Data
### ✅ Sample Datasets (Built-in)
```python
from sklearn import datasets

# Load the Iris dataset (for classification)
iris = datasets.load_iris()
X, y = iris.data, iris.target
```

### ✅ Load Data from CSV
```python
import pandas as pd

# Load custom dataset
df = pd.read_csv("data.csv")
X = df.drop("target", axis=1)  # Features
y = df["target"]                # Target
```

---

## 🔹 Data Preprocessing
### ✅ Train/Test Split
Split data into training and testing sets:
```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)
```

### ✅ Feature Scaling
Standardize features by removing the mean and scaling to unit variance:
```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

### ✅ Handling Missing Values
```python
from sklearn.impute import SimpleImputer

imputer = SimpleImputer(strategy="mean")
X_imputed = imputer.fit_transform(X)
```

### ✅ Encoding Categorical Variables
```python
from sklearn.preprocessing import OneHotEncoder

encoder = OneHotEncoder(sparse_output=False)
X_encoded = encoder.fit_transform(X_categorical)
```

---

## 🔹 Supervised Learning
### ✅ Linear Regression (for regression tasks)
```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

### ✅ Logistic Regression (for binary/multi-class classification)
```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression(max_iter=1000)
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

### ✅ K-Nearest Neighbors (KNN)
```python
from sklearn.neighbors import KNeighborsClassifier

model = KNeighborsClassifier(n_neighbors=5)
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

### ✅ Decision Tree Classifier
```python
from sklearn.tree import DecisionTreeClassifier

model = DecisionTreeClassifier()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

### ✅ Random Forest Classifier
```python
from sklearn.ensemble import RandomForestClassifier

model = RandomForestClassifier(n_estimators=100)
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

### ✅ Gradient Boosting Classifier
```python
from sklearn.ensemble import GradientBoostingClassifier

model = GradientBoostingClassifier()
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

### ✅ Voting Classifier (Ensemble of multiple models)
```python
from sklearn.ensemble import VotingClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.svm import SVC

model1 = LogisticRegression(max_iter=1000)
model2 = DecisionTreeClassifier()
model3 = SVC(probability=True)

ensemble = VotingClassifier(estimators=[
    ('lr', model1),
    ('dt', model2),
    ('svm', model3)
], voting='soft')

ensemble.fit(X_train, y_train)
predictions = ensemble.predict(X_test)
```

---

## 🔹 Unsupervised Learning
### ✅ K-Means Clustering
```python
from sklearn.cluster import KMeans

model = KMeans(n_clusters=3, init='k-means++', n_init=10, random_state=42)
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
### ✅ Grid Search (Exhaustive)
```python
from sklearn.model_selection import GridSearchCV

params = {'C': [0.1, 1, 10]}
grid = GridSearchCV(SVC(), params, cv=5, scoring='f1_macro')
grid.fit(X_train, y_train)
print("Best Parameters:", grid.best_params_)
```

### ✅ Randomized Search (Faster alternative)
```python
from sklearn.model_selection import RandomizedSearchCV

params = {'n_estimators': [10, 50, 100]}
random_search = RandomizedSearchCV(RandomForestClassifier(), params, cv=5, scoring='f1_macro')
random_search.fit(X_train, y_train)
print("Best Parameters:", random_search.best_params_)
```

---

## 🔹 Pipelines (Chaining Steps)
```python
from sklearn.pipeline import Pipeline

pipeline = Pipeline([
    ('scaler', StandardScaler()),
    ('classifier', LogisticRegression(max_iter=1000))
])

pipeline.fit(X_train, y_train)
predictions = pipeline.predict(X_test)
```

---

## 🔹 Saving & Loading Models
```python
import joblib

# Save model
joblib.dump(model, 'model.pkl')

# Load model
model = joblib.load('model.pkl')
```

---

## 🔹 Best Practices
- 🔹 Always **preprocess your data** (scaling, encoding, missing values).
- 🔹 Use **train/test split** to evaluate generalization.
- 🔹 Apply **cross-validation** for robust performance.
- 🔹 **Tune hyperparameters** to boost accuracy.
- 🔹 Prefer multiple metrics over just accuracy.
- 🔹 Watch for **data leakage** and **imbalanced datasets**.
- 🔹 Use **pipelines** to chain preprocessing and modeling.
- 🔹 Persist models using **joblib** for reuse in production.
- 🔹 Consider **ensemble methods** like Voting or Boosting for better performance on complex tasks.

---
