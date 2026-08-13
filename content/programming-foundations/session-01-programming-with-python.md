# Session 1 — Programming with Python

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Introduction to Python · **Prerequisite** None — this is day one
**Session type** Concept lecture · **Format** 50-min recalibrated, 2 ALS activities, Classroom Quiz mandatory (never cut)

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Programming with Python | `837f23cb-d3be-4f96-877f-b76f7defe3e2` |
| RM — Programming with Python | `e57497b0-cccd-4ec6-bd44-5c791468d4f0` |
| RM — Python Setup & Coding in VS Code | `292ce498-2b51-44b2-bc2c-65666c09090c` |
| RM — Algorithms, Flowcharts, and Pseudocode | `7516496f-23c2-4460-9691-b70219d4dc8b` |
| Classroom Quiz A (21 q) | `9567f314-fd85-4ef2-a445-6d9907337545` |
| Classroom Quiz B (59 q) | `d303e3b9-9b7a-457b-8357-a74987ba0dcb` |
| MCQ Practice (56 q) | `3c0cf49d-4c57-4468-83ca-63cb7c63b1dd` |
| Coding Practice (2 q) | `81959e79-ceeb-448c-af0e-7e0e7f5447f0` |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define software as a set of instructions to the hardware, and explain what a programming language is for. *(REMEMBERING)*
2. Explain why Python is chosen for this course by comparing it against Java for the same task. *(UNDERSTANDING)*
3. Write and run a `print()` statement that displays a text message. *(APPLYING)*
4. Predict the output of `print()` with and without quotes, and perform arithmetic inside `print()`. *(APPLYING)*
5. Identify the four common `print()` errors — misspelling, capital `P`, missing quotes, missing parenthesis — and correct them. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Projector on, previous class cleared out, attendance done, students actually seated before you start the clock on anything below. **This is real, planned time — don't try to teach through it.** If your room is usually settled faster, don't reclaim the minutes for content; hold them as extra flex at the end instead.

---

## Warm-Up Poll — Diagnostic (3–7 min) · ALS: Polling

> **This session is the exception.** There is no previous session to recall, so the poll is a *diagnostic*, not retrieval practice. No wrong answers. Purpose is to calibrate pace and to establish, on minute one, that this classroom expects everyone to answer.

Say: *"Five quick questions. Nobody is graded, nobody is named. I need to know who I'm teaching."*

**Q1.** Have you written a computer program before — any language?
`A` Never · `B` Tried once or twice · `C` A few small programs · `D` Yes, comfortably
→ *Read:* If A+B > 60%, keep every code example at RM pace and do not skip the VS Code walkthrough.

**Q2.** Have you used Python specifically?
`A` No · `B` Heard of it, never used it · `C` Some · `D` Regularly

**Q3.** Do you have Python installed on the laptop you'll use for this course?
`A` No · `B` Not sure · `C` Yes · `D` Yes, plus VS Code
→ *Read:* Anything below 70% at C/D means you assign the Python Setup RM as compulsory homework tonight, not optional.

**Q4.** When you hear "software", what comes to mind first?
`A` Apps on my phone · `B` Windows / operating system · `C` Instructions a computer follows · `D` Not sure
→ *Read:* C is where the session lands. If almost nobody picks C, that's your hook — don't correct it now, let Slide Block A do it.

**Q5.** In your own guess — what does `print("Hello")` do?
`A` Prints on paper · `B` Shows `Hello` on screen · `C` Shows `"Hello"` with quotes · `D` No idea
→ *Read:* C is the quotes misconception showing up early. Note the number; you'll revisit it in ALS Activity 2.

**Running it** — poll tool, ~40 s per question, project the distribution after each. Never name individuals. Total 3.5 min for the 5 questions.

**Explain-the-answer beat (~20 s):** don't just move on — say out loud: *"Most of you landed on [C] for Q4/Q5 or not — either way, that's exactly what today fixes."* One line, keep moving — this is the one line that tells the room the session is already teaching, not just polling.

---

## Hook (7–11 min)

> **Do not use the Java-vs-Python comparison here.** It is slide 16 of your own deck
> ("Easy to Learn"), further along. Showing it twice kills it.

Stand at the board with a marker. Ask for one volunteer to stay seated and give you
instructions.

> *"I am now a computer. I will do **exactly** what you tell me — nothing more, nothing
> less. Your job: get me to write your name on that board."*

