<div align="center">
    <img src="https://github.com/viethaa/intro-to-python/blob/daadf2f6df685972f825ac92ce80dba537d56f88/assets/01" alt="02" width="300">
    <h1>Data Types & Symbols</h1>
</div>

 `*` *Understanding data types and symbols is essential for writing effective Python code.*

 - `Data types 📦` like integers, strings, and lists are used to store and manipulate data efficiently.

 - `Symbols and Operators ➕` such as `+`, `==`, and `%` are used for performing arithmetic, comparison, and logical operations.

<br>

## ```📦 Data Types```

`*` **Boolean** (bool)
- Represents one of two values: `True` or `False`
- Example:
```python
is_active = True
is_active = False
```
<br>

`*` **String** (str)
- Represents a sequence of characters enclosed in single `(')`, double `(")` quotes
- Example:
```python
name = "Lan Dinh"
food = 'caesar wrap'
```

<br>

`*` **Integer** (int)
- Represents whole numbers (`pos`, `neg`, or `zero`)
- Example:
```python
age = 16
score = -200
```

<br>

`*` **Float** (float)
- Represents `decimal` or `floating-point` numbers
- Example:
```python
pi = 3.14
temperature = -5.8
```

<br>

`*` **List** (list)
- Represents `ordered` and `mutable` (can change) collection of elements
- Example:
```python
fruits = ["Apple", "Banana", "Strawberry"]
numbers = [1, 2, 3, 4, 5]
```

<br> 

`*` **Tuple** (tuple)
- Represents `ordered` and `immutable` (cannot change) collection of elements
- Example:
```python
coordinates = [10.0, 20.0]
```

<br>

`*` **Dictionary** (dict)
- Represents a key-value pair collection
- Example:
```python
person = {
  "name": "Bob",
  "age": 16,
  "is_cool": True
}
```

<br>

## ```➕ Symbols and Operators```

| Arithmetic Operators | Function               |  
|:----------------------:|:-----------------------:|  
| `+`                 | Addition              |  
| `-`                 | Subtraction           |  
| `*`                 | Multiplication        |  
| `/`                 | Division              |  
| `//`                | Floor Division        |  
| `%`                 | Modulus / Remainder   | 
| `**`                 | Exponent   | 

<br>

| Comparison Operators | Function               |  
|:----------------------:|:-----------------------:|  
| `==`                 | Equal to              |  
| `!=`                 | Not equal to          |  
| `>`                 | Greater than        |  
| `<`                 | Less than              |  
| `>=`                | Greater or equal to        |  
| `<=`                 | Less or equal to   | 

<br>

## ```🏋️‍♂️ Exercise```

Let’s build up your Python skills step by step.

### ✅ Stage 1: Simple Variables  
Start with individual pieces of information.

1. **Create a new Python file**  
   - In VS Code, make a new file and name it **`my_info.py`**.

2. **Create some variables**  
   - Add a few lines like this (but use *your* own details!):
<details>
<summary><h3>💡 Click to reveal a sample answer (try it yourself first!)<h3></summary>

```python
name = "Your Name"     # a string
age = 16               # an integer (whole number)
height = 5.6           # a float (decimal number)
likes_python = True    # a boolean (True or False)

print(name)
print(age)
print(height)
print(likes_python)
```
</details>

3. **Change a value**  
   - Try changing `age` to a different number.  
   - Save and run the file again to see the new output.

---

### ✅ Stage 2: Combine Everything into a Dictionary  
Now let’s keep all the information in **one place**.

1. **Add this to the bottom of your file**:
<details>
<summary><h3>💡 Click to reveal a sample answer (try it yourself first!)<h3></summary>

```python
my_info = {
    "name": name,
    "age": age,
    "height": height,
    "likes_python": likes_python
}

print(my_info)
```
</details>

💡 **Tip:**  
- Strings (words) go inside quotes `" "`.  
- Numbers don’t need quotes.  
- Booleans are either `True` or `False` (with capital letters).

2. **Mini Challenge**  
   - Add a new piece of information (for example `"favorite_color": "blue"`).  
   - Print only one value, like this:
```python
print(my_info["name"])
```

---

You’re now ready to run it in the terminal and see the results!

<br>

## ```▶️ Run Python Code```

1. **Open VS Code**  
   - Start Visual Studio Code on your computer.

<br>

2. **Open the Terminal**  
   - Press **`Ctrl/Command` + `J`** (the little backtick key, usually under the Esc key).  
   - A panel will open at the bottom of VS Code — this is the terminal.

<br>

3. **Run Your Python File**  
   - In the terminal, type:

```python
python3 your_file_name.py
```

<br>

4. **Check your results**  
   - Compare and check results if they are correct!

---