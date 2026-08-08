# Session 6 — Input and Output Basics

**Duration** 60 min · **Topic** Sequence of Instructions · **Prerequisite** Session 5
**Session type** Concept lecture

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

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 5**. Newly authored. ~45 s each, project the distribution, never name individuals.

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

**Q3.** `a = 5`, then `a = a + 3`. What's in `a`?
`A` `5` · `B` `8` · `C` `53` · `D` Error
→ **B.** *Targets:* Reassignment using the old value.

**Q4.** What does `print(10 / 2 + 3)` output?
`A` `13.0` · `B` `8.0` · `C` `8` · `D` `6.5`
→ **B.** *Targets:* BODMAS + division returns a float. *Misconception:* C means they've forgotten division always gives a decimal.

**Q5.** A leading space before a line gives which error?
`A` NameError · `B` SyntaxError · `C` IndentationError · `D` No error
→ **C.** *Targets:* Indentation.

**Q6.** Which run without error? *(MSQ — select all)*
`A` `x = 5` · `B` `5 = x` · `C` `x = x` after `x = 1` · `D` `print(x)` before `x = 1`
→ **A and C.** *Targets:* Assignment direction. *Misconception:* picking B means the left-right direction of `=` isn't fixed yet.

**Q7.** What's the data type of `"10"`?
`A` Integer · `B` String · `C` Float · `D` Boolean
→ **B.** *Targets:* Quotes decide type. **This is today's gateway** — `input()` returns a string, and if this isn't solid nothing after minute 34 will land. Note the number.

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

Tie back to **Q7** — *"Hold on to that. Whatever the user types, Python hands it back as a string. Every single time. That fact causes about half the bugs you'll hit this month."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

**Verified against the deck** (*"Copy of 2.1 Input Output Basics"*). Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1–2 | Welcome · **Recap — Order of Operations** | `5 * 2 + 3 * 4` → 22, with the BODMAS badges |
| 3 | **Adding Strings** | `a = "1" + "2"` → **`12`**. "Adding strings is called **String Concatenation**" |
| 4 | **String Concatenation** | `a = "*" + 10` → *"What will be the output?"* — posed as a question, no answer on the slide |
| 5 | **String Concatenation** | `a = "*" * 10` → `**********`. "String will be repeated 10 times. This is called **String Repetition**" |

**Beats to emphasise**

- **Slide 1–2 is a recap your warm-up poll already did.** Twenty seconds.
- **Slide 3's example is `"1" + "2"` → `12`, not `3`.** That is the strongest possible opening for this session — two things that look like numbers, added, giving a joined string. Take a prediction before revealing.
- **Slide 4 is deliberately unanswered.** The deck asks *"what will be the output?"* and moves on. **Do not skip past it — run it live.** `"*" + 10` raises a `TypeError`, and that error is Quiz Q3. If you don't run it, the class never sees the answer to a question the deck explicitly asked.
- **Slides 4 and 5 are the pair:** `"*" + 10` fails, `"*" * 10` works. Same two values, different operator. Show them back to back.

> ⚠️ **The deck never shows concatenation *with a space*** — no `"Good" + "Morning"` → `GoodMorning` example. **Quiz Q1's answer hinges on "without adding space."** Add it verbally: type `print("Good" + "Morning")` and let the missing space land.

**Checkpoint (at 22 min)** — cold-call two students:
> *"What does `"ab" * 3` give, and what does `"ab" + 3` give?"*
> **Answer:** `ababab`, and a TypeError.

---

## ⚡ Activity 1 — Fill the Blank Live (22–27 min)

### What this activity is

You put code on the projector with a piece missing. Students call out what fills the gap, and **you type exactly what they say — including if it's wrong.** You never silently correct them. The activity works because the gap between what students *mean* and what they *say* is invisible until someone types it literally.

### Why it's here

Students can recognise correct string operations but can't yet produce them. This exposes that gap cheaply.

### Before class

Nothing to prepare beyond having the editor open on the projector.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Say the setup line, put blank 1 on screen | Read it |
| 0:30–1:30 | Take an answer, type it **literally**, run it | Call out answers |
| 1:30–3:30 | Repeat for blanks 2 and 3 | Call out, react to failures |
| 3:30–5:00 | Debrief | Listen |

### Say this

> *"I'm typing exactly what you say. Not what you meant — what you said. If you say it wrong, we're all going to watch it break."*

### The blanks

Put them up one at a time. Target answer on the right — do not show it.

