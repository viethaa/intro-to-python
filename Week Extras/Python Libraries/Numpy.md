# NumPy Tutorial 

A hands‑on guide built from real notes. Every snippet below is **runnable** and grouped by topic. Explanations tell you what each line does; **you run cells in your own notebook to see output**.

> Tip: Start a new Jupyter notebook and copy sections in order. Begin with the **Setup** cell.

---

## Setup

```python
import numpy as np
import matplotlib.pyplot as plt  # for the trig plots
from numpy import linalg as LA   # linear algebra
```

---

## 1) Creating arrays

Arrays are the core data structure in NumPy. Unlike Python lists, arrays store elements of a single dtype in contiguous memory, which enables very fast vectorized operations and broadcasting. In this section you’ll see common constructors (from lists, ranges, evenly spaced grids, zeros/ones) and how dtype, shape, and randomness work together. A good mental model is: choose a shape, choose a dtype, and let NumPy handle bulk math over the whole block.

```python
# Python list → NumPy array (1D)
list_1 = [1,2,3,4,5]
np_arr_1 = np.array(list_1, dtype=np.int64)  # fixed-width integer type
np_arr_1
```

**What it does:** Converts a Python list to a fixed‑dtype array. Arrays enable vectorized math and broadcasting.

```python
# 2D (matrix) from nested lists
m_list_1 = [[1,2,3], [4,5,6], [7,8,9]]
np_m_list_1 = np.array(m_list_1, dtype=np.int64)
np_m_list_1
```

**What it does:** Builds a 3×3 matrix.

```python
# Ranged constructors
np.arange(1, 10, 2)     # start=1, stop<10, step=2
np.linspace(0, 5, 5)    # 5 evenly spaced points from 0 to 5 inclusive
np.zeros(4)             # length‑4 vector of 0s (float by default)
np.zeros((2,3))         # 2×3 of 0s
np.ones((2,3))          # 2×3 of 1s
```

**What it does:** Quickly builds arrays with patterns, shapes, and default dtypes.

```python
# Introspection and basic props
np_m_list_1.size        # total element count (here 9)
np_arr_2 = np.array([1,2,3,4,5,6])
np_arr_2.dtype          # dtype is inferred (machine‑dependent defaults)
```

```python
# Random integers (reproducibility optional)
np.random.seed(0)
np.random.randint(10, 50, 50)          # 50 random ints in [10,50)
np.random.randint(10, 50, size=(2,3))  # 2×3 matrix of random ints
```

**What it does:** Samples integers. Seeding lets you reproduce results.

```python
# How to discover API: add a question mark in notebooks
# (Run this in a notebook cell to open help pane)
# np.random.randint?
```

**What it does:** In Jupyter, `?` shows docstrings.

---

## 2) Indexing, slicing, boolean masks, fancy indexing

Indexing is how you select and rearrange data without loops. Basic slices usually return **views** (no copy) while advanced indexing (lists/arrays of indices, boolean masks) returns **copies**. Boolean masks let you filter by conditions; fancy indexing lets you pull arbitrary positions. Keep track of whether you have a view or a copy, because in‑place edits on views modify the original array.

```python
# Shapes and basic element access
np_m_list_1.shape        # (3, 3)
np_m_list_1[0, 1]        # row 0, col 1 → 2
np_m_list_1.item(0, 2)   # same as [0,2] but returns a Python scalar
```

```python
# Gather by flat (raveled) indices, then write by flat indices
np.take(np_m_list_1, [0,3,6])                 # elements at flat idx 0,3,6
np.put(np_m_list_1, [0,3,6], [10,10,10])      # overwrite those positions
np_m_list_1
```

**What it does:** `take`/`put` operate on the **flattened** array order.

```python
# 1D slicing on an earlier 1D array
np_arr_1[:5:2]  # up to index 5 (exclusive) step by 2
```

```python
# Column selection, reversing rows
np_m_list_1[:, 1]   # second column
np_m_list_1[::-1]   # reverse row order
```

