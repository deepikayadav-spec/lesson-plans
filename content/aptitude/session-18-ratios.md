# Session 18 — Ratios

**Duration** 60 min · **Topic** Ratios · **Prerequisite** Session 17 (Compound Interest)
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet for this topic.

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT_Ratios.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define a ratio (`a:b = a/b`) and explain why a ratio carries no units of its own. *(REMEMBERING)*
2. Combine two ratios that share a common term (e.g., `x:y` and `y:z`) into a single three-term ratio by equalising the shared term. *(UNDERSTANDING)*
3. Apply ratio division to split a quantity into parts — including parts defined by fractions, or by an "equal quotient" condition (half of one part = a third of another). *(APPLYING)*
4. Apply ratio reasoning to mixed-denomination and mixture word problems, converting every quantity to a common unit before writing the equation. *(APPLYING)*
5. Analyse multi-container mixture problems by breaking each container into its own ratio components before recombining them into one overall ratio. *(ANALYZING)*
6. Set up and solve an algebraic equation from a word problem where a ratio changes under a stated condition (e.g., ages after a number of years, or a partnership split). *(ANALYZING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 17 (Compound Interest)**. Newly authored from that deck's real figures. ~45 s each, project the distribution after each, never name individuals.

**Q1.** In the compound interest formula, what does "P" stand for?
`A` Profit · `B` Percentage · `C` Principal · `D` Period
→ **C.** *Targets:* basic CI vocabulary.

**Q2.** For a sum of Rs.1000 at 10% p.a., how do Simple Interest and Compound Interest compare in **Year 1 only**?
`A` They're equal (both Rs.100) · `B` CI is Rs.10 more · `C` CI is Rs.100 more · `D` Cannot say
→ **A.** *Targets:* the Session 17 worked table — SI and CI only start to diverge from Year 2 onward. *If >40% miss this:* the whole point of that comparison table didn't land; recap it in one sentence before moving on.

**Q3.** Which compounding frequency gives the **highest** amount for the same nominal rate?
`A` Compounded Per Annum · `B` Compounded Semi-Annually · `C` Compounded Quarterly · `D` All three are equal
→ **C.** *Targets:* the deck's own ordering, C.Q > C.S.A > C.P.A.

**Q4.** On Rs.8,000 for 2 years, at 10% for the first year and 12% for the second year, compound interest gave an amount of:
`A` Rs.9,600 · `B` Rs.9,856 · `C` Rs.9,800 · `D` Rs.10,000
→ **B.** *Targets:* straight recall of the deck's worked example.

**Q5.** A man invests Rs.6,000 for 2 years, compounded annually. At the end of Year 1 it amounts to Rs.7,200. What rate of interest is that?
`A` 10% · `B` 15% · `C` 20% · `D` 25%
→ **C.** (Rs.1,200 gained on Rs.6,000 = 20%.) *Targets:* working backwards from an amount to a rate — same skill CI and ratio problems both lean on.

**Q6.** *(MSQ — select all that apply)* Based on the Rs.1,000-at-10%-for-3-years example from last session, which statements are true?
`A` Year 1 SI and CI are equal · `B` Total SI over 3 years = Rs.300 · `C` Total CI over 3 years = Rs.331 · `D` CI is always less than SI
→ **A, B, C.** *Targets:* D is the trap — CI overtakes SI from Year 2 onward, it is never less. *If D gets picked heavily:* redraw the year-by-year table before the Hook.

**Q7.** The difference between CI and SI on a certain sum, at 10% p.a. for 2 years, was Rs.481. What was the sum?
`A` Rs.4,810 · `B` Rs.48,100 · `C` Rs.24,050 · `D` Rs.9,620
→ **B.** *Targets:* the hardest recall of the set — deliberately last, analysis-level.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–10 min)

Write on the board: **"This class has 40 students."** Nothing else yet.

Say: *"Last session you spent 60 minutes chasing rupees and paise to two decimal places. Forget money for a second."*

Add to the board: **"Boys : Girls = 2 : 3."**

