# Session 8 — Company-Specific MCQs: Numbers

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Company-Specific MCQs — Numbers (solved-problem consolidation) · **Prerequisite** Sessions 2–7 (Number Systems through Remainder Cycles)
**Session type** Consolidation / review lecture. No new concept is introduced. No classroom quiz bank, MCQ pool, or coding-practice unit IDs exist yet — no quiz block for that reason. · **Format** 50-min recalibrated, 2 ALS activities

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `1) NIAT_CSMCQ'S_Numbers.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Apply the digit-sum divisibility identity (a number minus its digit sum is always a multiple of 9, and therefore of 3) to justify an answer without testing a specific number. *(APPLYING)*
2. Convert decimals — both terminating products and a pure recurring decimal — into fractions to simplify a calculation or express an exact value. *(APPLYING)*
3. Apply power-cycle patterns to find units digits and remainders for large exponents without direct computation. *(APPLYING)*
4. Analyze a small set of candidate numbers or options to identify which pair is co-prime, by testing common factors directly rather than deriving from scratch. *(ANALYZING)*
5. Evaluate which solving method — direct computation, option verification, or a general identity — is fastest for a given placement-style question. *(EVALUATING)*
6. Distinguish questions that require substituting a specific value from questions solvable by a general rule, and choose the faster strategy under time pressure. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 7 (3–7 min) · ALS: Polling

5 questions on **Session 7 (Remainder Cycles)**. Every number below is taken directly from that deck. ~45 s each, project the distribution, never name individuals.

<!-- placement: inferred — exponents below were reconstructed from a pptx extraction artifact; see Instructor Notes -->

**Q1.** Find the remainder when 140 is divided by 12.
`A` 6 · `B` 8 · `C` 4 · `D` 10
→ **B.** *Targets:* plain remainder recall. Warm-up floor question — if missed by more than a couple of students, slow down for the rest.

**Q2.** Find the remainder when 4^5 is divided by 15.
`A` 1 · `B` 4 · `C` 8 · `D` 11
→ **B.** *Targets:* small-exponent case where direct computation is still faster than building a cycle — sets up today's method-choice theme.

**Q3.** Find the remainder when 2^356 is divided by 5?
`A` 1 · `B` 2 · `C` 4 · `D` 8
→ **A.** *Targets:* remainder-cycle of 2 mod 5 is {2,4,3,1}, length 4; 356÷4 leaves remainder 0, landing on the last term, 1. *If wrong:* the off-by-one on "remainder 0 means last term" is the exact mistake to re-teach.

**Q4.** Find the remainder when 477^856 is divided by 4?
`A` 1 · `B` 0 · `C` 3 · `D` 2
→ **A.** *Targets:* "reduce the base first" — 477 mod 4 = 1, and 1 raised to anything is 1. This exact shortcut is today's key move.

**Q5 (MSQ — select all).** A prime number greater than 3 is divided by 6. Which remainders are possible?
`A` 1 · `B` 2 · `C` 4 · `D` 5
→ **A and D.** *Targets:* any prime greater than 3 is coprime to 6, so it must land on 1 or 5 mod 6.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–11 min)

Put this on screen, nothing else, no context, no hint column:

> X is a 5-digit number. When we subtract the sum of the digits from X, it becomes divisible by?
> `A` 3 and 9 · `B` 4 · `C` 7 · `D` 6

Say: *"Sixty seconds. Silent. No talking, no notes. This is question one of a real company-specific placement set — solve it cold, the way you will on test day."*

Run a visible 60-second timer. At time, take a show of hands per option — do not reveal the answer yet.

> *"Hold that answer in your head. Here's the thing: that's not a made-up example. That is literally question one of a real company placement Numbers section. Today we are not learning anything new — Sessions 2 through 7 already gave you every tool you need. Today is ten of these, back to back, exactly the way they'll show up on test day, plus the fastest way to each answer."*

Move straight into Slide Block A, which opens by resolving this exact question.

---

## Slide Block A (11–20 min) — DELIVER AS-IS

Covers Company-Specific Questions 1–5 from the deck, each with its real worked solution. For each: state the question, reveal the real answer, then give the fastest method.

**Q1 — X is a 5-digit number. When we subtract the sum of the digits from X, it becomes divisible by?**
Options: 3 and 9 · 4 · 7 · 6 → **Answer: 3 and 9**

- Fastest method: you never need a real number. Every digit's place value is a power of 10, and every power of 10 ≡ 1 (mod 9). So any number ≡ its own digit sum (mod 9) — meaning the *difference* between them is always a multiple of 9, and therefore of 3.
- The deck's own worked example (X = 43,269 → sum = 24 → 43,269 − 24 = 43,245, divisible by 9) is an illustration, not a required step. Show it once, then say explicitly: "you do not need to pick a number on the real test — this is always true."

**Q2 — What number should be divided by (0.81)^1/2 to give the result as 81?**
**Answer: 72.9**

- Fastest method: recognise 0.81 = 0.9² immediately, so (0.81)^1/2 = 0.9 — don't reach for a calculator. Then it's one multiplication: 81 × 0.9 = 72.9.

**Q3 — Which is the closest approximation to the product 0.3333 × 0.25 × 0.499 × 0.125 × 24?**
Options: 0.128 · 0.12 · 0.126 · 0.125 → **Answer: 0.125**
Deck's own Hint: *"Convert the decimals into fractions."*

- Fastest method: recognise each decimal as a familiar fraction before multiplying anything — 0.3333 ≈ 1/3, 0.25 = 1/4, 0.499 ≈ 1/2, 0.125 = 1/8. Multiply and cancel: (1/3)(1/4)(1/2)(1/8)(24) = 24/192 = 1/8 = 0.125.

**Q4 — When an integer n is divided by 8, the remainder is 3. What is the remainder when 6n is divided by 8?**
Options: 2 · 3 · 4 · 6 → **Answer: 2**

- Fastest method: don't solve algebraically — plug in the *least* valid value of n (n=3). 6n = 18; 18 ÷ 8 leaves remainder 2. The deck notes this holds for any valid n, not just 3.

**Q5 — What smallest number should be added to 1056 so that the number is completely divisible by 23?**
Options: 2 · 0 · 1 · 3 → **Answer: 2**

- Fastest method: find the remainder first (1056 ÷ 23 leaves remainder 21), then subtract from the divisor: 23 − 21 = 2. Deck's own edge-case Note: *"If the remainder is 0, the smallest number to add would be 0"* — not the divisor itself.

**Checkpoint (at 20 min)** — 10 s silent think, cold-call two students:
> *"Why is X minus the sum of its digits always divisible by 9, for any 5-digit number at all — not just 43,269?"*
> **Answer:** Every digit's place value is a power of 10, and every power of 10 leaves remainder 1 when divided by 9. So the number always has the same remainder mod 9 as its digit sum — subtracting them cancels that remainder.

---

## ⚡ ALS Activity 1 — 60-Second Solve, Then I Reveal (20–27 min)

**ALS format:** Timed Individual Solve → Show-of-Hands → Reveal — two more real deck questions, one at a time, 60 seconds silent individual solving, then committing to an answer before the real worked answer is revealed. Chosen right after Slide Block A because students need to solve cold themselves before the next block of solutions, mirroring the pressure of the Hook.

**Setup line:**
> *"Sixty seconds, silent, no talking. Commit to an answer before I say time — hands up for your letter the second I call it. I reveal right after. This is exactly the pressure of the real thing."*

**Q6.** What is the remainder when (2p + 2)² is divided by 4, where p is any integer?
Options: 1 · 2 · 3 · None of the above
**Real answer: None of the above** — (2p + 2) is always even, and the square of an even number is always divisible by 4, so the remainder is 0 (not listed).

**Q7.** Find the remainder when 5^195 is divided by 3.
Options: 1 · 3 · 4 · 2
**Real answer: 2** — 5^n mod 3 cycles {2, 1}; 195 ÷ 2 leaves remainder 1, landing on the first term, 2.

**When it goes wrong**

| If… | Do this |
|---|---|
| Most of the room picks 1, 2, or 3 for Q6 | Expected — that's the trap. Reveal that "None of the above" is correct *because* the real remainder (0) was never printed as an option. Real placement tests do this on purpose. |
| Nobody attempts a cycle for Q7 in 60 seconds | Fine — it's meant to feel tight. Ask "what would you have needed to know in advance?" and answer: the cycle {2,1}, memorised, not derived live. |

**Debrief line:**
> *"The reveal is only useful paired with the reasoning in the same breath — the method, not the score, is the point."*

**Cut rule:** If running short, run Q7 only. Power-cycle remainders are the more test-relevant shortcut and recur in Slide Block B and ALS Activity 2.

---

## Slide Block B (27–37 min) — DELIVER AS-IS

Covers Company-Specific Questions 7, 9, and 10 from the deck, with their real worked solutions.

**Q7 — What will be the units digit in the result of the expression (3^65) x (6^53) x (9^5)?**
Options: 6 · 2 · 3 · 7 → **Answer: 2**
Deck's own Hint: *"Recall the power cycle concept."*

- Never compute the actual powers — track each base's units-digit cycle and reduce the exponent by the cycle length. 3's cycle {3,9,7,1}, length 4: 65÷4 remainder 1 → units digit 3. 6 always ends in 6. 9's cycle {9,1}, length 2: 5÷2 remainder 1 → units digit 9. Multiply: 3×6×9=162 → units digit **2**.

**Q9 — Out of the three numbers 26, 13, and 34, which two are the co-prime numbers?**
Options: 26 and 13 · 26 and 34 · 13 and 34 · None of these → **Answer: 13 and 34**
Deck's own Hint: *"Go for option verification."*

- Don't factorise all three from first principles — test the three *given* pairs directly for a shared factor: (26,13) share 13; (26,34) share 2; (13,34) share only 1 → co-prime.

**Q10 — Express 1.0232323….. as a fraction?**
Options: 1023/1000 · 1013/990 · 1023/99 · 1013/99 → **Answer: 1013/990**

- Identify the repeating block ("23") and the one non-repeating digit ("0"). x = 1.0232323…, 10x = 10.2323…, 1000x = 1023.2323…. Subtract: 1000x − 10x = 1013 → 990x = 1013 → x = 1013/990.

**Method-race beat (2 min, compressed from a full activity):** *"Two ways to solve Q9 — test only the three given pairs, or fully factorise all three numbers first. Which is faster, and why does it stay faster even with five options instead of three?"* Take 2-3 answers. *"Verification degrades much faster than factorisation as the option count grows — that's why the deck's own hint says option verification."* (Compressed to protect the schedule.)

**Checkpoint (at 37 min)** — show hands:
> *"6 raised to any positive power — what's the units digit, always?"*
> **Answer:** 6. Every power of 6 ends in 6 — no cycle to track, unlike 3 or 9.

---

## ⚡ ALS Activity 2 — Fill the Blank Live: Power Cycle Shortcut (37–45 min)

**ALS format:** Cold-Call Fill-the-Blank — the real worked solution to Q7 (units digit of (3^65)(6^53)(9^5)) goes on screen with the key numbers blanked out, and students call out the missing values live, one at a time, rebuilding the shortcut method as a class. Chosen as the closing activity because Q7 is the session's densest multi-step shortcut — reproducing it themselves, out loud, is the real test of whether it landed, not just watching it solved a second time.

**Setup line:**
> *"I'm not writing this one — you are, out loud. I'll point, you fill the blank. One number at a time, and I want the reasoning, not just the digit."*

**The skeleton (blanks in bold, real answers given here for you):**

> 3's units-digit cycle: {3, 9, 7, 1}, length **4**.
> 65 ÷ 4 leaves remainder **1** → units digit of 3^65 is **3**.
> 6 to any power always ends in **6**.
> 9's units-digit cycle: {9, 1}, length **2**.
> 5 ÷ 2 leaves remainder **1** → units digit of 9^5 is **9**.
> Multiply the units digits: 3 × 6 × 9 = **162** → final units digit is **2**.

**When it goes wrong**

| If… | Do this |
|---|---|
| Class stalls on "why does the cycle length matter" | Ask: "if I told you the exponent was exactly the cycle length, what would the units digit be?" — it's always the *last* term of the cycle. |
| Someone tries to actually multiply out 3^65 | Let them start, then stop after ten seconds: "that's the point — this is why the cycle exists." |
| The room fills blanks correctly but mechanically, nobody can explain "remainder 1 → first term" | Ask explicitly: "if the remainder were 0 instead of 1, which term would we use?" (Answer: the last term, not a zeroth term.) |

**Common instructor mistake:** filling in a blank yourself when the class is slow to answer. Wait the full silence out.

**Cut rule:** Run only the 3^65 portion (skip 6^53 and 9^5 detail) and jump straight to "multiply the three units digits" using 3, 6, and 9 as givens.

---

## Exit Ticket + Homework (45–48 min)

**Exit ticket** (~1 min) — on paper or in chat before anyone leaves:

> Out of the three numbers 26, 13, and 34, which two are co-prime, and why in one sentence?
> **Answer:** 13 and 34 — their only common factor is 1.

Scan responses on the way out. If most students still reach for full factorization instead of testing the given pairs, that's the signal to reopen the option-verification method for 90 seconds at the start of Session 9.

**Homework**

| Task | Detail |
|---|---|
| Redo Q3, Q7, and Q10 cold, no notes | The decimal-product conversion, the three-base units-digit cycle, and the recurring-decimal-to-fraction — the three questions with the most steps in today's deck |
| Revisit Session 2, 6, and 7 material for any rule used today that felt shaky | No dedicated practice unit exists yet for this topic — homework is the same 10 real questions, attempted a second time unaided |

Tell them: *"Nothing on the actual test will look exactly like today's ten questions — but the four moves you used today (digit-sum identity, decimals-to-fractions, power cycles, option verification) will cover almost everything you see. Redo the hard three before next session."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Multiply the decimals directly instead of converting to fractions first | Decimals feel more "exact" and immediate than fractions | The deck's own Hint on Q3 — Slide Block A runs the fraction cancellation live |
| Try to compute 3^65 or 6^53 as an actual number | No instinct yet that huge exponents are a signal to shortcut, not calculate | The deck's own Hint on Q7 — reinforced by ALS Activity 2's fill-the-blank |
| Fully factorise all candidate numbers before comparing, instead of testing the given pairs | Feels more rigorous than "just checking" the options in front of you | The deck's own Hint on Q9 — proven live by Slide Block B's method-race beat |
| Assume the correct answer to "(2p+2)² mod 4" must be one of the printed numeric options | Trusting the right answer is always literally on the list | ALS Activity 1's reveal on Q6 — "None of the above" because the true remainder (0) was deliberately not printed |
| Always add (divisor − remainder) to reach the next multiple, even when the remainder is already 0 | Pattern-matching Q5's rule without checking the edge case | The deck's own Note under Q5 — state this explicitly in Slide Block A |

---

## Instructor Notes

- **Grounding.** This plan is built entirely from local pptx text-extraction of two decks — `1) NIAT_CSMCQ'S_Numbers.pptx` (this session) and the Session 7 deck (used only for the warm-up poll). No platform unit IDs, classroom quiz bank, or MCQ/coding-practice pool exist yet.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Timed Individual Solve → Show-of-Hands → Reveal (new content, Q6 & Q8), Activity 2 is Cold-Call Fill-the-Blank (reinforces Q7, already delivered in Slide Block B). The original Fastest-Method Board Race on Q9 is folded into a 2-minute method-race beat inside Slide Block B instead of running as its own block — Q9 already gets full treatment there with the deck's own hint stated.
- **Consolidation, not new content.** Session 8 of 23. Nothing here is a new concept — it is Sessions 2, 6, and 7's tools applied to ten real solved placement-style questions.
- <!-- placement: inferred --> **Warm-up poll exponents were reconstructed** from a pptx extraction artifact that split superscripts into separate text runs. Each was verified by recomputing the stated remainder against the deck's own listed answer.
- **This session's own deck did not show that artifact** — all exponents in the CSMCQ Numbers deck extracted intact with carets and were cross-checked against the deck's own "Solution:" prose.
- **Pacing risk:** Slide Block A covers 5 full questions in 9 minutes. If running long, compress Q2 and Q4 to a single stated line each rather than full board derivations — Q1, Q3, and Q5 carry the session's real teaching weight.
- **No separate practice pool:** homework deliberately reuses the same 10 deck questions rather than pointing to a coding/MCQ practice unit.
