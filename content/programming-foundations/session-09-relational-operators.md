# Session 9 — Relational Operators

**Duration** 60 min · **Topic** Operators · **Prerequisite** Session 8
**Session type** Concept lecture · ⚠️ **No video and no slide deck exist for this session** — see Instructor Notes.

**Platform units**

| Resource | Unit ID |
|---|---|
| RM — Relational Operators | `e03da18b-8523-445e-81e9-8519b1c16a61` |
| Classroom Quiz A (52 q) | `6b210db5-685c-4856-8b2e-e9c2fc365bb8` |
| Classroom Quiz B (38 q) | `a045af4b-1c97-45ca-9693-aeadc5f10028` |
| MCQ Practice (40 q) | `176ab7ce-6e44-4ff5-9ac9-4bff2bb71f4d` |
| Coding Practice (10 q) | `9935f186-744c-4b1d-b775-b45056daa899` |

> ⚠️ **You have no deck.** The two "Slide Block" sections below are **Teaching Blocks** instead — board work and live typing, built from the reading material. Everything you need is written out; you supply the whiteboard.

---

## Learning Objectives

By the end of this session, students will be able to:

1. Name the six relational operators and what each compares. *(REMEMBERING)*
2. Explain that a comparison produces `True` or `False`, not a number. *(UNDERSTANDING)*
3. Distinguish `=` from `==` and state what each does. *(UNDERSTANDING)*
4. Predict the result of comparisons between integers, floats and strings. *(APPLYING)*
5. Explain why `10 == "10"` is `False`. *(ANALYZING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 8**. Newly authored. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `int(9.99)` give?
`A` `10` · `B` `9` · `C` `9.99` · `D` ValueError
→ **B.** *Targets:* `int()` chops, it doesn't round.

**Q2.** What does `int("nine")` give?
`A` `9` · `B` `0` · `C` ValueError · `D` TypeError
→ **C.** *Targets:* Invalid conversion raises ValueError.

**Q3.** `s = "Python"`. What is `s[0:3]`?
`A` `Pyth` · `B` `Pyt` · `C` `yth` · `D` `Pytho`
→ **B.** *Targets:* End index excluded. *Misconception:* A is the classic off-by-one.

**Q4.** Which converts a number to text?
`A` `int()` · `B` `float()` · `C` `str()` · `D` `type()`
→ **C.** *Targets:* Conversion function names.

**Q5.** `a = int(input())` and the user types `5`. What is `a`?
`A` The string `"5"` · `B` The number `5` · `C` `5.0` · `D` Error
→ **B.** *Targets:* The `int(input())` pattern.

**Q6.** Which raise an error? *(MSQ — select all)*
`A` `int("7")` · `B` `int("7.0")` · `C` `int(7.0)` · `D` `int("seven")`
→ **B and D.** *Targets:* The `"7.0"` trap. *Misconception:* missing B means Session 8's hardest idea didn't land.

**Q7.** What is `type("10")`?
`A` int · `B` str · `C` float · `D` bool
→ **B.** *Targets:* Quotes decide type. **Today's gateway** — `10 == "10"` depends entirely on this. Note the number.

---

## Hook (7–10 min)

Write on the board, nothing else:

```
5 > 3
```

> *"Is that true or false?"*

Everyone says true. Then:

> *"Right. Now here's the thing — Python agrees with you, and it will say so out loud."*

Type and run:

```python
print(5 > 3)
```

Output: `True`

> *"Every program that ever made a decision — a login that checks your password, a game that knows you lost, an app that says 'you're too young for this' — every one of them is built on this. A question that comes back True or False. Today you learn to ask them. Next session you learn to combine them. After that, your programs start making choices."*

---

## Teaching Block A (10–22 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from RM `e03da18b-8523-445e-81e9-8519b1c16a61` -->

**Write this table on the board and leave it up all session:**

| Operator | Meaning |
|---|---|
| `>` | is greater than |
| `<` | is less than |
| `==` | is equal to |
| `<=` | is less than or equal to |
| `>=` | is greater than or equal to |
| `!=` | is not equal to |

**Then type and run each of these, one at a time:**

```python
print(5 < 10)     # True
print(2 > 1)      # True
print(2 <= 3)     # True
print(2.53 >= 2.55)   # False
print(5 != 5)     # False
```

**Beats to emphasise**

- **The result is always `True` or `False`.** Never a number. Point at the capital letters — these are the Booleans from Session 4, finally being useful.
- **`==` is two characters, and it is not `=`.** Write both on the board side by side with labels: `=` puts a value in a box, `==` asks a question. This is the single most expensive confusion in the session.
- **`!=` reads as "not equal".** The `!` means "not" — that carries into next session's `not` operator.

**Checkpoint (at 22 min)** — cold-call two students:
> *"What does `x = 5` do, and what does `x == 5` do?"*
> **Answer:** The first puts 5 into `x`. The second asks whether `x` holds 5, and answers `True` or `False`.

---

## ⚡ Activity 1 — Rapid Fire Board Race (22–27 min)

### What this activity is

Two students at the whiteboard. You read prompts aloud; both write their answer simultaneously; the class judges who's right. It's fast, loud, and deliberately low-stakes — the purpose is energy and repetition, not assessment.

### Why it's here

Relational operators need drilling, not discussion. Six operators become automatic through rapid repetition, and this is minute 22 of a lecture — the room needs a lift.

### Before class

Clear a section of whiteboard, two markers ready.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Call two volunteers up, explain the rules | Two go to the board |
| 0:30–4:00 | Read prompts one at a time, class judges each | Write; class calls the winner |
| 4:00–5:00 | Debrief | Listen |

### Say this

> *"Two volunteers to the board. I read, you both write, the class decides. No laptops, no notes. This is not a test — it's a warm-up for your fingers."*

### The prompts

Read one at a time. Give ~15 seconds each.

| # | Prompt | Answer |
|---|---|---|
| 1 | Write code that checks if 8 is bigger than 3 | `print(8 > 3)` |
| 2 | Write code that checks if `a` equals 10 | `print(a == 10)` |
| 3 | Write code that checks if `x` is **not** 5 | `print(x != 5)` |
| 4 | What does `print(4 >= 4)` show? | `True` |
| 5 | Fix this: `print(3 = 3)` | `print(3 == 3)` |

### When it goes wrong

| If… | Do this |
|---|---|
| No volunteers | Name two people directly, lightly: *"Front row — you two, up."* Once it's been done once, volunteers come easily. |
| Both write the same wrong answer | Perfect teaching moment. *"You both agree, and you're both wrong. Class?"* |
| Class won't judge | Ask a specific person: *"Fourth row — which one's right?"* |
| It gets competitive or unkind | Cut it short and move on. The energy is the point; humiliation isn't. |
| Prompt 5 stumps them | This is the key one. If both miss it, spend a minute — `=` vs `==` recurs in the quiz. |

**Common instructor mistake:** letting it run long because it's fun. Five minutes, hard stop.

**Cut rule:** Prompts 1, 3 and 5.

---

## Classroom Quiz (27–34 min)

5 MCQs from the platform pools. ~80 s each including discussion.

**Q1** — `dae6dcf7-175e-436f-a917-e4150c4f1c09` *(Quiz A · REMEMBERING)*
Which relational operator in Python checks for equality between two values?
- `=`
- `>=`
- ✅ **`==`**
- `<=`

> *Explanation (platform):* The '==' operator is used to check if two values are equal in Python.

**Q2** — `a1f1566a-d8ee-4db7-963f-e5b6af89d3f9` *(Quiz A · UNDERSTANDING)*
What is the output of `print(7 > 3)`?
- False
- `4`
- ✅ **True**
- SyntaxError

> *Explanation (platform):* The expression 7 > 3 evaluates to True because 7 is greater than 3.
> **If anyone picks `4`:** they're expecting a calculation. Comparisons answer questions, they don't compute values.

**Q3** — `314fb90a-f760-49ac-ad61-aa643106b57d` *(Quiz A · APPLYING)*
Identify the error in `print(3 = 3)`.
- print should be Print
- ✅ **SyntaxError due to incorrect way of comparing**
- No error, the code is correct
- The numbers being compared are not valid

> *Explanation (platform):* The '=' operator is used for assignment, not for comparison. The correct operator for checking equality is '=='.
> **If >40% miss this:** stop and re-run the board comparison of `=` versus `==`. It costs a minute now and saves a session later.

**Q4** — `5275c12c-f77f-4b89-b003-0343aee3ed01` *(Quiz A · APPLYING)*
How do you fix the error in `print(2 < = 3)`?
- No fix needed; the code is correct
- ✅ **Remove the space between `<` and `=`**
- Replace `<=` with `=<`
- None of the given options

> *Explanation (platform):* The correct syntax for the 'less than or equal to' operator is '<=', without any space between the characters.
> **If they pick `=<`:** worth 20 seconds — the order is fixed, and `=<` is not valid Python at all.

**Q5** — `38e3ffaf-9e11-4f0b-bf3a-be7985916425` *(Quiz A · ANALYZING)*
What will be the output of `print(10 == '10')`?
- True
- ✅ **False**
- `'10'`
- TypeError

> *Explanation (platform):* The output will be False because the integer 10 is not equal to the string '10'.
> **This is the session's hardest question and its most important.** If they expected `True`, they're comparing what things *look like* rather than what they *are*. Note that Python doesn't error here — it just says False, which makes this a silent bug. Ties directly to Session 7's crash-vs-bug distinction.

---

## Teaching Block B (34–44 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from RM `e03da18b-8523-445e-81e9-8519b1c16a61` -->

**Cover three things, in this order.**

**1. The two syntax traps** — type both, let both fail:

```python
print(3 = 3)      # SyntaxError: perhaps you meant "=="?
print(2 < = 3)    # SyntaxError: invalid syntax
```

Read the first error aloud — Python literally suggests `==`. Say: *"It's telling you the answer. Read your errors."*

**2. Comparing across number types** — type and run:

```python
print(2 <= 3)         # True
print(2.53 >= 2.55)   # False
print(12 == 12.0)     # True   ← the surprising one
print(12 == 12.1)     # False
```

`12 == 12.0` being `True` surprises rooms. Say: *"An integer and a float can be equal, because both are numbers. Same value, different container."*

**3. Comparing strings** — type and run:

```python
print("Python" == "python")    # False
print("abc" < "abd")           # True
print(10 == "10")              # False
```

- **Case matters.** `"Python"` and `"python"` are different strings.
- **Strings compare alphabetically.** `"abc" < "abd"` is `True` because `c` comes before `d`.
- **A number is never equal to a string**, even when they look identical.

**Checkpoint (at 44 min)** — show hands:
> *"`print(12 == 12.0)` — True or False? And `print(12 == "12")`?"*
> **Answer:** `True`, then `False`. Both numbers versus a number and a string.

---

## ⚡ Activity 2 — Spot the Bug (44–50 min)

### What this activity is

Broken snippets on screen. Students find each problem **and name the error type** before offering a fix. One snippet doesn't crash at all — it just gives the wrong answer, and finding that one is the point.

### Why it's here

Every trap in this session — `=` vs `==`, the space in `< =`, the number-vs-string comparison — is a typo-level mistake that students will make tonight. This rehearses all three.

### Before class

All four snippets ready to run.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line | Listen |
| 0:30–1:30 | Show all four, silence | Diagnose on paper |
| 1:30–5:00 | Take one at a time, run each live | Name error + fix |
| 5:00–6:00 | Debrief on #4 | Listen |

### Say this

> *"Four snippets. Tell me what's wrong and what it's called. Then the fix. Ninety seconds, silent."*

### The snippets

```python
# 1
age = 18
print(age = 18)
```
```python
# 2
print(5 > = 3)
```
```python
# 3
password = "Python123"
print(password == "python123")
```
```python
# 4
user_age = input()
print(user_age == 18)
```

### Answers

| # | Diagnosis | Fix |
|---|---|---|
| 1 | `SyntaxError` — `=` assigns, doesn't compare | `print(age == 18)` |
| 2 | `SyntaxError` — space inside `>=` | `print(5 >= 3)` |
| 3 | **No error.** Prints `False` — capital `P` vs lowercase `p` | Match the case, or accept that it's genuinely different |
| 4 | **No error.** Always prints `False` — `input()` gives a string, and a string never equals a number | `int(user_age) == 18` |

**Snippet 4 is the one that matters.** It runs fine, produces `False` no matter what the user types, and combines Session 6, Session 8 and today. Ask directly:

> *"The user types 18. It prints False. Nothing crashed. How long would it take you to find that bug tonight?"*

### When it goes wrong

| If… | Do this |
|---|---|
| They spot 1–3 but not 4 | Expected and fine. Run it, type `18`, let `False` sit on screen in silence. |
| Someone says #3 is a bug | Push back gently — it depends on intent. If passwords should be case-sensitive, it's correct behaviour. Good nuance. |
| Nobody can fix #4 | Give it. The diagnosis matters more than the fix here. |
| Running long | Do 1 and 4. Snippet 4 is non-negotiable. |

**Common instructor mistake:** rushing snippet 4 because it's last. Reverse the order if you're worried about time — it deserves the most.

---

## ⚡ Activity 3 — Trace the Table (50–57 min)

### What this activity is

Students write a small table on paper and fill it in row by row as you read code aloud, tracking what each variable holds and what each comparison evaluates to. No laptops. It's slow, deliberate, and builds the mental habit of stepping through code.

### Why it's here

Next session combines comparisons with `and`/`or`. That is impossible for students who can't yet evaluate a single comparison reliably. This is the rehearsal.

### Before class

Nothing. Students need paper and a pen.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, dictate the column headers | Draw the table |
| 0:30–4:30 | Read one line at a time, pause after each | Fill in a row |
| 4:30–6:00 | Take answers row by row from different students | Report |
| 6:00–7:00 | Debrief | Listen |

### Say this

> *"Paper out, laptops shut. Three columns: `a`, `b`, and `result`. I read a line, you write what's in each after that line. If a line is a comparison, `result` is True or False."*

### The program

```python
a = 5
b = 5.0
result = a == b
a = "5"
result = a == b
result = a != b
```

### The completed table

| After line | `a` | `b` | `result` |
|---|---|---|---|
| `a = 5` | `5` | — | — |
| `b = 5.0` | `5` | `5.0` | — |
| `result = a == b` | `5` | `5.0` | **True** |
| `a = "5"` | `"5"` | `5.0` | True *(unchanged)* |
| `result = a == b` | `"5"` | `5.0` | **False** |
| `result = a != b` | `"5"` | `5.0` | **True** |

### The key moment

Row 3 gives `True` and row 5 gives `False` — **same comparison, same-looking values.** Ask:

> *"Nothing about the comparison changed. Why did the answer flip?"*

**Answer:** `a` stopped being a number and became a string. The types changed, so the answer changed.

Then row 6: `!=` on the same values gives `True`, because they genuinely are not equal.

### When it goes wrong

| If… | Do this |
|---|---|
| Students don't update `result` on the unchanged row | Good catch to make: *"Line 4 didn't touch `result`. It still holds what it held."* Variables persist. |
| Row 3 is contested | Run it live. `5 == 5.0` really is `True` — both are numbers. |
| Somebody finishes instantly | Ask them to predict row 6 before you read it. |
| It's dragging | Stop after row 5. That's where the lesson lives. |

**Common instructor mistake:** reading the lines too fast. Pause a full five seconds after each — students are writing, not just listening.

**Cut rule:** Stop after row 5.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — before anyone leaves:

> Write True or False for each: `7 != 7` · `3 <= 3` · `10 == "10"` · `"a" < "b"`
> **Answers:** False · True · False · True

The third one is the one to scan for on the way out.

**Homework**

| Task | Unit |
|---|---|
| Coding Practice — 10 problems | `9935f186-744c-4b1d-b775-b45056daa899` |
| MCQ Practice — 40 questions | `176ab7ce-6e44-4ff5-9ac9-4bff2bb71f4d` |
| RM — Relational Operators | `e03da18b-8523-445e-81e9-8519b1c16a61` |

> *"If you compare something to `input()` and always get False, you already know why. Convert it first."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `=` compares two things | Ten years of maths | Board comparison in Block A, then Quiz Q3 |
| `< =` with a space is fine | Spaces are usually harmless | Running it — SyntaxError |
| `10 == "10"` is True | They look identical | Quiz Q5 and Activity 3 row 5 |
| Comparisons produce numbers | Everything so far did | Quiz Q2 — the answer is `True`, not `4` |
| `12 == 12.0` is False | Different types must differ | Block B — both are numbers, same value |
| String comparison ignores case | Human reading does | Block B — `"Python" == "python"` is False |
| A wrong comparison will crash | Errors are their feedback | Activity 2 snippet 4 — runs fine, always False |

---

## Instructor Notes

- **⚠️ No video and no slide deck exist for this session in the platform export.** Both teaching blocks above are written as board-and-live-typing sessions built directly from the reading material, and everything you need is spelled out. If a deck does turn up, the two blocks map onto it directly and the activities slot between them unchanged.
- **This session is the runway for Sessions 10–12.** Conditionals are unusable without solid comparisons. If something has to be cut, cut Activity 1 (the board race is energy, not content) — never Quiz Q5 or Activity 3.
- **`=` versus `==` will keep coming back all term.** Write both on the board with their labels at the start and refuse to erase them. The visual reference does more than repetition.
- **Session 4 planted this.** When you taught the assignment operator, you flagged that comparison uses `==` and would arrive later. Call that back explicitly — students remember the promise.
- **Pacing risk:** the string-comparison part of Block B invites tangents about how Python orders letters. Keep it to alphabetical order and move on; the mechanism isn't needed yet.
- **Smallest MCQ pool since Session 4** — 40 questions. If the practice block runs long, Session 8's 130-question pool makes good revision.
