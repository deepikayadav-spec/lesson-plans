# Session 7 — How to Debug Your Code

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Type Conversions · **Prerequisite** Session 6
**Session type** Support session. No classroom quiz, no reading material, no MCQ pool of its own. · **Format** 50-min recalibrated, 2 ALS activities

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

## Classroom Settling (0–3 min) · Buffer — not instructional

Projector on, deck loaded, a failing coding problem open on the real platform (not just screenshots), students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** state the MCQ Practice completion number since Session 6. Target is 80%.

5 questions on **Session 6**. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `print("ab" + 3)` output?
`A` `ab3` · `B` `ababab` · `C` TypeError · `D` `3ab`
→ **C.** *Targets:* Can't join string to number.

**Q2.** What data type does `input()` return?
`A` Whatever the user typed · `B` Always a string · `C` Integer if it looks like one · `D` Depends
→ **B.** *Targets:* The load-bearing fact from Session 6. *If >40% wrong:* demonstrate immediately — `age = input()` then `age + 1`.

**Q3.** `name = "Ravi"`. What is `name[0]`?
`A` `R` · `B` `a` · `C` `Ravi` · `D` `0`
→ **A.** *Targets:* Indexing from zero.

**Q4.** `name = "Ravi"`. Which raises an IndexError? *(MSQ — select all)*
`A` `name[0]` · `B` `name[3]` · `C` `name[4]` · `D` `name[10]`
→ **C and D.** *Targets:* Length 4 means the highest index is 3. *Misconception:* missing C is the classic off-by-one.

**Q5.** Your program runs with no error but prints the wrong answer. What is that called?
`A` A syntax error · `B` A bug · `C` Not a problem · `D` A crash
→ **B.** *Targets:* Bug vs error. **This is today's hook** — most students think "no error" means "correct". Note the number.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–11 min)

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

> *"For the next forty minutes we do nothing but read these properly."*

---

## Slide Block A (11–20 min) — DELIVER SLIDES AS-IS

> ⚠️ **This deck is not what the session title suggests.** *"Copy of Python — Debugging Code"* teaches **the platform's built-in step-through debugger tool**, not how to read error messages. There is no slide on tracebacks, NameError, TypeError, IndexError or IndentationError. Plan accordingly: the deck gives students a *tool*, the activities below give them the *reading skill*. Both are needed, and they don't overlap.

**Verified against the deck.** Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1 | Welcome | Skip |
| 2 | **What is Debugging?** | "Debugging is the process of working through code **step-by-step** to **find** and **correct** errors" |
| 3 | **Coding Practice — Reverse the digits** | The real platform screen: a list of solved problems with *Reverse the digits* still IN PROGRESS |
| 4 | **Failed Test Case** | The problem open, Test Case 1 failing — *Your Output* `21` vs *Expected* `12` — with the **DEBUG** button highlighted |
| 5 | **Execute Code Line by Line** | The debugger open on a 5-line program, Step 1 of 5, with FIRST / PREV / NEXT / LAST controls |
| 6 | **Value in Variables** | Step 4 of 5 — the **Scopes** panel showing `word "21"`, `first_digit "2"`, `second_digit "1"` |
| 7 | **Debug** | The fix applied — line 4 changed to `second_digit + first_digit` — output now correct |
| 8 | **Update Input** | Changing the test input to `43` and re-running to confirm output `12` |

**Beats to emphasise**

- **This is a bug that does not crash.** The program runs perfectly and prints `21` instead of `12`. That is the crash-vs-bug distinction from warm-up Q5, and the deck opens on it. Name it explicitly.
- **Slide 6 is the payoff.** The Scopes panel shows what every variable actually holds at that moment. Say: *"This is print-statement debugging, except the platform does it for you."*
- **Walk slides 5–8 on the real platform if you can**, not as static images. Open a failing problem, click DEBUG, step through.
- **Slide 8's move — change the input, re-run** — is the habit that catches edge cases. Thirty seconds, worth keeping.

> ⚠️ **Nothing in this deck names an error type**, yet this session's exit ticket and both ALS activities are built on naming them. That content is instructor-supplied — a debugger doesn't help when the program won't start, but be aware you are adding it, not delivering it.

**Checkpoint (at 20 min)** — 10 s silent think, then cold-call:
> *"The program ran, nothing went red, and the answer was wrong. What did the debugger let us see that just reading the code didn't?"*
> **Answer:** What each variable actually held, at each step.

---

