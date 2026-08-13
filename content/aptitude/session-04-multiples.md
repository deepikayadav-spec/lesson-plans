# Session 4 — Multiples

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Multiples (deep dive) · **Prerequisite** Session 3 — Basics and Properties
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet — no quiz block for that reason. · **Format** 50-min recalibrated, 2 ALS activities

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT Multiples.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define a multiple as the product of two numbers, and identify numbers that are multiples of a given pair. *(REMEMBERING)*
2. Apply the LCM to find the least number that leaves the same specified remainder when divided by several given divisors. *(APPLYING)*
3. Apply the LCM to find the least number that must be added to a given number to make it exactly divisible by several divisors. *(APPLYING)*
4. Apply the LCM to a real-world periodic-event problem (events recurring at fixed intervals) to find when they next coincide. *(APPLYING)*
5. Determine the least perfect square divisible by a set of numbers by forcing every prime's power in the LCM to be even. *(ANALYZING)*
6. Compute the highest power of a composite number dividing n! by finding the highest power of each of its prime factors and taking the limiting one. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

5 questions on **Session 3 (Basics and Properties)**. Newly authored, real numbers from that deck. ~45 s each, project the distribution, never name individuals.

**Q1.** When two numbers are multiplied, Session 3 called the result a ____.
`A` Factor · `B` Multiple · `C` Remainder · `D` Ratio
→ **B.** *Targets:* the multiple definition itself.

**Q2.** Since 10 ÷ 2 = 5 is a whole number, what is 2 called, in relation to 10?
`A` A multiple of 10 · `B` A factor of 10 · `C` The HCF of 10 · `D` The LCM of 10
→ **B.** *Targets:* the factor definition.

**Q3.** Using prime factorisation (Session 3's method), what are the LCM and HCF of 18 and 30?
`A` LCM=90, HCF=6 · `B` LCM=540, HCF=6 · `C` LCM=90, HCF=3 · `D` LCM=180, HCF=6
→ **A.** *Targets:* the worked prime-factorisation method itself. *If >40% miss this:* redo the factor tree for 18 and 30 on the board before continuing — everything today builds on this.

**Q4.** Two numbers are in the ratio 4:14 and their HCF is 6. A student plugs straight into LCM = HCF × a × b and gets 6×4×14 = 336. What went wrong?
`A` HCF should have been squared · `B` 4:14 isn't in simplest form — it simplifies to 2:7 first, giving LCM = 6×2×7 = 84 · `C` Nothing — 336 is correct · `D` The ratio property doesn't apply here
→ **B.** *Targets:* the exact misconception Session 3 flagged. This recurs today in every LCM-of-a-ratio-style problem.

**Q5.** *(MSQ — select the 2 correct)* For the fractions 20/16, 16/15, and 20/21, Session 3 gave:
`A` LCM = 80 · `B` HCF = 1/420 · `C` LCM = 1/420 · `D` HCF = 80
→ **A and B.** *Targets:* LCM/HCF of fractions — the least-familiar method and the one most likely to have faded in a week.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–11 min)

Write on the board, nothing else:

```
10 × 3 = 30        10 × 4 = 40
```

Say: *"You saw this in Session 3 — 30 is a multiple of 10 and 3. 40 is a multiple of 10 and 4. Quick check: is 20 a multiple of both 10 and 3?"*