| # | On screen | Target |
|---|---|---|
| 1 | `print("ab" ___ 3)` — *"make it print `ababab`"* | `*` |
| 2 | `print("ab" ___ 3)` — *"now make it break"* | `+` → TypeError |
| 3 | `print("Hi" + ___ + "there")` — *"put a space between the words"* | `" "` |

### Answers and what they reveal

- **Blank 1 → `*`.** If someone says `+`, type it and run it. The TypeError does the teaching.
- **Blank 2 → `+`.** This one's a gift — they get to *choose* to break it, which removes the fear of errors.
- **Blank 3 → `" "` with quotes.** Most rooms say "space" without the quotes. Type `space` literally and let the `NameError` appear, then ask what's missing.

### When it goes wrong

| If… | Do this |
|---|---|
| Nobody answers | Wait 10 full seconds. Then: *"I'll take a wrong answer. Wrong is fine."* Silence usually breaks. |
| Everyone shouts at once | *"One voice. Third row, you."* Pick a specific person, not a volunteer. |
| First answer is correct immediately | Still type it, still run it. Then ask *"what would `+` have done?"* and run that too. |
| Someone gets defensive when theirs breaks | *"That's the most useful thing that's happened in ten minutes. Everybody just learned that."* Move on fast. |

**Common instructor mistake:** silently fixing a student's answer as you type it. That destroys the entire point — the literal typing *is* the lesson.

**Cut rule:** Blanks 1 and 3 only.

---

## Classroom Quiz (27–34 min)

5 MCQs from the platform pools. ~80 s each including discussion.

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
> **This is the single most important fact in the session.** If >40% miss it, stop everything and demonstrate: `age = input()` then `print(age + 1)` → TypeError. Do not proceed until it lands.

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

## Slide Block B (34–44 min) — DELIVER SLIDES AS-IS

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

**Checkpoint (at 44 min)** — show hands:
> *"`name = "Ravi"`. What is `name[0]`, and what is `len(name)`?"*
> **Answer:** `R` and `4`. Note that the last valid index is 3, not 4.

---

## ⚡ Activity 2 — Predict the Output (44–50 min)

### What this activity is

You show a code snippet and **every student commits to an answer out loud before you run it.** Then you run it. The value is entirely in the commitment — a student who has publicly guessed `13` remembers the correction far longer than one who passively watched.

### Why it's here

The string-vs-number confusion is invisible until it produces a wrong answer. This makes it visible in six minutes.

### Before class

Have all four snippets in a file, ready to run one at a time. Don't paste them all on screen at once — reveal one at a time.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:20 | Setup line | Listen |
| 0:20–4:30 | Reveal snippet, take a chorus prediction, **then** run | Predict out loud, react |
| 4:30–6:00 | Debrief | Listen |

### Say this

> *"Before I hit run, everyone says the answer out loud. Together. Being wrong out loud is the fastest way to never be wrong again."*

### The snippets

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

### Answers

| # | Output | Why |
|---|---|---|
| 1 | `53` | Two strings — joined, not added |
| 2 | `555` | String repeated three times |
| 3 | **TypeError** | Can't join a string to a number |
| 4 | **TypeError** | `input()` gave a string, so `age + 1` is string + number |

**Snippet 4 is the point of the session.** Everything before it is setup.

### When it goes wrong

| If… | Do this |
|---|---|
| Room predicts correctly every time | Good — go straight to 4, which almost nobody gets. |
| Nobody will call out | Make it a hands vote: *"Hands up for 8. Hands up for 53."* Voting is easier than speaking. |
| Someone explains before you run it | *"Hold it — don't tell them yet."* The reveal has to come from the run. |
| Running late | Skip 2. Never skip 3 or 4. |

**Common instructor mistake:** running the snippet before the prediction. Once output is on screen, the activity is worthless — it becomes a demo.

**Cut rule:** Snippets 1, 3 and 4.

---

## ⚡ Activity 3 — Live Coding: Build a Greeting (50–57 min)

### What this activity is

You are at the keyboard on the projector. **Students give every instruction; you type only what is said.** You deliberately introduce one bug along the way and let the class find it. It differs from Fill the Blank Live in that students drive the *whole program*, not a single gap.

### Why it's here

It assembles everything from the session — `input()`, concatenation, `len()` — into one working program, which is also the shape of tonight's homework.

### Before class

Empty file open, font ≥18pt, terminal visible so `input()` prompts are seen.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, state the goal | Listen |
| 0:30–4:00 | Ask *"what's the next line?"*, type what's said, run often | Dictate lines |
| 4:00–6:00 | Introduce the bug, let them find it | Diagnose |
| 6:00–7:00 | Debrief | Listen |

