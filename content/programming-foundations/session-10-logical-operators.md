# Session 10 — Logical Operators

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Operators · **Prerequisite** Session 9
**Session type** Concept lecture · ⚠️ **No video and no slide deck exist for this session** — see Instructor Notes. · **Format** 50-min recalibrated, 2 ALS activities, Classroom Quiz mandatory (never cut, runs last)

**Platform units**

| Resource | Unit ID |
|---|---|
| RM — Logical Operators | `35dfbabb-e989-46fd-8a1f-12f1a158cf84` |
| Classroom Quiz A (31 q — `and`) | `f6c5abb4-51cf-46de-925f-6ed6e80ca768` |
| Classroom Quiz B (26 q — `or`) | `d0f95f02-2d71-4743-86e9-c6da6d42b792` |
| Classroom Quiz C (29 q — `not`) | `54dd062f-30f7-4103-8a51-a65fed0f00e3` |
| MCQ Practice (98 q) | `bea78a11-7247-4662-8be4-68da6dda4251` |
| Coding Practice (15 q) | `2352eee0-7db2-4189-b245-bd0246d141ed` |

> ⚠️ **You have no deck.** The two "Teaching Block" sections replace Slide Blocks — board work and live typing, built from the reading material.

---

## Learning Objectives

By the end of this session, students will be able to:

