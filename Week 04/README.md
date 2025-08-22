<div align="center">
    <img src="https://github.com/viethaa/intro-to-python/blob/main/assets/04" alt="02" width="300">
    <h1>Ranges and For Loops</h1>
</div>




`*` *Loops and Ranges allow for repetition*

<br>


# Python For-Loops & `range()`: A Practical README

## For-loop Fundamentals <a name="for-loop-fundamentals"></a>

Python’s `for` iterates **over items of an iterable** (lists, strings, files, generators…) rather than counting by default.

```python
for ch in "abc":
    print(ch)
# a
# b
# c
```

When you **need numbers**, you typically use `range()`:

```python
for i in range(5):  # 0, 1, 2, 3, 4
    print(i)
```

---

## What is `range()`? <a name="what-is-range"></a>

`range()` produces a **lazy, memory-efficient** sequence of integers.

**Signatures**

* `range(stop)` → `0, 1, ..., stop-1`
* `range(start, stop)` → `start, start+1, ..., stop-1`
* `range(start, stop, step)` → arithmetic progression (step can be negative)

```python
range(5)            # 0..4
range(2, 5)         # 2, 3, 4
range(10, 0, -2)    # 10, 8, 6, 4, 2
```

**Key properties**

* Not a list; it’s a `range` object. Convert with `list(range(...))` if you actually need a list.
* Efficient: does not pre-allocate all numbers.
* Membership is O(1): `7 in range(0, 100, 7)` is fast.
* `len(range(a, b, s))` works and is O(1).

**Off-by-one sanity**

* `stop` is **exclusive**. That’s why `range(n)` gives `0..n-1`.

---

## Core Patterns <a name="core-patterns"></a>

### Count up / down

```python
for i in range(10):
    ...  # 0..9

for i in range(10, 0, -1):
    ...  # 10, 9, 8, ..., 1
```

### Custom step

```python
for i in range(0, 10, 2):
    ...  # 0, 2, 4, 6, 8
```

### Index + value (use `enumerate`)

```python
nums = [10, 20, 30]
for idx, value in enumerate(nums):
    print(idx, value)
# 0 10
# 1 20
# 2 30
```

### Parallel iteration (use `zip`)

```python
names = ["Ada", "Linus", "Guido"]
scores = [98, 91, 95]
for name, score in zip(names, scores):
    print(name, score)
```

### Range over indices when needed

```python
letters = ["a", "b", "c"]
for i in range(len(letters)):
    print(i, letters[i])
# Prefer enumerate unless you truly need the index arithmetic.
```

### Chunking with steps

```python
data = list(range(13))
chunk_size = 4
for start in range(0, len(data), chunk_size):
    chunk = data[start:start+chunk_size]
    print(chunk)
# [0,1,2,3], [4,5,6,7], [8,9,10,11], [12]
```

### Reversed iteration

```python
for i in reversed(range(5)):
    print(i)  # 4,3,2,1,0
# or: for i in range(4, -1, -1): ...
```

---

## Loop Control: `break`, `continue`, `else` <a name="loop-control"></a>

```python
# Find first even number
for x in [3, 5, 6, 7]:
    if x % 2 == 0:
        print("first even:", x)
        break
else:
    print("no even found")  # runs only if loop didn’t break
```

* `break`: exit loop immediately.
* `continue`: skip to next iteration.
* `for ... else`: the `else` runs **only if the loop finishes normally** (no `break`).

---

## Looping Over Collections the Pythonic Way <a name="looping-over-collections"></a>

**Strings**

```python
for ch in "hello":
    ...
```

**Lists / Tuples**

```python
for item in [1, 2, 3]:
    ...
```

**Sets** (unordered)

```python
for x in {"red", "green", "blue"}:
    ...
```

**Dictionaries**

```python
person = {"name": "Ada", "age": 36}
for k in person:           # keys
    ...
for k, v in person.items():
    ...
for v in person.values():
    ...
```

**Files** (line-by-line)

```python
with open("notes.txt") as f:
    for line in f:
        print(line.rstrip())
```

---

## Comprehensions vs. For-loops <a name="comprehensions"></a>

**List comprehension** (make a list)

```python
squares = [n*n for n in range(6)]  # [0,1,4,9,16,25]
```

**Generator expression** (lazy)

```python
sq = (n*n for n in range(10))  # use in for-loops or sum(), etc.
```

**With condition**

```python
evens = [n for n in range(20) if n % 2 == 0]
```

Use comprehensions for **small, clear transformations**. Prefer plain `for` when logic is complex or involves multiple statements.

---

## Gotchas & Pitfalls <a name="gotchas"></a>

1. **Empty ranges**

   * `range(5, 5)` → empty
   * `range(5, 1)` with positive step → empty
