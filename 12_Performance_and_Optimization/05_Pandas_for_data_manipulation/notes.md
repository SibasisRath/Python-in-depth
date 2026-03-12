# Pandas for Data Manipulation

## Explanation

Pandas provides data structures like DataFrame and Series for efficient data analysis. Built on NumPy, it handles tabular data with operations like filtering, grouping, and merging. Use for data cleaning, exploration, and transformation. Key features: vectorized operations, missing data handling, and time series support.

Key concepts:
- `pd.DataFrame` for 2D data
- `pd.Series` for 1D data
- Indexing with `.loc`, `.iloc`
- GroupBy operations and aggregations

## Examples

```python
import pandas as pd

# Create DataFrame
data = {'Name': ['Alice', 'Bob'], 'Age': [25, 30]}
df = pd.DataFrame(data)

# Filter and group
adults = df[df['Age'] > 26]
grouped = df.groupby('Age').mean()
```

## Tasks

### Beginner
1. Load a CSV into a DataFrame and display basic statistics.
2. Perform filtering and sorting on a dataset.

### Intermediate
1. Handle missing data with `fillna()` and `dropna()`.
2. Merge two DataFrames using `pd.merge()`.

### Advanced
1. Perform time series analysis on date-indexed data.
2. Optimize memory usage for large datasets.

## Quick Review
- What is the primary data structure in Pandas for tabular data?
- How do you select rows in a DataFrame by label?
