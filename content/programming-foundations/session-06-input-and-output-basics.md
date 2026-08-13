# Session 6 — Input and Output Basics

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Sequence of Instructions · **Prerequisite** Session 5
**Session type** Concept lecture · **Format** 50-min recalibrated, 2 ALS activities, Classroom Quiz mandatory (never cut, runs last)

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Input and Output Basics | `c3c48270-5880-4187-bd0c-6716a94cb99d` |
| RM — Input and Output Basics | `115d5b6e-cd8c-4925-9f68-5be66507aab4` |
| Classroom Quiz A (39 q) | `d0085ebf-dd52-4ae4-a321-74ad7ef470c9` |
| Classroom Quiz B (75 q) | `3b1d547d-50e1-4ad8-88cc-6db41dc5275d` |
| MCQ Practice (99 q) | `145ba1e4-adee-4089-b15f-d0bc1e6c85e3` |
| Coding Practice (15 q) | `3ec2d3fe-0670-4186-83ef-7fc0c70b5d6f` |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Join strings using `+` and repeat them using `*`. *(APPLYING)*
2. Explain why `"*" + 10` raises a `TypeError` but `"*" * 10` does not. *(UNDERSTANDING)*
3. Read user input with `input()` and state that it always returns a string. *(REMEMBERING)*
4. Find a string's length with `len()` and access a character by index. *(APPLYING)*
5. Predict when an `IndexError` will occur. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Projector on, deck loaded, terminal ready where `input()` visibly waits (test this before class), students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** state the MCQ Practice completion number since last session. Target is 80%.

5 questions on **Session 5**. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `print("score")` display when `score = 90`?
`A` `90` · `B` `score` · `C` `"score"` · `D` Error
→ **B.** *Targets:* Quotes print the literal word. *Misconception:* A means the quotes rule still isn't automatic. *If >40% wrong:* run both lines live — this decides half of today.

**Q2.** What happens here?
```python
print(total)
total = 50
```
`A` Prints `50` · `B` NameError · `C` Prints `total` · `D` SyntaxError
→ **B.** *Targets:* Line-by-line execution.

**Q3.** Which run without error? *(MSQ — select all)*
`A` `x = 5` · `B` `5 = x` · `C` `x = x` after `x = 1` · `D` `print(x)` before `x = 1`
→ **A and C.** *Targets:* Assignment direction. *Misconception:* picking B means the left-right direction of `=` isn't fixed yet.

**Q4.** `a = 5`, then `a = a + 3`. What's in `a`?
`A` `5` · `B` `8` · `C` `53` · `D` Error
→ **B.** *Targets:* Reassignment using the old value.

**Q5.** What's the data type of `"10"`?
`A` Integer · `B` String · `C` Float · `D` Boolean
→ **B.** *Targets:* Quotes decide type. **This is today's gateway** — `input()` returns a string, and if this isn't solid nothing after the halfway point will land. Note the number.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Type this live and run it:

```python
print("Your name is Ravi")
```

> *"Fine. Now everyone in this room runs it and it still says Ravi. That's a useless program. A program that can't ask you anything is just a very expensive printout."*

Then type:

```python
username = input()
print("Your name is " + username)
```

Run it. Type a student's name when it waits. Run it again with a different name.

> *"That's the whole difference between a program and a printout. Today your programs start listening."*

Tie back to **Q5** — *"Hold on to that. Whatever the user types, Python hands it back as a string. Every single time. That fact causes about half the bugs you'll hit this month."*

---

## Slide Block A (10–17 min) — DELIVER SLIDES AS-IS

**Verified against the deck** (*"Copy of 2.1 Input Output Basics"*). Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1–2 | Welcome · **Recap — Order of Operations** | `5 * 2 + 3 * 4` → 22, with the BODMAS badges |
| 3 | **Adding Strings** | `a = "1" + "2"` → **`12`**. "Adding strings is called **String Concatenation**" |
| 4 | **String Concatenation** | `a = "*" + 10` → *"What will be the output?"* — posed as a question, no answer on the slide |
| 5 | **String Concatenation** | `a = "*" * 10` → `**********`. "String will be repeated 10 times. This is called **String Repetition**" |

**Beats to emphasise**