Ask: *"Without any more information than that — how many boys and how many girls are in a class of 40?"*

Let them work it out out loud (2x + 3x = 5x = 40 → x = 8 → 16 boys, 24 girls). Someone will get there fast.

Say: *"That's it. That's the entire idea for today. Notice what I never told you — I never said what 'x' was. I never gave you a unit. A ratio compares two things of the same kind, and by itself it carries no unit at all. `2:3` could be 16-and-24, or 200-and-300, or 2-and-3. The ratio doesn't care. Today we learn what a ratio actually is, and then we spend the hour breaking real quantities apart using it."*

---

## Slide Block A (10–23 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — the deck itself has no timing metadata; this block covers the definition slide plus the first two worked examples that follow it, based on their order in NIAT_Ratios.pptx -->

Covers: the definition of a ratio → combining two ratios that share a term (`x:y` and `y:z`) → dividing a quantity directly in a given ratio.

**Beats to emphasise**

- **A ratio has no units.** `a:b = a/b`. In the Boys:Girls = 2:3 example, total boys = `2x`, total girls = `3x`, and `x` can be anything — the ratio only fixes the *proportion*, not the actual count. This is the Hook, now formalised.
- **Combining two ratios that share a term.** If `x:y = 2:3` and `y:z = 5:7`, you cannot just line them up — the `y` in each ratio is a different scale. The move is to scale each ratio so the shared term (`y`) matches: multiply `x:y` by 5 → `10:15`; multiply `y:z` by 3 → `15:21`. Now `y` reads `15` in both, so `x:y:z = 10:15:21`.
- **Direct division in a given ratio.** Two quantities in ratio `3:4`; if the first is Rs.810, one "part" is `810 ÷ 3 = 270`, so the second is `4 × 270 = 1080`. This single per-part move underlies almost every problem today.

**Checkpoint (at 23 min)** — cold-call:
> *"What's the actual trick for combining `x:y = 2:3` with `y:z = 5:7` into one ratio?"*
> **Answer:** Scale each ratio so the shared term matches — `x:y` becomes `10:15`, `y:z` becomes `15:21` — giving `x:y:z = 10:15:21`.

---

## ⚡ Activity 1 — Think–Pair–Share: Fractions and Denominations (23–30 min)

### What this activity is

Two short word problems, worked in pairs, both taken directly from the deck's own worked examples. Students think alone for 60 seconds, then pair up to agree on a method before you cold-call for answers.

### Why it's here

Both problems hide a conversion step before the "real" ratio work can start — fractional ratio terms in one, mixed coin denominations in the other. Students who skip the conversion get a confidently wrong answer, which is exactly the trap the deck's own hints are guarding against.

### Before class

Have both problems on one slide or the board, side by side.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, reveal both problems | Read |
| 0:30–1:30 | Wait, silent | Think alone |
| 1:30–4:30 | Circulate | Pair up, agree on a method and an answer |
| 4:30–6:30 | Cold-call one pair per problem | Give method + answer |
| 6:30–7:00 | Debrief | Listen |

### Say this

> *"Two problems. One minute alone, then talk to your partner. I'm not asking for just the number — I want the one conversion step you did *before* you touched the ratio."*

### The problems

