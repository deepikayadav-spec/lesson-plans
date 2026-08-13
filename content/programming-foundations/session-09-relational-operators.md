# Session 9 — Relational Operators

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Operators · **Prerequisite** Session 8
**Session type** Concept lecture · ⚠️ **No video and no slide deck exist for this session** — see Instructor Notes. · **Format** 50-min recalibrated, 2 ALS activities, Classroom Quiz mandatory (never cut, runs last)

**Platform units**

| Resource | Unit ID |
|---|---|
| RM — Relational Operators | `e03da18b-8523-445e-81e9-8519b1c16a61` |
| Classroom Quiz A (52 q) | `6b210db5-685c-4856-8b2e-e9c2fc365bb8` |
| Classroom Quiz B (38 q) | `a045af4b-1c97-45ca-9693-aeadc5f10028` |
| MCQ Practice (40 q) | `176ab7ce-6e44-4ff5-9ac9-4bff2bb71f4d` |
| Coding Practice (10 q) | `9935f186-744c-4b1d-b775-b45056daa899` |

> ⚠️ **You have no deck.** The two "Teaching Block" sections below replace Slide Blocks — board work and live typing, built from the reading material. Everything you need is written out; you supply the whiteboard.

---

## Learning Objectives

By the end of this session, students will be able to:

1. Name the six relational operators and what each compares. *(REMEMBERING)*
2. Explain that a comparison produces `True` or `False`, not a number. *(UNDERSTANDING)*
3. Distinguish `=` from `==` and state what each does. *(UNDERSTANDING)*
4. Predict the result of comparisons between integers, floats and strings. *(APPLYING)*
5. Explain why `10 == "10"` is `False`. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** state the MCQ Practice completion number since last session. Target is 80%.

5 questions on **Session 8**. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `int("nine")` give?
`A` `9` · `B` `0` · `C` ValueError · `D` TypeError
→ **C.** *Targets:* Invalid conversion raises ValueError.

**Q2.** Which converts a number to text?
`A` `int()` · `B` `float()` · `C` `str()` · `D` `type()`
→ **C.** *Targets:* Conversion function names.

**Q3.** `a = int(input())` and the user types `5`. What is `a`?
`A` The string `"5"` · `B` The number `5` · `C` `5.0` · `D` Error
→ **B.** *Targets:* The `int(input())` pattern — reused in today's Activity 1.

**Q4.** Which raise an error? *(MSQ — select all)*
`A` `int("7")` · `B` `int("7.0")` · `C` `int(7.0)` · `D` `int("seven")`
→ **B and D.** *Targets:* The `"7.0"` trap — same "looks right but isn't" family as today's `10 == "10"`.

**Q5.** What is `type("10")`?
`A` int · `B` str · `C` float · `D` bool
→ **B.** *Targets:* Quotes decide type. **Today's gateway** — `10 == "10"` depends entirely on this. Note the number.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–11 min)

Write on the board, nothing else:

```
5 > 3
```

> *"Is that true or false?"*

Everyone says true. Then:

> *"Right. Now here's the thing — Python agrees with you, and it will say so out loud."*

Type and run:

```python
print(5 > 3)
```

Output: `True`

> *"Every program that ever made a decision — a login that checks your password, a game that knows you lost, an app that says 'you're too young for this' — every one of them is built on this. A question that comes back True or False. Today you learn to ask them. Next session you learn to combine them. After that, your programs start making choices."*

---

## Teaching Block A (11–18 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from RM `e03da18b-8523-445e-81e9-8519b1c16a61` -->

**Write this table on the board and leave it up all session:**

| Operator | Meaning |
|---|---|
| `>` | is greater than |
| `<` | is less than |
| `==` | is equal to |
| `<=` | is less than or equal to |
| `>=` | is greater than or equal to |
| `!=` | is not equal to |

**Then type and run each of these, one at a time:**

```python
print(5 < 10)     # True
print(2 > 1)      # True
print(2 <= 3)     # True
print(2.53 >= 2.55)   # False
print(5 != 5)     # False
```

