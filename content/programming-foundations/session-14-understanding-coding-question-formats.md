# Session 14 — Understanding Coding Question Formats

**Duration** 60 min · **Topic** Loops · **Prerequisite** Session 13
**Session type** Support session. No reading material, no classroom quiz.

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Understanding Coding Question Formats | `48f61d2d-48ce-4d61-830f-df02062a43f4` |
| MCQ Practice (23 q) | `67ed319d-5282-470f-bb86-f56ac2283c4c` |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Translate a story-based question into a plain technical statement. *(ANALYZING)*
2. Identify the input, the output, and the rule in any problem statement. *(APPLYING)*
3. Write pseudocode before writing Python. *(APPLYING)*
4. Match a pseudocode description to the code that implements it. *(ANALYZING)*
5. Recognise the vocabulary that hides in story questions — *even*, *divisor*, *palindrome*, *maximum*. *(REMEMBERING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 13**. Newly authored. ~45 s each, project the distribution, never name individuals.

**Q1.** What are the three parts of a while loop?
`A` Start, middle, end · `B` Initialise, condition, update · `C` If, else, end · `D` Input, process, output
→ **B.** *Targets:* The three parts.

**Q2.** How many lines does this print?
```python
i = 0
while i < 3:
    print(i)
    i = i + 1
```
`A` 2 · `B` 3 · `C` 4 · `D` Infinite
→ **B.** *Targets:* Off-by-one.

**Q3.** A loop whose counter is never updated does what?
`A` Errors · `B` Runs once · `C` Runs forever · `D` Runs zero times
→ **C.** *Targets:* Infinite loop.

**Q4.** What stops an infinite loop in the terminal?
`A` Ctrl+C · `B` Ctrl+V · `C` Escape · `D` Nothing
→ **A.** *Targets:* Practical survival. *If >40% wrong:* demonstrate it again right now — 20 seconds.

**Q5.** `while i < 0:` with `i = 0`. How many times does the body run?
`A` Zero · `B` One · `C` Infinite · `D` Error
→ **A.** *Targets:* Condition checked before the first pass.

**Q6.** Which produce an infinite loop? *(MSQ — select all)*
`A` No update inside the body · `B` Update moving away from the condition · `C` Condition stored in a variable before the loop · `D` A correct counter update
→ **A, B and C.** *Targets:* The three loop failures.

**Q7.** Before writing code for a problem, what should you do first?
`A` Start typing · `B` Work out what the input and output are · `C` Search online · `D` Ask a friend
→ **B.** *Targets:* Problem-solving habit. **This is today's whole session.** No wrong-answer shaming — note the number honestly.

---

## Hook (7–10 min)

Put this on the screen. Nothing else.

> *"Mr. Adams is designing a classroom activity to teach students about numbers. He wants the students to find the numbers in a range that can be split into exactly two equal integer values. Write a program that will display such numbers."*

Give them 30 seconds of silence.

> *"Hands up if you know what program to write."*

Usually very few hands. Then:

> *"Read it again. 'Split into exactly two equal integer values.' Six split into three and three. Seven can't. What are we actually being asked for?"*

Wait for **even numbers**.

> *"That's it. Display the even numbers in a range. Four words. And notice — the hard part wasn't the code. You could all write that loop. The hard part was working out what was being asked."*

> *"That's what today is. Not new syntax. Every coding question you'll meet in an exam, an interview, or on this platform is wrapped in a story, and the wrapping is where people lose."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

**Verified against the deck** (*"Copy of Understanding Coding Question Formats"*). Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1 | Welcome | Skip |
| 2 | **Agenda** | Types of Coding Question Formats → Understanding Scenario/Story Format Questions → Tips for Solving Scenario/Story-Based Questions |
| 3 | **Example — Coding Questions** | Two boxes side by side: **Example 1** the long Sarah-teaching-division story · **Example 2** the one-liner *"Write a program to print all factors of a given number"* — the same problem, two formats |
| 4 | **Types of Coding Question Formats** | **Plain Technical Format** · **Scenario/Story Format** · *many more…* |
| 5 | **Example 1** | The Sarah story shown alone, full width |
| 6 | **Question** | *"Have you ever practice these type of questions?"* — a prompt to the room |
| 7 | **Scenario/Story Format Questions** | ⭐ A funnel diagram: **1 Identify Key Information → 2 Convert to Technical Terms → 3 Extract the Core Problem** |

**Beats to emphasise**

- **Slide 3 is the whole session in one picture.** The same problem — find the divisors — written as a five-line story and as a one-line technical statement. Put both on screen and ask *"which would you rather be given, and which will you actually get?"*
- **⭐ Slide 7's funnel is the deck's method, and it is better than a generic "input/output/rule" frame.** Use its three words verbatim — **Identify Key Information → Convert to Technical Terms → Extract the Core Problem** — throughout the session. Activity 1 and Activity 3 both map onto it directly.
- **Slide 6 asks the room a question.** Take a genuine show of hands; it tells you how much of the room has met story-format questions before.
- **Add input/output/rule as a sub-step of funnel stage 1**, not as a competing framework. Write those three words under "Identify Key Information".

**Story words map to technical words.** Build this table on the board *with* the class — ask before you write each right-hand entry:

  | Story says | It means |
  |---|---|
  | "split into two equal integer values" | even |
  | "reads the same forwards and backwards" | palindrome |
  | "divides with nothing left over" | divisible / remainder is 0 |
  | "the biggest one" | maximum |
  | "how many times each appears" | frequency |
  | "numbers that divide it exactly" | divisors / factors |

- **Read the whole question before writing anything.** Students start coding from the first sentence and miss constraints in the last one.

**Checkpoint (at 22 min)** — cold-call two students, using the funnel's words:
> *"Name the three stages of the funnel on slide 7."*
> **Answer:** Identify key information → convert to technical terms → extract the core problem.

**Later slides** (after Activity 1): worked **Examples** comparing *without Scenario/Story* against *Scenario/Story* for the same task — e.g. *"Find the missing number in an array containing n distinct numbers taken from 0 to n"* beside a classroom story about a student who forgot to return their number. The deck closes on a **Practice** section card.

> ⚠️ **The "Examples" slides use arrays and `n distinct numbers`** — content well beyond Session 14. **Use them for the story-vs-technical contrast only.** Do not attempt to solve them; students have not met lists. Say so out loud, or the room will assume they should be able to.

---

## ⚡ Activity 1 — Think–Pair–Share (22–29 min)

### What this activity is

A three-stage discussion. Students think alone (1 min), then discuss with a neighbour (2 min), then a few pairs report to the room (4 min). The staging matters: thinking alone first stops the fastest student setting everyone's answer, and the pair stage lets people rehearse before speaking publicly.

### Why it's here

Translating a story into a technical statement is a judgement, not a fact. Discussion surfaces students' reasoning — which is what needs correcting, not just the answer.

### Before class

Put the story on a slide or the board so it stays visible through all three stages.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:20 | Setup line, reveal the story | Read |
| 0:20–1:20 | **Silence.** Do not talk. | Think alone, write |
| 1:20–3:20 | *"Pairs, go."* | Discuss |
| 3:20–7:00 | Take answers from three pairs | Report |

### Say this

> *"One minute alone — no talking, write something down. Then two minutes with the person next to you. Then I take answers from three pairs. I want three things from you: the input, the output, and the rule."*

### The story

> *"Alice loves playing with words and wants to know if a given word reads the same forwards and backwards. Write a program that helps Alice check if a given word reads the same forwards and backwards."*

### What good answers look like

| | |
|---|---|
| **Technical statement** | Write a program to check if a given word is a palindrome |
| **Input** | A word (a string, from `input()`) |
| **Output** | Something indicating yes or no |
| **Rule** | The word equals itself reversed |

Accept partial answers generously. A pair that identifies input and output but not the word "palindrome" has done the useful part — **the vocabulary is the least important piece.**

### When it goes wrong

| If… | Do this |
|---|---|
| Nobody knows the word "palindrome" | Doesn't matter. Ask for the *rule* in their own words. Give the term afterwards. |
| Pairs go silent immediately | Sharper prompt: *"Just read each other what you wrote."* |
| One pair answers everything | Take from two more anyway: *"Different pair — what did you two have?"* |
| A pair jumps to writing code | Stop them: *"Not yet. I only want the three things."* Code is Activity 2. |
| Room finishes early | Extend: *"What if the word has capital letters? Is `Madam` a palindrome?"* Genuinely ambiguous — good discussion. |

**Common instructor mistake:** filling the one-minute silence with talking. The silence is the activity. Stand still.

**Cut rule:** 30 s think, 90 s pair, two reports.

---

## Practice Set Walkthrough (29–40 min)

> This session has **no classroom quiz pool** on the platform. Instead, work through 5 questions from the **MCQ Practice** set (`67ed319d-5282-470f-bb86-f56ac2283c4c`) live, using the same vote-then-discuss format.

The pool contains two useful question types:

1. **"Which is the correct technical form of this story-based question?"** — exactly the skill from Activity 1.
2. **"Which code matches this pseudocode?"** — the bridge from plan to program.

**Run them like this:** project one, everyone votes, take a reason from someone who voted for a *wrong* option before revealing. The reasoning behind a wrong choice is where the teaching happens.

**A worked example from the pool** — `53b9a322-3a19-4f7c-b415-493a38bc628c`:

> **Pseudocode:**
> 1. Take a number as input.
> 2. If the number is divisible by 2 with no remainder, print "Even".
> 3. Otherwise, print "Odd".

The correct option is:
```python
num = int(input())
if num % 2 == 0:
    print("Even")
else:
    print("Odd")
```

The three wrong options each break one thing — `% 2 == 1` for even, the branches swapped, and `//` instead of `%`. **Walk through why each is wrong**, not just which is right. That comparison is the entire value of the question.

> ⚠️ **The pool also contains `REARRANGE` questions** (e.g. `83ac0e01`, `ddce4f02`) which have **no correct option marked** in the data. Skip them in a live vote — they don't work as MCQs. They're fine as homework on the platform where the interaction is different.

---

## ⚡ Activity 2 — Write the Question (40–48 min)

### What this activity is

Students write a **story-based question** of their own that disguises a simple programming task. You collect a few, read them aloud anonymously, and the class decodes each one back to its technical statement. Writing the disguise forces students to understand how the disguise works.

### Why it's here

It's the session's assessment in disguise. A student who can *build* a story wrapper has understood the structure; one who can only decode may just be pattern-matching.

### Before class

Nothing. Students need paper or the chat.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:40 | Setup line, give the constraints, show the example | Listen |
| 0:40–3:30 | Circulate quietly, pick good ones | Write |
| 3:30–7:00 | Read three aloud, class decodes each | Decode |
| 7:00–8:00 | Debrief | Listen |

### Say this

> *"Everyone writes one story question. Take something simple we can already code — printing numbers, checking even, finding the biggest — and hide it inside a story. Two rules: a classmate must be able to solve it, and you must know the answer."*

### Give the constraints explicitly

- Must be solvable with what we've covered — input, `if`/`else`, `while`
- Must not name the technical word directly (don't write "even", describe it)
- Three sentences maximum
- **You must know your own answer**

### Show this example first

> *"A librarian is arranging books on shelves. Each shelf holds exactly one book. She wants to know how many shelves she needs to number, starting from one, up to the number of books she has. Write a program that displays those numbers."*

Decode it with the class: **print the numbers 1 to n.**

### Running the reports

Read three aloud without naming the author. For each:

1. Class calls out the technical statement.
2. Ask: *"What's the input? The output? The rule?"*
3. Ask the author whether that's what they meant.

**When the class decodes it differently from what the author intended** — that's the best moment available. Say so:

> *"Two different readings of the same question. That's exactly what happens in a real exam, and it's why you read the whole thing twice before you write a line."*

### When it goes wrong

| If… | Do this |
|---|---|
| Stories are too vague to decode | Perfect teaching moment. *"What's missing that would let you solve it?"* Usually the input. |
| Someone writes an unsolvable problem | Ask what tools it would need. Naming the gap is useful. |
| Nobody writes anything | Drop to pairs: *"One between two of you."* |
| Stories name the technical word outright | *"You've given the answer away. Bury it."* |
| Three minutes isn't enough | Give four. The writing is the learning; the decoding is the bonus. |

**Common instructor mistake:** picking only the cleverest stories. A muddled one the class can't decode teaches more about writing clearly than a polished one.

**Cut rule:** Collect two, skip step 3.

---

## ⚡ Activity 3 — Rapid Fire Board Race (48–55 min)

### What this activity is

Two students at the whiteboard. You read a story fragment; both write the technical statement; the class judges. Fast, loud, deliberately low-stakes — this is drilling and an energy lift, not assessment.

### Why it's here

Story-to-technical translation needs repetition to become automatic. It's also minute 48 of a discussion-heavy session and the room needs waking up.

### Before class

Clear a section of whiteboard, two markers.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Call two up, explain the rules | Two go to the board |
| 0:30–5:30 | Read prompts, class judges each | Write; class calls it |
| 5:30–7:00 | Debrief | Listen |

### Say this

> *"Two volunteers. I read a story, you both write the technical version in one line. Class decides. Not a test — a warm-up."*

### The prompts

~20 seconds each.

| # | Story fragment | Technical statement |
|---|---|---|
| 1 | *"Ravi wants to know if his number can be shared equally between two friends with nothing left over."* | Check if a number is even |
| 2 | *"A shopkeeper wants the highest price in his list."* | Find the maximum value in a list |
| 3 | *"Meera wants all the numbers that divide her number exactly."* | Find the divisors of a number |
| 4 | *"A teacher wants the class total divided by how many students there are."* | Calculate the average |
| 5 | *"Convert the distance the runner covered from kilometres into metres."* | Convert km to metres |

### When it goes wrong

| If… | Do this |
|---|---|
| No volunteers | Name two people lightly: *"Front row — you two."* After one round volunteers come easily. |
| Both write the same wrong answer | *"You agree, and you're both wrong. Class?"* |
| Class won't judge | Ask a specific person, not the room. |
| It turns unkind | Cut it short. The energy is the point; humiliation isn't. |
| Answers are wordy | *"One line. A technical statement is short — that's the whole idea."* |

**Common instructor mistake:** letting it run long because it's fun. Hard stop at seven minutes.

**Cut rule:** Prompts 1, 3 and 5.

---

## Exit Ticket + Homework (55–60 min)

**Exit ticket** — before anyone leaves:

> Read this and write the technical statement, plus the input and output:
> *"Priya has a list of daily temperatures and wants to know the coldest day."*
> **Answer:** Find the minimum value in a list. Input: a list of temperatures. Output: the smallest one.

**Homework**

| Task | Unit |
|---|---|
| MCQ Practice — 23 questions | `67ed319d-5282-470f-bb86-f56ac2283c4c` |
| Coding Practice — Session 13 loops set, if unfinished | `e13a266e-9a81-4716-b44f-893002bc30c0` |

> *"Before you write a single line tonight, write three things on paper: input, output, rule. Every time. It feels slower and it isn't."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Being stuck means I can't code | The blocker feels like a coding failure | The hook — everyone could write the loop; nobody could read the question |
| You should start typing immediately | Typing feels like progress | Warm-up Q7 and the input/output/rule frame |
| The first sentence is the whole problem | It reads like the problem | Block A — read it all before writing |
| Story questions are unfair padding | They feel deliberately obstructive | Naming it: every exam and interview does this |
| There's one right way to phrase it | Answers are usually unique | Activity 2 — two valid readings of the same story |
| Pseudocode is a waste of time | It isn't the real deliverable | The walkthrough — matching pseudocode to code |

---

## Instructor Notes

- **Nothing new is taught today.** This session is a skill and a habit — reading a problem before solving it. Judge it by whether students' first move on a hard problem changes from "stare and close the tab" to "write down input, output, rule."
- **This is a recovery window after Session 13.** Loops are the hardest content in the course and some students will be shaken. There's no new syntax here, so if a chunk of the room is still lost on `while`, spend the practice block on loop tracing instead of this set. Say so honestly — students respect it.
- **⚠️ No classroom quiz pool exists** for this session, so the usual quiz block is a live walkthrough of 5 MCQ Practice questions. The pool also contains `REARRANGE` items with no correct option in the data — **don't use those in a live vote.**
- **The MCQ pool is only 23 questions**, the smallest in the first fifteen, and you'll use 5 in class. The practice block needs a second source — Session 13's 112-question loops pool is the natural choice and doubles as revision.
- ✅ **Verified against the real deck** (*"Copy of Understanding Coding Question Formats"*). Slide Block A lists the actual slides in order.
- **⭐ The deck's funnel (slide 7) is its best asset** — *Identify Key Information → Convert to Technical Terms → Extract the Core Problem.* Use those exact words all session. The plan's original input/output/rule frame is now a sub-step of stage 1 rather than a competing method.
- **Slide 3 pairs the same problem in both formats** (long Sarah story vs. one-line technical). That single slide justifies the whole session — don't rush it.
- ⚠️ **The deck's later Examples slides use arrays and `n distinct numbers`**, far beyond Session 14. They work as format contrasts and nothing more. Flagged at the end of Slide Block A.
- **This session has more discussion than any other in the first fifteen.** If your room is quiet by default, Activity 3's board race is the one that reliably breaks the silence — consider moving it earlier.
- **Session 15 is `for` loops** and is the last of this batch. It's a lighter session than 13; students who survived `while` will find `for` a relief. Say so at the end — it's genuinely reassuring.