**1.** 351 bananas were distributed among three monkeys in the ratio `1/2 : 1/3 : 1/4`. How many bananas did the first monkey get?
*(Deck's own hint: convert the fractions into integers by taking the LCM of the denominators.)*

**2.** Vijay has coins of denominations Rs.1, 50p, and 25p in the ratio `12:10:7`. The total worth of his coins is Rs.75. Find the number of 25p coins Vijay has.

### Answers

| # | Conversion step | Method | Answer |
|---|---|---|---|
| 1 | LCM(2,3,4) = 12 → ratio becomes `6:4:3` | `351 × 6/13` | **162** |
| 2 | Convert every coin to rupees: `1, 0.50, 0.25` | `12k(1) + 10k(0.5) + 7k(0.25) = 18.75k = 75 → k = 4`; 25p coins `= 7k` | **28** |

**How it surfaces:** After each pair answers, ask *"what would happen if you'd skipped that conversion?"* — for #1, multiplying the fractions straight through gives the wrong split; for #2, treating 50 and 25 as whole rupees rather than half/quarter rupees breaks the total.

**Debrief line:**
> *"Every ratio problem with fractions or mixed units has this one hidden step — get everything into the same kind of number first. Do that, and the ratio part is just arithmetic."*

**Cut rule:** If running short, run the coins problem only — the denomination conversion is the higher-value skill and shows up again in the mixture problems coming up.

---

## Classroom Quiz (30 min)

> Classroom Quiz: not yet available — add once question bank exists for this topic.

*Time reallocated below: this deck's own "Quiz Time" section marker falls at exactly this point in the material, but carries no MCQ options (unlike the Compound Interest deck's quiz slides, which had A–D choices). With no live-vote question bank to draw from, the ~7 minutes this block would normally occupy have been folded into Slide Block A, Activity 1, and a third activity later in the session — see Instructor Notes.*

---

## Slide Block B (30–42 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — covers the remaining three worked examples in NIAT_Ratios.pptx that precede the deck's second "Quiz Time" marker -->

Covers: a three-way partnership split defined by fractions of the others' sum → dividing a quantity by an "equal quotient" condition → adjusting a mixture ratio by adding one ingredient.

**Beats to emphasise**

- **Partnership-style splits.** Rs.16,940 divided among A, B, C such that A gets `3/4` of `(B+C)` and B gets `5/6` of `(A+C)`. Don't solve three simultaneous equations — convert each condition into "A as a fraction of the total". `A = 3/4(B+C) = 3/4(T−A) → 7A = 3T → A = 3T/7`. Same move gives `B = 5T/11`. With `T = 16,940`: `B = 5 × 16,940 / 11 = Rs.7,700`. This reframing is the single most time-saving idea in the whole session.
- **Equal-quotient division.** "Half of the first part = one-third of the second = one-fifth of the third," total Rs.1,800. Set that common value to `k`: first `= 2k`, second `= 3k`, third `= 5k`. Sum `= 10k = 1800 → k = 180`. First part `= 2k = Rs.360`.
- **Adjusting a mixture.** Water:milk `= 7:3` in 30 L → water `= 21` L, milk `= 9` L fixed. To reach water:milk `= 6:1`, milk stays at 9 L, so water must become `6 × 9 = 54` L. Water to add `= 54 − 21 = 33` L. The instinct to check: which ingredient is fixed, and which is being changed?

**Checkpoint (at 42 min)** — show hands:
> *"Water:milk is 7:3 in a 30-litre mixture. How many litres of water is that right now, and how many litres do we add to make it 6:1?"*
> **Answer:** 21 L of water present now; add 33 L to reach 6:1 (milk stays fixed at 9 L, water needs to reach 54 L).

---

## ⚡ Activity 2 — Trace the Table: Three Containers (42–49 min)

### What this activity is

A harder mixture problem, solved by building a table on the board, one row per container, filled in by different students as you go.

### Why it's here

This is the deck's hardest problem and the one place students will try to shortcut by adding the three ratios directly — `1:5 + 3:5 + 5:7` — which is meaningless because the containers hold different total amounts. The table forces the correct order of operations: convert each container to actual quantities first, *then* combine.

### Before class

Draw an empty table on the board with these headers: **Container | Capacity | Milk:Water | Milk amount | Water amount (= Capacity − Milk)**.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, reveal the empty table and the problem | Read |
| 0:30–5:00 | Call a different student for each container's row | Fill capacity, then milk amount, then water amount |
| 5:00–6:00 | Sum the Milk and Water columns together | Watch, confirm the sum |
| 6:00–7:00 | Debrief | Listen |

### Say this

> *"Three containers, three different milk:water ratios, three different sizes. Do NOT add the ratios together — that number means nothing. We fill this table one container at a time, in actual litres, then add the litres."*

