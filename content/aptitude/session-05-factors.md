# Session 5 — Factors

**Duration** 60 min · **Topic** Factors (deep dive) — counting/summing/multiplying factors, then HCF-style applications · **Prerequisite** Session 4 (Multiples)
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet for this topic.

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

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 4 (Multiples)**. Newly authored from that deck's real content. ~45 s each, project the distribution, never name individuals.

**Q1.** In Session 4: when two numbers are multiplied, what is the result called?
`A` A factor · `B` A multiple · `C` A divisor · `D` A remainder
→ **B.** *Targets:* the core definition — "when two numbers are multiplied the resultant is called multiple."

**Q2.** Per the deck's own example — `10 × 3 = 30` and `10 × 4 = 40`. Which of these are multiples of 10? *(MSQ — select all)*
`A` 30 · `B` 40 · `C` 35 · `D` 50
→ **A and B.** *Targets:* reading the multiplication statement in both directions. *Misconception:* picking C or D shows the student is guessing "multiples of 10" from a times-table reflex rather than the deck's actual worked pair.

**Q3.** A number divided by 3, 5, and 11 leaves remainder 2 each time. What's the least 3-digit number satisfying this?
`A` 167 · `B` 178 · `C` 185 · `D` 200
→ **A) 167.** *Targets:* the "common remainder" number-building technique from Session 4.

**Q4.** *(verbatim from the deck, with its own options)* The least number which when divided by 21, 25 and 35 leaves a remainder of 13 is:
`A` 128 · `B` 518 · `C` 538 · `D` 48
→ **C) 538.** *Targets:* same technique, applied to three divisors at once. *If missed heavily:* the LCM(21,25,35) + 13 construction needs a 30-second reteach before Slide Block A starts.

**Q5.** What is the least number that should be added to 2502 so the sum is exactly divisible by 5, 6, 7 and 8?
`A` 12 · `B` 18 · `C` 24 · `D` 30
→ **B) 18.** *Targets:* "least number to add" as the mirror case of "least number to subtract."

**Q6.** Three bells ring at intervals of 120, 240 and 300 seconds. After how many minutes will they next ring together?
`A` 10 · `B` 15 · `C` 20 · `D` 25
→ **C) 20 mins.** *Targets:* LCM-of-intervals reasoning, and unit conversion (seconds → minutes) at the end.

**Q7.** What is the highest power of 12 in 100! ?
`A` 46 · `B` 48 · `C` 50 · `D` 52
→ **B) 48.** *Targets:* counting how many times a composite prime-power divides into a factorial. *Read this one out loud after revealing the answer:* "Hold that thought — counting prime powers inside a number is exactly the skill today's whole session is built on. Today we just point it at plain numbers instead of factorials."

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including your reads. Q7 is the deliberate bridge into today's Hook.

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

## Slide Block A (10–24 min) — DELIVER SLIDES AS-IS

Covers: Recap → Agenda ("Factors") → the core formula slide → worked examples (sum of factors of 240, product of factors of 60, number of factors of 1200, even-factor-count of 3-digit numbers, a remainder problem).

<!-- placement: inferred — the deck's formula slide renders "N = (a|x) x (b|y) x (c|z)" in the text extraction because it was laid out as a table/image in the original slide, and the "Sum of factors = " line has no formula text following it in the extraction (also image-rendered). Reconstructed below from the standard identity and cross-checked against every numeric answer the deck actually gives — all matched exactly. -->

**The formula, as delivered:**

For N = aˣ × bʸ × cᶻ (prime factorization):
- **Number of factors** = (x+1)(y+1)(z+1)
- **Sum of factors** = [(aˣ⁺¹−1)/(a−1)] × [(bʸ⁺¹−1)/(b−1)] × [(cᶻ⁺¹−1)/(c−1)]
- **Product of factors** = N^(number of factors / 2)

**Beats to emphasise**

