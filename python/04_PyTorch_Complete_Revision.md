# 🔥 PyTorch - Complete Beginner's Revision Guide

> Master PyTorch for deep learning from basics to models 🎯

---

## 1. 📌 What is PyTorch?

**PyTorch** = Deep learning framework by Facebook

**Key Features:**
- ✅ **Tensors** - like NumPy arrays but GPU-compatible
- ✅ **Automatic Differentiation (Autograd)** - calculates gradients automatically
- ✅ **Neural Networks** - easy model building
- ✅ **GPU Support** - 100x+ faster than CPU
- ✅ **Dynamic Computation Graph** - define networks on-the-fly

**Use Cases:**
- Computer vision (image classification, detection)
- Natural language processing (text, translation)
- Reinforcement learning
- Generative models (GANs, VAE)

**PyTorch vs TensorFlow:**
| Feature | PyTorch | TensorFlow |
|---|---|---|
| Learning Curve | Easier (Pythonic) | Steeper (Complex) |
| Speed | Slightly slower | Slightly faster |
| Debugging | Great (eager execution) | Harder (graph) |
| Research | More popular | Production-focused |

---

## 2. 🔧 Installation & Import

```python
# Install
# pip install torch torchvision torchaudio

# Import
import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader, TensorDataset

# Check version
print(torch.__version__)

# Check GPU availability
print(torch.cuda.is_available())      # True/False
print(torch.cuda.get_device_name(0))  # GPU name
```

---

## 3. 📦 Tensors (Basic Data Structure)

Tensors are n-dimensional arrays. They're like NumPy arrays but can run on GPU.

### Creating Tensors:
```python
# From Python list
t = torch.tensor([1, 2, 3, 4])
print(t)    # tensor([1, 2, 3, 4])

# 2D tensor
t = torch.tensor([[1, 2], [3, 4]])
print(t)
# tensor([[1, 2],
#         [3, 4]])

# From NumPy array
import numpy as np
arr = np.array([1, 2, 3])
t = torch.from_numpy(arr)

# Back to NumPy
arr = t.numpy()
```

### Special Tensors:
```python
# Zeros
t = torch.zeros(3, 3)
# tensor([[0., 0., 0.],
#         [0., 0., 0.],
#         [0., 0., 0.]])

# Ones
t = torch.ones(3, 3)

# Random
t = torch.rand(3, 3)   # Random 0-1

# Identity
t = torch.eye(3)

# Range
t = torch.arange(0, 10, 2)  # tensor([0, 2, 4, 6, 8])

# Empty (uninitialized)
t = torch.empty(3, 3)
```

---

## 4. 🔍 Tensor Properties & Operations

### Properties:
```python
t = torch.tensor([[1, 2, 3], [4, 5, 6]])

print(t.shape)      # torch.Size([2, 3])
print(t.dtype)      # torch.int64
print(t.device)     # cpu

# Reshape
t = t.reshape(3, 2)
t = t.view(3, 2)    # Alternative

# Flatten
t_flat = t.flatten()  # 1D tensor

# Transpose
t_T = t.t()         # For 2D
t_T = t.T           # For any dimension
```

### Moving to GPU:
```python
t = torch.tensor([1, 2, 3])

# Move to GPU
if torch.cuda.is_available():
    t = t.cuda()        # or t.to('cuda')
    print(t)            # tensor([1, 2, 3], device='cuda:0')

# Move back to CPU
t = t.cpu()
```

---

## 5. ➕ Tensor Operations

### Arithmetic:
```python
a = torch.tensor([1, 2, 3], dtype=torch.float32)
b = torch.tensor([4, 5, 6], dtype=torch.float32)

print(a + b)        # tensor([5., 7., 9.])
print(a - b)        # tensor([-3., -3., -3.])
print(a * b)        # tensor([ 4., 10., 18.])
print(a / b)        # tensor([0.2500, 0.4000, 0.5000])
print(a ** 2)       # tensor([1., 4., 9.])

# In-place operations
a.add_(b)           # a = a + b
a.mul_(2)           # a = a * 2
```