**The problem:** Containers A, B, C have milk:water ratios `1:5`, `3:5`, and `5:7` respectively. Their capacities are in ratio `5:4:5`. Find the combined ratio of milk to water when all three are mixed together.

### The table (capacities as `5k, 4k, 5k`)

| Container | Capacity | Milk : Water | Milk amount | Water amount |
|---|---|---|---|---|
| A | `5k` | 1:5 (milk = 1/6) | `5k/6` | `25k/6` |
| B | `4k` | 3:5 (milk = 3/8) | `3k/2` | `5k/2` |
| C | `5k` | 5:7 (milk = 5/12) | `25k/12` | — |
| **Total** | `14k` | — | `53k/12` | `14k − 53k/12 = 115k/12` |

### Answer

Milk : Water `= 53k/12 : 115k/12` → **53 : 115**

**How it surfaces:** Before revealing the table, ask *"who was tempted to just add 1+3+5 and 5+5+7?"* Hands will go up — that's the misconception, named out loud.

**When it goes wrong**

| If… | Do this |
|---|---|
| Someone insists on adding the ratios directly | Ask: *"Container B is bigger than A — should its ratio count the same as A's?"* That's the capacity difference the direct-add ignores. |
| Fraction arithmetic stalls the row-filling | Let a student say the fraction, you do the multiplication live rather than losing the room's pace. |
| Running long | Fill rows A and B live, then just state C's numbers and have the class do the final sum only. |

**Debrief line:**
> *"Ratios from different totals cannot be combined until you turn them into actual amounts. That's true whether it's litres, rupees, or people — always convert to real quantities before you add."*

**Cut rule:** Do containers A and B as full rows; give C's milk/water amounts directly and spend the saved time on the final sum and debrief.

---

## ⚡ Activity 3 — Fill the Blank Live: The Ages Problem (49–56 min)

### What this activity is

You put a skeleton equation on the board with blanks. Students fill one blank at a time, cold-called in sequence, until the equation is fully solved.

### Why it's here

This is the deck's final worked example and the one genuine "ratio changes over time" problem in the set — a distinct skill from everything else covered today (splitting a fixed total). It closes the session on algebra, not arithmetic.

### Before class

Write this skeleton on the board, blanks and all:

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

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, reveal the skeleton | Read |
| 0:30–5:00 | Point at each blank, cold-call one student per blank | Fill it, explain in one sentence |
| 5:00–6:30 | Solve the final equation together | Watch, confirm |
| 6:30–7:00 | Debrief | Listen |

### Say this

> *"The present ages of Ashish and Sai Kiran are in the ratio 5:4. Three years later, that ratio becomes 11:9. I've written the whole solution as blanks — one blank, one person, in order. No jumping ahead."*

### Answers

`Ashish = 5x, Sai Kiran = 4x` → three years later: `Ashish = 5x+3, Sai Kiran = 4x+3` → `(5x+3)/(4x+3) = 11/9` → `9(5x+3) = 11(4x+3)` → `45x + 27 = 44x + 33` → `x = 6` → **Sai Kiran's present age = 4x = 24**.

**When it goes wrong**

| If… | Do this |
|---|---|
| A student writes the new ratio as `(4x+3)/(5x+3) = 11/9` (flipped) | Point back at the problem statement: "Ashish : Sai Kiran" is always named in that order, so Ashish's expression is always the numerator here. |
| Cross-multiplication arithmetic goes wrong | Redo that one line slowly on the board rather than moving on — this is the exact spot marks are lost in this problem type. |
| Nobody can state why we add "+3" and not "×3" | Ask: *"In three years, does an age multiply or does it just go up by 3?"* |

**Cut rule:** If short on time, skip the first two blanks (present-age setup was already used all session) and start directly from "Three years later" — the graded skill is the cross-multiply and solve, not the initial `5x/4x` setup.

---

## Exit Ticket + Homework (56–60 min)

**Exit ticket** — before anyone leaves:

> Ashish : Sai Kiran are in the ratio 5:4 at present. Three years later, the ratio becomes 11:9. What is Sai Kiran's present age?
> **Answer:** 24 (solve `x = 6`, present age `= 4x = 24`).

