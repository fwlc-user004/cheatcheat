# 🧠 Deep Learning (CNN, RNN, Transformers) Cheatsheet

## 🔹 Introduction
Deep Learning involves **neural networks** that learn from data. This cheatsheet covers:
- **CNN (Convolutional Neural Networks)** → Image Processing
- **RNN (Recurrent Neural Networks)** → Sequential Data
- **Transformers** → NLP & Attention Mechanisms

---

## 🔹 Convolutional Neural Networks (CNNs)
### ✅ CNN Architecture
| Layer       | Description |
|------------|-------------|
| **Convolutional** | Extracts features using filters/kernels. |
| **Pooling** | Reduces dimensionality (e.g., MaxPooling). |
| **Fully Connected** | Final classification (Dense layers). |

### 📌 Implementing a CNN in TensorFlow/Keras
```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Conv2D, MaxPooling2D, Flatten, Dense

model = Sequential([
    Conv2D(32, (3,3), activation='relu', input_shape=(64,64,3)),
    MaxPooling2D(pool_size=(2,2)),
    Conv2D(64, (3,3), activation='relu'),
    MaxPooling2D(pool_size=(2,2)),
    Flatten(),
    Dense(128, activation='relu'),
    Dense(10, activation='softmax')
])
```

---

## 🔹 Recurrent Neural Networks (RNNs)
### ✅ RNN Structure
- **Maintains hidden state** between timesteps.
- Good for **time-series & sequential data** (text, speech, etc.).

### 📌 Implementing a Basic RNN in TensorFlow/Keras
```python
from tensorflow.keras.layers import SimpleRNN

model = Sequential([
    SimpleRNN(50, activation='relu', return_sequences=True, input_shape=(100, 1)),
    SimpleRNN(50, activation='relu'),
    Dense(1, activation='sigmoid')
])
```

### ✅ Limitations
- **Short-term memory** due to vanishing gradients.
- **Not ideal for long sequences** → Use LSTM/GRU.

---

## 🔹 Transformers (Attention-Based Models)
### ✅ Why Transformers?
- **Replaces RNNs in NLP.**
- Uses **self-attention** to process words **simultaneously**.

### 📌 Transformer Architecture
| Component | Purpose |
|-----------|---------|
| **Self-Attention** | Computes relationships between all words. |
| **Positional Encoding** | Adds sequence order information. |
| **Feedforward Network** | Processes features per token. |
| **Multi-Head Attention** | Captures different types of relationships. |
| **Layer Normalization** | Stabilizes training. |

### 📌 Implementing a Transformer with Hugging Face (BERT)
```python
from transformers import BertTokenizer, TFBertModel

# Load Pretrained Model
tokenizer = BertTokenizer.from_pretrained("bert-base-uncased")
bert_model = TFBertModel.from_pretrained("bert-base-uncased")
```

### ✅ Applications of Transformers
- **NLP Tasks**: Text classification, machine translation.
- **Vision Transformers** (ViT): Used in image processing.
- **Code Understanding**: GitHub Copilot, AI-based coding assistants.

---

## 🔹 Comparison: CNN vs RNN vs Transformers
| Model | Best For | Key Features |
|------|---------|-------------|
| **CNN** | Image Processing | Convolutional layers, feature extraction |
| **RNN** | Sequential Data | Recurrence, memory, good for short sequences |
| **Transformers** | NLP, Long Sequences | Self-attention, parallel processing |

---

## 🔹 Best Practices
- **Use CNNs for images** instead of RNNs.
- **Prefer Transformers for NLP** over RNN/LSTMs.
- **Use Transfer Learning** (e.g., Pretrained BERT/VGG16) for better performance.
- **Optimize hyperparameters** using tools like `keras-tuner`.

---