- **Slide 1–2 is a recap your warm-up poll already did.** Ten seconds.
- **Slide 3's example is `"1" + "2"` → `12`, not `3`.** That is the strongest possible opening for this session — two things that look like numbers, added, giving a joined string. Take a prediction before revealing.
- **Slide 4 is deliberately unanswered.** The deck asks *"what will be the output?"* and moves on. **Do not skip past it — run it live.** `"*" + 10` raises a `TypeError`, and that error is Quiz Q3.
- **Slides 4 and 5 are the pair:** `"*" + 10` fails, `"*" * 10` works. Same two values, different operator. Show them back to back.

> ⚠️ **The deck never shows concatenation *with a space*** — no `"Good" + "Morning"` → `GoodMorning` example. **Quiz Q1's answer hinges on "without adding space."** Add it verbally: type `print("Good" + "Morning")` and let the missing space land.

**Checkpoint + Quick Fill (at 17 min, ~2 min)** — 10 s silent think, cold-call two students for the checkpoint, then a compressed fill-the-blank beat (folded in here to protect the schedule):
> *Checkpoint:* *"What does `"ab" * 3` give, and what does `"ab" + 3` give?"* Answer: `ababab`, and a TypeError.
> *Quick fill:* put `print("Hi" + ___ + "there")` on screen — *"what fills the gap to put a space between the words?"* Take the answer, type it **literally**. Most rooms say "space" without quotes — type `space` and let the `NameError` land before someone corrects to `" "`.

---

## ⚡ ALS Activity 1 — Choral Prediction → Reveal (17–23 min)

**ALS format:** Choral Prediction — the whole room predicts out loud, together, before each run, rather than one student answering. Chosen over an individual cold-call because the string-vs-number confusion is near-universal at this point in the course; a shared wrong guess, corrected together, lands faster than picking on one student to be wrong in front of everyone.

> The value is entirely in the commitment — a room that has publicly guessed `13` remembers the correction far longer than one that passively watched.

**Setup line:**
> *"Before I hit run, everyone says the answer out loud. Together. Being wrong out loud is the fastest way to never be wrong again."*

Reveal one snippet at a time — don't put all four on screen together.

```python
print("5" + "3")        # 1
```
```python
print("5" * 3)          # 2
```
```python
print("5" + 3)          # 3
```
```python
age = input()           # 4  — type 20 when it asks
print(age + 1)
```

| # | Output | Why |
|---|---|---|
| 1 | `53` | Two strings — joined, not added |
| 2 | `555` | String repeated three times |
| 3 | **TypeError** | Can't join a string to a number |
| 4 | **TypeError** | `input()` gave a string, so `age + 1` is string + number |

**Snippet 4 is the point of the session.** Everything before it is setup.

**Debrief line:**
> *"`input()` always hands you back a string, even when someone types a number. That's the trap this whole session has been building to."*

**Cut rule:** Snippets 1, 3 and 4. Skip 2 first if running late.

---

## Slide Block B (23–31 min) — DELIVER SLIDES AS-IS

**Verified against the deck.** Slides, in order:

| # | Slide | Content |
|---|---|---|
| 6 | **Taking Input From User** | "When we download a software, do we change instructions in it?" → "We take **input** from users through interface" |
| 7+ | **Reading input** | `input()` examples |
| 8+ | **Accessing Characters in String** | `username = "Ravi"` → *"Can we access the first character in this string?"* |
| 9+ | **Indexing** | Position-based access, `username[0]` |
| last | **Key Takeaways** | Strings (Concatenation · Repetition) · Reading Input · Indexing |

**Beats to emphasise**

- **Slide 6's framing is good — use it.** Software you download has fixed instructions; what changes is the *input*. That's why programs need `input()`.
- **`input()` always returns a string.** Say it three times across this block. It is the highest-value sentence of the session and **Quiz Q4** tests it directly.
- **Indexing starts at 0.** Write `R-a-v-i` on the board with `0-1-2-3` underneath. The picture does more than the explanation.
- **Close on the Key Takeaways slide** — it names the session's four things and makes a clean handover to homework.

> ⚠️ **Two things the quiz needs that the deck is thin on:** `len()` (Quiz Q5 depends on knowing length vs. highest index) and the **IndexError** itself. Demonstrate both live — `print(len("Zoe"))` → `3`, then `print("Zoe"[10])` → `IndexError` — before the quiz.