```python
# Boolean masks (filtering)
evens = np_m_list_1[np_m_list_1 % 2 == 0]
evens

np_m_list_1[np_m_list_1 > 5]                       # elements > 5
np_m_list_1[(np_m_list_1 > 5) | (np_m_list_1 == 10)]  # logical OR
```

```python
# Unique values
np.unique(np_m_list_1)
```

> **Note:** The commented lines below also work if you uncomment them; they mutate in place.

```python
# np_m_list_1[0,0] = 2         # direct assignment
# np_m_list_1.itemset((0,1),1) # itemset using a tuple index
```

---

## 3) Reshaping and reordering

Reshaping changes how data are interpreted without moving bytes when possible. Use `reshape` to change shape, `transpose/swapaxes` to permute axes, and `flatten` to produce 1D versions (row‑major by default or column‑major with `'F'`). `resize` is different: it may repeat or truncate data to force a requested shape. Sorting along an axis mutates in place, so check your assumptions before and after.

```python
np_m_list_1.reshape((1, 9))   # row vector (1×9)
np_m_list_1.reshape((-1, 1))  # column vector (9×1); -1 infers
np.resize(np_m_list_1, (2, 5))# resize (repeats/truncates data as needed)
np_m_list_1.transpose()       # swap axes for 2D: same as .T
np_m_list_1.swapaxes(0, 1)    # explicitly swap two axes
np_m_list_1.flatten()         # row‑major flatten
np_m_list_1.flatten('F')      # column‑major (Fortran) flatten
np_m_list_1.sort(axis=0)      # sort each column in place
np_m_list_1                   # inspect the in‑place change
```

**What it does:** Changes **view of shape** (reshape/transpose/swapaxes) or **data order** (flatten/sort). `resize` may repeat/truncate values.

---

## 4) Stacking and splitting

Real workflows stitch arrays together or break them apart. Vertical stacks add rows when the column counts match; horizontal stacks add columns when the row counts match. Column and row stacks are convenience wrappers around concatenation. Splitting is the inverse: cut an array into equal parts or at specific indices. Always verify resulting shapes to avoid subtle broadcasting bugs later.

```python
ss_arr_1 = np.random.randint(10, size=(2,2))
ss_arr_2 = np.random.randint(10, size=(2,2))

np.vstack((ss_arr_1, ss_arr_2))  # stack rows (→ 4×2)
np.hstack((ss_arr_1, ss_arr_2))  # stack cols (→ 2×4)
```

```python
# Column/row stack after deleting a row
ss_arr_3 = np.delete(ss_arr_1, 1, 0)  # drop row index 1
ss_arr_4 = np.delete(ss_arr_2, 1, 0)
np.column_stack((ss_arr_3, ss_arr_4))  # column‑wise combine
np.row_stack((ss_arr_3, ss_arr_4))     # row‑wise combine
```

```python
# Horizontal splits
ss_arr_5 = np.random.randint(10, size=(2,10))
np.hsplit(ss_arr_5, 5)        # 5 equal splits along columns
np.hsplit(ss_arr_5, (2,4))    # split at column indices 2 and 4
```

**What it does:** Concatenate arrays along rows/columns, or split columns into chunks.

---

## 5) Views vs copies (copying semantics)

Performance in NumPy comes from sharing memory, but that also brings side effects. Simple assignment binds a new name to the same data. `view()` usually creates a new array **header** that points to the same buffer, while `copy()` duplicates the buffer so edits are isolated. Knowing which you have prevents hard‑to‑find bugs where one change unexpectedly affects another variable.

```python
cp_arr_1 = np.random.randint(10, size=(2,2))
cp_arr_2 = cp_arr_1           # just another reference (no copy)
cp_arr_1[0,0] = 2             # mutates both names

cp_arr_3 = cp_arr_1.view()    # a view: shares data, new metadata
cp_arr_3.flatten('F')          # returns a new array (no in‑place change)

cp_arr_4 = cp_arr_1.copy()    # deep copy: independent data buffer
```

