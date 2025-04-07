
# 🧠 Deep Learning (CNN, RNN, Transformers) Cheatsheet

## 🔹 Introduction
Deep Learning is a subfield of machine learning that uses **neural networks with multiple layers** to learn complex patterns from large amounts of data.

This cheatsheet focuses on the three most important neural network architectures:

- 🖼️ **CNN (Convolutional Neural Networks)** — Best for **image processing** and spatial data.
- ⏳ **RNN (Recurrent Neural Networks)** — Designed for **sequential data** like time series and text.
- 🧠 **Transformers** — The **state-of-the-art architecture** for NLP and beyond, based on **self-attention**.

---

## 🔹 Convolutional Neural Networks (CNNs)

### ✅ CNN Architecture
| Layer               | Description                                       |
|--------------------|---------------------------------------------------|
| **Convolutional**   | Extracts spatial features using filters/kernels. |
| **Pooling**         | Reduces spatial size (e.g., MaxPooling).         |
| **Fully Connected** | Final classification (Dense layers).             |

🔍 **Use Case Example**: Image classification, object detection (e.g., CIFAR-10, ImageNet)

💡 **Tip**: Use `BatchNormalization` after convolutional layers and `Dropout` before dense layers to improve generalization.

### 📌 Implementing a CNN in TensorFlow/Keras
```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Conv2D, MaxPooling2D, Flatten, Dense, Dropout, BatchNormalization

model = Sequential([
    Conv2D(32, (3,3), activation='relu', input_shape=(64,64,3)),
    BatchNormalization(),
    MaxPooling2D(pool_size=(2,2)),
    Conv2D(64, (3,3), activation='relu'),
    BatchNormalization(),
    MaxPooling2D(pool_size=(2,2)),
    Flatten(),
    Dense(128, activation='relu'),
    Dropout(0.5),
    Dense(10, activation='softmax')
])
```

---

## 🔹 Recurrent Neural Networks (RNNs)

### ✅ RNN Structure
- Maintains a **hidden state** across time steps.
- Suitable for **time-series, speech, and sequential text data**.

🧠 **Use LSTM or GRU** for better memory and long-sequence performance.

### 📌 Simple RNN Implementation
```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import SimpleRNN, Dense

model = Sequential([
    SimpleRNN(50, activation='relu', return_sequences=True, input_shape=(100, 1)),
    SimpleRNN(50, activation='relu'),
    Dense(1, activation='sigmoid')
])
```

### 📌 LSTM Example
```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import LSTM, Dense

model = Sequential([
    LSTM(64, return_sequences=True, input_shape=(100, 1)),
    LSTM(64),
    Dense(1, activation='sigmoid')
])
```

### ✅ Limitations
- Struggles with **long-term dependencies** due to vanishing gradients.
- RNNs are being replaced by **Transformers** in many NLP tasks.

---

## 🔹 Transformers (Attention-Based Models)

### ✅ Why Transformers?
- **Replace RNNs** in most NLP applications.
- Use **self-attention** to model relationships between all tokens **in parallel**.

🎯 In self-attention, each token attends to all other tokens in the sequence to capture context and relevance.

### 📌 Transformer Architecture
| Component             | Purpose                                                  |
|-----------------------|----------------------------------------------------------|
| **Self-Attention**    | Measures inter-token relationships.                      |
| **Positional Encoding** | Adds information about token order to input embeddings. |
| **Feedforward Network** | Applies dense layers to token representations.         |
| **Multi-Head Attention** | Captures multiple types of relationships.            |
| **Layer Normalization** | Helps stabilize and speed up training.                 |

### 📌 Implementing a Transformer with Hugging Face (BERT)
```python
from transformers import BertTokenizer, TFBertModel

# Load Pretrained Model
tokenizer = BertTokenizer.from_pretrained("bert-base-uncased")
bert_model = TFBertModel.from_pretrained("bert-base-uncased")
```

### ✅ Applications of Transformers
- **NLP Tasks**: Text classification, machine translation, sentiment analysis.
- **Vision Transformers (ViT)**: Image classification with patch embeddings.
- **AI Coding Tools**: GitHub Copilot, ChatGPT, Codex.

---

## 🔹 Comparison: CNN vs RNN vs Transformers

| Model         | Best For          | Key Features                           |
|---------------|-------------------|----------------------------------------|
| **CNN**       | Images             | Convolutional layers, feature maps     |
| **RNN**       | Sequential Data    | Memory via hidden states               |
| **Transformers** | NLP, Long Sequences | Self-attention, parallelism         |

---

## 🔹 Best Practices
- ✅ Use **CNNs for image tasks** instead of RNNs.
- ✅ Prefer **Transformers for NLP** over RNNs/LSTMs.
- ✅ Apply **Transfer Learning** (e.g., BERT, VGG16, ResNet) to boost performance.
- ✅ Use **BatchNormalization** and **Dropout** to regularize deep models.
- ✅ Tune hyperparameters using tools like `keras-tuner` or `Optuna`.
- ✅ Visualize learning using **TensorBoard** or **Weights & Biases**.

---

## 🔹 Recommended Tools by Task

| Task                    | Suggested Tool/Library          |
|-------------------------|---------------------------------|
| CNN Training            | TensorFlow / Keras / PyTorch    |
| NLP with Transformers   | Hugging Face Transformers       |
| Hyperparameter Tuning   | Keras Tuner, Optuna             |
| Model Monitoring        | TensorBoard, Weights & Biases   |

---

## 🔹 Final Notes
Deep Learning is evolving rapidly. Stay up-to-date with new architectures like **Diffusion Models**, **ConvNeXt**, or **Mamba**. Always balance **model complexity** with **dataset size**, **computational resources**, and the **specific task** at hand.

🎓 Learn continuously. Experiment often. Deploy responsibly.
