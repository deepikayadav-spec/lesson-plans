# Session 11 — Conditional Statements

**Duration** 60 min · **Topic** Conditional Statements · **Prerequisite** Sessions 9–10
**Session type** Concept lecture · ⚠️ **No video and no slide deck exist for this session** — see Instructor Notes.

**Platform units**

| Resource | Unit ID |
|---|---|
| RM — Conditional Statements | `0697ecbb-4f80-4cc1-ae05-7aa89881abec` |
| Classroom Quiz A (41 q) | `0c6761ef-0b03-49be-95dd-6d625d711e99` |
| Classroom Quiz B (33 q) | `f69d3517-226e-4a21-9194-8854131645fa` |
| MCQ Practice (140 q) | `672c651f-18bf-4b10-9a82-b744d1f11cf4` |
| Coding Practice (13 q) | `f092d9da-616f-4e13-ac18-f24b5a9c46d8` |

> ⚠️ **You have no deck.** The two "Slide Block" sections are **Teaching Blocks** — board work and live typing, built from the reading material. Everything you need is written out.

---

## Learning Objectives

By the end of this session, students will be able to:

1. Write an `if` statement with correct colon and indentation. *(APPLYING)*
2. Explain that indentation is what defines a block of code in Python. *(UNDERSTANDING)*
3. Add an `else` block and predict which branch runs for a given input. *(APPLYING)*
4. Identify the three syntax failures — missing colon, missing indent, inconsistent indent. *(ANALYZING)*
5. Explain why no code may sit between an `if` block and its `else`. *(UNDERSTANDING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 10**. Newly authored. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `print(True and False)` output?
`A` `True` · `B` `False` · `C` Error · `D` `None`
→ **B.** *Targets:* `and` needs both.

**Q2.** What does `print(True or False)` output?
`A` `True` · `B` `False` · `C` Error · `D` `None`
→ **A.** *Targets:* `or` needs one.

**Q3.** What does `print(not(5 > 3))` output?
`A` `True` · `B` `False` · `C` `5` · `D` Error
→ **B.** *Targets:* `not` flips a True.

**Q4.** Which is valid Python?
`A` `age > 18 and < 60` · `B` `age > 18 and age < 60` · `C` `age > 18 && age < 60` · `D` `18 < age < 60 and`
→ **B.** *Targets:* Both sides must be complete. *Misconception:* A is the most common homework error.

**Q5.** What does `print((4 > 2) and (2 > 4))` output?
`A` `True` · `B` `False` · `C` `4` · `D` Error
→ **B.** *Targets:* Combined comparison with `and`.

**Q6.** Which are True? *(MSQ — select all)*
`A` `(1 < 2) or (5 < 3)` · `B` `(1 < 2) and (5 < 3)` · `C` `not(1 == 2)` · `D` `(3 > 3) or (2 > 3)`
→ **A and C.** *Targets:* All three operators at once.

**Q7.** A comparison like `5 > 3` produces what?
`A` A number · `B` `True` or `False` · `C` Nothing · `D` Text
→ **B.** *Targets:* Booleans. **Today's foundation** — `if` needs exactly this. Note the number.

---

## Hook (7–10 min)

> *"For ten sessions your programs have done the same thing every time you ran them. Every line, top to bottom, no exceptions. Today that ends."*

Type this and run it twice — once entering `5`, once entering `-3`:

```python
a = int(input())
if a > 0:
    print("Positive")
else:
    print("Not Positive")
print("End")
```

> *"Same program. Different input. Different output. It made a choice."*

Then point at the structure:

> *"Look at what's carrying the decision. A condition — the thing you learned to write in the last two sessions. A colon. And some spaces. That's the entire mechanism. Every app you've ever used is built out of this."*

Tie back to **Q7** — *"You told me a comparison gives True or False. That's exactly what `if` is waiting for."*

---

## Teaching Block A (10–22 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from RM `0697ecbb-4f80-4cc1-ae05-7aa89881abec` -->

**Write the shape on the board first and leave it up all session:**

```
if <condition>:
    <indented block>
```

Label the three parts as you write them: **the condition** (must give True or False), **the colon** (ends the condition), **the indentation** (four spaces, marks the block).

**Then type and run:**

```python
if True:
    print("If Block")
    print("Inside If")
print("Outside")
```

Output: all three lines. Then change `True` to `False` and re-run — only `Outside` prints.

> *"The indented lines are inside the block. The un-indented one isn't. Python is deciding what's in and what's out purely by how far the line starts from the left."*

**Then break it three times, live.** Type each, run it, read the error aloud:

```python
if True                      # 1  SyntaxError — no colon
    print("Hi")
```
```python
if True:
print("Hi")                  # 2  IndentationError — no indent
```
```python
if True:
    print("If Block")
        print("Inside If")   # 3  IndentationError — inconsistent
```

**Beats to emphasise**

- **Four spaces is the standard.** Not two, not a tab. Consistency matters more than the number, but pick four and stay there.
- **Every line in a block gets the *same* indentation.** Failure 3 is the one students hit most.
- **The colon is not optional decoration.** It's how Python knows the condition has ended.

**Checkpoint (at 22 min)** — cold-call two students:
> *"Name the three things an `if` statement needs, and what breaks if each is missing."*
> **Answer:** A condition, a colon (SyntaxError), and indentation (IndentationError).

---

## ⚡ Activity 1 — Fill the Blank Live (22–27 min)

### What this activity is

You put code on the projector with a piece missing. Students call out what fills the gap, and **you type exactly what they say — including when it's wrong.** You never silently correct. The gap between what a student *means* and what they *say* stays invisible until someone types it literally.

### Why it's here

`if` syntax has three failure points and students can't yet feel where they are. Typing their exact words exposes each one in seconds.

### Before class

Editor open on the projector, nothing else needed.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, put blank 1 on screen | Read |
| 0:30–4:00 | Take an answer, type it **literally**, run it | Call out |
| 4:00–5:00 | Debrief | Listen |

### Say this

> *"I'm typing exactly what you say. If you say it wrong, we all watch it break — and that's the useful part."*

### The blanks

One at a time. Do not show the target column.

| # | On screen | Target |
|---|---|---|
| 1 | `if 10 > 5___`<br>`    print("Yes")` — *"finish line one"* | `:` |
| 2 | `if 10 > 5:`<br>`___print("Yes")` — *"what goes before print?"* | four spaces |
| 3 | `age = 20`<br>`if ___:`<br>`    print("Adult")` — *"check they're 18 or over"* | `age >= 18` |

### Answers and what they reveal

- **Blank 1 → `:`** — if someone says "nothing", type nothing and run it. The SyntaxError does the teaching.
- **Blank 2 → indentation.** Most rooms say "a space" — type *one* space. It runs. Then ask: *"How many should it be?"* Four is the standard, one merely works.
- **Blank 3 → `age >= 18`.** Watch for `age > 18` (wrong — excludes exactly 18) and `age = 18` (SyntaxError). Both are gold; run them.

### When it goes wrong

| If… | Do this |
|---|---|
| Nobody answers | Wait 10 full seconds. Then: *"I'll take a wrong answer. Wrong is fine here."* |
| Everyone shouts at once | *"One voice. Back row, you."* Pick a person, don't wait for a volunteer. |
| Blank 3 gets `age > 18` | Don't call it wrong. Run it, then ask *"what happens for someone who is exactly 18?"* |
| Someone gets defensive | *"That's the most useful thing that's happened in ten minutes."* Move fast. |

**Common instructor mistake:** silently correcting a student's answer while typing. That destroys the entire mechanism.

**Cut rule:** Blanks 1 and 3.

---

## Classroom Quiz (27–34 min)

5 MCQs from the platform pools. ~80 s each including discussion.

**Q1** — `e96c6f51-8c28-4525-937b-6ad54695b48f` *(Quiz A · REMEMBERING)*
What is the primary purpose of conditional statements in Python?
- To repeat a block of code multiple times
- ✅ **To execute a block of code only when a specific condition is true**
- To declare variables
- To create functions

> *Explanation (platform):* Conditional statements in Python are used to execute a block of code only when a specific condition is true, allowing for control over the flow of the program.
> **If they pick "repeat a block":** that's loops, two sessions away. Name it and move on.

**Q2** — `32ce9380-7d5e-4297-aa9f-7f3a7d78a1c4` *(Quiz A · APPLYING)*
Identify the error in:
```python
a = 6

if a > 5
    print("Greater than 5")
```
- ✅ **The if statement is missing a colon**
- The print statement is not indented
- The variable a is not defined
- There is no error in the code

> *Explanation (platform):* In Python, the if statement must end with a colon. The given code snippet is missing a colon after the if condition.

**Q3** — `b6cc2147-c8c2-444e-8285-7894496594b8` *(Quiz A · APPLYING)*
Identify the error in:
```python
if True:
print("This is a block of code")
```
- The 'if' statement should be capitalized
- There is no error in the code
- ✅ **The indentation is missing before print**
- The print statement should be indented

> *Explanation (platform):* In Python, blocks of code following a conditional statement are identified by their indentation, which is crucial for the correct execution of the code.
> ⚠️ **Two options say nearly the same thing** — "The indentation is missing before print" is marked correct, and "The print statement should be indented" is marked wrong, despite being an accurate description. Expect students to protest, and **acknowledge they have a point.** Say the marked answer identifies the *error* while the other describes the *fix*. Flag it to the content team.

**Q4** — `9172cd37-6cea-4895-982b-a927a5a934f1` *(Quiz B · APPLYING)*
What is the output if the input is `-10`?
```python
a = int(input())
if a > 0:
    print("Positive")
else:
    print("Not Positive")
```
- ✅ **Not Positive**
- `-10`
- Positive
- No output

> *Explanation (platform):* The code uses an if-else statement to check if the input number is greater than zero. Since -10 is not greater than zero, the else block will execute, printing "Not Positive".

**Q5** — `cb04cd34-b2b2-41ad-a868-cd1a2dd1a8cc` *(Quiz B · ANALYZING)*
Identify the error in:
```python
if False:
    print("If Block")
print("After If")
else:
    print("Else Block")
```
- There is no error in the code
- The print statement "After If" should be changed to "Before else"
- The print statement "Else Block" is wrongly indented
- ✅ **Code is present between if and else block**

> *Explanation (platform):* Placing statements between an if and else block in Python will cause a syntax error because the else block must immediately follow the if block without any other instructions in between.
> **This is the session's hardest question.** `else` is not a standalone statement — it's the second half of one statement that began with `if`. Nothing may come between them.

---

## Teaching Block B (34–44 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from RM `0697ecbb-4f80-4cc1-ae05-7aa89881abec` -->

**Write the shape on the board beneath the `if` shape from Block A:**

```
if <condition>:
    <runs when True>
else:
    <runs when False>
```

**Then type and run**, entering `2` and then `-2`:

```python
a = int(input())
if a > 0:
    print("Positive")
else:
    print("Not Positive")
print("End")
```

**Three things to draw out:**

1. **Exactly one branch runs.** Never both, never neither. Ask the room to confirm before each run.
2. **`print("End")` runs every time** — it's outside both blocks. Point at its indentation.
3. **`else` has no condition.** It's just *"otherwise"*. Students try to write `else a < 0:` — show it failing.

**Then the illegal version.** Type and run:

```python
if False:
    print("If Block")
print("After If")
else:
    print("Else Block")
```

SyntaxError.

> *"`else` isn't its own statement. It's the back half of the `if`. Put anything between them and Python loses track of which `if` the `else` belongs to."*

**Checkpoint (at 44 min)** — show hands:
> *"In an if-else, how many of the two blocks run?"*
> **Answer:** Exactly one. Always.

---

## ⚡ Activity 2 — Trace the Table (44–50 min)

### What this activity is

Students draw a small table on paper and fill it in row by row as you read code aloud — tracking the variable, whether the condition is True or False, and which branch runs. No laptops. It's slow and deliberate, and it builds the habit of stepping through a decision rather than guessing the outcome.

### Why it's here

Students predict conditional output by intuition and are often right by luck. This forces the actual evaluation, which is the skill nested conditionals will demand next session.

### Before class

Nothing. Students need paper and a pen.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, dictate the headers | Draw the table |
| 0:30–3:30 | Read each input value, pause | Fill a row |
| 3:30–5:00 | Take rows from different students | Report |
| 5:00–6:00 | Debrief on the boundary case | Listen |

### Say this

> *"Paper out, laptops shut. Three columns: `input`, `condition True or False`, and `what prints`. I'll give you an input, you complete the row."*

### The program

Put it on screen and leave it there:

```python
marks = int(input())
if marks >= 40:
    print("Pass")
else:
    print("Fail")
print("Done")
```

### Read these inputs one at a time

| Input | `marks >= 40` | Prints |
|---|---|---|
| `75` | True | `Pass` then `Done` |
| `12` | False | `Fail` then `Done` |
| `40` | **True** | `Pass` then `Done` |
| `39` | False | `Fail` then `Done` |
| `0` | False | `Fail` then `Done` |

### The key moment

Row 3 — input `40` — is the whole activity. Ask before revealing:

> *"Forty. Pass or fail?"*

Rooms split. Then: *"`>=` includes the number itself. If the rule is 'forty or above', `>` would be a bug — and a student would fail by one mark because of one character."*

Also press on `Done`: it appears in **every** row. Ask why.
**Answer:** it isn't indented, so it isn't in either block.

### When it goes wrong

| If… | Do this |
|---|---|
| Everyone gets row 3 right | Ask what `>` would have done instead. The contrast is the lesson. |
| Someone forgets `Done` on later rows | *"Check row one. Did `Done` print? Why would it stop?"* |
| Room finds it too easy | Add a row: what if the input is `"forty"` as text? (ValueError from `int()` — ties back to Session 8.) |
| It's dragging | Do inputs 75, 40 and 39 only. |

**Common instructor mistake:** reading the inputs too fast. Pause five full seconds — students are writing, not just listening.

**Cut rule:** Inputs 75, 40, 39.

---

## ⚡ Activity 3 — Live Coding: The Gatekeeper (50–57 min)

### What this activity is

You're at the keyboard on the projector; students dictate every line and you type only what they say. You deliberately produce one broken version so the class diagnoses it.

### Why it's here

It assembles the session — `int(input())`, a comparison, `if`/`else` — into one program that is exactly the shape of tonight's homework.

### Before class

Empty file, font ≥18pt, terminal visible so input prompts show.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, state the goal | Listen |
| 0:30–3:00 | Type what they dictate, run often | Dictate |
| 3:00–5:30 | Introduce the bug, let them find it | Diagnose |
| 5:30–7:00 | Fix, run, debrief | Confirm |

### Say this

> *"You're writing this, I'm the keyboard. Goal: ask for someone's age, then print `Welcome` if they're 18 or over, and `Sorry` if they're not."*

### Target program

```python
age = int(input())
if age >= 18:
    print("Welcome")
else:
    print("Sorry")
```

Build it a line at a time. Run with `20`, then `15`, then **`18`** — that last one is the boundary from Activity 2, and it's worth testing out loud.

### The deliberate bug

Before you finish, type this version and run it with `20`:

```python
age = input()
if age >= 18:
    print("Welcome")
else:
    print("Sorry")
```

**TypeError** — `'>=' not supported between instances of 'str' and 'int'`.

> *"Read it. It's telling you exactly what happened. What's missing?"*

Take the fix — `int()` around `input()`. Sessions 6, 8 and today, in one line.

### When it goes wrong

| If… | Do this |
|---|---|
| They dictate the correct version instantly | Say *"too good"*, then type the broken one yourself and ask what it does. The bug must happen. |
| Nobody diagnoses the TypeError | Ask: *"What does `input()` always give you? What are we comparing it to?"* |
| They write `if age > 18` | Run it with `18`. `Sorry`. Then ask whether that's what was asked for. |
| Someone suggests `elif` | Say it's real and it's next session's topic. Don't teach it now. |

**Common instructor mistake:** typing ahead when the room hesitates. The silence is productive — wait.

**Cut rule:** Skip the boundary tests, keep the bug.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — before anyone leaves:

> Write an `if`/`else` that prints `Even` when `n` is even and `Odd` otherwise. Then say what `print("Done")` at the end, un-indented, would do.
> **Answers:** `if n % 2 == 0:` / `    print("Even")` / `else:` / `    print("Odd")`. `Done` prints every time — it's outside both blocks.
> `%` hasn't been formally taught — accept any correct condition, and tell them `%` gives the remainder.

**Homework**

| Task | Unit |
|---|---|
| Coding Practice — 13 problems | `f092d9da-616f-4e13-ac18-f24b5a9c46d8` |
| MCQ Practice — 140 questions | `672c651f-18bf-4b10-9a82-b744d1f11cf4` |
| RM — Conditional Statements | `0697ecbb-4f80-4cc1-ae05-7aa89881abec` |

> *"Three things to check when an `if` breaks: colon at the end, four spaces on every line of the block, and `int()` around any input you compare with `>` or `<`."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Indentation is cosmetic | True in most other languages | Block A failure 2 — no indent, IndentationError |
| Any indentation works as long as there is some | It "looks" indented | Block A failure 3 — inconsistent indent still fails |
| `else` can have a condition | It feels like a second `if` | Block B — `else a < 0:` fails |
| Code can sit between `if` and `else` | They look like separate statements | Quiz Q5 and Block B's illegal version |
| `>` and `>=` are interchangeable | Both "mean" greater | Activity 2 row 3 — input `40` |
| Both branches might run | No mental model yet | Block B checkpoint — exactly one, always |
| You can compare `input()` directly | It looks like a number | Activity 3's deliberate bug |

---

## Instructor Notes

- **⚠️ No video and no slide deck exist for this session in the platform export.** Both teaching blocks are written as board-and-live-typing sessions built from the reading material. If a deck appears, the blocks map onto it directly and the activities slot between unchanged.
- **Three sessions in a row without a deck** (9, 10, 11). Your board carries all three. Consider photographing the board at the end — the `if` and `if/else` shapes especially, since students will copy them all term.
- **This is the payoff session for 9 and 10.** Comparisons and logical operators had no visible use until now. Say so explicitly in the hook — it retroactively justifies two sessions of abstract work.
- **⚠️ Quiz Q3 has two defensible options.** "The indentation is missing before print" is marked correct; "The print statement should be indented" is marked wrong but describes the same problem as a fix. Students will argue and they're not being difficult. Handle it as scripted and file it with the content team.
- **Don't teach `elif` today.** It's Session 12's opening. Students will ask during Activity 3 — name the session and move on.
- **`%` appears in the exit ticket** but hasn't been formally taught. It shows up throughout the coding practice set, so mention it in one sentence: `%` gives the remainder, `n % 2 == 0` means even.
- **140 MCQ questions** — the largest pool in the first fifteen sessions. No shortage for the practice block.
