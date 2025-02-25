# 🤖 TensorFlow Cheatsheet

## 🔹 Introduction
TensorFlow is an **open-source machine learning framework** developed by Google for **deep learning, neural networks, and AI applications**.

---

## 🔹 Installing TensorFlow
```sh
# Install TensorFlow using pip
pip install tensorflow

# Import TensorFlow
import tensorflow as tf
print(tf.__version__)
```

---

## 🔹 Creating Tensors
```python
# Create a scalar tensor
tensor_a = tf.constant(5)

# Create a vector tensor
tensor_b = tf.constant([1, 2, 3, 4])

# Create a matrix tensor
tensor_c = tf.constant([[1, 2], [3, 4]])
```

---

## 🔹 Tensor Operations
```python
# Addition, Subtraction, Multiplication
tensor_sum = tf.add(tensor_a, tensor_b)
tensor_prod = tf.multiply(tensor_a, tensor_b)

# Matrix multiplication
mat_a = tf.constant([[1, 2], [3, 4]])
mat_b = tf.constant([[5, 6], [7, 8]])
mat_mult = tf.matmul(mat_a, mat_b)
```

---

## 🔹 Building a Neural Network
### ✅ Define a Sequential Model
```python
from tensorflow import keras
from tensorflow.keras import layers

model = keras.Sequential([
    layers.Dense(64, activation='relu', input_shape=(10,)),
    layers.Dense(32, activation='relu'),
    layers.Dense(1, activation='sigmoid')
])
```

### ✅ Compile the Model
```python
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])
```

### ✅ Train the Model
```python
# Generate dummy data
import numpy as np
X_train = np.random.rand(1000, 10)
y_train = np.random.randint(2, size=1000)

model.fit(X_train, y_train, epochs=10, batch_size=32)
```

---

## 🔹 Model Evaluation & Predictions
```python
# Evaluate on test data
X_test = np.random.rand(200, 10)
y_test = np.random.randint(2, size=200)
model.evaluate(X_test, y_test)

# Make predictions
predictions = model.predict(X_test)
```

---

## 🔹 Saving & Loading Models
```python
# Save the model
model.save("model.h5")

# Load the model
loaded_model = keras.models.load_model("model.h5")
```

---

## 🔹 TensorFlow Best Practices
- **Use GPUs for faster training** (`tf.config.list_physical_devices('GPU')`).
- **Normalize input data** to improve convergence.
- **Save and reuse trained models** to avoid retraining.
- **Tune hyperparameters** using `keras-tuner`.
- **Use TensorBoard** for monitoring training (`tensorboard --logdir=logs`).

---