- **Prime-factorize first, always.** Every problem on these slides starts there — students who skip straight to guessing the answer stall immediately.
- **Three different questions, three different formulas.** "How many factors" is not "what do they sum to" is not "what do they multiply to." Say this once, explicitly, before running any example — it's the single easiest thing to blur.
- Run the worked examples live, in order, letting the class verify each against the deck's stated answer:
  - **Sum of factors of 240:** 240 = 2⁴ × 3¹ × 5¹. Sum = 31 × 4 × 6 = **744**.
  - **Product of factors of 60:** 60 = 2² × 3¹ × 5¹. Number of factors = 3×2×2 = 12. Product = 60^(12/2) = **60⁶**. Flag the deck's own hint: *"First find number of factors"* — the product formula needs that count as an input, so skipping it is the most common stall point.
  - **Number of factors of 1200:** 1200 = 2⁴ × 3¹ × 5². Count = 5×2×3 = **30**.
- **The 3-digit even-factor-count problem is the odd one out — hold it back as the checkpoint below rather than fully explaining it here.**

**Checkpoint (at 24 min)** — cold-call:
> *"How many 3-digit numbers have an even number of factors? And in one sentence, why isn't the answer just 900?"*
> **Answer:** 878. There are 900 three-digit numbers total (100–999). Only perfect squares have an *odd* number of factors — because every other factor pairs up with a partner, while a perfect square's square-root factor pairs with itself. The 3-digit perfect squares run from 10² to 31², which is 22 numbers. 900 − 22 = 878.

**A second real example, if the checkpoint lands fast:** the deck's own remainder problem — a number divided by 36 leaves remainder 19; divided by 12 (a factor of 36), the remainder is **7** (since 19 = 12×1 + 7). Use it to reinforce: once you know a number's relationship to 36, you already know its relationship to every factor of 36.

---

## ⚡ Activity 1 — Trace the Table (24–32 min)

### What this activity is

Students trace the prime-factorization-to-formula pipeline step by step, on paper, for three of the deck's own numbers — 240, 60, and 1200 — building a small table (prime, power, +1) each time, then reading the formula output straight off it.

### Why it's here

Slide Block A just *showed* the pipeline. This activity makes every student run it with their own hand, on numbers they haven't pre-memorised the answer to, before the next block moves on to a different family of problems (HCF).

### Before class

Have the three numbers (240, 60, 1200) ready on a slide or the board, each with a blank three-column table underneath: **Prime | Power | Power+1**.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line | Listen |
| 0:30–1:30 | Demo: fill the table for 240 live, on the board | Watch, copy |
| 1:30–5:30 | Give 60 and 1200, wait | Fill both tables individually |
| 5:30–7:30 | Take answers from two different students, one number each | Answer, everyone checks their own table |
| 7:30–8:00 | Debrief | Listen |

### Say this

> *"You just watched me do 240. Now you do 60 and 1200, on your own — same three columns: prime, power, power-plus-one. Once the table's built, the formula is just multiplying the last column. Four minutes."*

### The numbers and answers

| Number | Prime factorization | Table (prime / power / power+1) | Number of factors |
|---|---|---|---|
| 240 | 2⁴ × 3¹ × 5¹ | (2,4,5)(3,1,2)(5,1,2) | 5×2×2 = **20** |
| 60 | 2² × 3¹ × 5¹ | (2,2,3)(3,1,2)(5,1,2) | 3×2×2 = **12** → product of factors = 60⁶ |
| 1200 | 2⁴ × 3¹ × 5² | (2,4,5)(3,1,2)(5,2,3) | 5×2×3 = **30** |

Note: 240's own factor *count* (20) wasn't stated on the deck's slide — the deck asked for its *sum* (744) instead. Use 240 only for the demo table; take the two graded answers from 60 and 1200, which match the deck's stated results exactly.

**How it surfaces:** Watch for students who write the exponent itself in the last column instead of exponent+1 — that's the single most common table error and it's usually silent until they get a factor count that's obviously too small.

**Debrief line:**
> *"Every one of today's 'count/sum/product' problems is this same table. The only thing that changes is which column you read off at the end."*

**Cut rule:** If running long, drop 1200 and take only the 60 answer — it's the one that also produces the product-of-factors result (60⁶), so it carries the most of the block's content in one number.

---

## Classroom Quiz (originally 27–34 min slot — reallocated)

> Classroom Quiz: not yet available — add once question bank exists for this topic.

