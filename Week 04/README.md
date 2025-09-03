<div align="center">
  <img src="https://github.com/viethaa/intro-to-python/blob/main/assets/04" alt="Ranges and For Loops" width="300">
  <h1>Ranges and For Loops in Python</h1>
</div>

`*` *For Loops allow you to repeat a block of code multiple times*

- `For Loops 🔄` helps repeat a sequence, like a `list`, `string`, or `range of numbers`
- They automate repetitive tasks and make your code shorter and more efficient

<br>

## ```Looping through Numbers #️⃣```

`*` You can use `range()` when you want to repeat something a certain number of time
- There are three ways you can use range to loops through numbers
- Choose the correct one for the most appropriate situations

<br>

##
🌟 `range(n)` : *starts at 0, and goes up to n-1*

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

🌟 `range(start, stop)` : *Loops from start to stop -1*

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

🌟 `range(start, stop, step)` : *Loops from start to stop -1, step is the amount of increment*

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

<br>

## ```Looping through Strings 🧶```

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

##

<br>

## ```Looping through Lists 📋```

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

##



