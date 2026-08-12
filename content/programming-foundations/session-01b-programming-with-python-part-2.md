# Session 1b — Programming with Python (Part 2 of 2)

**Duration** 33 min · **Topic** Introduction to Python — print(), Mistakes & First Code · **Prerequisite** Session 1a — Programming with Python, Part 1 (software/code/syntax vocabulary) · **Session type** Concept lecture

<!-- Split note: continues session-01 (original 60 min) right after the Classroom Quiz. This part is where students first touch the editor — print() mechanics, the four classic mistakes, and live-coding predictions on quotes-vs-arithmetic. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Programming with Python | `837f23cb-d3be-4f96-877f-b76f7defe3e2` |
| RM — Programming with Python | `e57497b0-cccd-4ec6-bd44-5c791468d4f0` |
| RM — Python Setup & Coding in VS Code | `292ce498-2b51-44b2-bc2c-65666c09090c` |
| RM — Algorithms, Flowcharts, and Pseudocode | `7516496f-23c2-4460-9691-b70219d4dc8b` |
| Classroom Quiz A (21 q) | `9567f314-fd85-4ef2-a445-6d9907337545` |
| Classroom Quiz B (59 q) | `d303e3b9-9b7a-457b-8357-a74987ba0dcb` |
| MCQ Practice (56 q) | `3c0cf49d-4c57-4468-83ca-63cb7c63b1dd` |
| Coding Practice (2 q) | `81959e79-ceeb-448c-af0e-7e0e7f5447f0` |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Write and run a `print()` statement that displays a text message. *(APPLYING)*
2. Predict the output of `print()` with and without quotes, and perform arithmetic inside `print()`. *(APPLYING)*
3. Identify the four common `print()` errors — misspelling, capital `P`, missing quotes, missing parenthesis — and correct them. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 1a (0–5 min)

Say: *"Four quick ones on the vocabulary from Part 1, then we go straight to code."*

**Q1.** What is code?
`A` A physical computer part · `B` A set of instructions you write · `C` A type of error message · `D` A design tool
→ *Read:* B.

**Q2.** What is syntax?
`A` The meaning of a program · `B` The rules those instructions must follow · `C` A programming language's name · `D` A type of software
→ *Read:* B.

**Q3.** In Part 1's hook, both the Java and Python snippets did the same thing. What was it?
`A` Add two numbers · `B` Print "Hello World" · `C` Open a file · `D` Ask for input
→ *Read:* B.

**Q4.** Is Python case-sensitive?
`A` Yes · `B` No · `C` Only for variable names · `D` Only in some versions
→ *Read:* A — from the Classroom Quiz. This matters in about five minutes.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"Vocabulary's done. Editor open — you're about to write your first real line of Python, and then break it on purpose so you know what the error messages actually look like."*

Have the editor already open with a blank file before this part starts — setting it up live burns minutes you don't have.

---

## Slide Block B (7–17 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred from RM structure, confirm against deck -->
Covers: Hello World program → Possible Mistakes → Printing Without Quotes → Calculations with Python (`+`, `-`, `*`, `/`).

**Beats to emphasise**

- Run every snippet live as it appears. Do not describe output — show it.
- On **Division**: flag that `print(4/2)` gives `2.0`, not `2`. Say "remember this, it comes back in Type Conversions." Don't explain floats yet.
- The **Possible Mistakes** slides set up Activity 2 — deliver them, but don't over-explain. Let the activity do the work.

**Checkpoint (at 17 min)** — show hands:
> *"`print(5 / 2)` — who says `2`? Who says `2.5`?"*
> **Answer:** `2.5`. Python's `/` always gives a decimal result.

---

## ⚡ Activity 2 — Spot the Bug (17–23 min)

**Format:** Spot the Bug · **Exposes:** that students read code for meaning instead of for exact characters. Every snippet is taken verbatim from the RM's *Possible Mistakes* section — nothing new.

**Setup line (say this):**
> *"Four broken lines. Each one is a real mistake I have seen students make in week one. Find the error AND tell me what Python will say back to you. First correct **explanation** wins — not the first shout."*

Put all four on screen at once:

```python
prnt("Hello World!")        # 1
Print("Hello World!")       # 2
print(Hello World!)         # 3
print("Hello World!"        # 4
```

**What students do:** 60 seconds silent, then hands up. Take one student per snippet.

