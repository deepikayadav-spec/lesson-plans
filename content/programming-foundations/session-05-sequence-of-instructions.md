# Session 5 — Sequence of Instructions

**Duration** 60 min · **Topic** Sequence of Instructions · **Prerequisite** Session 4
**Session type** Concept lecture

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Sequence of Instructions | `90eaf231-9992-4c58-9015-c9d5312bb2eb` |
| RM — Sequence of Instructions | `7f36724e-216f-4adc-8a37-d2c56dbec018` |
| Classroom Quiz A (49 q) | `dd19eb06-8e94-41d7-b622-f73c08773029` |
| Classroom Quiz C (34 q) | `37bfe668-eb85-4175-ab34-3a38698d57bd` |
| MCQ Practice (104 q) | `d16f93a5-761d-41cb-a566-96ec5d65ce70` |
| Coding Practice (2 q) | `1cab5e23-4577-4878-b5ea-7178c46658fe` |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State that a program is a sequence of instructions executed line by line, top to bottom. *(REMEMBERING)*
2. Explain why using a variable before assigning it raises a `NameError`. *(UNDERSTANDING)*
3. Print a variable's value rather than its name, and explain the difference. *(APPLYING)*
4. Trace variable values through a sequence of reassignments. *(ANALYZING)*
5. Evaluate expressions using BODMAS and predict Python's output. *(APPLYING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 4**. Newly authored. ~45 s each, project the distribution, never name individuals.

**Q1.** What is a variable?
`A` A value that never changes · `B` A container for storing a value · `C` A Python function · `D` A type of error
→ **B.** *Targets:* Variable definition.

**Q2.** What does `=` do in `count = 5`?
`A` Checks whether count equals 5 · `B` Assigns 5 to count · `C` Adds 5 to count · `D` Creates a variable called 5
→ **B.** *Targets:* Assignment operator. *Misconception:* A is the maths carryover. *If >40% wrong:* re-say it once — *"right side first, then into the box on the left."*

**Q3.** What is the data type of `"42"`?
`A` Integer · `B` Float · `C` String · `D` Boolean
→ **C.** *Targets:* Quotes decide the type. *Misconception:* A means Session 4's central idea hasn't landed. *If >40% wrong:* stop — today's `print("age")` vs `print(age)` distinction will fail without it.

**Q4.** What does `print(a + b)` output when `a = "10"` and `b = "3"`?
`A` `13` · `B` `103` · `C` TypeError · `D` `10 3`
→ **B.** *Targets:* String joining vs addition, from Activity 2 last session.

**Q5.** Which is a valid Boolean in Python? *(MSQ — select all)*
`A` `True` · `B` `"True"` · `C` `true` · `D` `False`
→ **A and D.** *Targets:* Booleans need a capital and no quotes. *Misconception:* selecting B or C is very common — worth 20 seconds.

**Q6.** `age = 10` then `age = 20`. What's in `age`?
`A` `10` · `B` `20` · `C` `1020` · `D` Error — you can't reassign
→ **B.** *Targets:* Values can change. **This is today's foundation** — note the number carefully.

**Q7.** What's the data type of `7.0`?
`A` Integer · `B` Float · `C` String · `D` Boolean
→ **B.** *Targets:* Decimal point makes a float.

---

## Hook (7–10 min)

> **Don't run the `print(age)` / `age = 10` NameError here.** It is deck slide 7, about eight minutes away, complete with the explanation. Save it.

Write these four lines on the board — no laptop, no slide:

```
a = 1
b = 2
a = b
b = a
```

> *"Four lines. When Python finishes, what's in `a` and what's in `b`? Thirty seconds, write it down."*

Most of the room says `a` is 2 and `b` is 1 — they read it as a swap, because that's what it looks like as a set of equations. The real answer is **both hold 2**: by the time line 4 runs, `a` is already 2, so `b` gets 2 back.

Don't resolve it yet. Take a show of hands on each answer, write the counts on the board, and say:

> *"Half this room is confident and wrong — including some of you who are good at maths. That's not a maths mistake. It's that these aren't equations, they're **instructions**, and they happen in an order. By the end of the hour you'll all get this right, and we'll come back to these four lines."*

Return to it in Activity 2, where the trace table makes it obvious.

Tie back to **Q6** — *"You all knew a variable's value can change. Today you find out that **when** it changes is the whole game."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