**Beats to emphasise**

- **The result is always `True` or `False`.** Never a number. Point at the capital letters — these are the Booleans from Session 4, finally being useful.
- **`==` is two characters, and it is not `=`.** Write both on the board side by side with labels: `=` puts a value in a box, `==` asks a question. This is the single most expensive confusion in the session.
- **`!=` reads as "not equal".** The `!` means "not" — that carries into next session's `not` operator.

**Checkpoint + Fix-It Fire (at 18 min, ~2 min)** — 10 s silent think, cold-call two students for the checkpoint, then one quick fix-it prompt (compressed from a full board race — folded in here to protect the schedule):
> *Checkpoint:* *"What does `x = 5` do, and what does `x == 5` do?"* Answer: The first puts 5 into `x`. The second asks whether `x` holds 5, and answers `True` or `False`.
> *Fix-it:* put `print(3 = 3)` on screen — *"fix this, ten seconds."* Answer: `print(3 == 3)`. This is the single trap the quiz tests hardest — don't skip it.

---

## ⚡ ALS Activity 1 — Individual Diagnose, Cold-Call Reveal: Spot the Bug (18–24 min)

**ALS format:** Individual Diagnose → Cold-Call Reveal — everyone diagnoses all four snippets alone, silently, before any answer is taken. No pairing this time — chosen because every trap here (`=` vs `==`, the space in `< =`, comparing a string to a number) is exactly the kind of typo-level mistake students make alone at 11pm tonight, with nobody next to them to catch it.

**Setup line:**
> *"Four snippets. Tell me what's wrong and what it's called. Then the fix. Ninety seconds, silent, on your own."*

```python
# 1
age = 18
print(age = 18)
```
```python
# 2
print(5 > = 3)
```
```python
# 3
password = "Python123"
print(password == "python123")
```
```python
# 4
user_age = input()
print(user_age == 18)
```

**Answers**

| # | Diagnosis | Fix |
|---|---|---|
| 1 | `SyntaxError` — `=` assigns, doesn't compare | `print(age == 18)` |
| 2 | `SyntaxError` — space inside `>=` | `print(5 >= 3)` |
| 3 | **No error.** Prints `False` — capital `P` vs lowercase `p` | Match the case, or accept that it's genuinely different |
| 4 | **No error.** Always prints `False` — `input()` gives a string, and a string never equals a number | `int(user_age) == 18` |

**Snippet 4 is the one that matters.** It runs fine, produces `False` no matter what the user types, and combines Sessions 6, 8 and today. Ask directly:
> *"The user types 18. It prints False. Nothing crashed. How long would it take you to find that bug tonight?"*

**Debrief line:**
> *"Three of these are typos with a name. The fourth is silent and correct-looking. That's the one that actually costs you time."*

**Cut rule:** Do 1 and 4. Snippet 4 is non-negotiable.

---

## Classroom Quiz (24–31 min) · ALS: Individual Answer → Reveal

> 🔒 **Mandatory block — do not cut, do not shorten, do not skip under time pressure.** Protect these 7 minutes by using the cut rules everywhere else first.

Every question below is run ALS-style: **individual silent answer first, then explanation.**

5 MCQs from the platform pools. ~85 s each.

**Q1** — `dae6dcf7-175e-436f-a917-e4150c4f1c09` *(Quiz A · REMEMBERING)*
Which relational operator in Python checks for equality between two values?
- `=`
- `>=`
- ✅ **`==`**
- `<=`

> *Explanation (platform):* The '==' operator is used to check if two values are equal in Python.

**Q2** — `a1f1566a-d8ee-4db7-963f-e5b6af89d3f9` *(Quiz A · UNDERSTANDING)*
What is the output of `print(7 > 3)`?
- False
- `4`
- ✅ **True**
- SyntaxError

> *Explanation (platform):* The expression 7 > 3 evaluates to True because 7 is greater than 3.
> **If anyone picks `4`:** they're expecting a calculation. Comparisons answer questions, they don't compute values.

