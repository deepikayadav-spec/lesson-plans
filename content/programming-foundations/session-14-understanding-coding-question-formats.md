# Session 14 — Understanding Coding Question Formats

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Loops · **Prerequisite** Session 13
**Session type** Support session. No reading material, no classroom quiz pool. · **Format** 50-min recalibrated, 2 ALS activities

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

## Classroom Settling (0–3 min) · Buffer — not instructional

Projector on, deck loaded, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** state the MCQ Practice completion number since last session. Target is 80%.

5 questions on **Session 13**. ~45 s each, project the distribution, never name individuals.

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

**Q3.** What stops an infinite loop in the terminal?
`A` Ctrl+C · `B` Ctrl+V · `C` Escape · `D` Nothing
→ **A.** *Targets:* Practical survival. *If >40% wrong:* demonstrate it again right now — 20 seconds.

**Q4.** `while i < 0:` with `i = 0`. How many times does the body run?
`A` Zero · `B` One · `C` Infinite · `D` Error
→ **A.** *Targets:* Condition checked before the first pass.

**Q5.** Before writing code for a problem, what should you do first?
`A` Start typing · `B` Work out what the input and output are · `C` Search online · `D` Ask a friend
→ **B.** *Targets:* Problem-solving habit. **This is today's whole session.** No wrong-answer shaming — note the number honestly.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–11 min)

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

## Slide Block A (11–20 min) — DELIVER SLIDES AS-IS

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
- **⭐ Slide 7's funnel is the deck's method, and it is better than a generic "input/output/rule" frame.** Use its three words verbatim — **Identify Key Information → Convert to Technical Terms → Extract the Core Problem** — throughout the session.
- **Slide 6 asks the room a question.** Take a genuine show of hands.
- **Add input/output/rule as a sub-step of funnel stage 1**, not as a competing framework.

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

**Checkpoint (at 20 min)** — 10 s silent think, cold-call two students, using the funnel's words:
> *"Name the three stages of the funnel on slide 7."*
> **Answer:** Identify key information → convert to technical terms → extract the core problem.

> ⚠️ **Later deck slides use arrays and `n distinct numbers`** — well beyond Session 14. If you show them, use them for the story-vs-technical contrast only. Students have not met lists.

---

## ⚡ ALS Activity 1 — Think-Pair-Share (20–27 min)

**ALS format:** Think-Pair-Share. Chosen because translating a story into a technical statement is a judgement, not a fact — discussion surfaces students' reasoning, which is what needs correcting, not just the answer.

**Setup line:**
> *"One minute alone — no talking, write something down. Then two minutes with the person next to you. Then I take answers from three pairs. I want three things from you: the input, the output, and the rule."*

**Timing:** 1 min silent · 2 min pairs · 4 min report-out from three pairs.

**The story:**
> *"Alice loves playing with words and wants to know if a given word reads the same forwards and backwards. Write a program that helps Alice check if a given word reads the same forwards and backwards."*

**What good answers look like**

| | |
|---|---|
| **Technical statement** | Write a program to check if a given word is a palindrome |
| **Input** | A word (a string, from `input()`) |
| **Output** | Something indicating yes or no |
| **Rule** | The word equals itself reversed |

Accept partial answers generously. A pair that identifies input and output but not the word "palindrome" has done the useful part — **the vocabulary is the least important piece.**

**Debrief line:**
> *"None of you needed the word 'palindrome' to solve this. The vocabulary is a label you attach afterwards, not a prerequisite."*

**Cut rule:** 30 s think, 90 s pair, two reports.

---

## ⚡ ALS Activity 2 — Student-Generated Task Design: Write the Question (27–35 min)

**ALS format:** Student-Generated Task Design. Chosen as the second activity because it inverts Activity 1 — instead of decoding a story, students *construct* one, which is a stronger test of whether the funnel's logic actually landed.

**Setup line:**
> *"Everyone writes one story question. Take something simple we can already code — printing numbers, checking even, finding the biggest — and hide it inside a story. Two rules: a classmate must be able to solve it, and you must know the answer."*