**Verified against the deck.** Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1 | Welcome | Skip |
| 2 | **Recap — Data Types** | String · Integer · Float · Boolean |
| 3–5 | **Agenda** (build) | Variables *(Printing and Assignment)* → Expressions |
| 6 | **Program — Sequence of Instructions** | "A program is a **sequence** of instructions to a computer" |
| 7 | **Common Mistakes — Order of Instructions** | `print(age)` then `age = 10` → **NameError**. Notes: "Python executes the code line-by-line" · "Variable `age` is not created by the time we tried to print" |
| 8 | **Variable** | "Values in the variables can be changed" — glass changing colour |
| 9 | **Variable Assignment** | `a = 1` · `print(a)` · `a = 2` · `print(a)` — **animated**, with a box labelled `a` whose contents change 1 → 2 |
| 10–12 | **Value in Variable** | Three builds with box visuals: `a = b` (both become 2) · `a = b + 1` (a=3, b=2) · `a = a + 1` |

**Beats to emphasise**

- **Slide 2 is a recap your warm-up poll already did.** Twenty seconds.
- **Slide 7 is the NameError.** This is where the hook's "instructions, not equations" idea gets its formal statement. Read both bullet points aloud — the deck words them well.
- **Slides 9–12 animate the box.** Let the animation run and ask *"what's in the box now?"* before each click rather than narrating it. The visual is doing your work.
- **Slide 12 (`a = a + 1`) is the line that breaks maths brains.** It's false as an equation and correct as an instruction. Read it aloud as *"take what's in a, add 1, put the result back in a."*

> ⚠️ **The deck never shows `print(age)` vs `print("age")`.** That distinction is in the reading material and it's the subject of **Quiz Q2**. Add it verbally here — two lines, typed live:
> ```python
> age = 25
> print("age")   # age
> print(age)     # 25
> ```

**Checkpoint (at 22 min)** — cold-call two students:
> *"`name = "Alice"`. What does `print(name)` show, and what does `print("name")` show?"*
> **Answer:** `Alice` and `name`.

---

## ⚡ Activity 1 — Human Compiler (22–27 min)

**Format:** Human Compiler · **Exposes:** that students evaluate a program as a whole rather than one line at a time.

> **This is deck slide 9, handed back to the students.** The deck just animated this exact program with a box visual. Say so: *"You watched Python do that. Now you do it, without the animation."* Doing it unaided immediately after seeing it done is the point — recognition is not the same as being able to.

**Setup line:**
> *"You're Python. I point at a line, you tell me what the machine does and what's in the box afterwards. Not what the program means — that one line only."*

Put this on screen and point at each line, different student each time:

```python
a = 1
print(a)
a = 2
print(a)
```

| Line | What Python does | `a` afterwards |
|---|---|---|
| 1 | Creates `a`, puts 1 in it | `1` |
| 2 | Shows `1` | `1` |
| 3 | Replaces the contents with 2 | `2` |
| 4 | Shows `2` | `2` |

**Output:** `1` then `2`.

**Press on line 3:** *"Where did the 1 go?"*
**Answer:** gone. Overwritten. A box holds one thing at a time.

**Debrief line:**
> *"Same variable, two different values, because time passed between them. The order of the lines is what decided the output."*

**Cut rule:** Run all four lines — it's already the minimum version.

---

## Classroom Quiz (27–34 min)

5 MCQs from the platform pools. ~80 s each including discussion.

**Q1** — `07f0848f-eba9-48c0-ad8d-bd4efbb53cda` *(Quiz A · REMEMBERING)*
What occurs when a value is assigned to a variable in Python for the first time?
- ✅ **A new variable is created and it is assigned the value.**
- The variable is declared without being assigned any value.
- You must declare the variable before you can assign a value to it.
- Python raises an error because variables cannot be created in this manner.

> *Explanation (platform):* In Python, when you assign a value to a variable for the first time, the variable is created and the value is assigned to it. There is no need for explicit declaration prior to assignment.
> **If they pick "must declare first":** they've heard about other languages. Confirm that's true elsewhere, not in Python.

**Q2** — `47255537-2d10-44c3-89f6-ee68df02c0ce` *(Quiz A · UNDERSTANDING)*
What will be the output of:
```python
age = 25
print("age")
print(age)
```
- `25` then `age`
- `25` then `25`
- ✅ **`age` then `25`**
- `age` then `age`

> *Explanation (platform):* The code snippet will first print the string "age" and then print the number 25, which is the value assigned to the variable age.
> **This is the session's core question.** If >40% miss it, stop and re-run both lines live before continuing.

**Q3** — `7bc1684d-a83c-4cfc-8db2-1bca13d1547e` *(Quiz A · APPLYING)*
What will be the output of:
```python
print(score)
score = 100
```
- ✅ **NameError**
- `score`
- `100`
- SyntaxError

