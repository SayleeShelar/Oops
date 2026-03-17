# 🐼 Pandas - Complete Beginner's Revision Guide

> Master Pandas for data manipulation & analysis with examples 🎯

---

## 1. 📌 What is Pandas?

**Pandas** = Python library for data manipulation and analysis

**Key Features:**
- ✅ Work with **tabular data** (like Excel sheets)
- ✅ Read/write CSV, Excel, JSON, SQL files
- ✅ Data cleaning and transformation
- ✅ Missing data handling
- ✅ Grouping and aggregation
- ✅ Merging and joining datasets

**Use Cases:**
- Data cleaning for machine learning
- Data analysis and exploration
- Time series analysis
- Data aggregation and summarization

---

## 2. 🔧 Installation & Import

```python
# Install
# pip install pandas

# Import
import pandas as pd

# Check version
print(pd.__version__)
```

---

## 3. 📊 Series (1D Data)

### Create Series:
```python
# From list
s = pd.Series([10, 20, 30, 40])
print(s)
# Output:
# 0    10
# 1    20
# 2    30
# 3    40

# With custom index
s = pd.Series([10, 20, 30], index=['a', 'b', 'c'])
print(s)
# Output:
# a    10
# b    20
# c    30

# From dictionary
s = pd.Series({'name': 'Alice', 'age': 25, 'city': 'Delhi'})
print(s)
# Output:
# name       Alice
# age           25
# city       Delhi
```

### Series Operations:
```python
s = pd.Series([10, 20, 30, 40, 50])

print(s[0])             # 10
print(s[1:3])           # 20, 30
print(s.mean())         # 30.0
print(s.sum())          # 150
print(s.std())          # Standard deviation
print(s.max())          # 50
print(s.min())          # 10
print(s.describe())     # Stats summary
```

---

## 4. 📋 DataFrame (2D Data - Most Important!)

### Create DataFrame:
```python
# From dictionary
data = {
    'Name': ['Alice', 'Bob', 'Carol'],
    'Age': [25, 30, 28],
    'City': ['Delhi', 'Mumbai', 'Bangalore']
}
df = pd.DataFrame(data)
print(df)
# Output:
#     Name  Age       City
# 0  Alice   25      Delhi
# 1    Bob   30     Mumbai
# 2  Carol   28  Bangalore

# From list of lists
df = pd.DataFrame([
    ['Alice', 25, 'Delhi'],
    ['Bob', 30, 'Mumbai']
], columns=['Name', 'Age', 'City'])

# From CSV
df = pd.read_csv('file.csv')

# From Excel
df = pd.read_excel('file.xlsx')
```

### Basic Information:
```python
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Carol'],
    'Age': [25, 30, 28],
    'Salary': [50000, 60000, 55000]
})

print(df.shape)         # (3, 3) - 3 rows, 3 columns
print(df.columns)       # ['Name', 'Age', 'Salary']
print(df.index)         # [0, 1, 2]
print(df.info())        # Column types and null counts
print(df.describe())    # Statistical summary
print(df.head())        # First 5 rows
print(df.tail())        # Last 5 rows
print(df.dtypes)        # Data types
```

---

## 5. 🔍 Accessing Data

### Column Access:
```python
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Carol'],
    'Age': [25, 30, 28]
})

# Method 1
print(df['Name'])       # Returns Series
print(df['Name'][0])    # Alice

# Method 2
print(df.Name)          # Attribute access
print(df.Age[1])        # 30

# Multiple columns
print(df[['Name', 'Age']])  # Returns DataFrame
```

### Row Access:
```python
# .loc[] - label-based
print(df.loc[0])        # First row
print(df.loc[0, 'Name']) # Alice

# .iloc[] - index-based
print(df.iloc[0])       # First row
print(df.iloc[0, 0])    # Alice

# Slicing
print(df.iloc[0:2])     # First 2 rows
print(df.loc[0:1, ['Name', 'Age']])  # Rows 0-1, Name & Age
```

### Boolean Indexing:
```python
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Carol'],
    'Age': [25, 30, 28],
    'Salary': [50000, 60000, 55000]
})

# Get all people older than 25
print(df[df['Age'] > 25])
# Output:
#    Name  Age  Salary
# 1   Bob   30   60000
# 2 Carol   28   55000

# Multiple conditions
print(df[(df['Age'] > 25) & (df['Salary'] > 55000)])
```

---

## 6. ➕ Adding & Removing Columns

### Add Column:
```python
df = pd.DataFrame({
    'Name': ['Alice', 'Bob'],
    'Age': [25, 30]
})

# Add new column
df['City'] = ['Delhi', 'Mumbai']
df['Grade'] = [5, 4.5]

# Add calculated column
df['Birth_Year'] = 2024 - df['Age']

print(df)
#    Name  Age     City  Grade  Birth_Year
# 0  Alice   25    Delhi    5.0        1999
# 1    Bob   30   Mumbai    4.5        1994
```

