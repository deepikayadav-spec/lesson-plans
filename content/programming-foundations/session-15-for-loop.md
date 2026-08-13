# Session 15 — For Loop

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Loops · **Prerequisite** Sessions 13–14
**Session type** Concept lecture · **Format** 50-min recalibrated, 2 ALS activities, Classroom Quiz mandatory (never cut, runs last)

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

## Classroom Settling (0–3 min) · Buffer — not instructional

Projector on, deck loaded, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** state the MCQ Practice completion number since last session. Target is 80%.

5 questions on **Sessions 13–14**. ~45 s each, project the distribution, never name individuals.

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

**Q3.** Which part is missing here?
```python
counter = 0
while counter < 3:
    print("Hi")
```
`A` Initialise · `B` Condition · `C` Update · `D` Nothing
→ **C.** *Targets:* Diagnosing by the three parts.

**Q4.** Which are True about `while` loops? *(MSQ — select all)*
`A` The condition is checked before every pass · `B` The body always runs at least once · `C` The counter must be updated by you · `D` It needs a colon
→ **A, C and D.** *Targets:* Zero-pass loops and manual counters. *Misconception:* picking B is common and it's exactly what `for` will fix.

**Q5.** In a while loop, who updates the counter?
`A` Python, automatically · `B` You, in the loop body · `C` Nobody · `D` The condition
→ **B.** *Targets:* Manual updating. **This is today's hook** — `for` takes that job away. Note the number.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–11 min)

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

Tie back to **Q5** — *"You told me *you* update the counter in a while loop. From today, when you know how many times you're going round, Python does it for you."*

---

## Slide Block A (11–18 min) — DELIVER SLIDES AS-IS

**Verified against the deck** (*"Copy of 5.2 For Loop"*). Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1–2 | Welcome · Recap | |
| 3 | **Introduction to Loops — Loops** | "In Python there are **two primary ways** for looping" → **While Loop** · **For Loop** |
| 4 | **Daily Challenge — Identify The Mistake** | A `while` loop printing each character, with `while counter < (length_of_a - 1)` — input `Python`, expected output all six letters. The `- 1` is the bug |
| 5 | **Agenda** | For Loop *(Sequence, Syntax)* → Range *(Sequence of Numbers)* → Code Walkthrough *(Possible Mistakes)* |
| 6 | **For Loop — Iterate Over Characters** | `word = "Python"` · `for each_char in word:` · `print(each_char)`, with a dashed loop-back arrow and the note **"Initialization, termination condition and updation are not required"** |
| 7+ | **For Loop** | Stepping through, with a purple **`each_char` box** showing `P`, then `y`, then `t`… and an arrow pointing at the current character in `"Python"`, output building alongside |

**Beats to emphasise**

- **Slide 3 frames the session as a choice between two tools**, which is exactly ALS Activity 2's job. Say it now and call back to it later.
- **Slide 4 is a `while`-loop bug hunt on the very content of Session 13.** A free retrieval-practice beat and a perfect bridge — the off-by-one `- 1` means the last character never prints. Take answers before revealing.
- **⭐ Slide 6's note is the single most important line in the deck** — *"Initialization, termination condition and updation are not required."* Point at it and say it twice.
- **Write the shape on the board and leave it up:**
  ```
  for <variable> in <sequence>:
      <indented block>
  ```
  Colon and indentation are identical to `if` and `while` — say so.
- **The loop variable is yours to name.** `for each_char in word` — `each_char` isn't a keyword. Rename it live to `letter`, re-run, same output.
- **A string is a sequence.** That's why you can loop over it. Numbers aren't sequences — `for i in 5:` fails. Show it.

**Checkpoint (at 18 min)** — 10 s silent think, cold-call two students:
> *"In `for letter in "Hi":`, what does `letter` hold on the first pass, and on the second?"*
> **Answer:** `H`, then `i`.

---

## ⚡ ALS Activity 1 — Round-Robin Pass Trace: Human Compiler (18–24 min)

**ALS format:** Round-Robin Pass Trace — one student per *pass* of the loop (not per line), naming the variable's value and what prints. Chosen right after Slide A's animated box because `for` loops hide the counter and can feel like magic; walking pass by pass, unaided, shows there's no magic — just an automatic sequence.

**Setup line:**
> *"You are Python. I'll ask about one pass at a time. Two things each: what's in the variable, and what prints. Don't tell me the whole output."*

**Program 1**

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