**What it does:** Assignment shares memory; `view()` often shares; `copy()` duplicates. `flatten()` returns a new array.

---

## 6) Element‑wise math, random sampling, and reductions

Universal functions (ufuncs) apply fast, element‑wise operations across arrays and support broadcasting across mismatched shapes. Reductions like `sum`, `max`, and `argmax` collapse dimensions along an `axis`, which is essential for column‑wise or row‑wise statistics. Random sampling produces synthetic data for testing; setting a seed makes results reproducible across runs.

```python
arr_3 = np.array([1,2,3,4])
arr_4 = np.array([2,4,6,8])

arr_3 + arr_4
arr_3 - arr_4
arr_3 * arr_4
arr_3 / arr_4
```

**What it does:** Vectorized element‑wise arithmetic.

```python
# NumPy.random convenience
np.random.rand(4)         # 4 floats in [0,1)
np.random.choice(arr_3)   # pick one element from arr_3
```

**What it does:** Samples from simple distributions.

```python
# Reductions (sum, etc.)
arr_3.sum()
# For 2D arrays, you can use axis=0/1 to reduce by columns/rows.
# e.g. arr_6.sum(axis=0), arr_6.cumsum(axis=1), arr_6.max(axis=0)
```

```python
# Equivalent ufuncs
np.add(arr_3, arr_4)
np.subtract(arr_3, arr_4)
np.multiply(arr_3, arr_4)
np.divide(arr_3, arr_4)
```

```python
# More ufuncs
arr_5 = np.array([[1,2],[3,4]])
arr_6 = np.array([[2,4],[6,9]])
np.remainder(arr_6, arr_5)
np.power(arr_6, arr_5)
np.sqrt(arr_3)
np.cbrt(arr_3)
np.absolute([-1,-2])
np.exp(arr_3)
np.log10(arr_3)

np.gcd.reduce([9,12,15])   # 3
np.lcm.reduce([9,12,15])   # 180

np.floor([1.2,2.5,3.7])
np.ceil([1.2,2.5,3.7])
```

**What it does:** Demonstrates universal functions (`ufuncs`) that act element‑wise and reductions like `reduce`.

```python
# Fancy indexing with another array of indices
sq_arr = np.arange(6)**2   # [0,1,4,9,16,25]
sq_arr[arr_3]              # selects positions 1,2,3,4
```

```python
# Column‑wise argmax and gathering
arr_7 = np.random.randint(10, size=(5,3))
mc_index = arr_7.argmax(axis=0)           # row index of max per column
# To gather the max element in each column:
max_nums = arr_7[mc_index, np.arange(arr_7.shape[1])]
max_nums
```

**What it does:** `argmax(axis=0)` finds the row index for each column’s max. Use advanced indexing to fetch the actual values per column.

---

## 7) Reading from files (CSV → NumPy)

NumPy can load text files directly, but pandas often provides a smoother path when you have headers or mixed types. The pattern is: load with pandas, then convert to a clean numeric array. When using pure NumPy, be mindful of missing values (`nan`) and dtypes. Establishing a tidy, numeric matrix early makes the rest of your analysis simpler and faster.

> This section expects a file named `icecreamsales.csv` (two columns like `temperature, sales`). If you don’t have it, create a tiny sample:

```python
import pandas as pd
pd.DataFrame({"temperature":[20,22,25,28,30], "sales":[120,135,160,190,210]}).to_csv("icecreamsales.csv", index=False)
```

```python
# Pandas path: easy → then convert to NumPy
import pandas as pd
from numpy import genfromtxt

sales = pd.read_csv('icecreamsales.csv').to_numpy()
sales
```

**What it does:** Loads CSV into a DataFrame, then `to_numpy()` gives a numeric array.

```python
# Pure NumPy path; handle NaNs per row
sales_2 = genfromtxt('icecreamsales.csv', delimiter=',')
sales_2 = [row[~np.isnan(row)] for row in sales_2]
sales_2
```