**Q3** — `314fb90a-f760-49ac-ad61-aa643106b57d` *(Quiz A · APPLYING)*
Identify the error in `print(3 = 3)`.
- print should be Print
- ✅ **SyntaxError due to incorrect way of comparing**
- No error, the code is correct
- The numbers being compared are not valid

> *Explanation (platform):* The '=' operator is used for assignment, not for comparison. The correct operator for checking equality is '=='.
> **If >40% miss this:** stop and re-run the board comparison of `=` versus `==`.

**Q4** — `5275c12c-f77f-4b89-b003-0343aee3ed01` *(Quiz A · APPLYING)*
How do you fix the error in `print(2 < = 3)`?
- No fix needed; the code is correct
- ✅ **Remove the space between `<` and `=`**
- Replace `<=` with `=<`
- None of the given options

> *Explanation (platform):* The correct syntax for the 'less than or equal to' operator is '<=', without any space between the characters.
> **If they pick `=<`:** worth 20 seconds — the order is fixed, and `=<` is not valid Python at all.

**Q5** — `38e3ffaf-9e11-4f0b-bf3a-be7985916425` *(Quiz A · ANALYZING)*
What will be the output of `print(10 == '10')`?
- True
- ✅ **False**
- `'10'`
- TypeError

> *Explanation (platform):* The output will be False because the integer 10 is not equal to the string '10'.
> **This is the session's hardest question and its most important.** If they expected `True`, they're comparing what things *look like* rather than what they *are*. Python doesn't error here — it just says False, which makes this a silent bug. Ties directly to Session 7's crash-vs-bug distinction.

---

## Teaching Block B (31–39 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from RM `e03da18b-8523-445e-81e9-8519b1c16a61` -->

**Cover three things, in this order.**

**1. The two syntax traps** — type both, let both fail:

```python
print(3 = 3)      # SyntaxError: perhaps you meant "=="?
print(2 < = 3)    # SyntaxError: invalid syntax
```

Read the first error aloud — Python literally suggests `==`. Say: *"It's telling you the answer. Read your errors."*

**2. Comparing across number types** — type and run:

```python
print(2 <= 3)         # True
print(2.53 >= 2.55)   # False
print(12 == 12.0)     # True   ← the surprising one
print(12 == 12.1)     # False
```

`12 == 12.0` being `True` surprises rooms. Say: *"An integer and a float can be equal, because both are numbers. Same value, different container."*

**3. Comparing strings** — type and run:

```python
print("Python" == "python")    # False
print("abc" < "abd")           # True
print(10 == "10")              # False
```

- **Case matters.** `"Python"` and `"python"` are different strings.
- **Strings compare alphabetically.** `"abc" < "abd"` is `True` because `c` comes before `d`.
- **A number is never equal to a string**, even when they look identical.

**Checkpoint (at 39 min)** — show hands:
> *"`print(12 == 12.0)` — True or False? And `print(12 == "12")`?"*
> **Answer:** `True`, then `False`. Both numbers versus a number and a string.

---

## ⚡ ALS Activity 2 — Structured Solo Tracing: Trace the Table (39–45 min)

**ALS format:** Structured Solo Tracing — everyone fills in their own table, silently, as you read code aloud, no pairing or discussion. Chosen because next session combines comparisons with `and`/`or`, which is impossible for students who can't reliably evaluate a single comparison alone yet — the skill has to be individual and automatic before it's combined with anything else.

**Setup line:**
> *"Paper out, laptops shut. Three columns: `a`, `b`, and `result`. I read a line, you write what's in each after that line. If a line is a comparison, `result` is True or False."*

```python
a = 5
b = 5.0
result = a == b
a = "5"
result = a == b
result = a != b
```

**The completed table**

| After line | `a` | `b` | `result` |
|---|---|---|---|
| `a = 5` | `5` | — | — |
| `b = 5.0` | `5` | `5.0` | — |
| `result = a == b` | `5` | `5.0` | **True** |
| `a = "5"` | `"5"` | `5.0` | True *(unchanged)* |
| `result = a == b` | `"5"` | `5.0` | **False** |
| `result = a != b` | `"5"` | `5.0` | **True** |

