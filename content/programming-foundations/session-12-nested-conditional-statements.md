# Session 12 — Nested Conditional Statements

**Duration** 60 min · **Topic** Conditional Statements · **Prerequisite** Session 11
**Session type** Concept lecture

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Nested Conditional Statements | `595fd9ac-95a9-4e1b-91cb-ae0d66006e30` |
| RM — Nested Conditional Statements | `5bf28868-119e-4d0b-beb2-f3eb5a2f29f4` |
| Classroom Quiz A (30 q — nesting) | `72145a83-fe6b-4d15-9dce-aa4b938ba390` |
| Classroom Quiz B (31 q — `elif`) | `f32e2390-1c97-4cdf-ba9c-fade1cc0159f` |
| MCQ Practice (93 q) | `2932ccef-5438-4cf3-b05b-677c8fcce424` |
| Coding Practice (12 q) | `d2c22172-d19f-4eb4-a7b1-198d2a2faae3` |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Write an `if` inside another `if` with correct indentation levels. *(APPLYING)*
2. Determine which block a line belongs to by reading its indentation. *(ANALYZING)*
3. Use `elif` to check several conditions in sequence. *(APPLYING)*
4. State that only the first true branch in an `if`/`elif`/`else` chain runs. *(UNDERSTANDING)*
5. Explain why `elif` cannot appear after `else`. *(UNDERSTANDING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 11**. Newly authored. ~45 s each, project the distribution, never name individuals.

**Q1.** What does an `if` statement need at the end of its condition line?
`A` A semicolon · `B` A colon · `C` Nothing · `D` Brackets
→ **B.** *Targets:* Colon.

**Q2.** `if True:` followed by an un-indented `print("Hi")` gives what?
`A` Prints `Hi` · `B` IndentationError · `C` SyntaxError · `D` Nothing
→ **B.** *Targets:* Indentation defines the block.

**Q3.** In an if-else, how many blocks run?
`A` Both · `B` Exactly one · `C` Neither · `D` Depends
→ **B.** *Targets:* Exactly one branch.

**Q4.** `marks = 40`. What does `if marks >= 40:` do?
`A` Runs the if block · `B` Runs the else block · `C` Error · `D` Nothing
→ **A.** *Targets:* `>=` includes the boundary. *Misconception:* B means the boundary case from last session didn't stick.

**Q5.** Can code sit between an `if` block and its `else`?
`A` Yes · `B` No — SyntaxError · `C` Only comments · `D` Only prints
→ **B.** *Targets:* `else` must immediately follow.

**Q6.** Which are valid? *(MSQ — select all)*
`A` `if x > 5:` · `B` `if x > 5` · `C` `else:` · `D` `else x < 5:`
→ **A and C.** *Targets:* Colons, and `else` takes no condition.

**Q7.** What decides whether a line is inside an `if` block?
`A` Its position in the file · `B` Its indentation · `C` The colon · `D` The condition
→ **B.** *Targets:* Indentation. **Today's whole session** — nesting is just indentation at two levels. Note the number.

---

## Hook (7–10 min)

> *"Last session your programs could answer one question. But some decisions need a second question — and the second one only makes sense if the first was yes."*

Write on the board:

```
Did the team win more than 8 matches?
    ...and did they also score more than 20 goals?
```

> *"You don't ask the second question unless the first one was true. That's a nested condition."*

Type and run with `10` then `22`:

```python
matches_won = int(input())
goals = int(input())
if matches_won > 8:
    if goals > 20:
        print("Hurray")
    print("Winner")
```

Then run again with `10` and `18` → only `Winner`.
Then `5` and `30` → nothing at all.

> *"Three different outputs from the same program. Look at the indentation — it's the only thing telling Python which question sits inside which."*

Tie back to **Q7** — *"You said indentation decides what's inside a block. Today that goes two levels deep, and it's the entire mechanism."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

**Verified against the deck** (*"Copy of 4.3 Nested Conditional Statements"*). Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1–3 | Welcome · Recap | |
| 4 | **Agenda** | Nested Conditions *(Indentation)* → Else If Statement *(if-elif-else)* |
| 5 | **Nested Conditions** — the structure diagram | `if condition A:` → Block 1, `if condition B:` → Block 2, Block 3, then Block 4 outside. **Each block ticked or crossed as the conditions resolve**, with Block 4 labelled *"Will always execute"* |
| 6+ | **Nested Conditions** | Worked code examples |
| 7+ | **Possible Mistakes** | `is_a_greatest` / `is_b_greatest` three-number example → **`NameError: name 'is_b_greatest' is not defined`**, with the offending block highlighted in red |

**Beats to emphasise**

- **Slide 5 is a better teaching device than any code.** It's an abstract diagram with dashed boxes showing which block belongs to which condition, and green ticks / red crosses showing what runs. **Use its vocabulary — Block 1, Block 2, Block 3, Block 4 — then map your code onto it.** Students who can read this diagram can read any nesting.
- **"Block 4 will always execute"** is called out explicitly on the slide. That is the `print("Winner")` idea from the reading material, stated more clearly. Point at it.
- **Slide 7's `NameError` is subtle and worth real time.** `is_b_greatest` is defined *inside* the `else` block, then used by an `if` at the outer level — so when the `else` doesn't run, the variable never exists. This combines Session 5's NameError with today's indentation. It is the best slide in the deck for showing that indentation has consequences beyond syntax.

**Checkpoint (at 22 min)** — cold-call two students, using the slide's own labels:
> *"On the diagram — if condition A is True and condition B is False, which blocks run?"*
> **Answer:** Block 1, Block 3 and Block 4. Block 2 is skipped.

---

## ⚡ Activity 1 — Human Compiler (22–27 min)

### What this activity is

Students **become** the Python interpreter. You point at one line at a time; the student you pick says whether that line runs and why — never the whole program at once. Nobody is allowed to jump ahead or describe what the program "is for".

### Why it's here

Nested conditions are read by eye and guessed at. Forcing a line-by-line walk exposes exactly which students are tracking indentation levels and which are pattern-matching.

### Before class

Have the program on screen with visible indentation. If your editor shows indent guides, turn them on.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, state the input values | Look |
| 0:30–3:30 | Point at each line, one student each | Say runs / skipped, and why |
| 3:30–4:30 | Re-run with the second input set | Same |
| 4:30–5:00 | Debrief | Listen |

### Say this

> *"You are Python. I point at a line, you tell me two things: does it run, and why. Not what the program is for. One line."*

### The program

State the values before you start: **`matches_won = 10`, `goals = 18`.**

```python
matches_won = 10
goals = 18
if matches_won > 8:
    if goals > 20:
        print("Hurray")
    print("Winner")
print("Done")
```

### Line by line

| Line | Runs? | Why |
|---|---|---|
| `if matches_won > 8:` | — | `10 > 8` is True, so enter the block |
| `if goals > 20:` | — | `18 > 20` is False, so **skip its block** |
| `print("Hurray")` | **No** | Inside the false inner block |
| `print("Winner")` | **Yes** | Level 4 — inside the outer block only |
| `print("Done")` | **Yes** | Level 0 — outside everything |

**Output:** `Winner` then `Done`.

### Second pass

Change to **`matches_won = 5`** and walk it again. Now the outer condition is False, so lines 2–4 are all skipped and only `Done` prints. Ask: *"How many lines did Python just skip in one go?"* — three, because they were all inside one false block.

### When it goes wrong

| If… | Do this |
|---|---|
| Student answers for the whole program | *"Too fast — this line only. Does it run?"* The staging is the activity. |
| Nobody sees why `Winner` runs | Point at the left edge. *"Count the spaces. Which block is it in?"* |
| Room finds it easy | Ask what would change if `print("Winner")` were indented to level 8. (It'd only print with `Hurray`.) |
| Someone argues about the second pass | Run it. Let the terminal settle it. |

**Common instructor mistake:** narrating the trace yourself while pointing. Students must supply each answer or it's a demo.

**Cut rule:** First pass only.

---

## Classroom Quiz (27–34 min)

5 MCQs from the platform pools — two on nesting, three on `elif`. ~80 s each.

**Q1** — `04cc638e-9810-4985-8ee6-1246569c31c6` *(Quiz A · APPLYING)*
What will be the output of:
```python
matches_won = 9
goals = 21

if matches_won > 8:
    if goals > 20:
        print("Hurray")
    print("Winner")
```
- ✅ **`Hurray` then `Winner`**
- `Winner`
- No output
- `Hurray`

> *Explanation:* **[authored — the platform record has an empty explanation field]** `9 > 8` is True, so the outer block runs. Inside it, `21 > 20` is also True, so `Hurray` prints. `print("Winner")` sits at the outer level, so it runs too.

**Q2** — `d15e25f4-7ab5-4a2c-b328-23b8b2653761` *(Quiz A · APPLYING)*
How can the error in this snippet be fixed?
```python
matches_won = 10
goals = 18

if matches_won > 8:
if goals > 20:
        print("Hurray")
    print("Winner")
```
- Change the print statement to uppercase
- There is no need to fix anything
- Remove the nested if statement
- ✅ **Adding four space indentation to `if goals > 20`**

> *Explanation:* **[authored — the platform record has an empty explanation field]** The inner `if` is at the same indentation level as the outer one, so Python sees the outer `if` block as empty and raises an IndentationError. Indenting the inner `if` by four spaces puts it inside the outer block.

**Q3** — `e88f6d5e-1db5-45b1-9042-4b9e923d65d0` *(Quiz B · REMEMBERING)*
What is the purpose of the `elif` statement?
- To define the final condition to be checked
- ✅ **To provide an alternative condition if the `if` condition is False**
- To terminate the conditional structure
- To execute regardless of the previous conditions

> *Explanation:* **[authored — the platform record has an empty explanation field]** `elif` lets you test another condition when the previous one was False. It sits between `if` and `else`, and you can have as many as you need.

**Q4** — `0d81fbb5-337a-4e05-8a04-f2b249f6804c` *(Quiz B · APPLYING)*
Which `elif` block will be executed?
```python
x = 5
if x > 10:
    print("Greater than 10")
elif x > 7:
    print("Greater than 7")
elif x > 3:
    print("Greater than 3")
else:
    print("3 or less")
```
- Both elif blocks
- `elif x > 7`
- No elif blocks will be executed
- ✅ **`elif x > 3`**

> *Explanation (platform):* `x` is 5. The first `if` condition `x > 10` is False, so it is skipped. The first `elif` condition `x > 7` is also False, so it is skipped. The second `elif` condition `x > 3` evaluates to True since 5 > 3.

**Q5** — `56d3452e-05be-40ef-8052-6bf25021f32f` *(Quiz B · ANALYZING)*
If multiple `elif` conditions evaluate to true, which block executes?
- All true `elif` blocks will be executed in sequence
- ✅ **Only the first true `elif` block will be executed**
- Only the last true `elif` block will be executed
- No `elif` blocks will be executed

> *Explanation (platform):* Python checks each condition in order from top to bottom. As soon as it finds the first condition that evaluates to True, it executes that block and skips all remaining ones.
> **This is the session's most important idea.** Order matters. A chain written in the wrong order produces silently wrong results — no error, just the wrong branch.

---

## Slide Block B (34–44 min) — DELIVER SLIDES AS-IS

**Verified against the deck.** Slides, in order:

| # | Slide | Content |
|---|---|---|
| 8 | **Elif Statement** — the structure diagram | `if condition A:` **False** → Block 1 ✗ · `elif condition B:` **False** → Block 2 ✗ · `else:` → Block 3 ✓. Same tick/cross visual language as slide 5 |
| 9+ | **Elif** | Worked code examples with `%` divisibility checks |
| last | Next Session | *Loops* |

**Beats to emphasise**

- **Slide 8 mirrors slide 5 deliberately** — same diagram grammar, same ticks and crosses. Say so: *"Same picture, different construct. Nesting goes inwards; elif goes downwards."* That contrast is the clearest way to explain when to use which.
- **Exactly one block runs in an `if`/`elif`/`else` chain.** The diagram shows it — two crosses and one tick.
- **`%` appears in the deck's elif examples** (divisible by 10, divisible by 5). Students met `%` only as a passing mention in Session 11's exit ticket. **Give it one sentence before slide 9:** `%` gives the remainder, `n % 10 == 0` means divisible by 10.

> ⚠️ **Two things the deck does not show, both tested:**
> - **`elif` ordering going wrong.** No slide demonstrates that a badly ordered chain silently gives the wrong answer. That's **Quiz Q5 and Activity 3's core idea** — the most important thing in the session. Type it live:
>   ```python
>   x = 100
>   if x > 3:      print("Above 3")     # this wins
>   elif x > 50:   print("Above 50")    # never checked
>   ```
> - **`elif` after `else` being a SyntaxError** (Activity 2 snippet 3). Run it.

**Checkpoint (at 44 min)** — show hands:
> *"Three `elif` conditions are all true. How many blocks run?"*
> **Answer:** One. The first.

---

## ⚡ Activity 2 — Spot the Bug (44–50 min)

### What this activity is

Broken snippets on screen. Students find each problem **and name the error** before offering a fix. One snippet doesn't crash at all — it runs and gives a wrong answer, and finding that one is the point.

### Why it's here

Every trap in this session is either an indentation slip or an ordering mistake. The ordering one produces no error, which makes it the most dangerous thing students learn today.

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

> *"Four snippets. Tell me what's wrong and what it's called. One of these does not crash. Ninety seconds, silent."*

### The snippets

```python
# 1
if True:
if False:
    print("Inner")
```
```python
# 2
x = 5
if x > 10:
    print("Big")
elif:
    print("Small")
```
```python
# 3
if False:
    print("If")
else:
    print("Else")
elif True:
    print("Elif")
```
```python
# 4
marks = 95
if marks > 30:
    print("Pass")
elif marks > 90:
    print("Distinction")
```

### Answers

| # | Diagnosis | Fix |
|---|---|---|
| 1 | `IndentationError` — inner `if` not indented, so the outer block is empty | Indent the inner `if` by four spaces |
| 2 | `SyntaxError` — `elif` has no condition | `elif x > 3:` or use `else:` |
| 3 | `SyntaxError` — `elif` cannot come after `else` | Move the `elif` above the `else` |
| 4 | **No error.** Prints `Pass`. A 95-mark student never gets `Distinction` | Put `marks > 90` first |

**Snippet 4 is the session.** Ask directly:

> *"A student scores 95 and the program says Pass. Nothing crashed. Nobody gets an error email. How long does that bug live in production?"*

### When it goes wrong

| If… | Do this |
|---|---|
| They spot 1–3 but not 4 | Expected. Run it, let `Pass` sit on screen in silence for a few seconds. |
| Someone says #4 is correct behaviour | Ask what result a 95-mark student should get. That settles it. |
| Nobody can fix #4 | Give it: swap the two conditions. Then ask *why* that works. |
| Running long | Do 1 and 4. Snippet 4 is non-negotiable. |

**Common instructor mistake:** rushing #4 because it's last. Reverse the order if you're short on time — it deserves the most.

---

## ⚡ Activity 3 — Predict the Output (50–57 min)

### What this activity is

You reveal a snippet, **the whole class commits to an answer out loud before you run it**, then you run it. The public commitment is the mechanism — a student who has said `Above 50` aloud remembers the correction; one who watched does not.

### Why it's here

`elif` ordering feels obvious until it isn't. This finds students who are reading the conditions rather than tracing the order.

### Before class

Snippets in a file, revealed one at a time.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:20 | Setup line | Listen |
| 0:20–5:30 | Reveal, take a chorus answer, **then** run | Predict aloud |
| 5:30–7:00 | Debrief | Listen |

### Say this

> *"Everyone answers out loud together before I hit run. Say it with confidence even if you're guessing — a wrong guess out loud is worth ten right answers in your head."*

### The snippets

```python
x = 100                     # 1
if x > 3:
    print("Above 3")
elif x > 50:
    print("Above 50")
```
```python
x = 100                     # 2
if x > 50:
    print("Above 50")
elif x > 3:
    print("Above 3")
```
```python
age = 25                    # 3
if age > 18:
    if age > 60:
        print("Senior")
    print("Adult")
```
```python
n = 7                       # 4
if n > 5:
    print("A")
if n > 3:
    print("B")
```

### Answers

| # | Output | Why |
|---|---|---|
| 1 | `Above 3` | First true condition wins — the `elif` is never checked |
| 2 | `Above 50` | Same values, order reversed, different answer |
| 3 | `Adult` | Inner condition false; `Adult` is at the outer level |
| 4 | `A` then `B` | **Two separate `if`s** — both run. Not a chain. |

**Snippets 1 and 2 are the pair that matters** — run them back to back and let the contrast land without commentary first.

**Snippet 4 is the sting.** Students expect one output because it looks like a chain. Two separate `if` statements are independent; only `elif` makes them exclusive.

### When it goes wrong

| If… | Do this |
|---|---|
| Room gets 1 and 2 instantly | Good. Spend the time on 4, which almost nobody gets. |
| Someone predicts one line for #4 | Very common. Run it, then ask what would make it exclusive. (Change the second `if` to `elif`.) |
| Nobody will call out together | Hands vote instead: *"Hands for A only. Hands for A and B."* |
| Running late | Snippets 1, 2 and 4. |

**Common instructor mistake:** running before the prediction. Once output is on screen it's a demo, not an activity.

**Cut rule:** Snippets 1, 2 and 4.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — before anyone leaves:

> `score = 95`. Write an `if`/`elif`/`else` chain that prints `Distinction` above 90, `Pass` above 40, and `Fail` otherwise — **in the correct order.**
> **Answer:** `if score > 90:` → `Distinction`, `elif score > 40:` → `Pass`, `else:` → `Fail`. Any chain with `> 40` first is wrong.

**Homework**

| Task | Unit |
|---|---|
| Coding Practice — 12 problems | `d2c22172-d19f-4eb4-a7b1-198d2a2faae3` |
| MCQ Practice — 93 questions | `2932ccef-5438-4cf3-b05b-677c8fcce424` |
| RM — Nested Conditional Statements | `5bf28868-119e-4d0b-beb2-f3eb5a2f29f4` |

> *"Two rules. Count your indentation — every nesting level is four more spaces. And put your most specific condition first, or your chain will quietly give the wrong answer."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| All true branches run | Reading it as a list of checks | Quiz Q5 and Activity 3 snippet 1 |
| `elif` order doesn't matter | The conditions look independent | Activity 3 snippets 1 and 2, back to back |
| Consecutive `if`s behave like `if`/`elif` | They look the same on the page | Activity 3 snippet 4 — both run |
| `elif` can go after `else` | `else` feels like a divider | Activity 2 snippet 3 — SyntaxError |
| Nesting needs new syntax | It looks like a new construct | Block A — it's the same `if`, indented further |
| A line inside an outer block is inside the inner one too | Indentation levels blur | Activity 1 — `print("Winner")` at level 4 |
| A wrong `elif` order will error | Errors are their feedback | Activity 2 snippet 4 — runs fine, wrong result |

---

## Instructor Notes

- ✅ **Verified against the real deck** (*"Copy of 4.3 Nested Conditional Statements"*). Slide Blocks A and B list the actual slides in order.
- **The deck's two structure diagrams (slides 5 and 8) are its strongest assets.** Both use the same tick/cross grammar, so nesting and `elif` can be contrasted picture-to-picture. Teach from the diagrams and map code onto them, rather than the reverse.
- **Slide 7's `NameError`** — a variable defined inside an `else` block and used outside it — is the deck's best argument that indentation has real consequences. Don't rush it.
- ⚠️ **The deck never shows a mis-ordered `elif` chain**, which is Quiz Q5 and the point of Activity 3. Live-typing script is in Slide Block B. **Worth raising with the content team** — it's the highest-value idea in the session and it's absent.
- **`%` shows up in the deck's elif examples** but has never been formally taught. One sentence before slide 9.
- **This session is two topics** — nesting (Block A, Activity 1) and `elif` (Block B, Activities 2–3). They solve the same problem, and `elif` is usually the better answer. Say that explicitly; students otherwise nest three levels deep in the homework.
- **Turn on indent guides in your editor** before this session. Nesting is invisible without them on a projector at the back of the room.
- **The single most valuable moment is Activity 3 snippets 1 and 2.** Same values, order swapped, different output, no error. If you cut anything, don't cut that pair.
- **Four questions in this session's quiz have empty `answer_explanation` fields on the platform** — `04cc638e`, `d15e25f4`, `e88f6d5e`, and Session 13's set has more. The explanations above are authored and labelled. **Running total across the first 15 sessions is now 10 empty explanations** — worth a systematic audit rather than a one-off fix.
- **Pacing risk:** the RM's three-way-largest example in Block A (`is_a_greatest` / `is_b_greatest`) is dense and `elif` supersedes it ten minutes later. Show it briefly, don't trace it fully.
- **Note the RM has a formatting bug** in that same example — one line uses a tab where the rest use spaces. If you copy code from the RM, retype the indentation rather than pasting.
- **Sessions 13–15 are loops.** Students who still can't count indentation levels will not cope. If Activity 1 goes badly, use the practice block for indentation drilling rather than the coding set.