**What it does:** `genfromtxt` loads as floats and can produce `nan` for missing values; we strip NaNs from each row.

---

## 8) Statistics and a simple regression line

Descriptive statistics summarize your data quickly, while correlation and least‑squares regression help you measure and model relationships between variables. The manual regression here shows the algebra under the hood: center variables, compute slope, then back out the intercept. This foundation helps you trust later, more complex models because you understand the mechanics.

```python
sarr_1 = np.arange(1,6)
np.mean(sarr_1)
np.median(sarr_1)
np.average(sarr_1)
np.std(sarr_1)
np.var(sarr_1)
# Note: there are nan‑aware variants: nanmean, nanmedian, nanstd, nanvar
```

```python
# Inspect the sales data
print("sales\n", sales)

np.percentile(sales, 50, axis=0)  # column medians
sales[:,1]                         # second column (sales)

# Correlation between temperature and sales
np.corrcoef(sales[:,0], sales[:,1])
```

```python
# Manually compute least‑squares regression line: sales ≈ slope*temp + intercept
temp_mean  = np.mean(sales[:,0])
sales_mean = np.mean(sales[:,1])
numerator   = np.sum((sales[:,0]-temp_mean) * (sales[:,1]-sales_mean))
denominator = np.sum(np.square(sales[:,0]-temp_mean))
slope = numerator / denominator
intercept = sales_mean - slope * temp_mean
reg_arr = sales[:,0] * slope + intercept
reg_arr
```

**What it does:** Computes simple linear regression parameters and the predicted sales for each temperature.

---

## 9) Trigonometry and helpers

Trigonometric functions in NumPy expect radians. Use them for signal processing, geometry, and simulations. Helpers like `rad2deg` convert units, and `hypot` computes Euclidean norms safely. When plotting functions like `tan`, remember they have discontinuities; sampling more points or limiting the y‑axis can make plots easier to read.

```python
t_arr = np.linspace(-np.pi, np.pi, 200)
plt.plot(t_arr, np.cos(t_arr))
plt.show()

plt.plot(t_arr, np.tan(t_arr))
plt.show()

np.arctan(1)

# Utility trig helpers
np.rad2deg(np.pi)  # 180 degrees
np.hypot(10, 10)   # sqrt(10**2 + 10**2)
```

**What it does:** Plots cosine/tangent and uses inverse trig and helpers (`rad2deg`, `hypot`).

---

## 10) Matrix & tensor operations (Linear Algebra)

Matrix multiplication, tensor contractions, and Einstein summation underpin modern numerical computing. Pay close attention to shapes: `(m×n)·(n×p)` yields `(m×p)`. `einsum` provides compact, readable formulas for complex contractions and can be both faster and clearer than chaining transposes and dots. Inversion and determinants are numerically sensitive—prefer `solve` for systems and watch condition numbers to judge stability.

```python
# Re‑use earlier 2×2 arrays
arr_5 = np.array([[1,2],[3,4]])
arr_6 = np.array([[2,4],[6,9]])
arr_8 = np.array([[5,6],[7,8]])

np.dot(arr_5, arr_6)                 # matrix multiply
LA.multi_dot([arr_6, arr_5, arr_8])  # chained dot with optimal order

np.inner(arr_5, arr_6)               # inner products across last axis
```

```python
# Tensor dot: sum over last 2 axes of arr_9 and both axes of arr_10
arr_9  = np.array([[[1,2],[3,4]],
                   [[5,6],[7,8]]])       # shape (2,2,2)
arr_10 = np.array([[1,2],[3,4]])         # shape (2,2)
np.tensordot(arr_9, arr_10)              # default axes=2
```

```python
# Einstein summation (compact tensor algebra)
arr_11 = np.array([0,1])
arr_12 = np.array([[0,1,2,3],[4,5,6,7]])

np.einsum('i,ij->i', arr_11, arr_12)   # weighted row‑sum per row of arr_12
np.einsum('i->', arr_11)               # sum of a vector
np.einsum('ij,jk->', arr_5, arr_6)     # sum of all elements of arr_5@arr_6
np.einsum('i,i->', arr_3, arr_4)       # dot product of two vectors
```

