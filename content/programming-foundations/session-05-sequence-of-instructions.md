# Session 5 — Sequence of Instructions

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Sequence of Instructions · **Prerequisite** Session 4
**Session type** Concept lecture · **Format** 50-min recalibrated, 2 ALS activities, Classroom Quiz mandatory (never cut, runs last)

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

## Classroom Settling (0–3 min) · Buffer — not instructional

Projector on, deck loaded, students seated before the clock starts on anything below. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** state the MCQ Practice completion number since last session. Target is 80%.

5 questions on **Session 4**. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `=` do in `count = 5`?
`A` Checks whether count equals 5 · `B` Assigns 5 to count · `C` Adds 5 to count · `D` Creates a variable called 5
→ **B.** *Targets:* Assignment operator. *Misconception:* A is the maths carryover. *If >40% wrong:* re-say it once — *"right side first, then into the box on the left."*

**Q2.** What is the data type of `"42"`?
`A` Integer · `B` Float · `C` String · `D` Boolean
→ **C.** *Targets:* Quotes decide the type. *This is a gate* — today's `print("age")` vs `print(age)` distinction will fail without it. *If >40% wrong:* stop and fix before continuing.

**Q3.** What does `print(a + b)` output when `a = "10"` and `b = "3"`?
`A` `13` · `B` `103` · `C` TypeError · `D` `10 3`
→ **B.** *Targets:* String joining vs addition, from last session.

**Q4.** `age = 10` then `age = 20`. What's in `age`?
`A` `10` · `B` `20` · `C` `1020` · `D` Error — you can't reassign
→ **B.** *Targets:* Values can change. **This is today's foundation** — note the number carefully.

**Q5.** What's the data type of `7.0`?
`A` Integer · `B` Float · `C` String · `D` Boolean
→ **B.** *Targets:* Decimal point makes a float. Ties into today's BODMAS answers, which always come out as floats.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

> **Don't run the `print(age)` / `age = 10` NameError here.** It is deck slide 7, coming up soon, complete with the explanation. Save it.

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

Return to it in **ALS Activity 2**, where the trace table makes it obvious.

Tie back to **Q4** — *"You all knew a variable's value can change. Today you find out that **when** it changes is the whole game."*

---

## Slide Block A (10–18 min) — DELIVER SLIDES AS-IS

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

- **Slide 2 is a recap your warm-up poll already did.** Ten seconds.
- **Slide 7 is the NameError.** This is where the hook's "instructions, not equations" idea gets its formal statement. Read both bullet points aloud — the deck words them well.
- **Slides 9–12 animate the box.** Let the animation run and ask *"what's in the box now?"* before each click rather than narrating it. The visual is doing your work.
- **Slide 12 (`a = a + 1`) is the line that breaks maths brains.** It's false as an equation and correct as an instruction. Read it aloud as *"take what's in a, add 1, put the result back in a."*

> ⚠️ **The deck never shows `print(age)` vs `print("age")`.** That distinction is in the reading material and it's the subject of **Quiz Q2**. Add it verbally here — two lines, typed live:
> ```python
> age = 25
> print("age")   # age
> print(age)     # 25
> ```

**Checkpoint (at 18 min)** — 10 s silent think, then cold-call two students:
> *"`name = "Alice"`. What does `print(name)` show, and what does `print("name")` show?"*
> **Answer:** `Alice` and `name`.

---

## ⚡ ALS Activity 1 — Chain Trace: Human Compiler (18–23 min)

**ALS format:** Round-Robin Chain Trace — a different student takes each line, and the value in the box only makes sense in light of what the last student said. Chosen right after Slide A's box animation because the skill is running the exact same trace unaided immediately after watching it done — recognition versus production.

> **This is deck slide 9, handed back to the students.** Say so: *"You watched Python do that. Now you do it, without the animation."*

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

## Slide Block B (23–31 min) — DELIVER SLIDES AS-IS

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

- **Do not tell students BODMAS is old news.** The deck deliberately produces **three different answers — 22, 100, 70 — to the same expression** *before* naming the rule. Take a vote on each approach before revealing slide 17.
- **Slide 18 is Quiz Q5 verbatim** (`print(10 / 2 + 3)` → `8.0`). If the room follows this slide, they will get it right.
- **Slides 18 and 19 are the bracket pair.** Same characters, brackets moved, `8.0` versus `2.0`.
- **Flag the `.0` in both answers** — division always returns a decimal.

**Silent-fail check (30 s, before the checkpoint):** put this on screen — *"No error here. What does it actually print?"*
```python
name = "Ravi"
print("name")
```
10 s silent guess, then reveal: prints the word `name`, not `Ravi`. *"That's the dangerous kind of bug — it runs, it just runs wrong. Read your output, not just your error messages."*

**Checkpoint (at 31 min)** — show hands:
> *"`a = 5`, then `a = a + 3`. What's in `a`?"*
> **Answer:** `8`. Right side runs first using the old value, then the result goes back into the box.

---

## ⚡ ALS Activity 2 — Guided Individual Tracking: Trace the Table (31–38 min)

