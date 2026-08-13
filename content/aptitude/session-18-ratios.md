# Session 18 — Ratios

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Ratios · **Prerequisite** Session 17 (Compound Interest)
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet — a 5-min quiz slot is reserved but empty for that reason. · **Format** 50-min recalibrated, 2 ALS activities

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT_Ratios.pptx` |
| Classroom Quiz | not yet available — 5-min slot reserved at end of session, add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define a ratio (`a:b = a/b`) and explain why a ratio carries no units of its own. *(REMEMBERING)*
2. Combine two ratios that share a common term into a single three-term ratio by equalising the shared term. *(UNDERSTANDING)*
3. Apply ratio division to split a quantity into parts — including parts defined by fractions, or by an "equal quotient" condition. *(APPLYING)*
4. Apply ratio reasoning to mixed-denomination and mixture word problems, converting every quantity to a common unit before writing the equation. *(APPLYING)*
5. Analyse multi-container mixture problems by breaking each container into its own ratio components before recombining them. *(ANALYZING)*
6. Set up and solve an algebraic equation from a word problem where a ratio changes under a stated condition. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

5 questions on **Session 17 (Compound Interest)**. Newly authored from that deck's real figures. ~45 s each, project the distribution, never name individuals.

**Q1.** In the compound interest formula, what does "P" stand for?
`A` Profit · `B` Percentage · `C` Principal · `D` Period
→ **C.**

**Q2.** For a sum of Rs.1000 at 10% p.a., how do Simple Interest and Compound Interest compare in **Year 1 only**?
`A` They're equal (both Rs.100) · `B` CI is Rs.10 more · `C` CI is Rs.100 more · `D` Cannot say
→ **A.** *Targets:* SI and CI only diverge from Year 2 onward.

**Q3.** Which compounding frequency gives the **highest** amount for the same nominal rate?
`A` Compounded Per Annum · `B` Compounded Semi-Annually · `C` Compounded Quarterly · `D` All three are equal
→ **C.**

**Q4.** A man invests Rs.6,000 for 2 years, compounded annually. At the end of Year 1 it amounts to Rs.7,200. What rate of interest is that?
`A` 10% · `B` 15% · `C` 20% · `D` 25%
→ **C.** *Targets:* working backwards from an amount to a rate — the same skill today's ratio problems lean on.

**Q5.** *(MSQ — select all that apply)* Based on the Rs.1,000-at-10%-for-3-years example from last session, which statements are true?
`A` Year 1 SI and CI are equal · `B` Total SI over 3 years = Rs.300 · `C` Total CI over 3 years = Rs.331 · `D` CI is always less than SI
→ **A, B, C.** *Targets:* D is the trap — CI overtakes SI from Year 2 onward.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–9 min)

Write on the board: **"This class has 40 students."** Nothing else yet.

Say: *"Last session you spent an hour chasing rupees and paise to two decimal places. Forget money for a second."*

Add to the board: **"Boys : Girls = 2 : 3."**

Ask: *"Without any more information than that — how many boys and how many girls are in a class of 40?"*

Let them work it out out loud (2x + 3x = 5x = 40 → x = 8 → 16 boys, 24 girls).

Say: *"That's it. That's the entire idea for today. Notice what I never told you — I never said what 'x' was. I never gave you a unit. A ratio compares two things of the same kind, and by itself it carries no unit at all. `2:3` could be 16-and-24, or 200-and-300, or 2-and-3. The ratio doesn't care. Today we learn what a ratio actually is, and then we spend the hour breaking real quantities apart using it."*

---

## Slide Block A (9–18 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — the deck itself has no timing metadata; this block covers the definition slide plus the first two worked examples that follow it -->

Covers: the definition of a ratio → combining two ratios that share a term (`x:y` and `y:z`) → dividing a quantity directly in a given ratio.

**Beats to emphasise**

- **A ratio has no units.** `a:b = a/b`. In the Boys:Girls = 2:3 example, total boys = `2x`, total girls = `3x`, and `x` can be anything — the ratio only fixes the *proportion*.
- **Combining two ratios that share a term.** If `x:y = 2:3` and `y:z = 5:7`, you cannot just line them up — the `y` in each ratio is a different scale. Scale each ratio so the shared term (`y`) matches: `x:y` → `10:15`; `y:z` → `15:21`. Now `x:y:z = 10:15:21`.
- **Direct division in a given ratio.** Two quantities in ratio `3:4`; if the first is Rs.810, one "part" is `810 ÷ 3 = 270`, so the second is `4 × 270 = 1080`. This single per-part move underlies almost every problem today.

**Checkpoint (at 18 min)** — 10 s silent think, cold-call:
> *"What's the actual trick for combining `x:y = 2:3` with `y:z = 5:7` into one ratio?"*
> **Answer:** Scale each ratio so the shared term matches — `x:y:z = 10:15:21`.

---

## Slide Block B (18–25 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — covers the remaining three worked examples in NIAT_Ratios.pptx that precede the deck's second "Quiz Time" marker -->

Covers: a three-way partnership split defined by fractions of the others' sum → dividing a quantity by an "equal quotient" condition → adjusting a mixture ratio by adding one ingredient.

**Beats to emphasise**

- **Partnership-style splits.** Rs.16,940 divided among A, B, C such that A gets `3/4` of `(B+C)` and B gets `5/6` of `(A+C)`. Don't solve three simultaneous equations — convert each condition into "A as a fraction of the total". `A = 3/4(B+C) = 3/4(T−A) → 7A = 3T → A = 3T/7`. Same move gives `B = 5T/11`. With `T = 16,940`: `B = Rs.7,700`. This reframing is the single most time-saving idea in the whole session.
- **Equal-quotient division.** "Half of the first part = one-third of the second = one-fifth of the third," total Rs.1,800. Set that common value to `k`: first `= 2k`, second `= 3k`, third `= 5k`. Sum `= 10k = 1800 → k = 180`. First part `= Rs.360`.
- **Adjusting a mixture.** Water:milk `= 7:3` in 30 L → water `= 21` L, milk `= 9` L fixed. To reach water:milk `= 6:1`, milk stays at 9 L, so water must become `6 × 9 = 54` L. Water to add `= 33` L.

**Checkpoint (at 25 min)** — show hands:
> *"Water:milk is 7:3 in a 30-litre mixture. How many litres of water is that right now, and how many litres do we add to make it 6:1?"*
> **Answer:** 21 L present now; add 33 L to reach 6:1.

---

## ⚡ ALS Activity 1 — Trace the Table: Three Containers (25–33 min)

**ALS format:** Guided Table Build — a harder mixture problem, solved by building a table on the board, one row per container, filled in by different students. Chosen right after Slide Block B because this is the deck's hardest problem and the one place students will try to shortcut by adding the three ratios directly — the table forces the correct order: convert each container to actual quantities first, *then* combine.

**Setup line:**
> *"Three containers, three different milk:water ratios, three different sizes. Do NOT add the ratios together — that number means nothing. We fill this table one container at a time, in actual litres, then add the litres."*

Draw an empty table: **Container | Capacity | Milk:Water | Milk amount | Water amount**.

**The problem:** Containers A, B, C have milk:water ratios `1:5`, `3:5`, and `5:7` respectively. Their capacities are in ratio `5:4:5`. Find the combined ratio of milk to water when all three are mixed together.

**The table (capacities as `5k, 4k, 5k`)**

| Container | Capacity | Milk : Water | Milk amount | Water amount |
|---|---|---|---|---|
| A | `5k` | 1:5 (milk = 1/6) | `5k/6` | `25k/6` |
| B | `4k` | 3:5 (milk = 3/8) | `3k/2` | `5k/2` |
| C | `5k` | 5:7 (milk = 5/12) | `25k/12` | — |
| **Total** | `14k` | — | `53k/12` | `115k/12` |

**Answer:** Milk : Water `= 53k/12 : 115k/12` → **53 : 115**

**How it surfaces:** Before revealing the table, ask *"who was tempted to just add 1+3+5 and 5+5+7?"* Hands will go up — that's the misconception, named out loud.

**When it goes wrong**

| If… | Do this |
|---|---|
| Someone insists on adding the ratios directly | Ask: *"Container B is bigger than A — should its ratio count the same as A's?"* |
| Fraction arithmetic stalls the row-filling | Let a student say the fraction, you do the multiplication live. |

**Debrief line:**
> *"Ratios from different totals cannot be combined until you turn them into actual amounts. That's true whether it's litres, rupees, or people — always convert to real quantities before you add."*

**Cut rule:** Do containers A and B as full rows; give C's numbers directly and spend the saved time on the final sum.

---

## ⚡ ALS Activity 2 — Fill the Blank Live: The Ages Problem (33–40 min)

**ALS format:** Cold-Call Fill-the-Blank — a skeleton equation on the board with blanks, filled one at a time, in sequence. Chosen as the closing activity because this is the one genuine "ratio changes over time" problem in the set — a distinct skill from splitting a fixed total — and closes the session on algebra, not arithmetic.

**Setup line:**
> *"The present ages of Ashish and Sai Kiran are in the ratio 5:4. Three years later, that ratio becomes 11:9. I've written the whole solution as blanks — one blank, one person, in order. No jumping ahead."*

```
Ashish : Sai Kiran  (present)      =  5 : 4
Ashish = ___ x        Sai Kiran = ___ x

