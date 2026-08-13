# Session 13 — Loops

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Loops · **Prerequisite** Sessions 11–12
**Session type** Concept lecture · **Format** 50-min recalibrated, 2 ALS activities, Classroom Quiz mandatory (never cut, runs last)

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

## Classroom Settling (0–3 min) · Buffer — not instructional

Projector on, deck loaded, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** state the MCQ Practice completion number since last session. Target is 80%.

5 questions on **Session 12**. ~45 s each, project the distribution, never name individuals.

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

**Q3.** How many spaces per nesting level, by convention?
`A` 1 · `B` 2 · `C` 4 · `D` Any
→ **C.** *Targets:* Four-space standard. Same rule that governs today's loop bodies.

**Q4.** `n = 7`. What prints?
```python
if n > 5:
    print("A")
if n > 3:
    print("B")
```
`A` `A` · `B` `B` · `C` `A` and `B` · `D` Nothing
→ **C.** *Targets:* Separate `if`s both run.

**Q5.** How many times does a block inside an `if` run when the condition is True?
`A` Once · `B` Twice · `C` Until it's false · `D` Forever
→ **A.** *Targets:* Conditionals run a block **once**. **This is today's hook** — loops break exactly this assumption. Note the number.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–11 min)

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

Reference **Q5** — *"You all said an `if` block runs once. Correct. Today you get the thing that runs a block again, and again, and again — as long as a condition stays true."*

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

## Slide Block A (11–17 min) — DELIVER SLIDES AS-IS

**Verified against the deck** (*"Copy of 5.1 Loops"*). Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1–3 | Welcome · **Recap — Nested Conditions** | The `if` / `elif` / `else` block diagram from Session 12 |
| 4 | **Introduction — Sequence of Instructions** | "Python executes code in a sequence and each block of code is executed **once**" |
| 5 | **Introduction to Loops — Code** | `a = int(input())` then `a = a + 1` / `print(a)` **written out three times**, input `5` → output `6 7 8` |
| 6 | **While Loop** | The same task as a loop, with `condition` **blanked out and highlighted** → *"What should the condition be?"*, and a dashed arrow showing control jumping back from `counter = counter + 1` to the `while` line |
| 7+ | **While Loop** | `while counter < 3:` filled in, stepping through with **coloured boxes** for `a` (green) and `counter` (purple) updating alongside the output |

**Beats to emphasise**

- **Slide 4 is the setup for your hook.** "Each block is executed *once*" is exactly the assumption loops break.
- **Slide 5 is the manual version.** Ask *"and if I wanted a thousand?"* before advancing.
- **Slide 6 leaves the condition blank and asks the room.** Take answers before revealing. The dashed control-flow arrow shows the jump back — point at it explicitly.
- **Slides 7+ animate two boxes** — `a` and `counter`. This is the deck's version of ALS Activity 1's trace table. Ask *"what's in each box now?"* before each click.
- **Three parts, and name them every time.** Write them on the board and leave them up:
  ```
  1. INITIALISE   counter = 0        (before the loop)
  2. CONDITION    while counter < 3: (checked before every pass)
  3. UPDATE       counter = counter + 1   (inside the loop)
  ```
  Missing any one of the three is a bug, and each produces a different failure. This framing carries the whole session.
- **The condition is checked *before* every pass**, including the first. If it's false at the start, the body never runs at all.

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

**Checkpoint (at 17 min)** — 10 s silent think, cold-call two students:
> *"Name the three parts of a while loop and where each one goes."*
> **Answer:** Initialise before the loop, condition on the `while` line, update inside the body.

---

## ⚡ ALS Activity 1 — Structured Solo Loop-Tracing: Trace the Table (17–24 min)

**ALS format:** Guided Individual Tracing — everyone fills their own table silently, one row per pass, as you dictate. **This is the highest-value activity in the entire session** — a student who can trace a loop can debug one; a student who can't will guess all term. Chosen as fully solo (no pairing) because the skill has to become automatic in each student's own head before Session 14 asks them to debug loops unaided.

**Setup line:**
> *"Paper out, laptops shut. Four columns: `counter`, `condition`, `a`, and `printed`. One row per trip through the loop. I'll walk it; you write."*

