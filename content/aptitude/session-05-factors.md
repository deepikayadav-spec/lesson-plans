# Session 5 — Factors

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Factors (deep dive) — counting/summing/multiplying factors, then HCF-style applications · **Prerequisite** Session 4 (Multiples)
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet — no quiz block for that reason. · **Format** 50-min recalibrated, 2 ALS activities

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT Factors.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the formula linking a number's prime factorization — N = aˣ × bʸ × cᶻ — to its number, sum, and product of factors. *(REMEMBERING)*
2. Apply the number-of-factors formula (x+1)(y+1)(z+1) to find how many factors a given number has. *(APPLYING)*
3. Compute the sum and the product of the factors of a number, using the two derived formulas rather than listing every factor. *(APPLYING)*
4. Determine how many numbers in a range have an even (vs. odd) number of factors, using the fact that only perfect squares have an odd count. *(ANALYZING)*
5. Recognise word-problem cues — "highest," "greatest," "longest" — that signal an HCF approach, and distinguish the "different remainders" case from the "same remainder" case. *(ANALYZING)*
6. Solve HCF-based word problems involving remainders, co-prime factor pairs, and decimal numbers. *(APPLYING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

5 questions on **Session 4 (Multiples)**. Newly authored from that deck's real content. ~45 s each, project the distribution, never name individuals.

**Q1.** In Session 4: when two numbers are multiplied, what is the result called?
`A` A factor · `B` A multiple · `C` A divisor · `D` A remainder
→ **B.** *Targets:* the core definition.

**Q2.** Per the deck's own example — `10 × 3 = 30` and `10 × 4 = 40`. Which of these are multiples of 10? *(MSQ — select all)*
`A` 30 · `B` 40 · `C` 35 · `D` 50
→ **A and B.** *Targets:* reading the multiplication statement in both directions.

**Q3.** *(verbatim from the deck, with its own options)* The least number which when divided by 21, 25 and 35 leaves a remainder of 13 is:
`A` 128 · `B` 518 · `C` 538 · `D` 48
→ **C) 538.** *Targets:* the LCM(21,25,35) + 13 construction.

**Q4.** Three bells ring at intervals of 120, 240 and 300 seconds. After how many minutes will they next ring together?
`A` 10 · `B` 15 · `C` 20 · `D` 25
→ **C) 20 mins.** *Targets:* LCM-of-intervals reasoning, and unit conversion (seconds → minutes) at the end.

**Q5.** What is the highest power of 12 in 100! ?
`A` 46 · `B` 48 · `C` 50 · `D` 52
→ **B) 48.** *Targets:* counting how many times a composite prime-power divides into a factorial. *Read this one out loud after revealing the answer:* "Hold that thought — counting prime powers inside a number is exactly the skill today's whole session is built on. Today we just point it at plain numbers instead of factorials."

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions. Q5 is the deliberate bridge into today's Hook.

---

## Hook (7–10 min)

Write this on the board, exactly as it appeared in Session 4:

```
10 × 3 = 30      →  30 is a multiple of 10 and 3
```

Say: *"That's where we left off. Two small numbers, multiplied, give you a bigger one. That bigger one is a multiple of both."*

Now put a big arrow underneath, pointing backward, and write just:

```
? × ? = 30
```

Ask: *"Flip it. I hand you only 30, no working shown, and I ask: which numbers multiply together to make you? What do you call the numbers you're hunting for now?"*

Take a few shouted guesses. Reveal:

> *"Those are factors. Same relationship as yesterday — multiplication — just read backward. Yesterday you built a big number from small ones. Today you take a big number apart and don't just list the pieces — you count them, add them up, and multiply them together, all with one formula. That formula is on the next slide."*

---

## Slide Block A (10–20 min) — DELIVER SLIDES AS-IS

Covers: Recap → Agenda ("Factors") → the core formula slide → worked examples (sum of factors of 240, product of factors of 60, number of factors of 1200, even-factor-count of 3-digit numbers, a remainder problem).

<!-- placement: inferred — the deck's formula slide renders "N = (a|x) x (b|y) x (c|z)" in the text extraction because it was laid out as a table/image in the original slide, and the "Sum of factors = " line has no formula text following it in the extraction (also image-rendered). Reconstructed below from the standard identity and cross-checked against every numeric answer the deck actually gives — all matched exactly. -->