> *Explanation (platform):* The variable 'score' is called before it is assigned any value, which leads to a NameError because the variable is not yet defined in the execution flow.
> **If they pick SyntaxError:** they're guessing the error type. The code is perfectly well-formed — nothing is misspelled. The problem is *when*, not *what*.

**Q4** — `da8f2048-83da-42a5-a0d5-d2a7b3a511f7` *(Quiz A · UNDERSTANDING)*
What is the result of incorrect indentation in a Python code block?
- The code will still execute correctly, but it will be slower.
- ✅ **The code will not execute and will result in a syntax error.**
- The indentation has no impact on the code execution.
- The code will execute correctly, but it will be considered poor practice.

> *Explanation (platform):* Incorrect indentation in Python leads to a syntax error because indentation is a part of the Python syntax used to define code blocks.
> ⚠️ **The deck has no slide on indentation or spacing** — it isn't even in the deck's agenda. This comes from the reading material only. **Demonstrate it before the quiz** or the room will miss this question:
> ```python
> a = 10 * 5
> b = 5 * 0.5
>  b = a + b        # leading space → IndentationError
> ```
> **If they pick "poor practice":** they're carrying over from languages where whitespace is cosmetic. In Python it's grammar.

**Q5** — `5b1004bc-2bd8-4336-84eb-a66893515505` *(Quiz C · APPLYING)*
What will be the output of `print(10 / 2 + 3)`?
- `13.0`
- `5.0`
- `6.5`
- ✅ **`8.0`**

> *Explanation (platform):* According to the BODMAS rule, division is performed before addition. Thus, 10 divided by 2 equals 5, and adding 3 results in 8.
> **If they pick `13.0`:** they evaluated left to right ignoring precedence — `10 / 5`. That's the BODMAS gap, and Slide Block B is about to address it.
> **Worth naming:** the answer is `8.0`, not `8`, because division always produces a float.

---

## Slide Block B (34–44 min) — DELIVER SLIDES AS-IS

**Verified against the deck.** This half is a single well-built argument — don't shortcut it.

| # | Slide | Content |
|---|---|---|
| 13 | **Order of Operations** | `5 * 2 + 3 * 4` — *"What are the different possible ways to evaluate this expression?"* |
| 14 | **Approach 1** | `(5*2) + (3*4)` → 10 + 12 → **22** |
| 15 | **Approach 2** | `5 * (2+3) * 4` → 5 * 5 * 4 → **100** |
| 16 | **Approach 3** | `5 * 2 + (3*4)` … → 5 * 14 → **70** |
| 17 | **BODMAS** | The six badges — B ( ) · O √ · D ÷ · M × · A + · S − — resolving the expression to 22 |
| 18 | **Order of Operations (BODMAS)** | `print(10 / 2 + 3)` → `8.0`, reduced step by step: `10/2 + 3` → `5.0 + 3` → `8.0` |
| 19 | **Order of Operations (BODMAS)** | `print(10 / (2 + 3))` → `2.0` |
| 20 | Tomorrow's Session | *Input and Output Basics* |

**Beats to emphasise**

- **Do not tell students BODMAS is old news.** The deck deliberately produces **three different answers — 22, 100, 70 — to the same expression** *before* naming the rule. That manufactured confusion is the whole point: it makes the rule feel necessary rather than remembered. Take a vote on each approach before revealing slide 17.
- **Slide 18 is Quiz Q5 verbatim** (`print(10 / 2 + 3)` → `8.0`). The deck even shows the reduction. If the room follows this slide, they will get Q5 right.
- **Slides 18 and 19 are the bracket pair.** Same characters, brackets moved, `8.0` versus `2.0`.
- **Flag the `.0` in both answers** — division always returns a decimal. It comes back in Session 8.

**Checkpoint (at 44 min)** — show hands:
> *"`a = 5`, then `a = a + 3`. What's in `a`?"*
> **Answer:** `8`. Right side runs first using the old value, then the result goes back into the box.

---

## ⚡ Activity 2 — Trace the Table (44–50 min)

**Format:** Trace the Table · **Exposes:** whether students can hold variable state in their head across lines — the skill that loops will demand shortly.

**Setup line:**
> *"Everyone draw two columns on paper: `a` and `b`. I read a line, you write what's in each box after that line. No laptops."*

Read one line at a time, pausing after each:

```python
a = 1
b = 2
a = b + 1
b = a + b
print(a)
print(b)
```

**The table students should end up with:**

| After line | `a` | `b` |
|---|---|---|
| `a = 1` | 1 | — |
| `b = 2` | 1 | 2 |
| `a = b + 1` | **3** | 2 |
| `b = a + b` | 3 | **5** |

**Output:** `3` then `5`.