Three years later:
Ashish = ___             Sai Kiran = ___

New ratio is 11 : 9, so:     ___ / ___  =  11 / 9

Cross-multiply:     9 × ( ___ )  =  11 × ( ___ )

Solve:     x = ___

Sai Kiran's present age = 4x = ___
```

**Answers:** `Ashish = 5x, Sai Kiran = 4x` → three years later: `Ashish = 5x+3, Sai Kiran = 4x+3` → `(5x+3)/(4x+3) = 11/9` → `9(5x+3) = 11(4x+3)` → `45x+27=44x+33` → `x=6` → **Sai Kiran's present age = 4x = 24**.

**When it goes wrong**

| If… | Do this |
|---|---|
| A student writes the new ratio flipped | Point back at the problem: "Ashish : Sai Kiran" is always named in that order. |
| Cross-multiplication arithmetic goes wrong | Redo that one line slowly on the board — this is the exact spot marks are lost. |
| Nobody can state why we add "+3" and not "×3" | Ask: *"In three years, does an age multiply or does it just go up by 3?"* |

**Debrief line:**
> *"Same ratio skeleton you've used all session, just moving through time now instead of splitting a fixed total."*

**Cut rule:** If short on time, skip the first two blanks and start directly from "Three years later" — the graded skill is the cross-multiply and solve, not the initial `5x/4x` setup.

---

## Classroom Quiz (40–45 min) · Reserved — not yet available

No quiz bank exists yet for this Aptitude course (see Resources table). This 5-minute slot is reserved here, at the end of the session and right before the Exit Ticket, so the plan doesn't need restructuring once a quiz bank is added. Until then, run the dropped fractions-ratio drill here instead — "351 bananas split in ratio 1/2 : 1/3 : 1/4, what's the hidden first step?" — or fold the slot into Buffer and end early.

---

## Exit Ticket + Homework (45–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> Ashish : Sai Kiran are in the ratio 5:4 at present. Three years later, the ratio becomes 11:9. What is Sai Kiran's present age?
> **Answer:** 24.

Scan responses on the way out. If most get the ratio flipped or drop the "+3," open Session 19 with a 2-minute recap.

**Homework**

Re-solve, from memory and without looking at today's slides, all seven word problems from `NIAT_Ratios.pptx`:

1. Combine `x:y = 2:3` and `y:z = 5:7` into `x:y:z`.
2. Split Rs.810 in the ratio 3:4.
3. Split 351 bananas in the ratio `1/2 : 1/3 : 1/4`.
4. Split Rs.16,940 among A, B, C given A `= 3/4(B+C)` and B `= 5/6(A+C)`.
5. Find the number of 25p coins from the Rs.1, 50p, 25p coin problem (ratio 12:10:7, total Rs.75).
6. Split Rs.1,800 by the "half : one-third : one-fifth" equal-quotient condition.
7. Find how much water to add to the 30 L, water:milk `= 7:3` mixture to reach 6:1.

Check answers against today's board work. Bring a list of which ones you got wrong, and why, to the next session.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, run the coin-denomination problem: *"Vijay has coins of Rs.1, 50p, and 25p in ratio 12:10:7, total worth Rs.75. Find the number of 25p coins."* Convert every coin to rupees: `12k(1)+10k(0.5)+7k(0.25)=18.75k=75 → k=4`; 25p coins `=7k=`**28**. Never required.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A ratio has a fixed unit or size | Every ratio they've seen outside class comes attached to a real, fixed count | The Hook — same ratio 2:3 giving 16-and-24 in a class of 40, "x can be anything" |
| Two ratios sharing a term can be lined up without scaling | It looks like the terms already "match" by name | Slide Block A's worked method — scale until the shared term is numerically equal |
| Fractional ratio terms can be divided the same way as whole-number ratios | Fractions "already look like" parts of a whole | Slide Block A's fractions beat — clearing denominators via LCM first |
| In "A gets a fraction of (B+C)" problems, you must solve simultaneous equations | The problem *looks* like three unknowns, three equations | Slide Block B's reframing — express each person's share directly as a fraction of the total T |
| Ratios from different totals can be combined by adding the ratios directly | Adding looks like the natural way to "combine" | ALS Activity 1's table — forcing conversion to actual litres per container |

---

## Instructor Notes

- **Grounding:** This plan is built entirely from a local text-extraction of `NIAT_Ratios.pptx`. No platform unit ID, classroom quiz pool, or MCQ/coding practice bank exist for this topic yet.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Guided Table Build (the hardest problem in the deck — three containers), Activity 2 is Cold-Call Fill-the-Blank (the ages equation, a distinct algebra skill). The original Think-Pair-Share on fractions/denominations is folded into a 2-minute beat inside Slide Block A, with the coin-denomination problem demoted to an optional buffer closer.
- <!-- placement: inferred --> **Both Slide Block boundaries and the activity assignments are instructor judgment calls** — the deck has no timing metadata, only slide order.
- **Text-extraction artifacts:** the source text has corrupted special characters in a few places. All numbers and answers were independently re-derived and checked.
- **Slide 5's hint names a "Reverse N methodology"** with no definition anywhere in the extracted text. This plan teaches the underlying algebra without relying on that name. <!-- placement: inferred -->
- **Why there's no Classroom Quiz:** both "Quiz Time" slides in this deck are bare section dividers with no answer options attached.
