# Session 13 — Loops

**Duration** 60 min · **Topic** Loops · **Prerequisite** Sessions 11–12
**Session type** Concept lecture

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Loops | `3b64b5f7-1d85-4a83-8688-dc9d051d852f` |
| RM — Loops | `44c34a16-eeb9-4a98-8ddc-d06f2eb8db56` |
| Classroom Quiz A (34 q — while basics) | `7d4a3a28-6d7b-4393-b783-c0ce3c9503ab` |
| Classroom Quiz B (27 q — loop failures) | `dc216550-6a6d-4879-8aad-7781b5828834` |
| MCQ Practice (112 q) | `fe6b0aae-e9a6-46f0-bb21-247678eddffb` |
| Coding Practice (11 q) | `e13a266e-9a81-4716-b44f-893002bc30c0` |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State that a loop repeats a block of code while a condition stays True. *(REMEMBERING)*
2. Write a `while` loop with all three parts — initialisation, condition, update. *(APPLYING)*
3. Trace a loop's variables across every iteration. *(ANALYZING)*
4. Diagnose the three loop failures — missing initialisation, condition that never changes, counter never updated. *(ANALYZING)*
5. Predict how many times a given loop body runs. *(APPLYING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 12**. Newly authored. ~45 s each, project the distribution, never name individuals.

**Q1.** Three `elif` conditions are all true. How many blocks run?
`A` All three · `B` One — the first · `C` One — the last · `D` None
→ **B.** *Targets:* First true branch wins.

**Q2.** `x = 100`. What prints?
```python
if x > 3:
    print("Above 3")
elif x > 50:
    print("Above 50")
```
`A` `Above 3` · `B` `Above 50` · `C` Both · `D` Error
→ **A.** *Targets:* Order matters. *Misconception:* B means the ordering lesson didn't land.

**Q3.** Can `elif` come after `else`?
`A` Yes · `B` No — SyntaxError · `C` Only one · `D` Sometimes
→ **B.** *Targets:* `else` is last.

**Q4.** How many spaces per nesting level, by convention?
`A` 1 · `B` 2 · `C` 4 · `D` Any
→ **C.** *Targets:* Four-space standard.

**Q5.** `n = 7`. What prints?
```python
if n > 5:
    print("A")
if n > 3:
    print("B")
```
`A` `A` · `B` `B` · `C` `A` and `B` · `D` Nothing
→ **C.** *Targets:* Separate `if`s both run.

**Q6.** Which are valid? *(MSQ — select all)*
`A` `elif x > 5:` · `B` `elif:` · `C` `else:` · `D` `else x > 5:`
→ **A and C.** *Targets:* `elif` needs a condition, `else` takes none.

**Q7.** How many times does a block inside an `if` run when the condition is True?
`A` Once · `B` Twice · `C` Until it's false · `D` Forever
→ **A.** *Targets:* Conditionals run a block **once**. **This is today's hook** — loops break exactly this assumption. Note the number.

---

## Hook (7–10 min)

> *"Print the numbers 1 to 5."*

Type it the only way they currently can:

```python
print(1)
print(2)
print(3)
print(4)
print(5)
```

> *"Fine. Now do 1 to 1000."*

Wait for the groan.

> *"Right. And that's not laziness — that's a real limit. Everything you've written so far runs each line exactly once."*

Reference **Q7** — *"You all said an `if` block runs once. Correct. Today you get the thing that runs a block again, and again, and again — as long as a condition stays true."*

Type and run:

```python
i = 1
while i <= 5:
    print(i)
    i = i + 1
```

Then change `5` to `1000`, run it, let it scroll.

> *"Four lines. Same four lines for a thousand, or a million. This is the single biggest jump in the course."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred from RM structure, confirm against deck -->
Covers: what loops are for → the `while` loop → the consecutive-numbers example.

**Beats to emphasise**

- **Three parts, and name them every time.** Write them on the board and leave them up:
  ```
  1. INITIALISE   counter = 0        (before the loop)
  2. CONDITION    while counter < 3: (checked before every pass)
  3. UPDATE       counter = counter + 1   (inside the loop)
  ```
  Missing any one of the three is a bug, and each produces a different failure. This framing carries the whole session.
- **The condition is checked *before* every pass**, including the first. If it's false at the start, the body never runs at all.
- **`while` reuses everything they know** — a condition from Session 9, a colon and indentation from Session 11. Say so; it's less new than it looks.

Walk the RM's example line by line with input `4`:

```python
a = int(input())
counter = 0
while counter < 3:
    a = a + 1
    print(a)
    counter = counter + 1
```

Output: `5`, `6`, `7`.

**Checkpoint (at 22 min)** — cold-call two students:
> *"Name the three parts of a while loop and where each one goes."*
> **Answer:** Initialise before the loop, condition on the `while` line, update inside the body.

---

## ⚡ Activity 1 — Trace the Table (22–28 min)

### What this activity is

Students draw a table on paper and fill in one row per loop pass, tracking every variable and the condition's value. No laptops. It is deliberately slow — the point is to see the loop as a sequence of distinct passes rather than a single blurry repetition.

### Why it's here

This is the highest-value activity in the session. Students cannot debug a loop they cannot trace, and every loop failure in Block B is diagnosed by tracing.

### Before class

Nothing. Students need paper and a pen. Draw the empty table on the board first so they copy the right columns.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:40 | Setup line, dictate the four column headers | Draw the table |
| 0:40–4:00 | Walk one pass at a time, pause after each | Fill a row |
| 4:00–5:30 | Take rows from different students | Report |
| 5:30–6:00 | Debrief on the final check | Listen |

### Say this

> *"Paper out, laptops shut. Four columns: `counter`, `condition`, `a`, and `printed`. One row per trip through the loop. I'll walk it; you write."*

### The program

On screen, with input `4`:

```python
a = 4
counter = 0
while counter < 3:
    a = a + 1
    print(a)
    counter = counter + 1
```

### The completed table

| Pass | `counter` at check | `counter < 3` | `a` after | printed |
|---|---|---|---|---|
| 1 | 0 | **True** | 5 | `5` |
| 2 | 1 | **True** | 6 | `6` |
| 3 | 2 | **True** | 7 | `7` |
| 4 | 3 | **False** | 7 | — loop ends |

### The key moment

**Row 4 is the one to press on.** Ask before revealing:

> *"Counter is 3. Does the loop run again?"*

Rooms split. Then: *"The condition is checked one final time, it comes back False, and Python leaves. That fourth check happens — it just doesn't produce a pass."*

Then ask: *"How many times did `print` run?"* — three. *"And what's the highest value counter reached?"* — three. Those two numbers being different is what confuses students all term.

### When it goes wrong

| If… | Do this |
|---|---|
| Students skip row 4 | That's the whole point. *"The loop stopped. Why? Something must have been checked."* |
| Someone loses track mid-trace | Slow down. Do a pass entirely out loud yourself, then hand back. |
| Room finds it easy | Ask: *"What if I deleted `counter = counter + 1`?"* Don't answer — Block B does. |
| It's dragging | Do passes 1 and 4. Row 4 is non-negotiable. |

**Common instructor mistake:** walking the passes too fast. Pause five full seconds after each — students are writing.

**Cut rule:** Passes 1 and 4.

---

## Classroom Quiz (28–35 min)

5 MCQs from the platform pools. ~80 s each including discussion.

**Q1** — `062a16e4-25bd-4231-a7bc-3bdccb582277` *(Quiz A · REMEMBERING)*
What is the primary purpose of using loops in programming?
- To execute a block of code only once
- ✅ **To execute a block of code multiple times**
- To enhance the speed of program execution
- To reduce the number of variables in the code

> *Explanation (platform):* Loops allow us to execute a block of code several times. Without loops, we would need to write the same instructions repeatedly for each execution, making code longer and harder to maintain.

**Q2** — `e70489bb-4f3b-40e0-a5fb-c3868930b55d` *(Quiz A · UNDERSTANDING)*
What will be the output of:
```python
i = 0
while i < 3:
    print(i)
    i = i + 1
```
- `0 1 2 3`
- `1 2 3`
- ✅ **`0 1 2`**
- `0 1`

> *Explanation:* **[authored — the platform record has an empty explanation field]** `i` starts at 0 and the loop runs while `i < 3`. It prints 0, 1 and 2. When `i` becomes 3 the condition is False and the loop ends, so 3 is never printed.
> **If they pick `0 1 2 3`:** they're forgetting the condition is checked *before* the body. Point back to Activity 1's row 4.

**Q3** — `ef4a1245-91f4-41f2-a74b-54a716771534` *(Quiz A · APPLYING)*
What is the error in:
```python
counter = 0
while counter < 3
    print("Loop iteration")
    counter = counter + 1
```
- The increment of counter is incorrect
- There is no error in the code
- The print statement should be indented
- ✅ **Missing colon after the while condition**

> *Explanation (platform):* The syntax of a while loop requires a colon at the end of the while statement, just like conditional statements. Without it, Python cannot identify where the condition ends and the loop block begins.

**Q4** — `eb9a145c-7254-4246-9b0e-27fa60abd0a4` *(Quiz B · APPLYING)*
Identify the error in:
```python
a = 5
while counter < 3:
    a = a + 1
    print(a)
    counter = counter + 1
print("End")
```
- SyntaxError
- ✅ **Counter variable is not initialised**
- `a` should be initialised with 1
- IndentationError

> *Explanation (platform):* The code attempts to use `counter` in the while condition before it has been assigned a value. A variable must be created by assigning a value to it before it can be used.
> **This is failure #1 of three.** The error is a NameError — the same one from Session 5, in a new place.

**Q5** — `80733d77-44d1-4b2e-bb47-3d824b29a198` *(Quiz B · ANALYZING)*
What will be the output of:
```python
counter = 0
while counter < 3:
    print("Python is fun!")
```
- `"Python is fun!"` printed three times
- ✅ **`"Python is fun!"` printed infinite times**
- No output
- Error

> *Explanation:* **[authored — the platform record has an empty explanation field]** The counter is never updated inside the loop, so `counter < 3` stays True forever and the loop never ends. The program prints continuously until it is stopped manually.
> **This is failure #3 and the most disorienting one.** No error message ever appears. The program simply never stops. **Tell them now how to stop it: Ctrl+C in the terminal, or the stop button on the platform.** They will need this within the hour.

---

## Slide Block B (35–45 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred from RM structure, confirm against deck -->
Covers: Possible Mistakes — missing initialisation, incorrect termination condition, counter not updated.

**Beats to emphasise**

Map each failure back to the three parts from Block A. **Run all three live** — students need to see an infinite loop happen and be stopped.

**Failure 1 — no initialisation (part 1 missing)**
```python
while counter < 3:      # NameError: 'counter' is not defined
```
Crashes immediately. The friendly failure — it tells you what's wrong.

**Failure 2 — condition frozen in a variable (part 2 broken)**
```python
counter = 0
condition = (counter < 3)
while condition:
    counter = counter + 1
```
`condition` was computed **once, before the loop**, and holds `True` forever. Updating `counter` changes nothing. This is subtle and worth real time.

**Failure 3 — no update (part 3 missing)**
```python
counter = 0
while counter < 3:
    print("Hi")         # counter never changes → infinite
```

**Run failure 3 live and stop it with Ctrl+C in front of them.** Say: *"This will happen to you tonight. Now you know it isn't broken — it's just waiting, and you know how to stop it."*

**Checkpoint (at 45 min)** — show hands:
> *"Which of the three parts is missing in an infinite loop like failure 3?"*
> **Answer:** The update. The counter never changes, so the condition never becomes False.

---

## ⚡ Activity 2 — Predict the Output (45–51 min)

### What this activity is

You reveal a snippet, **the class commits to an answer out loud before you run it**, then you run it. The public commitment converts passive watching into an active prediction students remember being right or wrong about.

### Why it's here

Off-by-one errors and infinite loops are the two things students will hit tonight. This makes both happen in a controlled setting first.

### Before class

Snippets in a file, revealed one at a time. **Be ready to Ctrl+C** — snippet 4 does not stop on its own.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:20 | Setup line | Listen |
| 0:20–4:30 | Reveal, take a chorus answer, **then** run | Predict aloud |
| 4:30–6:00 | Debrief | Listen |

### Say this

> *"Everyone answers out loud together before I run it. How many lines print, and what are they? One of these doesn't stop — I'll deal with that."*

### The snippets

```python
i = 1                   # 1
while i <= 3:
    print(i)
    i = i + 1
```
```python
i = 0                   # 2
while i < 0:
    print(i)
    i = i + 1
```
```python
i = 5                   # 3
while i > 0:
    print(i)
    i = i - 2
```
```python
i = 1                   # 4  — will not stop
while i <= 3:
    print(i)
```

### Answers

| # | Output | Why |
|---|---|---|
| 1 | `1 2 3` | Runs while `i` is 1, 2, 3; stops at 4 |
| 2 | **Nothing** | Condition is False on the first check — the body never runs |
| 3 | `5 3 1` | Counts *down* by 2; stops when `i` reaches −1 |
| 4 | `1` forever | No update — infinite |

**Snippet 2 surprises most rooms** — a loop that runs zero times is valid, not an error.
**Snippet 3** shows the counter doesn't have to go up by one.
**Snippet 4** — take the prediction, run it, let it scroll for three seconds, then Ctrl+C in full view.

### When it goes wrong

| If… | Do this |
|---|---|
| Room says snippet 2 errors | Run it. Nothing happens. *"Zero times is a valid number of times."* |
| Someone gets snippet 3 wrong | Trace it on the board — 5, 3, 1, then −1 fails the check. |
| The room panics at snippet 4 | Good. Then show Ctrl+C calmly. That calm is what you're teaching. |
| Running late | Snippets 2 and 4. |

**Common instructor mistake:** skipping snippet 4 to avoid the infinite loop. It's the most valuable one — students must see it stopped, or they'll assume they broke the computer.

**Cut rule:** Snippets 2 and 4.

---

## ⚡ Activity 3 — Live Coding: Countdown (51–57 min)

### What this activity is

You're at the keyboard on the projector; students dictate every line. You type only what they say, and you deliberately produce one broken version for the class to diagnose.

### Why it's here

It assembles all three loop parts into one program while students still have the trace table fresh, and it is the shape of tonight's homework.

### Before class

Empty file, font ≥18pt. Ctrl+C ready.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, state the goal | Listen |
| 0:30–3:00 | Type what they dictate, run | Dictate |
| 3:00–5:00 | Introduce the bug, let them find it | Diagnose |
| 5:00–6:00 | Fix, run, debrief | Confirm |

### Say this

> *"You're writing this, I'm the keyboard. Goal: count down from 5 to 1, then print `Liftoff`. Tell me the three parts before you tell me any code."*

Make them name initialise / condition / update **before** dictating. That's the habit being built.

### Target program

```python
n = 5
while n > 0:
    print(n)
    n = n - 1
print("Liftoff")
```

### The deliberate bug

Type this version instead and run it:

```python
n = 5
while n > 0:
    print(n)
    n = n + 1
```

It counts *up* forever. Let it run three seconds, Ctrl+C.

> *"Which of the three parts is wrong? Not missing — wrong."*

**Answer:** the update. It exists, but it moves the counter *away* from making the condition false.

> *"An update that goes the wrong direction is the same as no update at all."*

### When it goes wrong

| If… | Do this |
|---|---|
| They dictate it perfectly first time | Say *"too good"*, then type the `n + 1` version yourself and ask what happens. |
| Nobody names the three parts | Point at the board. They're still written up from Block A. |
| They put `print("Liftoff")` indented | Run it. It prints five times. *"Which block is it in?"* |
| Someone asks about `for` loops | Say Session 15, two sessions away. Don't teach it. |

**Common instructor mistake:** typing ahead when the room hesitates. Wait.

**Cut rule:** Skip the correct version, go straight to the bug and fix it.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — before anyone leaves:

> Name the three parts of a while loop. Then say how many times this prints:
> ```python
> i = 0
> while i < 4:
>     print("Hi")
>     i = i + 1
> ```
> **Answers:** Initialise, condition, update. Four times — `i` is 0, 1, 2, 3.

**Homework**

| Task | Unit |
|---|---|
| Coding Practice — 11 problems | `e13a266e-9a81-4716-b44f-893002bc30c0` |
| MCQ Practice — 112 questions | `fe6b0aae-e9a6-46f0-bb21-247678eddffb` |
| RM — Loops | `44c34a16-eeb9-4a98-8ddc-d06f2eb8db56` |

> *"When a loop misbehaves tonight, check the three parts in order: is the counter initialised, does the condition ever become false, does the update run every pass. And if it never stops — Ctrl+C. You didn't break anything."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The loop stops the instant the counter hits the limit | The final check is invisible | Activity 1 row 4 — the check happens, then it exits |
| `while i < 3` prints 0,1,2,3 | Off-by-one | Quiz Q2, traced against the table |
| A loop always runs at least once | It's a loop, surely it loops | Activity 2 snippet 2 — zero passes |
| An infinite loop is a crash | The program stops responding | Block B failure 3 — run it, Ctrl+C, stay calm |
| The counter must go up by one | Every example so far did | Activity 2 snippet 3 — counting down by 2 |
| Storing a condition in a variable keeps it live | It reads like a rule | Block B failure 2 — computed once, frozen |
| Any update ends the loop | Update feels like progress | Activity 3's bug — `n + 1` on a `n > 0` condition |

---

## Instructor Notes

- **This is the hardest session in the first fifteen.** Loops are where beginner attrition happens. Everything before this ran once, top to bottom; this breaks that model. Expect the quiz results to be worse than usual and don't read it as failure.
- **Activity 1 is the load-bearing activity.** A student who can trace a loop can debug one; a student who can't will guess all term. If you're short on time, cut Activity 3 rather than shortening the trace.
- **You must demonstrate Ctrl+C.** Students who hit an infinite loop at home and don't know how to stop it conclude they've broken something and stop working. Do it live, twice, calmly.
- **Name the three parts constantly.** Initialise / condition / update, in Block A, in every failure in Block B, and again in Activity 3. The vocabulary is what makes the debugging procedure usable.
- **Two questions in this quiz have empty `answer_explanation` fields** — `e70489bb` and `80733d77`. Authored and labelled above. **Running total is now 12 across the first fifteen sessions.**
- **Pacing note:** the quiz starts at 28 rather than 27 because Activity 1 needs the extra minute. The timeline still totals 60.
- **Don't teach `for` loops.** Session 15. Students who've read ahead will ask; tell them `while` is the general case and `for` is the convenient one, and that seeing `while` first is deliberate.
- **Session 14 is a lighter, support session** before `for` loops arrive. If this session goes badly, Session 14's practice block is your recovery window.
