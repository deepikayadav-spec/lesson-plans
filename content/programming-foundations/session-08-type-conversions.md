# Session 8 — Type Conversions

**Duration** 60 min · **Topic** Type Conversions · **Prerequisite** Sessions 6–7
**Session type** Concept lecture

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Type Conversions | `dcc9159c-fe50-428b-8cc1-e3211b66d2ef` |
| RM — Type Conversions | `5de624d9-3ae4-4a49-8049-4d691a378cec` |
| Classroom Quiz A (34 q — **slicing**) | `104cc1ec-9635-40ad-87d7-df4acfc9170c` |
| Classroom Quiz B (55 q — **reassignment**) | `6a897dfd-5ed0-4cf7-8197-04ab772e6e39` |
| MCQ Practice (130 q — includes conversion) | `639c2eb6-a7dd-4bfa-8aa8-0a1a64bb23bb` |
| Coding Practice (18 q) | `683b9b75-5fc6-4401-9db1-abe0af1854ad` |

> ⚠️ **Quiz-pool mismatch.** Neither Classroom Quiz pool covers type conversion — Quiz A is string slicing, Quiz B is variable reassignment from Session 5. The conversion questions live in the MCQ Practice pool. The Classroom Quiz below therefore draws 2 from Quiz A and 3 from the MCQ pool. See Instructor Notes.

---

## Learning Objectives

By the end of this session, students will be able to:

1. Extract part of a string using slicing, and state that the end index is excluded. *(APPLYING)*
2. Check any value's type using `type()`. *(REMEMBERING)*
3. Convert between types using `int()`, `float()` and `str()`. *(APPLYING)*
4. Explain why `int("Five")` raises a `ValueError` but `int("5")` does not. *(UNDERSTANDING)*
5. Take numeric input from a user and perform arithmetic on it correctly. *(ANALYZING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Sessions 6–7**. Newly authored. ~45 s each, project the distribution, never name individuals.

**Q1.** What data type does `input()` return?
`A` Integer if it looks like one · `B` Always a string · `C` Whatever you typed · `D` Depends on the user
→ **B.** *Targets:* The load-bearing fact from Session 6. *If >40% wrong:* stop. Today is unteachable without it.

**Q2.** What does `print("7" + "3")` output?
`A` `10` · `B` `73` · `C` TypeError · `D` `7 3`
→ **B.** *Targets:* Strings join, they don't add.

**Q3.** What does `print("7" + 3)` output?
`A` `73` · `B` `10` · `C` TypeError · `D` `37`
→ **C.** *Targets:* Mixing types fails.

**Q4.** In an error message, which line tells you the error type?
`A` The first line · `B` The last line · `C` The line number · `D` None
→ **B.** *Targets:* Session 7's reading order.

**Q5.** `word = "Python"`. Which raise an IndexError? *(MSQ — select all)*
`A` `word[0]` · `B` `word[5]` · `C` `word[6]` · `D` `word[9]`
→ **C and D.** *Targets:* Length 6, highest index 5.

**Q6.** A program runs with no error but prints the wrong thing. What do you do first?
`A` Rewrite it · `B` `print()` the variables and look at them · `C` Ask a friend · `D` Nothing, it ran
→ **B.** *Targets:* Session 7's procedure.

**Q7.** `age = input()` and the user types `20`. What is `age`?
`A` The number 20 · `B` The string `"20"` · `C` Depends · `D` Undefined
→ **B.** *Targets:* Same as Q1, asked concretely. **This is the door into today's session.** Note the number and reference it in the hook.

---

## Hook (7–10 min)

Type this live. Enter `20` when it asks.

```python
age = input()
print(age + 1)
```

TypeError. Let it sit.

> *"You met this in the last session and you diagnosed it correctly — `input()` gave us a string, and we tried to add a number to it. You knew what was wrong. What you couldn't do yet was fix it."*

Then add one word and re-run:

```python
age = int(input())
print(age + 1)
```

`21`.

> *"One word. That's today. By the end of this hour you'll be able to move any value from one type to another — which means your programs can finally do maths with what the user types."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

**Verified against the deck** (*"Copy of 2.2 Type Conversion"*). Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1–3 | Welcome · **Recap — String Repetition** | `a = "*" * 10` → `**********` |
| 4 | **Agenda** | Strings *(Slicing)* → Identifying Data Types *(`type()`)* → Type Conversions *(Changing Data Types)* |
| 5 | **Slicing** | `message = "Hi Ravi"` · `part = message[3:6]` — **posed without an answer** |
| 6+ | **Slicing** | `message[3:]` → `Ravi`, with the string shown character-by-character over indices `0 1 2 3 4 5 6` |
| 7+ | **Slicing** | `message[:]` → the whole string, all indices highlighted |

**Beats to emphasise**

- **The index strip on slides 6–7 is the best teaching asset in this deck.** `"Hi Ravi"` written out with `0 1 2 3 4 5 6` beneath it and the slice highlighted. Point at it constantly; Activity 1 reuses exactly this.
- **The end index is excluded.** Say "up to but not including" every single time. It is the source of nearly every slicing error, and of Quiz Q1.
- **Slide 5 poses `message[3:6]` and doesn't answer it.** Take a prediction from the room before advancing — the deck set the question up for you.
- **Empty sides mean "all the way."** `[3:]` to the end, `[:]` the whole thing.

> ⚠️ **The deck never shows `[:2]`** — slicing *from* the start with an explicit end. It shows `[3:]` and `[:]` only. **Quiz Q1 (`message[7:12]`) and Activity 1 snippet 3 (`s[:3]`) both need it.** Add it live: `print("Hi Ravi"[:2])` → `Hi`.

**Checkpoint (at 22 min)** — cold-call two students:
> *"`s = "Python"`. What is `s[0:3]`, and how many characters is that?"*
> **Answer:** `Pyt`, three characters — indices 0, 1 and 2. Index 3 is excluded.

---

## ⚡ Activity 1 — Predict the Output (22–27 min)

### What this activity is

You show a snippet and **the whole class commits to an answer before you run it.** Then you run it. The commitment is the mechanism — a student who has publicly said `Pyth` remembers the off-by-one far better than one who watched passively.

### Why it's here

Slicing's excluded end index cannot be learned by being told. It has to be got wrong once, visibly.

### Before class

Snippets in a file, ready to run one at a time. Write `P-y-t-h-o-n` on the board with `0-1-2-3-4-5` underneath and leave it up.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:20 | Setup line, point at the index strip on the board | Look |
| 0:20–4:00 | Reveal one snippet, take a chorus answer, **then** run | Predict aloud |
| 4:00–5:00 | Debrief | Listen |

### Say this

> *"The index strip is on the board — use it. Everyone answers out loud together before I run anything. If you're wrong, you'll remember this for the rest of the course."*

### The snippets

```python
s = "Python"
print(s[0:4])      # 1
```
```python
print(s[2:])       # 2
```
```python
print(s[:3])       # 3
```
```python
print(s[3:3])      # 4
```

### Answers

| # | Output | Why |
|---|---|---|
| 1 | `Pyth` | Indices 0,1,2,3 — index 4 excluded |
| 2 | `thon` | From index 2 to the end |
| 3 | `Pyt` | From the start, up to but not including 3 |
| 4 | *(empty line)* | Starts at 3, stops before 3 — nothing in between |

**Snippet 1 is where most rooms say `Pytho`.** Let that happen.
**Snippet 4 surprises everyone** — an empty string is a valid, non-error result.

### When it goes wrong

| If… | Do this |
|---|---|
| Room gets #1 right | Go straight to #4, which almost nobody gets. |
| Nobody will call out | Hands vote: *"Hands for `Pyth`. Hands for `Pytho`."* Voting is easier than speaking. |
| Someone argues #4 should be an error | Good argument — say so. Then: *"Python returns an empty string. It's not an error, it's just nothing."* |
| Running late | Do 1 and 4. |

**Common instructor mistake:** running before the prediction. Once output is on screen it's a demo, not an activity.

**Cut rule:** Snippets 1 and 4.

---

## Classroom Quiz (27–34 min)

5 MCQs. ~80 s each including discussion. **Q1–Q2 from Classroom Quiz A; Q3–Q5 from the MCQ Practice pool** — see the mismatch note at the top.

**Q1** — `a9182d8a-f595-4326-b42e-2c3e04a828b6` *(Quiz A · APPLYING)*
What will be the output of:
```python
message = "Hello, World!"
print(message[7:12])
```
- `, Worl`
- `ello,`
- ✅ **`World`**
- `World!`

> *Explanation (platform):* The slicing operation `message[7:12]` starts from index 7 and stops at index 12 (not including index 12). In "Hello, World!", the characters from index 7 to 11 are 'W','o','r','l','d', which forms "World".
> **If they pick `World!`:** classic excluded-end error. Count it out on the board.

**Q2** — `f052d7df-43b7-4e3c-b4ef-43ade607d9b7` *(Quiz A · ANALYZING)*
Identify the error in:
```python
message = "Programming"
print(message(6:))
```
- ✅ **Round brackets are used instead of square brackets**
- The slicing will cause an IndexError
- The code will print 'Programming'
- Syntax error due to missing start index

> *Explanation (platform):* Round brackets are used instead of square brackets. The correct statement is `print(message[6:])`.
> **Worth saying:** round brackets call something; square brackets index into something. Different jobs, easy to typo.

**Q3** — `ae00d4e1-ad5e-446c-912c-9311881cf649` *(MCQ pool · REMEMBERING)*
`type()` is used to check the data type in Python.
- ✅ **True**
- False

> *Explanation (platform):* The statement is correct. In Python, the `type()` function is used to check the data type of a value or variable.

**Q4** — `03b879bc-0aec-44cf-9955-10c482714c0f` *(MCQ pool · APPLYING)*
What will be the output of:
```python
a = 99.99
a = int(a)
print(a)
```
- ValueError
- ✅ **99**
- 100
- "100"

> *Explanation (platform):* When converting a float to an integer using `int()`, Python removes the decimal part without rounding. Therefore `int(99.99)` results in `99`, not `100`.
> **If they pick 100:** they assumed rounding. This is a real-money bug in the wild — worth 30 seconds. `int()` chops, it does not round.

**Q5** — `26bfad0c-01b8-4254-927b-73697cbc0a78` *(MCQ pool · APPLYING)*
What will be the output of:
```python
x = 60
y = "60"
result = x + int(y)
print(result)
```
- `"60"`
- `60`
- TypeError
- ✅ **`120`**
- `60 + int("60")`

> *Explanation (platform):* `x` is the integer 60 and `y` is the string "60". `x + int(y)` converts the string to the integer 60, then adds it to `x`, giving 120.
> **If they pick TypeError:** they spotted the type mix but missed that `int()` resolves it. Half-right — say so.

---

## Slide Block B (34–44 min) — DELIVER SLIDES AS-IS

**Verified against the deck.** This half is built as a problem → diagnosis → tool sequence. Deliver it in that order.

| # | Slide | Content |
|---|---|---|
| 8 | **I/O Basics — Adding Two Numbers** | `a = input()` · `b = input()` · `result = a + b` · input `2` and `3` → *"What will be the output?"* — **unanswered** |
| 9 | **Printing Data Type** | `print(type(4.2))` beside `print(type("Hi"))` |
| 10 | **Printing Data Type** | `a = input()` · `print(type(a))` → `<class 'str'>` → *"Can we convert the data type of variables to integer?"* |
| 11 | **String to Integer** | `a = "5.0"` · `a = int(a)` · `print(type(a))` — **posed without its answer** |
| 12 | **Type Conversion — Adding Two Numbers** | The fixed version: `a = int(a)` and `b = int(b)` inserted, inputs `2` and `3` |
| 13 | **Week in Review** | Indexing · Slicing · Type Conversions |

**Beats to emphasise**

- **Slide 8 is the session's hook, placed mid-deck.** It asks what `input()` + `input()` gives and doesn't say. Take a vote — most will say `5`. Run it: `23`. That failure motivates everything after it.
- **Slide 10 is the diagnosis.** `type(a)` on an `input()` reveals `<class 'str'>`. Say: *"That's the answer to why we got 23."*
- **Slide 12 is the fix** — the same program with `int()` inserted. Show slides 8 and 12 back to back at the end.
- **The `input()` + `int()` combination** is the practical payoff. Both forms are identical:
  ```python
  a = input()
  a = int(a)
  ```
  ```python
  a = int(input())
  ```

> ⚠️ **Slide 11 (`int("5.0")`) is posed and never answered.** This is the hardest idea in the session — it raises a **ValueError**, because `"5.0"` isn't a whole number in text form. **You must run it live**, or Activity 2 has nothing to discuss. The deck sets the question up and walks away.

> ⚠️ **The deck never shows `str()`.** It converts *into* numbers, never back into text. **Quiz Q4/Q5 and Activity 3's second bug both need `str()`** — and it's the exact bug from Session 6's Activity 3. Add it live: `print("Sum: " + str(5))`.

**Checkpoint (at 44 min)** — show hands:
> *"Which of these fail: `int("7")`, `int("seven")`, `int("7.0")`?"*
> **Answer:** The last two. `int("7.0")` fails despite looking like a number.

---

## ⚡ Activity 2 — Think–Pair–Share (44–50 min)

### What this activity is

A three-stage discussion. Students think alone first (1 min), then discuss in pairs (2 min), then a few pairs report to the room (3 min). The staging matters: thinking alone first stops the fastest talker from setting everyone's answer, and the pair stage lets students rehearse before speaking publicly.

### Why it's here

`int("5.0")` failing is genuinely counter-intuitive. A discussion surfaces students' reasoning, which is what needs correcting — not just the fact.

### Before class

Put the question on a slide or write it on the board so it stays visible through all three stages.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:20 | Setup line, reveal the question | Read |
| 0:20–1:20 | **Silence.** Do not talk during this. | Think alone, write |
| 1:20–3:20 | Say "pairs, go" | Discuss with neighbour |
| 3:20–6:00 | Take answers from three pairs | Report out |

### Say this

> *"One minute on your own — no talking, write something down. Then two minutes with the person next to you. Then I'll take answers from three pairs."*

### The question

> **`int("5")` works and gives 5.**
> **`int("5.0")` fails with a ValueError.**
> **Why? And what would you write instead to get the number 5 out of `"5.0"`?**

### What good answers look like

- **The why:** `int()` on a string requires the text to be a whole number, exactly. `"5.0"` contains a decimal point, so as *text* it isn't a valid integer — Python won't guess.
- **The fix:** convert to float first, then to int — `int(float("5.0"))` → `5`.

Accept partial answers generously. A pair that gets the "why" without the fix has done the harder half.

### When it goes wrong

| If… | Do this |
|---|---|
| Nobody reaches the fix | Expected. Give it, then ask *why* it works — the two-step is the insight. |
| Pairs go silent immediately | They need a sharper prompt: *"Just say out loud what you each wrote down."* |
| One pair answers everything | Take from two more anyway. *"Different pair — what did you two say?"* |
| Room finishes early | Extend: *"What about `int(5.0)` — no quotes. Does that work?"* (Yes, it gives 5. Floats convert fine; float-shaped *strings* don't.) |

**Common instructor mistake:** filling the one-minute silence with talking. The silence is the activity. Stand still and let it run.

**Cut rule:** 30 s think, 90 s pair, two reports.

---

## ⚡ Activity 3 — Live Coding: The Adding Machine (50–57 min)

### What this activity is

You're at the keyboard on the projector; students dictate every line. You type only what they say, and you deliberately write one broken version so the class diagnoses it.

### Why it's here

It assembles the whole session — `input()`, `int()`, `str()` — into one program, which is the shape of tonight's homework.

### Before class

Empty file, font ≥18pt, terminal visible so input prompts show.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, state the goal | Listen |
| 0:30–2:30 | Type the naive version they dictate, run it, hit the bug | Dictate |
| 2:30–5:00 | Fix with `int()`, run, then hit the `str()` bug | Diagnose |
| 5:00–6:00 | Final working version | Confirm |
| 6:00–7:00 | Debrief | Listen |

### Say this

> *"You're writing this, I'm the keyboard. Goal: ask the user for two numbers, then print `Sum: ` followed by the answer."*

### Stage 1 — the naive version

Most rooms dictate this:

```python
a = input()
b = input()
print(a + b)
```

Run it, enter `2` and `3`. Output: **`23`**

> *"No error. It ran. It's wrong. What happened?"*

Take the diagnosis — both are strings, so `+` joined them.

### Stage 2 — the fix, and the second bug

```python
a = int(input())
b = int(input())
print("Sum: " + a + b)
```

Run it. **TypeError.**

> *"We fixed one thing and broke another. Read the error — what's it saying now?"*

Answer: now they're numbers, and you can't join a number to `"Sum: "`.

### Stage 3 — working version

```python
a = int(input())
b = int(input())
result = a + b
print("Sum: " + str(result))
```

> *"`int()` on the way in, `str()` on the way out. That's the shape of almost every program you'll write for the next month."*

### When it goes wrong

| If… | Do this |
|---|---|
| They dictate the correct version immediately | Say *"too good"* — then type the naive version yourself and ask what it would output. Stage 1 must happen. |
| Nobody diagnoses `23` | Ask: *"What type is `a`? What does `+` do to two of those?"* |
| They suggest `print("Sum:", result)` (comma) | It works and is valid Python. Say so, run it — then say the course uses `+` with `str()` for now, and both are fine. |
| Running long | Skip stage 2, go straight from the `23` bug to the working version. |

**Common instructor mistake:** rescuing stage 1 too fast. The `23` output needs a few seconds of silence to register.

**Cut rule:** Stages 1 and 3.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — before anyone leaves:

> Write the output of each: `int(9.99)` · `int("9")` · `int("nine")` · `str(9) + "9"`
> **Answers:** `9` · `9` · ValueError · `"99"`

**Homework**

| Task | Unit |
|---|---|
| Coding Practice — 18 problems | `683b9b75-5fc6-4401-9db1-abe0af1854ad` |
| MCQ Practice — 130 questions | `639c2eb6-a7dd-4bfa-8aa8-0a1a64bb23bb` |
| RM — Type Conversions | `5de624d9-3ae4-4a49-8049-4d691a378cec` |

> *"Rule of thumb for tonight: `int()` on the way in, `str()` on the way out. If you get a TypeError, ask which side you forgot."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `s[0:4]` gives 5 characters | The end number looks inclusive | Activity 1 snippet 1, counted on the board strip |
| `int()` rounds | Every calculator they've used rounds | Quiz Q4 — `int(99.99)` gives `99` |
| `int("5.0")` should work | It looks like a number | Activity 2 — the whole discussion |
| Fixing one type error fixes all of them | Errors feel like one problem | Activity 3 stage 2 — fixing input breaks output |
| `input()` gives a number if you type a number | It looks like a number on screen | Warm-up Q7, then Activity 3 stage 1 |
| A slice that returns nothing is an error | Empty results feel like failure | Activity 1 snippet 4 — `s[3:3]` is a valid empty string |

---

## Instructor Notes

- ✅ **Verified against the real deck** (*"Copy of 2.2 Type Conversion"*). Slide Blocks A and B list the actual slides in order.
- **Three deck slides pose a question and never answer it** — slide 5 (`message[3:6]`), slide 8 (`input() + input()`), slide 11 (`int("5.0")`). That's a deliberate teaching style and it works well **only if you run each one live.** If you click past them the class gets three open questions and no answers. Slide 11 is the critical one.
- ⚠️ **Deck gaps this session's quiz depends on:** `[:2]`-style slicing (Q1), and `str()` entirely (Q4/Q5, Activity 3). Both scripted as live additions above. **Worth raising with the content team** — a session on type conversion that never shows `str()` is a real omission.
- **This session pays off Sessions 6 and 7.** Students have already *felt* the TypeError; today they get the tool. Reference that debt explicitly in the hook — it makes the content feel earned rather than arbitrary.
- **⚠️ The Classroom Quiz pools don't match this session's content.** Quiz A is slicing (which is in today's RM) and Quiz B is variable reassignment from Session 5. Type conversion — the session's actual title topic — appears only in the MCQ Practice pool. The five questions above are drawn accordingly. **Worth raising with the content team:** a session on type conversion with no classroom-quiz coverage of type conversion is a real gap, and any instructor who picks 5 questions at random from Quiz A/B will assess the wrong thing entirely.
- **Two topics share this session** — slicing (Block A) and conversion (Block B) — and they aren't obviously related. Don't pretend they are. Say plainly: *"Two separate tools today, both about getting at the data you actually want."*
- **Pacing risk:** slicing generates a lot of "what about…" questions. Cap Block A at 12 minutes; the conversion half is the one students need for homework.
- **130 MCQ questions and 18 coding problems** — the largest set so far. Plenty for the practice block.
- The `int("5.0")` case in Activity 2 is the hardest idea of the session. If time is short elsewhere, protect it — it's what separates students who understand conversion from students who've memorised `int()`.
