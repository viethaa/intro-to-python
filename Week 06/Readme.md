<div align="center">
    <img src="https://github.com/viethaa/intro-to-python/blob/e8aaac496c74797dae9a9b5d2938893c9c90729b/assets/06" alt="Python Logo" width="300">
    <h1>Functions</h1>
</div>

`*` *Functions let us organize code into reusable blocks that make programs easier to read and maintain.*

- `Functions` group code into blocks that perform specific tasks.  
- They can be reused to avoid repetition and make code cleaner.  
<br>

## ```Defining a Function ⚙️```

`*` A function in Python is defined using the `def` keyword, followed by the function name and parentheses.

Example:
```python
def greet():
    print("Hello, world!")
```

- `def` tells Python you are creating a function
- `greet` is the function name
- The indented block of code runs when the function is called

<br>

## ```Calling a Function 📞```

`*` To use a function, write its name followed by parentheses.

Example:
```python
greet()  
```

Output:
```
Hello, world!
```

<br>

## ```Parameters and Arguments 📦```

`*` Functions can take inputs called *parameters*.

Example:
```python
def greet(name):
    print("Hello, " + name + "!")

greet("Kanye")
```

Output:
```
Hello, Kanye!
```

- `name` is the parameter
- `"Kanye"` is the argument passed into the function

<br>

## ```Return Values 🎁```

`*` A function can send back a value using `return`.

Example:
```python
def add(a, b):
    return a + b

result = add(3, 5)
print(result)
```

Output:
```
8
```

<br>

## ```Exercise 01: Your Own Greeter 🙌```

`*` Write a function that asks for your name and prints a personalized greeting.

<br>

## ```Exercise 02: Simple Calculator ➕➖```  

`*` Write a function that takes two numbers and returns their sum, difference, product, and quotient.
