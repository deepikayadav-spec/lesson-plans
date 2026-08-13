# Session 12 — Nested Conditional Statements

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Conditional Statements · **Prerequisite** Session 11
**Session type** Concept lecture · **Format** 50-min recalibrated, 2 ALS activities, Classroom Quiz mandatory (never cut, runs last)

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Nested Conditional Statements | `595fd9ac-95a9-4e1b-91cb-ae0d66006e30` |
| RM — Nested Conditional Statements | `5bf28868-119e-4d0b-beb2-f3eb5a2f29f4` |
| Classroom Quiz A (30 q — nesting) | `72145a83-fe6b-4d15-9dce-aa4b938ba390` |
| Classroom Quiz B (31 q — `elif`) | `f32e2390-1c97-4cdf-ba9c-fade1cc0159f` |
| MCQ Practice (93 q) | `2932ccef-5438-4cf3-b05b-677c8fcce424` |
| Coding Practice (12 q) | `d2c22172-d19f-4eb4-a7b1-198d2a2faae3` |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Write an `if` inside another `if` with correct indentation levels. *(APPLYING)*
2. Determine which block a line belongs to by reading its indentation. *(ANALYZING)*
3. Use `elif` to check several conditions in sequence. *(APPLYING)*
4. State that only the first true branch in an `if`/`elif`/`else` chain runs. *(UNDERSTANDING)*
5. Explain why `elif` cannot appear after `else`. *(UNDERSTANDING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Projector on, deck loaded, editor with indent guides turned on, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** state the MCQ Practice completion number since last session. Target is 80%.

5 questions on **Session 11**. ~45 s each, project the distribution, never name individuals.

**Q1.** What does an `if` statement need at the end of its condition line?
`A` A semicolon · `B` A colon · `C` Nothing · `D` Brackets
→ **B.** *Targets:* Colon.

**Q2.** In an if-else, how many blocks run?
`A` Both · `B` Exactly one · `C` Neither · `D` Depends
→ **B.** *Targets:* Exactly one branch.

**Q3.** `marks = 40`. What does `if marks >= 40:` do?
`A` Runs the if block · `B` Runs the else block · `C` Error · `D` Nothing
→ **A.** *Targets:* `>=` includes the boundary. *Misconception:* B means the boundary case from last session didn't stick.

**Q4.** Can code sit between an `if` block and its `else`?
`A` Yes · `B` No — SyntaxError · `C` Only comments · `D` Only prints
→ **B.** *Targets:* `else` must immediately follow.

**Q5.** What decides whether a line is inside an `if` block?
`A` Its position in the file · `B` Its indentation · `C` The colon · `D` The condition
→ **B.** *Targets:* Indentation. **Today's whole session** — nesting is just indentation at two levels. Note the number.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–11 min)

> *"Last session your programs could answer one question. But some decisions need a second question — and the second one only makes sense if the first was yes."*

Write on the board:

```
Did the team win more than 8 matches?
    ...and did they also score more than 20 goals?
```

> *"You don't ask the second question unless the first one was true. That's a nested condition."*

Type and run with `10` then `22`:

```python
matches_won = int(input())
goals = int(input())
if matches_won > 8:
    if goals > 20:
        print("Hurray")
    print("Winner")
```

Then run again with `10` and `18` → only `Winner`.
Then `5` and `30` → nothing at all.

> *"Three different outputs from the same program. Look at the indentation — it's the only thing telling Python which question sits inside which."*

Tie back to **Q5** — *"You said indentation decides what's inside a block. Today that goes two levels deep, and it's the entire mechanism."*

---

## Slide Block A (11–18 min) — DELIVER SLIDES AS-IS

**Verified against the deck** (*"Copy of 4.3 Nested Conditional Statements"*). Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1–3 | Welcome · Recap | |
| 4 | **Agenda** | Nested Conditions *(Indentation)* → Else If Statement *(if-elif-else)* |
| 5 | **Nested Conditions** — the structure diagram | `if condition A:` → Block 1, `if condition B:` → Block 2, Block 3, then Block 4 outside. **Each block ticked or crossed as the conditions resolve**, with Block 4 labelled *"Will always execute"* |
| 6+ | **Nested Conditions** | Worked code examples |
| 7+ | **Possible Mistakes** | `is_a_greatest` / `is_b_greatest` three-number example → **`NameError: name 'is_b_greatest' is not defined`**, with the offending block highlighted in red |

**Beats to emphasise**

- **Slide 5 is a better teaching device than any code.** It's an abstract diagram with dashed boxes showing which block belongs to which condition, and green ticks / red crosses showing what runs. **Use its vocabulary — Block 1, Block 2, Block 3, Block 4.**
- **"Block 4 will always execute"** is called out explicitly on the slide. Point at it.
- **Slide 7's `NameError`** — a variable defined *inside* the `else` block, used by an `if` at the outer level, so when `else` doesn't run the variable never exists. Combines Session 5's NameError with today's indentation. Worth real time.

**Checkpoint + Quick Trace (at 18 min, ~2 min)** — 10 s silent think, cold-call two students for the checkpoint, then a compressed line-by-line trace (folded in here to protect the schedule):
> *Checkpoint (using the slide's own labels):* *"If condition A is True and condition B is False, which blocks run?"* Answer: Block 1, Block 3 and Block 4. Block 2 is skipped.
> *Quick trace:* re-run the hook's program with `matches_won = 5` — *"how many lines does Python just skip in one go?"* Answer: three, because they were all inside one false block.

---

## ⚡ ALS Activity 1 — Silent Diagnose, Named Reveal: Spot the Bug (18–24 min)

**ALS format:** Silent Individual Diagnose, then Named Reveal — everyone diagnoses all four snippets alone before any answer is taken from a specific student. Chosen because every trap here is either an indentation slip or an ordering mistake, and the ordering one produces *no error at all* — the only way to catch it is to have actually looked, alone, not to have heard someone else catch it first.

**Setup line:**
> *"Four snippets. Tell me what's wrong and what it's called. One of these does not crash. Ninety seconds, silent."*

```python
# 1
if True:
if False:
    print("Inner")
```
```python
# 2
x = 5
if x > 10:
    print("Big")
elif:
    print("Small")
```
```python
# 3
if False:
    print("If")
else:
    print("Else")
elif True:
    print("Elif")
```
```python
# 4
marks = 95
if marks > 30:
    print("Pass")
elif marks > 90:
    print("Distinction")
```

**Answers**

| # | Diagnosis | Fix |
|---|---|---|
| 1 | `IndentationError` — inner `if` not indented, so the outer block is empty | Indent the inner `if` by four spaces |
| 2 | `SyntaxError` — `elif` has no condition | `elif x > 3:` or use `else:` |
| 3 | `SyntaxError` — `elif` cannot come after `else` | Move the `elif` above the `else` |
| 4 | **No error.** Prints `Pass`. A 95-mark student never gets `Distinction` | Put `marks > 90` first |

**Snippet 4 is the session.** Ask directly:
> *"A student scores 95 and the program says Pass. Nothing crashed. Nobody gets an error email. How long does that bug live in production?"*

**Debrief line:**
> *"Three of these crash and tell you where. The fourth just quietly gives the wrong answer to a top student. That's the one worth losing sleep over."*

**Cut rule:** Do 1 and 4. Snippet 4 is non-negotiable.

---

## Slide Block B (24–31 min) — DELIVER SLIDES AS-IS

**Verified against the deck.** Slides, in order:

| # | Slide | Content |
|---|---|---|
| 8 | **Elif Statement** — the structure diagram | `if condition A:` **False** → Block 1 ✗ · `elif condition B:` **False** → Block 2 ✗ · `else:` → Block 3 ✓. Same tick/cross visual language as slide 5 |
| 9+ | **Elif** | Worked code examples with `%` divisibility checks |
| last | Next Session | *Loops* |

**Beats to emphasise**

- **Slide 8 mirrors slide 5 deliberately** — same diagram grammar, same ticks and crosses. Say so: *"Same picture, different construct. Nesting goes inwards; elif goes downwards."*
- **Exactly one block runs in an `if`/`elif`/`else` chain.** The diagram shows it — two crosses and one tick.
- **`%` appears in the deck's elif examples.** Students met `%` only as a passing mention in Session 11's exit ticket. **Give it one sentence before slide 9:** `%` gives the remainder, `n % 10 == 0` means divisible by 10.

> ⚠️ **The deck never shows a mis-ordered `elif` chain going silently wrong.** That's **Quiz Q5 and ALS Activity 2's core idea** — the most important thing in the session. Type it live:
> ```python
> x = 100
> if x > 3:      print("Above 3")     # this wins
> elif x > 50:   print("Above 50")    # never checked
> ```

**Checkpoint (at 31 min)** — show hands:
> *"Three `elif` conditions are all true. How many blocks run?"*
> **Answer:** One. The first.

---

## ⚡ ALS Activity 2 — Choral Prediction → Reveal (31–38 min)

**ALS format:** Choral Prediction — the whole room predicts out loud together before each run. Chosen for the closing activity because the pairing of snippets 1 and 2 (same values, order swapped) lands hardest as a shared "we were all wrong together" moment, not an individual correction.

**Setup line:**
> *"Everyone answers out loud together before I hit run. Say it with confidence even if you're guessing — a wrong guess out loud is worth ten right answers in your head."*

```python
x = 100                     # 1
if x > 3:
    print("Above 3")
elif x > 50:
    print("Above 50")
```
```python
x = 100                     # 2
if x > 50:
    print("Above 50")
elif x > 3:
    print("Above 3")
```
```python
n = 7                       # 3
if n > 5:
    print("A")
if n > 3:
    print("B")
```

| # | Output | Why |
|---|---|---|
| 1 | `Above 3` | First true condition wins — the `elif` is never checked |
| 2 | `Above 50` | Same values, order reversed, different answer |
| 3 | `A` then `B` | **Two separate `if`s** — both run. Not a chain. |

**Snippets 1 and 2 are the pair that matters** — run them back to back and let the contrast land without commentary first.

**Snippet 3 is the sting.** Students expect one output because it looks like a chain. Two separate `if` statements are independent; only `elif` makes them exclusive.

**Debrief line:**
> *"Same numbers, different order, different answer — with no error to warn you. That's the single most important thing you'll take from this session."*

**Cut rule:** Snippets 1 and 2 are non-negotiable — they're the pair. Drop 3 first if running late.

---

## Classroom Quiz (38–45 min) · ALS: Individual Answer → Reveal

> 🔒 **Mandatory block — do not cut, do not shorten, do not skip under time pressure.** Runs last, right before the Exit Ticket. Two questions on nesting, three on `elif`. Protect these 7 minutes by using the cut rules everywhere else first.

Every question below is run ALS-style: **individual silent answer first, then explanation.**

**Q1** — `04cc638e-9810-4985-8ee6-1246569c31c6` *(Quiz A · APPLYING)*
What will be the output of:
```python
matches_won = 9
goals = 21

if matches_won > 8:
    if goals > 20:
        print("Hurray")
    print("Winner")
```
- ✅ **`Hurray` then `Winner`**
- `Winner`
- No output
- `Hurray`

> *Explanation:* **[authored — the platform record has an empty explanation field]** `9 > 8` is True, so the outer block runs. Inside it, `21 > 20` is also True, so `Hurray` prints. `print("Winner")` sits at the outer level, so it runs too.

**Q2** — `d15e25f4-7ab5-4a2c-b328-23b8b2653761` *(Quiz A · APPLYING)*
How can the error in this snippet be fixed?
```python
matches_won = 10
goals = 18

if matches_won > 8:
if goals > 20:
        print("Hurray")
    print("Winner")
```
- Change the print statement to uppercase
- There is no need to fix anything
- Remove the nested if statement
- ✅ **Adding four space indentation to `if goals > 20`**

> *Explanation:* **[authored — the platform record has an empty explanation field]** The inner `if` is at the same indentation level as the outer one, so Python sees the outer `if` block as empty and raises an IndentationError. Indenting the inner `if` by four spaces puts it inside the outer block.

**Q3** — `e88f6d5e-1db5-45b1-9042-4b9e923d65d0` *(Quiz B · REMEMBERING)*
What is the purpose of the `elif` statement?
- To define the final condition to be checked
- ✅ **To provide an alternative condition if the `if` condition is False**
- To terminate the conditional structure
- To execute regardless of the previous conditions

> *Explanation:* **[authored — the platform record has an empty explanation field]** `elif` lets you test another condition when the previous one was False. It sits between `if` and `else`, and you can have as many as you need.

**Q4** — `0d81fbb5-337a-4e05-8a04-f2b249f6804c` *(Quiz B · APPLYING)*
Which `elif` block will be executed?
```python
x = 5
if x > 10:
    print("Greater than 10")
elif x > 7:
    print("Greater than 7")
elif x > 3:
    print("Greater than 3")
else:
    print("3 or less")
```
- Both elif blocks
- `elif x > 7`
- No elif blocks will be executed
- ✅ **`elif x > 3`**

> *Explanation (platform):* `x` is 5. The first `if` condition `x > 10` is False, so it is skipped. The first `elif` condition `x > 7` is also False, so it is skipped. The second `elif` condition `x > 3` evaluates to True since 5 > 3.

**Q5** — `56d3452e-05be-40ef-8052-6bf25021f32f` *(Quiz B · ANALYZING)*
If multiple `elif` conditions evaluate to true, which block executes?
- All true `elif` blocks will be executed in sequence
- ✅ **Only the first true `elif` block will be executed**
- Only the last true `elif` block will be executed
- No `elif` blocks will be executed

> *Explanation (platform):* Python checks each condition in order from top to bottom. As soon as it finds the first condition that evaluates to True, it executes that block and skips all remaining ones.
> **This is the session's most important idea.** Order matters. A chain written in the wrong order produces silently wrong results — no error, just the wrong branch.

---

## Exit Ticket + Quiz Push (45–48 min)

**Exit ticket** (~30 s) — before anyone leaves:

> `score = 95`. Write an `if`/`elif`/`else` chain that prints `Distinction` above 90, `Pass` above 40, and `Fail` otherwise — **in the correct order.**
> **Answer:** `if score > 90:` → `Distinction`, `elif score > 40:` → `Pass`, `else:` → `Fail`. Any chain with `> 40` first is wrong.

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Open MCQ Practice. Everyone, this room, right now — attempt the first 3 questions before you leave your seat."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 13's warm-up."*

**Remaining homework**

| Task | Unit |
|---|---|
| Coding Practice — 12 problems | `d2c22172-d19f-4eb4-a7b1-198d2a2faae3` |
| MCQ Practice — 93 questions *(started in class above — finish the rest)* | `2932ccef-5438-4cf3-b05b-677c8fcce424` |
| RM — Nested Conditional Statements | `5bf28868-119e-4d0b-beb2-f3eb5a2f29f4` |

> *"Two rules. Count your indentation — every nesting level is four more spaces. And put your most specific condition first, or your chain will quietly give the wrong answer."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| All true branches run | Reading it as a list of checks | Quiz Q5 and ALS Activity 2 snippet 1 |
| `elif` order doesn't matter | The conditions look independent | ALS Activity 2 snippets 1 and 2, back to back |
| Consecutive `if`s behave like `if`/`elif` | They look the same on the page | ALS Activity 2 snippet 3 — both run |
| `elif` can go after `else` | `else` feels like a divider | ALS Activity 1 snippet 3 — SyntaxError |
| Nesting needs new syntax | It looks like a new construct | Slide Block A — it's the same `if`, indented further |
| A line inside an outer block is inside the inner one too | Indentation levels blur | The quick-trace beat — `print("Winner")` at the outer level |
| A wrong `elif` order will error | Errors are their feedback | ALS Activity 1 snippet 4 — runs fine, wrong result |

---

## Instructor Notes

- ✅ **Verified against the real deck** (*"Copy of 4.3 Nested Conditional Statements"*). Slide Blocks A and B list the actual slides in order.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **The deck's two structure diagrams (slides 5 and 8) are its strongest assets.** Both use the same tick/cross grammar. Teach from the diagrams and map code onto them.
- **Two ALS activities this session:** Activity 1 is Silent Diagnose → Named Reveal, Activity 2 is Choral Prediction → Reveal, saved for the session's single most important contrast (snippets 1 and 2). The original Human Compiler activity is folded into a 2-minute quick-trace beat at the end of Slide Block A's checkpoint.
- **The Classroom Quiz runs last, right before the Exit Ticket** — never cut, never shortened.
- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair.** Target is 80% platform MCQ attempt rate, currently ~33%.
- ⚠️ **The deck never shows a mis-ordered `elif` chain**, which is Quiz Q5 and ALS Activity 2's point. Live-typing script is in Slide Block B. **Worth raising with the content team.**
- **This session is two topics** — nesting (Block A, ALS Activity 1) and `elif` (Block B, ALS Activity 2). `elif` is usually the better answer. Say that explicitly; students otherwise nest three levels deep in the homework.
- **Turn on indent guides in your editor** before this session.
- **The single most valuable moment is ALS Activity 2 snippets 1 and 2.** Same values, order swapped, different output, no error. Never cut that pair.
- **Four questions in this session's quiz have empty `answer_explanation` fields on the platform.** The explanations above are authored and labelled.
- **Note the RM has a formatting bug** — one line in its three-way example uses a tab where the rest use spaces. If you copy code from the RM, retype the indentation rather than pasting.
- **Sessions 13–15 are loops.** Students who still can't count indentation levels will not cope. If ALS Activity 1 goes badly, use the Quiz Push time for indentation drilling rather than the coding set.
