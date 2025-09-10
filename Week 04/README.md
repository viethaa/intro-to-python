<div align="center">
  <img src="https://github.com/viethaa/intro-to-python/blob/main/assets/04" alt="Ranges and For Loops" width="300">
  <h1>Ranges and For Loops</h1>
</div>

`*` *For Loops allow you to repeat a block of code multiple times*

* `For Loops 🔄` helps repeat a sequence, like a `list`, `string`, or `range of numbers`
* They **automate repetitive tasks** and make your code shorter and more efficient

<br>

##

## `#️⃣ Looping through Numbers`

`*` You can use `range()` when you want to **repeat something a certain number of time**

* There are **three** ways you can use range to loops through numbers
* Choose the correct one for the most appropriate situations

<br>

##

🌟 `range(n)` : **starts at 0, and goes up to n-1**

```python3
for i in range(5):
  print(i)
```

<br>

🕹️ `Output:`

```python3
# 0
# 1
# 2
# 3
# 4
```

<br>

##

🌟 `range(start, stop)` : **Loops from start to stop -1**

```python3
for i in range(3, 7):
  print(i)
```

<br>

🕹️ `Output:`

```python3
# 3
# 4
# 5
# 6
```

<br>

##

🌟 `range(start, stop, step)` : **Loops from start to stop -1, step is the amount of increment**

```python3
for i in range(2, 10, 2):
  print(i)
```

<br>

🕹️ `Output:`

```python3
# 2
# 4
# 6
# 8
```

<br>

##

## `🧶 Looping through Strings`

`*` You can loop through each character in a string one by one

```python3
for letter in "LanDinh":
  print(letter)
```

<br>

`Output:`

```python3
# L
# a
# n
# D
# i
# n
# h
```

<br>

##

## `📋 Looping through Lists`

`*` You can loop through items stored in a list

```python3
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
  print(fruit)
```

<br>

`Output:`

```python3
# apple
# banana
# cherry
```

<br>

##

## `⏸️ Loop Control`

`*` Python gives you special keywords to control the flow of a loop beyond the normal sequence

* `Break 🔴`
* `Continue 🔁`
* `Else ✅`

<br>

##

🔴 `Break` : **Stops the Loop Early**

* Ends the loop immediately, even if it hasn't finished all iterations.

```python3
for i in range(10):
  if i == 5:
    break
  print(i)
```

<br>

🕹️ `Output:`

```python3
# 0
# 1
# 2
# 3
# 4
```

<br>

##

🔁 `Continue` : **Skip to Next Iteration**

* Skips the current loop run and jumps to the next one

```python3
for i in range(5):
  if i == 2:
    continue
  print(i)
```

<br>

🕹️ `Output:`

```python3
# 0
# 1
# 3
# 4
```

<br>

##

✅ `Else` : **Run Code After a Loop Finishes**

* **Executes once after the loop ends if the loop was not broken by the break**

```python3
for i in range(3):
  print(i)
else:
  print("Loop finished without break")
```

<br>

🕹️ `Output:`

```python3
# 0
# 1
# 2
# Loop finished without break
```

<br>

---

## Examples

```python3
# Example 1 — Repeat something n times
for _ in range(3):
    print("Hello, loop!")
```

```python3
# Example 2 — Count down with a negative step
for i in range(5, 0, -1):
    print(i)
print("Liftoff!")
```

```python3
# Example 3 — Even numbers using start/stop/step
# (stop is exclusive, so use 11 to include 10)
for i in range(2, 11, 2):
    print(i)
```

```python3
# Example 4 — Loop through a string and count vowels
text = "LanDinh"
vowels = 0
for ch in text:
    if ch.lower() in "aeiou":
        vowels += 1
print("Vowel count:", vowels)
```

```python3
# Example 5 — Using break/else to search
colors = ["red", "green", "blue"]
target = "green"

for c in colors:
    if c == target:
        print("Found:", c)
        break
else:
    # runs only if the loop wasn't broken
    print("Not found")
```

```python3
# Example 6 — Using continue to skip certain items
for i in range(1, 6):
    if i == 3:
        continue  # skip printing 3
    print(i)
```

---

## 🧪 Challenge Exercise

Build a filtered sum with loop control:

* Iterate from **1** to **100**.
* **Skip** numbers divisible by **both 3 and 5** using `continue`.
* **Add** numbers divisible by **3 or 5** (but **not both**) to a running `total`.
* If `total` **exceeds 400**, use `break` and print `"Stopped early at {i}"`.
* If the loop finishes without breaking, use the loop's `else` to print `"Clean finish"`.
* After the loop, print the final sum as `Total = X`.

**Expected output (deterministic with these rules):**

```
Stopped early at 42
Total = 405
```

**Starter code:**

```python3
total = 0

for i in range(1, 101):
    # your code here
    pass
else:
    # your code here
    pass

print("Total =", total)
```

**One possible solution (peek only after trying!):**

```python3
total = 0

for i in range(1, 101):
    if i % 3 == 0 and i % 5 == 0:
        continue
    if (i % 3 == 0) ^ (i % 5 == 0):  # xor: divisible by 3 or 5, but not both
        total += i
    if total > 400:
        print(f"Stopped early at {i}")
        break
else:
    print("Clean finish")

print("Total =", total)
```

---

### Tiny fixes to keep student output consistent

* In a `break` example like `if i == 5: break` inside `range(10)`, the printed numbers should be `0, 1, 2, 3, 4`.
* In a `continue` example like `if i == 2: continue` inside `range(5)`, the printed numbers should be `0, 1, 3, 4`.
* The `else:` block should be indented to align with the `for` block’s body.
