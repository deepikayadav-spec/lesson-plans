# Session 6 — Power Cycles

**Duration** 60 min · **Topic** Power Cycles (unit-digit patterns of powers) · **Prerequisite** Session 5 (Factors)
**Session type** Concept lecture. No classroom quiz bank, MCQ/coding-practice pool, or platform unit IDs exist yet for this topic — everything below is grounded in the local source deck only.

> **Sequencing flag (read before you teach this):** this deck's own "Recap" slide cites only *Number Systems* — unlike every other deck in this course, which cumulatively recaps everything covered so far (Basics and Properties, Multiples, Factors...). Power Cycles has been placed at position 6, immediately after Factors, by instructor judgment: a later consolidation deck ("Company-Specific MCQs — Numbers") mixes power-cycle reasoning with factor/divisibility reasoning and sits right after this block, so teaching Factors → Power Cycles back-to-back sets that deck up well. **An equally defensible alternative is teaching Power Cycles immediately after Session 2 (Number Systems), before Basics and Properties / Multiples / Factors** — that's the order the deck's own Recap slide implies. If your actual delivery order differs, resequence the warm-up poll accordingly (it currently drills Session 5 / Factors). See Instructor Notes.

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

## Warm-Up Poll — Retrieval Practice on Session 5, Factors (0–7 min)

7 questions on **Session 5 (Factors)**. Newly authored, grounded in that deck's real worked numbers. ~45 s each, project the distribution, never name individuals.

**Q1.** For `N = a^x × b^y × c^z` (prime factorised), the number of factors of `N` is:
`A` `x × y × z` · `B` `(x+1)(y+1)(z+1)` · `C` `(x−1)(y−1)(z−1)` · `D` `xyz + 1`
→ **B.** *Targets:* the core factors formula from Session 5's opening slide. *If >40% wrong:* rewrite the formula on the board now — everything else this session depends on it.

**Q2.** What is the sum of factors of 240?
`A` 504 · `B` 744 · `C` 360 · `D` 840
→ **B, 744.** *Targets:* recall of Session 5's first worked example.

**Q3.** The product of the factors of 60 was shown as `60^k`. What is `k`?
`A` 3 · `B` 4 · `C` 6 · `D` 8
→ **C, 6.** *Targets:* "product of factors = N^(number of factors / 2)" — recall that 60 has 12 factors.

**Q4.** How many factors does 1200 have?
`A` 24 · `B` 28 · `C` 30 · `D` 36
→ **C, 30.** *Targets:* applying the factor-count formula to a fresh number.

**Q5.** A number divided by 36 leaves remainder 19. What is the remainder when the *same* number is divided by 12?
`A` 5 · `B` 7 · `C` 3 · `D` 0
→ **B, 7.** *Targets:* since 12 divides 36, you can reduce the remainder directly (19 mod 12 = 7) instead of restarting the division. *Misconception:* students re-derive from scratch instead of seeing that 12 | 36.

**Q6.** To find the greatest number that divides 30, 39 and 57 leaving the **same** remainder in each case, you take the HCF of:
`A` the numbers themselves · `B` the differences between the numbers · `C` the sum of the numbers · `D` the remainders
→ **B, the differences.** *Targets:* distinguishing this ("same remainder", answer 9) from the "given specific remainders" case (subtract the remainders first, answer 12) — two different Session 5 problems students commonly conflate.

**Q7.** The product of two numbers is 6300 and their HCF is 15. How many such pairs of numbers exist?
`A` 1 · `B` 2 · `C` 3 · `D` 4
→ **B, 2.** *Targets:* co-prime-pair reasoning — the two numbers must be `15 × (co-prime pair)` whose product is `6300/15² = 28`, and 28 has 2 co-prime factor pairs. Last question, analysis-level — expect the lowest score here.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–10 min)

Put this on the projector, exactly as the deck's own opening slide poses it, and say nothing else first:

> **Find the unit digit of `256489^248647662`?**
> `A` 9 · `B` 1 · `C` 3 · `D` Can't be determined

<!-- placement: inferred --> The source deck's text extraction lost the `^` between base and exponent and ran the two numbers together as "(256489) 248647662". Reconstructed as base `256489`, exponent `248647662` — the same base-in-parentheses / exponent-as-separate-number pattern the deck uses on every later slide (e.g. slide 10's `3367 / 736535`), just with deliberately huge, scary-looking numbers because this is the *opening hook*, before any technique has been taught. This reading is confirmed against the deck's marked answer: `256489` ends in 9, `248647662` is even, and the deck's own cycle for 9 (taught two slides later) is `{9, 1}` — odd exponent → 9, even exponent → 1. Even exponent here gives **1**, matching the deck's marked answer **B) 1**. **Verify this reconstruction against the real slide before class.**

Say: *"Take twenty seconds. Shout me a guess — any digit 0 to 9."*

Let a few guesses land (they'll be scattered and mostly wrong — that's fine, don't correct any of them yet).

> *"Nobody can multiply that out by hand, and you don't need to. In the next twelve minutes you'll learn a pattern that makes this a five-second answer. Hold onto your guess — we come back to this exact number before the block ends."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

Covers: the power-cycle concept (blank cycle table → filled cycle table) and the first two applied questions.

**Beats to emphasise**

- **Beat 1 — build the pattern live, don't just reveal it.** Using the blank table, take digit 2 as an example: write out `2, 4, 8, 16, 32, 64, 128...` and underline only the unit digits — `2, 4, 8, 6, 2, 4, 8, 6...`. Let the class see the repeat happen before you show the filled table.
- **Beat 2 — reveal the full filled table** and group it by cycle length, not by digit order — this is the structural insight:
  - Length 1: `4:{4,6}`... *(correction — see table below)* — group as: **length 1** → `5:{5}`, `6:{6}`; **length 2** → `4:{4,6}`, `9:{9,1}`; **length 4** → `2:{2,4,8,6}`, `3:{3,9,7,1}`, `7:{7,9,3,1}`, `8:{8,4,2,6}`.
  - Say explicitly: *"5 and 6 never change. 4 and 9 flip between two values depending on odd/even exponent. The rest cycle through four values — you need the exponent's remainder when divided by 4."*
  - **The remainder-0 trap:** if the exponent is exactly divisible by the cycle length, the remainder is 0 — but there is no "0th" entry. Remainder 0 maps to the **last** entry in the cycle, not the first. State this explicitly; it is the single most common error in this topic.
- **Beat 3 — apply it twice, live:**
  - `232^329` → last digit of base is 2, cycle `{2,4,8,6}`, `329 mod 4 = 1` → 1st entry → **2**.
  - `234^329` → last digit of base is 4, cycle `{4,6}`, `329` is odd → 1st entry → **4**.

**Checkpoint (at 22 min)** — return to the Hook:
> *"Back to `256489^248647662`. Last digit of the base?"* (9) *"Cycle for 9?"* (`{9,1}`) *"Is the exponent odd or even?"* (even) *"So?"*
> **Answer: 1 — option B.** Reveal it and let the earlier guesses stand or fall.

---

## ⚡ Activity 1 — Rapid Fire Board Race (22–29 min)

### What this activity is

Two teams race to solve the same problem on the board, showing their remainder step and their cycle-lookup step — first team to the correct final digit with both steps visible wins the round. Two rounds, one per problem, straight from the deck's own "Quiz Time" set that immediately follows the cycle table.

### Why it's here

Slide Block A taught the method through your worked examples. This activity is the first time *students* run the method start to finish, under a small amount of competitive pressure, with the two problems the deck itself flags as the next step ("Quiz Time").

### Before class

Split the board into two halves. Have both problems ready to reveal one at a time — do not show problem 2 until round 1 is scored.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Split into two teams, explain scoring (correct final digit + visible remainder step = win) | Listen, pick a runner |
| 0:30–3:30 | Reveal Problem 1, run the race | One runner per team writes on the board |
| 3:30–4:00 | Score round 1, reveal answer | Watch |
| 4:00–6:30 | Reveal Problem 2, run the race | New runner per team writes on the board |
| 6:30–7:00 | Score round 2, debrief | Listen |

### Say this

> *"One runner from each team, board pen in hand. I show a problem, you race to the answer — but you don't just shout the digit, you write the remainder step AND the cycle lookup. First team with both steps correct wins the round. Losing team explains where they went wrong."*

### The problems

**Problem 1** — Find the unit's place value of `323^446`?
`A` 3 · `B` 9 · `C` 7 · `D` 1

**Problem 2** — Find the right-most value of the expression `3367^736535`?
`A` 7 · `B` 9 · `C` 3 · `D` 1

### Answers

| # | Base's last digit | Cycle | Exponent mod (cycle length) | Answer |
|---|---|---|---|---|
| 1 | 3 | `{3,9,7,1}` | `446 mod 4 = 2` → 2nd entry | **B) 9** |
| 2 | 7 | `{7,9,3,1}` | `736535 mod 4`: last two digits `35 mod 4 = 3` → 3rd entry | **C) 3** |

