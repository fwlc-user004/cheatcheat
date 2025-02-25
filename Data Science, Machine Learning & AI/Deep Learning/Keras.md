# 🤖 Keras Comprehensive Cheatsheet

## 🔹 Introduction
Keras is a **high-level deep learning API** that runs on top of **TensorFlow**, making it easy to build, train, and deploy neural networks.

---

## 🔹 Installing Keras
```sh
# Install Keras (via TensorFlow)
pip install tensorflow

# Import Keras
from tensorflow import keras
```

---

## 🔹 Building a Neural Network
### ✅ Define a Sequential Model
```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Dropout, Flatten

model = Sequential([
    Dense(64, activation='relu', input_shape=(10,)),
    Dense(32, activation='relu'),
    Dense(1, activation='sigmoid')
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
X_test = np.random.rand(200, 10)
y_test = np.random.randint(2, size=200)

# Evaluate model
model.evaluate(X_test, y_test)

# Make predictions
predictions = model.predict(X_test)
```

---

## 🔹 Saving & Loading Models
```python
# Save model
model.save("model.h5")

# Load model
from tensorflow.keras.models import load_model
loaded_model = load_model("model.h5")
```

---

## 🔹 Advanced Layers
### ✅ Convolutional Layers (CNNs)
```python
from tensorflow.keras.layers import Conv2D, MaxPooling2D

model = Sequential([
    Conv2D(32, (3,3), activation='relu', input_shape=(64,64,3)),
    MaxPooling2D(pool_size=(2,2)),
    Flatten(),
    Dense(128, activation='relu'),
    Dense(10, activation='softmax')
])
```

### ✅ Recurrent Layers (RNNs)
```python
from tensorflow.keras.layers import SimpleRNN, LSTM

model = Sequential([
    SimpleRNN(50, activation='relu', return_sequences=True, input_shape=(100, 1)),
    LSTM(50, activation='relu'),
    Dense(1, activation='sigmoid')
])
```

---

## 🔹 Callbacks & Early Stopping
```python
from tensorflow.keras.callbacks import EarlyStopping

callback = EarlyStopping(monitor='val_loss', patience=3)
model.fit(X_train, y_train, epochs=50, batch_size=32, validation_split=0.2, callbacks=[callback])
```

---

## 🔹 Hyperparameter Tuning
```python
from keras_tuner import RandomSearch

def build_model(hp):
    model = Sequential()
    model.add(Dense(hp.Int('units', min_value=32, max_value=256, step=32), activation='relu'))
    model.add(Dense(1, activation='sigmoid'))
    model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])
    return model

tuner = RandomSearch(build_model, objective='val_accuracy', max_trials=5)
tuner.search(X_train, y_train, epochs=10, validation_split=0.2)
```

---

## 🔹 Best Practices
- **Use `relu` for hidden layers** and `softmax` or `sigmoid` for output layers.
- **Normalize input data** for better convergence.
- **Use Dropout layers** to prevent overfitting.
- **Use EarlyStopping** to avoid unnecessary training epochs.
- **Perform hyperparameter tuning** for better model performance.

---