**How it surfaces:** After line 3, ask three students what's in `a`. After line 4, ask what `b` is *and* whether `a` changed. It didn't — that's the point most rooms get wrong.

**Debrief line:**
> *"Line four used the new `a`, not the old one, because line three already happened. You just did what Python does. When we get to loops, this table is the only tool that will save you."*

**Cut rule:** Stop after line 4 and take the answers verbally without the print lines.

---

## ⚡ Activity 3 — Spot the Bug (50–57 min)

**Format:** Spot the Bug · **Exposes:** the three ordering and spacing failures from this session's RM, all of which students will hit tonight.

**Setup line:**
> *"Three broken programs. Find the error and tell me the error *name*, not just 'it's wrong'. Sixty seconds."*

```python
# 1
print(total)
total = 50
```

```python
# 2
a = 10 * 5
b = 5 * 0.5
 b = a + b
```

```python
# 3
name = "Ravi"
print("name")
```

**Answers**

| # | Error | Fix |
|---|---|---|
| 1 | `NameError` — used before it exists | Swap the two lines |
| 2 | `IndentationError` — leading space on line 3 | Delete the space |
| 3 | **No error** — it prints `name` instead of `Ravi` | Remove the quotes |

**Number 3 is the trap.** It runs perfectly and produces the wrong thing. Ask specifically: *"Which of these three would the computer let you get away with?"*

**Debrief line:**
> *"Two of those crashed and told you the line number. The third ran happily and gave you the wrong answer. The silent one is always the dangerous one — that's why you read your output, not just check for errors."*

**Cut rule:** Snippets 1 and 3. Number 3 is non-negotiable.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — before anyone leaves:

> `x = 4`, then `x = x + 6`. What is in `x`? And what does `print("x")` display?
> **Answers:** `10`, and `x`.

**Homework**

| Task | Unit |
|---|---|
| Coding Practice — *Product of 37, 61 and 391*, *Divide 33968 by 176* | `1cab5e23-4577-4878-b5ea-7178c46658fe` |
| MCQ Practice — 104 questions | `d16f93a5-761d-41cb-a566-96ec5d65ce70` |
| RM — Sequence of Instructions | `7f36724e-216f-4adc-8a37-d2c56dbec018` |

> Flag for the division problem: *"Your answer will come out with a decimal point. That's not a mistake — division always does that in Python."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `print("age")` shows the value | Both forms look similar | Running both lines back to back, every single time |
| Python reads the whole program first | Reading habits from prose | The hook — `print(age)` before `age = 10` |
| `a = a + 1` is impossible | It's false as an equation | Reading it as an instruction: right side first, then into the box |
| Indentation is cosmetic | True in most other languages | Running the leading-space example and naming the error |
| All errors are "syntax errors" | Only category they know | Quiz Q3 and Activity 3 — naming NameError vs IndentationError separately |
| No error means correct | Errors are their only feedback | Activity 3 snippet 3 — runs fine, prints the wrong thing |

---

## Instructor Notes

- ✅ **Verified against the real deck** (*"Copy of 1.3 Sequence of Instructions"*, ~20 slides). Slide Blocks A and B list the actual slides in order.
- **Two big ideas share this session:** execution order (hook, Block A, Activities 1 & 3) and expression evaluation (Block B, Activity 2, Quiz Q5). Both are well supported by the deck — don't cut either.
- ⚠️ **Two things the quiz tests that the deck never shows:** `print("age")` vs `print(age)` (Quiz Q2) and indentation errors (Quiz Q4). Both are in the reading material only. Scripted verbal fixes are in Slide Block A and at Quiz Q4. **Worth raising with the content team** — two of five quiz questions assess material absent from the deck.
- **The deck's box animation (slides 9–12) is the same mental model as Activity 2's trace table.** Use the deck's vocabulary — "what's in the box" — in both, so students see them as one idea rather than two.
- **The hook's four-line puzzle resolves in Activity 2.** Come back to it explicitly; students remember being wrong and want the answer.
- **Warm-up Q3 is a gate.** If the room can't identify `"42"` as a string, `print("age")` vs `print(age)` will not land today. Spend the 30 seconds.
- **Activity 2 is an investment in Session 13.** Variable-state tracing is exactly the skill loops require. If it lands well here, say so and name it — *"remember this table, you'll need it."*
- **Pacing risk:** the `a = a + 1` discussion in Block B expands to fill any space you give it. Cap at 3 minutes; Activity 2 reinforces it anyway.
- **Quiz question `9ae028e4` in Quiz C is worth avoiding** — its marked answer is `3` where Python actually produces `3.0`. Not used above; don't substitute it in.
- **104 MCQ practice questions here** — the largest pool so far. No shortage for the practice block.