### Matrix Operations:
```python
a = torch.tensor([[1, 2], [3, 4]], dtype=torch.float32)
b = torch.tensor([[5, 6], [7, 8]], dtype=torch.float32)

# Matrix multiplication
result = torch.matmul(a, b)
result = a @ b      # Same thing
print(result)
# tensor([[ 19.,  22.],
#         [ 43.,  50.]])

# Transpose
print(a.t())
# tensor([[1., 3.],
#         [2., 4.]])

# Element-wise
print(a * b)
# tensor([[ 5., 12.],
#         [21., 32.]])
```

---

## 6. 🧮 Automatic Differentiation (Autograd)

Autograd automatically calculates gradients! This is PyTorch's superpower.

### Basic Backpropagation:
```python
# Create tensor with requires_grad=True
x = torch.tensor([2.0], requires_grad=True)
print(x)  # tensor([2.], requires_grad=True)

# Perform operations
y = x ** 2          # y = 4
z = y * 3           # z = 12

# Backpropagation
z.backward()        # Calculate gradients

# Check gradient (dz/dx)
print(x.grad)       # tensor([12.])
# Explanation: dz/dx = d(3*x^2)/dx = 6*x = 6*2 = 12
```

### Complex Graph:
```python
x = torch.tensor([2.0, 3.0], requires_grad=True)

# Forward pass
y = x ** 2
z = y.sum()         # Sum all elements

# Backward pass
z.backward()

# Gradients
print(x.grad)       # tensor([4., 6.])
# Because: dz/dx0 = 2*2 = 4, dz/dx1 = 2*3 = 6
```

### Reset Gradients:
```python
x.grad.zero_()      # Set gradients to zero
```

---

## 7. 🧠 Neural Network Basics

### Simple Neural Network:
```python
import torch.nn as nn

# Create a simple model
model = nn.Sequential(
    nn.Linear(10, 20),       # Input 10 → 20 neurons
    nn.ReLU(),               # Activation function
    nn.Linear(20, 5)         # Hidden 20 → Output 5
)

# Create input (say 32 samples, 10 features)
x = torch.randn(32, 10)

# Forward pass
output = model(x)
print(output.shape)          # torch.Size([32, 5])
```

### Custom Model:
```python
class SimpleNet(nn.Module):
    def __init__(self):
        super(SimpleNet, self).__init__()
        self.fc1 = nn.Linear(784, 128)      # Image: 28x28 = 784
        self.fc2 = nn.Linear(128, 64)
        self.fc3 = nn.Linear(64, 10)        # 10 classes
    
    def forward(self, x):
        x = x.view(x.size(0), -1)           # Flatten
        x = torch.relu(self.fc1(x))         # Hidden layer with ReLU
        x = torch.relu(self.fc2(x))         # Hidden layer with ReLU
        x = self.fc3(x)                     # Output layer
        return x

model = SimpleNet()
print(model)

# Test
x = torch.randn(32, 1, 28, 28)  # 32 images, 28x28
output = model(x)
print(output.shape)              # torch.Size([32, 10])
```

---

## 8. 🎯 Loss Functions & Optimization

### Loss Functions:
```python
# For classification
criterion = nn.CrossEntropyLoss()   # Multi-class
criterion = nn.BCELoss()            # Binary classification

# For regression
criterion = nn.MSELoss()            # Mean squared error
criterion = nn.L1Loss()             # Mean absolute error

# Calculate loss
predictions = torch.tensor([[0.1, 0.2, 0.7],
                            [0.3, 0.4, 0.3]])
targets = torch.tensor([2, 0])      # Class indices

loss = criterion(predictions, targets)
print(loss)                         # Some value
```

### Optimizers:
```python
import torch.optim as optim

# Create optimizer
optimizer = optim.SGD(model.parameters(), lr=0.01)
optimizer = optim.Adam(model.parameters(), lr=0.001)
optimizer = optim.RMSprop(model.parameters(), lr=0.01)

# Learning rate: step size for updating weights
# SGD = simple, Adam = adaptive (usually better)
```

---

## 9. 🔄 Training Loop

Complete training example:

```python
import torch
import torch.nn as nn
import torch.optim as optim

# Create model
model = nn.Sequential(
    nn.Linear(10, 20),
    nn.ReLU(),
    nn.Linear(20, 5)
)

# Loss and optimizer
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr=0.001)

# Create dummy data
X = torch.randn(100, 10)                    # 100 samples, 10 features
y = torch.randint(0, 5, (100,))             # 100 labels (0-4)

# Training loop
epochs = 10
for epoch in range(epochs):
    # Forward pass
    output = model(X)
    loss = criterion(output, y)
    
    # Backward pass
    optimizer.zero_grad()       # Clear old gradients
    loss.backward()             # Calculate gradients
    
    # Update weights
    optimizer.step()            # Update weights
    
    if (epoch + 1) % 2 == 0:
        print(f"Epoch {epoch+1}/{epochs}, Loss: {loss.item():.4f}")

# Output:
# Epoch 2/10, Loss: 1.5234
# Epoch 4/10, Loss: 1.4102
# ...
```

---

## 10. 📊 DataLoader (Batch Processing)

```python
from torch.utils.data import TensorDataset, DataLoader

# Create dataset
X = torch.randn(100, 10)
y = torch.randint(0, 2, (100,))

dataset = TensorDataset(X, y)

# Create dataloader (batches)
train_loader = DataLoader(dataset, batch_size=32, shuffle=True)

# Iterate through batches
for batch_X, batch_y in train_loader:
    print(batch_X.shape)        # torch.Size([32, 10])
    print(batch_y.shape)        # torch.Size([32])
    # Train on this batch
    break
```

---

## 11. 🎨 Activation Functions

```python
# ReLU - most popular
x = torch.tensor([[-1.0, 0.0, 1.0, 2.0]])
print(torch.relu(x))            # tensor([[0., 0., 1., 2.]])

# Sigmoid - outputs 0-1
print(torch.sigmoid(x))         # tensor([[0.2689, 0.5000, 0.7311, 0.8808]])

# Tanh - outputs -1 to 1
print(torch.tanh(x))            # tensor([[-0.7616, 0.0000, 0.7616, 0.9640]])

# Softmax - converts to probabilities
x = torch.tensor([[1.0, 2.0, 3.0]])
print(torch.softmax(x, dim=1))  # tensor([[0.0900, 0.2447, 0.6652]])
```

### Using in model:
```python
model = nn.Sequential(
    nn.Linear(10, 20),
    nn.ReLU(),              # Hidden activation
    nn.Linear(20, 5)        # Output (no activation for regression)
)
```

---

## 12. 💾 Saving & Loading Models

```python
# Save model
torch.save(model.state_dict(), 'model.pth')

# Load model
model = SimpleNet()  # Create new instance
model.load_state_dict(torch.load('model.pth'))

# Save entire model (with architecture)
torch.save(model, 'model.pth')

# Load entire model
model = torch.load('model.pth')
```

---

## 13. 🔍 Common Functions

### Utilities:
```python
# Clone tensor
t_copy = t.clone()

# Detach (no gradient tracking)
x = torch.tensor([1.0], requires_grad=True)
y = x ** 2
z = y.detach()          # z doesn't track gradients

# Convert to Python value
t = torch.tensor([42])
value = t.item()        # 42

# No grad context (faster inference)
with torch.no_grad():
    output = model(X)   # Doesn't track gradients
```

### Reshape operations:
```python
t = torch.randn(2, 3, 4)

print(t.shape)          # torch.Size([2, 3, 4])
print(t.view(-1))       # Flatten to 1D (-1 = infer)
print(t.view(2, -1))    # 2 x ? (? inferred as 12)
print(t.reshape(6, 4))  # Same as view, creates copy
```

---

## 14. 🎯 Training Tips

### 1. Normalize Data:
```python
# Normalize inputs to mean=0, std=1
mean = X.mean(dim=0)
std = X.std(dim=0)
X_normalized = (X - mean) / std
```

### 2. Learning Rate Scheduling:
```python
scheduler = torch.optim.lr_scheduler.StepLR(optimizer, 
                                           step_size=5, 
                                           gamma=0.1)

for epoch in range(epochs):
    # Training...
    scheduler.step()  # Reduce LR every 5 epochs
```