### Rename Column:
```python
df = df.rename(columns={'Age': 'Years', 'City': 'Location'})

# In-place
df.rename(columns={'Name': 'Full_Name'}, inplace=True)
```

### Remove Column:
```python
# Drop column
df = df.drop('Birth_Year', axis=1)

# Drop multiple
df = df.drop(['City', 'Grade'], axis=1)

# Drop row
df = df.drop(0)  # Drop row 0
```

---

## 7. 🧹 Handling Missing Data

### Find Missing Data:
```python
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', None],
    'Age': [25, None, 28],
    'Salary': [50000, 60000, 55000]
})

print(df.isnull())      # Shows True where null
print(df.notnull())     # Opposite
print(df.isnull().sum()) # Count of nulls per column
```

### Handle Missing Data:
```python
# Drop rows with missing data
df = df.dropna()

# Drop columns with missing data
df = df.dropna(axis=1)

# Fill missing values
df = df.fillna(0)           # Fill with 0
df = df.fillna('Unknown')   # Fill with 'Unknown'

# Forward fill (use previous value)
df = df.fillna(method='ffill')

# Backward fill
df = df.fillna(method='bfill')

# Mean/median fill
df['Age'] = df['Age'].fillna(df['Age'].mean())
```

---

## 8. 📊 Data Statistics

```python
df = pd.DataFrame({
    'Subject': ['Math', 'Science', 'English'],
    'Score': [85, 90, 78]
})

print(df.mean())        # Mean of each column
print(df.median())      # Median
print(df.std())         # Standard deviation
print(df.var())         # Variance
print(df.sum())         # Sum
print(df.min())         # Minimum
print(df.max())         # Maximum
print(df.count())       # Count of non-null
print(df.describe())    # Statistical summary

# For specific column
print(df['Score'].mean())       # 84.33
print(df['Score'].median())     # 85
```

---

## 9. 🔀 Sorting & Filtering

### Sorting:
```python
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Carol'],
    'Age': [25, 30, 28]
})

# Sort by column
df_sorted = df.sort_values('Age')
df_sorted = df.sort_values('Age', ascending=False)

# Sort by multiple columns
df_sorted = df.sort_values(['Age', 'Name'])

# In-place
df.sort_values('Age', inplace=True)
```

### Filtering:
```python
# Single condition
young = df[df['Age'] < 28]

# Multiple conditions
result = df[(df['Age'] > 25) & (df['Age'] < 30)]

# Using isin()
result = df[df['Name'].isin(['Alice', 'Bob'])]

# Using between()
result = df[df['Age'].between(25, 28)]
```

---

## 10. 📈 GroupBy & Aggregation

```python
df = pd.DataFrame({
    'Department': ['IT', 'IT', 'HR', 'HR', 'Sales'],
    'Name': ['Alice', 'Bob', 'Carol', 'David', 'Eve'],
    'Salary': [50000, 60000, 45000, 47000, 55000]
})

# Group by department
grouped = df.groupby('Department')

# Get statistics per group
print(grouped['Salary'].mean())
# Output:
# Department
# HR       46000
# IT       55000
# Sales    55000

print(grouped['Salary'].sum())
print(grouped.size())           # Count in each group

# Multiple aggregations
agg_data = grouped['Salary'].agg(['mean', 'sum', 'count', 'std'])
print(agg_data)
```

### Custom Aggregation:
```python
result = df.groupby('Department').agg({
    'Salary': ['mean', 'max', 'min'],
    'Name': 'count'
})
print(result)
```

---

## 11. 🔗 Merging & Joining

### Merge (SQL-like):
```python
df1 = pd.DataFrame({
    'ID': [1, 2, 3],
    'Name': ['Alice', 'Bob', 'Carol']
})

df2 = pd.DataFrame({
    'ID': [1, 2, 3],
    'Salary': [50000, 60000, 55000]
})

# Inner join (only matching)
result = pd.merge(df1, df2, on='ID')
# Output:
#   ID    Name  Salary
# 0  1   Alice   50000
# 1  2     Bob   60000
# 2  3   Carol   55000

# Left join (keep all from df1)
result = pd.merge(df1, df2, on='ID', how='left')

# Right join
result = pd.merge(df1, df2, on='ID', how='right')

# Outer join (all from both)
result = pd.merge(df1, df2, on='ID', how='outer')
```

### Concatenate:
```python
df1 = pd.DataFrame({'A': [1, 2], 'B': [3, 4]})
df2 = pd.DataFrame({'A': [5, 6], 'B': [7, 8]})

# Stack vertically
result = pd.concat([df1, df2])
#    A  B
# 0  1  3
# 1  2  4
# 0  5  7
# 1  6  8

# Stack horizontally
result = pd.concat([df1, df2], axis=1)
```

