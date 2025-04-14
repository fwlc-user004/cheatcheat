
# 🔥 PyTorch Comprehensive Cheatsheet

## 🔹 Introduction
**PyTorch** is an open-source deep learning framework known for its **flexibility, dynamic computation graph**, and strong GPU acceleration. It supports everything from **tensor operations** to **complex neural networks**.

---

## 🔹 Installation
```sh
pip install torch torchvision torchaudio
```
```python
import torch
print(torch.__version__)
```

---

## 🔹 Tensors: Creation & Initialization
```python
# Scalar
a = torch.tensor(5)

# Vector
b = torch.tensor([1, 2, 3])

# Matrix
c = torch.tensor([[1, 2], [3, 4]])
```

### ✅ Useful Initializers
```python
torch.zeros(2, 3)
torch.ones(2, 3)
torch.rand(2, 3)
torch.eye(3)              # Identity matrix
torch.arange(0, 10, 2)    # Like np.arange
torch.linspace(0, 1, 5)   # Evenly spaced values
```

---

## 🔹 Tensor Operations
```python
# Element-wise ops
x = torch.tensor([1, 2])
y = torch.tensor([3, 4])
x + y, x * y, x ** 2

# Matrix multiplication
A = torch.tensor([[1, 2], [3, 4]])
B = torch.tensor([[5, 6], [7, 8]])
torch.matmul(A, B)

# Common ops
x.mean(), x.sum()
torch.cat((x, y), dim=0)
```

---

## 🔹 Tensor Manipulations
```python
x = torch.rand(2, 3)
x.shape
x.view(3, 2)             # reshape
x.unsqueeze(0)           # add dimension
x.squeeze()              # remove dimensions of size 1
```

---

## 🔹 GPU Acceleration
```python
device = "cuda" if torch.cuda.is_available() else "cpu"
torch.manual_seed(42)
if torch.cuda.is_available():
    torch.cuda.manual_seed(42)

tensor = torch.randn(2, 2).to(device)
model.to(device)
```

---

## 🔹 Autograd & Gradients
```python
x = torch.randn(3, requires_grad=True)
y = x ** 2
z = y.sum()
z.backward()
print(x.grad)  # Gradient of z w.r.t x
```

---

## 🔹 Neural Network (nn.Module)
```python
import torch.nn as nn
import torch.optim as optim

class Net(nn.Module):
    def __init__(self):
        super().__init__()
        self.linear1 = nn.Linear(10, 64)
        self.relu = nn.ReLU()
        self.linear2 = nn.Linear(64, 1)

    def forward(self, x):
        x = self.relu(self.linear1(x))
        return self.linear2(x)

model = Net()
```

### ✅ nn.Sequential (Quick Model)
```python
model = nn.Sequential(
    nn.Linear(10, 64),
    nn.ReLU(),
    nn.Linear(64, 1)
)
```

---

## 🔹 Loss Function & Optimizer
```python
criterion = nn.MSELoss()
optimizer = optim.Adam(model.parameters(), lr=0.001)
```

---

## 🔹 Training Loop
```python
X_train = torch.rand((100, 10))
y_train = torch.rand((100, 1))

model.train()
for epoch in range(10):
    optimizer.zero_grad()
    output = model(X_train)
    loss = criterion(output, y_train)
    loss.backward()
    torch.nn.utils.clip_grad_norm_(model.parameters(), max_norm=1.0)  # Gradient Clipping
    optimizer.step()
    print(f"Epoch {epoch+1}, Loss: {loss.item():.4f}")
```

---

## 🔹 Evaluation & Inference
```python
X_test = torch.rand((20, 10))

model.eval()
with torch.no_grad():
    preds = model(X_test.to(device)).cpu()  # Ensure result on CPU
    print(preds.shape)  # Debugging output shape
```

---

## 🔹 Save & Load Model
```python
# Save only weights
torch.save(model.cpu().state_dict(), "model.pth")

# Load model
model.load_state_dict(torch.load("model.pth"))
model.eval()
```

---

## 🔹 Datasets & Dataloaders
```python
from torch.utils.data import Dataset, DataLoader, TensorDataset

# From tensors
dataset = TensorDataset(X_train, y_train)
loader = DataLoader(dataset, batch_size=16, shuffle=True)

# Custom dataset
class MyDataset(Dataset):
    def __init__(self, X, y):
        self.X, self.y = X, y
    def __len__(self):
        return len(self.X)
    def __getitem__(self, idx):
        return self.X[idx], self.y[idx]

loader = DataLoader(MyDataset(X_train, y_train), batch_size=32)
```

---

## 🔹 Best Practices ✅
- Always `.to(device)` for models and tensors when using CUDA.
- Use `model.eval()` + `torch.no_grad()` during evaluation.
- Set seeds: `torch.manual_seed(42)` and `torch.cuda.manual_seed(42)` for reproducibility.
- Use `detach()` to remove tensors from the autograd graph:
```python
y = model(X_train)
y_detached = y.detach()
```
- Wrap training code with `try/except` for clean interruptions.
- Prefer using `DataLoader` for better batching and shuffling.
- Print model parameters:
```python
for name, param in model.named_parameters():
    print(name, param.shape)
```

---

## 🔹 Bonus Tips
- Use `torchvision.transforms` for image data augmentation.
- Use `nn.Sequential()` for simpler model definitions.
- Use `Gradient Clipping` to prevent exploding gradients.
- Monitor training with tools like `TensorBoard` or `Weights & Biases`.
- Print model summary (requires `torchsummary`):
```python
from torchsummary import summary
summary(model, input_size=(10,))
```