**The key moment:** row 3 gives `True` and row 5 gives `False` — **same comparison, same-looking values.** Ask:
> *"Nothing about the comparison changed. Why did the answer flip?"*
**Answer:** `a` stopped being a number and became a string. The types changed, so the answer changed.

Then row 6: `!=` on the same values gives `True`, because they genuinely are not equal.

**Debrief line:**
> *"You just tracked a bug you can't see with your eyes — only by knowing what type each variable actually holds. That's the whole session in one table."*

**Cut rule:** Stop after row 5.

---

## Exit Ticket + Quiz Push (45–48 min)

**Exit ticket** (~30 s) — before anyone leaves:

> Write True or False for each: `7 != 7` · `3 <= 3` · `10 == "10"` · `"a" < "b"`
> **Answers:** False · True · False · True

The third one is the one to scan for on the way out.

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Open MCQ Practice. Everyone, this room, right now — attempt the first 3 questions before you leave your seat."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 10's warm-up."*

**Remaining homework**

| Task | Unit |
|---|---|
| Coding Practice — 10 problems | `9935f186-744c-4b1d-b775-b45056daa899` |
| MCQ Practice — 40 questions *(started in class above — finish the rest)* | `176ab7ce-6e44-4ff5-9ac9-4bff2bb71f4d` |
| RM — Relational Operators | `e03da18b-8523-445e-81e9-8519b1c16a61` |

> *"If you compare something to `input()` and always get False, you already know why. Convert it first."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock and want an energy-lift closer instead of ending early, run the optional Rapid Fire Board Race below — two volunteers at the board, class judges:
1. Write code that checks if 8 is bigger than 3 → `print(8 > 3)`
2. Write code that checks if `x` is **not** 5 → `print(x != 5)`
> Never required — the schedule doesn't depend on it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `=` compares two things | Ten years of maths | Board comparison in Teaching Block A, then Quiz Q3 |
| `< =` with a space is fine | Spaces are usually harmless | Running it — SyntaxError |
| `10 == "10"` is True | They look identical | Quiz Q5 and ALS Activity 2 row 5 |
| Comparisons produce numbers | Everything so far did | Quiz Q2 — the answer is `True`, not `4` |
| `12 == 12.0` is False | Different types must differ | Teaching Block B — both are numbers, same value |
| String comparison ignores case | Human reading does | Teaching Block B — `"Python" == "python"` is False |
| A wrong comparison will crash | Errors are their feedback | ALS Activity 1 snippet 4 — runs fine, always False |

---

## Instructor Notes

- **⚠️ No video and no slide deck exist for this session in the platform export.** Both teaching blocks above are written as board-and-live-typing sessions built directly from the reading material.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Individual Diagnose → Cold-Call Reveal (fully solo, no pairing), Activity 2 is Structured Solo Tracing (also solo — deliberately, since both skills need to be individually automatic before next session combines them with `and`/`or`). The original Rapid Fire Board Race is demoted to an optional buffer-only closer — it was flagged in the original plan as "energy, not content," the first thing to cut under time pressure, so it's the one dropped from the scheduled 45 minutes. Its highest-value prompt (fixing `3 = 3`) is folded into Teaching Block A's checkpoint instead.
- **The Classroom Quiz runs last, right before the Exit Ticket** — never cut, never shortened.
- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair.** Target is 80% platform MCQ attempt rate, currently ~33%.
- **This session is the runway for Sessions 10–12.** Conditionals are unusable without solid comparisons. If something has to be cut beyond the board race, cut minutes from Teaching Block A's number-type examples before touching Quiz Q5 or ALS Activity 2.
- **`=` versus `==` will keep coming back all term.** Write both on the board with their labels at the start and refuse to erase them.
- **Session 4 planted this.** When you taught the assignment operator, you flagged that comparison uses `==` and would arrive later. Call that back explicitly.
- **Smallest MCQ pool since Session 4** — 40 questions. If the Quiz Push or practice block runs long, Session 8's 130-question pool makes good backup revision.