---

## 12. 📁 Reading & Writing Files

### Read Files:
```python
# CSV
df = pd.read_csv('file.csv')

# Excel
df = pd.read_excel('file.xlsx', sheet_name='Sheet1')

# JSON
df = pd.read_json('file.json')

# With parameters
df = pd.read_csv('file.csv', delimiter=',', header=0, nrows=100)
```

### Write Files:
```python
# To CSV
df.to_csv('output.csv', index=False)

# To Excel
df.to_excel('output.xlsx', index=False)

# To JSON
df.to_json('output.json')

# To SQL
import sqlalchemy
df.to_sql('table_name', conn, if_exists='replace')
```

---

## 13. 🧭 Data Cleaning Examples

### Example 1: Remove Duplicates
```python
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Alice', 'Carol'],
    'Age': [25, 30, 25, 28]
})

# Remove duplicate rows
df = df.drop_duplicates()

# Remove duplicates based on column
df = df.drop_duplicates(subset=['Name'])
```

### Example 2: Change Data Types
```python
df['Age'] = df['Age'].astype(int)
df['Score'] = df['Score'].astype(float)
df['Date'] = pd.to_datetime(df['Date'])
```

### Example 3: String Operations
```python
df = pd.DataFrame({'Name': ['Alice', 'Bob', 'Carol']})

# Uppercase
df['Name'] = df['Name'].str.upper()

# Lowercase
df['Name'] = df['Name'].str.lower()

# Contains
print(df[df['Name'].str.contains('Al')])

# Replace
df['Name'] = df['Name'].str.replace('Al', 'Alabama')

# Get length
df['Name_Length'] = df['Name'].str.len()
```

---

## 14. 📊 Data Visualization (with Pandas)

```python
import matplotlib.pyplot as plt

df = pd.DataFrame({
    'Month': ['Jan', 'Feb', 'Mar', 'Apr'],
    'Sales': [100, 150, 120, 180]
})

# Line plot
df.plot(x='Month', y='Sales')
plt.show()

# Bar chart
df.plot(x='Month', y='Sales', kind='bar')
plt.show()

# Histogram
df['Sales'].plot(kind='hist', bins=10)
plt.show()
```

---

## 15. 🎯 Most Used Methods

### Data Inspection:
```
.head() .tail() .info() .describe() .shape .columns .dtypes
.value_counts() .nunique() .isnull() .notnull() .duplicated()
```

### Data Manipulation:
```
.drop() .rename() .sort_values() .groupby() .agg()
.apply() .merge() .concat() .fillna() .dropna()
```

### Calculations:
```
.sum() .mean() .median() .std() .var() .min() .max()
.corr() .cov() .quantile() .rank()
```

---

## 📋 Common Operations Table

| Operation | Code | Result |
|---|---|---|
| Read CSV | `df = pd.read_csv('file.csv')` | Load data |
| First 5 rows | `df.head()` | Show top |
| Last 5 rows | `df.tail()` | Show bottom |
| Shape | `df.shape` | (rows, cols) |
| Info | `df.info()` | Column details |
| Stats | `df.describe()` | Summary statistics |
| Column mean | `df['col'].mean()` | Average |
| Filter | `df[df['col'] > 5]` | Conditional rows |
| Sort | `df.sort_values('col')` | Sort by column |
| Group | `df.groupby('col').mean()` | Group aggregation |
| Merge | `pd.merge(df1, df2)` | Join tables |

---

## 🧠 Placement Interview Questions

1. **What is Pandas used for?**
   - Data manipulation, cleaning, analysis

2. **Difference between Series and DataFrame?**
   - Series is 1D (like list), DataFrame is 2D (like table)

3. **How to handle missing data?**
   - Drop with dropna(), fill with fillna()

4. **How to read CSV?**
   - `pd.read_csv('file.csv')`

5. **What's groupby used for?**
   - Group data by categories and compute statistics

6. **How to merge dataframes?**
   - `pd.merge(df1, df2, on='key')`

7. **What does apply() do?**
   - Applies function to each element

8. **How to remove duplicates?**
   - `df.drop_duplicates()`

9. **How to sort a dataframe?**
   - `df.sort_values('column')`

10. **What's loc vs iloc?**
    - loc uses labels, iloc uses integer positions

11. **How to create new column?**
    - `df['new'] = calculation`

12. **How to change data type?**
    - `df['col'].astype(int)`

13. **What's filter with boolean indexing?**
    - `df[df['col'] > value]`

14. **How to concatenate dataframes?**
    - `pd.concat([df1, df2])`

15. **How to get summary statistics?**
    - `df.describe()`

---

> 💡 **Tip:** Load CSV → Explore with head/describe → Clean data → Analyze with groupby → Visualize! 🚀