Follow every instruction with deliberate literalism. *"Pick up the marker"* — pick it up
and stop. *"Write my name"* — write the words "my name". *"Go to the board"* — walk into
it, or walk anywhere but the board. Keep going until the room is laughing and the
volunteer is exasperated.

Then stop and land it:

> *"You knew exactly what you wanted. You just couldn't say it precisely enough. That is
> the entire job. A computer is fast, obedient, and completely stupid — it does what you
> said, not what you meant. Today you start learning how to say things precisely."*

**Real-life anchor (30 s, folded into the hook — not a separate activity):** *"Quick one — name one app you used in the last hour. [take 2–3 shouted answers] Every single feature in that app is somebody having this exact conversation with a computer. That's all software is."*

Tie back to **Q4** of the poll — *"Most of you said software is the apps on your phone.
In two minutes you'll have a sharper answer than that."*

This sets up the Software slide directly, and it sets up both ALS activities, where you
type literally what students say.

---

## Slide Block A (11–19 min) — DELIVER SLIDES AS-IS

**Verified against the deck.** Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1–2 | Welcome · Title | Skip quickly |
| 3–8 | **Agenda** (animated build) | Introduction → Programming Language → Using Python as a Calculator, with callouts for Basic Terminology, Why Python?, Arithmetic Operators |
| 9 | **Software** | "Software is a set of instructions to the hardware" |
| 10 | **Programming Language** | Give instructions in a language the computer understands |
| 11 | **Popular Programming Languages** | Logo wall, ~700 languages |
| 12 | **Why Python? — Versatile Language** | AI/ML, Big Data, IOT, Game Dev, Backend |
| 13 | **Why Python? — Plenty of Opportunities** | Data Scientist, ML Engineer, Python Developer, DevOps, Software Developer, Data Analyst |
| 14 | **Huge Salaries** | ~$91,000 / ~₹66,00,000, sourced to PayScale |
| 15 | **Demand for Python** | Hacker News hiring-trends chart |
| 16 | **Easy to Learn** | Java vs Python "Hello World" side by side |

**Beats to emphasise**

- **Slide 9 is the payoff of your hook.** Land it in one line: software is instructions, and instructions have to be exact — which they just watched fail at the board.
- **Slides 12–15 are four consecutive motivation slides — tightest squeeze in the 50-min version.** Cap the whole block at **2 minutes total**: one breath on Versatile + Opportunities together, one breath on Salaries + Demand together. Do not narrate each bullet — point and move. The session's time budget is in the two ALS activities, not here.
- **Slide 16 (Java vs Python) is the one to slow down on.** Ask *"show of hands — who wants to learn the top one?"* here, not earlier.

> ⚠️ **The deck has no slide for *Code* or *Syntax*** — those terms appear only in the Reading Material. But **Classroom Quiz Q2 asks for the definition of syntax**, and Quiz A contains several more syntax questions. **You must teach both verbally**, or students will be assessed on something they were never shown. Thirty seconds on slide 10 is enough:
> *"The instructions you write are called **code**. Every language has rules for writing that code — like grammar — and those rules are called **syntax**. Get the syntax wrong and the computer rejects the whole thing."*

**Checkpoint (at 19 min)** — 10 s silent think, then cold-call two students:
> *"What is software, and what is syntax?"*
> **Answer:** Software is a set of instructions to the hardware. Syntax is the set of rules those instructions must follow.

---

## ⚡ ALS Activity 1 — Error-Spotting Pairs (19–25 min)

**ALS format:** Individual → Pair → Share (error-analysis variant). Snippets are taken verbatim from the RM's *Possible Mistakes* section — nothing new. Chosen over a straight Think-Pair-Share because the payoff here is a real error message, not just a discussed opinion.

**Setup line (say this):**
> *"Four broken lines. 30 seconds, silent, on your own — find the error and predict what Python will say back. Then 30 seconds with the person next to you — compare and agree on one answer per line."*

Put all four on screen at once:

```python
prnt("Hello World!")        # 1
Print("Hello World!")       # 2
print(Hello World!)         # 3
print("Hello World!"        # 4
```

**What students do:** 30 s silent individual attempt → 30 s pair comparison → one pair per snippet shares out.

**Answers**

| # | Error | What Python says |
|---|---|---|
| 1 | `print` misspelled as `prnt` | `NameError` — Python has no function by that name |
| 2 | Capital `P` | `NameError` — Python is case-sensitive, `Print` ≠ `print` |
| 3 | Missing quotes | `SyntaxError` — without quotes Python reads `Hello World!` as code, not text |
| 4 | Missing closing parenthesis | `SyntaxError` — Python is still waiting for you to finish the line |