Scan responses on the way out. If most get the ratio flipped or drop the "+3," open Session 19 with a 2-minute recap of this equation.

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

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A ratio has a fixed unit or size (e.g., "2:3 means 2 boys") | Every ratio they've seen outside class comes attached to a real, fixed count | The Hook — same ratio 2:3 giving 16-and-24 in a class of 40, with "x can be anything" from the deck stated explicitly |
| Two ratios sharing a term can be lined up without scaling (`x:y=2:3`, `y:z=5:7` → just read off `x:y:z`) | It looks like the terms already "match" by name | Slide Block A's worked method — scale both ratios until the shared term is numerically equal, then read off `x:y:z = 10:15:21` |
| Fractional ratio terms (`1/2 : 1/3 : 1/4`) can be divided the same way as whole-number ratios | Fractions "already look like" parts of a whole | Activity 1 — clearing denominators via LCM first, then dividing |
| In "A gets a fraction of (B+C)" problems, you must solve simultaneous equations for A, B, and C | The problem *looks* like three unknowns, three equations | Slide Block B's reframing — express each person's share directly as a fraction of the total T |
| Ratios from different totals can be combined by adding the ratios directly (`1:5 + 3:5 + 5:7`) | Adding looks like the natural way to "combine" | Activity 2's table — forcing conversion to actual litres per container before any combination |

---

## Instructor Notes

- **Grounding:** This plan is built entirely from a local text-extraction of `NIAT_Ratios.pptx` (17 slides). There is no platform unit ID, no classroom quiz pool, and no MCQ/coding practice bank for this topic yet — all three are flagged as "not yet available" rather than invented. The warm-up poll's Session 17 figures are pulled verbatim from a matching extraction of `NIAT_Compound interest.txt`.
- <!-- placement: inferred --> **Both Slide Block boundaries and the activity/checkpoint assignments are instructor judgment calls**, not stated by the deck itself — the deck has no timing metadata, only slide order. The split used here (Block A = definition + first 2 examples; Activity 1 = next 2 examples; Block B = next 3 examples; Activities 2–3 = final 2 examples) follows the deck's own two "Quiz Time" section markers as natural halves. Re-check against the live deck and adjust if your institution paces it differently.
- **Text-extraction artifacts:** the source text has corrupted special characters in a few places (e.g. `Ratio's` renders as `Ratio�s`, and slide 4's speaker note reads `Duplicating ratio | �#�`). All numbers and answers used in this plan were independently re-derived and checked against the stated answers in the extraction — the corruption only affects punctuation/notes, not figures. The "Duplicating ratio" note most likely refers to equivalent ratios (`a:b = ka:kb`); confirm the exact wording against the live slide before using it verbatim.
- **Slide 5's hint names a "Reverse N methodology"** with no definition anywhere in the extracted text. This plan teaches the underlying algebra (equalise the shared term) without relying on that name, since inventing a definition for it would violate the no-invention rule. If this refers to a named technique taught elsewhere in your course, confirm it and insert the proper explanation before class.
- **Slide 14's answer appears in the raw extraction as two fragments, "2" then "4"** (likely split across two text boxes on the slide, i.e. "24"). Independently verified by re-solving the problem (`x = 6`, `4x = 24`) — the reconstructed answer is correct.
- **Why there's no Classroom Quiz:** both "Quiz Time" slides in this deck (originally slide 10 and slide 15) are bare section dividers with no answer options attached — unlike the Compound Interest deck, whose quiz slides carried real A–D choices. There is genuinely no MCQ material in this deck to run a live vote from, hence the placeholder and the time reallocation to a third activity.
- **Pacing risk:** Slide Block B carries three problems in 12 minutes, including the hardest algebra of the session (the partnership split). If that reframing needs re-explaining, trim the Rs.1,800 equal-quotient walkthrough to the answer only — the underlying "set a common value to k" skill is reinforced again structurally in Activity 3's ages problem.
