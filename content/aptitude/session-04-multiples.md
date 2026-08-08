# Session 4 — Multiples

**Duration** 60 min · **Topic** Multiples (deep dive) · **Prerequisite** Session 3 — Basics and Properties
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet for this topic.

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

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 3 (Basics and Properties)**. Newly authored, real numbers from that deck. ~45 s each, project the distribution, never name individuals. Difficulty ramps recall → application → analysis.

**Q1.** When two numbers are multiplied, Session 3 called the result a ____.
`A` Factor · `B` Multiple · `C` Remainder · `D` Ratio
→ **B.** *Targets:* the multiple definition itself (Session 3: "10×3 = 30, 30 is a multiple of 10 and 3").

**Q2.** Since 10 ÷ 2 = 5 is a whole number, what is 2 called, in relation to 10?
`A` A multiple of 10 · `B` A factor of 10 · `C` The HCF of 10 · `D` The LCM of 10
→ **B.** *Targets:* the factor definition (Session 3's exact line: "2 is a factor of 10").

**Q3.** Session 3 showed 12 ÷ 4 = 3. Which statement is correct?
`A` 12 is a factor of 4 · `B` 4 is a factor of 12 · `C` 3 is a factor of 4 · `D` 4 is not a factor of 12
→ **B.** *Targets:* which side of the division is the factor — a common reversal error.

**Q4.** Using prime factorisation (Session 3's method), what are the LCM and HCF of 18 and 30?
`A` LCM=90, HCF=6 · `B` LCM=540, HCF=6 · `C` LCM=90, HCF=3 · `D` LCM=180, HCF=6
→ **A.** *Targets:* the worked prime-factorisation method itself. *If >40% miss this:* redo the factor tree for 18 and 30 on the board before continuing — everything today builds on this.

**Q5.** Two numbers are in the ratio 3:4 and their HCF is 6. Using the property LCM = HCF × (product of the ratio terms), what is their LCM?
`A` 12 · `B` 18 · `C` 24 · `D` 72
→ **D** (6×3×4 = 72). *Targets:* the ratio-based LCM/HCF property.

**Q6.** Two numbers are in the ratio 4:14 and their HCF is 6. A student plugs straight into LCM = HCF × a × b and gets 6×4×14 = 336. What went wrong?
`A` HCF should have been squared · `B` 4:14 isn't in simplest form — it simplifies to 2:7 first, giving LCM = 6×2×7 = 84 · `C` Nothing — 336 is correct · `D` The ratio property doesn't apply here
→ **B.** *Targets:* the exact misconception Session 3 flagged ("What is simplest form of ratios?"). This recurs today in every LCM-of-a-ratio-style problem — if it's weak, re-simplify 4:14 → 2:7 on the board now.

**Q7.** *(MSQ — select the 2 correct)* For the fractions 20/16, 16/15, and 20/21, Session 3 gave:
`A` LCM = 80 · `B` HCF = 1/420 · `C` LCM = 1/420 · `D` HCF = 80
→ **A and B.** *Targets:* LCM/HCF of fractions — the least-familiar Session 3 method and the one most likely to have faded in a week.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–10 min)

Write on the board, nothing else:

```
10 × 3 = 30        10 × 4 = 40
```

Say: *"You saw this in Session 3 — 30 is a multiple of 10 and 3. 40 is a multiple of 10 and 4. Quick check: is 20 a multiple of both 10 and 3?"*

Take the answer. *(No — 20 isn't divisible by 3.)*

> *"Correct. Now here's today's real question. Three bells ring every 120, 240, and 300 seconds. Each of those numbers has an endless pile of multiples. Somewhere in that pile, all three bells land on the exact same tick — the same second. Today's whole session is one idea, applied five different ways: remainders, perfect squares, factorials, and yes — bells. Every time, we're hunting for numbers that multiple divisors have in common."*

Tell them: *"By the time we reach the bells problem for real, it'll take you twenty seconds."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

Covers: Multiples definition → three worked "least number satisfying a remainder condition" problems.

**Beats to emphasise**

- **One template drives all three problems.** Write it on the board and leave it up: *N = LCM(divisors) × k + remainder*, take the smallest k that fits. Everything in this block is that one line, applied three times.
- **The second problem is a ready-made live poll.** The deck presents it as an MCQ (A) 128 (B) 518 (C) 538 (D) 48 — run a show-of-hands vote before revealing the answer instead of just solving it at the board.
- **The third problem runs the template backwards.** "Least number to add" is the same LCM template, just read as "find the next multiple of the LCM above this number, then subtract."

**Checkpoint (at 22 min)** — cold-call one student:
> *"The least number which should be added to 2502 so that the sum is exactly divisible by 5, 6, 7 and 8 — what is it, and what's the first thing you compute?"*
> **Answer:** 18. First compute LCM(5,6,7,8) = 840; the next multiple of 840 above 2502 is 2520; 2520 − 2502 = 18.

---

## ⚡ Activity 1 — Rapid Fire Board Race (22–28 min)

### What this activity is

Two teams race on the board to apply the LCM-plus-remainder template just taught, to two fresh problems pulled straight from the deck's own worked examples. First team to the board with the full working — not just the number — wins the round.

### Why it's here

The template from Slide Block A evaporates fast if it isn't used within minutes. This is the drill, immediately, before the class moves on.

### Before class

Split the board (or shared screen) into two halves, one per team. Have both problems written on a slide or card, out of sight until you reveal them.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, reveal Problem 1 | Listen |
| 0:30–2:30 | Time the race | Both teams work Problem 1 on their half of the board |
| 2:30–3:00 | Call it, reveal answer, quick debrief | Watch |
| 3:00–3:30 | Reveal Problem 2 | Listen |
| 3:30–5:30 | Time the race | Both teams work Problem 2 |
| 5:30–6:00 | Call it, reveal answer, debrief | Watch |

### Say this

> *"Two teams, one board each. I give you a problem, you race to get the full working up — not just a shouted number, I want to see the LCM step and the final answer. First team with correct, complete working wins the round. Two rounds."*

### The problems

**Problem 1** — *"A number when divided by 3, 5 and 11 gives a remainder of 2. Find the least 3-digit number which satisfies this condition."*
**Answer:** 167. LCM(3,5,11) = 165; least number of the form 165k+2 that is 3 digits is 165×1+2 = 167.

**Problem 2** — *"Find the least number which, when divided by 21, 25 and 35, leaves a remainder of 13."*
**Answer:** 538. LCM(21,25,35) = 525; 525+13 = 538.

### When it goes wrong

| If… | Do this |
|---|---|
| A team writes the answer with no LCM shown | No credit — say so before the next round. The working *is* the point, not the number. |
| Both teams stall on the LCM itself | Pause the race, rebuild the prime factorisation for that one divisor set on the board together, then restart the clock. |
| One team finishes in under 30 seconds | Ask them to explain their steps aloud to the room while the other team finishes — free reteach. |

**Common instructor mistake:** racing to be the first to reveal the answer yourself. Let the teams reach it — your only job is the clock and the final check.

**Cut rule:** if running short, run Problem 1 only as the race and solve Problem 2 yourself at the board as a fast worked demo instead.

---

## Classroom Quiz — not yet available

> Classroom Quiz: not yet available — add once question bank exists for this topic.

No question bank exists for Multiples yet, so this slot carries no content of its own. Its 7 minutes are folded into the blocks around it: Activity 1 (+1 min), Slide Block B (+2 min), Activity 2 (+1 min), Activity 3 (+3 min) — reflected in the retimed headings below, so the full 60 minutes still has no gaps.

---

## Slide Block B (28–40 min) — DELIVER SLIDES AS-IS

Covers: the deck's own "Quiz Time" problem set — a mixed remainder-and-divisibility problem, a least-perfect-square problem, the bells (LCM real-world) problem, and the highest-power-in-a-factorial problem.

**Beats to emphasise**

<!-- placement: inferred — the deck poses each of the following as a rhetorical instructor prompt ("What is divisibility rule of 9?", "What is a perfect square number?", "What is meant by Factorial?") rather than stating the rule/definition on-slide. Exact phrasing below is the instructor's call. -->

- **Problem 1 stacks two conditions.** It needs the LCM-plus-remainder template *and* a divisibility filter: state the rule plainly — a number is divisible by 9 if its digit sum is divisible by 9 — and show that you must keep stepping through multiples of LCM(5,6,7,8)=840, plus remainder 3, until one also clears that filter.
- **Problem 2's trick is the "perfect square" word.** A perfect square number is one that can be written as n² for a whole number n. Taking the LCM(25,75,300)=300 is necessary but not sufficient — every prime's power in that LCM must be even. 300 = 2²×3¹×5²: the 3 has an odd power, so multiply by one more 3 to get 900 = 30².
- **Pay off the Hook here.** When you reach the bells problem, say: *"Here they are — the bells from the start of class."* LCM(120,240,300) = 1200 seconds = 20 minutes.
- **Problem 4 needs a prime split first.** n! = 1×2×3×...×n. 12 isn't prime, so break it into 2²×3, find the highest power of 2 in 100! and the highest power of 3 in 100! separately, then combine.

**Checkpoint (at 40 min)** — cold-call:
> *"Bells ring every 120, 240 and 300 seconds. After how many minutes do all three ring together, and what's the one number you had to compute to get there?"*
> **Answer:** 20 minutes. The number needed is LCM(120, 240, 300) = 1200 seconds.

---

## ⚡ Activity 2 — Spot the Bug (40–47 min)

### What this activity is

Two "solutions" are shown on screen, each stopping one step short of correct — both are realistic shortcuts a student takes under time pressure on exactly the two problems just delivered in Slide Block B. Students must name what's missing before anyone gives the fix.

### Why it's here

Both problems in this pair have a second condition that's easy to forget the moment the first LCM is found. This activity puts the exact failure mode in front of the class before it happens on their own paper.

### Before class

Have both flawed solutions ready on a slide, side by side, with the final "wrong" number clearly written as if it were the final answer.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, reveal Bug 1 | Listen |
| 0:30–2:00 | Wait | Diagnose silently, hands up when ready |
| 2:00–3:30 | Take the answer, confirm/complete on the board | Answer, watch |
| 3:30–4:00 | Reveal Bug 2 | Listen |
| 4:00–5:30 | Wait | Diagnose silently |
| 5:30–7:00 | Take the answer, confirm/complete on the board | Answer, watch |

### Say this

> *"Two solutions, both stop one step early. Before you tell me the right answer, tell me exactly what step got skipped. 'It's wrong' doesn't count — I want the missing step named."*

### The bugs

**Bug 1** *(based on the divided-by-5,6,7,8-remainder-3-and-divisible-by-9 problem)*
> A student computes LCM(5,6,7,8) = 840, adds the remainder 3, gets 843, and writes that as the final answer.

**Bug 2** *(based on the least-perfect-square-divisible-by-25,75,300 problem)*
> A student computes LCM(25,75,300) = 300 and writes that as the final answer, since "300 is divisible by all three."

### Answers

| # | What's missing | Correct answer |
|---|---|---|
| 1 | 843 was never checked against the "divisible by 9" condition — the digit sum of 843 is 15, not a multiple of 9. Must keep stepping through 840k+3 until one clears that filter. | **1683** (k=2: 840×2+3=1683; digit sum 18, divisible by 9) |
| 2 | 300 = 2²×3¹×5² isn't a perfect square — the power of 3 is odd. Must multiply by one more 3. | **900** (= 2²×3²×5² = 30²) |

**How it surfaces:** for each bug, run the check live — add up the digits of 843, or ask "what's the square root of 300?" — so the gap is visible, not just asserted.

### When it goes wrong

| If… | Do this |
|---|---|
| Someone says "843 looks fine, it has a remainder of 3" | Right on the remainder, wrong on the point — ask them to check the digit sum for divisibility by 9. |
| Nobody remembers the perfect-square rule | Point back to Slide Block B's rule: "every prime's power in the LCM must be even." Rebuild 300's prime factorisation on the board. |
| Both bugs get spotted instantly | Good sign — ask *why* the LCM alone isn't enough in each case, don't just move on. |

**Common instructor mistake:** revealing the correct final number before a student has named the missing step. The named step is the actual skill; the number is just proof they got there.

**Cut rule:** run Bug 1 only; state Bug 2's rule and answer directly.

---

## ⚡ Activity 3 — Trace the Table (47–57 min)

### What this activity is

The class builds, row by row, the two power-tables needed to find the highest power of 12 in 100!. You point at a row; a different student computes it and states what goes in the box. Nobody skips ahead to the final answer.

### Why it's here

This is the hardest and newest technique in the deck — splitting a composite number into primes before hunting for its power in a factorial. It only sticks if the class builds the table themselves, one row at a time, rather than watching you fill it in.

### Before class

Draw two empty tables on the board (or have a slide with empty cells): one for powers of 2 (rows for 2¹ through 2⁶), one for powers of 3 (rows for 3¹ through 3⁴).

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, explain why 12 = 2²×3 | Listen |
| 0:30–5:00 | Point at each row of the power-of-2 table in turn | Compute floor(100/2^k) for that row |
| 5:00–8:00 | Point at each row of the power-of-3 table | Compute floor(100/3^k) for that row |
| 8:00–9:30 | Combine: divide each running total by its exponent in 12, take the smaller | Follow, answer the final question |
| 9:30–10:00 | Debrief | Listen |

### Say this

> *"12 isn't prime, so we can't hunt for it directly in 100! — we hunt for its prime pieces instead. 12 = 2 squared times 3. I'm going to point at a row of this table, and whoever I point at gives me the number that goes in the box. Nobody jumps ahead to the final answer — one row at a time."*

### The tables

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

### When it goes wrong

| If… | Do this |
|---|---|
| A student gives a running total instead of just their row | Fine — write it in, but make the next student give only their own row so the pattern of the method is clear. |
| The class forgets to divide the power-of-2 total by 2 before combining | Point back at "12 = 2 squared" — ask how many pairs of 2 you can make from 97 twos. |
| Someone assumes the answer is always min of the two raw totals | It happened to be 48 and 48 here by coincidence of these particular numbers — flag that you must divide each total by its own exponent in 12 first, then take the minimum. |
| Running long | Do the power-of-2 table as a class, then give the power-of-3 table's final total (48) directly and move to combining. |

**Common instructor mistake:** filling in the tables yourself "to save time." The row-by-row cold call is the entire mechanism that makes this technique stick — narrating it yourself turns it back into a lecture.

**Cut rule:** build the powers-of-2 table together; state the powers-of-3 total (48) and the combining step directly.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — on paper or in chat before anyone leaves:

> Three bells ring every 120, 240 and 300 seconds. State the general rule for finding when repeating events like this next happen together, then give today's numeric answer.
> **Answer:** Find the LCM of the intervals. LCM(120, 240, 300) = 1200 seconds = 20 minutes.

Scan responses on the way out — anyone still describing "add the intervals" instead of "LCM the intervals" needs the rule repeated at the start of Session 5.

**Homework**

| Task | Instruction |
|---|---|
| Re-solve without notes | The three "Quiz Time" problems from today (1683, 900, and the highest-power-of-12-in-100! = 48 problem). Check your working against today's board notes, not just the final number. |
| Revisit Session 3 | The ratio-based LCM/HCF property (LCM = HCF × product of ratio terms) — always simplify the ratio first. Warm-up Q6 today showed this is the most-missed step. |

Tell them: *"Next session builds on today's method. If you can't redo the 1683 problem cold, that's tonight's actual homework — not just looking at the answer."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The LCM alone is the final answer to a "least number satisfying a remainder condition" problem | The remainder step feels like an add-on, not core to the method | Slide Block A's checkpoint and Activity 1 — every problem needs LCM *then* + remainder |
| "Least perfect square divisible by X" = the LCM of X itself | LCM already satisfies "divisible by" — the perfect-square condition is easy to forget | Activity 2, Bug 2 — 300 is divisible by 25, 75, 300 but isn't a perfect square |
| A remainder-and-divisibility problem is solved the moment the remainder condition is met once | Students stop at the first number that fits and forget the second filter | Activity 2, Bug 1 — 843 fits the remainder but fails the divisible-by-9 check |
| A ratio like 4:14 can go straight into LCM = HCF × a × b without simplifying | The ratio "looks" already reduced | Warm-up poll Q6, carried over from Session 3 |
| The highest power of a composite number (like 12) in n! is the same as counting the number itself | Students haven't yet split it into prime factors | Activity 3 — the 2²×3 breakdown, and dividing each prime's power by its exponent in 12 before combining |

---

## Instructor Notes

- **This plan is grounded in a local pptx text-extraction (`NIAT Multiples.pptx`), not a platform export.** No unit IDs, quiz question IDs, or MCQ/coding practice pools exist for this topic — none have been invented. Add the real IDs once a bank exists.
- <!-- placement: inferred --> **Three rules/definitions are instructor-supplied, not deck-stated.** The deck poses "What is divisibility rule of 9?", "What is a perfect square number?", and "What is meant by Factorial?" as rhetorical prompts to the instructor, without spelling out the rule text on-slide. The phrasing used in Slide Block B (digit-sum rule for 9, n² definition for perfect square, 1×2×...×n for factorial) is standard and safe, but confirm against the live deck in case a slide with the explicit statement exists and wasn't captured in extraction.
- <!-- placement: inferred --> **The deck's second "Quiz Time" slide (before Feedback/Thank You) has no problems attached in the extracted text.** It may be a closing section marker, or it may have had additional problems delivered as images/diagrams that text extraction couldn't capture. If the live deck has more problems there, they're a natural extension of Activity 3's cut round — check before class.
- **Slides 1–3 (Welcome, Recap, Agenda) and 14–15 (Feedback, Thank You) are administrative** and not delivered as content blocks in this plan — same treatment as non-lecture RM material in the Programming Foundations set.
- **The factorial problem (Activity 3) is the pacing risk.** It's the newest technique in the session and the one most likely to be rushed. It has been given the longest activity slot (10 min) deliberately — if you must cut somewhere, cut Activity 1's second round, not Activity 3.
- **Classroom Quiz has no bank yet**, so its scheduled 7 minutes were folded into Activity 1 (+1), Slide Block B (+2), Activity 2 (+1), and Activity 3 (+3) to keep the 60-minute timeline gapless. Re-run this reallocation once a real quiz pool exists for Multiples.
- **Numbers in this plan are unverified against the live deck's exact wording** beyond the extracted text — all arithmetic (167, 538, 18, 1683, 900, 20 minutes, 48) was independently re-derived and matches the deck's stated answers exactly, so the underlying method is sound even if a slide's phrasing differs slightly from what's quoted here.