**How it surfaces:** After each pair shares, type the broken line live and run it so the class sees the real error message. This is the point of the activity — students must learn error messages are readable, not scary.

**Debrief line:**
> *"Three of these four are just typing. That's the job. You will not be stuck because you can't think — you'll be stuck because of a capital letter. Read the error message, it tells you which line."*

**Cut rule:** If running late, skip the pair-compare step and go straight from individual guess to share on snippets 2 and 3 only — they carry case-sensitivity and the quotes rule, which are the two that recur all course.

---

## Slide Block B (25–32 min) — DELIVER SLIDES AS-IS

**Verified against the deck.** Slides, in order:

| # | Slide | Content |
|---|---|---|
| 17 | **Your First Program** | `print("Hello World!")` with its output shown |
| 18 | **Possible Mistakes** | Table of four: `prnt(…)`, `Print(…)`, missing quotes, missing parenthesis |
| 19 | **Addition** | `2 + 5` → `print(2 + 5)` → `7` |
| 20 | **Printing the Result** | `print(2 + 5)` → `7` **beside** `print("2 + 5")` → `2 + 5` |
| 21 | **Subtraction** | `print(5 - 2)` → `3` |
| 22 | **Multiplication** | `print(2 * 5)` → `10` |
| 23 | **Division** | `print(6 / 3)` → `2.0` |
| 24 | All The Best | Closing card |

**Beats to emphasise**

- **Slide 18 (Possible Mistakes) is exactly ALS Activity 1, already run.** Deliver the table in one breath as a recap — *"you already broke every one of these"* — don't re-teach it.
- **Slide 20 is the most important slide in the deck.** The quotes contrast is already side by side. Pause here, take a show of hands on each output before revealing, then move straight into ALS Activity 2 — it drills exactly this.
- **Slide 23 (Division):** the deck's example is `print(6 / 3)` giving **`2.0`**, not `2`. Flag it: *"remember this, it comes back in Type Conversions."* Don't explain floats yet.

**Checkpoint (at 32 min)** — 10 s silent think, then show hands:
> *"`print(6 / 3)` — who says `2`? Who says `2.0`?"*
> **Answer:** `2.0`. Python's `/` always gives a decimal result.

---

## ⚡ ALS Activity 2 — Predict & Verify (32–38 min)

**ALS format:** Individual predict → instructor-run verification (live-coding variant of Polling). Chosen instead of another Think-Pair-Share so students commit to an answer *before* seeing it run, rather than discussing an opinion — this is the session's single highest-stakes misconception and needs individual accountability, not group averaging.

> Slide 20 already showed `print(2 + 5)` beside `print("2 + 5")`. The value here is that students commit to an answer *before* each run, and watch it typed live rather than pre-rendered. Say so: *"You've seen this on a slide. Now you get to be wrong about it out loud, which is how it sticks."*

**Setup line (say this):**
> *"Editor is open, I'm typing, you're predicting. Before I hit run, everyone commits to an answer out loud or on the poll. If you're wrong, that's the useful part."*

Type and run these **one at a time**, taking an individual prediction before each. Cut down to the four lines that carry the whole point (per cut rule below):

```python
print("Hello World!")    # → Hello World!
print(2 + 5)             # → 7
print("2 + 5")           # → 2 + 5
print(6 / 3)             # → 2.0
```

**The deliberate bug** — after the four above, type this and run it:

```python
Print("I can code")
```

Let the `NameError` appear. Ask: *"30 seconds with your neighbour — agree on the fix."* Take the instruction from one pair and type exactly what they say.

**Debrief line:**
> *"Quotes mean 'print these exact characters.' No quotes means 'work it out, then print the answer.' That one rule explains half the confusion in your first week."*

**Cut rule:** If running late, drop `print("Hello World!")` from the predict list (already established) and go straight from `print(2 + 5)` → `print("2 + 5")` → deliberate bug. Never drop the quotes-pair or the deliberate bug — those are the whole point.

---

## Classroom Quiz (38–45 min) · ALS: Individual Answer → Reveal

> 🔒 **Mandatory block — do not cut, do not shorten, do not skip under time pressure.** Runs **last, right before the Exit Ticket** — a cumulative check across both slide blocks and both ALS activities, not a mid-session interruption. This is the only hard data you get on whether the class actually followed the session. If you're running behind by the time you reach it, that's what the cut rules on the Hook, both Slide Blocks, and both ALS activities are for — protect these 7 minutes first, and if you're still short, dip into the 2-min end buffer or shorten the homework read-out, not this block.