**How it surfaces:** for Problem 2, watch whether a team tries to divide the whole 6-digit exponent by 4 the long way instead of noticing only the last two digits matter for mod 4. Call this out live if it happens — it's a genuine time-saver, not a shortcut to be suspicious of.

**Debrief line:**
> *"Notice Problem 2's exponent had six digits. Didn't matter. You only ever need two things: the base's last digit, and the exponent's remainder. Everything else is noise."*

**Cut rule:** If running long, run Problem 1 as the race and Problem 2 as a 60-second individual "everyone writes it, I cold-call one" instead of a second team race.

> **Classroom Quiz:** not yet available — add once question bank exists for this topic. Time reallocated into Slide Block B and Activities 2–3 below; the 60-minute timeline has no gap where the quiz would have sat.

---

## Slide Block B (29–40 min) — DELIVER SLIDES AS-IS

Covers: the two harder patterns the deck introduces after "Quiz Time" — a **sum** of two power terms, and a **nested (tower) power**.

**Beats to emphasise**

- **Beat 1 — sum of two powers.** `Find the last digit of (545^656 + 656^545)?` — reduce *each term separately* to its last digit, then add: base 545 ends in 5 → any power of a number ending in 5 ends in 5 → `545^656` last digit **5**. Base 656 ends in 6 → any power ends in 6 → `656^545` last digit **6**. `5 + 6 = 11` → last digit **1**. **Answer: A) 1.** Say explicitly: *"You never need the actual sum. Just the last digits of the last digits."*
- **Beat 2 — nested power.** `Find the last digit of ((888^644)^596)?` — the key move is collapsing the tower: `(888^644)^596 = 888^(644 × 596)`, **multiply the exponents, don't try to evaluate the inner power first.** Base 888 ends in 8, cycle `{8,4,2,6}`. `644 × 596` — you don't even need the full product: `644 mod 4 = 0`, so the *entire* product `644 × 596` is divisible by 4 regardless of what 596 is. Remainder 0 → last entry in the cycle → **6**. **Answer: D) 6.**
- Flag explicitly: *"Two different combining rules today — sum of powers: reduce then add. Nested power: multiply the exponents first, then reduce once."* Students conflate these; say the distinction out loud twice.

**Checkpoint (at 40 min)** — cold-call:
> *"Tell me the one move that makes a nested power like `(a^b)^c` solvable in one step."*
> **Answer:** Multiply the exponents — `(a^b)^c = a^(b×c)` — then apply the cycle to that single combined exponent.

---

## ⚡ Activity 2 — Predict the Output (40–47 min)

### What this activity is

