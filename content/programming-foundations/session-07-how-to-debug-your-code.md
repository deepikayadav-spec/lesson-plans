# Session 7 — How to Debug Your Code

**Duration** 60 min · **Topic** Type Conversions · **Prerequisite** Session 6
**Session type** Support session. No classroom quiz, no reading material, no MCQ pool.

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — How to debug your code? | `644bef74-d150-4442-ba7b-0e03acfe3544` |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Name the four errors they've met so far and what each one means. *(REMEMBERING)*
2. Read a Python error message and extract the line number and error type. *(APPLYING)*
3. Apply a fixed procedure when code breaks, instead of guessing. *(APPLYING)*
4. Distinguish an error that crashes from a bug that runs and produces the wrong answer. *(ANALYZING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 6**. Newly authored. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `print("ab" * 3)` output?
`A` `ab3` · `B` `ababab` · `C` `ab ab ab` · `D` TypeError
→ **B.** *Targets:* String repetition.

**Q2.** What does `print("ab" + 3)` output?
`A` `ab3` · `B` `ababab` · `C` TypeError · `D` `3ab`
→ **C.** *Targets:* Can't join string to number.

**Q3.** What data type does `input()` return?
`A` Whatever the user typed · `B` Always a string · `C` Integer if it looks like one · `D` Depends
→ **B.** *Targets:* The load-bearing fact from Session 6. *If >40% wrong:* demonstrate immediately — `age = input()` then `age + 1`.

**Q4.** `name = "Ravi"`. What is `name[0]`?
`A` `R` · `B` `a` · `C` `Ravi` · `D` `0`
→ **A.** *Targets:* Indexing from zero.

**Q5.** `name = "Ravi"`. Which raises an IndexError? *(MSQ — select all)*
`A` `name[0]` · `B` `name[3]` · `C` `name[4]` · `D` `name[10]`
→ **C and D.** *Targets:* Length 4 means the highest index is 3. *Misconception:* missing C is the classic off-by-one.

**Q6.** `print(len("Hello World"))` outputs what?
`A` `10` · `B` `11` · `C` `2` · `D` Error
→ **B.** *Targets:* The space counts as a character.

**Q7.** Your program runs with no error but prints the wrong answer. What is that called?
`A` A syntax error · `B` A bug · `C` Not a problem · `D` A crash
→ **B.** *Targets:* Bug vs error. **This is today's hook** — most students think "no error" means "correct". Note the number.

---

## Hook (7–10 min)

Put this on the projector and run it. Type `20` when it asks for input.

```python
age = input()
print("Next year you will be " + age + 1 + " years old")
```

It crashes. Let the traceback sit on screen — don't scroll past it.

> *"Hands up — who feels a small amount of panic looking at that red text?"*

Let the hands go up.

> *"Here's what nobody tells you. That message is not Python being angry with you. It is Python doing its best to help. It has told you the file, the line number, the type of error, and what it tried to do. It's the most useful text on your screen and most of you have been closing it without reading it."*

Point at the parts, one at a time: file, line number, error type, message.

> *"For the next fifty minutes we do nothing but read these properly."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred, deck not readable when this plan was written — see Instructor Notes -->
Covers: what debugging is, reading an error message, the common Python error types, a systematic approach.

**Beats to emphasise**

- **Read the error bottom-up.** The last line names the error type; the line above gives the location. That's the reading order.
- **The line number is a starting point, not a verdict.** Sometimes the real problem is the line above. Say this — it saves hours of confusion.
- **Errors are the good case.** A crash tells you where. A wrong answer tells you nothing.

Keep the tone matter-of-fact. Debugging is a normal, constant part of programming — not evidence of failure.

**Checkpoint (at 22 min)** — cold-call:
> *"In an error message, where do you look first, and what does it tell you?"*
> **Answer:** The last line — it names the error type. Then the line number just above it.

---

## ⚡ Activity 1 — Error Message Match (22–28 min)

### What this activity is

You show broken code snippets and a shuffled list of error messages. Students match each snippet to the error it produces. It's a matching exercise, not a fixing exercise — the goal is recognising error *types*, which is a prerequisite to fixing anything.

### Why it's here

Students currently have one mental category — "it broke." This session is the moment to split that into four distinct, named categories they've all already encountered.

### Before class

Write the two columns on the board, or have a slide ready with both. Snippets on the left, errors shuffled on the right — **do not present them in matching order.**

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, reveal both columns | Read |
| 0:30–2:00 | Wait, silent | Match individually on paper |
| 2:00–5:00 | Take each match from a different student, run it live | Answer, watch |
| 5:00–6:00 | Debrief | Listen |

### Say this

> *"Four broken programs, four error messages, shuffled. Match them. Two minutes, on your own, no talking. You have all seen every one of these before."*

### The matching set

| # | Snippet | | Error |
|---|---|---|---|
| 1 | `print(score)`<br>`score = 10` | A | `TypeError` |
| 2 | `print("age" + 5)` | B | `IndexError` |
| 3 | `name = "Zoe"`<br>`print(name[7])` | C | `IndentationError` |
| 4 | `a = 1`<br>` b = 2` | D | `NameError` |

### Answers

**1→D · 2→A · 3→B · 4→C**

| Error | What it actually means |
|---|---|
| `NameError` | You used a name Python has never seen — or hasn't seen *yet* |
| `TypeError` | You combined two kinds of things that don't combine |
| `IndexError` | You asked for a position that doesn't exist |
| `IndentationError` | Your spacing broke the structure |

**Run each one live** as you take the answer. Students need to see the real message, not a description of it.

### When it goes wrong

| If… | Do this |
|---|---|
| Everyone gets all four | Excellent. Ask *why* for two of them — recognition without understanding is common here. |
| Room is stuck on 1 vs 3 | Both involve a name. Ask: *"Does `score` exist at all? Does `name` exist?"* That separates them. |
| Someone says "they're all syntax errors" | This is the belief you're here to break. Run all four and read the last line of each aloud. |
| Two minutes isn't enough | Give three. Don't rush the silent thinking part — it's where the work happens. |

**Common instructor mistake:** giving the answers verbally instead of running the code. The real terminal output is the whole point.

**Cut rule:** Use snippets 1, 2 and 3.

---

## ⚡ Activity 2 — Spot the Bug (28–36 min)

### What this activity is

Broken code on screen; students find the error **and name it** before suggesting a fix. Unlike Error Message Match, here the errors aren't listed — students must diagnose from scratch. Crucially, one snippet has no error at all and simply produces the wrong answer.

### Why it's here

It's the first time students distinguish a *crash* from a *bug*. That distinction is the session's real content.

### Before class

Have all four snippets ready to run.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line | Listen |
| 0:30–2:00 | Show all four, wait | Diagnose silently |
| 2:00–6:30 | Take one snippet at a time, run each | Name error + fix |
| 6:30–8:00 | Debrief on #4 | Listen |

### Say this

> *"Four programs. For each one, tell me two things: what breaks, and the *name* of the error. 'It's wrong' is not an answer. Ninety seconds."*

### The snippets

```python
# 1
username = input()
print("Hello " + username + "!"
```
```python
# 2
Print("Welcome")
```
```python
# 3
word = "Python"
print(word[6])
```
```python
# 4
name = input()
print("Your name is " + "name")
```

### Answers

| # | Diagnosis | Fix |
|---|---|---|
| 1 | `SyntaxError` — missing closing parenthesis | Add `)` |
| 2 | `NameError` — capital `P`, Python is case-sensitive | `print` |
| 3 | `IndexError` — `"Python"` has length 6, highest index 5 | `word[5]` or lower |
| 4 | **No error.** It prints the literal word `name` instead of what the user typed | Remove the quotes around `name` |

**Snippet 4 is the whole session.** Ask explicitly:

> *"Which one of these would the computer happily let you ship?"*

### When it goes wrong

| If… | Do this |
|---|---|
| They spot #4 immediately | Ask the harder question: *"How would you ever catch that in a big program?"* Answer: read your output, don't just check it ran. |
| They say #4 is fine | Perfect. Run it, type a name, and let the mismatch land silently for a few seconds. |
| Someone jumps to fixes without naming errors | Push back once: *"What's it called?"* The naming is the skill being built. |
| Running long | Do 2 and 4. Number 4 is non-negotiable. |

**Common instructor mistake:** treating snippet 4 as a trick. It isn't — it's the single most realistic bug in the set. Give it the most time, not the least.

---

## Slide Block B (36–44 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred, deck not readable — see Instructor Notes -->
Covers: the debugging procedure, print-statement debugging, and when to ask for help.

**Beats to emphasise**

- **Print-statement debugging.** Put `print()` between lines to see what variables actually hold. This is the single most useful technique they'll learn all month, and it needs no tools.
- **Change one thing at a time.** Students change five things and lose track of which fixed it.
- **Read the error before doing anything else.** Not after two random edits.

**Checkpoint (at 44 min)** — show hands:
> *"Your program runs but the answer's wrong. What's your first move?"*
> **Answer:** Put a `print()` after each line and look at what the variables actually contain.

---

## ⚡ Activity 3 — Human Compiler (44–52 min)

### What this activity is

Students **become** the Python interpreter. You point at one line at a time; the student you point to says exactly what the machine does at that line and what each variable now holds. Nobody is allowed to jump ahead or describe what the program "is trying to do" — one line, literally.

### Why it's here

Print-statement debugging only works if students can predict what a variable *should* contain. This rehearses that skill without a computer.

### Before class

Write the program on the board, or have it on screen with room for a variable table beside it.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line | Listen |
| 0:30–5:30 | Point at each line, take one student per line | Say what the machine does |
| 5:30–7:00 | Reach the crash, ask what a `print()` would have shown | Diagnose |
| 7:00–8:00 | Debrief | Listen |

### Say this

> *"You are Python now. I point at a line, you tell me exactly what the machine does — and what's in each box afterwards. Not what the program is trying to achieve. One line."*

### The program

Assume the user types `20` when prompted.

```python
age = input()
next_age = age + 1
print("Next year: " + next_age)
```

### Line by line

| Line | What the machine does | `age` | `next_age` |
|---|---|---|---|
| 1 | Waits, reads `20`, stores it **as the string `"20"`** | `"20"` | — |
| 2 | Tries to add the number 1 to the string `"20"` → **TypeError, stops** | `"20"` | never created |
| 3 | Never runs | — | — |

### The key question

After line 2 fails, ask:

> *"If you'd put a `print(age)` after line 1, what would you have seen — and would it have helped?"*

**Answer:** You'd see `20`, which looks like a number and tells you nothing. The trap is that `print()` alone doesn't reveal type. Then show the fix:

```python
print(type(age))     # <class 'str'>
```

> *"That's the tool. When a TypeError makes no sense, print the *type*, not just the value."*

`type()` gets taught properly next session — this is a deliberate preview, and students remember it because it solved a problem they just felt.

### When it goes wrong

| If… | Do this |
|---|---|
| Student describes the goal, not the line | *"Not what it's for. What does the machine do, right now, on this line?"* |
| Nobody spots that `age` is a string | That's expected. Point at line 1 again: *"What does `input()` always give you?"* |
| They want the fix immediately | Give it — `int(age)` — but say it's Session 8's topic and don't teach it. |
| Class is quiet and slow | Do lines 1–2 yourself out loud as a model, then hand over. |

**Common instructor mistake:** letting a student narrate the whole program in one go. Stop them at line 1. The line-at-a-time constraint *is* the activity.

---

## Exit Ticket + Homework (52–60 min)

**Exit ticket** — first 4 minutes, before anyone leaves:

> Name the four errors you met today and one line of code that causes each.
> **Answers:** NameError (`print(x)` before `x` exists) · TypeError (`"a" + 5`) · IndexError (`"Zoe"[7]`) · IndentationError (a stray leading space).

**Wrap and homework** — final 4 minutes

Write the procedure on the board and tell them to copy it:

```
WHEN IT BREAKS
1. Read the LAST line — that's the error type
2. Find the LINE NUMBER just above it
3. print() the variables around that line
4. Change ONE thing. Run again.
```

| Task | Unit |
|---|---|
| Coding Practice — Session 6 set, 15 problems | `3ec2d3fe-0670-4186-83ef-7fc0c70b5d6f` |
| MCQ Practice — Session 6 set, 99 questions | `145ba1e4-adee-4089-b15f-d0bc1e6c85e3` |

> *"Tonight, when something breaks, don't message anyone until you've done steps 1 to 3. Then message with the error type and what you tried. You'll fix most of them yourself before you finish typing the message."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Errors mean I'm bad at this | School conditioning — red means failure | The hook: naming the panic, then reframing the message as help |
| All errors are "syntax errors" | Only category they have | Activity 1 — four errors, four distinct names |
| No error means correct | Errors are their only feedback | Activity 2 snippet 4 — runs perfectly, wrong output |
| The error line number is always where the bug is | It's stated so confidently | Slide Block A — a starting point, sometimes the line above |
| `print()` shows me everything | It shows the value, not the type | Activity 3 — `20` and `"20"` print identically |
| Debugging is a special skill some people have | Never seen anyone do it methodically | Running the four-step procedure visibly, twice |

---

## Instructor Notes

- **This session teaches a habit, not a topic.** Nothing new is added to the language. Judge it by whether students stop messaging "my code doesn't work" with no error text attached.
- **Never look impatient at a wrong diagnosis.** The whole session argues that being wrong is information. Your reaction in the first ten minutes decides whether they believe it.
- **The hook needs the traceback visible on a real terminal.** A screenshot works but lands softer. Test your setup.
- **You'll be tempted to teach `int()` and `str()`** — students will ask three times. Don't. They're Session 8, and arriving there having *felt* the TypeError makes the conversion tools land far better. Preview `type()` only, as scripted in Activity 3.
- **This session has an unusual shape:** four activity-style blocks and only two short slide blocks, because debugging cannot be taught by telling. Exit ticket starts at 52 min rather than 57 to leave room for the procedure.
- **Slide placement is unverified.** The deck exists on the platform but wasn't readable when this plan was written, so Block A/B contents are inferred from the session title. Confirm against the real deck and adjust — activities can slot between any two blocks.
- **Data note:** no reading material, no classroom quiz, no MCQ pool exists for this session. Homework points back to Session 6.