**Give the constraints explicitly:**
- Must be solvable with what we've covered — input, `if`/`else`, `while`
- Must not name the technical word directly (don't write "even", describe it)
- Three sentences maximum
- **You must know your own answer**

**Show this example first:**
> *"A librarian is arranging books on shelves. Each shelf holds exactly one book. She wants to know how many shelves she needs to number, starting from one, up to the number of books she has. Write a program that displays those numbers."*

Decode it with the class: **print the numbers 1 to n.**

**Running the reports:** read three aloud without naming the author. For each: class calls out the technical statement, then *"what's the input? The output? The rule?"*, then ask the author whether that's what they meant.

**When the class decodes it differently from what the author intended** — that's the best moment available:
> *"Two different readings of the same question. That's exactly what happens in a real exam, and it's why you read the whole thing twice before you write a line."*

**Cut rule:** Collect two, skip confirming with the author.

---

## Practice Set Walkthrough (35–45 min) · ALS: Vote → Discuss → Reveal

> This session has **no classroom quiz pool** on the platform — this block is its equivalent, run last as a cumulative check, same as the mandatory quiz in other sessions. Work through 5 questions from the **MCQ Practice** set (`67ed319d-5282-470f-bb86-f56ac2283c4c`), voting before revealing each one.

The pool contains two useful question types:

1. **"Which is the correct technical form of this story-based question?"** — exactly the skill from ALS Activity 1.
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

The three wrong options each break one thing — `% 2 == 1` for even, the branches swapped, and `//` instead of `%`. **Walk through why each is wrong**, not just which is right.

> ⚠️ **The pool also contains `REARRANGE` questions** (e.g. `83ac0e01`, `ddce4f02`) which have **no correct option marked** in the data. Skip them in a live vote — they don't work as MCQs. They're fine as homework on the platform where the interaction is different.

---

## Exit Ticket + Quiz Push (45–48 min)

**Exit ticket** (~30 s) — before anyone leaves:

> Read this and write the technical statement, plus the input and output:
> *"Priya has a list of daily temperatures and wants to know the coldest day."*
> **Answer:** Find the minimum value in a list. Input: a list of temperatures. Output: the smallest one.

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Open MCQ Practice. Whoever hasn't finished — at least 3 more questions before you leave your seat. Only 23 questions this time, and you've already seen 5 of them."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 15's warm-up."*

**Remaining homework**

| Task | Unit |
|---|---|
| MCQ Practice — 23 questions *(started in class above — finish the rest)* | `67ed319d-5282-470f-bb86-f56ac2283c4c` |
| Coding Practice — Session 13 loops set, if unfinished | `e13a266e-9a81-4716-b44f-893002bc30c0` |

> *"Before you write a single line tonight, write three things on paper: input, output, rule. Every time. It feels slower and it isn't."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock and want an energy-lift closer instead of ending early, run the optional Rapid Fire Board Race below — two volunteers at the board, you read a story fragment, both write the technical statement, class judges:
1. *"Ravi wants to know if his number can be shared equally between two friends with nothing left over."* → Check if a number is even
2. *"Meera wants all the numbers that divide her number exactly."* → Find the divisors of a number
> Never required — the schedule doesn't depend on it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Being stuck means I can't code | The blocker feels like a coding failure | The hook — everyone could write the loop; nobody could read the question |
| You should start typing immediately | Typing feels like progress | Warm-up Q5 and the input/output/rule frame |
| The first sentence is the whole problem | It reads like the problem | Slide Block A — read it all before writing |
| Story questions are unfair padding | They feel deliberately obstructive | Naming it: every exam and interview does this |
| There's one right way to phrase it | Answers are usually unique | ALS Activity 2 — two valid readings of the same story |
| Pseudocode is a waste of time | It isn't the real deliverable | The walkthrough — matching pseudocode to code |

---

## Instructor Notes

- **Nothing new is taught today.** This session is a skill and a habit — reading a problem before solving it. Judge it by whether students' first move on a hard problem changes from "stare and close the tab" to "write down input, output, rule."
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **This is a recovery window after Session 13.** Loops are the hardest content in the course and some students will be shaken. If a chunk of the room is still lost on `while`, spend the Quiz Push time on loop tracing instead. Say so honestly.
- **Two ALS activities this session:** Activity 1 is Think-Pair-Share (decoding a story), Activity 2 is Student-Generated Task Design (constructing one) — deliberately inverse skills. The original third activity (Rapid Fire Board Race) is demoted to an optional buffer-only closer, consistent with its role elsewhere in this course as an energy-lift, not core content.
- **The Practice Set Walkthrough runs last, right before the Exit Ticket** — it's this session's equivalent of the mandatory Classroom Quiz in other sessions, since no classroom quiz pool exists here. The pool also contains `REARRANGE` items with no correct option in the data — **don't use those in a live vote.**
- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair.** Target is 80% platform MCQ attempt rate, currently ~33%.
- **The MCQ pool is only 23 questions**, the smallest in the first fifteen, and 5 are used in the walkthrough. Session 13's 112-question loops pool is good backup revision.
- ✅ **Verified against the real deck** (*"Copy of Understanding Coding Question Formats"*). Slide Block A lists the actual slides in order.
- **⭐ The deck's funnel (slide 7) is its best asset** — *Identify Key Information → Convert to Technical Terms → Extract the Core Problem.* Use those exact words all session.
- **Slide 3 pairs the same problem in both formats** (long Sarah story vs. one-line technical). That single slide justifies the whole session — don't rush it.
- **Session 15 is `for` loops** and is the last of this batch. It's a lighter session than 13; students who survived `while` will find `for` a relief. Say so at the end — it's genuinely reassuring.