One meaty problem, revealed in stages. Before each stage's reveal, every student commits out loud (or via poll) to a prediction. This is a *product* of two separate power terms — the deck's next "Quiz Time" problem — and it forces students to do two independent cycle-lookups before combining them, which is a different failure mode than the sum (Slide Block B) or the nested tower.

### Why it's here

Sum-of-powers and nested-powers were just taught. A *product* of two powers looks identical to the sum on the surface, and mixing up "add the reduced digits" with "multiply the reduced digits" is the exact next mistake waiting to happen. This activity catches it in the room instead of on a test.

### Before class

Have the problem ready, but reveal it in three stages: (1) the full expression, (2) after the first term is reduced, (3) after the second term is reduced. Cover the rest with a slide build or your hand.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, reveal full expression | Listen |
| 0:30–1:30 | Ask for a prediction of the *first* term's last digit only | Commit out loud / show fingers |
| 1:30–2:30 | Reveal first term's answer, ask for the *second* term's last digit | Commit again |
| 2:30–3:30 | Reveal second term's answer, ask for the **combined** final digit | Commit again |
| 3:30–5:30 | Walk the full working on the board | Watch, correct their own prediction |
| 5:30–7:00 | Debrief | Listen |

### Say this

> *"Full problem's on screen. I'm not asking for the final answer yet — I'm asking for one piece at a time. Commit to each piece before I reveal it. This is a product, not a sum — that word matters."*

### The problem

**Find the units digit for the following expression: `(52^14) × (97^19)`**
`A` 2 · `B` 1 · `C` 5 · `D` 4

### Answers

| Term | Base's last digit | Cycle | Exponent mod (cycle length) | Term's last digit |
|---|---|---|---|---|
| `52^14` | 2 | `{2,4,8,6}` | `14 mod 4 = 2` → 2nd entry | 4 |
| `97^19` | 7 | `{7,9,3,1}` | `19 mod 4 = 3` → 3rd entry | 3 |

Combine by **multiplying**, not adding: `4 × 3 = 12` → last digit **2**. **Answer: A) 2.**

**When it goes wrong**

| If… | Do this |
|---|---|
| Students add the two reduced digits (4 + 3 = 7) instead of multiplying | Point back at the original expression — it has an `×`, not a `+`. Contrast with Slide Block B's sum problem side by side. |
| Someone tries to reduce `14 × 19` first, as if it were a nested power | Stop and ask: *"Is one exponent sitting on top of the other, or are these two separate power terms being multiplied?"* This is a genuinely useful confusion to surface. |

**Common instructor mistake:** revealing the full worked solution before taking the three staged predictions. The staging is the entire point — it isolates exactly where the multiply-vs-add slip happens.

**Cut rule:** If running short, skip the three-stage reveal and just do one combined prediction, then the full board working.

---

## ⚡ Activity 3 — Think–Pair–Share (47–54 min)

### What this activity is

Pairs work through two related trailing-zero problems together before any answer is given, then share out. Both problems are the deck's own closing "Quiz Time" pair, and they build on each other — the second only makes sense once the first has landed.

### Why it's here