On screen, with input `4`:

```python
a = 4
counter = 0
while counter < 3:
    a = a + 1
    print(a)
    counter = counter + 1
```

**The completed table**

| Pass | `counter` at check | `counter < 3` | `a` after | printed |
|---|---|---|---|---|
| 1 | 0 | **True** | 5 | `5` |
| 2 | 1 | **True** | 6 | `6` |
| 3 | 2 | **True** | 7 | `7` |
| 4 | 3 | **False** | 7 | — loop ends |

**Row 4 is the one to press on.** Ask before revealing:
> *"Counter is 3. Does the loop run again?"*

Rooms split. Then: *"The condition is checked one final time, it comes back False, and Python leaves. That fourth check happens — it just doesn't produce a pass."*

Then ask: *"How many times did `print` run?"* — three. *"And what's the highest value counter reached?"* — three. Those two numbers being different is what confuses students all term.

**Debrief line:**
> *"You just watched a loop stop without being told to. That's the whole mechanism — a condition checked one time too many, quietly, every single loop."*

**Cut rule:** Passes 1 and 4. Row 4 is non-negotiable.

---

## Slide Block B (24–31 min) — DELIVER SLIDES AS-IS

**Verified against the deck.** Remaining slides cover **Common Mistakes and Errors** then a **Code Walkthrough**, closing on a Key Takeaways slide that names the session's structure explicitly:

> Loops · While Loop (**Syntax · Initialization · Termination Condition · Updation**) · Common Mistakes and Errors · Code Walkthrough

**Use the deck's own four words** — Syntax, Initialization, Termination Condition, Updation.

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

**Failure 3 — no update, and its cousin, the wrong-direction update (part 3 missing or broken)**
```python
counter = 0
while counter < 3:
    print("Hi")         # counter never changes → infinite
```
Run it live and **stop it with Ctrl+C in front of them.** Say: *"This will happen to you tonight. Now you know it isn't broken — it's just waiting, and you know how to stop it."*

Then show the sneakier cousin — an update that exists but moves the wrong way:
```python
n = 5
while n > 0:
    print(n)
    n = n + 1        # should be n - 1
```
Let it run three seconds, Ctrl+C again. *"Which part is wrong here? Not missing — wrong. An update that moves away from making the condition false is the same as no update at all."*

**Checkpoint (at 31 min)** — show hands:
> *"Which of the three parts was broken in both versions we just stopped?"*
> **Answer:** The update — missing in one, pointed the wrong way in the other.

---

## ⚡ ALS Activity 2 — Choral Prediction → Reveal (31–38 min)

**ALS format:** Choral Prediction — the whole room predicts out loud together before each run. Chosen for the closing activity because it's the safest way to get everyone to commit to a prediction on the one snippet that won't stop on its own — group confidence, followed by a calm live Ctrl+C, defuses what would otherwise be an alarming moment for a student hitting it alone at home.

**Setup line:**
> *"Everyone answers out loud together before I run it. How many lines print, and what are they? One of these doesn't stop — I'll deal with that."*

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

| # | Output | Why |
|---|---|---|
| 1 | `1 2 3` | Runs while `i` is 1, 2, 3; stops at 4 |
| 2 | **Nothing** | Condition is False on the first check — the body never runs |
| 3 | `5 3 1` | Counts *down* by 2; stops when `i` reaches −1 |
| 4 | `1` forever | No update — infinite |

**Snippet 2 surprises most rooms** — a loop that runs zero times is valid, not an error.
**Snippet 4** — take the prediction, run it, let it scroll for three seconds, then Ctrl+C in full view.

**Debrief line:**
> *"Zero passes is valid. Counting down by two is valid. Never stopping is a bug you now know how to interrupt. Loops are more flexible — and more dangerous — than anything you've written so far."*

**Cut rule:** Snippets 2 and 4. Never skip 4 — students must see it stopped, or they'll assume they broke the computer.

---

## Classroom Quiz (38–45 min) · ALS: Individual Answer → Reveal

> 🔒 **Mandatory block — do not cut, do not shorten, do not skip under time pressure.** Runs last, right before the Exit Ticket. Protect these 7 minutes by using the cut rules everywhere else first.

