<div align="center">
    <img src="https://github.com/viethaa/intro-to-python/blob/72f9af9d96c6eb96629931d3e51eb3694cffedc9/assets/03" alt="02" width="300">
    <h1>Variables & If Else Statements</h1>
</div>

`*` *Variables and If Else statements are fundamental building blocks in Python Code*

- `Variables 🪣` store data, while `if-else statements ⚖️` help make decisions based on conditions.
- Understanding these concepts will allow you programs in Python.

<br>

## ```Variables 🪣```

`*` Variables are used to store data in Python. They act as containers for values that can be changed throughout the program.

- Variable names must start with a `letter` or an `underscore _`
- Variable names cannot start with a number
- Variable names are case-sensitive (`age` and `Age` are different)

<br>

Example:
```python
name = "Kanye"   # name is the variable, "Kanye" is the str value
age = "17"       # age is the variable, 17 is the int value
```

<br>

## ```If Else Statements 🪣```

`*` If-Else statements are used for decision-making in Python. They allow the program to execute different code blocks based on conditions.

### Syntax of If Else:
```python
if condition = True                  
    print("The condition is True")     

else:                             
    print("The condition is False")    
```

- If `condition` is **True**, print "The condition is True"
- Otherwise, print "The condition is False"

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

## ```Excercise 01: Can You Enter The Club? 🎉```

`*` Check if a person is old enough to enter a club (18+) &nbsp; 🔞

- In Visual Code Studio, create a new file. Name it `age_check.py`
- Ask for user input:
```python
age = int(input("Enter your age: ")) 
```
- Write an `If Else statement` to check if the age is bigger or older than 18
- If the user age is > 18, `print("Welcome!")`
- If the user age is < 18, `print("Sorry, you need to be 18 to enter")`

<br>
<br>

## ```Excercise 02: Odd or Even? 🏋️‍♂️```

`*` Check if the number is odd or even based on user input &nbsp; 📥

- In Visual Code Studio, create a new file. Name it `if_else.py`
- Ask for user input:
```python
num = int(input("Enter a number: "))  
```
- Write an If Else statement to check if the number is odd or even

`❗` &nbsp; **`Hint: Use the operator: Modulus / Remainder (%)`**
