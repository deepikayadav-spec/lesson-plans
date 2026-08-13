# Session 8 — Type Conversions

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Type Conversions · **Prerequisite** Sessions 6–7
**Session type** Concept lecture · **Format** 50-min recalibrated, 2 ALS activities, Classroom Quiz mandatory (never cut, runs last)

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

## Classroom Settling (0–3 min) · Buffer — not instructional

Projector on, deck loaded, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** state the MCQ Practice completion number since last session. Target is 80%.

5 questions on **Sessions 6–7**. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `print("7" + "3")` output?
`A` `10` · `B` `73` · `C` TypeError · `D` `7 3`
→ **B.** *Targets:* Strings join, they don't add.

**Q2.** What does `print("7" + 3)` output?
`A` `73` · `B` `10` · `C` TypeError · `D` `37`
→ **C.** *Targets:* Mixing types fails.

**Q3.** `word = "Python"`. Which raise an IndexError? *(MSQ — select all)*
`A` `word[0]` · `B` `word[5]` · `C` `word[6]` · `D` `word[9]`
→ **C and D.** *Targets:* Length 6, highest index 5. Same indices you'll be slicing today.

**Q4.** A program runs with no error but prints the wrong thing. What do you do first?
`A` Rewrite it · `B` `print()` the variables and look at them · `C` Ask a friend · `D` Nothing, it ran
→ **B.** *Targets:* Session 7's procedure.

**Q5.** `age = input()` and the user types `20`. What is `age`?
`A` The number 20 · `B` The string `"20"` · `C` Depends · `D` Undefined
→ **B.** *Targets:* **This is the door into today's session.** Note the number and reference it in the hook.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

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

## Slide Block A (10–17 min) — DELIVER SLIDES AS-IS

**Verified against the deck** (*"Copy of 2.2 Type Conversion"*). Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1–3 | Welcome · **Recap — String Repetition** | `a = "*" * 10` → `**********` |
| 4 | **Agenda** | Strings *(Slicing)* → Identifying Data Types *(`type()`)* → Type Conversions *(Changing Data Types)* |
| 5 | **Slicing** | `message = "Hi Ravi"` · `part = message[3:6]` — **posed without an answer** |
| 6+ | **Slicing** | `message[3:]` → `Ravi`, with the string shown character-by-character over indices `0 1 2 3 4 5 6` |
| 7+ | **Slicing** | `message[:]` → the whole string, all indices highlighted |

**Beats to emphasise**

- **The index strip on slides 6–7 is the best teaching asset in this deck.** `"Hi Ravi"` written out with `0 1 2 3 4 5 6` beneath it and the slice highlighted. Point at it constantly; ALS Activity 1 reuses exactly this.
- **The end index is excluded.** Say "up to but not including" every single time.
- **Slide 5 poses `message[3:6]` and doesn't answer it.** Take a prediction from the room before advancing.
- **Empty sides mean "all the way."** `[3:]` to the end, `[:]` the whole thing.

> ⚠️ **The deck never shows `[:2]`** — slicing *from* the start with an explicit end. **Quiz Q1 (`message[7:12]`) and ALS Activity 1 snippet 3 (`s[:3]`) both need it.** Add it live: `print("Hi Ravi"[:2])` → `Hi`.

**Checkpoint (at 17 min)** — 10 s silent think, cold-call two students:
> *"`s = "Python"`. What is `s[0:3]`, and how many characters is that?"*
> **Answer:** `Pyt`, three characters — indices 0, 1 and 2. Index 3 is excluded.

---

## ⚡ ALS Activity 1 — Peer Instruction: Predict the Slice (17–23 min)

**ALS format:** Peer Instruction — individual silent commit, hands-vote, then reveal. Chosen over a full pair-discussion because slicing's excluded-end-index error is best caught as an individual mistake in the moment — averaging answers in a pair would let the correct student quietly carry the wrong one.

**Setup line:**
> *"Index strip's on the board — use it. Commit alone first, hands up for your answer, then I run it. If you're wrong, you'll remember this for the rest of the course."*