Every question below is run ALS-style: **individual silent answer first, then explanation.**

5 MCQs from the platform pools. ~85 s each.

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
> **If they pick `0 1 2 3`:** they're forgetting the condition is checked *before* the body. Point back to ALS Activity 1's row 4.

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
> **This is failure #3 and the most disorienting one.** No error message ever appears. **Tell them now how to stop it: Ctrl+C in the terminal, or the stop button on the platform.** They will need this within the hour.

---

## Exit Ticket + Quiz Push (45–48 min)

**Exit ticket** (~30 s) — before anyone leaves:

> Name the three parts of a while loop. Then say how many times this prints:
> ```python
> i = 0
> while i < 4:
>     print("Hi")
>     i = i + 1
> ```
> **Answers:** Initialise, condition, update. Four times — `i` is 0, 1, 2, 3.

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Open MCQ Practice. Everyone, this room, right now — attempt the first 3 questions before you leave your seat. 112 questions here."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 14's warm-up."*

**Remaining homework**

| Task | Unit |
|---|---|
| Coding Practice — 11 problems | `e13a266e-9a81-4716-b44f-893002bc30c0` |
| MCQ Practice — 112 questions *(started in class above — finish the rest)* | `fe6b0aae-e9a6-46f0-bb21-247678eddffb` |
| RM — Loops | `44c34a16-eeb9-4a98-8ddc-d06f2eb8db56` |

> *"When a loop misbehaves tonight, check the three parts in order: is the counter initialised, does the condition ever become false, does the update run every pass — and in the right direction. And if it never stops — Ctrl+C. You didn't break anything."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The loop stops the instant the counter hits the limit | The final check is invisible | ALS Activity 1 row 4 — the check happens, then it exits |
| `while i < 3` prints 0,1,2,3 | Off-by-one | Quiz Q2, traced against the table |
| A loop always runs at least once | It's a loop, surely it loops | ALS Activity 2 snippet 2 — zero passes |
| An infinite loop is a crash | The program stops responding | Slide Block B failure 3 — run it, Ctrl+C, stay calm |
| The counter must go up by one | Every example so far did | ALS Activity 2 snippet 3 — counting down by 2 |
| Storing a condition in a variable keeps it live | It reads like a rule | Slide Block B failure 2 — computed once, frozen |
| Any update ends the loop | Update feels like progress | Slide Block B's wrong-direction demo — `n + 1` on a `n > 0` condition |

---

## Instructor Notes

- ✅ **Verified against the real deck** (*"Copy of 5.1 Loops"*). Slide Blocks A and B list the actual slides in order.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **This is the hardest session in the first fifteen.** Loops are where beginner attrition happens. Expect the quiz results to be worse than usual and don't read it as failure.
- **Two ALS activities this session:** Activity 1 is Guided Individual Tracing — **the load-bearing activity of the session, protect it above everything except the mandatory quiz.** Activity 2 is Choral Prediction → Reveal, chosen specifically so the infinite-loop snippet is faced as a group. The original third activity (Live Coding: Countdown) is folded into Slide Block B as the wrong-direction-update demo instead of running as its own block — its unique insight (a bug that isn't "missing," just pointed the wrong way) survives.
- **The Classroom Quiz runs last, right before the Exit Ticket** — never cut, never shortened.
- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair.** Target is 80% platform MCQ attempt rate, currently ~33%.
- **You must demonstrate Ctrl+C, twice, calmly.** Students who hit an infinite loop at home and don't know how to stop it conclude they've broken something and stop working. ⚠️ The deck never demonstrates this — it's entirely instructor-supplied.
- **Name the three parts constantly.** Initialise / condition / update — in Slide Block A, in every failure in Slide Block B, and again in the Exit Ticket. The vocabulary is what makes the debugging procedure usable.
- **Two questions in this quiz have empty `answer_explanation` fields** — `e70489bb` and `80733d77`. Authored and labelled above.
- **Don't teach `for` loops.** Session 15. Tell curious students `while` is the general case and `for` is the convenient one, and that seeing `while` first is deliberate.
- **Session 14 is a lighter, support session** before `for` loops arrive. If this session goes badly, Session 14's practice block is your recovery window.