Trailing zeros is a distinct sub-skill from the rest of the session (it's about factors of 2 and 5, not unit-digit cycles), and the deck itself flags two sticking points on these exact slides: *"When do we get zero in the last?"* and *"What are consecutive numbers?"* — both are genuine, named confusions worth pairing on rather than lecturing through.

### Before class

Have both problems ready. Do not reveal Problem 2 until Problem 1 is fully debriefed — Problem 2 depends on the "count factors of 2 and 5" habit Problem 1 builds.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, reveal Problem 1 | Listen |
| 0:30–2:30 | Circulate, prompt pairs | Discuss in pairs, no individual answers yet |
| 2:30–3:30 | Take answers from 2–3 pairs, debrief Problem 1 | Share reasoning |
| 3:30–4:00 | Reveal Problem 2 | Listen |
| 4:00–5:30 | Circulate | Discuss in pairs |
| 5:30–7:00 | Take answers, debrief | Share reasoning |

### Say this

> *"Turn to your partner. Trailing zeros don't come from any factor ending in 0 — they come specifically from *pairs* of 2s and 5s hiding inside the numbers. Find how many of each are available, then tell me the smaller count. Ninety seconds, then I want an answer from two pairs."*

### The problems

**Problem 1** — Find the number of zeros in `57 × 45 × 30 × 12`?
`A` 2 · `B` 3 · `C` 4 · `D` 1

**Problem 2** — How many minimum consecutive numbers should be multiplied starting from 20, so that the result has 3 zeros at the end?
`A` 5 · `B` 6 · `C` 10 · `D` 11

### Answers

**Problem 1:** factors of 5 available — `45` contributes one, `30` contributes one → 2 fives. Factors of 2 available — `30` contributes one, `12` contributes two → 3 twos. `57` contributes neither. Trailing zeros = `min(2, 3)` = **2 — Answer A**.

**Problem 2:** starting at 20 and multiplying consecutively — `20 × 21 × 22 × 23 × 24 × 25` (6 numbers). Fives: `20` gives one, `25` gives two → 3 fives. Twos: `20` gives two, `22` gives one, `24` gives three → 6 twos. `min(3, 6) = 3` zeros, achieved exactly at 6 numbers — with only 5 numbers (20–24), there's no 25, so only 1 five is available, which isn't enough. **Answer B) 6.**

**When it goes wrong**

| If… | Do this |
|---|---|
| A pair counts every trailing-0-looking number as "a zero" (e.g. treats `30` itself as automatically "one zero") | Redirect: *"30 isn't a zero. 30 is `2 × 3 × 5`. It's the 5 inside it we're counting."* |
| Room is unclear what "consecutive numbers" means (deck's own flagged sticking point) | Clarify explicitly: *"20, 21, 22, 23... each one exactly one more than the last, no skipping, starting at 20."* Write the run out on the board. |
| A pair stops at 5 numbers for Problem 2 because "that's the minimum guess" | Ask them to actually count the fives in the 20–24 range only — they'll find just 1, and see for themselves it's short. |

**Common instructor mistake:** revealing Problem 2 before Problem 1 is fully debriefed. Problem 2 only works as an extension if the "count factors of 2 and 5 separately, take the minimum" habit is already fresh.

**Cut rule:** If running short, do Problem 1 as pairs and Problem 2 as a full-class cold-call instead of a second paired discussion.

---

## Exit Ticket + Homework (54–60 min)

**Exit ticket** — on paper before anyone leaves:

> Find the unit's place value of `323^446`, and show your remainder step.
> **Answer:** base ends in 3, cycle `{3,9,7,1}`, `446 mod 4 = 2` → 2nd entry → **9**. (Same problem as Activity 1, Problem 1 — this checks whether it actually stuck, not whether they can memorise a new one.)

Scan responses on the way out. If the remainder-mod-cycle-length step is missing or wrong on more than a few tickets, open Session 7 with a 3-minute recap of that step specifically.

**Homework**

> Re-attempt, from memory, all 7 "Quiz Time" problems from today's deck — the two under Activity 1 (`323^446`, `3367^736535`), the sum and the nested power from Slide Block B (`545^656 + 656^545`, `((888^644)^596)`), and the three from Activities 2–3 (`(52^14) × (97^19)`, the zeros in `57 × 45 × 30 × 12`, and the consecutive-numbers problem). Write out the cycle you used for each base. Bring your working to the next session — no answer key needed, you already have every answer from today's board work.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Remainder 0 (exponent divisible by cycle length) means "no digit" or defaults to the 1st cycle entry | Everywhere else in maths, remainder 0 feels like "nothing left" | Slide Block A's explicit remainder-0 rule: it maps to the **last** entry, not the first — walk a concrete case (e.g. exponent that's a clean multiple of 4) on the board |
| Sum of two powers requires computing the actual (huge) sum | Deck literally shows this as a "summation" — looks like real addition is needed | Slide Block B Beat 1: reduce each term to its last digit *first*, then add just those two digits |
| A nested power `(a^b)^c` should be evaluated by reducing `a^b` to a small number first, then raising that | Order of operations, read left to right the way they'd literally compute it | Slide Block B Beat 2: show `(a^b)^c = a^(b×c)` — multiply exponents once, reduce once |
| Trailing zeros come from any number that "looks like it has a zero in it" or ends in 0 | Surface-level pattern matching on the digit 0 | Activity 3 Problem 1: zeros come specifically from *pairing* a factor of 2 with a factor of 5 — count each separately |
| "Consecutive numbers" is vague / miscounting how many multiples of 5 appear in a run | Deck's own flagged sticking point on this exact slide ("What are consecutive numbers?") | Activity 3 Problem 2: write the actual run (20, 21, 22, 23, 24, 25) on the board and count factors number-by-number |