**The formula, as delivered:**

For N = aˣ × bʸ × cᶻ (prime factorization):
- **Number of factors** = (x+1)(y+1)(z+1)
- **Sum of factors** = [(aˣ⁺¹−1)/(a−1)] × [(bʸ⁺¹−1)/(b−1)] × [(cᶻ⁺¹−1)/(c−1)]
- **Product of factors** = N^(number of factors / 2)

**Beats to emphasise**

- **Prime-factorize first, always.** Every problem on these slides starts there — students who skip straight to guessing the answer stall immediately.
- **Three different questions, three different formulas.** "How many factors" is not "what do they sum to" is not "what do they multiply to." Say this once, explicitly, before running any example.
- Run the worked examples live, in order, letting the class verify each against the deck's stated answer:
  - **Sum of factors of 240:** 240 = 2⁴ × 3¹ × 5¹. Sum = 31 × 4 × 6 = **744**.
  - **Product of factors of 60:** 60 = 2² × 3¹ × 5¹. Number of factors = 3×2×2 = 12. Product = 60^(12/2) = **60⁶**. Flag the deck's own hint: *"First find number of factors"* — the product formula needs that count as an input.
  - **Number of factors of 1200:** 1200 = 2⁴ × 3¹ × 5². Count = 5×2×3 = **30**.
- **The 3-digit even-factor-count problem is the odd one out — hold it back as the checkpoint below.**

**Checkpoint (at 20 min)** — 10 s silent think, cold-call:
> *"How many 3-digit numbers have an even number of factors? And in one sentence, why isn't the answer just 900?"*
> **Answer:** 878. There are 900 three-digit numbers total (100–999). Only perfect squares have an *odd* number of factors — every other factor pairs up with a partner, while a perfect square's square-root factor pairs with itself. The 3-digit perfect squares run from 10² to 31², which is 22 numbers. 900 − 22 = 878.

---

## ⚡ ALS Activity 1 — Individual Table Build → Cold-Call Check: Trace the Table (20–27 min)

**ALS format:** Individual Table Build, then Cold-Call Check — students trace the prime-factorization-to-formula pipeline step by step, on paper, for the deck's own numbers, building a small table (prime, power, +1) each time, then reading the formula output straight off it. Chosen right after Slide Block A because the pipeline was just *shown* — this makes every student run it with their own hand, on numbers they haven't pre-memorised the answer to, before the session moves to a different problem family (HCF).

**Setup line:**
> *"You just watched me do 240. Now you do 60 and 1200, on your own — same three columns: prime, power, power-plus-one. Once the table's built, the formula is just multiplying the last column. Four minutes."*

Have both numbers ready with a blank three-column table underneath: **Prime | Power | Power+1**.

**The numbers and answers**

| Number | Prime factorization | Table (prime / power / power+1) | Number of factors |
|---|---|---|---|
| 60 | 2² × 3¹ × 5¹ | (2,2,3)(3,1,2)(5,1,2) | 3×2×2 = **12** → product of factors = 60⁶ |
| 1200 | 2⁴ × 3¹ × 5² | (2,4,5)(3,1,2)(5,2,3) | 5×2×3 = **30** |

**How it surfaces:** Watch for students who write the exponent itself in the last column instead of exponent+1 — that's the single most common table error, usually silent until they get a factor count that's obviously too small.

**Debrief line:**
> *"Every one of today's 'count/sum/product' problems is this same table. The only thing that changes is which column you read off at the end."*

**Cut rule:** If running long, drop 1200 and take only the 60 answer — it also produces the product-of-factors result (60⁶), so it carries the most of the block's content in one number.

---

## Slide Block B (27–37 min) — DELIVER SLIDES AS-IS

Covers: perfect-square HCF problem → HCF-with-remainders (two variants) → HCF-and-co-prime-pairs → smallest number with a given divisor count → decimal HCF → HCF-and-co-prime-pairs (second instance) → longest-common-measure ("tape") problem.

