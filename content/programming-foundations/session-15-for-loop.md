# Session 15 — For Loop

**Duration** 60 min · **Topic** Loops · **Prerequisite** Sessions 13–14
**Session type** Concept lecture

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — For Loop | `f6a42c4e-cad0-4591-b363-afdd25e4b49f` |
| RM — For Loop | `384585b9-ff4a-43a6-884a-e918abf0eaeb` |
| Classroom Quiz A (56 q) | `48287995-78af-408c-964b-ad31f8767a64` |
| MCQ Practice (84 q) | `513f4a5f-5ce9-44c9-803e-e89155504772` |
| Coding Practice (6 q) | `ad396947-a6fc-4dc5-b3ec-221c6a4e9d0d` |
| Coding Practice - 1 (11 q) | `8de7fd4f-3c84-4b46-863e-d84c15c03a92` |
| Coding Practice - 2 (11 q) | `7c7f921a-2eed-4e2e-b98a-5580be1d3561` |
| Coding Practice - 3 (11 q) | `52d26bc5-7e81-4e3d-a4fd-63046263820b` |

> **Note:** this session has **one** classroom quiz pool (A), not the usual two, and **four** coding practice sets totalling 39 problems — by far the largest in the first fifteen sessions.

---

## Learning Objectives

By the end of this session, students will be able to:

1. Write a `for` loop that iterates over the characters of a string. *(APPLYING)*
2. Use `range(n)` and state that it starts at 0 and stops before `n`. *(UNDERSTANDING)*
3. Use `range(start, end)` and predict the sequence it produces. *(APPLYING)*
4. Explain why a `for` loop needs no manual counter update. *(UNDERSTANDING)*
5. Choose between `for` and `while` for a given task. *(ANALYZING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Sessions 13–14**. Newly authored. ~45 s each, project the distribution, never name individuals.

**Q1.** What are the three parts of a while loop?
`A` Input, process, output · `B` Initialise, condition, update · `C` Start, check, stop · `D` If, while, else
→ **B.** *Targets:* The three parts — today's contrast depends on it.

**Q2.** How many lines does this print?
```python
i = 0
while i < 4:
    print(i)
    i = i + 1
```
`A` 3 · `B` 4 · `C` 5 · `D` Infinite
→ **B.** *Targets:* Off-by-one — `i` is 0, 1, 2, 3.

**Q3.** What makes a loop infinite?
`A` Too many lines · `B` The condition never becomes False · `C` A missing colon · `D` Wrong indentation
→ **B.** *Targets:* Infinite loop cause.

**Q4.** Which part is missing here?
```python
counter = 0
while counter < 3:
    print("Hi")
```
`A` Initialise · `B` Condition · `C` Update · `D` Nothing
→ **C.** *Targets:* Diagnosing by the three parts.

**Q5.** Before writing code, what should you write down?
`A` The input, output and rule · `B` Your name · `C` The answer · `D` Nothing
→ **A.** *Targets:* Session 14's habit.

**Q6.** Which are True about `while` loops? *(MSQ — select all)*
`A` The condition is checked before every pass · `B` The body always runs at least once · `C` The counter must be updated by you · `D` It needs a colon
→ **A, C and D.** *Targets:* Zero-pass loops and manual counters. *Misconception:* picking B is common and it's exactly what `for` will fix.

**Q7.** In a while loop, who updates the counter?
`A` Python, automatically · `B` You, in the loop body · `C` Nobody · `D` The condition
→ **B.** *Targets:* Manual updating. **This is today's hook** — `for` takes that job away. Note the number.

---

## Hook (7–10 min)

Write on the board — the `while` version of printing each letter of a word:

```python
word = "Python"
i = 0
while i < len(word):
    print(word[i])
    i = i + 1
```

> *"That works. Count the things that can go wrong in it — I count four. Wrong starting value. Wrong comparison. Forgetting `len`. Forgetting to update `i`."*

Then type the `for` version underneath:

```python
word = "Python"
for each_char in word:
    print(each_char)
```

Run both. Identical output.

> *"Three lines instead of five, and every single one of those four bugs is now impossible. There's no counter to get wrong because you don't have a counter."*

Tie back to **Q7** — *"You told me *you* update the counter in a while loop. From today, when you know how many times you're going round, Python does it for you."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred from RM structure, confirm against deck -->
Covers: the `for` statement → iterating over a sequence → the string example.

**Beats to emphasise**

- **Write the shape on the board and leave it up:**
  ```
  for <variable> in <sequence>:
      <indented block>
  ```
  Colon and indentation are identical to `if` and `while` — say so. It's the third construct with the same skeleton, and that consistency is worth naming.
- **The loop variable is yours to name.** `for each_char in word` — `each_char` isn't a keyword. Rename it live to `letter`, re-run, same output. Students assume these words are magic.
- **The variable holds a different value each pass.** Run the string example slowly. `P`, then `y`, then `t` — one pass per character, automatically.
- **A string is a sequence.** That's why you can loop over it. Numbers aren't sequences — `for i in 5:` fails. Show it.

**Checkpoint (at 22 min)** — cold-call two students:
> *"In `for letter in "Hi":`, what does `letter` hold on the first pass, and on the second?"*
> **Answer:** `H`, then `i`.

---

## ⚡ Activity 1 — Human Compiler (22–27 min)

### What this activity is

Students **become** the Python interpreter. You point at the loop and ask one student per pass what the loop variable holds and what prints. Nobody describes the whole loop — one pass at a time.

### Why it's here

`for` loops hide the counter, which makes them feel like magic. Walking pass by pass shows there's no magic — just the same sequence of steps, managed automatically.

### Before class

Program on screen, board space to write the passes as a list.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line | Look |
| 0:30–3:00 | Ask for pass 1, 2, 3… one student each | Say variable + output |
| 3:00–4:30 | Second program | Same |
| 4:30–5:00 | Debrief | Listen |

### Say this

> *"You are Python. I'll ask about one pass at a time. Two things each: what's in the variable, and what prints. Don't tell me the whole output."*

### Program 1

```python
word = "Bird"
for each_char in word:
    print(each_char)
```

| Pass | `each_char` | prints |
|---|---|---|
| 1 | `B` | `B` |
| 2 | `i` | `i` |
| 3 | `r` | `r` |
| 4 | `d` | `d` |

Then ask: *"Is there a pass 5?"* — **no.** The sequence ran out. That's what ends a `for` loop, not a condition.

### Program 2

```python
for number in range(3):
    print(number)
```

| Pass | `number` | prints |
|---|---|---|
| 1 | `0` | `0` |
| 2 | `1` | `1` |
| 3 | `2` | `2` |

Press: *"Why no 3?"* — `range(3)` produces 0, 1, 2. Three numbers, starting at 0.

### When it goes wrong

| If… | Do this |
|---|---|
| Student gives the whole output | *"Just pass one. What's in the variable?"* |
| Someone says `range(3)` gives 1, 2, 3 | Very common. Run it. Then write `0 1 2` on the board and count — three numbers. |
| Room finds it easy | Ask what `for c in "":` does. (Nothing — empty sequence, zero passes. Same idea as a while loop that never runs.) |
| Nobody volunteers | Each answer is one character. Say that — the risk is tiny. |

**Common instructor mistake:** filling in passes yourself to speed up. Students must supply each one.

**Cut rule:** Program 1 only.

---

## Classroom Quiz (27–34 min)

5 MCQs from Classroom Quiz A — this session has only one pool. ~80 s each.

**Q1** — `bcc2c417-ab21-46be-a14b-1e99cdbcd1d0` *(REMEMBERING)*
What does `range(n)` generate in Python?
- A sequence of numbers from 1 to n
- ✅ **A sequence of numbers from 0 to n-1**
- A sequence of numbers from n to 0
- A sequence of n random numbers

> *Explanation (platform):* `range(n)` generates a sequence of integers starting from 0 and stops before n, meaning n is not included. For example, `range(3)` produces 0, 1 and 2.

**Q2** — `c075b579-7407-42f0-9064-3d678eb36afd` *(UNDERSTANDING)*
What is the output of:
```python
for i in range(3):
    print(i)
```
- Syntax Error
- `1 2 3`
- ✅ **`0 1 2`**
- `0 1 2 3`

> *Explanation:* **[authored — the platform record has an empty explanation field]** `range(3)` produces 0, 1 and 2 — three numbers starting at 0 and stopping before 3. The loop prints each one on its own line.

**Q3** — `867ec6fd-84fd-4227-99e3-ba79e2963d85` *(APPLYING)*
What will be the output of:
```python
for number in range(5, 8):
    print(number)
```
- ✅ **`5 6 7`**
- `4 5 6`
- `5 6 7 8`
- `4 5 6 7`

> *Explanation (platform):* `range(5, 8)` generates a sequence starting from 5 and stopping before 8 (the end value is not included), resulting in 5, 6 and 7 printed on separate lines.
> **The excluded end again** — same rule as string slicing in Session 8. Call that back; it's the third time this pattern has appeared.

**Q4** — `6973fab9-54e0-4c28-8ac9-becb60f57221` *(APPLYING)*
What will be the output of:
```python
word = "Bird"
for each_char in word:
    print(each_char)
```
- None of the given options
- ✅ **`B` `i` `r` `d`** — each on its own line
- `driB`
- `Bird`

> *Explanation:* **[authored — the platform record has an empty explanation field]** The `for` loop takes one character at a time from the string. Each `print` puts its character on a new line, so the output is B, i, r, d on four separate lines.
> **If they pick `Bird`:** they're thinking of the whole string, not the per-character iteration. Point at Activity 1's table.

**Q5** — `d2edf67e-3774-4094-9eea-67470b39df39` *(ANALYZING)*
What will be the output of:
```python
for i in range(1, 4):
    print('*' * i)
```
- `****` `***` `**`
- `***` `***` `***`
- `*` `* *` `* * *`
- ✅ **`*` `**` `***`**

> *Explanation:* **[authored — the platform record has an empty explanation field]** `range(1, 4)` gives 1, 2 and 3. On each pass `'*' * i` repeats the star that many times, printing one star, then two, then three.
> **This combines string repetition from Session 6 with `for` and `range`.** It's the shape of every pattern problem in tonight's homework — worth the full 80 seconds.

---

## Slide Block B (34–44 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred from RM structure, confirm against deck -->
Covers: `range(n)` → `range(start, end)` → worked examples.

**Beats to emphasise**

- **`range(n)` starts at 0.** Not 1. Say it, write it, then run `range(3)` and count the three numbers on the board.
- **The end is always excluded** — `range(5, 8)` gives 5, 6, 7. Connect it explicitly to string slicing from Session 8: *"Same rule you met with `[3:7]`. Python is consistent about this."*
- **Common gotcha — `range(4, 1)` produces nothing.** Run it. No error, no output, because you can't count up from 4 to 1. Silent, like the `elif` ordering bug in Session 12.
- **`range[3]` with square brackets is a TypeError.** Round brackets call it; square brackets index. Same distinction as Session 8's `message(6:)` error.

**Checkpoint (at 44 min)** — show hands:
> *"How many numbers does `range(2, 6)` produce, and what are they?"*
> **Answer:** Four — 2, 3, 4, 5.

---

## ⚡ Activity 2 — Trace the Table (44–50 min)

### What this activity is

Students draw a table on paper and fill in one row per pass, tracking the loop variable and the output. No laptops. Same format as Session 13's while-loop trace — deliberately, so students can compare the two.

### Why it's here

Pattern problems dominate tonight's 39 coding questions, and every one of them is solved by tracing what the loop variable holds on each pass.

### Before class

Nothing. Students need paper. Draw the empty table on the board so they copy the right columns.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, dictate headers | Draw the table |
| 0:30–3:30 | Walk one pass at a time, pause | Fill a row |
| 3:30–5:00 | Take rows from different students | Report |
| 5:00–6:00 | Debrief | Listen |

### Say this

> *"Paper out, laptops shut. Three columns: `pass`, `i`, and `what prints`. Same as the while-loop table two sessions ago — notice what's missing from it this time."*

### The program

```python
for i in range(1, 5):
    print("*" * i)
```

### The completed table

| Pass | `i` | prints |
|---|---|---|
| 1 | 1 | `*` |
| 2 | 2 | `**` |
| 3 | 3 | `***` |
| 4 | 4 | `****` |

**No pass 5** — `range(1, 5)` stops before 5.

### The key moment

Ask what's missing compared with the Session 13 table:

> *"Two sessions ago this table had a column for the condition and a column for the counter update. Where did they go?"*

**Answer:** `range` handles both. There's no condition to check and no counter to update — that's the entire benefit of `for`.

Then press on the last row: *"Why is there no pass 5?"* — `range(1, 5)` produces 1, 2, 3, 4. The end is excluded.

### When it goes wrong

| If… | Do this |
|---|---|
| Students add a pass 5 | *"How many numbers does `range(1, 5)` give? Count them."* |
| Someone writes `*` counts wrong | Have them count the stars aloud per row. It's a repetition, not a calculation. |
| Room finds it easy | Ask them to predict `range(4, 0, -1)`. Don't teach the step argument — just note it exists. |
| It's dragging | Passes 1 and 4 only. |

**Common instructor mistake:** walking the passes too fast. Five seconds after each — students are writing.

**Cut rule:** Passes 1 and 4.

---

## ⚡ Activity 3 — Live Coding: Pick the Right Loop (50–57 min)

### What this activity is

You're at the keyboard on the projector; students dictate. Unlike previous live-coding blocks, the decision they're making is **which loop to use** — not just how to write it.

### Why it's here

Students now know two loops and will default to whichever they saw most recently. This gives them a rule for choosing.

### Before class

Empty file, font ≥18pt. Board space for a two-column comparison.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line | Listen |
| 0:30–3:00 | Task 1 — take the choice, then the code | Choose + dictate |
| 3:00–5:00 | Task 2 — take the choice, then the code | Choose + dictate |
| 5:00–7:00 | Build the rule on the board, debrief | Contribute |

### Say this

> *"Two tasks. Before any code, I want one word from you: `for` or `while`. Then tell me why. Then we write it."*

### Task 1 — print each character of a name

> *"Ask the user for their name, then print each letter on its own line."*

**Expected choice: `for`.** We know the sequence — the string itself.

```python
name = input()
for letter in name:
    print(letter)
```

### Task 2 — keep asking until the user types `stop`

> *"Keep asking the user for a word until they type `stop`."*

**Expected choice: `while`.** We have no idea how many times — it depends on the user.

```python
word = input()
while word != "stop":
    print(word)
    word = input()
```

**If the room tries `for` here, let them try.** They'll get stuck on what to put after `in` — and that's the lesson. There's no sequence to loop over.

### Build the rule on the board

Take the wording from the class:

| Use `for` when | Use `while` when |
|---|---|
| You know the sequence or how many times | You don't know how many times |
| Looping over a string or a range | Repeating until something happens |
| Python manages the counter | You manage the counter |

### When it goes wrong

| If… | Do this |
|---|---|
| They pick `for` for task 2 | Best case. Let them try, let it stall, then ask what goes after `in`. |
| They pick `while` for task 1 | Also fine — it works. Write both, then ask which has fewer things to get wrong. |
| Nobody commits to a choice | Make it a vote: *"Hands for `for`. Hands for `while`."* |
| Running long | Task 2 only — the choice matters more than task 1's code. |

**Common instructor mistake:** giving the rule before they attempt the tasks. The rule only means something after they've felt task 2 resist a `for` loop.

**Cut rule:** Task 2 and the board rule.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — before anyone leaves:

> Write the output of each:
> `for i in range(3): print(i)` and `for i in range(2, 5): print(i)`
> Then: which loop would you use to print every character of a word?
> **Answers:** `0 1 2` · `2 3 4` · `for`.

**Homework**

| Task | Unit |
|---|---|
| Coding Practice (6 q) | `ad396947-a6fc-4dc5-b3ec-221c6a4e9d0d` |
| Coding Practice - 1 (11 q) | `8de7fd4f-3c84-4b46-863e-d84c15c03a92` |
| Coding Practice - 2 (11 q) | `7c7f921a-2eed-4e2e-b98a-5580be1d3561` |
| Coding Practice - 3 (11 q) | `52d26bc5-7e81-4e3d-a4fd-63046263820b` |
| MCQ Practice — 84 questions | `513f4a5f-5ce9-44c9-803e-e89155504772` |
| RM — For Loop | `384585b9-ff4a-43a6-884a-e918abf0eaeb` |

> ⚠️ **39 coding problems across four sets — by far the largest homework of the course so far.** Say this explicitly and set a realistic target: *"Nobody is finishing all thirty-nine tonight. Do the first set of six, then start set one. If you're stuck, trace the table."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `range(3)` gives 1, 2, 3 | Counting starts at 1 in life | Activity 1 program 2 — count 0, 1, 2 on the board |
| `range(5, 8)` includes 8 | The end number is written there | Quiz Q3, connected back to slicing |
| The loop variable name is a keyword | It appears in every example | Block A — rename it live, same output |
| `for` loops need a counter update | `while` needed one | Activity 2 — the missing columns |
| `range(4, 1)` counts backwards | It reads like a range | Block B — run it, no output, no error |
| `for` replaces `while` entirely | It's newer and shorter | Activity 3 task 2 — no sequence to loop over |
| `range[3]` works | Brackets look interchangeable | Block B — TypeError, same as `message(6:)` |

---

## Instructor Notes

- **This session is a relief after 13.** Say so. Students who struggled with `while` will find `for` genuinely easier, and naming that rebuilds confidence at exactly the right moment.
- **The excluded end appears for the third time** — string slicing (Session 8), and now `range` twice. Point at the pattern explicitly: Python consistently stops *before* the end value. Students who see it as one rule stop re-learning it.
- **Activity 3 is the session's real content.** Anyone can write a `for` loop after Block A; choosing between two loops is the actual skill. If time is short, cut Activity 2 — the trace is a rehearsal, Activity 3 is the point.
- **⚠️ Only one classroom quiz pool** (A, 56 questions) instead of the usual two. All five questions above come from it. Fine for one session, but worth flagging to the content team alongside Session 8's mismatch.
- **⚠️ 39 coding problems across four sets.** Set an explicit target or students will look at the number and not start at all — the exact behaviour the practice playbook exists to prevent. Six from the first set is a fair night's work.
- **Three more empty `answer_explanation` fields here** — `c075b579`, `6973fab9`, `d2edf67e`. Authored and labelled. That makes **10 authored explanations** across the questions quoted in these 15 plans. The wider gap is much bigger: **409 of the 1,855 questions in these sessions' pools (22%) have no explanation at all.** Worth a content audit rather than one-off fixes.
- **Sessions 16+ are not planned.** Session 16 is *Comparing Strings & Naming Variables*; the sequence continues through nested loops, lists, functions and OOP.
