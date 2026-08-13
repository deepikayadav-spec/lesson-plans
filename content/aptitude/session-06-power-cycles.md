# Session 6 — Power Cycles

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Power Cycles (unit-digit patterns of powers) · **Prerequisite** Session 5 (Factors)
**Session type** Concept lecture. No classroom quiz bank, MCQ/coding-practice pool, or platform unit IDs exist yet — no quiz block for that reason. · **Format** 50-min recalibrated, 2 ALS activities

> **Sequencing flag (read before you teach this):** this deck's own "Recap" slide cites only *Number Systems* — unlike every other deck in this course, which cumulatively recaps everything covered so far. Power Cycles has been placed at position 6, immediately after Factors, by instructor judgment — see Instructor Notes for the full reasoning and the alternative sequencing option.

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT Power Cycles.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Recall the unit-digit power cycle for each base digit 2–9 (e.g. `2:{2,4,8,6}`, `7:{7,9,3,1}`, `5:{5}`). *(REMEMBERING)*
2. Explain why some digits (5, 6) have a power cycle of length 1 while others (2, 3, 7, 8) have length 4 and others (4, 9) have length 2. *(UNDERSTANDING)*
3. Apply the remainder-of-exponent-mod-cycle-length method to find the unit digit of a large power such as `X^Y`. *(APPLYING)*
4. Apply the method to expressions combining several power terms — sums and products of powers (e.g. `545^656 + 656^545`). *(APPLYING)*
5. Analyze a nested/tower power expression (e.g. `(888^644)^596`) by collapsing it to a single exponent via multiplication before reducing. *(ANALYZING)*
6. Determine the number of trailing zeros in a product of numbers or consecutive integers by counting factors of 2 and 5. *(APPLYING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 5, Factors (3–7 min) · ALS: Polling

5 questions on **Session 5 (Factors)**. Newly authored, grounded in that deck's real worked numbers. ~45 s each, project the distribution, never name individuals.

**Q1.** For `N = a^x × b^y × c^z` (prime factorised), the number of factors of `N` is:
`A` `x × y × z` · `B` `(x+1)(y+1)(z+1)` · `C` `(x−1)(y−1)(z−1)` · `D` `xyz + 1`
→ **B.** *Targets:* the core factors formula. *If >40% wrong:* rewrite the formula on the board now.

**Q2.** What is the sum of factors of 240?
`A` 504 · `B` 744 · `C` 360 · `D` 840
→ **B, 744.** *Targets:* recall of Session 5's first worked example.

**Q3.** The product of the factors of 60 was shown as `60^k`. What is `k`?
`A` 3 · `B` 4 · `C` 6 · `D` 8
→ **C, 6.** *Targets:* "product of factors = N^(number of factors / 2)".

**Q4.** How many factors does 1200 have?
`A` 24 · `B` 28 · `C` 30 · `D` 36
→ **C, 30.** *Targets:* applying the factor-count formula to a fresh number.

**Q5.** A number divided by 36 leaves remainder 19. What is the remainder when the *same* number is divided by 12?
`A` 5 · `B` 7 · `C` 3 · `D` 0
→ **B, 7.** *Targets:* since 12 divides 36, you can reduce the remainder directly (19 mod 12 = 7).

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Put this on the projector, exactly as the deck's own opening slide poses it, and say nothing else first:

> **Find the unit digit of `256489^248647662`?**
> `A` 9 · `B` 1 · `C` 3 · `D` Can't be determined

<!-- placement: inferred --> The source deck's text extraction lost the `^` between base and exponent. Reconstructed as base `256489`, exponent `248647662`, confirmed against the deck's marked answer B (unit digit 1). **Verify this reconstruction against the real slide before class.**

Say: *"Take twenty seconds. Shout me a guess — any digit 0 to 9."*

Let a few guesses land (they'll be scattered and mostly wrong — that's fine, don't correct any of them yet).

> *"Nobody can multiply that out by hand, and you don't need to. In the next ten minutes you'll learn a pattern that makes this a five-second answer. Hold onto your guess — we come back to this exact number before the block ends."*

---

## Slide Block A (10–19 min) — DELIVER SLIDES AS-IS

Covers: the power-cycle concept (blank cycle table → filled cycle table) and the first two applied questions.

**Beats to emphasise**

- **Beat 1 — build the pattern live, don't just reveal it.** Using the blank table, take digit 2 as an example: write out `2, 4, 8, 16, 32, 64, 128...` and underline only the unit digits — `2, 4, 8, 6, 2, 4, 8, 6...`. Let the class see the repeat happen before you show the filled table.
- **Beat 2 — reveal the full filled table** and group it by cycle length, not by digit order:
  - **length 1** → `5:{5}`, `6:{6}`; **length 2** → `4:{4,6}`, `9:{9,1}`; **length 4** → `2:{2,4,8,6}`, `3:{3,9,7,1}`, `7:{7,9,3,1}`, `8:{8,4,2,6}`.
  - Say explicitly: *"5 and 6 never change. 4 and 9 flip between two values depending on odd/even exponent. The rest cycle through four values — you need the exponent's remainder when divided by 4."*
  - **The remainder-0 trap:** if the exponent is exactly divisible by the cycle length, the remainder is 0 — but there is no "0th" entry. Remainder 0 maps to the **last** entry in the cycle, not the first. State this explicitly; it is the single most common error in this topic.
- **Beat 3 — apply it twice, live:**
  - `232^329` → last digit of base is 2, cycle `{2,4,8,6}`, `329 mod 4 = 1` → 1st entry → **2**.
  - `234^329` → last digit of base is 4, cycle `{4,6}`, `329` is odd → 1st entry → **4**.

**Checkpoint (at 19 min)** — return to the Hook:
> *"Back to `256489^248647662`. Last digit of the base?"* (9) *"Cycle for 9?"* (`{9,1}`) *"Is the exponent odd or even?"* (even) *"So?"*
> **Answer: 1 — option B.** Reveal it and let the earlier guesses stand or fall.

---

## ⚡ ALS Activity 1 — Rapid Fire Board Race (19–26 min)

**ALS format:** Board Race — two teams race to solve the same problem on the board, showing their remainder step and cycle-lookup step, first team to the correct final digit with both steps visible wins the round. Chosen right after Slide Block A because this is the first time students run the method start to finish themselves, with a small amount of competitive pressure, on the two problems the deck itself flags as the immediate next step.

**Setup line:**
> *"One runner from each team, board pen in hand. I show a problem, you race to the answer — but you don't just shout the digit, you write the remainder step AND the cycle lookup. First team with both steps correct wins the round. Losing team explains where they went wrong."*

**Problem 1** — Find the unit's place value of `323^446`?
`A` 3 · `B` 9 · `C` 7 · `D` 1

**Problem 2** — Find the right-most value of the expression `3367^736535`?
`A` 7 · `B` 9 · `C` 3 · `D` 1

**Answers**

| # | Base's last digit | Cycle | Exponent mod (cycle length) | Answer |
|---|---|---|---|---|
| 1 | 3 | `{3,9,7,1}` | `446 mod 4 = 2` → 2nd entry | **B) 9** |
| 2 | 7 | `{7,9,3,1}` | `736535 mod 4`: last two digits `35 mod 4 = 3` → 3rd entry | **C) 3** |