**Checkpoint (at 31 min)** — show hands:
> *"`name = "Ravi"`. What is `name[0]`, and what is `len(name)`?"*
> **Answer:** `R` and `4`. Note that the last valid index is 3, not 4.

---

## ⚡ ALS Activity 2 — Guided Full-Build Dictation (31–38 min)

**ALS format:** Full-Program Cold-Call Dictation — students dictate every line of a complete program, not just one gap. Chosen instead of a repeat of the checkpoint's single-blank fill because this is the session's synthesis moment: `input()`, concatenation, and `len()` all have to come together into one working program, which is also the shape of tonight's homework.

**Setup line:**
> *"You're writing this, I'm just the keyboard. Goal: ask the user their name, then print a greeting that also says how many letters are in their name."*

**Target program:**

```python
name = input()
print("Hello " + name)
print("Your name has " + str(len(name)) + " letters")
```

Build it a line at a time, asking *"what's the next line?"* Run after every line — students need to see it working incrementally.

**The deliberate bug** — when you reach the third line, type this instead and run it:

```python
print("Your name has " + len(name) + " letters")
```

**Output:** `TypeError: can only concatenate str (not "int") to str`

> *"Read the error. It's telling you exactly what's wrong — in plain English. What is it saying?"*

Take the diagnosis from students. `len()` returns a number; you can't join a number to a string. **If nobody knows the fix, that's fine** — `str()` arrives properly in Session 8:

> *"There's a tool for this called `str()`. You'll meet it properly in two sessions. For now, notice the shape of the problem — Python is very fussy about mixing types."*

Then add `str()` and run the working version.

**Debrief line:**
> *"Same bug as Activity 1's snippet 4, different shape — mixing a string with a number. You will see this exact error family for the rest of the course."*

**When it goes wrong**

| If… | Do this |
|---|---|
| Nobody offers a first line | Give line 1 yourself, ask for line 2. Momentum matters more than purity. |
| They dictate the whole program instantly | Spend the saved time on the bug and let two students explain the fix. |
| The class fixates on `str()` | Cap it at 60 seconds. Name Session 8 and move on. |

**Cut rule:** Build lines 1 and 2 only, then jump straight to the bug on line 3.

---

## Classroom Quiz (38–45 min) · ALS: Individual Answer → Reveal

> 🔒 **Mandatory block — do not cut, do not shorten, do not skip under time pressure.** Runs last, right before the Exit Ticket. Protect these 7 minutes by using the cut rules everywhere else first.

Every question below is run ALS-style: **individual silent answer first, then explanation.**

5 MCQs from the platform pools. ~85 s each.

**Q1** — `1e137728-46f1-444f-875e-85f2004718d9` *(Quiz A · REMEMBERING)*
What does the `+` operator do when used between two strings in Python?
- It adds the numerical values of the strings.
- ✅ **It concatenates the strings without adding space.**
- It creates a list containing the strings.
- It generates a TypeError.

> *Explanation (platform):* In Python, the '+' operator is used to concatenate two strings directly, joining them together without adding any space between them.
> **The words "without adding space" matter.** Students expect a space. Point at it.

**Q2** — `d5eeb64f-e3bd-4619-b6a4-4c6f5c11896f` *(Quiz A · UNDERSTANDING)*
What is the output of `print("*" * 3)`?
- `*3`
- ✅ **`***`**
- TypeError
- `* * *`

> *Explanation (platform):* The `*` operator in Python, when used with a string and an integer, repeats the string the specified number of times. Therefore, `"*" * 3` results in `***`.
> **If they pick `* * *`:** they're assuming a separator gets added. It doesn't — same lesson as Q1.

**Q3** — `49fa11bc-eddf-48a4-96d1-e631193eb7f0` *(Quiz A · APPLYING)*
Identify the type of error in `print("Hello" + 5)`.
- ValueError
- IndexError
- ✅ **TypeError**
- SyntaxError

> *Explanation (platform):* Python does not allow concatenation of strings with integers, which results in a TypeError.
> **If they pick SyntaxError:** the code is perfectly well-formed — nothing is misspelled or misplaced. The problem is the *kinds of things* being combined. That distinction is the session.

**Q4** — `724ef555-a99f-4c0b-8d39-fe79b6346359` *(Quiz B · REMEMBERING)*
What data type does `input()` return in Python?
- Integer
- None of the given options
- ✅ **String**
- Boolean

