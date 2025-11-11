# Programming Exercises – README

A set of small console-style exercises. Each section tells you what to **read** from input and what to **print**. Unless otherwise stated, indices are 1-based and comparisons are case-insensitive where noted.

**Conventions & Notes**

- “Read:” describes inputs in order.
- “Do:” describes the exact output behavior.
- Treat vowels as `a e i o u` unless otherwise specified. “Case-insensitive” means treat uppercase the same as lowercase.
- When asked to “print,” write each item on its own line unless the rule clearly implies otherwise.
- If a task mentions parity: even/odd are with respect to standard integer parity.
- If any priority order is specified, follow it exactly.

---

## 1) Three-Beat Greeting (skip the middle)

**Read:** `n`

**Do:** Print `Hello #k` for `k = 1..n`, except skip the middle index `floor((n+1)/2)`.

**Example (n = 5):**
```
Hello #1
Hello #2
Hello #4
Hello #5
```

---

## 2) Odd-Even Echo

**Read:** `n`

**Do:** For `k = 1..n` print `k` followed by:
- `*` if `k` is odd
- `**` if `k` is even **and** divisible by `4`
- nothing extra otherwise

**Example (n = 8):**
```
1*
2
3*
4**
5*
6
7*
8**
```

---

## 3) Selective Countdown

**Read:** `start, end` with `start < end`

**Do:** Print numbers from `end` down to `start`. Replace multiples of `3` with `BEEP`.

---

## 4) Step-and-Swap

**Read:** `reps, step`

**Do:** Print `Rep k` for `k = 1..reps` in steps of `step`. If `k` is even, print `Rep k (left)`; else `Rep k (right)`.

---

## 5) Divisor Bar with Prime Tag

**Read:** `n`

**Do:** For each `i = 1..n`, print `i: ` followed by a number of `*` equal to the **number of divisors of `i`**. Append `(prime)` if `i` is prime.

---

## 6) UGA/BUGA Pyramid with Switch

**Read:** `n`

**Do:** Print `n` rows. Row `r` has `r` tokens alternating `UGA/BUGA`. Odd rows start with `UGA`; even rows start with `BUGA`.

---

## 7) Checkerboard with Row Labels

**Read:** `rows, cols`

**Do:** Grid with `X` where `(i + j)` is even, `O` otherwise. After each row, append `| even` or `| odd` based on the **row index parity** (choose 0-based or 1-based; be consistent).

---

## 8) Wave Blocks with Symbol Choice

**Read:** `rows, cols, ch` (single character)

**Do:** For each row, print **two lines** (two “waves”):
- **Wave A:** `ch` on even columns, spaces on odd
- **Wave B:** spaces on even, `ch` on odd

Alternate row symbol: odd-numbered rows use `ch`; even-numbered rows use `*`.

---

## 9) Diagonal Cross

**Read:** `n` (odd)

**Do:** Print an `n × n` grid; `X` on both diagonals, `.` elsewhere; the exact center is `O`.

---

## 10) Times Table with Hiding Rules

**Read:** `n`

**Do:** `n × n` multiplication table where each cell is:
- `-` if product is **even**
- `#` if product is **divisible by 3**
- the product otherwise

**Priority:** check **even first**, then **divisible by 3**.

---

## 11) Running Max Arrows

**Read:** `n`, then `n` integers one by one

**Do:** After each number, print the running **maximum so far**. If the new number sets a new maximum, also print `↑` on that line.

---

## 12) Lead Changes

**Read:** `m`, then `m` pairs `A B` (scores after each round)

**Do:** After each pair, print leader: `A`, `B`, or `tie`. Whenever the leader switches compared to previous line, also print `lead change`.

---

## 13) Name Tag Filter

**Read:** `count`, then `count` first names

**Do:**
- If name starts with a **vowel** (`a e i o u`; case-insensitive): print `Welcome, <name>!`
- Else if `len(name)` is **even**: print `Hello, <name>.`
- Else: print an empty line

---

## 14) Character After Vowel (Safe Peek)

**Read:** string `s`

**Do:** Print characters that immediately **follow** a lowercase vowel (`a e i o u`). If the follower equals the vowel (like `aa`), print `!` instead.

---

## 15) Ph-ish Replacement with Lookahead

**Read:** string `s`

**Do:** Replace `f` with `ph` **only when** the next character exists and is a **vowel (case-insensitive)**. Keep other `f` as is. Print the result.

---

## 16) Custom X-Replace with No-Digits Rule

**Read:** string `s`, character `c`

**Do:** Replace every `x` with `c`, **except** when the next character is a **digit**; then keep `x`. Also print how many replacements were made.

---

## 17) Vowel-Triggered Star Mask

**Read:** non-empty string `s`

**Do:** Build a new string where each char is `*` if the **previous** char is a lowercase vowel; otherwise keep the char. Print the string **and** the count of `*`.

---

## 18) Centered Badge with Width Check

**Read:** `first name, last name, grad year, width`

**Do:** Print a **boxed badge** with `*` border of given `width`. If any content line would overflow `width`, print `ERROR: width too small`.

---

## 19) Menu Bill with Tiered VAT

**Read:** quantities for **three items** (you pick names and prices)