## ⚡ ALS Activity 1 — Silent Match → Cold-Call Reveal: Error Message Match (20–27 min)

**ALS format:** Silent Individual Match, then Cold-Call Reveal — everyone matches alone on paper first (no talking, no pairing), then answers are pulled one at a time from different students. Chosen because this is the first time these four errors get *named* as a set; an individual, unaided pass at the naming is what actually tests whether the category exists in each student's head, not just the room's collective memory.

**Setup line:**
> *"Four broken programs, four error messages, shuffled. Match them. Two minutes, on your own, no talking. You have all seen every one of these before."*

Snippets on the left, errors shuffled on the right — **do not present them in matching order.**

| # | Snippet | | Error |
|---|---|---|---|
| 1 | `print(score)`<br>`score = 10` | A | `TypeError` |
| 2 | `print("age" + 5)` | B | `IndexError` |
| 3 | `name = "Zoe"`<br>`print(name[7])` | C | `IndentationError` |
| 4 | `a = 1`<br>` b = 2` | D | `NameError` |

**Answers:** 1→D · 2→A · 3→B · 4→C

| Error | What it actually means |
|---|---|
| `NameError` | You used a name Python has never seen — or hasn't seen *yet* |
| `TypeError` | You combined two kinds of things that don't combine |
| `IndexError` | You asked for a position that doesn't exist |
| `IndentationError` | Your spacing broke the structure |

**Run each one live** as you take the answer from a different student per snippet. Students need to see the real message, not a description of it.

**Debrief line:**
> *"Four names for four different problems. 'It broke' stops being useful the moment you can say which of these four it was."*

**Cut rule:** Use snippets 1, 2 and 3.

---

## Teaching Block B — Board + Live Typing (27–35 min)

> **The deck ends at slide 8.** There are no further slides, so this block is yours. It supplies the half the deck omits: what to do when the program won't run at all, and how to debug without the platform's tool.

**Cover three things.**

**1. Print-statement debugging** — the manual version of the Scopes panel they just saw:

```python
word = input()
print(word)              # what did I actually get?
first_digit = word[0]
print(first_digit)       # is it what I expected?
```

> *"The debugger showed you a Scopes panel. When you're coding outside the platform there is no panel — so you build one with `print()`. Same idea, five seconds of typing."*

**2. `print()` shows the value, not the type — live demo (2 min).** `20` and `"20"` print identically. Assume the user types `20`:

```python
age = input()
next_age = age + 1        # TypeError — age is the string "20"
```

Ask: *"If you'd put a `print(age)` after line 1, what would you have seen — and would it have helped?"* **Answer:** you'd see `20`, which looks like a number and tells you nothing. Then show the actual tool:

```python
print(type(age))     # <class 'str'>
```

> *"That's the fix. When a TypeError makes no sense, print the *type*, not just the value."* `type()` gets taught properly next session — this is a deliberate preview, and it lands because it just solved a problem they felt.

**3. The procedure** — write it on the board and leave it up:

```
WHEN IT BREAKS
1. Read the LAST line — that's the error type
2. Find the LINE NUMBER just above it
3. print() the variables around that line
4. Change ONE thing. Run again.
```

**Beats to emphasise**

- **The debugger only helps when the program runs.** If it won't start, you're reading an error message — which is steps 1 and 2.
- **Change one thing at a time.** Students change five things and lose track of which fixed it.

**Checkpoint (at 35 min)** — show hands:
> *"Your program runs but the answer's wrong. Two ways to see what's inside your variables — name both."*
> **Answer:** The platform's DEBUG button, or `print()` after each line.

---

## ⚡ ALS Activity 2 — Silent Diagnose → Pair Verify: Spot the Bug (35–43 min)

**ALS format:** Silent Diagnose → Pair Verify — everyone diagnoses all four snippets alone first, then briefly checks their error-type naming with a neighbour before any answer is taken publicly. Different from Activity 1's pure silent-match: here nothing is listed, students must produce the diagnosis from scratch, so the pair check catches an individually-missed error type before it goes uncorrected.

**Setup line:**
> *"Four programs. On your own first: for each one, decide what breaks and the *name* of the error. 'It's wrong' is not an answer. Ninety seconds silent, then 30 seconds — compare with your neighbour."*

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

**Answers**

| # | Diagnosis | Fix |
|---|---|---|
| 1 | `SyntaxError` — missing closing parenthesis | Add `)` |
| 2 | `NameError` — capital `P`, Python is case-sensitive | `print` |
| 3 | `IndexError` — `"Python"` has length 6, highest index 5 | `word[5]` or lower |
| 4 | **No error.** It prints the literal word `name` instead of what the user typed | Remove the quotes around `name` |