**ALS format:** Guided Individual Tracking (structured notes, no pairing) — everyone builds their own trace table in real time as you read lines aloud. Chosen instead of a pair or cold-call format because the skill is holding state silently in your own head across lines, which is exactly what loops will demand a few sessions from now — it has to be practiced solo.

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
> *"Line four used the new `a`, not the old one, because line three already happened. You just did what Python does. When we get to loops, this table is the only tool that will save you."* **Now resolve the hook's four-line puzzle** the same way — both `a` and `b` end at 2.

**Cut rule:** Stop after line 4 and take the answers verbally without the print lines.

---

## Classroom Quiz (38–45 min) · ALS: Individual Answer → Reveal

> 🔒 **Mandatory block — do not cut, do not shorten, do not skip under time pressure.** Runs last, right before the Exit Ticket. Protect these 7 minutes by using the cut rules everywhere else first.

Every question below is run ALS-style: **individual silent answer first, then explanation.**

5 MCQs from the platform pools. ~85 s each.

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
> **This is the session's core question.** If >40% miss it, that's your signal to reopen it at the start of Session 6.

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
> ⚠️ **The deck has no slide on indentation or spacing.** This comes from the reading material only. If you have a spare 20 seconds anywhere above, demonstrate it live: `a = 10` then a line with a leading space → `IndentationError`.
> **If they pick "poor practice":** they're carrying over from languages where whitespace is cosmetic. In Python it's grammar.

**Q5** — `5b1004bc-2bd8-4336-84eb-a66893515505` *(Quiz C · APPLYING)*
What will be the output of `print(10 / 2 + 3)`?
- `13.0`
- `5.0`
- `6.5`
- ✅ **`8.0`**

> *Explanation (platform):* According to the BODMAS rule, division is performed before addition. Thus, 10 divided by 2 equals 5, and adding 3 results in 8.
> **If they pick `13.0`:** they evaluated left to right ignoring precedence — Slide Block B is exactly this fix.
> **Worth naming:** the answer is `8.0`, not `8`, because division always produces a float.

---

## Exit Ticket + Quiz Push (45–48 min)

**Exit ticket** (~30 s) — before anyone leaves:

> `x = 4`, then `x = x + 6`. What is in `x`? And what does `print("x")` display?
> **Answers:** `10`, and `x`.

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Open MCQ Practice. Everyone, this room, right now — attempt the first 3 questions before you leave your seat. 104 questions in this pool — plenty of runway."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 6's warm-up."*

**Remaining homework**

| Task | Unit |
|---|---|
| Coding Practice — *Product of 37, 61 and 391*, *Divide 33968 by 176* | `1cab5e23-4577-4878-b5ea-7178c46658fe` |
| MCQ Practice — 104 questions *(started in class above — finish the rest)* | `d16f93a5-761d-41cb-a566-96ec5d65ce70` |
| RM — Sequence of Instructions | `7f36724e-216f-4adc-8a37-d2c56dbec018` |

> Flag for the division problem: *"Your answer will come out with a decimal point. That's not a mistake — division always does that in Python."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `print("age")` shows the value | Both forms look similar | Running both lines back to back, every single time |
| Python reads the whole program first | Reading habits from prose | The hook — `print(age)` before `age = 10` |
| `a = a + 1` is impossible | It's false as an equation | Reading it as an instruction: right side first, then into the box |
| Indentation is cosmetic | True in most other languages | Naming the IndentationError explicitly at Quiz Q4 |
| All errors are "syntax errors" | Only category they know | Quiz Q3 — naming NameError vs IndentationError separately |
| No error means correct | Errors are their only feedback | The silent-fail check in Slide Block B — runs fine, prints the wrong thing |

---

## Instructor Notes

- ✅ **Verified against the real deck** (*"Copy of 1.3 Sequence of Instructions"*, ~20 slides). Slide Blocks A and B list the actual slides in order.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two big ideas share this session:** execution order (hook, Block A, ALS Activity 1) and expression evaluation (Block B, ALS Activity 2, Quiz Q5). Both are well supported by the deck — don't cut either.
- **Two ALS activities, both new formats:** Activity 1 is Round-Robin Chain Trace, Activity 2 is Guided Individual Tracking (silent, solo, no pairing — deliberately different since the skill itself is solo state-tracking). The original third activity (Spot the Bug) is folded into a 30-second silent-fail check inside Slide Block B.
- **The Classroom Quiz runs last, right before the Exit Ticket** — never cut, never shortened.
- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair.** Target is 80% platform MCQ attempt rate, currently ~33%.
- ⚠️ **Two things the quiz tests that the deck never shows:** `print("age")` vs `print(age)` (Quiz Q2) and indentation errors (Quiz Q4). Both are in the reading material only. **Worth raising with the content team.**
- **The deck's box animation (slides 9–12) is the same mental model as ALS Activity 2's trace table.** Use the deck's vocabulary — "what's in the box" — in both.
- **The hook's four-line puzzle resolves in ALS Activity 2.** Come back to it explicitly; students remember being wrong and want the answer.
- **Warm-up Q2 is a gate.** If the room can't identify `"42"` as a string, `print("age")` vs `print(age)` will not land today.
- **ALS Activity 2 is an investment in Session 13.** Variable-state tracing is exactly the skill loops require. If it lands well here, say so and name it.
- **Quiz question `9ae028e4` in Quiz C is worth avoiding** — its marked answer is `3` where Python actually produces `3.0`. Not used above; don't substitute it in.
- **104 MCQ practice questions here** — the largest pool so far. No shortage for the Quiz Push.