### 3. Early Stopping:
```python
best_loss = float('inf')
patience = 5
patience_count = 0

for epoch in range(epochs):
    # Training...
    if val_loss < best_loss:
        best_loss = val_loss
        patience_count = 0
        torch.save(model.state_dict(), 'best_model.pth')
    else:
        patience_count += 1
        if patience_count >= patience:
            print("Early stopping")
            break
```

### 4. Gradient Clipping:
```python
# Prevent exploding gradients
torch.nn.utils.clip_grad_norm_(model.parameters(), max_norm=1.0)
```

---

## 15. 📊 Common Layers & Functions

### Neural Network Layers:
```
nn.Linear(in, out)          → Fully connected layer
nn.Conv2d(in, out, kernel)  → Convolutional layer
nn.RNN(input, hidden)       → Recurrent layer
nn.LSTM(input, hidden)      → Long short-term memory
nn.Embedding(vocab, embedding) → Embedding layer
nn.Dropout(p)               → Dropout (regularization)
nn.BatchNorm2d(channels)    → Batch normalization
```

### Activation Functions:
```
torch.relu()    → ReLU
torch.sigmoid() → Sigmoid
torch.tanh()    → Tanh
torch.softmax() → Softmax
nn.ReLU()       → ReLU layer
```

---

## 📋 Quick Reference

| Task | Code |
|---|---|
| Create tensor | `torch.tensor([1, 2, 3])` |
| Random tensor | `torch.randn(3, 3)` |
| Forward pass | `output = model(input)` |
| Calculate loss | `loss = criterion(output, target)` |
| Zero gradients | `optimizer.zero_grad()` |
| Backward pass | `loss.backward()` |
| Update weights | `optimizer.step()` |
| Save model | `torch.save(model.state_dict(), 'file.pth')` |
| Load model | `model.load_state_dict(torch.load('file.pth'))` |
| GPU | `x = x.cuda()` or `x = x.to('cuda')` |

---

## 🧠 Placement Interview Questions

1. **What is PyTorch?**
   - Deep learning framework with tensors and autograd

2. **Tensor vs NumPy array?**
   - Tensors can run on GPU, support gradients

3. **What is autograd?**
   - Automatic differentiation (calculates gradients automatically)

4. **How does backward pass work?**
   - loss.backward() calculates gradients using chain rule

5. **What does optimizer.step() do?**
   - Updates model weights based on gradients

6. **Why zero_grad() is needed?**
   - Clears old gradients before new backward pass

7. **What's the difference between view() and reshape()?**
   - Both reshape; view requires contiguous tensors

8. **What is CrossEntropyLoss used for?**
   - Multi-class classification loss

9. **Why normalize data?**
   - Makes training faster and more stable

10. **What is requires_grad?**
    - Flag to track gradients for a tensor

11. **How to prevent overfitting?**
    - Dropout, regularization, early stopping

12. **What does model.eval() do?**
    - Sets model to evaluation mode (disables dropout)

13. **What is batch size?**
    - Number of samples processed before gradient update

14. **Difference between training and evaluation?**
    - Training updates weights, evaluation only predicts

15. **How to use GPU?**
    - `x = x.cuda()` or move model/data to GPU

---

## 🔥 Complete Training Example

```python
import torch
import torch.nn as nn
import torch.optim as optim

# 1. Create model
class SimpleNet(nn.Module):
    def __init__(self):
        super().__init__()
        self.fc1 = nn.Linear(10, 20)
        self.fc2 = nn.Linear(20, 2)
    
    def forward(self, x):
        x = torch.relu(self.fc1(x))
        x = self.fc2(x)
        return x

# 2. Setup
model = SimpleNet()
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr=0.001)

# 3. Data
X = torch.randn(100, 10)
y = torch.randint(0, 2, (100,))

# 4. Train
for epoch in range(20):
    output = model(X)
    loss = criterion(output, y)
    
    optimizer.zero_grad()
    loss.backward()
    optimizer.step()
    
    if (epoch + 1) % 5 == 0:
        print(f"Loss: {loss.item():.4f}")
```

---

> 💡 **Tip:** Tensors + Autograd + Neural Networks = The PyTorch Trinity for Deep Learning! 🚀
