# 🔥 PyTorch Comprehensive Cheatsheet

## 🔹 Introduction
PyTorch is an **open-source deep learning framework** that provides **tensor computation and automatic differentiation** for AI and deep learning applications.

---

## 🔹 Installing PyTorch
```sh
# Install PyTorch with pip
pip install torch torchvision torchaudio

# Import PyTorch
import torch
print(torch.__version__)
```

---

## 🔹 Creating Tensors
```python
# Create a scalar tensor
tensor_a = torch.tensor(5)

# Create a vector tensor
tensor_b = torch.tensor([1, 2, 3, 4])

# Create a matrix tensor
tensor_c = torch.tensor([[1, 2], [3, 4]])
```

### ✅ Random Tensors
```python
# Random tensor of size (3,3)
torch.rand(3,3)

# Tensor filled with zeros
torch.zeros(2,2)

# Tensor filled with ones
torch.ones(2,2)
```

---

## 🔹 Tensor Operations
```python
# Element-wise addition, multiplication
tensor_sum = tensor_a + tensor_b
tensor_prod = tensor_a * tensor_b

# Matrix multiplication
mat_a = torch.tensor([[1, 2], [3, 4]])
mat_b = torch.tensor([[5, 6], [7, 8]])
mat_mult = torch.matmul(mat_a, mat_b)
```

---

## 🔹 Moving Tensors to GPU
```python
# Check for GPU availability
device = "cuda" if torch.cuda.is_available() else "cpu"

# Move tensor to GPU
tensor_gpu = torch.tensor([1, 2, 3]).to(device)
```

---

## 🔹 Building a Neural Network
### ✅ Define a Neural Network Model
```python
import torch.nn as nn
import torch.optim as optim

class NeuralNetwork(nn.Module):
    def __init__(self):
        super(NeuralNetwork, self).__init__()
        self.layer1 = nn.Linear(10, 64)
        self.layer2 = nn.Linear(64, 1)
        self.activation = nn.ReLU()

    def forward(self, x):
        x = self.activation(self.layer1(x))
        x = self.layer2(x)
        return x

model = NeuralNetwork()
```

### ✅ Define Loss & Optimizer
```python
loss_function = nn.MSELoss()
optimizer = optim.Adam(model.parameters(), lr=0.001)
```

---

## 🔹 Training a Model
```python
X_train = torch.rand((100, 10))
y_train = torch.rand((100, 1))

for epoch in range(10):
    optimizer.zero_grad()
    predictions = model(X_train)
    loss = loss_function(predictions, y_train)
    loss.backward()
    optimizer.step()
    print(f"Epoch {epoch+1}, Loss: {loss.item()}")
```

---

## 🔹 Model Evaluation & Predictions
```python
X_test = torch.rand((20, 10))
predictions = model(X_test)
```

---

## 🔹 Saving & Loading Models
```python
# Save the model
torch.save(model.state_dict(), "model.pth")

# Load the model
model.load_state_dict(torch.load("model.pth"))
model.eval()
```

---

## 🔹 Best Practices
- **Use `.to(device)`** to move models and tensors to GPU for faster computations.
- **Normalize input data** for better training stability.
- **Use `.detach()` on tensors** to prevent unwanted gradient tracking.
- **Set random seeds (`torch.manual_seed`)** for reproducibility.
- **Use DataLoaders (`torch.utils.data.DataLoader`)** for efficient batch processing.

---