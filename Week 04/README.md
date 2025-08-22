<div align="center">
  <img src="https://github.com/viethaa/intro-to-python/blob/main/assets/04" alt="Ranges and For Loops" width="300">
  <h1>Ranges and For Loops in Python</h1>
  <p><em>Loops and ranges allow for structured repetition in Python programs.</em></p>
</div>

---

# 📘 Python `for` Loops & `range()`: A Practical Guide

## 📍 1. For-loop Fundamentals

Python’s `for` loop iterates over the items of an iterable such as lists, strings, files, or generators.  
When you need numeric iteration, you typically use the `range()` function.

---

## 🔢 2. What is `range()`?

The `range()` function generates a memory-efficient, lazy sequence of integers.  

### Signatures:

- `range(stop)`
- `range(start, stop)`
- `range(start, stop, step)`

### Key Properties:

- Not a list — it produces a `range` object.
- Very efficient, no pre-allocation of values.
- Constant-time length and membership checks.
- The `stop` value is exclusive.

---

## 🧩 3. Core Patterns

Common ways to use `range()` in combination with `for` loops:

- Counting up or down
- Using custom steps
- Accessing both index and value (with `enumerate`)
- Iterating multiple sequences in parallel (with `zip`)
- Index-based iteration
- Chunking data with custom step sizes
- Reversing iteration

---

## ⛔ 4. Loop Control: `break`, `continue`, `else`

- `break`: Exits the loop immediately.
- `continue`: Skips the current iteration.
- `else`: Runs only if the loop completes normally (no `break`).

---

## 🧺 5. Looping Over Collections

You can use `for` loops with a variety of built-in Python collections:

- Strings
- Lists and Tuples
- Sets (unordered)
- Dictionaries (keys, values, or items)
- Files (line-by-line)

---

## 🧠 6. Comprehensions vs. For-Loops

Use list comprehensions or generator expressions for concise, simple transformations.  
Stick to standard `for` loops when logic is complex or spans multiple lines.

---

## ⚠️ 7. Gotchas & Pitfalls

- Empty ranges
- Invalid `step` values (e.g., `step=0`)
- Modifying collections during iteration
- `range()` does not support floating-point numbers
- Off-by-one errors
- Overuse of `range(len(...))` when `enumerate()` is better

---

## ⚡ 8. Performance Notes

- `range()` is memory-efficient regardless of size.
- Membership tests and length checks are fast (constant time).
- `reversed(range(...))` is also efficient.
- Avoid converting `range()` to a list unless absolutely necessary.

---

## 🎮 9. Fun & Interesting Examples

Includes classic and creative use cases such as:

- FizzBuzz
- Multiplication tables
- Collatz conjecture
- ASCII sine waves
- Progress bars
- Prime sieves
- Sliding window problems
- ASCII triangles

---

## 🧪 10. Try It Yourself!

1. Sum all numbers below 1000 that are multiples of 3 or 5.
2. Print words in reverse order from a sentence using index-based looping.
3. Calculate the diagonal difference of an `n×n` matrix using a single loop.
4. Create a Caesar cipher (shift alphabetic characters by 3).
5. Print a vertical histogram from a list of digits.

---

## 🧮 Cheatsheet

```text
# Basics
for i in range(n)
for i in range(a, b)
for i in range(a, b, s)
for i in reversed(range(n))

# Collections
for x in seq
for i, x in enumerate(seq)
for a, b in zip(A, B)
for k, v in d.items()

# Control
break, continue
for ... else

# Idioms
for i in range(0, len(seq), k)      # chunk
for i in range(len(seq)-1, -1, -1)  # reverse
