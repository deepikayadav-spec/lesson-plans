# Session 9 — Company-Specific MCQs: LCM & HCF

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Company-Specific MCQs — LCM & HCF · **Prerequisite** Session 3 (Basics and Properties — LCM/HCF), reinforced across Sessions 4–8
**Session type** Consolidation / review lecture — a set of fully solved Company-Specific MCQs. No new concept is taught. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet — no quiz block for that reason. The warm-up poll deliberately reaches back to **Session 3** rather than Session 8 — Session 8 was a Numbers consolidation session and did not cover LCM/HCF. See Instructor Notes. · **Format** 50-min recalibrated, 2 ALS activities (this session already had exactly 2)

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `2) NIAT_CSMCQ'S_LCM & HCF.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the two core LCM–HCF properties used throughout this deck — *HCF is always a factor of LCM*, and *Product of two numbers = LCM × HCF* — from memory. *(REMEMBERING)*
2. Apply the HCF × LCM = Product shortcut to recover an unknown number given the other number, the HCF, and the LCM. *(APPLYING)*
3. Apply prime factorisation to find the LCM of three or more numbers in "smallest number divisible by…" and "leaves remainder…" problem types. *(APPLYING)*
4. Apply LCM of times/periods to solve "meet again at the starting point" circular-motion problems. *(APPLYING)*
5. Analyse ratio-based and fraction-based LCM/HCF problems to select the correct shortcut formula instead of recomputing from scratch. *(ANALYZING)*
6. Evaluate, for a given company-specific question, which solving method is fastest. *(EVALUATING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Reach-Back to Session 3 (3–7 min) · ALS: Polling

<!-- placement: inferred — poll deliberately targets Session 3's LCM/HCF content, not Session 8, because Session 8 (Numbers) never covered LCM/HCF. See Instructor Notes. -->

5 questions, newly authored, grounded in the real worked numbers from Session 3. ~45 s each, project the distribution, never name individuals. Say up front: *"Quick show of hands on LCM and HCF — we haven't touched this since Session 3, so don't panic if it's rusty. That's exactly why we're doing this."*

**Q1.** What is the HCF of 18 and 30?
`A` 3 · `B` 6 · `C` 9 · `D` 18
→ **B.** *Targets:* basic HCF via prime factorisation.

**Q2.** Two numbers have LCM 30 and HCF 5. One of the numbers is 10. Using *Product of numbers = LCM × HCF*, what is the other number?
`A` 6 · `B` 15 · `C` 20 · `D` 25
→ **B.** *Targets:* the product shortcut. This exact move recurs as today's Q2 in the deck.

**Q3.** Two numbers are in the ratio 3:4. Their HCF is 6. What is their LCM?
`A` 24 · `B` 48 · `C` 72 · `D` 96
→ **C.** *Targets:* the ratio shortcut — LCM = HCF × (ratio term 1) × (ratio term 2) = 6×3×4 = 72.

**Q4.** *(MSQ — select all that are true)* Two numbers are in the ratio 4:14. Their HCF is 6.
`A` The simplest form of the ratio is 2:7 · `B` Their LCM is 84 · `C` The two numbers are 24 and 84 · `D` HCF × LCM equals the product of the two numbers
→ **A, B, D.** *Targets:* the ratio shortcut only works on the *simplified* ratio. *If they pick C:* they multiplied the HCF into the unsimplified ratio — the single most common error in this problem type.

**Q5.** Find the HCF of the fractions 20/16, 16/15, and 20/21.
`A` 1/420 · `B` 80 · `C` 4/420 · `D` 1/1680
→ **A.** *Targets:* HCF of fractions = HCF(numerators)/LCM(denominators). *If they pick B (80):* that's the *LCM* of the same three fractions, not the HCF — Slide Block B's Q6 revisits fraction HCF/LCM today.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–11 min)

Put this on the board, **numbers only, no options yet**:

> *"The LCM of three numbers A, B, and C is 1024. Which of the following is NOT a possible value of the HCF of A, B, and C — 8, 124, 32, or 256?"*

Say: *"Don't calculate anything yet. HCF and LCM aren't two separate numbers you compute independently — one is built out of the other. Just look at these four numbers. Which one already feels wrong to you?"*

Let a few guesses land, right or wrong.

> *"Here's the rule that just did the work in your head, even if you didn't name it: the HCF of any set of numbers must divide their LCM exactly — every single time, no exceptions. Check each option against 1024. Whichever one doesn't divide it cleanly is your answer — and that's the entire logic of every question in today's deck. Ten problems, four or five properties, different costumes each time."*

Tie back to the poll: *"That's the same relationship you just used on 18 and 30 in the poll — you just didn't have a name for it yet."*

---

## Slide Block A (11–21 min) — DELIVER AS-IS

Covers the deck's first five Company-Specific Questions (Q1–Q5), in order, with real worked solutions.

**Q1.** *The LCM of three numbers A, B and C is 1024. Which of the following is not a possible value of the HCF of A, B, and C?* — Options: 8, 124, 32, 256.
> **Hint (deck):** HCF is a factor of LCM.
> **Solution (deck):** Among the given options, 8, 32, and 256 exactly divide 1024. However, 124 does not divide 1024.
> **Answer: 124**

**Q2.** *The HCF of two numbers is 11, and the LCM of those numbers is 693. If one of the numbers is 99, what is the other number?* — Options: 12, 45, 77, 34.
> **Solution (deck):** LCM × HCF = Product of the two numbers. 693 × 11 = 99 × x → x = (693 × 11)/99 = 77.
> **Answer: 77**

**Q3.** *What is the smallest four-digit number that is divisible by 18, 24, and 32?* — Options: 1152, 1512, 1216, 1680.
> **Hint (deck):** Try to find a common multiple if you see the word "smallest" in the question.
> **Solution (deck):** 18 = 2×3×3, 24 = 2×2×2×3, 32 = 2×2×2×2×2 → LCM(18,24,32) = 288. Least 4-digit number = 1000; 1000 ÷ 288 leaves remainder 136; add (288 − 136 = 152) → 1000 + 152 = 1152.
> **Answer: 1152**

**Q4.** *A number 'X' leaves a remainder 2 when divided by 3, 4, 5, and 6. What is the smallest possible value of X?* — Options: 62, 56, 128, 32.
> **Solution (deck):** LCM(3,4,5,6) = 2²×3×5 = 60. Required remainder is 2, so X = 60 + 2 = 62.
> **Answer: 62**

**Q5.** *A, B, and C start to run in the same direction at the same time around a circular park. A completes a round in 252 seconds, B in 308 seconds, C in 198 seconds. After what time will they meet again at the starting point?* — Options: 46 min 10 sec, 46 min 12 sec, 40 min 45 sec, cannot be determined.
> **Hint (deck):** Since they must return to the start together, use common multiple.
> **Solution (deck):** LCM(252,308,198) = 2×2×3×3×7×11 = 2772 seconds = 46 minutes 12 seconds.
> **Answer: 46 minutes 12 seconds**

**Beats to emphasise**

- **Beat 1 (Q1):** HCF-must-divide-LCM is a two-second elimination check — no long division needed if you spot it.
- **Beat 2 (Q2):** *Product of two numbers = LCM × HCF* turns a "find the missing number" question into one line of algebra. Flag that this is the single most reused property across today's deck.
- **Beat 3 (Q3–Q5):** Whenever the question says "smallest number divisible by," "leaves a remainder," or "meet again at the start," the fastest route is *always* prime-factorisation LCM first.

**Checkpoint (at 21 min)** — 10 s silent think, cold-call two students:
> *"What's the one-line shortcut that connects LCM, HCF, and the product of two numbers?"*
> **Answer:** Product of the two numbers = LCM × HCF.

---

## ⚡ ALS Activity 1 — Timed Silent Solve → Reveal (21–29 min)

**ALS format:** Timed Silent Solve → Reveal — three real deck questions, one at a time, 90 seconds silent individual solving on paper, then a student narrates the solution before the real one is revealed. Chosen right after Slide Block A because this tests whether the properties transfer to new numbers without the instructor's voice walking them through it — the real test of a consolidation session.

**Setup line:**
> *"Three real questions, ninety seconds each, no talking, no calculator apps — just what you learned two minutes ago. I reveal the question, you solve, then one of you walks the room through it before I show the real solution."*

**Q6.** *What is the H.C.F. of 4/9, 10/21 and 20/63?* — Options: 4/189, 20/21, 6/63, 2/63.
> **Solution (deck):** HCF of fractions = HCF(numerators)/LCM(denominators). HCF(4,10,20)=2, LCM(9,21,63)=63. Required HCF = 2/63.
> **Answer: 2/63**

**Q7.** *Two numbers X and Y are in the ratio 3:2, and their LCM is 60. What are the values of X and Y?* — Options: 40&10, 80&100, 30&20, cannot be determined.
> **Solution (deck):** HCF = LCM / LCM(ratio terms) = 60 / LCM(2,3) = 60/6 = 10. Numbers = ratio × HCF: 2×10=20, 3×10=30.
> **Answer: 30, 20**

**Q8.** *The ratio of two numbers is 1:2. If their HCF is 10, what is the sum of the two numbers?* — Options: 30, 50, 35, 60.
> **Solution (deck):** Numbers = ratio × HCF = 10 and 20. Sum = 30.
> **Answer: 30**

**When it goes wrong**

| If… | Do this |
|---|---|
| Q6 answers come back as 63/2 or 189/4 (flipped) | They applied the LCM-of-fractions formula instead of the HCF one. |
| Q7 answers come back as 40 & 10 | Walk through: HCF must be found first, from LCM ÷ LCM(ratio terms) — not given directly here, unlike Q8. |
| Nobody attempts within 60 s | Give one hint aloud: "which of Session 3's two fraction formulas applies here?" Do not give the answer. |

**Debrief line:**
> *"The point of this activity is students narrating the method, not hearing it a second time from me."*

**Cut rule:** If running short, drop Q8 and keep Q6 and Q7 — the fraction-HCF and ratio-LCM shortcuts are the two most company-tested types.

---

## Slide Block B (29–38 min) — DELIVER AS-IS

Covers the deck's remaining two Company-Specific Questions (Q9–Q10) — the two most conceptually dense in the set.

**Q9.** *There are three numbers which are co-prime to each other. The product of the first two numbers is 399. The product of the last two numbers is 525. What is the sum of the three numbers?* — Options: 75, 81, 65, 89.
> **Hint (deck):** Co-prime numbers are those numbers which do not have any common factor.
> **Solution (deck):** Let the numbers be a, b, c, pairwise co-prime. a×b=399, b×c=525 → b = HCF(399,525). 399 = 3×7×19; 525 = 3×5×5×7 → HCF = 21, so b=21. a = 399/21 = 19; c = 525/21 = 25. Sum = 65.
> **Answer: 65**

**Q10.** *The HCF of two numbers is 29, and their sum is 174. The possible numbers are?* — Options: 29&154, 29&145, 1&174, 74&100.
> **Solution (deck):** Numbers are 29a and 29b. 29(a+b) = 174 → a+b = 6. Since HCF is 29, a and b must be co-prime. The co-prime pair summing to 6 is (1,5). Numbers = 29 and 145.
> **Answer: 29, 145**

**Beats to emphasise**

- **Beat 1 (Q9):** When a middle term is shared between two given products and the numbers are pairwise co-prime, that shared term *is* the HCF of the two products.
- **Beat 2 (Q10):** Writing the two unknowns as HCF×a and HCF×b, with a and b forced co-prime, is the standard move whenever a question gives HCF *and* a sum but not the actual numbers.

**Checkpoint (at 38 min)** — show hands:
> *"In Q10, why must a and b be co-prime, and not just any pair of numbers that adds to 6?"*
> **Answer:** Because if a and b shared a common factor, that factor would multiply with 29 to give a *larger* common factor of the two numbers — contradicting that 29 is their HCF.

---

## ⚡ ALS Activity 2 — Fastest-Method Match (38–45 min)

**ALS format:** Matching Exercise (methods to questions) — reuses today's own already-solved questions; no new problems introduced. Chosen as the closing activity because it tests whether students can identify *which* property applies before they start calculating — the EVALUATING-level skill this whole session builds toward.

**Setup line:**
> *"You've solved all ten of today's questions. Now the real skill: given a question, can you name the fastest method *before* you touch a calculation? Six questions, six methods, shuffled. Match them. Ninety seconds, no talking."*

**The matching set**

| # | Question (stub) | | Method |
|---|---|---|---|
| 1 | Q1 — LCM=1024, which value can't be the HCF | A | HCF × LCM = Product of the two numbers |
| 2 | Q2 — HCF=11, LCM=693, one number=99, find the other | B | HCF must exactly divide the LCM |
| 3 | Q4 — X leaves remainder 2 on division by 3,4,5,6 | C | Prime-factorisation LCM, then add the remainder |
| 4 | Q6 — HCF of 4/9, 10/21, 20/63 | D | HCF(numerators) / LCM(denominators) |
| 5 | Q9 — co-prime triple, two products given | E | Shared term = HCF of the two given products |
| 6 | Q10 — HCF=29, sum=174, find the numbers | F | Write numbers as HCF×a, HCF×b with a,b co-prime |

**Answers:** 1→B · 2→A · 3→C · 4→D · 5→E · 6→F

**When it goes wrong**

| If… | Do this |
|---|---|
| Room swaps 1 and 2 | Ask: "does #1 give you two numbers to multiply, or one LCM to check against?" |
| Room swaps 4 and 6 | Push: "is #4 about fractions or about a sum?" |
| Someone says "just calculate it, method doesn't matter" | This is the belief the activity exists to break — remind them of Q5 in the poll, where naming the method wrong gave a confidently wrong answer. |

**Debrief line:**
> *"The calculation was already done earlier in the session — this is about recognition, not re-solving."*

**Cut rule:** If short on time, use only rows 1, 2, 4, and 5 — they span the four most distinct method families in the deck.

---

## Exit Ticket + Homework (45–48 min)

**Exit ticket** (~1 min) — on paper before anyone leaves:

> The HCF of two numbers is 11, and their LCM is 693. If one of the numbers is 99, what is the other?
> **Answer:** 77 — from `LCM × HCF = Product of the two numbers`: (693 × 11) ÷ 99 = 77.

**Homework**

| Task | Instruction |
|---|---|
| Re-attempt today's deck cold | Go through all 10 questions again without looking at the solutions. For each, first write down which of the six method labels from ALS Activity 2 applies — *then* solve. |
| Revisit Session 3 if the warm-up poll was shaky | If you missed more than 2 of the 5 warm-up poll questions, redo Session 3's worked examples before next session. |

Tell them: *"Nothing you tried today was new maths. It was five properties from Session 3, recognised fast. That recognition speed is what a company aptitude round is actually testing."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

Grounded in the deck's own "Hint :-" lines.

| Misconception | Deck's hint | Correct it live by |
|---|---|---|
| Any of the given options could plausibly be the HCF, so you have to compute each one from scratch | Q1 — "HCF is a factor of LCM" | Running Q1's elimination check live: only 124 fails to divide 1024 exactly |
| "Smallest number divisible by…" questions are solved by testing options one at a time | Q3 — "Try to find a common multiple if you see the word smallest in the question" | Slide Block A's Q3 walkthrough |
| "Meet again at the start" problems need averaging or adding the individual times | Q5 — "Since they must return to the start together, use common multiple" | Slide Block A's Q5 walkthrough |
| Co-prime means "no two of the numbers share any factor in general," rather than a specific pairwise check | Q9 — "Co-prime numbers are those numbers which do not have any common factor" | Slide Block B's Q9 walkthrough |

---

## Instructor Notes

- **This plan is grounded entirely in local pptx text-extraction.** No platform unit IDs, quiz-bank question IDs, or MCQ-pool counts exist for this topic yet.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **This session already ran exactly 2 activities before this recalibration** — Activity 1 is Timed Silent Solve → Reveal (Q6–Q8), Activity 2 is Fastest-Method Match (recognition, reusing all 10 questions). No activity was demoted; only timing and headers changed.
- **Warm-up poll reach-back (judgment call):** the immediately-previous session (8) was a Numbers consolidation session and contains no LCM/HCF content — reusing it would test the wrong material. The poll instead draws on Session 3, the actual source of the methods this deck applies. <!-- placement: inferred -->
- **No new content today.** If a student asks "wait, is this new?", the answer is no — say so directly. The value of this session is speed and method-recognition.
- **ALS Activity 2 depends on Activity 1 and Slide Blocks A/B already being delivered** — it reuses those exact questions. Do not run it out of order.