**Program 2** (if time allows)

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

**Debrief line:**
> *"No condition, no counter update, and it still knows exactly when to stop. The sequence itself decides — that's the whole trick."*

**Cut rule:** Program 1 only.

---

## Slide Block B (24–31 min) — DELIVER SLIDES AS-IS

**Verified against the deck.** Slides, in order:

| # | Slide | Content |
|---|---|---|
| 8+ | **Range** | `range(n)` and `range(start, end)` worked examples |
| 9+ | **Right Angle Triangular Pattern — Input / Output Format** | Input `3` → output `*` / `* *` / `* * *`, with the input format stated: *"First line will contain a positive integer"* |
| 10+ | **Code Walkthrough** | Building the pattern program |
| last | **Daily Challenge — Identify The Mistake** | `a = input()` · `len_of_a = len(a)` · `b = ""` · `for i in range(1, len_of_a):` · `b = b + "-" + a[i]` · `print(b)` — input `Python`, expected `P-y-t-h-o-n`. **Two bugs:** `range(1, …)` skips index 0, and the separator logic puts a leading `-` |

**Beats to emphasise**

- **`range(n)` starts at 0.** Not 1. Say it, write it, then run `range(3)` and count the three numbers on the board.
- **The end is always excluded** — `range(5, 8)` gives 5, 6, 7. Connect it explicitly to string slicing from Session 8.
- **Common gotcha — `range(4, 1)` produces nothing.** Run it. No error, no output. Silent, like the `elif` ordering bug in Session 12.
- **`range[3]` with square brackets is a TypeError.** Round brackets call it; square brackets index.

**Pattern-trace beat (2 min):** put `for i in range(1, 5): print("*" * i)` on screen — *"how many passes, and what prints on each?"* 10 s silent, then reveal: 4 passes, `*` `**` `***` `****`, no pass 5 since `range(1, 5)` stops before 5. Then run the deck's own **closing "Identify the Mistake"** challenge live — the `P-y-t-h-o-n` dash-join with two bugs (`range(1, …)` skips index 0; leading `-`). Take fixes from the room before revealing.

**Checkpoint (at 31 min)** — show hands:
> *"How many numbers does `range(2, 6)` produce, and what are they?"*
> **Answer:** Four — 2, 3, 4, 5.

---

## ⚡ ALS Activity 2 — Guided Decision Dictation: Pick the Right Loop (31–38 min)

**ALS format:** Guided Decision Dictation — students commit to a choice (`for` or `while`) *before* any code gets written, then dictate. Different from every other activity this session: the skill being tested isn't syntax, it's judgment about which tool fits. **This is the session's real content** — anyone can write a `for` loop after Slide Block A; choosing between two loops is the actual transferable skill.

**Setup line:**
> *"Two tasks. Before any code, I want one word from you: `for` or `while`. Then tell me why. Then we write it."*

**Task 1 — print each character of a name**
> *"Ask the user for their name, then print each letter on its own line."*

**Expected choice: `for`.** We know the sequence — the string itself.

```python
name = input()
for letter in name:
    print(letter)
```

**Task 2 — keep asking until the user types `stop`**
> *"Keep asking the user for a word until they type `stop`."*

**Expected choice: `while`.** We have no idea how many times — it depends on the user.

```python
word = input()
while word != "stop":
    print(word)
    word = input()
```

**If the room tries `for` here, let them try.** They'll get stuck on what to put after `in` — and that's the lesson. There's no sequence to loop over.

**Build the rule on the board**, taking the wording from the class:

| Use `for` when | Use `while` when |
|---|---|
| You know the sequence or how many times | You don't know how many times |
| Looping over a string or a range | Repeating until something happens |
| Python manages the counter | You manage the counter |

**Debrief line:**
> *"The rule only means something because you just felt task 2 resist a `for` loop. That resistance is the actual lesson — everything else today was syntax."*

**Cut rule:** Task 2 and the board rule — the choice matters more than task 1's code.

---

## Classroom Quiz (38–45 min) · ALS: Individual Answer → Reveal

> 🔒 **Mandatory block — do not cut, do not shorten, do not skip under time pressure.** Runs last, right before the Exit Ticket. This session has only one classroom quiz pool (A) instead of the usual two. Protect these 7 minutes by using the cut rules everywhere else first.

Every question below is run ALS-style: **individual silent answer first, then explanation.**