**Snippet 4 is the whole session.** Ask explicitly:
> *"Which one of these would the computer happily let you ship?"*

**Debrief line:**
> *"Three of these crashed and told you exactly where. The fourth ran fine and lied to you. That's why step 3 of the procedure — print your variables — matters even when nothing turns red."*

**Cut rule:** Do 2 and 4. Number 4 is non-negotiable.

---

## Exit Ticket + Quiz Push (43–48 min)

**Exit ticket** (~1.5 min) — before anyone leaves:

> Name the four errors you met today and one line of code that causes each.
> **Answers:** NameError (`print(x)` before `x` exists) · TypeError (`"a" + 5`) · IndexError (`"Zoe"[7]`) · IndentationError (a stray leading space).

Have students copy the procedure off the board:
```
WHEN IT BREAKS
1. Read the LAST line — that's the error type
2. Find the LINE NUMBER just above it
3. print() the variables around that line
4. Change ONE thing. Run again.
```

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Open MCQ Practice from Session 6 — whoever hasn't finished it. At least 3 more questions before you leave your seat."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 8's warm-up."*

**Remaining homework**

| Task | Unit |
|---|---|
| Coding Practice — Session 6 set, 15 problems | `3ec2d3fe-0670-4186-83ef-7fc0c70b5d6f` |
| MCQ Practice — Session 6 set, 99 questions *(started in class above — finish the rest)* | `145ba1e4-adee-4089-b15f-d0bc1e6c85e3` |

> *"Tonight, when something breaks, don't message anyone until you've done steps 1 to 3. Then message with the error type and what you tried. You'll fix most of them yourself before you finish typing the message."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Errors mean I'm bad at this | School conditioning — red means failure | The hook: naming the panic, then reframing the message as help |
| All errors are "syntax errors" | Only category they have | ALS Activity 1 — four errors, four distinct names |
| No error means correct | Errors are their only feedback | ALS Activity 2 snippet 4 — runs perfectly, wrong output |
| The error line number is always where the bug is | It's stated so confidently | Slide Block A — a starting point, sometimes the line above |
| `print()` shows me everything | It shows the value, not the type | Teaching Block B — `20` and `"20"` print identically |
| Debugging is a special skill some people have | Never seen anyone do it methodically | Running the four-step procedure visibly, twice |

---

## Instructor Notes

- **This session teaches a habit, not a topic.** Nothing new is added to the language. Judge it by whether students stop messaging "my code doesn't work" with no error text attached.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities, both individual-first designs:** Activity 1 is Silent Match → Cold-Call Reveal (no pairing at all), Activity 2 is Silent Diagnose → Pair Verify (individual first, pair only to check). The original third activity (Human Compiler) is folded into Teaching Block B as the `type()` preview demo instead of running as its own block — its unique content (the type-vs-value trap) survives, the line-by-line format doesn't repeat a third time in this course.
- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair.** Target is 80% platform MCQ attempt rate, currently ~33%. This session has no MCQ pool of its own — push is against Session 6's pool.
- **Never look impatient at a wrong diagnosis.** The whole session argues that being wrong is information. Your reaction in the first ten minutes decides whether they believe it.
- **The hook needs the traceback visible on a real terminal.** A screenshot works but lands softer. Test your setup.
- **You'll be tempted to teach `int()` and `str()`** — students will ask three times. Don't. They're Session 8, and arriving there having *felt* the TypeError makes the conversion tools land far better. Preview `type()` only, as scripted in Teaching Block B.
- ✅ **Verified against the real deck** (*"Copy of Python — Debugging Code"*, 8 slides).
- ⚠️ **The deck teaches a tool, not a skill.** It is entirely a walkthrough of the platform's step-through debugger on one worked example (*Reverse the digits*). It never names a single error type, never shows a traceback, and stops after slide 8. **Roughly half this session is instructor-supplied** — Teaching Block B and both ALS activities. That's a deliberate choice, not an oversight. **Worth raising with the content team** that a session titled *"How to debug your code"* omits error messages entirely.
- **Have a failing coding problem open on the real platform** before class. Slides 3–8 are screenshots of it; doing it live is far better.
- **Data note:** no reading material, no classroom quiz, no MCQ pool of its own exists for this session. Homework points back to Session 6.
