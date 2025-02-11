# Module 2: Essential Python Libraries

## Overview
This module covers fundamental Python libraries commonly used in data processing and visualization.

## Table of Contents
1. [NumPy](#1-numpy)
2. [Pandas](#2-pandas)
3. [Matplotlib](#3-matplotlib)
4. [SciPy](#4-scipy)

## 1. NumPy
NumPy is a library for numerical computing in Python.

### 1.1 Arrays and Basic Operations
```python
import numpy as np

# Creating arrays
array_1d = np.array([1, 2, 3, 4, 5])
array_2d = np.array([[1, 2, 3], [4, 5, 6]])

# Array initialization
zeros = np.zeros((3, 3))        # Array of zeros
ones = np.ones((2, 2))          # Array of ones
random_array = np.random.rand(3, 3)  # Random values between 0 and 1
range_array = np.arange(0, 10, 2)    # Array with step size

# Basic operations
addition = array_1d + 2         # Add 2 to each element
multiplication = array_1d * 3    # Multiply each element by 3
power = array_1d ** 2           # Square each element
```

### 1.2 Array Manipulation
```python
# Reshaping arrays
reshaped = array_1d.reshape(5, 1)  # Convert to column vector
flattened = array_2d.flatten()     # Convert to 1D array

# Array concatenation
horizontal = np.hstack((array_1d, array_1d))
vertical = np.vstack((array_1d, array_1d))

# Array splitting
split_arrays = np.split(array_1d, 5)  # Split into 5 parts

# Indexing and slicing
element = array_2d[0, 1]        # Single element
row = array_2d[0, :]           # Entire row
column = array_2d[:, 0]        # Entire column
subset = array_2d[0:2, 1:3]    # Subset of array
```

### 1.3 Mathematical Operations
```python
# Statistical operations
mean = np.mean(array_1d)
median = np.median(array_1d)
std = np.std(array_1d)
var = np.var(array_1d)

# Linear algebra
matrix_a = np.array([[1, 2], [3, 4]])
matrix_b = np.array([[5, 6], [7, 8]])

dot_product = np.dot(matrix_a, matrix_b)
determinant = np.linalg.det(matrix_a)
inverse = np.linalg.inv(matrix_a)
eigenvalues = np.linalg.eigvals(matrix_a)
```

## 2. Pandas
Pandas is a library for data manipulation and analysis.

### 2.1 Series and DataFrames
```python
import pandas as pd

# Creating Series
series = pd.Series([1, 2, 3, 4, 5], name='numbers')
series_with_index = pd.Series([1, 2, 3], index=['a', 'b', 'c'])

# Creating DataFrames
data = {
    'name': ['John', 'Anna', 'Peter'],
    'age': [28, 22, 35],
    'city': ['New York', 'Paris', 'London']
}
df = pd.DataFrame(data)

# Reading data
csv_df = pd.read_csv('data.csv')
excel_df = pd.read_excel('data.xlsx')
json_df = pd.read_json('data.json')
```

### 2.2 Data Manipulation
```python
# Selecting data
names = df['name']                  # Select single column
subset = df[['name', 'age']]       # Select multiple columns
filtered = df[df['age'] > 25]      # Filter rows

# Adding and modifying data
df['salary'] = [50000, 60000, 75000]  # Add new column
df.loc[3] = ['Sarah', 30, 'Berlin']   # Add new row
df['age'] = df['age'] + 1             # Modify column

# Handling missing values
df.dropna()                        # Remove rows with missing values
df.fillna(0)                       # Fill missing values with 0
df.fillna(method='ffill')         # Forward fill missing values
```

### 2.3 Data Analysis
```python
# Basic statistics
summary = df.describe()            # Statistical summary
mean_age = df['age'].mean()       # Column mean
correlation = df.corr()            # Correlation matrix

# Grouping and aggregation
grouped = df.groupby('city')
city_stats = grouped.agg({
    'age': ['mean', 'min', 'max'],
    'salary': 'mean'
})

# Sorting
sorted_df = df.sort_values('age', ascending=False)
```

## 3. Matplotlib
Matplotlib is a library for creating static visualizations.

### 3.1 Basic Plotting
```python
import matplotlib.pyplot as plt

# Line plot
plt.figure(figsize=(10, 6))
plt.plot([1, 2, 3, 4], [1, 4, 2, 3])
plt.title('Simple Line Plot')
plt.xlabel('X axis')
plt.ylabel('Y axis')
plt.grid(True)
plt.show()

# Scatter plot
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]
plt.scatter(x, y)
plt.show()
```

### 3.2 Multiple Plots
```python
# Subplots
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))
ax1.plot([1, 2, 3], [1, 2, 3], 'r-')
ax2.scatter([1, 2, 3], [1, 2, 3], c='b')
plt.tight_layout()
plt.show()

# Different plot types
plt.figure(figsize=(10, 6))
plt.subplot(2, 2, 1)
plt.plot([1, 2, 3], [1, 2, 3])
plt.subplot(2, 2, 2)
plt.scatter([1, 2, 3], [1, 2, 3])
plt.subplot(2, 2, 3)
plt.bar([1, 2, 3], [1, 2, 3])
plt.subplot(2, 2, 4)
plt.hist([1, 2, 2, 3, 3, 3])
plt.tight_layout()
plt.show()
```

## 4. SciPy
SciPy is a library for scientific and technical computing.

### 4.1 Basic Statistics
```python
from scipy import stats

# Descriptive statistics
data = [1, 2, 2, 3, 3, 3, 4, 4, 5]
mean = stats.tmean(data)
variance = stats.tvar(data)
skewness = stats.skew(data)
kurtosis = stats.kurtosis(data)

# Probability distributions
normal_dist = stats.norm(loc=0, scale=1)
samples = normal_dist.rvs(1000)
```

### 4.2 Optimization
```python
from scipy import optimize

# Function to minimize
def f(x):
    return (x[0] - 1)**2 + (x[1] - 2)**2

# Minimize function
result = optimize.minimize(f, [0, 0])
print(result.x)  # Optimal values
```

## Practice Exercises

### Exercise 1: Data Analysis
```python
def analyze_data(filename):
    """
    Load a CSV file and perform basic analysis using pandas.
    Calculate statistics and create visualizations.
    """
    # Load data
    df = pd.read_csv(filename)
    
    # Basic statistics
    stats = df.describe()
    
    # Create visualizations
    plt.figure(figsize=(12, 6))
    df.hist()
    plt.tight_layout()
    plt.show()
    
    return stats

# Test the function
# analyze_data('data.csv')  # Uncomment to test with actual file
```

## Summary
This module covered:
- NumPy for numerical computing
- Pandas for data manipulation
- Matplotlib for visualization
- SciPy for scientific computing

## Next Steps
- Practice with real datasets
- Explore advanced features of each library
- Learn about other visualization libraries (Seaborn, Plotly) 