Every question below is run ALS-style, not read-and-reveal: **individual silent answer first (poll or show of fingers), then explanation.** No question goes straight to the answer key.

5 MCQs from the platform pools. Run at ~85 s each including the individual-answer beat and discussion.

**Q1** — `7918cf2f-e55d-411b-b16e-501709630ca2` *(Quiz A · REMEMBERING)*
Which of the following is referred as software in computer programming?
- ✅ **A set of instructions to the hardware**
- A physical component of a computer system
- A user interface design
- A type of computer virus

> *Explanation (platform):* In computer programming, software refers to a set of instructions that the hardware executes to perform tasks, not a physical component, a design element, or a virus.
> **If they pick "physical component":** they're conflating hardware with software. Point at the laptop, then at the code on screen.

**Q2** — `31ad6935-bb8a-4e34-a34c-17249e2c06c6` *(Quiz A · REMEMBERING)*
Which of the following best describes 'syntax' in programming languages?
- The instructions for installing software
- ✅ **The rules for writing code.**
- The process of compiling a program
- The user interface of a development environment

> *Explanation (platform):* Syntax in programming languages is the set of the rules for writing the code, ensuring that it is correctly formatted and can be understood by the computer.
> ⚠️ **The deck never defines syntax** — see the note in Slide Block A. If you skipped the verbal 30 seconds there, this question is unanswerable and the whole room will miss it. That's a deck gap, not a student failure.
> **If they pick "process of compiling":** the grammar analogy didn't land. Re-run it in one sentence before moving on.

**Q3** — `2bb88302-3225-4cf9-86bb-6b49fd71e4fe` *(Quiz A · UNDERSTANDING)*
Select the code that correctly prints "Hello World" in Python.
- ✅ **`print("Hello World")`**
- `echo "Hello World"`
- `Console.WriteLine("Hello World");`
- `System.out.println("Hello World");`

> *Explanation (platform):* In Python, the `print` statement is used to display text.
> **If they pick the Java option:** they were pattern-matching on the hook rather than reading. Harmless — say so and move on.

**Q4** — `3dcc4930-83e1-4f21-87d1-6184c5d5a652` *(Quiz B · APPLYING)*
Which of the following will fix the error in `Print("Hello World!")`?
- ✅ **The 'print' function should start with a lowercase 'p'.**
- The message should not be in quotes.
- The 'print' function should not have parentheses.
- There is no error in the code.

> *Explanation (platform):* In Python, the syntax rules require that the `print()` function name be written in lowercase. Using an uppercase 'P' as in `Print()` violates Python's syntax rules and will cause an error.
> **If >40% miss this:** stop. Python is case-sensitive and they haven't internalised it. State it as a rule, write it on the board, leave it there for the rest of the session.

**Q5** — `a51ca9ea-ee77-443b-bb3a-17672eebd42f` *(Quiz B · APPLYING)*
What will be the output of `print("2 + 5")`?
- `2`
- ✅ **`2 + 5`**
- `"7"`
- `7`

> *Explanation:* **[authored — the platform record for this question has an empty explanation field]** The quotes make `2 + 5` a text message, not a calculation. Python prints the characters exactly as written. Remove the quotes and Python does the arithmetic instead, giving `7`.
> **If they pick `7`:** the single most common misconception of this session — this is the confirmation check. It was already drilled live in ALS Activity 2; if it's still failing here, that's your signal to reopen it at the start of Session 2, not something to re-teach in the seconds you have left now.

---

## Exit Ticket + Homework (45–48 min)

**Exit ticket** — on paper or in chat before anyone leaves:

> Write the one line of Python that prints your own name, and next to it write what `print(3 * 4)` outputs.
> **Answers:** `print("Your Name")` (quotes required) and `12`.

Scan the responses on the way out. Missing quotes is the signal to open Session 2 with a quick recap.

**Homework** (read the list, don't walk through it — time's up):

| Task | Unit |
|---|---|
| Coding Practice — *Hello World*, *Three Hashes* | `81959e79-ceeb-448c-af0e-7e0e7f5447f0` |
| MCQ Practice — 56 questions | `3c0cf49d-4c57-4468-83ca-63cb7c63b1dd` |
| RM — Programming with Python | `e57497b0-cccd-4ec6-bd44-5c791468d4f0` |
| **RM — Python Setup & Coding in VS Code (compulsory if poll Q3 was weak)** | `292ce498-2b51-44b2-bc2c-65666c09090c` |
| RM — Algorithms, Flowcharts, and Pseudocode | `7516496f-23c2-4460-9691-b70219d4dc8b` |