No question bank exists for Factors yet, so this 7-minute slot is not run as a quiz. Its time is folded into the surrounding blocks instead: Slide Block A gains 2 min (12→14), Activity 1 gains 3 min (5→8), Slide Block B gains 2 min (10→12), Activity 2 gains 2 min (6→8) — offset by Activity 3 running 2 min shorter (7→5) since it is the lightest-lift of the three activities. Net effect: +7 min absorbed, 0 min left unaccounted for. The 60-minute timeline below reflects this directly — there is no gap.

---

## Slide Block B (32–44 min) — DELIVER SLIDES AS-IS

Covers: perfect-square HCF problem → HCF-with-remainders (two variants) → HCF-and-co-prime-pairs → smallest number with a given divisor count → decimal HCF → HCF-and-co-prime-pairs (second instance) → longest-common-measure ("tape") problem.

<!-- placement: inferred — the deck marks slide 10 ("Quiz Time") as a section break between the count/sum/product problems above and this run of HCF-flavoured problems; the deck does not explicitly label these as "Slide Block A" and "Slide Block B," that split is this plan's own structuring choice. -->

**Frame the transition explicitly, out loud:**
> *"We just learned to count factors going forward — given N, how many factors, what do they add up to. Now watch the same prime-factorization table work sideways, into HCF, and once — backward, where you're given the factor count and have to find N."*

**Beats to emphasise**

- **The deck hands you the technique inside the question itself.** Three of these slides carry the identical hint line: *"Try finding HCF if you find highest / greatest / longest in the question."* Say this explicitly — it's not a coincidence, it's the pattern the deck wants students to notice.
- **Two remainder variants look alike but aren't:**
  - *Different remainders stated* (30, 39, 50 leaving 6, 3, 2) → **subtract each remainder from its number**, then HCF: HCF(24, 36, 48) = **12**.
  - *Same remainder, unstated* (30, 39, 57) → **subtract pairwise differences**, then HCF: HCF(9, 18, 27) = **9**.
  Put both on the board side by side — this is the pairing to watch for confusion on.
- **HCF and co-prime pairs, run twice in this block:** product of two numbers 6300, HCF 15 → numbers are 15a, 15b with a,b co-prime and ab = 28 → co-prime pairs of 28 are (1,28) and (4,7) → **2 pairs**. The second instance (product 6845, HCF 37) uses the same idea to find one specific number: ab = 5, only co-prime pair is (1,5), so the numbers are 37 and 185 → greater number = **185**.
- **The reverse-direction problem is today's formula run backward:** smallest number with 15 divisors. 15 = 5×3, so exponents are 4 and 2; assign the larger exponent to the smaller prime: 2⁴ × 3² = **144**. Say explicitly: *"This is literally this morning's formula, (x+1)(y+1), solved for x and y instead of for the answer."*
- **Decimal HCF needs a scaling step first:** 0.36, 0.48, 1.36 → ×100 → 36, 48, 136 → HCF = 4 → scale back → **0.04**. The most common silent error is forgetting to scale the final HCF back down.
- **The "longest tape" problem is a unit-conversion trap before it's an HCF problem:** 8m 25cm, 6m 75cm, 4m 50cm → convert everything to cm (825, 675, 450) → HCF = **75** (cm).

**Checkpoint (at 44 min)** — show hands:
> *"144 has exactly 15 divisors. Using this morning's formula, why? Give me the two numbers that multiply to 15."*
> **Answer:** 144 = 2⁴ × 3², so number of divisors = (4+1)(2+1) = 5 × 3 = 15.

---

## ⚡ Activity 2 — Rapid Fire Board Race (44–52 min)

### What this activity is

Two teams. You read out just the *phrasing* of a problem stem — not the full numbers yet — and the first team to correctly shout the technique it calls for ("HCF!" plus the specific twist: subtract-remainder / subtract-difference / perfect-square / co-prime-pair) scores a point. After all stems are called, you solve two of them live with the class using the real deck numbers.

### Why it's here

Slide Block B just showed that "highest," "greatest," and "longest" are all the same instruction in disguise — plus two remainder variants that look alike but aren't. This activity tests whether students actually caught the pattern, at speed, before they leave the room.

### Before class

Write the five stems (below) on cards or a slide, in shuffled order, phrasing only — no numbers yet.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line | Listen |
| 0:30–4:30 | Read each stem, award points | Shout technique, teams race |
| 4:30–7:30 | Reveal numbers for 2 stems, solve live | Work along, check answers |
| 7:30–8:00 | Debrief | Listen |