2. **`step=0` is invalid** → `ValueError`
3. **Modifying a list while iterating it** can skip elements; iterate a copy or build a new list.

   ```python
   items = [1, 2, 3, 4]
   for x in items[:]:  # safe copy
       if x % 2 == 0:
           items.remove(x)
   ```
4. **Floats**: `range()` only handles integers. For floats, use `numpy.arange`, `numpy.linspace`, or compute indexes and map to floats.
5. **Off-by-one**: Remember that `stop` is exclusive. Double-check boundaries.
6. **Prefer `enumerate` over `range(len(...))`** unless you need index math.

---

## Performance Notes <a name="performance"></a>

* `range` is **constant-space** regardless of size.
* Membership check is arithmetic (fast): `10_000_000 in range(0, 1_000_000_000, 10)` is O(1).
* `reversed(range(...))` is also lazy and efficient.
* Avoid `list(range(...))` unless you truly need the list.

---

## Fun & Interesting Examples <a name="fun-examples"></a>

### 1) FizzBuzz (classic)

```python
for n in range(1, 101):
    out = ""
    if n % 3 == 0: out += "Fizz"
    if n % 5 == 0: out += "Buzz"
    print(out or n)
```

### 2) Multiplication Table (pretty)

```python
size = 10
for r in range(1, size+1):
    row = [str(r*c).rjust(4) for c in range(1, size+1)]
    print("".join(row))
```

### 3) Collatz Steps

```python
def collatz_steps(n):
    steps = 0
    while n != 1:
        n = (n//2) if (n % 2 == 0) else (3*n + 1)
        steps += 1
    return steps

for n in range(2, 21):
    print(n, collatz_steps(n))
```

### 4) ASCII Sine Wave

```python
import math
width = 60
for x in range(width):
    y = int((math.sin(2*math.pi * x/width) + 1) * 10)  # 0..20
    print(" " * y + "*")
```

### 5) Emoji Progress Bar

```python
import time
steps = 20
for i in range(steps + 1):
    bar = "█" * i + "-" * (steps - i)
    print(f"\r[{bar}] {i/steps:>5.0%}", end="")
    time.sleep(0.05)
print()  # newline
```

### 6) Prime Sieve (lite)

```python
n = 100
is_prime = [True] * (n+1)
is_prime[0] = is_prime[1] = False
for p in range(2, int(n**0.5) + 1):
    if is_prime[p]:
        for m in range(p*p, n+1, p):
            is_prime[m] = False
primes = [i for i, ok in enumerate(is_prime) if ok]
print(primes)
```

### 7) Sliding Window Max (indices + range)

```python
def window_max(nums, k):
    out = []
    for i in range(0, len(nums) - k + 1):
        out.append(max(nums[i:i+k]))
    return out

print(window_max([2,1,3,2,5,2,6], 3))  # [3,3,5,5,6]
```

### 8) Triangle (ASCII Art)

```python
h = 10
for r in range(1, h+1):
    print(" "*(h-r) + "/" + "^"*(2*r-2) + "\\")
```

---

## Mini Cheatsheet <a name="cheatsheet"></a>

```text
# Basics
for i in range(n):
for i in range(a, b):
for i in range(a, b, s):
for i in reversed(range(n)):

# Collections
for x in seq:
for i, x in enumerate(seq, start=0):
for a, b in zip(A, B):
for k, v in d.items():

# Control
break, continue
for ... else:

# Handy idioms
for i in range(0, len(seq), k):  # chunk indices
for i in range(len(seq)-1, -1, -1):  # reverse indices
```

---

## Try it! <a name="practice"></a>

1. **Sum of multiples**: Sum all numbers `< 1000` that are multiples of 3 or 5.

2. **Reverse words**: Given a sentence, print words in reverse order using indices and `range`.

3. **Diagonal difference**: For an `n×n` matrix (list of lists), compute the absolute difference between the sums of its diagonals using a single loop and `range(n)`.

4. **Caesar cipher (shift=3)**: Shift only alphabetic characters forward by 3 (wrap around); keep spaces/punctuation.

5. **Histogram**: Given a list of integers 0–9, print a vertical histogram using loops.

**Hints**

* Use `enumerate` to get indices.
* Remember `stop` is exclusive.
* For reverse order, try `reversed(range(n))` or `range(n-1, -1, -1)`.

---

### Appendix: `range` curiosities

* `range` equality compares **sequences of values**: `range(0) == range(2, 1)` → `True` (both empty).
* Slicing a `range` returns another `range`: `range(10)[::2]` → `range(0, 10, 2)`.
* `len(range(a, b, s))` is defined; it’s the count of steps in the arithmetic progression.

---

**That’s it!** If you want, we can extend this README with: nested loops patterns, `itertools` tricks (`product`, `permutations`), or benchmarking examples.


