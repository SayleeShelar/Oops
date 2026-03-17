# 📊 NumPy - Complete Beginner's Revision Guide

> Master NumPy for numerical computing with fast arrays 🎯

---

## 1. 📌 What is NumPy?

**NumPy** = Numerical Python library for numerical computing

**Key Features:**
- ✅ **N-dimensional arrays** (ndarrays) - faster than lists
- ✅ Mathematical operations on entire arrays
- ✅ Linear algebra, Fourier transforms
- ✅ Statistical operations
- ✅ Broadcasting (automatic dimension expansion)

**Why NumPy?**
- 50-100x faster than Python lists
- Less memory usage
- Easier mathematical operations

**Use Cases:**
- Numerical computing
- Physics simulations
- Image processing
- Machine learning preprocessing

---

## 2. 🔧 Installation & Import

```python
# Install
# pip install numpy

# Import
import numpy as np

# Check version
print(np.__version__)
```

---

## 3. 📦 Creating Arrays

### From Lists:
```python
# 1D array
arr = np.array([1, 2, 3, 4, 5])
print(arr)          # [1 2 3 4 5]

# 2D array
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(arr)
# [[1 2 3]
#  [4 5 6]]

# 3D array
arr = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
```

### Special Arrays:
```python
# Array of zeros
arr = np.zeros(5)           # [0. 0. 0. 0. 0.]
arr = np.zeros((3, 3))      # 3x3 matrix of zeros

# Array of ones
arr = np.ones(5)            # [1. 1. 1. 1. 1.]

# Array of same value
arr = np.full(5, 7)         # [7 7 7 7 7]

# Range of numbers
arr = np.arange(0, 10, 2)   # [0 2 4 6 8]

# Evenly spaced numbers
arr = np.linspace(0, 10, 5) # [0. 2.5 5. 7.5 10.]

# Random integers
arr = np.random.randint(0, 10, 5)   # [3 7 1 9 2]

# Random floats (0-1)
arr = np.random.rand(5)     # [0.23 0.68 0.12 ...]

# Identity matrix
arr = np.eye(3)
# [[1. 0. 0.]
#  [0. 1. 0.]
#  [0. 0. 1.]]
```

---

## 4. 🔍 Array Properties

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])

print(arr.shape)        # (2, 3) - 2 rows, 3 columns
print(arr.size)         # 6 - total elements
print(arr.dtype)        # int64 - data type
print(arr.ndim)         # 2 - number of dimensions
print(arr.itemsize)     # 8 - bytes per element

# Reshape
arr_reshaped = arr.reshape(3, 2)
# [[1 2]
#  [3 4]
#  [5 6]]

# Flatten to 1D
arr_flat = arr.flatten()  # [1 2 3 4 5 6]
```

---

## 5. 🔂 Indexing & Slicing

### 1D Array:
```python
arr = np.array([10, 20, 30, 40, 50])

print(arr[0])       # 10
print(arr[-1])      # 50
print(arr[1:4])     # [20 30 40]
print(arr[::2])     # [10 30 50] (step by 2)
print(arr[::-1])    # [50 40 30 20 10] (reverse)
```

### 2D Array:
```python
arr = np.array([[1, 2, 3], 
                [4, 5, 6],
                [7, 8, 9]])

print(arr[0])       # [1 2 3] - first row
print(arr[0, 2])    # 3 - element at row 0, col 2
print(arr[1:3, 1:3])  # Sub-matrix
# [[5 6]
#  [8 9]]

print(arr[0, :])    # [1 2 3] - entire first row
print(arr[:, 2])    # [3 6 9] - entire third column
```

---

## 6. ➕ Array Operations

### Arithmetic Operations:
```python
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

print(arr1 + arr2)      # [5 7 9]
print(arr1 - arr2)      # [-3 -3 -3]
print(arr1 * arr2)      # [4 10 18]
print(arr1 / arr2)      # [0.25 0.4 0.5]
print(arr1 ** 2)        # [1 4 9]

# Element-wise operations
arr = np.array([1, 2, 3])
print(arr + 10)         # [11 12 13]
print(arr * 2)          # [2 4 6]
print(np.sqrt(arr))     # [1. 1.41 1.73]
```

### Universal Functions (ufuncs):
```python
arr = np.array([-1, 0, 1, 2, 3])