### Say this

> *"I'll read you five problem stems, no numbers. First team to shout the correct technique — and the specific twist — gets the point. 'HCF' alone isn't enough on the remainder ones; I need to hear which kind."*

### The stems (from the deck) and correct calls

| # | Stem (as read aloud) | Correct call | Real numbers (for the live solve) |
|---|---|---|---|
| 1 | "Find the highest perfect square number which divides 25, 75 and 300." | HCF, then check if it's already a perfect square | HCF(25,75,300) = 25 (already a perfect square) |
| 2 | "Find the greatest number that divides 30, 39 and 50, leaving remainders 6, 3 and 2." | HCF, subtract each stated remainder first | HCF(24,36,48) = **12** |
| 3 | "Find the greatest number that divides 30, 39 and 57, leaving the *same* remainder each time." | HCF, subtract pairwise differences first | HCF(9,18,27) = **9** |
| 4 | "The product of two numbers is 6300 and their HCF is 15. How many such pairs exist?" | HCF, then count co-prime pairs | ab = 28 → 2 pairs: (1,28),(4,7) |
| 5 | "The longest tape which can exactly measure 8m 25cm, 6m 75cm, and 4m 50cm." | HCF, convert units first | HCF(825,675,450) cm = 75 cm |

**Live-solve stems 2 and 3 together, side by side on the board** — that pairing is exactly where the room's confusion lives, and seeing both worked next to each other is the point of the activity.

**How it surfaces:** If a team shouts "HCF" on stem 2 or 3 but can't say *which* variant, don't award the point yet — ask "subtract what, from what?" That question is the actual skill.

**Debrief line:**
> *"Five different sentences, one operation underneath every one of them. The words that gave it away: highest, greatest, longest. Say those three words in your head from now on and HCF, not LCM, should be the reflex."*

**Cut rule:** If running short on time, drop stems 1 and 5 from the race and go straight to live-solving 2 and 3 — those two carry the block's hardest distinction.

---

## ⚡ Activity 3 — Think–Pair–Share (52–57 min)

### What this activity is

Two remaining problems from the deck — the decimal HCF (0.36, 0.48, 1.36) and the second co-prime-pair problem (product 6845, HCF 37) — given to pairs of students to work through together, then shared cold-call style. Unlike the rapid-fire pace of Activity 2, this one deliberately slows down for the two problems in the block that need a careful extra step (decimal scaling; solving for the *specific* greater number, not just a count of pairs).

### Why it's here

Both problems are one careless step away from a wrong answer — forgetting to rescale the decimal, or reporting the co-prime multiplier pair instead of the actual numbers. A quiet pair-think catches that step better than a shouted answer does.

### Before class

Have both problems on one slide, side by side.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:20 | Setup line | Listen |
| 0:20–2:20 | Silent think, alone | Attempt individually |
| 2:20–3:50 | "Turn to your partner, compare" | Pair, reconcile answers |
| 3:50–4:50 | Cold-call two pairs, one problem each | Share answer + method |
| 4:50–5:00 | Debrief | Listen |

### Say this

> *"Two problems, two minutes alone first — no talking. Then ninety seconds with your partner to compare and fix anything that doesn't match. I will cold-call, so make sure you both agree before time's up."*

### The problems and answers

| Problem | Working | Answer |
|---|---|---|
| Find the GCD of 0.36, 0.48, 1.36 | ×100 → HCF(36,48,136) = 4 → ÷100 | **0.04** |
| Product of two numbers is 6845, HCF is 37 — find the greater number | ab = 6845/37² = 5 → only co-prime pair (1,5) → numbers are 37, 185 | **185** |

**How it surfaces:** The most common pair-disagreement is one partner reporting "4" instead of "0.04" on the decimal problem, or one partner reporting "5" (the co-prime multiplier) instead of "185" (the actual greater number) on the second. Both are the exact same category of mistake — stopping one step before the question actually asked.

**Debrief line:**
> *"Both of today's traps are the same trap: the formula gets you 90% there, and then the question asks for one more small step — rescale, or multiply back up. Always re-read the question after you get a number."*