---

## Instructor Notes

- **Sequencing judgment call — flagged above and repeated here:** this deck's Recap slide references only *Number Systems*, not the cumulative list (Basics and Properties / Multiples / Factors) every other deck in this course uses. It was slotted at position 6 (right after Factors) so it feeds directly into the later "Company-Specific MCQs — Numbers" consolidation deck, which blends power-cycle and factor/divisibility reasoning. **If your actual teaching order puts Power Cycles right after Session 2 (Number Systems) instead**, swap the warm-up poll to drill Number Systems content rather than Factors, and drop the Factors-specific framing from this plan. <!-- placement: inferred -->
- **The Hook's exponent (`256489^248647662`) is a reconstruction from a text-extraction artifact** — the deck's raw extracted text ran the base and exponent together as "(256489) 248647662" with no visible `^`. The split used here (base `256489`, exponent `248647662`) matches the deck's own base-in-parens / exponent-as-number pattern used on every later slide, and is independently confirmed by working backward from the deck's marked answer (B, unit digit 1) through the cycle for 9 taught two slides later. **Verify this against the actual slide before class** — if the real slide shows different digit groupings, the teaching point (odd/even exponent on a base ending in 9) still holds, only the specific digits would need updating. <!-- placement: inferred -->
- **All other power problems in this plan (slides behind Activities 1–3 and Slide Block B) were already cleanly separated by the extraction** — base in one token, exponent in the next — and every one of them was independently recomputed here and checks out exactly against the deck's own marked answer key. The only edit made was adding back the `^` symbol for readability. Confidence on these is high; still worth a visual spot-check against the real slides.
- **The mapping of specific slides to Activities 1–3 is an inferred grouping**, not something stated explicitly in the extracted text beyond the deck's own "Quiz Time" divider slides (which appear twice, with no content of their own). The problems immediately preceding and following each divider were grouped into activities by content type (single power → Activity 1; sum/nested power → Slide Block B; product of powers → Activity 2; trailing zeros → Activity 3). If the real deck's slide order differs from the extraction order, re-sequence the activities but keep the problems as given — none were invented. <!-- placement: inferred -->
- **No classroom quiz, MCQ pool, or coding-practice bank exists for this topic.** This plan is grounded entirely in a local text extraction of `NIAT Power Cycles.pptx` (and, for the warm-up poll, `NIAT Factors.txt`). No platform unit IDs were invented anywhere in this document — every "not yet available" line is deliberate.
- **The 60 minutes is tight with three activities.** If you overrun, use the cut rules in Activities 1 and 3 first (both have a built-in shorter path) before touching Slide Block B, which carries the two hardest new ideas of the session (sum-reduction and exponent-multiplication for nested powers).
- **Have the cycle table (2 through 9) already written on a spare board or slide** before class starts — students will refer back to it constantly through Activities 1–3, and re-deriving it each time burns minutes you don't have.
