# Pandas/CSV

## Load a CSV (one‑liner)

**What this does:** Imports pandas and reads a CSV file into a DataFrame named `df`. From here on, `df` is your in‑memory table.

```python
import pandas as pd

df = pd.read_csv("(name of file).csv")  # load CSV -> DataFrame
```

---

## Part A: Intro to Pandas!

### Understanding DataFrames

**What this does:** Creates a tiny dataset (a list of dictionaries), converts it into a DataFrame, and displays it.

```python
import pandas as pd

# 1) Create a small in‑memory dataset (list of row‑dictionaries)
l = [{'a': 1, 'b': 2}, {'a': -2, 'b': 0}]

# 2) Turn it into a DataFrame (a table with columns a, b)
df = pd.DataFrame(l)

# 3) Display the DataFrame (in notebooks this renders a table)
df
#    a  b
# 0  1  2
# 1 -2  0
```

**What this does:** Shows how to inspect the index, raw NumPy values, and the Python type of a single column.

```python
# Index is the row labels; values is the underlying 2D NumPy array
print(df.index)   # RangeIndex(start=0, stop=2, step=1)
print(df.values)  # array([[ 1,  2],
                  #        [-2,  0]])

# Selecting a single column returns a Series (1D labeled array)
print(type(df['a']))  # pandas.core.series.Series
```

---

### CSV Essentials (read, peek, clean, save)

**What this does:** Demonstrates common patterns for reading a CSV, previewing it, handling missing data, and saving a cleaned copy.

```python
import pandas as pd

# Read a CSV (common options)
# - parse_dates=['colA', ...]: auto‑parse listed columns as datetime
# - usecols=['col1','col2']: load only selected columns
# - dtype={'col': 'Int64'}: force data types on read

# If your file lives at data/students.csv
df = pd.read_csv('data/students.csv', parse_dates=['enroll_date'])

# Or if using the provided article file in the project root
# df = pd.read_csv('article_previews.csv')

# Quick peek at shape, first rows, dtypes/nulls, and numeric summary
print(df.shape)      # (rows, cols)
print(df.head())     # first 5 rows
print(df.info())     # column dtypes + non‑null counts
print(df.describe()) # numeric summary stats

# Null handling examples (pick what fits your data)
# Drop rows missing a required field, e.g., Program
# df = df.dropna(subset=['Program'])

# Fill numeric nulls with a statistic, e.g., median age
# df['Age'] = df['Age'].fillna(df['Age'].median())

# Save a cleaned version without the index column
# df.to_csv('data/students_clean.csv', index=False)
```

> If you are using `article_previews.csv` instead of `students.csv`, swap column names accordingly (for example, `df['tag']`, `df['title']`, `df['year']`).

---

### Column Access and Lists

**What this does:** Shows several ways to access columns, convert them to Python lists, get unique values, filter rows by membership, and sort.

```python
# Single column -> Series
programs = df['Program']            # pandas Series

# Convert a column to a plain Python list
program_list = df['Program'].tolist()

# Unique values from a column (dropping NaN), returned as a list
unique_programs = df['Program'].dropna().unique().tolist()

# Multiple columns -> new DataFrame with just those columns
mini = df[['Name', 'Program', 'Age']]

# Filter rows by membership (keep only Physics or Chemistry)
stem = df[df['Program'].isin(['Physics', 'Chemistry'])]

# Sort by multiple columns; here, youngest first then lowest Student ID
best_young = df.sort_values(['Age', 'Student ID'], ascending=[True, True]).head(10)
```

---

### Filtering, Subsetting, Sorting, Counting

**What this does:** Demonstrates boolean filters, label‑ vs position‑based column selection, sorting, and quick category counts.

```python
# Boolean filter: keep rows where column 'a' is positive
filtered_df = df[df['a'] > 0]

# Label vs. position indexing (same two columns picked in different ways)
subset_loc  = df.loc[:, ['a', 'b']]   # by column names
subset_iloc = df.iloc[:, [0, 1]]      # by column positions

# Sorting by a single column
sorted_df = df.sort_values(by='a')

# Top categories by frequency in a column (uncomment and adjust column name)
# df['Program'].value_counts().head(10)
```

---

## That’s it!
You now know how to load CSV files into a DataFrame, preview and inspect the data, pick out columns/rows, handle missing values at a basic level, and save a cleaned file. For many beginner tasks, this is enough to get real work done with pandas.