Tell them: *"Next session is a walkthrough of these exact coding problems. Attempt them first — a walkthrough of something you haven't tried is a waste of your hour."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. Use it for: a slow exit ticket, dismissal, or absorbing a small overrun from any block above. **If you reach here with time still on the clock, let the session end early** — don't stretch content to fill it. If a block overran and you're here with none left, this is why the Classroom Quiz was never touched — everything else had cut rules built in for exactly this moment.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `print("2 + 5")` outputs `7` | They read for meaning; quotes look decorative | Running both lines back-to-back in ALS Activity 2 |
| `Print` and `print` are the same | Every other written language they know is case-forgiving | Showing the raw `NameError`, then writing "Python is case-sensitive" on the board and leaving it up |
| `print(10 / 5)` outputs `2` | Whole-number division from school maths | Running it; flag that `2.0` returns in Type Conversions |
| Error messages mean "you failed" | School conditioning | Deliberately breaking your own code in ALS Activity 2 and reading the message aloud calmly |
| Software = the apps on my phone | Only consumer-facing software is visible | Slide Block A, reinforced by the hook's real-life anchor |

---

## Instructor Notes

- ✅ **Verified against the real deck** (*"Copy of 1.1 Programming with Python"*, 41 animation steps, ~20 distinct slides). Slide Blocks A and B list the actual slides in order — no longer inferred.
- **50-min format, recalibrated from the original 60-min plan: 45 min instruction + 5 min buffer (3 min settling at the start, 2 min flex at the end).** Every section above has a tighter window than before — this is the actual delivery constraint, not a suggestion. If you overrun anywhere, use the cut rules given in each block first; the end buffer is the last resort, not the first one.
- **The Classroom Quiz runs last, right before the Exit Ticket** — a deliberate cumulative check across everything taught, not a mid-session interruption. It's the one block that never moves: it still gets its full 7 minutes even if the session is running behind. Protect it by trimming earlier blocks (Hook, both Slide Blocks, both ALS activities all have cut rules for exactly this); if you're still short by the time you reach it, dip into the 2-min end buffer or shorten the homework read-out instead. It's the only point in the session where you get real signal on whether the room followed.
- **Exactly two ALS (Active Learning Strategy) activities this session, deliberately different formats** — not the same strategy twice: Activity 1 is Individual→Pair→Share (error analysis), Activity 2 is Individual-Predict→Verify (a Polling variant). Pick the ALS format per session based on what the content needs — don't default to Think-Pair-Share every time.
- **The Classroom Quiz is also run ALS-style** — individual answer first, then reveal — not read-question-then-answer. Any question on a slide gets the same treatment: think first, then check.
- **The deck is heavily animated.** Many "slides" are builds — the agenda alone takes six clicks. Don't be surprised when a click reveals one more arrow rather than a new slide.
- ⚠️ **Deck gap: no slide defines *code* or *syntax*,** yet Classroom Quiz A is full of syntax questions and this session's Quiz Q2 asks for the definition outright. The 30-second verbal fix is scripted in Slide Block A. **Worth raising with the content team** — every instructor who follows the deck alone will fail that question.
- **Pacing risk:** slides 12–15 are four consecutive motivation slides (Versatile, Opportunities, Salaries, Demand). In the 50-min version these get 2 minutes total, not 12 — cap it hard, they carry no skill.
- **Have the editor already open** with a blank file before the session starts. Setting up VS Code live burns time you don't have.
- **Day-one dynamic:** students will not volunteer yet. ALS Activity 1's individual-then-pair structure is deliberately the lowest-risk way to get a first answer out of a silent room before Activity 2 asks for a public prediction.
- **Data note:** the poll here is diagnostic because there's no prior session, and is capped at 5 questions per the 50-min format. From Session 2 onward, warm-up polls are retrieval practice on the previous session, also capped at 4–5 questions.
- **Quiz Q5 (`a51ca9ea`) has an empty `answer_explanation` on the platform.** The explanation above is authored — review it before use, and consider filing a content fix.
- The two RMs on *Python Setup* and *Algorithms, Flowcharts, Pseudocode* are attached to this session but are **not** covered in the lecture. They are homework only. Say this explicitly or students will expect them in class.