**Frame the transition explicitly, out loud:**
> *"We just learned to count factors going forward — given N, how many factors, what do they add up to. Now watch the same prime-factorization table work sideways, into HCF, and once — backward, where you're given the factor count and have to find N."*

**Beats to emphasise**

- **The deck hands you the technique inside the question itself.** Three of these slides carry the identical hint line: *"Try finding HCF if you find highest / greatest / longest in the question."*
- **Two remainder variants look alike but aren't:**
  - *Different remainders stated* (30, 39, 50 leaving 6, 3, 2) → **subtract each remainder from its number**, then HCF: HCF(24, 36, 48) = **12**.
  - *Same remainder, unstated* (30, 39, 57) → **subtract pairwise differences**, then HCF: HCF(9, 18, 27) = **9**.
  Put both on the board side by side — this is the pairing to watch for confusion on.
- **HCF and co-prime pairs:** product of two numbers 6300, HCF 15 → numbers are 15a, 15b with a,b co-prime and ab = 28 → co-prime pairs of 28 are (1,28) and (4,7) → **2 pairs**.
- **The reverse-direction problem is today's formula run backward:** smallest number with 15 divisors. 15 = 5×3, so exponents are 4 and 2; assign the larger exponent to the smaller prime: 2⁴ × 3² = **144**. Say explicitly: *"This is literally this morning's formula, (x+1)(y+1), solved for x and y instead of for the answer."*
- **The "longest tape" problem is a unit-conversion trap before it's an HCF problem:** 8m 25cm, 6m 75cm, 4m 50cm → convert everything to cm (825, 675, 450) → HCF = **75** (cm).

**Quick trap-check beat (2 min):** put these two on screen — *"Product of two numbers is 6845, HCF is 37 — find the greater number"* (10 s silent, then reveal: ab=6845/37²=5 → only co-prime pair (1,5) → numbers 37, 185 → **185**, not 5), and *"GCD of 0.36, 0.48, 1.36"* (×100 → HCF(36,48,136)=4 → ÷100 → **0.04**, not 4). *"Both traps are the same trap — the formula gets you 90% there, then the question asks one more small step. Always re-read the question after you get a number."* (Compressed from a full activity to protect the schedule.)

**Checkpoint (at 37 min)** — show hands:
> *"144 has exactly 15 divisors. Using this morning's formula, why? Give me the two numbers that multiply to 15."*
> **Answer:** 144 = 2⁴ × 3², so number of divisors = (4+1)(2+1) = 5 × 3 = 15.

---

## ⚡ ALS Activity 2 — Rapid Fire Board Race: Pattern Recognition + Live Solve (37–45 min)

**ALS format:** Board Race — the instructor reads just the *phrasing* of a problem stem, no numbers yet, and the first team to correctly shout the technique it calls for scores a point; two of the stems are then solved live with real numbers. Chosen as the closing activity because it tests whether students caught the pattern (highest/greatest/longest → HCF, plus which remainder variant) at speed, before they leave the room — the fastest possible check across the whole session's vocabulary.

**Setup line:**
> *"I'll read you five problem stems, no numbers. First team to shout the correct technique — and the specific twist — gets the point. 'HCF' alone isn't enough on the remainder ones; I need to hear which kind."*

Write the five stems on cards or a slide, shuffled, phrasing only.

**The stems and correct calls**

| # | Stem (as read aloud) | Correct call | Real numbers (for the live solve) |
|---|---|---|---|
| 1 | "Find the highest perfect square number which divides 25, 75 and 300." | HCF, then check if it's already a perfect square | HCF(25,75,300) = 25 (already a perfect square) |
| 2 | "Find the greatest number that divides 30, 39 and 50, leaving remainders 6, 3 and 2." | HCF, subtract each stated remainder first | HCF(24,36,48) = **12** |
| 3 | "Find the greatest number that divides 30, 39 and 57, leaving the *same* remainder each time." | HCF, subtract pairwise differences first | HCF(9,18,27) = **9** |
| 4 | "The product of two numbers is 6300 and their HCF is 15. How many such pairs exist?" | HCF, then count co-prime pairs | ab = 28 → 2 pairs: (1,28),(4,7) |
| 5 | "The longest tape which can exactly measure 8m 25cm, 6m 75cm, and 4m 50cm." | HCF, convert units first | HCF(825,675,450) cm = 75 cm |

