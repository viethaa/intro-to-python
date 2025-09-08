<div align="center">
    <img src="https://github.com/viethaa/intro-to-python/blob/main/assets/05.png" alt="02" width="300">
    <h1>Dictionaries</h1>
</div>

 `*` *A dictionary in Python is literally like a dictionary in your common sense:*

 - Dictionaries are mainly used for **storing related data together**, like grouping a person's `age`, `name`, and `email` in **one variable**.

 - Organizes data in `key`, `value` pairs, making code easier to read and manage.

<br>

## ```📚 Dictionary Syntax```

`*` Like a normal dictionary which pairs a `word`, and a `meaning`, a dictionary in Python pairs a `key`, and a `value`.
- Start by creating a **single variable** to store the dictionary's contents
- The dictionary syntax is written by using curly braces `{}`.

<br>

Example:
```python3
student = {
    'name': 'Khoi',
    'age': 16,
    'grade': 'Junior'
}
```

- `🔑 keys:` name, age, grade
- `🗂️ values:` Khoi, 16, Junior

<br>


## ```🗂️ Accessing Values```

`*` To access a `value` in a dictionary, call the `variable_name` and input the `key` pair in square brackets.
- This way, you don't have the **manually** go through the dictionary to find the `value`.
- In programming, always **prioritize efficiency**.

<br>

💡 `Example:`
```python
goat = {
    "name": "Ronaldo",
    "age": 40
    "club": "Al Nassr FC"
    "goals" "941"
}

print(goat["name"])
print(goat["club"])
print(f'{goat["name"]} is already {goat["age"]} years old, but he has scored {goat["goals"]} goals.')


# Output:
- Ronaldo
- Al Nassr FC
- Ronaldo is already 40 years old, but he has scored 941 goals.
```

<br>

## ```✏️ Adding & Updating Items```

`*` You can add a new key to a dictionary by **simply assigning a value**
- If the `key` **already exists**, assigning a new `value` will update it
- If a `key` **does not yet exist**, assigning a new `value` and will add a new `key-value pair`

<br>

💡 `Example:`
```python
goat = {
    "name": "Ronaldo",
    "age": 40,
    "club": "Al Nassr FC",
    "goals": 941
}

# Add
goat["nationality"] = "Portuguese"

# Update
goat["age"] = 41

```

<br>

📖 `Updated Dictionary:`
```python
goat = {
    "name": "Ronaldo",
    "age": 41,
    "club": "Al Nassr FC",
    "goals": 941,
    "nationality": "Portugese"
}
```

<br>

## ```❌ Removing Items```

`*` Removing items from a dictionary means deleting a `key-value` pair so that it **no longer exists** in the dictionary
- Use `del` or `.pop()` or `clear()` to **remove items**.

#

<br>

`pop()`
- Removes a specific key and returns its value.

<br>

```python
student = {"name": "Alicu", "age": 17, "grade": "A"}
removed = student.pop("age")  

print(student)   # {'name': 'Alicu', 'grade': 'A'}
print(removed)   # 17
```
#

## ```Looping Through a Dictionary 🔄```

* You can loop through keys, values, or both.

### Example:

```python
for key, value in student.items():
    print(key, ":", value)
```

### Output:

```
name : Alice
age : 17
```

---

## ```Exercise 01: Phonebook 📱```

* Create a dictionary where names are keys and phone numbers are values.  
* Write a function to look up a phone number by name.

---

## ```Exercise 02: Word Counter 📝```

* Write a program that counts how many times each word appears in a sentence using a dictionary.
