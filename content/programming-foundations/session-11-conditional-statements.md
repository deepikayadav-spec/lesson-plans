# Session 11 — Conditional Statements

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Conditional Statements · **Prerequisite** Sessions 9–10
**Session type** Concept lecture · ⚠️ **No video and no slide deck exist for this session** — see Instructor Notes. · **Format** 50-min recalibrated, 2 ALS activities, Classroom Quiz mandatory (never cut, runs last)

**Platform units**

| Resource | Unit ID |
|---|---|
| RM — Conditional Statements | `0697ecbb-4f80-4cc1-ae05-7aa89881abec` |
| Classroom Quiz A (41 q) | `0c6761ef-0b03-49be-95dd-6d625d711e99` |
| Classroom Quiz B (33 q) | `f69d3517-226e-4a21-9194-8854131645fa` |
| MCQ Practice (140 q) | `672c651f-18bf-4b10-9a82-b744d1f11cf4` |
| Coding Practice (13 q) | `f092d9da-616f-4e13-ac18-f24b5a9c46d8` |

> ⚠️ **You have no deck.** The two "Teaching Block" sections replace Slide Blocks — board work and live typing, built from the reading material.

---

## Learning Objectives

By the end of this session, students will be able to:

1. Write an `if` statement with correct colon and indentation. *(APPLYING)*
2. Explain that indentation is what defines a block of code in Python. *(UNDERSTANDING)*
3. Add an `else` block and predict which branch runs for a given input. *(APPLYING)*
4. Identify the three syntax failures — missing colon, missing indent, inconsistent indent. *(ANALYZING)*
5. Explain why no code may sit between an `if` block and its `else`. *(UNDERSTANDING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** state the MCQ Practice completion number since last session. Target is 80%.

5 questions on **Session 10**. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `print(True and False)` output?
`A` `True` · `B` `False` · `C` Error · `D` `None`
→ **B.** *Targets:* `and` needs both.

**Q2.** What does `print(not(5 > 3))` output?
`A` `True` · `B` `False` · `C` `5` · `D` Error
→ **B.** *Targets:* `not` flips a True.

**Q3.** Which is valid Python?
`A` `age > 18 and < 60` · `B` `age > 18 and age < 60` · `C` `age > 18 && age < 60` · `D` `18 < age < 60 and`
→ **B.** *Targets:* Both sides must be complete. *Misconception:* A is the most common homework error.

**Q4.** What does `print((4 > 2) and (2 > 4))` output?
`A` `True` · `B` `False` · `C` `4` · `D` Error
→ **B.** *Targets:* Combined comparison with `and`.

**Q5.** A comparison like `5 > 3` produces what?
`A` A number · `B` `True` or `False` · `C` Nothing · `D` Text
→ **B.** *Targets:* Booleans. **Today's foundation** — `if` needs exactly this. Note the number.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–11 min)

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

Tie back to **Q5** — *"You told me a comparison gives True or False. That's exactly what `if` is waiting for."*

---

## Teaching Block A (11–18 min) — BOARD + LIVE TYPING

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

**Checkpoint + Quick Fill (at 18 min, ~2 min)** — 10 s silent think, cold-call two students for the checkpoint, then a compressed fill-the-blank beat (folded in here to protect the schedule):
> *Checkpoint:* *"Name the three things an `if` statement needs, and what breaks if each is missing."* Answer: A condition, a colon (SyntaxError), and indentation (IndentationError).
> *Quick fill:* put `age = 20` / `if ___:` / `    print("Adult")` on screen — *"fill the blank to check they're 18 or over."* Take the answer literally. Watch for `age > 18` (wrong — excludes exactly 18) — run it, ask what happens for someone exactly 18. That boundary comes back in ALS Activity 1.

---

## ⚡ ALS Activity 1 — Dictated Row-by-Row Tracing: Trace the Table (18–24 min)

**ALS format:** Guided Individual Tracing — everyone fills their own table silently as you read inputs aloud, no pairing. Chosen because students predict conditional output by intuition and are often right by luck; forcing the actual row-by-row evaluation is what nested conditionals will demand next session.

**Setup line:**
> *"Paper out, laptops shut. Three columns: `input`, `condition True or False`, and `what prints`. I'll give you an input, you complete the row."*

Put the program on screen and leave it there:

```python
marks = int(input())
if marks >= 40:
    print("Pass")
else:
    print("Fail")
print("Done")
```

Read these inputs one at a time:

| Input | `marks >= 40` | Prints |
|---|---|---|
| `75` | True | `Pass` then `Done` |
| `40` | **True** | `Pass` then `Done` |
| `39` | False | `Fail` then `Done` |

**The key moment:** row 2 — input `40` — is the whole activity. Ask before revealing:
> *"Forty. Pass or fail?"*

Rooms split. Then: *"`>=` includes the number itself. If the rule is 'forty or above', `>` would be a bug — and a student would fail by one mark because of one character."*

Also press on `Done`: it appears in **every** row. Ask why. **Answer:** it isn't indented, so it isn't in either block.

**Debrief line:**
> *"One character — `>` versus `>=` — is the difference between a correct grading program and one that fails someone unfairly. That's why you trace boundaries, not just the obvious cases."*

**Cut rule:** Inputs 75 and 40 only.

---

## Classroom Quiz (24–31 min) · ALS: Individual Answer → Reveal

> 🔒 **Mandatory block — do not cut, do not shorten, do not skip under time pressure.** Protect these 7 minutes by using the cut rules everywhere else first.

Every question below is run ALS-style: **individual silent answer first, then explanation.**

5 MCQs from the platform pools. ~85 s each.

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
> ⚠️ **Two options say nearly the same thing.** Expect students to protest, and **acknowledge they have a point.** Say the marked answer identifies the *error* while the other describes the *fix*. Flag it to the content team.

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
> **This is the session's hardest question.** `else` is not a standalone statement — it's the second half of one statement that began with `if`.

---

## Teaching Block B (31–38 min) — BOARD + LIVE TYPING

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

**Checkpoint (at 38 min)** — show hands:
> *"In an if-else, how many of the two blocks run?"*
> **Answer:** Exactly one. Always.

---

## ⚡ ALS Activity 2 — Guided Build + Deliberate Bug: The Gatekeeper (38–45 min)

**ALS format:** Cold-Call Dictation with a Deliberate Bug — students dictate every line of a working program, then watch the instructor deliberately reproduce the exact TypeError from omitting `int()`. Chosen as the closing activity because it assembles everything in the session — `int(input())`, a boundary comparison, `if`/`else` — into the shape of tonight's homework.

**Setup line:**
> *"You're writing this, I'm the keyboard. Goal: ask for someone's age, then print `Welcome` if they're 18 or over, and `Sorry` if they're not."*

**Target program:**

```python
age = int(input())
if age >= 18:
    print("Welcome")
else:
    print("Sorry")
```

Build it a line at a time. Run with `20`, then `15`, then **`18`** — that last one is the boundary from ALS Activity 1, worth testing out loud.

**The deliberate bug** — type this version and run it with `20`:

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

**Debrief line:**
> *"Every piece of this session shows up in that one bug: comparisons need matching types, `input()` gives a string, and reading the error tells you exactly where to look."*

**Cut rule:** Skip the boundary tests (`15`, `18`), keep the bug.

---

## Exit Ticket + Quiz Push (45–48 min)

**Exit ticket** (~30 s) — before anyone leaves:

> Write an `if`/`else` that prints `Even` when `n` is even and `Odd` otherwise. Then say what `print("Done")` at the end, un-indented, would do.
> **Answers:** `if n % 2 == 0:` / `    print("Even")` / `else:` / `    print("Odd")`. `Done` prints every time — it's outside both blocks.
> `%` hasn't been formally taught — accept any correct condition, and tell them `%` gives the remainder.

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Open MCQ Practice. Everyone, this room, right now — attempt the first 3 questions before you leave your seat. 140 questions here, the biggest pool yet."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 12's warm-up."*

**Remaining homework**

| Task | Unit |
|---|---|
| Coding Practice — 13 problems | `f092d9da-616f-4e13-ac18-f24b5a9c46d8` |
| MCQ Practice — 140 questions *(started in class above — finish the rest)* | `672c651f-18bf-4b10-9a82-b744d1f11cf4` |
| RM — Conditional Statements | `0697ecbb-4f80-4cc1-ae05-7aa89881abec` |

> *"Three things to check when an `if` breaks: colon at the end, four spaces on every line of the block, and `int()` around any input you compare with `>` or `<`."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Indentation is cosmetic | True in most other languages | Teaching Block A failure 2 — no indent, IndentationError |
| Any indentation works as long as there is some | It "looks" indented | Teaching Block A failure 3 — inconsistent indent still fails |
| `else` can have a condition | It feels like a second `if` | Teaching Block B — `else a < 0:` fails |
| Code can sit between `if` and `else` | They look like separate statements | Quiz Q5 and Teaching Block B's illegal version |
| `>` and `>=` are interchangeable | Both "mean" greater | ALS Activity 1 — input `40` |
| Both branches might run | No mental model yet | Teaching Block B checkpoint — exactly one, always |
| You can compare `input()` directly | It looks like a number | ALS Activity 2's deliberate bug |

---

## Instructor Notes

- **⚠️ No video and no slide deck exist for this session in the platform export.** Both teaching blocks are written as board-and-live-typing sessions built from the reading material.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Three sessions in a row without a deck** (9, 10, 11). Consider photographing the board at the end — the `if` and `if/else` shapes especially.
- **Two ALS activities this session:** Activity 1 is Guided Individual Tracing (silent, solo, boundary-focused), Activity 2 is Cold-Call Dictation with a Deliberate Bug. The original Fill-the-Blank activity is folded into a 2-minute quick-fill beat at the end of Teaching Block A's checkpoint.
- **The Classroom Quiz runs last, right before the Exit Ticket** — never cut, never shortened.
- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair.** Target is 80% platform MCQ attempt rate, currently ~33%.
- **This is the payoff session for 9 and 10.** Comparisons and logical operators had no visible use until now. Say so explicitly in the hook.
- **⚠️ Quiz Q3 has two defensible options.** Students will argue and they're not being difficult. Handle it as scripted and file it with the content team.
- **Don't teach `elif` today.** It's Session 12's opening. Students will ask during ALS Activity 2 — name the session and move on.
- **`%` appears in the exit ticket** but hasn't been formally taught. Mention it in one sentence: `%` gives the remainder, `n % 2 == 0` means even.
- **140 MCQ questions** — the largest pool in the first fifteen sessions. No shortage for the Quiz Push.
