<div align="center">
  <img src="https://github.com/viethaa/intro-to-python/blob/main/assets/04.png" alt="Loop Review & While Loops" width="300">
  <h1>Loop Review & While Loops</h1>
</div>

`*` *Today, we’ll review what we learned about For Loops, finish the exercises we didn’t complete, and introduce a new type of loop — the While Loop!*

---

## 🔁 Quick Review: For Loops

* `for` loops are used when you **know exactly how many times** you want to repeat something.
* You can loop through **ranges**, **strings**, and **lists**.
* Special keywords like `break`, `continue`, and `else` let you control the loop’s flow.

💡 *Example:*
```python
for i in range(5):
    if i == 3:
        continue
    print(i)
else:
    print("Loop finished!")
```

🕹️ *Output:*
```
0
1
2
4
Loop finished!
```

---

## 🧪 Exercise 1 — Finish the Challenge!

* Copy your “Filtered Sum” challenge from last week.
* Try to finish it **without peeking** 👀
* Once done, test your code and share your output.

```python
total = 0

for i in range(1, 101):
    # your code here
    pass
else:
    # your code here
    pass

print("Total =", total)
```

---

## ⏱️ New Topic: While Loops

`*` *While Loops repeat a block of code as long as a certain condition is TRUE.*

* Unlike `for` loops, you don’t need to know how many times it runs.
* The loop will keep running **until the condition becomes False**.

💡 *Example:*
```python
count = 1
while count <= 5:
    print("Count =", count)
    count += 1
```

🕹️ *Output:*
```
Count = 1
Count = 2
Count = 3
Count = 4
Count = 5
```

---

## ⚠️ Important: Avoid Infinite Loops!

* Always make sure something in your loop **changes the condition**.
* Otherwise, your loop will run forever!

💡 *Example (❌ infinite loop!):*
```python
x = 0
while x < 5:
    print(x)
    # forgot to increment x!
```

---

## 🧩 Comparison: For vs While

| Feature | For Loop | While Loop |
|----------|-----------|-------------|
| Use when | You know how many times to repeat | You don’t know how many times |
| Condition type | Based on sequence (`range`, `list`, etc.) | Based on logical condition |
| Common use | Counting, iterating items | Waiting for something to happen |

---

## 🧪 Exercise 2 — Guessing Game 🎯

* Write a program that keeps asking the user to guess a number until they get it right.

```python
secret = 7
guess = 0

while guess != secret:
    guess = int(input("Guess the number: "))

print("You got it!")
```

---

## 🧠 Challenge: Countdown Timer ⏰

* Use a `while` loop to count down from 5 to 0.
* Print “Liftoff” when finished!

Expected Output:
```
5
4
3
2
1
Liftoff
```
