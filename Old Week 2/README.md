<div align="center">
    <img src="https://github.com/viethaa/intro-to-python/blob/daadf2f6df685972f825ac92ce80dba537d56f88/assets/02" alt="02" width="300">
    <h1>Data Types & Symbols</h1>
</div>

 `*` *Understanding data types and symbols is essential for writing effective Python code.*

 - `Data types 📦` like integers, strings, and lists are used to store and manipulate data efficiently.

 - `Symbols and Operators ➕` such as `+`, `==`, and `%` are used for performing arithmetic, comparison, and logical operations.

<br>

## ```Data Types: 📦```

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

## ```Symbols and Operators: ➕```

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

## ```Excercise: 🏋️‍♂️```

`*` In Visual Code Studio, create a new file. Name it `operators.py`

- Write a dictionary that includes the following data types in it: `str`, `int`, `float`, `bool`
- Example *(DO NOT COPY)*:
```python
student = {
  "name": "Lan Dinh",   #str
  "age": 16,            #int
  "height": 5.6,        #float
  "loves_food": True    #bool
}
```

```python
print(student)
```

---

<br>

## ```Run Python Code: ▶️```

1. **Open VS Code**  
   - Start Visual Studio Code on your computer.

<br>

2. **Open the Terminal**  
   - Press **`Ctrl` + `~`** (the little backtick key, usually under the Esc key).  
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
