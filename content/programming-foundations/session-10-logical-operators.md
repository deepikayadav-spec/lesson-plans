# Session 10 — Logical Operators

**Duration** 60 min · **Topic** Operators · **Prerequisite** Session 9
**Session type** Concept lecture · ⚠️ **No video and no slide deck exist for this session** — see Instructor Notes.

**Platform units**

| Resource | Unit ID |
|---|---|
| RM — Logical Operators | `35dfbabb-e989-46fd-8a1f-12f1a158cf84` |
| Classroom Quiz A (31 q — `and`) | `f6c5abb4-51cf-46de-925f-6ed6e80ca768` |
| Classroom Quiz B (26 q — `or`) | `d0f95f02-2d71-4743-86e9-c6da6d42b792` |
| Classroom Quiz C (29 q — `not`) | `54dd062f-30f7-4103-8a51-a65fed0f00e3` |
| MCQ Practice (98 q) | `bea78a11-7247-4662-8be4-68da6dda4251` |
| Coding Practice (15 q) | `2352eee0-7db2-4189-b245-bd0246d141ed` |

> ⚠️ **You have no deck.** The two "Slide Block" sections are **Teaching Blocks** — board work and live typing, built from the reading material. Everything you need is written out below.

---

## Learning Objectives

By the end of this session, students will be able to:

1. Name the three logical operators — `and`, `or`, `not` — and state what each does. *(REMEMBERING)*
2. State the rule for `and` (all must be True) and `or` (at least one must be True). *(UNDERSTANDING)*
3. Evaluate expressions combining comparisons with logical operators. *(APPLYING)*
4. Work through a combined expression step by step, inner comparisons first. *(ANALYZING)*
5. Choose the right operator for a stated condition in plain English. *(APPLYING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 9**. Newly authored. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `print(7 > 3)` output?
`A` `4` · `B` `True` · `C` `7` · `D` SyntaxError
→ **B.** *Targets:* Comparisons produce Booleans.

**Q2.** Which operator checks equality?
`A` `=` · `B` `==` · `C` `!=` · `D` `>=`
→ **B.** *Targets:* `=` vs `==`.

**Q3.** What does `print(3 = 3)` produce?
`A` `True` · `B` `False` · `C` SyntaxError · `D` `3`
→ **C.** *Targets:* Assignment can't compare.

**Q4.** What does `print(10 == "10")` output?
`A` `True` · `B` `False` · `C` TypeError · `D` `10`
→ **B.** *Targets:* Number never equals string. *If >40% wrong:* re-run it live — today's combined expressions will hide this error completely.

**Q5.** What does `print(12 == 12.0)` output?
`A` `True` · `B` `False` · `C` TypeError · `D` `12`
→ **A.** *Targets:* Int and float can be equal.

**Q6.** Which are True? *(MSQ — select all)*
`A` `5 != 5` · `B` `4 >= 4` · `C` `"a" < "b"` · `D` `"A" == "a"`
→ **B and C.** *Targets:* `!=`, `>=`, string ordering, case sensitivity.

**Q7.** How many values can a comparison result be?
`A` Any number · `B` Two — True or False · `C` Three · `D` Depends
→ **B.** *Targets:* Booleans are binary. **Today's foundation** — logical operators take Booleans in and give Booleans out.

---

## Hook (7–10 min)

Say it before writing anything:

> *"Last session you learned to ask Python one question at a time. But nothing in real life is one question."*

Write on the board:

```
To pass this course you need attendance above 75%  AND  marks above 40
To get a refund you must be within 30 days  OR  the item must be faulty
```

> *"Two conditions each. And they behave completely differently. In the first one, failing either means you fail. In the second, satisfying either one is enough."*

Then type and run:

```python
print(True and False)     # False
print(True or False)      # True
```

> *"That's the entire session. Three small words — `and`, `or`, `not` — and after them your programs can express any condition you can say out loud."*

---

## Teaching Block A (10–22 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from RM `35dfbabb-e989-46fd-8a1f-12f1a158cf84` -->

**Write the three operators on the board and leave them up:**

| Operator | Gives True when |
|---|---|
| `and` | **both** sides are True |
| `or` | **at least one** side is True |
| `not` | flips it — True becomes False |

**Then build the truth tables on the board with the class.** Ask before you write each answer:

**`and`**

| Left | Right | Result |
|---|---|---|
| True | True | **True** |
| True | False | **False** |
| False | True | **False** |
| False | False | **False** |

**`or`**

| Left | Right | Result |
|---|---|---|
| True | True | **True** |
| True | False | **True** |
| False | True | **True** |
| False | False | **False** |

**`not`** — `not True` is `False`, `not False` is `True`.

**Then type and run each row** so students see the board and the terminal agree:

```python
print(True and True)      # True
print(True and False)     # False
print(True or False)      # True
print(False or False)     # False
print(not(False))         # True
```

**Beats to emphasise**

- **`and` is strict, `or` is generous.** One phrase, and it covers both tables.
- **These are English words, not symbols.** No `&&` or `||` here — Python uses the actual words. Students coming from other languages trip on this.
- **`not` needs something to flip.** It works on one value, not two.

**Checkpoint (at 22 min)** — cold-call two students:
> *"`True and False` — what and why? Then `True or False`."*
> **Answer:** `False`, because `and` needs both. `True`, because `or` needs only one.

---

## ⚡ Activity 1 — Human Compiler (22–27 min)

### What this activity is

Students **become** the Python interpreter. You point at one piece of an expression at a time and the student you pick says what that piece evaluates to — never the whole expression at once. You build up the answer in visible stages on the board.

### Why it's here

Students look at `(2 < 3) and (1 < 2)` and try to answer it in one leap. The RM shows the step-by-step reduction explicitly, and this activity makes the class perform it.

### Before class

Board space to write three lines under each other.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, write the expression | Look |
| 0:30–3:30 | Point at one bracket, take an answer, rewrite the line below | One piece each |
| 3:30–5:00 | Repeat with the second expression | Same |

### Say this

> *"You are Python. I point at one piece — one bracket, not the whole thing. You tell me what that piece becomes. We'll rewrite the line each time until there's nothing left to work out."*

### Expression 1

Write it, then reduce a step at a time, taking each step from a different student:

```
(2 < 3) and (1 < 2)
True    and (1 < 2)
True    and True
True
```

Point at `(2 < 3)` first: *"What does this piece become?"* → `True`. Rewrite the whole line. Then `(1 < 2)`. Then the final `and`.

### Expression 2

```
(2 < 3) or (2 < 1)
True    or (2 < 1)
True    or False
True
```

**Press here:** *"The right side is False. Why is the answer still True?"*
**Answer:** `or` only needs one side to be True.

### When it goes wrong

| If… | Do this |
|---|---|
| Student answers the whole expression at once | *"Too fast — just this bracket. What does this one become?"* The staging is the activity. |
| Someone says `(2 < 3)` is `2` | They're computing instead of comparing. *"It's a question. What's the answer — yes or no?"* |
| Room finds it trivially easy | Give them `(5 > 2) and (3 > 7) or (1 < 2)` and let them argue about order. Don't formalise precedence — just show that brackets settle it. |
| Nobody volunteers | Point at specific rows. Each answer is one word, so the risk is low — say that. |

**Common instructor mistake:** writing the reduction yourself while talking. Students must supply each step, or they're watching a demo.

**Cut rule:** Expression 1 only.

---

## Classroom Quiz (27–34 min)

5 MCQs from the platform pools — one from each of A, B and C, plus two combined. ~80 s each.

**Q1** — `a06873fa-d2e1-49a0-b976-8fd30595a43f` *(Quiz A · REMEMBERING)*
What is the output of `print(True and False)`?
- True
- None
- Error
- ✅ **False**

> *Explanation (platform):* The logical `and` operator returns True only if both operands are True. In this case, since one operand is False, the output is False.

**Q2** — `39a2a593-06b3-465f-88c8-b8019427568e` *(Quiz B · REMEMBERING)*
What is the output of `print(True or False)`?
- False
- ✅ **True**
- None
- Error

> *Explanation (platform):* In Python, the logical `or` operator returns True if at least one of the operands is True. Since the first operand is True, the result is True.

**Q3** — `986cc3f8-7425-4a40-853e-921e004c5b62` *(Quiz C · UNDERSTANDING)*
What is the output of `print(not(True))`?
- ✅ **False**
- None
- Error
- True

> *Explanation (platform):* The not operator returns the opposite Boolean value of the operand. Since the operand is True, not(True) evaluates to False.

**Q4** — `0647a93c-94c3-4564-90ac-f3002d68688d` *(Quiz A · APPLYING)*
What will be the output of `print((5 == 5) and (3 > 6))`?
- ✅ **False**
- True
- `5`
- `3`

> *Explanation (platform):* The first condition (5 == 5) is True, but the second condition (3 > 6) is False. The `and` operator returns False because both operands are not True.

**Q5** — `23a8a2e8-74b1-45bd-9846-8a92efd0d362` *(Quiz B · APPLYING)*
What will be the output of `print((5 == 5) or (3 > 6))`?
- False
- ✅ **True**
- `5`
- `3`

> *Explanation (platform):* The first condition (5 == 5) is True, but the second condition (3 > 6) is False. The `or` operator returns True because one of the operands is True.
> **Run Q4 and Q5 side by side after the vote.** Identical operands, one word different, opposite answers. That contrast teaches more than either question alone — don't let it pass unremarked.

---

## Teaching Block B (34–44 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from RM `35dfbabb-e989-46fd-8a1f-12f1a158cf84` -->

**Cover three things.**

**1. Combining comparisons with variables** — type and run:

```python
a = 10
b = 5
c = 3
d = 1
print(a > b and c > d)      # True
print(a > b and c < d)      # False
print(a < b or c > d)       # True
```

Read each aloud in English first: *"Is a bigger than b, AND is c bigger than d?"* Then run it.

**2. `not` applied to a comparison** — type and run:

```python
print(not(2 < 3))     # False
print(not(5 == 6))    # True
```

Reduce on the board, as in Activity 1:
```
not(2 < 3)
not(True)
False
```

**3. Translating English to code.** This is the practical skill. Do three on the board together:

| In English | In Python |
|---|---|
| Age is over 18 and under 60 | `age > 18 and age < 60` |
| Score is 100 or lives are 0 | `score == 100 or lives == 0` |
| The user is *not* logged in | `not(logged_in)` |

**Beats to emphasise**

- **Say it in English first, always.** Students who translate word by word get it right; students who guess at symbols don't.
- **Each side of `and`/`or` must be a complete comparison.** `age > 18 and < 60` is a SyntaxError — you can't abbreviate. Show it failing; it's the most common mistake in tonight's homework.

**Checkpoint (at 44 min)** — show hands:
> *"Write the condition for 'marks are above 40 and attendance is above 75'."*
> **Answer:** `marks > 40 and attendance > 75`. Both sides complete.

---

## ⚡ Activity 2 — Predict the Output (44–50 min)

### What this activity is

You reveal a snippet, **the whole class commits to an answer out loud before you run it**, then you run it. The public commitment is the mechanism — it converts a passive watch into an active prediction that students remember being right or wrong about.

### Why it's here

`and`/`or` feel obvious until they're combined with comparisons and a type mismatch. This finds the students who are pattern-matching rather than evaluating.

### Before class

Snippets in a file, revealed one at a time.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:20 | Setup line | Listen |
| 0:20–4:30 | Reveal, take a chorus answer, **then** run | Predict aloud |
| 4:30–6:00 | Debrief on #4 | Listen |

### Say this

> *"Everyone answers out loud together before I run it. True or False. Say it with confidence even if you're guessing — a wrong guess out loud is worth ten right answers in your head."*

### The snippets

```python
print((10 > 5) and (5 > 10))       # 1
```
```python
print((10 > 5) or (5 > 10))        # 2
```
```python
print(not(10 > 5))                 # 3
```
```python
age = input()                       # 4 — type 20
print(age > 18)
```

### Answers

| # | Output | Why |
|---|---|---|
| 1 | `False` | `and` needs both; the right side is False |
| 2 | `True` | `or` needs one; the left side is True |
| 3 | `False` | `10 > 5` is True, `not` flips it |
| 4 | **TypeError** | `input()` gave a string; you can't compare a string to a number with `>` |

**Snippet 4 is the point.** It looks like the most natural thing a beginner would write — *"is the age over 18?"* — and it crashes.

> *"That's the program you were about to write tonight. What's missing?"*
> **Answer:** `age = int(input())`.

### When it goes wrong

| If… | Do this |
|---|---|
| Room gets 1–3 instantly | Good, that's expected. Move fast to #4. |
| Someone predicts `False` for #4 | Very common — they assume it compares somehow. Run it, let the TypeError land. |
| They fix #4 immediately | Excellent. Ask *why* `==` on a string wouldn't crash but `>` does. (Equality can compare any two things; ordering can't.) |
| Nobody will call out together | Do a hands vote instead: *"Hands for True. Hands for False."* |

**Common instructor mistake:** running snippet 4 before taking a prediction. The wrong prediction is the entire value.

**Cut rule:** Snippets 1 and 4.

---

## ⚡ Activity 3 — Write the Question (50–57 min)

### What this activity is

Students write their own condition — one line of Python — designed to be genuinely tricky for a classmate. You collect a few, put them on screen anonymously, and the class evaluates them. Writing a question forces a different kind of thinking than answering one: to build a trap, you have to understand where the traps are.

### Why it's here

It's the session's assessment in disguise. A student who can construct a tricky `and`/`or` expression has understood the operators; one who can only answer them may not have.

### Before class

Nothing. Students need paper or the chat.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:40 | Setup line, give the constraints | Listen |
| 0:40–3:00 | Circulate quietly, look for good ones | Write one expression |
| 3:00–6:00 | Put 3 on screen, class evaluates each | Answer, argue |
| 6:00–7:00 | Debrief | Listen |

### Say this

> *"Everyone writes one line — a `print()` with a condition inside it, using `and`, `or` or `not`. The rule: you must know the answer, and it must be something a classmate could get wrong. Two minutes."*

**Give the constraints explicitly** or you'll get unusable submissions:

- Must use at least one of `and`, `or`, `not`
- Must use only numbers, strings and comparisons — nothing we haven't covered
- Must fit on one line
- **You must know the answer**

### Worked example to show them first

Put one up so they know the shape:

```python
print((5 > 3) and not(2 > 1))
```

Reduce it with the class: `True and not(True)` → `True and False` → **`False`**

### Running the reports

Collect three by walking round. Put each on screen without naming the author. For each:

1. Class votes True or False.
2. Ask the author to reduce it step by step on the board.
3. Run it. Confirm.

**If an author's own answer is wrong** — treat it as the best moment of the session: *"They wrote it and even they got it wrong. That's how easy these are to misread. Let's reduce it properly."*

### When it goes wrong

| If… | Do this |
|---|---|
| Submissions are all trivial (`True and False`) | Show the worked example again and ask for one with real comparisons in it. |
| Someone uses something not yet taught | Fine — say it's beyond today and pick another. Don't make it a correction. |
| Nobody writes anything | Drop to pairs: *"Write one between two of you."* |
| Two minutes isn't enough | Give three. The writing is the learning; the reporting is the bonus. |

**Common instructor mistake:** picking only the cleverest submissions. A simple one that half the room gets wrong teaches more than an elaborate one nobody follows.

**Cut rule:** Collect two, skip the author's board reduction.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — before anyone leaves:

> Write True or False: `(4 > 2) and (2 > 4)` · `(4 > 2) or (2 > 4)` · `not(3 == 3)`
> **Answers:** False · True · False

**Homework**

| Task | Unit |
|---|---|
| Coding Practice — 15 problems | `2352eee0-7db2-4189-b245-bd0246d141ed` |
| MCQ Practice — 98 questions | `bea78a11-7247-4662-8be4-68da6dda4251` |
| RM — Logical Operators | `35dfbabb-e989-46fd-8a1f-12f1a158cf84` |

> *"Two rules for tonight. Both sides of `and`/`or` must be complete comparisons — `age > 18 and < 60` is not valid. And if you're comparing something the user typed, convert it first."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `age > 18 and < 60` is valid | It reads fine in English | Block B — run it, SyntaxError |
| `or` means "one or the other, not both" | Everyday English usage | The `or` truth table — True and True gives True |
| `and`/`or` are `&&` and `\|\|` | Other languages | Block A — Python uses the English words |
| A comparison can produce a number | Everything before this did | Warm-up Q1 and Activity 1 |
| `not` works on two values | The other two operators do | Block A — `not` flips one thing |
| `input()` can be compared with `>` | It looks like a number | Activity 2 snippet 4 — TypeError |
| Combined expressions must be answered in one leap | Nobody showed the reduction | Activity 1 — one bracket at a time |

---

## Instructor Notes

- **⚠️ No video and no slide deck exist for this session in the platform export.** Both teaching blocks are written as board-and-live-typing sessions built from the reading material. If a deck appears later, the blocks map onto it directly and the activities slot between them unchanged.
- **This session has three quiz pools — A (`and`), B (`or`), C (`not`)** — the only session in the first fifteen with three. The five questions above deliberately take one from each plus two combined. Don't draw all five from one pool or you'll assess a third of the content.
- **Quiz Q4 and Q5 are the same expression with one word changed.** Run them side by side after the vote. That single contrast does more work than any explanation of the truth tables.
- **Translating English to code (Block B, part 3) is the skill that actually transfers.** Conditionals in Sessions 11–12 are entirely built on it. If time is tight, cut Activity 3 rather than that.
- **Pacing risk:** the truth tables in Block A can eat the whole block if you build all three exhaustively with the class. Build `and` fully with them, then do `or` and `not` faster — the pattern is established by then.
- **Two sessions in a row with no deck** (9 and 10). Your board work carries both. Consider photographing your board at the end for students who want it.
- **This is the last session before conditionals.** Students who can't reliably evaluate `and`/`or` will not survive Session 11. If the quiz results look weak, use the practice block for `and`/`or` drilling rather than the coding problems.
