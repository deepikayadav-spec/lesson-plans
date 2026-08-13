# Session 3 — Basics and Properties (Multiples, Factors & LCM/HCF)

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Multiples, Factors & LCM/HCF — Basics and Properties · **Prerequisite** Session 2 (Number Systems 1)
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet — a 5-min quiz slot is reserved but empty for that reason. · **Format** 50-min recalibrated, 2 ALS activities

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT Basics and Properties.pptx` |
| Classroom Quiz | not yet available — 5-min slot reserved at end of session, add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define *multiple* and *factor*, and decide from a division/multiplication fact which number is which. *(REMEMBERING)*
2. Explain the prime-factorisation method for finding the LCM and HCF of two or more numbers. *(UNDERSTANDING)*
3. Apply prime factorisation to compute the LCM and HCF of a given set of numbers (e.g. 18 & 30; 24, 36 & 48). *(APPLYING)*
4. Apply the ratio-based shortcut — ratio `a:b`, HCF `H` → LCM `= H × a × b` — to find an unknown number or the LCM of two numbers in a stated ratio, simplifying the ratio first where needed. *(APPLYING)*
5. Verify the relationship **Product of two numbers = LCM × HCF** for a given pair. *(ANALYZING)*
6. Compute the LCM and HCF of a set of fractions, including a case with no directly visible common factor. *(APPLYING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 2 (3–7 min) · ALS: Polling

5 questions on **Session 2 (Number Systems 1)**. Newly authored from that deck's own content. ~45 s each, project the distribution, never name individuals. Ramp: recall → application → analysis.

**Q1.** In last session's number-classification diagram, which statement about `0` is correct?
`A` `0` is a Natural number · `B` `0` is a Whole number but not a Natural number · `C` `0` is neither Whole nor Natural · `D` `0` is irrational
→ **B.** *Targets:* the `I ⊃ W ⊃ N` nesting (Whole numbers start at 0, Natural numbers start at 1). *If <60% correct:* redraw the nested-set diagram before moving on.

**Q2.** Apply the rule of 7: is **343** divisible by 7?
`A` Yes · `B` No
→ **A (Yes).** *Method:* unit digit `3 × 2 = 6`; remaining digits `34`; `34 − 6 = 28`; 28 is divisible by 7.

**Q3.** Apply the rule of 11: is **3546** divisible by 11?
`A` Yes · `B` No
→ **B (No).** *Method:* odd-place sum `3+4=7`; even-place sum `5+6=11`; difference `= 4`, not 0 or a multiple of 11.

**Q4.** 2 and 3 are co-primes. What are their HCF and LCM?
`A` HCF = 1, LCM = 5 · `B` HCF = 1, LCM = 6 · `C` HCF = 2, LCM = 6 · `D` HCF = 1, LCM = 3
→ **B** (HCF = 1; LCM = product = 6). *Read:* note this score — today's session opens the door to LCM/HCF properties, and co-primes (HCF = 1) is the exact edge case that makes the ratio shortcut click.

**Q5.** *(MSQ — select all that apply)* Which of these divisibility rules were taught as a **combination** of two smaller rules?
`A` Divisible by 6 (needs 2 and 3) · `B` Divisible by 12 (needs 3 and 4) · `C` Divisible by 8 (its own 3-digit rule) · `D` Divisible by 10 (its own last-digit rule)
→ **A and B.** *If someone picks C or D:* they're right that 8 and 10 have rules, but only 6 and 12 were explicitly taught as "divisible by X **and** Y."

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Write these three lines on the board, nothing else:

```
10 × 2 = 20
10 × 3 = 30
10 × 4 = 40
```

Ask: *"What do 20, 30 and 40 all have in common with 10?"* Let the answer land: they're all **multiples of 10**.

Now flip the operation. Write:

```
10 ÷ 2 = 5     (an integer  →  2 is a factor of 10)
7 ÷ 2 = 3.5    (not an integer  →  2 is NOT a factor of 7)
```

Ask: *"So if 2 is a factor of 10, is 10 a multiple of 2?"* — Yes. *"A multiple and a factor are the same division fact, looked at from two directions."*

> *"Every single thing we do for the next forty minutes — LCM, HCF, ratios, fractions — is just multiples and factors, organised. That's the whole session in one board."*

---

## Slide Block A (10–16 min) — DELIVER SLIDES AS-IS

Covers: Multiples → Factors → Methods of finding LCM & HCF (prime factorisation) → the Properties slide (previewed here because ALS Activity 1 needs it immediately).

**Beats to emphasise**

- **Beat 1 — Multiples & Factors.** Use the deck's own examples: `10×2=20`, `10×3=30`, `10×4=40` are multiples of 10; `10/2=5` (2 is a factor of 10), `12/4=3` (4 is a factor of 12), `7/2=3.5` (2 is **not** a factor of 7).
- **Beat 2 — Prime factorisation method for LCM & HCF.** Work both worked examples from the deck, on the board, step by step:
  - LCM & HCF of **18 and 30** → 18 = 2×3², 30 = 2×3×5 → **HCF = 2×3 = 6**, **LCM = 2×3²×5 = 90**.
  - LCM & HCF of **24, 36 & 48** → **HCF = 12**, **LCM = 144**. <!-- placement: inferred — reconstructed from the deck's own prime-factorisation method and cross-checked. Confirm against the live slide before teaching. -->
- **Beat 3 — Properties preview.** <!-- placement: inferred --> State, without yet drilling: *"If the ratio of two numbers is `a:b`, and their HCF is `H`, then LCM `= H × a × b`."* Also flag that **Product of two numbers = LCM × HCF** — you'll verify this properly in Slide Block B.

**Checkpoint (at 16 min)** — 10 s silent think, cold-call two students:
> *"Using prime factorisation, what's the HCF of 18 and 30?"*
> **Answer:** 6 (common prime factors 2 and 3).

---

## ⚡ ALS Activity 1 — Rapid Fire Board Race (16–26 min)

**ALS format:** Board Race — four real problems from the deck, revealed one at a time, increasing in difficulty. Students solve individually or in pairs and race to the board; the instructor takes the first *correct method*, not the first shout.

**Setup line:**
> *"Four problems, one at a time. First person to the board with the **right method**, not just a number, wins the round. Method beats speed."*

**The problems**

| # | Problem | Property used | Answer |
|---|---|---|---|
| 1 | Find `a`, if the LCM & HCF of `(10, a)` is 30 & 5. | Product = LCM × HCF → `a = (30×5)/10` | **15** |
| 2 | Find `a`, if the LCM & HCF of `(48, a)` is 336 & 16. | Product = LCM × HCF → `a = (336×16)/48` | **112** |
| 3 | The ratio of two numbers is 3:4. Their HCF is 6. Find the LCM. | Ratio shortcut → `LCM = H×a×b = 6×3×4` | **72** |
| 4 | The ratio of two numbers is 4:14. Their HCF is 6. Find the LCM. | **Simplify the ratio first** (4:14 → 2:7), then `LCM = 6×2×7` | **84** |

**The trap in Problem 4:** the deck flags this explicitly — *"What is Simplest form of ratios?"* If a student plugs in 4 and 14 directly (`6×4×14 = 336`), that's the exact wrong answer this problem is designed to catch.

**When it goes wrong**

| If… | Do this |
|---|---|
| Everyone uses Product=LCM×HCF for Problems 3–4 too | Fine as a cross-check, but push them to also state the ratio shortcut. |
| Room gets stuck on Problem 4's `336` | Ask: *"Is 4:14 in its simplest form?"* Let them spot the common factor of 2 themselves. |

**Debrief line:**
> *"Method beat speed on every round — that's not a slogan, it's the actual skill. A fast wrong answer teaches you nothing."*

**Cut rule:** Problems 1 and 4 only, ~6 minutes, if the warm-up or Slide Block A overran. Do not cut Problem 4 — the simplification trap is the point.

---

## Slide Block B (26–33 min) — DELIVER SLIDES AS-IS

Covers: Product of two numbers = LCM × HCF (verified) → LCM/HCF of fractions → the harder worked fraction example.

**Beats to emphasise**

- **Beat 1 — Verify Product = LCM × HCF.** Check it against a number the class already trusts: 18 and 30, from Slide Block A. `18 × 30 = 540`. `LCM × HCF = 90 × 6 = 540`. ✅ Matches.
- **Beat 2 — LCM/HCF of fractions.** State the formulas: **LCM of fractions = LCM(numerators) / HCF(denominators)**; **HCF of fractions = HCF(numerators) / LCM(denominators)**. <!-- placement: inferred — reconstructed and verified against the deck's own worked answer below. Confirm against the live slide before teaching. -->
- **Beat 3 — Harder worked example.** Find LCM & HCF of `20/16`, `16/15`, `20/21`. The deck flags this exact sticking point: *"What is the HCF when there is no direct common factor in the given numbers?"* Work it on the board:
  - Numerators 20, 16, 20 → LCM = 80. Denominators 16, 15, 21 → HCF = 1. → **LCM of fractions = 80/1 = 80.**
  - Numerators 20, 16, 20 → HCF = 4. Denominators 16, 15, 21 → LCM = 1680. → **HCF of fractions = 4/1680 = 1/420.**

**Checkpoint (at 33 min)** — show hands:
> *"Why is the HCF of those three fractions `1/420` and not a whole number, when none of them looks like it shares an obvious common factor?"*
> **Answer:** Because HCF of fractions isn't found by inspection — it's `HCF(numerators) ÷ LCM(denominators)`. The formula still gives a clean answer even when nothing is "directly" common.

---

## ⚡ ALS Activity 2 — Student-Generated Task Design: Write the Question (33–39 min)

**ALS format:** Student-Generated Task Design — students write their own ratio-based LCM/HCF question using today's exact template, swap with a partner, and solve each other's question. Chosen as the closing activity because it's a generative check, not a recognition one: to build a valid question, a student has to actually understand where the traps are (the same simplification trap the board race just demonstrated), not just apply a formula to given numbers.

**Setup line:**
> *"You've solved four of these today. Now you write one. Pick a ratio, pick an HCF, decide what you're asking for — the LCM, or the two actual numbers. Give it to your partner. If their question doesn't have a clean answer, that's useful information too."*

Write the template on the board:
```
Ratio of two numbers = a : b
HCF of the two numbers = H
→ LCM = H × a × b
→ the two numbers themselves = H×a and H×b
```

**Timing:** 2 min write · swap · 2 min solve partner's question · cold-call 2 pairs to share.

**Model example if the room hesitates:** ratio `2:5`, `H=4` → numbers `8, 20`, LCM `= 4×2×5 = 40`.

**When it goes wrong**

| If… | Do this |
|---|---|
| A student picks a ratio not in simplest form (e.g. `4:14`) | Don't correct it — let their partner hit the exact trap from ALS Activity 1 and self-correct. |
| Nobody knows where to start | Model the `2:5, H=4` example above, live. |

**Debrief line:**
> *"Every question up here was built by someone in this room using the same template you now own. That's the actual test of whether you understood the shortcut — not solving it, building it."*

**Cut rule:** Skip the swap-and-solve step; have 2 students share their question and solve it as a class instead.

---

## Classroom Quiz (39–44 min) · Reserved — not yet available

No quiz bank exists yet for this Aptitude course (see Resources table). This 5-minute slot is reserved here, at the end of the session and right before the Exit Ticket, so the plan doesn't need restructuring once a quiz bank is added. Until then, run the dropped re-verify beat here instead — pick one more pair from the board race (e.g. 10 and 15) and have the class predict the product before revealing `LCM × HCF` — or fold the slot into Buffer and end early.

---

## Exit Ticket + Homework (44–48 min)

**Exit ticket** (~1 min) — on paper before anyone leaves:

> 1. In one line, what is a factor?
> 2. Find `a`, if the LCM & HCF of `(10, a)` is 30 & 5.

**Answers:** 1. A factor is a number that divides another exactly, leaving no remainder. 2. `a = 15`.

Scan responses on the way out. A wrong answer on Q2 is the signal to reopen the Product=LCM×HCF property at the start of Session 4.

**Homework**

| Task |
|---|
| Redo, cold, with no notes: Find LCM & HCF of `20/16`, `16/15`, `20/21`. Check against today's answer — LCM = 80, HCF = 1/420. |
| Redo, cold: the ratio 4:14, HCF 6 problem. Check that you simplified the ratio to 2:7 *before* multiplying — the answer is LCM = 84. |

> *"Both of these have already been solved on the board today. If you get a different answer at home, that's not bad luck — it means you skipped a step. Find which one."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Not sure what "prime factorisation" actually means as a method (rather than just a term) | The deck itself flags this directly | Working the 18 & 30 example fully on the board in Slide Block A, showing the factor tree |
| Using a ratio directly in the LCM shortcut without simplifying it (e.g. `6×4×14` instead of `6×2×7`) | The shortcut looks like a formula to plug numbers into, and 4:14 doesn't obviously look "unsimplified" | ALS Activity 1, Problem 4 |
| Assuming HCF of a set of fractions must be found by inspecting for an obvious shared factor, and concluding "there isn't one" | The deck flags this directly | Slide Block B, Beat 3 — the formula produces a clean `1/420` even though nothing looks "directly" common |
| Treating *multiple* and *factor* as unrelated ideas rather than the same division fact read in two directions | Definitions are taught on separate slides with no explicit link | The Hook — flipping `10÷2=5` against `10×2=20` on the same board, side by side |

---

## Instructor Notes

- **This plan is grounded entirely in a local pptx text-extraction** (`NIAT Basics and Properties.pptx`), not a platform export. No platform unit IDs, question IDs, or quiz/MCQ/coding pools exist yet for this topic.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is the Board Race (absorbs the missing-quiz slot, as in the original plan), Activity 2 is Student-Generated Task Design. The original Predict the Output re-verification activity is folded into a 2-minute quick-check beat inside Slide Block B instead of running as its own block.
- **Two numeric reconstructions were needed** because the text extraction split multi-digit numbers across separate text runs: `144` (LCM of 24, 36, 48) and `80` (LCM of the fraction set). Both independently re-derived and check out — confirm against the live slide before teaching.
- **The fraction LCM/HCF formulas are reconstructed**, not read directly off the slide — verified by recomputing the deck's own stated answer (LCM=80, HCF=1/420) for the (20/16, 16/15, 20/21) example, and they reproduce it exactly.
- **Pacing risk:** the fraction example in Slide Block B (Beat 3) has two separate LCM and HCF computations. Don't rush it — if the class doesn't cleanly get the 90/30/6 style examples in Block A, this one will lose them.
- **Warm-up Q5 (MSQ)** deliberately excludes 8 and 10 as "combination rules" even though a mathematically inclined student might argue 10 = 2×5. The deck only ever states 6 and 12 as explicit combinations; 8 and 10 are taught with their own independent rules.