**Do:** Compute `subtotal`; VAT is **5%** if `subtotal < 50,000`; otherwise **8%**. Print subtotal, VAT, total with **thousands separators**. If any quantity is negative, print `INVALID` and stop.

---

## 20) Assembly Banner with Center & Crop

**Read:** `day, place, quote, width`

**Do:** Print centered title `Assembly - <day> @ <place>` within `=` border of length `width`. Then print `quote` within `-` border. If `quote` exceeds `width - 4`, crop and append `...`.

---

## 21) Exact Rows Seating

**Read:** `students, seats_per_row`

**Do:**
- If `seats_per_row == 0`: print a friendly error
- Else print: `full rows`, `students in last row`
- If last row **not** full, also print how many seats are empty; else print `last row full`

---

## 22) Username Rulebook

**Read:** `first, last, grade (int)`

**Do:** `username = first letter of first name + last name` (all lowercase). If `grade < 6` append `_junior`; if `grade > 12` append `_alumni`. Print a welcome line and the username.

---

## 23) House Duel with Mercy Rule

**Read:** two house names and their points

**Do:** Print who leads and by how many. If lead `≥ 50`, also print `MERCY RULE`; otherwise print `GAME ON`.

---

## 24) Lab Access Matrix

**Read:** `score (0–100), teacher (yes/no), pass (yes/no), detention (yes/no)`

**Do:** Print `Access granted` **only if**:
- `score ≥ 70`
- (`teacher == yes` **OR** `pass == yes`)
- `detention == no`

If denied, print exactly **one** reason in this priority:
1. `Access denied: safety quiz must be ≥ 70.`
2. `Access denied: teacher on duty or signed pass required.`
3. `Access denied: detention today.`

---

## 25) Trip Eligibility with Helper Path

**Read:** `grade (int), form (yes/no), fee (yes/no), council (yes/no)`

**Do:**
- Approve if `grade ≥ 9` **and** `form + fee` are `yes`
- Else if `grade < 9` **and** `council` is `yes` **and** `form + fee` are `yes` → print `Approved as helper`
- Else print `Not eligible: <reasons>` (e.g., `grade < 9 and not Student Council`, `permission form missing`, `fee not paid`)

---

## 26) Late Fee Ladder with Cap & Discount

**Read:** `days, eco (yes/no)`

**Do:** Fee = `2000/day` for days `1–3`; `3000/day` for days `4–10`; `5000/day` for days `11+`. **Cap** at `100,000`. Eco members get **20% off** unless the cap is reached. Print **fee before discount**, **discount**, **final fee**.

---

## 27) Shuttle Gatekeeper (Strict Order)

**Read:** `grade (int), valid_id (yes/no), full (yes/no), prefect (yes/no), reserved (yes/no), late (yes/no)`

**Do:** Deny in this exact order (print **one line only**):
1. `Denied: valid ID required.`
2. `Denied: grades 6–12 only.`
3. `Denied: late boarding requires reservation.`
4. `Denied: bus full (prefect or reservation required).`

Else: `Boarding approved.`

---

## 28) Parities Triangle

**Read:** `n`

**Do:** Print rows `r = 1..n`; each row contains numbers `k = 1..r`. Print `k` if `(r + k)` is even; print `.` otherwise.

**Example (n = 4):**
```
1
. .
1 . 3
. 2 . 4
```

---

## 29) Zigzag Columns

**Read:** `rows, cols`

**Do:** Print a grid of `.` with a zigzag of `X`:
- On odd-numbered rows, `X` at columns `1, 3, 5, ...`
- On even-numbered rows, `X` at columns `2, 4, 6, ...`
- All other cells `.`

---

## 30) Staircase Sum with Alerts

**Read:** `n`, then `n` integers

**Do:** After each input, print cumulative sum. If the current number is **negative**, also print `ALERT`. The **first time** the sum exceeds `100`, also print `CAP REACHED` on that line.

---

## 31) Digit-Fence

**Read:** string `s`

**Do:** For each character:
- If it’s a **digit** and the **previous character** is also a digit, print `_` **instead** of the digit
- Otherwise print the character

**Example:** `a12b034 → a1_b0_34`

---

## 32) Border & Checker Fill

**Read:** `rows, cols`

**Do:** Rectangle with `#` border. Inside, fill with a checker of `A/B` by `(i + j)` parity. If `rows` and `cols` are both **odd**, replace exact center with `@`.

---

## 33) Selective Powers

**Read:** `start, end`

**Do:** For `k` from `start` to `end`:
- If `k < 0`: print `|k|`
- If `k == 0`: print `0`
- If `k > 0` and **odd**: print `k^2`
- If `k > 0` and **even**: print `k^3`

---

## 34) Mod-Clock

**Read:** `n, mod`

**Do:** Print numbers `1..n`, but:
- If `k % mod == 0` → print `tick`
- If `k % mod == 1` → print `tock`
- Else print `k`

If `mod <= 1`: print `INVALID MOD`.

---

## 35) Row Sums with Threshold

**Read:** `rows, cols`, then `rows * cols` integers **row by row**

**Do:** After each row, print the **row sum**. If the row sum is greater than **previous row’s** sum, append `↑`; if less, `↓`; if equal, `=`. For the **first row**, print the sum with no arrow.

---

**End of set.**

**Tip:** In Google Docs, apply a monospace font to the “Example” blocks for neat alignment.
