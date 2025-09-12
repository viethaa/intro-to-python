<div align="center">
    <img src="https://github.com/viethaa/intro-to-python/blob/72f9af9d96c6eb96629931d3e51eb3694cffedc9/assets/02" alt="02" width="300">
    <h1>Variables & Conditionals</h1>
</div>

`*` *Variables and If Else statements are fundamental building blocks in Python Code*

* `Variables 🪣` store data, while `if-else statements ⚖️` help make decisions based on conditions.
* Understanding these concepts will allow you program in Python.

<br>

## `Variables 🪣`

`*` Variables are used to store data in Python. They act as containers for values that can be changed throughout the program.

* Variable names must start with a `letter` or an `underscore _`
* Variable names cannot start with a number
* Variable names are case-sensitive (`age` and `Age` are different)

<br>

Example:

```python
name = "Kanye"  
age = "17"   
```

* `name` is the variable, "Kanye" is the str value
* `age` is the variable, 17 is the int value

<br>

### Examples

**Basics: strings vs. integers, and `type()`**

```python
name = "Kanye"      # string (text)
age = 17            # integer (number)

print(name)
print(age)
print(type(name))   # -> <class 'str'>
print(type(age))    # -> <class 'int'>
```

**Reassignment and dynamic typing**

```python
x = 10
print("x is:", x)   # -> x is: 10

x = x + 5
print("x is now:", x)  # -> x is now: 15

x = "now I'm text"
print("x became:", x)  # -> x became: now I'm text
print(type(x))         # -> <class 'str'>
```

**Multiple assignment & swapping**

```python
a, b = 1, 2
print("before:", a, b)   # -> before: 1 2
a, b = b, a
print("after: ", a, b)   # -> after:  2 1
```

<br>

### Working with Parts of Data

You can use **indexes** and **slicing** to work with parts of a string (or later, a list).

```python
text = "Python"
print(text[0])     # -> 'P' (first character, index starts at 0)
print(text[-1])    # -> 'n' (last character)
print(text[1:4])   # -> 'yth' (characters from index 1 up to but not including 4)
print(text[:3])    # -> 'Pyt' (from start to index 3)
print(text[3:])    # -> 'hon' (from index 3 to the end)
```

You can also find the length of a string or list:
```python
len(text)          # -> 6
```

These same ideas of indexing and slicing also work with **lists**, which are containers that hold multiple values.

<br>

## `Lists 📝` (Intro)

`*` Lists are used to store multiple items in a single variable. They are ordered and changeable.

Example:

```python
fruits = ["apple", "banana", "cherry"]
print(fruits[0])       # -> apple
print(fruits[1:3])     # -> ['banana', 'cherry']
print(len(fruits))     # -> 3
```

<br>

## `If Else Statements 🪣`

`*` If-Else statements are used for decision-making in Python. They allow the program to execute different code blocks based on conditions.

### Syntax of If Else:

```python
if condition = True                  
    print("The condition is True")     

else:                             
    print("The condition is False")    
```

* If `condition` is **True**, print "The condition is True"
* Otherwise, print "The condition is False"

<br>

### Syntax of Elif:

`*` Sometimes, multiple conditions needs to be checked. This is where `elif` comes in.

```python
score = 85

if score >= 90:
    print("Grade: A")

elif score >= 80:
    print("Grade: B")

elif score >= 70:
    print("Grade: C")

else:
    print("Grade: F")   
```

<br>

> **Note:** In Python, `=` assigns a value to a variable, while `==` compares two values for equality. Each `if`, `elif`, and `else` line ends with a colon `:` and the following block is indented.

### Examples

**Simple if/else**

```python
is_raining = True

if is_raining:
    print("Bring an umbrella!")
else:
    print("Sky's clear. Sunglasses time.")
```

**Using comparisons**

```python
age = 18

if age >= 18:
    print("Adult ticket")
else:
    print("Youth ticket")
```

**Elif chain with ranges**

```python
temp_c = int(input("Enter the temperature: "))

if temp_c >= 35:
    print("Heat warning!")
elif temp_c >= 25:
    print("Warm")
elif temp_c >= 15:
    print("Mild")
else:
    print("Chilly")
```

**Truthy / Falsy values**

```python
# Empty values are "falsy"; non-empty are "truthy".
name = ""
if name:
    print("We have a name.")
else:
    print("Name is missing.")   # -> Name is missing.

items = [1, 2, 3]
if items:
    print("The list has stuff.") # -> The list has stuff.
```

**Combining conditions with `and` / `or`**

```python
has_id = True
age = 20

if has_id and age >= 18:
    print("You may enter.")
elif not has_id and age >= 18:
    print("Come back with an ID.")
else:
    print("Too young.")
```

**One-line (ternary) conditional**

```python
score = int(input())
result = "pass" if score >= 60 else "fail"
print(result)  
```

<br>

## `Excercise 01: What grade did you get? 🎉`

`*` Check the powerschool grade that the user got

* In Visual Code Studio, create a new file.
* Ask for user input:

```python
grade = int(input("Enter your grade (%): "))  # use 'grade' for clarity
```

* Write an `If Else statement` to check if the grade falls between these values:

| Number Grade | Letter Grade               |  
|:----------------------:|:-----------------------:|  
| 92-100                | A   |  
| 85-91                 | A-  |  
| 75-84                 | B+  |  
| 65-74                 | B   |  
| 55-64                 | B-  |  
| 45-54                 | C+  | 
| 35-44                 | C   | 
| 25-34                 | C-  | 
| 15-24                 | D+  |
| 5-14                  | D   |
| 0                     | F   | 

> 💡 **Tip:** Test numbers in between 2 grades (like 91, 92, 84, 85) to make sure your comparisons (`>=`, `<`) work correctly.

<br>
<h3>For the sake of time you only need to do A, A-, B+, and B<h3>

**`->`** If the number grade is > 91:

```python
print("Congratulations! You got an A")
```

**`->`** If the number grade is < 85 and >= 75:

```python
print("Well done! You got a B+")
```

<br>

> ⭐ **Bonus Challenge:**  
> - Add checks to make sure the grade is between 0 and 100.  
> - Print a friendly error message if someone enters a number outside this range.

<details>
<summary><h4>💡 Click to reveal a sample solution</h4></summary>

```python
grade = int(input("Enter your grade (%): "))

if grade > 91:
    print("Congratulations! You got an A")
elif grade >= 85:
    print("Great job! You got an A-")
elif grade >= 75:
    print("Nice work! You got a B+")
elif grade >= 65:
    print("You got a B")
else:
    print("Keep trying! Below B range.")
```
</details>

<br>
<br>

## `Excercise 02: Odd or Even? 🏋️‍♂️`

`*` Check if the number is odd or even based on user input   📥

* In Visual Code Studio, create a new file. Name it `if_else.py`
* Ask for user input:

```python
num = int(input("Enter a number: "))  
```

* Write an If Else statement to check if the number is odd or even

`❗`   **`Hint: Use the operator: Modulus / Remainder (%)`**

<details>
<summary><h4>💡 Click to reveal a sample solution</h4></summary>

```python
num = int(input("Enter a number: "))

if num % 2 == 0:
    print("The number is Even")
else:
    print("The number is Odd")
```
</details>