Take the answer. *(No — 20 isn't divisible by 3.)*

> *"Correct. Now here's today's real question. Three bells ring every 120, 240, and 300 seconds. Each of those numbers has an endless pile of multiples. Somewhere in that pile, all three bells land on the exact same tick — the same second. Today's whole session is one idea, applied five different ways: remainders, perfect squares, factorials, and yes — bells. Every time, we're hunting for numbers that multiple divisors have in common."*

Tell them: *"By the time we reach the bells problem for real, it'll take you twenty seconds."*

---

## Slide Block A (11–21 min) — DELIVER SLIDES AS-IS

Covers: Multiples definition → three worked "least number satisfying a remainder condition" problems.

**Beats to emphasise**

- **One template drives all three problems.** Write it on the board and leave it up: *N = LCM(divisors) × k + remainder*, take the smallest k that fits. Everything in this block is that one line, applied three times.
- **The second problem is a ready-made live poll.** The deck presents it as an MCQ (A) 128 (B) 518 (C) 538 (D) 48 — run a show-of-hands vote before revealing the answer instead of just solving it at the board.
- **The third problem runs the template backwards.** "Least number to add" is the same LCM template, just read as "find the next multiple of the LCM above this number, then subtract."

**Checkpoint + Quick Race (at 21 min, ~2 min)** — 10 s silent think, cold-call for the checkpoint, then a compressed drill (folded in here to protect the schedule):
> *Checkpoint:* *"The least number which should be added to 2502 so that the sum is exactly divisible by 5, 6, 7 and 8 — what is it, and what's the first thing you compute?"* Answer: 18. First compute LCM(5,6,7,8) = 840; the next multiple of 840 above 2502 is 2520; 2520 − 2502 = 18.
> *Quick race:* *"A number when divided by 3, 5 and 11 gives a remainder of 2. Least 3-digit number satisfying this — go, on paper, 30 seconds."* Answer: **167** (LCM(3,5,11)=165; 165×1+2=167).

---

## ⚡ ALS Activity 1 — Silent Diagnose, Named Reveal: Spot the Bug (21–28 min)

**ALS format:** Silent Individual Diagnose, then Named Reveal — two flawed "solutions" are shown, each stopping one step short of correct, both realistic shortcuts a student takes under time pressure. Students diagnose alone before any answer is taken. Chosen right after Slide Block A because both problems have a second condition that's easy to forget the moment the first LCM is found — this puts the exact failure mode in front of the class before it happens on their own paper.

**Setup line:**
> *"Two solutions, both stop one step early. Before you tell me the right answer, tell me exactly what step got skipped. 'It's wrong' doesn't count — I want the missing step named."*

**Bug 1** *(based on the divided-by-5,6,7,8-remainder-3-and-divisible-by-9 problem)*
> A student computes LCM(5,6,7,8) = 840, adds the remainder 3, gets 843, and writes that as the final answer.

**Bug 2** *(based on the least-perfect-square-divisible-by-25,75,300 problem)*
> A student computes LCM(25,75,300) = 300 and writes that as the final answer, since "300 is divisible by all three."

**Answers**

| # | What's missing | Correct answer |
|---|---|---|
| 1 | 843 was never checked against the "divisible by 9" condition — the digit sum of 843 is 15, not a multiple of 9. Must keep stepping through 840k+3 until one clears that filter. | **1683** (k=2: 840×2+3=1683; digit sum 18, divisible by 9) |
| 2 | 300 = 2²×3¹×5² isn't a perfect square — the power of 3 is odd. Must multiply by one more 3. | **900** (= 2²×3²×5² = 30²) |

**How it surfaces:** for each bug, run the check live — add up the digits of 843, or ask "what's the square root of 300?" — so the gap is visible, not just asserted.

**Debrief line:**
> *"Both of these had the LCM right. Both were still wrong. The LCM is step one, never the whole answer — there's always a second filter to check."*

**Cut rule:** run Bug 1 only; state Bug 2's rule and answer directly.

---

## Slide Block B (28–37 min) — DELIVER SLIDES AS-IS

Covers: the deck's own "Quiz Time" problem set — a mixed remainder-and-divisibility problem, a least-perfect-square problem, the bells (LCM real-world) problem, and the highest-power-in-a-factorial problem.

**Beats to emphasise**

<!-- placement: inferred — the deck poses each of the following as a rhetorical instructor prompt ("What is divisibility rule of 9?", "What is a perfect square number?", "What is meant by Factorial?") rather than stating the rule/definition on-slide. Exact phrasing below is the instructor's call. -->

- **Problem 1 stacks two conditions** — already drilled in ALS Activity 1. Recap in one line: LCM-plus-remainder, then a divisibility filter on top.
- **Problem 2's trick is the "perfect square" word** — already drilled in ALS Activity 1. A perfect square number is one that can be written as n² for a whole number n; every prime's power in the LCM must be even.
- **Pay off the Hook here.** When you reach the bells problem, say: *"Here they are — the bells from the start of class."* LCM(120,240,300) = 1200 seconds = 20 minutes.
- **Problem 4 needs a prime split first.** n! = 1×2×3×...×n. 12 isn't prime, so break it into 2²×3, find the highest power of 2 in 100! and the highest power of 3 in 100! separately, then combine.

**Checkpoint (at 37 min)** — cold-call:
> *"Bells ring every 120, 240 and 300 seconds. After how many minutes do all three ring together, and what's the one number you had to compute to get there?"*
> **Answer:** 20 minutes. The number needed is LCM(120, 240, 300) = 1200 seconds.

---

## ⚡ ALS Activity 2 — Round-Robin Table Build: Trace the Table (37–46 min)

**ALS format:** Round-Robin Table Build — the class builds, row by row, the two power-tables needed to find the highest power of 12 in 100!, one student per row, nobody skipping ahead to the final answer. **This is the newest and hardest technique in the session** — splitting a composite number into primes before hunting for its power in a factorial — and it only sticks if the class builds the table themselves rather than watching it filled in.

**Setup line:**
> *"12 isn't prime, so we can't hunt for it directly in 100! — we hunt for its prime pieces instead. 12 = 2 squared times 3. I'm going to point at a row of this table, and whoever I point at gives me the number that goes in the box. Nobody jumps ahead to the final answer — one row at a time."*

Draw two empty tables on the board: one for powers of 2 (rows for 2¹ through 2⁶), one for powers of 3 (rows for 3¹ through 3⁴).

**Powers of 2 in 100!** — floor(100 ÷ 2^k):

| k | 2^k | floor(100/2^k) |
|---|---|---|
| 1 | 2 | 50 |
| 2 | 4 | 25 |
| 3 | 8 | 12 |
| 4 | 16 | 6 |
| 5 | 32 | 3 |
| 6 | 64 | 1 |

Running total: 50+25+12+6+3+1 = **97** — the highest power of 2 in 100!.

**Powers of 3 in 100!** — floor(100 ÷ 3^k):

| k | 3^k | floor(100/3^k) |
|---|---|---|
| 1 | 3 | 33 |
| 2 | 9 | 11 |
| 3 | 27 | 3 |
| 4 | 81 | 1 |

Running total: 33+11+3+1 = **48** — the highest power of 3 in 100!.

**Combine:** 12 = 2²×3¹. From the power of 2 (97), we can form floor(97/2) = 48 pairs of 2². From the power of 3 (48), we can form 48 single 3s. The highest power of 12 in 100! is the smaller of the two: **min(48, 48) = 48.**

**When it goes wrong**

| If… | Do this |
|---|---|
| The class forgets to divide the power-of-2 total by 2 before combining | Point back at "12 = 2 squared" — ask how many pairs of 2 you can make from 97 twos. |
| Someone assumes the answer is always min of the two raw totals | It happened to be 48 and 48 here by coincidence — flag that you must divide each total by its own exponent in 12 first. |
| Running long | Do the power-of-2 table as a class; state the power-of-3 total (48) and the combining step directly. |

**Common instructor mistake:** filling in the tables yourself "to save time." The row-by-row cold call is the entire mechanism that makes this technique stick.

**Cut rule:** build the powers-of-2 table together; state the powers-of-3 total (48) and the combining step directly.

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — on paper or in chat before anyone leaves:

> Three bells ring every 120, 240 and 300 seconds. State the general rule for finding when repeating events like this next happen together, then give today's numeric answer.
> **Answer:** Find the LCM of the intervals. LCM(120, 240, 300) = 1200 seconds = 20 minutes.

Scan responses on the way out — anyone still describing "add the intervals" instead of "LCM the intervals" needs the rule repeated at the start of Session 5.

**Homework**

| Task | Instruction |
|---|---|
| Re-solve without notes | The three "Quiz Time" problems from today (1683, 900, and the highest-power-of-12-in-100! = 48 problem). Check your working against today's board notes, not just the final number. |
| Revisit Session 3 | The ratio-based LCM/HCF property — always simplify the ratio first. Warm-up Q4 today showed this is the most-missed step. |

Tell them: *"Next session builds on today's method. If you can't redo the 1683 problem cold, that's tonight's actual homework — not just looking at the answer."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The LCM alone is the final answer to a "least number satisfying a remainder condition" problem | The remainder step feels like an add-on, not core to the method | Slide Block A's checkpoint and ALS Activity 1 — every problem needs LCM *then* + remainder |
| "Least perfect square divisible by X" = the LCM of X itself | LCM already satisfies "divisible by" — the perfect-square condition is easy to forget | ALS Activity 1, Bug 2 |
| A remainder-and-divisibility problem is solved the moment the remainder condition is met once | Students stop at the first number that fits and forget the second filter | ALS Activity 1, Bug 1 |
| A ratio like 4:14 can go straight into LCM = HCF × a × b without simplifying | The ratio "looks" already reduced | Warm-up poll Q4, carried over from Session 3 |
| The highest power of a composite number (like 12) in n! is the same as counting the number itself | Students haven't yet split it into prime factors | ALS Activity 2 — the 2²×3 breakdown, dividing each prime's power by its exponent in 12 before combining |

---

## Instructor Notes

- **This plan is grounded in a local pptx text-extraction (`NIAT Multiples.pptx`), not a platform export.** No unit IDs, quiz question IDs, or MCQ/coding practice pools exist for this topic.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Silent Diagnose → Named Reveal, Activity 2 is Round-Robin Table Build — **the newest technique in the session, protect it above everything else if the session runs behind.** The original Board Race drilling activity is folded into a compressed 2-minute quick-race beat at the end of Slide Block A's checkpoint.
- <!-- placement: inferred --> **Three rules/definitions are instructor-supplied, not deck-stated.** The deck poses "What is divisibility rule of 9?", "What is a perfect square number?", and "What is meant by Factorial?" as rhetorical prompts without spelling out the rule text on-slide. Confirm against the live deck.
- **Slides 1–3 (Welcome, Recap, Agenda) and 14–15 (Feedback, Thank You) are administrative** and not delivered as content blocks.
- **The factorial problem (ALS Activity 2) is the pacing risk.** It's the newest technique in the session — if you must cut somewhere, cut Slide Block A's quick-race beat, not this.
- **Numbers in this plan are unverified against the live deck's exact wording** beyond the extracted text — all arithmetic (167, 538, 18, 1683, 900, 20 minutes, 48) was independently re-derived and matches the deck's stated answers exactly.