**How it surfaces:** for Problem 2, watch whether a team tries to divide the whole 6-digit exponent by 4 the long way instead of noticing only the last two digits matter for mod 4.

**Debrief line:**
> *"Notice Problem 2's exponent had six digits. Didn't matter. You only ever need two things: the base's last digit, and the exponent's remainder. Everything else is noise."*

**Cut rule:** If running long, run Problem 1 as the race and Problem 2 as a 60-second individual "everyone writes it, I cold-call one" instead of a second team race.

---

## Slide Block B (26–38 min) — DELIVER SLIDES AS-IS

Covers: the two harder patterns the deck introduces after "Quiz Time" — a **sum** of two power terms, a **nested (tower) power**, and trailing zeros.

**Beats to emphasise**

- **Beat 1 — sum of two powers.** `Find the last digit of (545^656 + 656^545)?` — reduce *each term separately* to its last digit, then add: base 545 ends in 5 → any power of a number ending in 5 ends in 5 → `545^656` last digit **5**. Base 656 ends in 6 → any power ends in 6 → `656^545` last digit **6**. `5 + 6 = 11` → last digit **1**. **Answer: A) 1.** Say explicitly: *"You never need the actual sum. Just the last digits of the last digits."*
- **Beat 2 — nested power.** `Find the last digit of ((888^644)^596)?` — the key move is collapsing the tower: `(888^644)^596 = 888^(644 × 596)`, **multiply the exponents, don't try to evaluate the inner power first.** Base 888 ends in 8, cycle `{8,4,2,6}`. `644 mod 4 = 0`, so the *entire* product `644 × 596` is divisible by 4 regardless of what 596 is. Remainder 0 → last entry in the cycle → **6**. **Answer: D) 6.**
- Flag explicitly: *"Two different combining rules today — sum of powers: reduce then add. Nested power: multiply the exponents first, then reduce once."*
- **Beat 3 — trailing zeros, a separate sub-skill (not unit-digit cycles).** *"Find the number of zeros in `57 × 45 × 30 × 12`?"* Trailing zeros come from *pairs* of 2s and 5s, not from any digit that "looks like a zero." Factors of 5 available: `45` contributes one, `30` contributes one → 2 fives. Factors of 2: `30` contributes one, `12` contributes two → 3 twos. Zeros = `min(2,3)` = **2**.