**Live-solve stems 2 and 3 together, side by side on the board** — that pairing is exactly where the room's confusion lives.

**How it surfaces:** If a team shouts "HCF" on stem 2 or 3 but can't say *which* variant, don't award the point yet — ask "subtract what, from what?"

**Debrief line:**
> *"Five different sentences, one operation underneath every one of them. The words that gave it away: highest, greatest, longest. Say those three words in your head from now on and HCF, not LCM, should be the reflex."*

**Cut rule:** Drop stems 1 and 5 from the race and go straight to live-solving 2 and 3 — those two carry the block's hardest distinction.

---

## Exit Ticket + Homework (45–48 min)

**Exit ticket** (~1 min) — on paper or in chat before anyone leaves:

> N = 1200. Using today's formula, how many factors does N have — and which prime powers did you use to get there?
> **Answer:** 30. 1200 = 2⁴ × 3¹ × 5² → (4+1)(1+1)(2+1) = 5×2×3 = 30.

Scan responses on the way out. Anyone who reaches for the wrong exponents (or forgets the "+1") is the signal to open Session 6 with a 60-second formula recap.

**Homework**

- Redo all eight HCF-style problems from today's Slide Block B **from a blank page, without the on-slide hints visible.** Then check your working against the hint line printed on each slide.
- Re-derive, from scratch, the number of factors, sum of factors, and product of factors of 240 — all three, not just the one the deck asked for. Compare your sum and product against 744 and the pattern used for 60⁶.

> *"Next session builds on today directly. If today's formula isn't automatic by tomorrow, everything after it gets harder than it needs to be."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| "Product of factors" means the answer should look like N | They stop at N instead of applying the formula | Running 60 → 60⁶ live in Slide Block A |
| Number-of-factors and sum-of-factors use the same calculation | Both start from the same prime factorization table | ALS Activity 1 — same table, explicitly different last step for each |
| "Greatest," "highest," "longest" might mean LCM, since Session 4 wired "least" to LCM-style thinking | Direct carry-over from the previous session's opposite keyword | ALS Activity 2's rapid-fire round, plus the deck's own repeated hint line |
| The two remainder-HCF problems (30,39,50 vs 30,39,57) are the same technique | Both are "greatest number that divides, leaving a remainder" on the surface | Slide Block B's side-by-side board work, then ALS Activity 2 stems 2 and 3 |
| Every number has an even number of factors | Most everyday numbers do — perfect squares are a small, easy-to-forget exception | The 878 checkpoint in Slide Block A |
| GCD of decimals is found by taking HCF of the digits directly | Ignoring decimal places "looks like" the same numbers | Slide Block B's trap-check beat — scale by 100 first, then scale the answer back down |

---

## Instructor Notes

- **This plan is grounded entirely in a local pptx text-extraction of `NIAT Factors.pptx` and `NIAT Multiples.pptx`.** No platform unit IDs, classroom quiz bank, or MCQ/coding practice pool exist yet for this Aptitude course.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Individual Table Build → Cold-Call Check (the formula pipeline), Activity 2 is Board Race Pattern Recognition + Live Solve (HCF keyword detection). The original Think-Pair-Share activity on decimal HCF and the specific-number co-prime problem is folded into a 2-minute trap-check beat inside Slide Block B.
- **`<!-- placement: inferred -->` used twice:** (1) the exact formula text on the deck's slide 4 was image-rendered and lost in text extraction — reconstructed and verified against every numeric answer the deck states; (2) the Slide Block A / Slide Block B split is this plan's own structuring choice.
- **All eleven numeric answers in the deck were independently re-derived, not just copied** — every one checks out against the deck's stated answer.
- **Pacing risk:** Slide Block B carries eight distinct problems. Do not attempt to fully solve all eight out loud — deliver the slides, narrate the beats above, and let ALS Activity 2 do the pattern-recognition work. If you find yourself solving problem #6 by minute 34, you are behind; skip to the checkpoint.
- **Have the two remainder-variant problems (30,39,50 vs 30,39,57) pre-written side by side on the board before class starts.**
