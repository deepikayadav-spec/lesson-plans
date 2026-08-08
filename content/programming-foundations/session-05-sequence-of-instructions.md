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

Type this live, exactly as written, and run it:

```python
print(age)
age = 10
```

Let the `NameError` land.

> *"Everything in there is correct. Spelling's right, syntax is right, the variable exists — two lines down. So why did it fail?"*

Take a couple of guesses, then:

> *"Because Python doesn't read your program. It *executes* it, one line at a time, top to bottom, and it has no idea what's coming next. On line one, `age` genuinely does not exist yet. Today is about order — and order turns out to be most of programming."*

Tie back to **Q6** — *"You all knew a variable's value can change. Today you'll find out that when it changes is the whole game."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred from RM structure, confirm against deck -->
Covers: Program as a sequence → Defining a variable → Printing a variable's value → `print(age)` vs `print("age")` → Order of Instructions → the NameError → Spacing and IndentationError.

**Beats to emphasise**

- **`print(age)` vs `print("age")`.** The single most confusable pair in the session. Run both, back to back, every time it comes up. Quotes mean *the literal word*; no quotes means *what's in the box*.
- **Line-by-line execution.** Say it as a rule and write it on the board: *Python does one line, finishes it, then looks at the next.*
- **IndentationError:** a leading space breaks the line. Show it live — students hit this constantly and don't recognise it.

**Checkpoint (at 22 min)** — cold-call two students:
> *"`name = "Alice"`. What does `print(name)` show, and what does `print("name")` show?"*
> **Answer:** `Alice` and `name`.

---

## ⚡ Activity 1 — Human Compiler (22–27 min)

**Format:** Human Compiler · **Exposes:** that students evaluate a program as a whole rather than one line at a time.

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

<!-- placement: inferred from RM structure, confirm against deck -->
Covers: Variable Assignment and reassignment examples → Expressions → BODMAS → worked evaluations.

**Beats to emphasise**

- **`a = a + 1`.** The line that breaks maths brains — it's false as an equation and correct as an instruction. Read it aloud as *"take what's in a, add 1, put the result back in a."*
- **BODMAS is not new.** Students know this from school. Frame it as *"Python follows the rule you already know"* — that's reassuring, and it's true.
- Run `print(10 / 2 + 3)` and `print(10 / (2 + 3))` back to back. Same characters, brackets moved, different answers.

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

- **Two big ideas share this session:** execution order (hook, Block A, Activities 1 & 3) and expression evaluation (Block B, Activity 2, Quiz Q5). If you're short on time, protect execution order — BODMAS is revision from school, order is genuinely new.
- **Warm-up Q3 is a gate.** If the room can't identify `"42"` as a string, `print("age")` vs `print(age)` will not land today. Spend the 30 seconds.
- **Activity 2 is an investment in Session 13.** Variable-state tracing is exactly the skill loops require. If it lands well here, say so and name it — *"remember this table, you'll need it."*
- **Pacing risk:** the `a = a + 1` discussion in Block B expands to fill any space you give it. Cap at 3 minutes; Activity 2 reinforces it anyway.
- **Quiz question `9ae028e4` in Quiz C is worth avoiding** — its marked answer is `3` where Python actually produces `3.0`. Not used above; don't substitute it in.
- **104 MCQ practice questions here** — the largest pool so far. No shortage for the practice block.