**Checkpoint (at 38 min)** — cold-call:
> *"Tell me the one move that makes a nested power like `(a^b)^c` solvable in one step."*
> **Answer:** Multiply the exponents — `(a^b)^c = a^(b×c)` — then apply the cycle to that single combined exponent.

---

## ⚡ ALS Activity 2 — Predict the Output (38–45 min)

**ALS format:** Staged Prediction — one problem revealed in three stages, students committing out loud before each reveal. Chosen as the closing activity because a *product* of two power terms looks identical to Slide Block B's sum on the surface, and mixing up "add the reduced digits" with "multiply the reduced digits" is the exact next mistake waiting to happen — this catches it in the room instead of on a test.

**Setup line:**
> *"Full problem's on screen. I'm not asking for the final answer yet — I'm asking for one piece at a time. Commit to each piece before I reveal it. This is a product, not a sum — that word matters."*

**Find the units digit for the following expression: `(52^14) × (97^19)`**
`A` 2 · `B` 1 · `C` 5 · `D` 4

**Timing:** predict first term's last digit → reveal → predict second term's last digit → reveal → predict the combined final digit → reveal full working.

**Answers**

| Term | Base's last digit | Cycle | Exponent mod (cycle length) | Term's last digit |
|---|---|---|---|---|
| `52^14` | 2 | `{2,4,8,6}` | `14 mod 4 = 2` → 2nd entry | 4 |
| `97^19` | 7 | `{7,9,3,1}` | `19 mod 4 = 3` → 3rd entry | 3 |

Combine by **multiplying**, not adding: `4 × 3 = 12` → last digit **2**. **Answer: A) 2.**

**When it goes wrong**

| If… | Do this |
|---|---|
| Students add the two reduced digits (4 + 3 = 7) instead of multiplying | Point back at the original expression — it has an `×`, not a `+`. Contrast with Slide Block B's sum problem side by side. |
| Someone tries to reduce `14 × 19` first, as if it were a nested power | Stop and ask: *"Is one exponent sitting on top of the other, or are these two separate power terms being multiplied?"* |

**Debrief line:**
> *"Sum, product, or tower — three different combining rules, and the operator symbol in the original question tells you which one every time."*

**Cut rule:** If running short, skip the three-stage reveal and just do one combined prediction, then the full board working.

---

## Exit Ticket + Homework (45–48 min)