5 MCQs from Classroom Quiz A. ~85 s each.

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
> **If they pick `Bird`:** they're thinking of the whole string, not the per-character iteration. Point at ALS Activity 1's table.

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
> **This combines string repetition from Session 6 with `for` and `range`.** It's the shape of every pattern problem in tonight's homework — worth the full 85 seconds.

---

## Exit Ticket + Quiz Push (45–48 min)

**Exit ticket** (~30 s) — before anyone leaves:

> Write the output of each:
> `for i in range(3): print(i)` and `for i in range(2, 5): print(i)`
> Then: which loop would you use to print every character of a word?
> **Answers:** `0 1 2` · `2 3 4` · `for`.

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Open MCQ Practice. Everyone, this room, right now — attempt the first 3 questions before you leave your seat. 84 questions here."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 16's warm-up."*

**Remaining homework**

| Task | Unit |
|---|---|
| Coding Practice (6 q) | `ad396947-a6fc-4dc5-b3ec-221c6a4e9d0d` |
| Coding Practice - 1 (11 q) | `8de7fd4f-3c84-4b46-863e-d84c15c03a92` |
| Coding Practice - 2 (11 q) | `7c7f921a-2eed-4e2e-b98a-5580be1d3561` |
| Coding Practice - 3 (11 q) | `52d26bc5-7e81-4e3d-a4fd-63046263820b` |
| MCQ Practice — 84 questions *(started in class above — finish the rest)* | `513f4a5f-5ce9-44c9-803e-e89155504772` |
| RM — For Loop | `384585b9-ff4a-43a6-884a-e918abf0eaeb` |

> ⚠️ **39 coding problems across four sets — by far the largest homework of the course so far.** Say this explicitly and set a realistic target: *"Nobody is finishing all thirty-nine tonight. Do the first set of six, then start set one. If you're stuck, trace the table."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `range(3)` gives 1, 2, 3 | Counting starts at 1 in life | ALS Activity 1 program 2 — count 0, 1, 2 on the board |
| `range(5, 8)` includes 8 | The end number is written there | Quiz Q3, connected back to slicing |
| The loop variable name is a keyword | It appears in every example | Slide Block A — rename it live, same output |
| `for` loops need a counter update | `while` needed one | ALS Activity 1 — no condition or update column |
| `range(4, 1)` counts backwards | It reads like a range | Slide Block B — run it, no output, no error |
| `for` replaces `while` entirely | It's newer and shorter | ALS Activity 2 task 2 — no sequence to loop over |
| `range[3]` works | Brackets look interchangeable | Slide Block B — TypeError, same as `message(6:)` |

---

## Instructor Notes

- ✅ **Verified against the real deck** (*"Copy of 5.2 For Loop"*). Slide Blocks A and B list the actual slides in order.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **⭐ Slide 6's note — *"Initialization, termination condition and updation are not required"*** — is the deck's answer to why `for` exists, phrased in Session 13's own vocabulary. Highest-value line in the session.
- **The deck contains two "Identify The Mistake" challenges.** The first (slide 4) runs as posed in Slide Block A. The closing one is folded into Slide Block B's pattern-trace beat rather than getting its own activity slot — it needs no wrapper, it works run as posed.
- **Two ALS activities this session:** Activity 1 is Round-Robin Pass Trace (Slide A's animation, handed to students unaided), Activity 2 is Guided Decision Dictation — **the session's real content**, since choosing between `for` and `while` is the actual transferable skill. The original Trace the Table activity is folded into Slide Block B's pattern-trace beat instead of running as its own block, per the original plan's own suggestion that the closing daily-challenge slide can substitute for it.
- **The Classroom Quiz runs last, right before the Exit Ticket** — never cut, never shortened. Only one pool (A, 56 questions) this session instead of the usual two.
- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair.** Target is 80% platform MCQ attempt rate, currently ~33%.
- **This session is a relief after 13.** Say so. Students who struggled with `while` will find `for` genuinely easier.
- **The excluded end appears for the third time** — string slicing (Session 8), and now `range` twice. Point at the pattern explicitly.
- **⚠️ 39 coding problems across four sets.** Set an explicit target or students will look at the number and not start at all. Six from the first set is a fair night's work.
- **Three empty `answer_explanation` fields here** — `c075b579`, `6973fab9`, `d2edf67e`. Authored and labelled above.
- **Sessions 16+ are not planned.** Session 16 is *Comparing Strings & Naming Variables*; the sequence continues through nested loops, lists, functions and OOP.