print(np.abs(arr))      # [1 0 1 2 3] - absolute
print(np.sqrt(4))       # 2.0 - square root
print(np.exp(arr))      # [0.37 1. 2.72 7.39 20.09] - exponential
print(np.log([1, 2.71, 7.39]))  # [0. 1. 2.] - natural log
print(np.sin(arr))      # sine
print(np.cos(arr))      # cosine
```

---

## 7. 📊 Statistical Operations

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])

print(arr.sum())        # 55
print(arr.mean())       # 5.5
print(arr.median())     # Can't use on array, use np.median()
print(np.median(arr))   # 5.5
print(arr.std())        # Standard deviation
print(arr.var())        # Variance
print(arr.min())        # 1
print(arr.max())        # 10
print(np.percentile(arr, 50))  # 50th percentile (median)

# 2D array operations
arr2d = np.array([[1, 2, 3], 
                  [4, 5, 6]])

print(arr2d.sum())      # 21 (sum all)
print(arr2d.sum(axis=0))  # [5 7 9] (sum columns)
print(arr2d.sum(axis=1))  # [6 15] (sum rows)
print(arr2d.mean(axis=0))  # [2.5 3.5 4.5]
```

---

## 8. 🎯 Broadcasting

Broadcasting automatically expands arrays to compatible shapes.

```python
arr1 = np.array([[1, 2, 3],
                 [4, 5, 6]])  # Shape: (2, 3)

arr2 = np.array([10, 20, 30])  # Shape: (3,)

# Broadcasting: arr2 is repeated for each row
result = arr1 + arr2
# [[11 22 33]
#  [14 25 36]]

# Scalar broadcasting
result = arr1 * 2
# [[2  4  6]
#  [8 10 12]]
```

---

## 9. 🔀 Sorting & Searching

### Sorting:
```python
arr = np.array([3, 1, 4, 1, 5, 9, 2, 6])

sorted_arr = np.sort(arr)
print(sorted_arr)       # [1 1 2 3 4 5 6 9]

# 2D sorting
arr2d = np.array([[3, 1], [2, 4]])
sorted_2d = np.sort(arr2d, axis=1)  # Sort each row
print(sorted_2d)
# [[1 3]
#  [2 4]]

# Indices that would sort array
indices = np.argsort(arr)
print(indices)          # [1 3 6 0 2 4 7 5]
```

### Searching:
```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])

# Find indices where condition is true
indices = np.where(arr > 5)
print(indices)          # (array([5, 6, 7, 8]),)
print(arr[indices])     # [6 7 8 9]

# Find closest value
idx = np.argmin(np.abs(arr - 5.5))  # Find index closest to 5.5

# Find max/min indices
print(np.argmax(arr))   # 8 (index of max)
print(np.argmin(arr))   # 0 (index of min)
```

---

## 10. 🔗 Concatenation & Stacking

```python
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

# Concatenate horizontally
result = np.concatenate([arr1, arr2])
print(result)           # [1 2 3 4 5 6]

# Stack vertically (create 2D)
result = np.vstack([arr1, arr2])
print(result)
# [[1 2 3]
#  [4 5 6]]

# Stack horizontally
result = np.hstack([arr1, arr2])
print(result)           # [1 2 3 4 5 6]

# Add dimension
result = np.column_stack([arr1, arr2])
print(result)
# [[1 4]
#  [2 5]
#  [3 6]]
```

---

## 11. 🧩 Matrix Operations

```python
arr1 = np.array([[1, 2], [3, 4]])
arr2 = np.array([[5, 6], [7, 8]])

# Element-wise multiplication
print(arr1 * arr2)
# [[ 5 12]
#  [21 32]]

# Matrix multiplication (dot product)
print(np.dot(arr1, arr2))
print(arr1 @ arr2)  # @ operator (Python 3.5+)
# [[19 22]
#  [43 50]]

# Transpose
print(arr1.T)
# [[1 3]
#  [2 4]]

# Determinant
print(np.linalg.det(arr1))  # -2.0

# Inverse
print(np.linalg.inv(arr1))
# [[-2.   1. ]
#  [ 1.5 -0.5]]

# Eigenvalues and eigenvectors
eigenvalues, eigenvectors = np.linalg.eig(arr1)
```

---

## 12. 📋 Boolean Indexing

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])

# Keep elements > 5
result = arr[arr > 5]
print(result)           # [6 7 8 9 10]

# Multiple conditions
result = arr[(arr > 3) & (arr < 8)]
print(result)           # [4 5 6 7]