> *Explanation (platform):* The input() always returns the user input as a string data type.
> **This is the single most important fact in the session.** If >40% miss it, that's your signal to re-run the ALS Activity 1 demo at the start of Session 7.

**Q5** — `36ec33cb-364c-4d7c-9bca-fea7e6cbb919` *(Quiz B · ANALYZING)*
Identify the error in:
```python
username = "Zoe"
print(username[10])
```
- ✅ **IndexError**
- ValueError
- KeyError
- SyntaxError

> *Explanation (platform):* The string "Zoe" has a length of 3, so the highest valid index is 2. Accessing index 10 raises an IndexError because it is out of range.
> **Note the off-by-one:** length 3, highest index 2. Say it out loud — it's the root of most index confusion.

---

## Exit Ticket + Quiz Push (45–48 min)

**Exit ticket** (~30 s) — before anyone leaves:

> `word = "Python"`. Write down: `len(word)`, `word[0]`, and the output of `print("ha" * 3)`.
> **Answers:** `6`, `P`, `hahaha`.

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Open MCQ Practice. Everyone, this room, right now — attempt the first 3 questions before you leave your seat. 99 questions in this pool."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 7's warm-up."*

**Remaining homework**

| Task | Unit |
|---|---|
| Coding Practice — 15 problems | `3ec2d3fe-0670-4186-83ef-7fc0c70b5d6f` |
| MCQ Practice — 99 questions *(started in class above — finish the rest)* | `145ba1e4-adee-4089-b15f-d0bc1e6c85e3` |
| RM — Input and Output Basics | `115d5b6e-cd8c-4925-9f68-5be66507aab4` |

> Say this: *"Fifteen coding problems tonight — the biggest set so far. They're short. If you get a TypeError, read it: it will tell you which two types you tried to mix."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `+` between strings adds a space | Reading habits — words have spaces | Running `"Good" + "Morning"` → `GoodMorning` |
| `input()` returns a number when you type a number | It looks like a number on screen | ALS Activity 1 snippet 4 — `age + 1` → TypeError |
| `"5" + 3` should work, Python is being difficult | Humans convert automatically | Naming it: Python won't guess what you meant |
| Indexing starts at 1 | Everyday counting | Writing `R-a-v-i` over `0-1-2-3` on the board |
| `len("Ravi")` is 4, so `name[4]` is valid | Length and last index feel identical | Quiz Q5 — length 3, highest index 2 |
| All errors are the same | Only category they know | Quiz Q3 and Q5 — TypeError vs IndexError, named separately |

---

## Instructor Notes

- ✅ **Verified against the real deck** (*"Copy of 2.1 Input Output Basics"*). Slide Blocks A and B list the actual slides in order.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Deck slide 4 asks a question it never answers** (`"*" + 10` → *"What will be the output?"*). Running it live is not optional — that TypeError is Quiz Q3.
- **Two ALS activities this session:** Activity 1 is Choral Prediction → Reveal (whole room predicts together, not one student), Activity 2 is Guided Full-Build Dictation (a complete program, not a single gap). The original Fill-the-Blank activity is folded into a 2-minute quick-fill beat at the end of Slide Block A's checkpoint.
- **The Classroom Quiz runs last, right before the Exit Ticket** — never cut, never shortened.
- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair.** Target is 80% platform MCQ attempt rate, currently ~33%.
- ⚠️ **Deck gaps this session's quiz depends on:** concatenation-without-a-space (Q1), `len()` and IndexError (Q5). Both scripted as verbal/live additions above. **Worth raising with the content team.**
- **The session has one load-bearing fact:** `input()` returns a string. Warm-up Q5 measures readiness, Slide Block B states it three times, Quiz Q4 tests it, ALS Activity 1 makes it bite. Protect that chain over everything else.
- **You need a terminal where `input()` visibly waits.** If your setup swallows the prompt, students won't understand what "waiting for input" means. Test before class.
- **Don't teach `int()` or `str()` today.** They're Session 8. Students will ask during ALS Activity 2 — name the session, show the shape of the problem, move on.
- **This session has 15 coding problems** versus 2 in earlier sessions. The Quiz Push and homework readout matter more than usual here — point at the size of the set explicitly.
- **String slicing is *not* in this session** — it's the opening of Session 8's RM despite feeling like it belongs here. Don't pull it forward.
