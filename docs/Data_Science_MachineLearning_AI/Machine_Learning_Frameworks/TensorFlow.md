
# 🤖 TensorFlow Cheatsheet

## 🔹 Introduction  
TensorFlow is an **open-source machine learning framework** developed by Google. It is widely used for **deep learning, neural networks, and AI applications**, offering both **low-level operations** and **high-level APIs like Keras**.

---

## 🔹 Installing TensorFlow
```sh
# Install TensorFlow using pip
pip install tensorflow

# Optional: For GPU support (requires CUDA/cuDNN)
# pip install tensorflow-gpu

# Import TensorFlow and check version
import tensorflow as tf
print(tf.__version__)
```

---

## 🔹 Creating Tensors
```python
# Scalar tensor (0D) → a single number
tensor_a = tf.constant(5)

# Vector tensor (1D) → like a list
tensor_b = tf.constant([1, 2, 3, 4])

# Matrix tensor (2D) → like a 2D array
tensor_c = tf.constant([[1, 2], [3, 4]])

# Float tensor with shape info
tensor_d = tf.constant([1.0, 2.0, 3.0])
print(tensor_d.shape, tensor_d.dtype)
```

---

## 🔹 Tensor Operations
```python
# Element-wise operations
tensor_sum = tf.add(tensor_a, tensor_b)
tensor_prod = tf.multiply(tensor_a, tensor_b)
tensor_sub = tf.subtract(tensor_b, [1, 1, 1, 1])  # Broadcasting

# Matrix multiplication
mat_a = tf.constant([[1, 2], [3, 4]])
mat_b = tf.constant([[5, 6], [7, 8]])
mat_mult = tf.matmul(mat_a, mat_b)

# Reshape tensors
reshaped = tf.reshape(tensor_c, (4, 1))
```

---

## 🔹 Building a Neural Network

### ✅ Define a Sequential Model
```python
from tensorflow import keras
from tensorflow.keras import layers

model = keras.Sequential([
    layers.Dense(64, activation='relu', input_shape=(10,)),  # 10 features
    layers.Dense(32, activation='relu'),
    layers.Dense(1, activation='sigmoid')  # Binary output
])
```

### ✅ Compile the Model
```python
model.compile(
    optimizer='adam',
    loss='binary_crossentropy',
    metrics=['accuracy']
)
```

### ✅ Train the Model
```python
# Generate dummy data
import numpy as np
X_train = np.random.rand(1000, 10)
y_train = np.random.randint(2, size=1000)

# Train with validation split
model.fit(X_train, y_train, epochs=10, batch_size=32, validation_split=0.2)
```

---

## 🔹 Model Evaluation & Predictions
```python
# Generate test data
X_test = np.random.rand(200, 10)
y_test = np.random.randint(2, size=200)

# Evaluate the model
model.evaluate(X_test, y_test)

# Make predictions (returns probabilities)
predictions = model.predict(X_test)

# Convert probabilities to binary class labels
predicted_classes = (predictions > 0.5).astype("int32")

# View first 5 predicted classes
print(predicted_classes[:5])
```

---

## 🔹 Saving & Loading Models
```python
# Save model to HDF5 format
model.save("model.h5")

# Load from HDF5
loaded_model = keras.models.load_model("model.h5")

# Alternatively, save in TensorFlow SavedModel format
model.save("saved_model_folder")
loaded_model = keras.models.load_model("saved_model_folder")

# Save and load weights only
model.save_weights("weights_only.h5")
model.load_weights("weights_only.h5")
```

---

## 🔹 TensorFlow Best Practices
- ✅ Use **GPUs** for faster training:  
  ```python
  tf.config.list_physical_devices('GPU')
  ```

- ✅ **Normalize input data** for better convergence.

- ✅ **Use callbacks** like `EarlyStopping` and `ModelCheckpoint`:
  ```python
  from tensorflow.keras.callbacks import EarlyStopping, ModelCheckpoint

  callbacks = [
      EarlyStopping(patience=3, restore_best_weights=True),
      ModelCheckpoint('best_model.h5', save_best_only=True)
  ]
  ```

- ✅ Use **TensorBoard** for monitoring:  
  ```sh
  tensorboard --logdir=logs
  ```

- ✅ Use **`tf.data` API** for efficient data pipelines.

- ✅ Use **mixed precision training** on modern GPUs:  
  ```python
  tf.keras.mixed_precision.set_global_policy('mixed_float16')
  ```

- ✅ Save and reuse trained models to avoid retraining.

- ✅ Tune hyperparameters using tools like **Keras Tuner**:
  ```python
  # Install Keras Tuner
  # pip install keras-tuner

  import keras_tuner as kt
  ```