**Answers**

| # | Error | What Python says |
|---|---|---|
| 1 | `print` misspelled as `prnt` | `NameError` — Python has no function by that name |
| 2 | Capital `P` | `NameError` — Python is case-sensitive, `Print` ≠ `print` |
| 3 | Missing quotes | `SyntaxError` — without quotes Python reads `Hello World!` as code, not text |
| 4 | Missing closing parenthesis | `SyntaxError` — Python is still waiting for you to finish the line |

**How it surfaces:** After each answer, type the broken line live and run it so the class sees the real error message. This is the point of the activity — students must learn error messages are readable, not scary.

**Debrief line:**
> *"Three of these four are just typing. That's the job. You will not be stuck because you can't think — you'll be stuck because of a capital letter. Read the error message, it tells you which line."*

**Cut rule:** If running late, do snippets 2 and 3 only — they carry case-sensitivity and the quotes rule, which are the two that recur all course.

---

## ⚡ Activity 3 — Live Coding: Quotes or No Quotes (23–30 min)

**Format:** Live Coding · **Exposes:** the quotes-vs-arithmetic misconception flagged in Part 1's poll Q5 and quiz Q5.

**Setup line (say this):**
> *"Editor is open, I'm typing, you're predicting. Before I hit run, everyone commits to an answer out loud. If you're wrong, that's the useful part."*

Type and run these **one at a time**, taking a prediction before each:

```python
print("Hello World")     # → Hello World
print(2 + 5)             # → 7
print("2 + 5")           # → 2 + 5
print(5 - 2)             # → 3
print(5 * 0.5)           # → 2.5
print(10 / 5)            # → 2.0
```

**The deliberate bug** — after the six above, type this and run it:

```python
Print("I can code")
```

Let the `NameError` appear. Ask: *"Who can fix it without me touching the keyboard?"* Take the instruction from a student and type exactly what they say.

**Debrief line:**
> *"Quotes mean 'print these exact characters.' No quotes means 'work it out, then print the answer.' That one rule explains half the confusion in your first week."*

**Cut rule:** Drop lines 4 and 5 (`5 - 2`, `5 * 0.5`). Keep the `"2 + 5"` vs `2 + 5` pair and keep the deliberate bug — those are the whole point.

---

## Exit Ticket + Homework (30–33 min)

**Exit ticket** — on paper or in chat before anyone leaves:

> Write the one line of Python that prints your own name, and next to it write what `print(3 * 4)` outputs.
> **Answers:** `print("Your Name")` (quotes required) and `12`.

Scan the responses on the way out. Missing quotes is the signal to open Session 2 with a quick recap.

**Homework**

| Task | Unit |
|---|---|
| Coding Practice — *Hello World*, *Three Hashes* | `81959e79-ceeb-448c-af0e-7e0e7f5447f0` |
| MCQ Practice — 56 questions | `3c0cf49d-4c57-4468-83ca-63cb7c63b1dd` |
| RM — Programming with Python | `e57497b0-cccd-4ec6-bd44-5c791468d4f0` |
| **RM — Python Setup & Coding in VS Code (compulsory if Part 1's poll Q3 was weak)** | `292ce498-2b51-44b2-bc2c-65666c09090c` |
| RM — Algorithms, Flowcharts, and Pseudocode | `7516496f-23c2-4460-9691-b70219d4dc8b` |

Tell them: *"Next session is a walkthrough of these exact coding problems. Attempt them first — a walkthrough of something you haven't tried is a waste of your hour."*

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `print("2 + 5")` outputs `7` | They read for meaning; quotes look decorative | Running both lines back-to-back in Activity 3 |
| `print(10 / 5)` outputs `2` | Whole-number division from school maths | Running it; flag that `2.0` returns in Type Conversions |
| Error messages mean "you failed" | School conditioning | Deliberately breaking your own code in Activity 3 and reading the message aloud calmly |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz.** This is the part where students first touch the editor.
- **The 33 minutes here are tight with two coding activities.** If you overrun, cut activity content per the cut rules. Do not cut slide content.
- **Have the editor already open** with a blank file before this part starts — setting up VS Code live burns minutes you don't have.
- The two RMs on *Python Setup* and *Algorithms, Flowcharts, Pseudocode* are attached to this session but are **not** covered in the lecture. They are homework only. Say this explicitly or students will expect them in class.