Write `P-y-t-h-o-n` on the board with `0-1-2-3-4-5` underneath and leave it up. Reveal one snippet at a time:

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

| # | Output | Why |
|---|---|---|
| 1 | `Pyth` | Indices 0,1,2,3 — index 4 excluded |
| 2 | `thon` | From index 2 to the end |
| 3 | `Pyt` | From the start, up to but not including 3 |
| 4 | *(empty line)* | Starts at 3, stops before 3 — nothing in between |

**Snippet 1 is where most rooms vote `Pytho`.** Let that happen. **Snippet 4 surprises everyone** — an empty string is a valid, non-error result.

**Debrief line:**
> *"An empty result isn't a failure — it's just Python telling you honestly there was nothing in that range."*

**Cut rule:** Snippets 1 and 4.

---

## Slide Block B (23–31 min) — DELIVER SLIDES AS-IS

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
- **Slide 10 is the diagnosis.** `type(a)` on an `input()` reveals `<class 'str'>`.
- **Slide 12 is the fix** — the same program with `int()` inserted. Show slides 8 and 12 back to back at the end.

> ⚠️ **The deck never shows `str()`.** It converts *into* numbers, never back into text. **Quiz Q4/Q5 and ALS Activity 2 both need `str()`.** Add it live: `print("Sum: " + str(5))`.

**The hardest idea, compressed (2 min, before the checkpoint):** slide 11 (`int("5.0")`) is posed and never answered — run it live, let the `ValueError` land. Then:
> *"`int("5")` works. `int("5.0")` fails. 15 seconds — with your neighbour, why?"*
> **Answer:** as *text*, `"5.0"` isn't a whole number, and Python won't guess. **Fix:** convert to float first, then int — `int(float("5.0"))` → `5`.

**Checkpoint (at 31 min)** — show hands:
> *"Which of these fail: `int("7")`, `int("seven")`, `int("7.0")`?"*
> **Answer:** The last two. `int("7.0")` fails despite looking like a number.

---

## ⚡ ALS Activity 2 — Progressive Bug-Fix Dictation: The Adding Machine (31–38 min)

**ALS format:** Progressive Bug-Fix Dictation — students dictate a program that instructors deliberately let fail twice, in two different ways, before it works. Different from Activity 1's single predict-and-reveal: here the same program breaks, gets fixed, breaks again differently, and gets fixed again — rehearsing that fixing one type problem doesn't guarantee you've fixed them all.

**Setup line:**
> *"You're writing this, I'm the keyboard. Goal: ask the user for two numbers, then print `Sum: ` followed by the answer."*

**Stage 1 — the naive version.** Most rooms dictate this:

```python
a = input()
b = input()
print(a + b)
```

Run it, enter `2` and `3`. Output: **`23`**

> *"No error. It ran. It's wrong. What happened?"*

Take the diagnosis — both are strings, so `+` joined them.

**Stage 2 — the fix, and the second bug**

```python
a = int(input())
b = int(input())
print("Sum: " + a + b)
```

Run it. **TypeError.**

> *"We fixed one thing and broke another. Read the error — what's it saying now?"*

Answer: now they're numbers, and you can't join a number to `"Sum: "`.

**Stage 3 — working version**

```python
a = int(input())
b = int(input())
result = a + b
print("Sum: " + str(result))
```

> *"`int()` on the way in, `str()` on the way out. That's the shape of almost every program you'll write for the next month."*

**Debrief line:**
> *"Two different bugs, both about type, both invisible until you ran the code. That's why the procedure from last session — read, then check — never stops mattering."*

**Cut rule:** Stages 1 and 3. Skip stage 2's TypeError detour if running late.

---

## Classroom Quiz (38–45 min) · ALS: Individual Answer → Reveal

> 🔒 **Mandatory block — do not cut, do not shorten, do not skip under time pressure.** Runs last, right before the Exit Ticket. **Q1–Q2 from Classroom Quiz A; Q3–Q5 from the MCQ Practice pool** — see the mismatch note at the top of this file.