# Using np.where for conditional operations
result = np.where(arr > 5, arr * 2, arr)
# If > 5: multiply by 2, else: keep original
print(result)           # [1 2 3 4 5 12 14 16 18 20]
```

---

## 13. 🎲 Random Numbers

```python
# Set seed for reproducibility
np.random.seed(42)

# Random integers
arr = np.random.randint(0, 10, 5)  # 5 random integers 0-9
print(arr)

# Random floats (0-1)
arr = np.random.rand(3, 3)  # 3x3 matrix

# From normal distribution
arr = np.random.randn(1000)  # 1000 values from normal dist

# Random choice from array
arr = np.array([1, 2, 3, 4, 5])
choice = np.random.choice(arr, 3)  # Pick 3 random items

# Shuffle
arr = np.array([1, 2, 3, 4, 5])
np.random.shuffle(arr)  # Shuffle in-place
```

---

## 14. 🔧 Useful Functions

### Data Type Conversion:
```python
arr = np.array([1.5, 2.7, 3.2])

# Convert to int
arr_int = arr.astype(int)  # [1 2 3]

# Convert to string
arr_str = arr.astype(str)  # ['1.5' '2.7' '3.2']
```

### Unique & Counts:
```python
arr = np.array([1, 2, 2, 3, 3, 3, 4])

unique = np.unique(arr)
print(unique)           # [1 2 3 4]

unique, counts = np.unique(arr, return_counts=True)
print(counts)           # [1 2 3 1]
```

### Difference:
```python
arr = np.array([1, 2, 4, 7, 0])
diff = np.diff(arr)
print(diff)             # [1 2 3 -7]
```

---

## 15. 📊 Useful Methods Summary

### Creation:
```
np.array() np.zeros() np.ones() np.arange() np.linspace()
np.random.rand() np.random.randint() np.eye() np.full()
```

### Inspection:
```
.shape .size .dtype .ndim .reshape() .flatten()
```

### Operations:
```
+, -, *, /, ** np.sqrt() np.exp() np.log()
np.sin() np.cos() np.abs() np.exp()
```

### Statistics:
```
.sum() .mean() .std() .var() .min() .max() .argmin() .argmax()
```

### Array Manipulation:
```
np.concatenate() np.vstack() np.hstack() np.column_stack()
np.sort() np.argsort() np.where() np.unique()
```

---

## 📋 Common Operations Table

| Operation | Code | Result |
|---|---|---|
| Create array | `np.array([1, 2, 3])` | [1 2 3] |
| Zeros | `np.zeros(5)` | [0. 0. 0. 0. 0.] |
| Ones | `np.ones(5)` | [1. 1. 1. 1. 1.] |
| Range | `np.arange(0, 10, 2)` | [0 2 4 6 8] |
| Reshape | `arr.reshape(2, 3)` | 2x3 matrix |
| Sum | `arr.sum()` | Total sum |
| Mean | `arr.mean()` | Average |
| Max | `arr.max()` | Maximum |
| Sort | `np.sort(arr)` | Sorted array |
| Dot product | `np.dot(a, b)` | Matrix multiplication |

---

## 🧠 Placement Interview Questions

1. **What is NumPy?**
   - Library for numerical computing with fast arrays

2. **Why use NumPy over Python lists?**
   - 50-100x faster, less memory, easier math operations

3. **What's an ndarray?**
   - N-dimensional array (NumPy's main object)

4. **How to create an array of zeros?**
   - `np.zeros((3, 3))`

5. **What's the difference between . and np.dot()?**
   - Same thing; `@` is matrix multiplication operator

6. **How to get array shape?**
   - `arr.shape` returns (rows, columns)

7. **What is broadcasting?**
   - Automatic dimension expansion for operations

8. **How to reshape array?**
   - `arr.reshape(new_shape)`

9. **How to sum specific axis?**
   - `arr.sum(axis=0)` for columns, `axis=1` for rows

10. **What does flatten do?**
    - Converts multi-dimensional array to 1D

11. **How to sort array?**
    - `np.sort(arr)` or `np.argsort()` for indices

12. **How to get unique elements?**
    - `np.unique(arr)`

13. **What's boolean indexing?**
    - `arr[arr > 5]` to filter elements

14. **How to concatenate arrays?**
    - `np.concatenate([arr1, arr2])`

15. **How to multiply matrices?**
    - `np.dot(arr1, arr2)` or `arr1 @ arr2`

---

> 💡 **Tip:** NumPy = Fast arrays + Math operations. Use for preprocessing data before machine learning! 🚀