**Cut rule:** If time is short, run the co-prime-pair problem only (185) — it's the one whose "stop one step early" trap most directly mirrors Activity 2's stem 4.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — on paper or in chat before anyone leaves:

> N = 1200. Using today's formula, how many factors does N have — and which prime powers did you use to get there?
> **Answer:** 30. 1200 = 2⁴ × 3¹ × 5² → (4+1)(1+1)(2+1) = 5×2×3 = 30.

Scan responses on the way out. Anyone who reaches for the wrong exponents (or forgets the "+1") is the signal to open Session 6 with a 60-second formula recap.

**Homework**

- Redo all eight HCF-style problems from today's Slide Block B (the "highest perfect square," both remainder variants, both co-prime-pair problems, the divisor-count reversal, the decimal GCD, and the tape problem) **from a blank page, without the on-slide hints visible.** Then check your working against the hint line printed on each slide.
- Re-derive, from scratch, the number of factors, sum of factors, and product of factors of 240 — all three, not just the one the deck asked for. Compare your sum and product against 744 and the pattern used for 60⁶.

> *"Next session builds on today directly. If today's formula isn't automatic by tomorrow, everything after it gets harder than it needs to be."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| "Product of factors" means the answer should look like N | They stop at N instead of applying the formula | Running 60 → 60⁶ live in Slide Block A and naming the deck's own hint: "first find number of factors" |
| Number-of-factors and sum-of-factors use the same calculation | Both start from the same prime factorization table | Activity 1 — same table, explicitly different last step for each |
| "Greatest," "highest," "longest" might mean LCM, since Session 4 wired "least" to LCM-style thinking | Direct carry-over from the previous session's opposite keyword | Activity 2's rapid-fire round, plus the deck's own repeated hint line |
| The two remainder-HCF problems (30,39,50 vs 30,39,57) are the same technique | Both are "greatest number that divides, leaving a remainder" on the surface | Slide Block B's side-by-side board work, then Activity 2 stems 2 and 3 |
| Every number has an even number of factors | Most everyday numbers do — perfect squares are a small, easy-to-forget exception | The 878 checkpoint in Slide Block A, stated as a rule and left visible |
| GCD of decimals is found by taking HCF of the digits directly | Ignoring decimal places "looks like" the same numbers | Slide Block B and Activity 3 — scale by 100 first, then scale the answer back down |

---

## Instructor Notes

- **This plan is grounded entirely in a local pptx text-extraction of `NIAT Factors.pptx` and `NIAT Multiples.pptx`.** No platform unit IDs, classroom quiz bank, or MCQ/coding practice pool exist yet for this Aptitude course — every "not yet available" line above is literal, not a placeholder to be filled from memory.
- **`<!-- placement: inferred -->` used twice:** (1) the exact formula text on the deck's slide 4 (sum-of-factors formula, and the a/b/c-x/y/z layout) was image-rendered in the original slide and lost in text extraction — reconstructed from the standard identity and verified against every numeric answer the deck states (240→744, 60→60⁶, 1200→30 all check out exactly); (2) the Slide Block A / Slide Block B split point is this plan's own structuring choice around the deck's "Quiz Time" marker (slide 10) — the deck itself doesn't label two halves.
- **All eleven numeric answers in the deck were independently re-derived, not just copied** — 744, 60⁶, 30, 878, 7 (Block A) and 25, 12, 9, 2, 144, 0.04, 185, 75 (Block B). Every one checks out against the deck's stated answer. Trust the numbers in this plan.
- **The deck's two "Quiz Time" slides (10 and 19) carry no extractable question text** — they are almost certainly image-based in the source file. This plan does not build any activity from them; every activity here is built instead from the deck's own numbered worked examples, which do have full text.
- **Pacing risk:** Slide Block B carries eight distinct problems in 12 minutes. Do not attempt to fully solve all eight out loud — deliver the slides, narrate the beats above, and let Activities 2 and 3 do the actual problem-solving. If you find yourself solving problem #6 by minute 40, you are behind; skip to the checkpoint.
- **Have the two remainder-variant problems (30,39,50 vs 30,39,57) pre-written side by side on the board before class starts.** Writing them live during Slide Block B costs time you don't have in this session.