**Exit ticket** (~1 min) — on paper before anyone leaves:

> Find the unit's place value of `323^446`, and show your remainder step.
> **Answer:** base ends in 3, cycle `{3,9,7,1}`, `446 mod 4 = 2` → 2nd entry → **9**. (Same problem as ALS Activity 1, Problem 1 — this checks whether it actually stuck.)

Scan responses on the way out. If the remainder-mod-cycle-length step is missing or wrong on more than a few tickets, open Session 7 with a 3-minute recap of that step specifically.

**Homework**

> Re-attempt, from memory, all the "Quiz Time" problems from today's deck — the two from ALS Activity 1, the sum and nested power from Slide Block B, the trailing-zeros problem, and ALS Activity 2's product of powers. Write out the cycle you used for each base. Bring your working to the next session.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock and want an extension instead of ending early, run the harder trailing-zeros extension below:

**Optional closer:** *"How many minimum consecutive numbers should be multiplied starting from 20, so that the result has 3 zeros at the end?"* `A` 5 · `B` 6 · `C` 10 · `D` 11
Starting at 20: `20 × 21 × 22 × 23 × 24 × 25` (6 numbers). Fives: `20` gives one, `25` gives two → 3 fives. Twos: `20` gives two, `22` gives one, `24` gives three → 6 twos. `min(3,6)=3` zeros, achieved exactly at 6 numbers. **Answer: B) 6.** Never required — the schedule doesn't depend on it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Remainder 0 (exponent divisible by cycle length) means "no digit" or defaults to the 1st cycle entry | Everywhere else in maths, remainder 0 feels like "nothing left" | Slide Block A's explicit remainder-0 rule: it maps to the **last** entry, not the first |
| Sum of two powers requires computing the actual (huge) sum | Deck literally shows this as a "summation" — looks like real addition is needed | Slide Block B Beat 1: reduce each term to its last digit *first*, then add just those two digits |
| A nested power `(a^b)^c` should be evaluated by reducing `a^b` to a small number first, then raising that | Order of operations, read left to right the way they'd literally compute it | Slide Block B Beat 2: show `(a^b)^c = a^(b×c)` — multiply exponents once, reduce once |
| Trailing zeros come from any number that "looks like it has a zero in it" or ends in 0 | Surface-level pattern matching on the digit 0 | Slide Block B Beat 3: zeros come specifically from *pairing* a factor of 2 with a factor of 5 |
| A product of two power terms is combined the same way as a sum (add the reduced digits) | Both look like "two power terms next to an operator" | ALS Activity 2 — the operator symbol (`×` vs `+`) decides multiply vs. add |

---

## Instructor Notes

- **Sequencing judgment call:** this deck's Recap slide references only *Number Systems*, not the cumulative list every other deck uses. It was slotted at position 6 (right after Factors) so it feeds directly into a later consolidation deck. **If your actual teaching order puts Power Cycles right after Session 2 (Number Systems) instead**, swap the warm-up poll accordingly. <!-- placement: inferred -->
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is the Board Race (single-power drilling), Activity 2 is Staged Prediction (product-vs-sum confusion). The original Think-Pair-Share trailing-zeros activity is folded into Slide Block B (Problem 1 only) with its harder consecutive-numbers extension demoted to an optional buffer-only closer.
- **The Hook's exponent is a reconstruction from a text-extraction artifact** — confirmed against the deck's marked answer. **Verify against the actual slide before class.** <!-- placement: inferred -->
- **No classroom quiz, MCQ pool, or coding-practice bank exists for this topic.** This plan is grounded entirely in local text extractions of `NIAT Power Cycles.pptx` and `NIAT Factors.pptx`.
- **Slide Block B carries the two hardest new ideas of the session** (sum-reduction and exponent-multiplication for nested powers) plus trailing zeros. If you overrun, use the cut rules in the two ALS activities first — never trim Slide Block B itself.
- **Have the cycle table (2 through 9) already written on a spare board or slide** before class starts — students will refer back to it constantly.
