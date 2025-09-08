<div align="center">
    <img src="https://github.com/viethaa/intro-to-python/blob/daadf2f6df685972f825ac92ce80dba537d56f88/assets/02" alt="02" width="300">
    <h1>Dictionaries</h1>
</div>

 `*` *A dictionary in Python is literally like a dictionary in your common sense*

 - Dictionaries are mainly used for **storing related data together**, like grouping a person's `age`, `name`, and `email` in **one variable**.

 - Organizes data in `key`, `value` pairs, making code easier to read and manage.

<br>

## ```📚 Dictionary Syntax```

* A dictionary is created using curly braces `{}` with keys and values.

### Example:

```python
student = {
    "name": "Khoi",
    "age": 16,
    "grade": "A-"
}
```

- `"name"`, `"age"`, and `"grade"` are keys  
- `"Khoi"`, `16`, and `"A-"` are their values

---

## ```Accessing Values 🔑```

* Use the key inside square brackets `[]` to get a value.

### Example:

```python
print(student["name"])
print(student["age"])
```

### Output:

```
Alice
16
```

---

## ```Adding or Updating Items ✏️```

* Assign a value to a key to add or update data.

### Example:

```python
student["age"] = 17   # update age
student["school"] = "High School"  # add new key
print(student)
```

### Output:

```
{'name': 'Alice', 'age': 17, 'grade': 'A', 'school': 'High School'}
```

---

## ```Removing Items ❌```

* Use `del` or `.pop()` to remove items.

### Example:

```python
del student["grade"]
school = student.pop("school")
print(student)
print("Removed:", school)
```

### Output:

```
{'name': 'Alice', 'age': 17}
Removed: High School
```

---

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