```python
# Matrix power, Kronecker, eigen, norms, inverse, condition, determinant
LA.matrix_power(arr_5, 2)
np.kron(arr_5, arr_6)
LA.eig(arr_5)       # eigenvalues and right eigenvectors
LA.norm(arr_5)      # default is Frobenius norm for 2D
LA.inv(arr_5)       # inverse (if non‑singular)
LA.cond(arr_5)      # condition number

A = np.array([[1,2],[3,4]])
LA.det(A)           # determinant
A_i = LA.inv(A)
np.dot(A, A_i)      # ≈ identity (floating‑point error possible)
```

```python
# Solve linear systems Ax=b
arr_13 = np.array([[1,4],[6,18]])
arr_14 = np.array([10, 42])
LA.solve(arr_13, arr_14)

np.eye(2,2, dtype=int)   # 2×2 identity
```

**What it does:** Covers matrix multiply, multi‑dot optimization, tensor ops, eigendecomposition, norms, inverses, determinants, solving systems.

---

## 11) Saving and loading

Use `.npy` for fast, exact round‑trips of arrays (shape and dtype preserved). Text formats like CSV are human‑readable but may change precision and dtype. A common workflow is to save intermediate results as `.npy` for performance and export final tables to CSV for sharing.

```python
arr_15 = np.array([[1,2],[3,4]])
np.save('randarray', arr_15)          # saves to randarray.npy
arr_16 = np.load('randarray.npy')

np.savetxt('randcsv.csv', arr_15)     # text CSV (default float fmt)
arr_17 = np.loadtxt('randcsv.csv')
```

**What it does:** Demonstrates NumPy‑native binary (`.npy`) and text I/O.

---

## 12) Financial functions (numpy‑financial)

Time‑value‑of‑money calculations (future value, payment schedules) are compact with `numpy‑financial`. Be careful with signs: by convention, payments you make are negative and money you receive is positive. Always convert annual rates to per‑period rates when compounding monthly or weekly.

```python
import numpy_financial as npf

# Future value of monthly savings for 10 years at 8% APR
npf.fv(0.08/12, 10*12, -400, -400)

# Amortization breakdown example (interest vs principal)
period = np.arange(1, 1*12) + 1   # months 1..12
principal = 3000.00
ipmt = npf.ipmt(0.0925/12, period, 1*12, principal)  # interest portion
ppmt = npf.ppmt(0.0925/12, period, 1*12, principal)  # principal portion
for payment in period:
    idx = payment - 1
    principal = principal + ppmt[idx]
    print(f"{payment:2d}  principal_paid={ppmt[idx]:8.2f}  interest={ipmt[idx]:8.2f}  balance={principal:9.2f}")
```

**What it does:** Uses the `numpy‑financial` add‑on for time‑value‑of‑money calculations. (Install via `pip install numpy-financial`.)

> Common pitfalls fixed here: it’s `ipmt` not `impt`; and keep variable names consistent (`ppmt`).

---

## 13) Comparison functions

Element‑wise comparisons create boolean arrays that you can use for filtering, counting, or conditional assignment. They broadcast like other ufuncs, which makes it easy to compare an entire matrix to a scalar threshold or align two arrays of compatible shapes.

```python
carr_1 = np.array([2,3])
carr_2 = np.array([3,2])
np.greater(carr_1, carr_2)  # element‑wise comparison → boolean array
```

**What it does:** Returns `True/False` per position; pairs well with boolean masking.

---

## Extras & Notes

* `random.rand` / `random.choice`: In NumPy use `np.random.rand(...)` and `np.random.choice(...)`. The bare `random` module is Python’s standard library and behaves differently.
* `np.random.randint?` with a question mark only works in IPython/Jupyter.
* When mixing shapes, read the docstring for broadcasting rules.
* Many operations above mutate in place; if you need to preserve the original, work on a **copy**.

---