### Say this

> *"You're writing this, I'm just the keyboard. Goal: ask the user their name, then print a greeting that also says how many letters are in their name."*

### Target program

```python
name = input()
print("Hello " + name)
print("Your name has " + str(len(name)) + " letters")
```

Build it a line at a time. Run after every line — students need to see it working incrementally.

### The deliberate bug

When you reach the third line, type this instead and run it:

```python
print("Your name has " + len(name) + " letters")
```

**Output:** `TypeError: can only concatenate str (not "int") to str`

> *"Read the error. It's telling you exactly what's wrong — in plain English. What is it saying?"*

Take the diagnosis from students. `len()` returns a number; you can't join a number to a string. **If nobody knows the fix, that's fine** — `str()` arrives properly in Session 8. Say so:

> *"There's a tool for this called `str()`. You'll meet it properly in two sessions. For now, notice the shape of the problem — Python is very fussy about mixing types."*

Then add `str()` and run the working version.

### When it goes wrong

| If… | Do this |
|---|---|
| Nobody offers a first line | Give line 1 yourself, ask for line 2. Momentum matters more than purity. |
| They dictate the whole program instantly | Great — spend the saved time on the bug and let two students explain the fix. |
| The class fixates on `str()` | Cap it at 90 seconds. Name Session 8 and move on. |
| Someone suggests a different valid solution | Type it. Run it. If it works, say so — there's more than one right answer. |

**Common instructor mistake:** typing ahead when students hesitate. The silence is productive. Wait.

**Cut rule:** Build lines 1 and 2 only, then jump to the bug on line 3.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — before anyone leaves:

> `word = "Python"`. Write down: `len(word)`, `word[0]`, and the output of `print("ha" * 3)`.
> **Answers:** `6`, `P`, `hahaha`.

**Homework**

| Task | Unit |
|---|---|
| Coding Practice — 15 problems | `3ec2d3fe-0670-4186-83ef-7fc0c70b5d6f` |
| MCQ Practice — 99 questions | `145ba1e4-adee-4089-b15f-d0bc1e6c85e3` |
| RM — Input and Output Basics | `115d5b6e-cd8c-4925-9f68-5be66507aab4` |

> Say this: *"Fifteen coding problems tonight — the biggest set so far. They're short. If you get a TypeError, read it: it will tell you which two types you tried to mix."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `+` between strings adds a space | Reading habits — words have spaces | Running `"Good" + "Morning"` → `GoodMorning` |
| `input()` returns a number when you type a number | It looks like a number on screen | Activity 2 snippet 4 — `age + 1` → TypeError |
| `"5" + 3` should work, Python is being difficult | Humans convert automatically | Naming it: Python won't guess what you meant |
| Indexing starts at 1 | Everyday counting | Writing `R-a-v-i` over `0-1-2-3` on the board |
| `len("Ravi")` is 4, so `name[4]` is valid | Length and last index feel identical | Quiz Q5 — length 3, highest index 2 |
| All errors are the same | Only category they know | Quiz Q3 and Q5 — TypeError vs IndexError, named separately |

---

## Instructor Notes

- ✅ **Verified against the real deck** (*"Copy of 2.1 Input Output Basics"*). Slide Blocks A and B list the actual slides in order.
- **Deck slide 4 asks a question it never answers** (`"*" + 10` → *"What will be the output?"*). Running it live is not optional — that TypeError is Quiz Q3.
- ⚠️ **Deck gaps this session's quiz depends on:** concatenation-without-a-space (Q1), `len()` and IndexError (Q5). All three scripted as verbal/live additions above. **Worth raising with the content team.**
- **The session has one load-bearing fact:** `input()` returns a string. Warm-up Q7 measures readiness, Slide Block B states it three times, Quiz Q4 tests it, Activity 2 makes it bite. Protect that chain over everything else.
- **You need a terminal where `input()` visibly waits.** If your setup swallows the prompt, students won't understand what "waiting for input" means. Test before class.
- **Don't teach `int()` or `str()` today.** They're Session 8. Students will ask during Activity 3 — name the session, show the shape of the problem, move on. Feeling the problem first makes Session 8 land much harder.
- **Pacing risk:** Slide Block A's pattern example (`* * * Python * * *`) is fun and can eat five minutes. Cap it at two.
- **This session has 15 coding problems** versus 2 in earlier sessions. The practice block will feel very different — the playbook's "problem 1 together" step matters more than usual here.
- **String slicing is *not* in this session** — it's the opening of Session 8's RM despite feeling like it belongs here. Don't pull it forward; Session 8 needs the runway.