1. Name the three logical operators — `and`, `or`, `not` — and state what each does. *(REMEMBERING)*
2. State the rule for `and` (all must be True) and `or` (at least one must be True). *(UNDERSTANDING)*
3. Evaluate expressions combining comparisons with logical operators. *(APPLYING)*
4. Work through a combined expression step by step, inner comparisons first. *(ANALYZING)*
5. Choose the right operator for a stated condition in plain English. *(APPLYING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** state the MCQ Practice completion number since last session. Target is 80%.

5 questions on **Session 9**. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `print(7 > 3)` output?
`A` `4` · `B` `True` · `C` `7` · `D` SyntaxError
→ **B.** *Targets:* Comparisons produce Booleans.

**Q2.** Which operator checks equality?
`A` `=` · `B` `==` · `C` `!=` · `D` `>=`
→ **B.** *Targets:* `=` vs `==`.

**Q3.** What does `print(10 == "10")` output?
`A` `True` · `B` `False` · `C` TypeError · `D` `10`
→ **B.** *Targets:* Number never equals string. *If >40% wrong:* re-run it live — today's combined expressions will hide this error completely.

**Q4.** Which are True? *(MSQ — select all)*
`A` `5 != 5` · `B` `4 >= 4` · `C` `"a" < "b"` · `D` `"A" == "a"`
→ **B and C.** *Targets:* `!=`, `>=`, string ordering, case sensitivity.

**Q5.** How many values can a comparison result be?
`A` Any number · `B` Two — True or False · `C` Three · `D` Depends
→ **B.** *Targets:* Booleans are binary. **Today's foundation** — logical operators take Booleans in and give Booleans out.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–11 min)

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

## Teaching Block A (11–18 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from RM `35dfbabb-e989-46fd-8a1f-12f1a158cf84` -->

**Write the three operators on the board and leave them up:**

| Operator | Gives True when |
|---|---|
| `and` | **both** sides are True |
| `or` | **at least one** side is True |
| `not` | flips it — True becomes False |

**Then build the truth tables on the board with the class.** Ask before you write each answer — build `and` fully, then move faster through `or` and `not` once the pattern's established:

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

**Checkpoint (at 18 min)** — 10 s silent think, cold-call two students:
> *"`True and False` — what and why? Then `True or False`."*
> **Answer:** `False`, because `and` needs both. `True`, because `or` needs only one.

---

## ⚡ ALS Activity 1 — Staged Expression Reduction: Human Compiler (18–23 min)

**ALS format:** Round-Robin Staged Reduction — students become the interpreter, but instead of tracing separate lines of a program (as in earlier sessions' Human Compiler activities), each student resolves just *one bracket* of a single expression, and the board rewrites one step smaller each time. Chosen because combined expressions like `(2 < 3) and (1 < 2)` are almost always answered in one wrong leap — this format makes the leap impossible.

**Setup line:**
> *"You are Python. I point at one piece — one bracket, not the whole thing. You tell me what that piece becomes. We'll rewrite the line each time until there's nothing left to work out."*

**Expression 1** — write it, then reduce a step at a time, taking each step from a different student:

```
(2 < 3) and (1 < 2)
True    and (1 < 2)
True    and True
True
```

Point at `(2 < 3)` first: *"What does this piece become?"* → `True`. Rewrite the whole line. Then `(1 < 2)`. Then the final `and`.

**Expression 2** (if time allows):

```
(2 < 3) or (2 < 1)
True    or (2 < 1)
True    or False
True
```

**Press here:** *"The right side is False. Why is the answer still True?"*
**Answer:** `or` only needs one side to be True.

**Debrief line:**
> *"Every combined expression reduces the same way — smallest piece first, one step at a time. Never guess the whole thing in your head."*

**Cut rule:** Expression 1 only.

---

## Classroom Quiz (23–30 min) · ALS: Individual Answer → Reveal

> 🔒 **Mandatory block — do not cut, do not shorten, do not skip under time pressure.** This session has three quiz pools — A (`and`), B (`or`), C (`not`) — the only session in the first fifteen with three. The five questions below deliberately take one from each plus two combined; don't substitute all five from one pool.

Every question below is run ALS-style: **individual silent answer first, then explanation.**

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

## Teaching Block B (30–38 min) — BOARD + LIVE TYPING

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

Reduce on the board, as in ALS Activity 1:
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

**Checkpoint (at 38 min)** — show hands:
> *"Write the condition for 'marks are above 40 and attendance is above 75'."*
> **Answer:** `marks > 40 and attendance > 75`. Both sides complete.

---

## ⚡ ALS Activity 2 — Choral Prediction → Reveal (38–45 min)

**ALS format:** Choral Prediction — the whole room answers out loud together before each run. Chosen because `and`/`or` feel obvious in isolation; a shared, confident wrong guess on the type-mismatch snippet is more memorable corrected as a group than picked apart from one student.

**Setup line:**
> *"Everyone answers out loud together before I run it. True or False. Say it with confidence even if you're guessing — a wrong guess out loud is worth ten right answers in your head."*

Reveal one snippet at a time:

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

| # | Output | Why |
|---|---|---|
| 1 | `False` | `and` needs both; the right side is False |
| 2 | `True` | `or` needs one; the left side is True |
| 3 | `False` | `10 > 5` is True, `not` flips it |
| 4 | **TypeError** | `input()` gave a string; you can't compare a string to a number with `>` |

**Snippet 4 is the point.** It looks like the most natural thing a beginner would write — *"is the age over 18?"* — and it crashes.
> *"That's the program you were about to write tonight. What's missing?"*
> **Answer:** `age = int(input())`.

**Debrief line:**
> *"Equality can compare any two things and just says False. Ordering — `>`, `<` — refuses outright when the types don't match. That's why this one crashes and `10 == "10"` doesn't."*

**Cut rule:** Snippets 1 and 4.

---

## Exit Ticket + Quiz Push (45–48 min)

**Exit ticket** (~30 s) — before anyone leaves:

> Write True or False: `(4 > 2) and (2 > 4)` · `(4 > 2) or (2 > 4)` · `not(3 == 3)`
> **Answers:** False · True · False

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Open MCQ Practice. Everyone, this room, right now — attempt the first 3 questions before you leave your seat. 98 questions in this pool."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 11's warm-up."*

**Remaining homework**

| Task | Unit |
|---|---|
| Coding Practice — 15 problems | `2352eee0-7db2-4189-b245-bd0246d141ed` |
| MCQ Practice — 98 questions *(started in class above — finish the rest)* | `bea78a11-7247-4662-8be4-68da6dda4251` |
| RM — Logical Operators | `35dfbabb-e989-46fd-8a1f-12f1a158cf84` |

> *"Two rules for tonight. Both sides of `and`/`or` must be complete comparisons — `age > 18 and < 60` is not valid. And if you're comparing something the user typed, convert it first."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock and want a closer instead of ending early, run the optional Write the Question round below:

**Optional closer — Write the Question:** everyone writes one `print()` condition using `and`/`or`/`not` that they know the answer to and think could trick a classmate. Collect one or two, put on screen anonymously, class votes True/False, author reduces it on the board. Worked example if needed: `print((5 > 3) and not(2 > 1))` → `True and not(True)` → `True and False` → **`False`**. Never required — the schedule doesn't depend on it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `age > 18 and < 60` is valid | It reads fine in English | Teaching Block B — run it, SyntaxError |
| `or` means "one or the other, not both" | Everyday English usage | The `or` truth table — True and True gives True |
| `and`/`or` are `&&` and `\|\|` | Other languages | Teaching Block A — Python uses the English words |
| A comparison can produce a number | Everything before this did | Warm-up Q1 and ALS Activity 1 |
| `not` works on two values | The other two operators do | Teaching Block A — `not` flips one thing |
| `input()` can be compared with `>` | It looks like a number | ALS Activity 2 snippet 4 — TypeError |
| Combined expressions must be answered in one leap | Nobody showed the reduction | ALS Activity 1 — one bracket at a time |

---

## Instructor Notes

- **⚠️ No video and no slide deck exist for this session in the platform export.** Both teaching blocks are written as board-and-live-typing sessions built from the reading material.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Round-Robin Staged Reduction (one bracket at a time, not a whole line), Activity 2 is Choral Prediction → Reveal (whole room together). The original third activity (Write the Question) is demoted to an optional buffer-only closer — the instructor notes for the original plan already flagged it as the first thing to cut under time pressure, so it's the one dropped from the scheduled 45 minutes rather than the translating-skill content in Teaching Block B.
- **The Classroom Quiz runs last, right before the Exit Ticket** — never cut, never shortened. Draws one question from each of the three pools plus two combined, deliberately — don't pull all five from one pool.
- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair.** Target is 80% platform MCQ attempt rate, currently ~33%.
- **Quiz Q4 and Q5 are the same expression with one word changed.** Run them side by side after the vote.
- **Translating English to code (Teaching Block B, part 3) is the skill that actually transfers.** Conditionals in Sessions 11–12 are entirely built on it. If time is tight anywhere, protect this over everything except the mandatory quiz.
- **Two sessions in a row with no deck** (9 and 10). Consider photographing your board at the end for students who want it.
- **This is the last session before conditionals.** Students who can't reliably evaluate `and`/`or` will not survive Session 11. If the quiz results look weak, use the Quiz Push time for `and`/`or` drilling rather than the coding problems.