Every question below is run ALS-style: **individual silent answer first, then explanation.**

5 questions. ~85 s each.

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
> **If they pick 100:** they assumed rounding. This is a real-money bug in the wild. `int()` chops, it does not round.

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

## Exit Ticket + Quiz Push (45–48 min)

**Exit ticket** (~30 s) — before anyone leaves:

> Write the output of each: `int(9.99)` · `int("9")` · `int("nine")` · `str(9) + "9"`
> **Answers:** `9` · `9` · ValueError · `"99"`

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Open MCQ Practice. Everyone, this room, right now — attempt the first 3 questions before you leave your seat. 130 questions here, the biggest pool yet."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 9's warm-up."*

**Remaining homework**

| Task | Unit |
|---|---|
| Coding Practice — 18 problems | `683b9b75-5fc6-4401-9db1-abe0af1854ad` |
| MCQ Practice — 130 questions *(started in class above — finish the rest)* | `639c2eb6-a7dd-4bfa-8aa8-0a1a64bb23bb` |
| RM — Type Conversions | `5de624d9-3ae4-4a49-8049-4d691a378cec` |

> *"Rule of thumb for tonight: `int()` on the way in, `str()` on the way out. If you get a TypeError, ask which side you forgot."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `s[0:4]` gives 5 characters | The end number looks inclusive | ALS Activity 1 snippet 1, counted on the board strip |
| `int()` rounds | Every calculator they've used rounds | Quiz Q4 — `int(99.99)` gives `99` |
| `int("5.0")` should work | It looks like a number | The compressed pair-check in Slide Block B |
| Fixing one type error fixes all of them | Errors feel like one problem | ALS Activity 2 stage 2 — fixing input breaks output |
| `input()` gives a number if you type a number | It looks like a number on screen | Warm-up Q5, then ALS Activity 2 stage 1 |
| A slice that returns nothing is an error | Empty results feel like failure | ALS Activity 1 snippet 4 — `s[3:3]` is a valid empty string |

---

## Instructor Notes

- ✅ **Verified against the real deck** (*"Copy of 2.2 Type Conversion"*). Slide Blocks A and B list the actual slides in order.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Three deck slides pose a question and never answer it** — slide 5 (`message[3:6]`), slide 8 (`input() + input()`), slide 11 (`int("5.0")`). Run each one live or the class gets open questions with no answers.
- **Two ALS activities this session:** Activity 1 is Peer Instruction (individual vote, not a pair discussion), Activity 2 is Progressive Bug-Fix Dictation (a program that breaks twice, differently). The original Think-Pair-Share on `int("5.0")` is folded into a 2-minute pair-check inside Slide Block B instead of running as a full 6-minute activity — the reasoning content survives, the timeboxed slot doesn't.
- **The Classroom Quiz runs last, right before the Exit Ticket** — never cut, never shortened.
- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair.** Target is 80% platform MCQ attempt rate, currently ~33%.
- ⚠️ **Deck gaps this session's quiz depends on:** `[:2]`-style slicing (Q1), and `str()` entirely (Q4/Q5, ALS Activity 2). Both scripted as live additions above. **Worth raising with the content team.**
- **This session pays off Sessions 6 and 7.** Students have already *felt* the TypeError; today they get the tool. Reference that debt explicitly in the hook.
- **⚠️ The Classroom Quiz pools don't match this session's content.** Quiz A is slicing (in today's RM) and Quiz B is variable reassignment from Session 5. Type conversion appears only in the MCQ Practice pool — the 5 questions above are drawn accordingly. **Worth raising with the content team.**
- **Two topics share this session** — slicing (Block A) and conversion (Block B) — and they aren't obviously related. Say plainly: *"Two separate tools today, both about getting at the data you actually want."*
- **130 MCQ questions and 18 coding problems** — the largest set so far. Plenty for the Quiz Push and homework.
- The `int("5.0")` case is the hardest idea of the session. If time is short elsewhere, protect its compressed beat in Slide Block B — it's what separates students who understand conversion from students who've memorised `int()`.
