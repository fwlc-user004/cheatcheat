
# 🤖 Keras Comprehensive Cheatsheet

## 🔹 Introduction
Keras is a **high-level deep learning API** that runs on top of **TensorFlow**, making it easy to build, train, and deploy neural networks.

---

## 🔹 Installing Keras
```sh
# Install Keras (via TensorFlow)
pip install tensorflow
```

```python
# Import Keras
from tensorflow import keras
```

---

## 🔹 Building a Neural Network

### ✅ Sequential API
```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Dropout, Flatten

model = Sequential([
    Dense(64, activation='relu', input_shape=(10,)),
    Dense(32, activation='relu'),
    Dense(1, activation='sigmoid')
])
```

### ✅ Functional API (Recommended for Complex Models)
```python
from tensorflow.keras.models import Model
from tensorflow.keras.layers import Input, Dense

inputs = Input(shape=(10,))
x = Dense(64, activation='relu')(inputs)
x = Dense(32, activation='relu')(x)
outputs = Dense(1, activation='sigmoid')(x)

model = Model(inputs=inputs, outputs=outputs)
```

---

## 🔹 Model Compilation, Training & Evaluation

### ✅ Compile the Model
```python
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])
```

### ✅ Train the Model
```python
import numpy as np
X_train = np.random.rand(1000, 10)
y_train = np.random.randint(2, size=1000)

model.fit(X_train, y_train, epochs=10, batch_size=32)
```

### ✅ Evaluate & Predict
```python
X_test = np.random.rand(200, 10)
y_test = np.random.randint(2, size=200)

model.evaluate(X_test, y_test)
predictions = model.predict(X_test)
```

---

## 🔹 Saving & Loading Models
```python
model.save("model.h5")

from tensorflow.keras.models import load_model
loaded_model = load_model("model.h5")
```

---

## 🔹 Model Summary & Visualization
```python
model.summary()

from tensorflow.keras.utils import plot_model
plot_model(model, to_file="model_architecture.png", show_shapes=True)
```

---

## 🔹 Advanced Layers

### ✅ CNN Example
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

### ✅ RNN Example
```python
from tensorflow.keras.layers import SimpleRNN, LSTM

model = Sequential([
    SimpleRNN(50, return_sequences=True, input_shape=(100, 1)),
    LSTM(50),
    Dense(1, activation='sigmoid')
])
```

---

## 🔹 Callbacks

### ✅ EarlyStopping & ModelCheckpoint
```python
from tensorflow.keras.callbacks import EarlyStopping, ModelCheckpoint

early_stop = EarlyStopping(monitor='val_loss', patience=3)
checkpoint = ModelCheckpoint("best_model.h5", save_best_only=True)

model.fit(X_train, y_train, validation_split=0.2, epochs=50, callbacks=[early_stop, checkpoint])
```

---

## 🔹 Preprocessing

### ✅ Normalization
```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
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

## 🔹 Custom Components

### ✅ Custom Loss
```python
import tensorflow.keras.backend as K

def custom_mse(y_true, y_pred):
    return K.mean(K.square(y_pred - y_true))
```

### ✅ Custom Metric
```python
from tensorflow.keras.metrics import AUC

model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy', AUC()])
```

---

## 🔹 tf.data Input Pipeline
```python
import tensorflow as tf

dataset = tf.data.Dataset.from_tensor_slices((X_train, y_train))
dataset = dataset.shuffle(buffer_size=1024).batch(32)
```

---

## 🔹 Best Practices
- Use **ReLU** for hidden layers and **Sigmoid/Softmax** for outputs.
- Normalize input data.
- Use **Dropout** to prevent overfitting.
- Use **EarlyStopping + ModelCheckpoint** together.
- Tune hyperparameters with **Keras Tuner**.
- Visualize model and training metrics.
- Set random seed for reproducibility.

---

## 🔹 Final Notes
Keras is ideal for both prototyping and production-grade deep learning. Combine it with TensorFlow tools for more flexibility and power.

🎯 Explore:
- Functional API for custom architectures
- `tf.data` for performance input pipelines
- Custom callbacks, layers, and metrics
