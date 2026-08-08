# Session 16 — Simple Interest: Terms and Formulas

**Duration** 60 min · **Topic** Simple Interest — Terms and Formulas · **Prerequisite** Session 15 (Discount)
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet.

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT_Simple interest.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define Principal, Rate, Time, and Interest, and state the relation Amount = Principal + Interest. *(REMEMBERING)*
2. State the simple interest formula SI = (P × R × T) / 100 and map each symbol onto the given values in a word problem. *(UNDERSTANDING)*
3. Calculate an unknown principal or time, given the other three quantities in the SI formula. *(APPLYING)*
4. Solve for rate or time when no principal is stated directly, by assuming a convenient value such as 100. *(APPLYING)*
5. Solve multi-part simple interest problems where the principal changes partway through the time period — a partial withdrawal, or an amount split across two schemes. *(ANALYZING)*
6. Compare simple interest earned by the same principal and rate across different time periods using ratios. *(ANALYZING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 15 (Discount)**. Newly authored MCQs, real numbers and answers from that deck. ~45 s each, project the distribution, never name individuals.

**Q1.** A shopkeeper offers "buy 3 shirts, get 1 shirt free." What discount percent is this equivalent to?
`A` 20% · `B` 25% · `C` 33% · `D` 40%
→ **B) 25%.** *Targets:* converting a "buy X get Y free" offer into an equivalent discount percentage.

**Q2.** Three successive discounts of 10%, 20%, and 25% are applied to the same item. What single discount is this equivalent to?
`A` 55% · `B` 46% · `C` 40% · `D` 51%
→ **B) 46%.** *Targets:* successive discounts multiply the remaining fraction (0.9 × 0.8 × 0.75), they do not add.

**Q3.** Shop A gives successive discounts of 15% then 10%. Shop B gives a flat 25% discount on the same item. Which is the better deal for the buyer?
`A` Shop A · `B` Shop B (flat 25%) · `C` Identical · `D` Cannot be determined
→ **B) Shop B.** *Targets:* the same misconception as Q2 — successive 15% and 10% is only ≈23.5%, less than a flat 25%. *If most pick "identical,"* that's tonight's reteach candidate for the Hook.

**Q4.** A shopkeeper marks goods 20% above cost price, then sells at a 30% discount on the marked price. What's the result?
`A` 16% profit · `B` 16% loss · `C` 6% profit · `D` No profit, no loss
→ **B) 16% loss.**

**Q5.** Marked price of a chair is Rs 12,800. The shopkeeper first offers 20% off, then a further successive discount, and finally sells it for Rs 9,216. What was the second discount?
`A` 5% · `B` 10% · `C` 12% · `D` 15%
→ **B) 10%.** *Targets:* working backward through a successive discount to recover a missing percentage.

**Q6.** It costs Rs 1 per sheet to photocopy. A 2% discount applies to every sheet after the first 1000. What is the total cost of 5000 sheets?
`A` Rs 4900 · `B` Rs 4920 · `C` Rs 5000 · `D` Rs 4800
→ **B) Rs 4920.**

**Q7.** By what percent should cost price be increased so that a shopkeeper still earns a 20% profit after giving a 40% discount on the marked price?
`A` 60% · `B` 80% · `C` 100% · `D` 120%
→ **C) 100%.** *Hardest of the set — reverse-percentage chaining.* If this lands weak, don't reteach now; note it and move on, today's topic is different maths.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including reads.

---

## Hook (7–10 min)

Put the deck's own recap line on the board, exactly as it opens:

> Recap: Profit & Loss → Percentages → LCM & HCF → Number Systems → **Discount** (last session) → **Simple Interest** (today).

Say: *"Every topic on that list is about one number changing because of another — profit changes with cost, discount changes with price. Today, money changes because of time. If I lend you Rs 100 today and you hand me back exactly Rs 100 in a year — have I gained anything?"*

Let them answer "no."

*"Right. Nothing. That's why interest exists — it's rent, charged for the use of money instead of the use of a room. Every question today is really asking one thing: how much rent is fair, given how much money, at what rate, for how long? By the end of the next twelve minutes you'll have the one formula that answers that, every time."*

---

## Slide Block A (10–23 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred from deck slide order (Slides 4–6). Slide 4 ("Terms and Formulas") lists the symbols P, R, T, I and the line "Amount = P + I" but the text-extraction did not capture an explicit "SI = PRT/100" line — it is likely rendered as an equation graphic on the slide itself. The formula below is the standard relation these listed terms define; confirm its exact on-screen wording/layout against the live deck before class. -->

Covers: Terms and Formulas → Worked Example (find Principal) → Worked Example (find Time).

**Beats to emphasise**

- **Terms, cold, on the board:** Amount = P + I. P = Principal (also called Sum). R = Rate of Interest. T = Time. I (or SI) = Simple Interest. Then write the connective formula next to it: **SI = (P × R × T) / 100.** The deck gives you the parts; the formula is what makes them useful.
- **Worked Example 1** *(Slide 5)* — "A man took a loan from a bank at the rate of 14% p.a. simple interest. After 3 years he had to pay Rs 8400 as interest. What was the principal amount borrowed?" Show the substitution live, step by step:
  - 8400 = P × 14 × 3 / 100 → P = 8400 × 100 / 42 = **Rs 20,000.**
- **Worked Example 2** *(Slide 6)* — "How much time will it take for an amount of Rs 650 to yield Rs 169 as interest at 6.5% p.a. simple interest?"
  - 169 = 650 × 6.5 × T / 100 → T = 16900 / 4225 = **4 years.**
- **Beat:** name it explicitly — both problems used the exact same formula, just solving for a different letter. That reframe (one formula, four unknowns, solve for whichever is missing) is the whole session.

**Checkpoint (at 23 min)** — cold-call two students:
> *"In Example 1, the man borrowed Rs 20,000 and paid Rs 8,400 in interest. What Amount did he actually hand back to the bank?"*
> **Answer:** Amount = P + I = 20,000 + 8,400 = **Rs 28,400.**

---

## ⚡ Activity 1 — Think–Pair–Share (23–30 min)

**Format:** Think–Pair–Share · **Exposes:** two classic Simple-Interest misreadings — treating "rate increased by 3%" as rate × 1.03 instead of rate + 3, and reasoning about "doubling" problems the way you would compound interest.

**Setup line (say this):**
> *"Two problems, same rule both times: work it out on your own first, then check with your neighbour before anyone shouts an answer."*

**Problem 1** *(Slide 7)* — **Think, 90 sec, alone:**
> *"A sum of Rs 800 amounts to Rs 920 in 3 years at simple interest. If the interest rate is increased by 3%, what would it amount to?"*

Give 90 seconds of silence — no hints yet.

**Pair, 60 sec:** Compare working with your neighbour. If your answers don't match, find whose first step is wrong.

**Share — run it together on the board:**
- SI so far = 920 − 800 = Rs 120 over 3 years.
- Rate = SI × 100 / (P × T) = 120 × 100 / (800 × 3) = **5%.**
- New rate = 5% + 3 = **8%** — not 5% × 1.03. Say this explicitly: *"increased by 3%"* means 3 more percentage points, added, not 3% of the rate.
- New SI = 800 × 8 × 3 / 100 = Rs 192.
- New Amount = 800 + 192 = **Rs 992.**

**Problem 2** *(Slide 8)* — **Think, 45 sec, straight to a vote (MCQ):**
> *"In how many years will a sum double itself at 11.11% p.a. simple interest? A) 4  B) 8  C) 9  D) 16"*

Take the vote, then run it:
- Doubling means Amount = 2P, so SI = Amount − P = P.
- SI = PRT/100 → P = P × 11.11 × T / 100 → T = 100 / 11.11 = **9 years → C.**

**Debrief line:**
> *"Both problems had a trap in the wording, not the maths. 'Increased by 3%' is addition. 'Doubles' just means the interest equals the whole principal — nothing to do with compounding."*

**When it goes wrong**

| If… | Do this |
|---|---|
| Pairs land on 8.24% (multiplying 5% × 1.03) | Stop. Write "increased BY 3%" vs "increased TO 3%" side by side and ask which the sentence actually says. |
| Someone answers Problem 2 with 8 (rounding 100/11.11 down early) | Point out 11.11% is a rounded form of 1/9 — walk the division once more slowly; it lands exactly on 9. |
| Room is silent in the Think phase | Prompt: *"What's the very first number you can calculate, even before you know the rate?"* (→ SI = 120) |

**Cut rule:** If short on time, drop the Pair step on Problem 1 and go straight from Think to the board walkthrough. Keep Problem 2's vote — it's faster and carries the doubling misconception, which is the one likely to resurface later.

---

## Classroom Quiz

> Classroom Quiz: not yet available — add once question bank exists for this topic.

No classroom quiz pool exists yet for Simple Interest, so this session has no dedicated 27–34 min quiz block. That time is folded into the schedule below: Slide Block A runs to 23 min instead of 22 to seat both worked examples properly, and the remaining minutes are absorbed into Slide Block B and the activities that follow — the 60-minute timeline has no gap.

---

## Slide Block B (30–42 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred from deck slide order (Slides 9, 11). Slide 9's time value renders as "3 �" in the text-extraction (an encoding artifact) — read here as 3½ years; this is confirmed by the arithmetic working out exactly to the deck's stated answer (see below), but verify the actual glyph against the live deck. -->

Covers: Worked Example (find the Sum from two Amounts at two different times) → Quiz-Time Problem (partial withdrawal, find the Rate).

**Beats to emphasise**

- **Worked Example** *(Slide 9)* — "A certain sum of money amounts to Rs 1008 in 2 years and to Rs 1164 in 3½ years. Find the sum." Deck's own hint: *"Sum = Principal."* Flag that explicitly — "sum" here means Principal, not the Amount.
  - Difference in Amount (1164 − 1008 = 156) is the interest earned over the *extra* 1.5 years only → interest per year = 104.
  - Interest for the first 2 years = 104 × 2 = 208.
  - Sum (Principal) = 1008 − 208 = **Rs 800.**
- **Quiz-Time Problem** *(Slide 11)* — "Pragna deposited Rs 8000 in a bank paying simple interest. After one year, she withdraws Rs 2000. At the end of 3 years, she received Rs 7800, having never collected her interest till then. Find the rate." Deck's own hint: *"Divide the simple interest into 2 parts."*
  - Interest on the full Rs 8000 for year 1, plus interest on the remaining Rs 6000 for years 2–3: total interest = (8000×R×1)/100 + (6000×R×2)/100 = 200R.
  - What she "received" at the end = the Rs 6000 still on deposit + all accumulated interest: 6000 + 200R = 7800 → 200R = 1800 → **R = 9%.**

**Checkpoint (at 42 min)** — cold-call:
> *"State the 'divide into parts' technique in one sentence — when do you use it?"*
> **Answer:** Whenever the principal changes partway through the time period, split the timeline at the point it changes and calculate the interest on each amount for its own duration, separately.

---

## ⚡ Activity 2 — Rapid Fire Board Race (42–49 min)

**Format:** Rapid Fire Board Race · **Exposes:** the "no rate or principal was given directly, so I can't solve it" freeze — and rehearses the deck's own fix for it.

**Setup line (say this):**
> *"One problem, no number you can plug in directly, four rounds, teams race to the board each round. First team with the right number on the board wins that round."*

**Before class:** Split the room into 2–4 teams. Have a board column ready per team.

**The problem** *(Slide 12, on screen throughout):*
> *"A sum becomes 5 times in 20 years at simple interest. Find the rate. A) 10% B) 30% C) 40% D) 20%"*
Deck's own hint: *"Assume a simple value like 100 when nothing is given."*

**Round 1 (30 sec) — Assume:** Teams write an assumed Principal and the resulting Amount. Correct opening move: P = 100, Amount = 500 (five times). First team to get both numbers right wins the round.

**Round 2 (30 sec) — Extract SI:** SI = Amount − Principal = 500 − 100 = **400.**

**Round 3 (60 sec) — Solve for R:** R = SI × 100 / (P × T) = 400 × 100 / (100 × 20) = **20%.**

**Round 4 (30 sec) — Vote the MCQ:** Confirm **D) 20%.**

**Debrief line:**
> *"Nothing changes if you'd assumed P = 200 instead of 100 — try it after class and check you still land on 20%. The number you assume gets thrown away; only the ratio survives. That's why assuming 100 is always safe."*

**When it goes wrong**

| If… | Do this |
|---|---|
| A team assumes Amount = 5 (not 5 × P) | Reread the sentence together: "becomes 5 times" — the Amount is five times the Principal, not the literal value 5. |
| Teams stall on Round 1 | Give the sentence starter: "If nothing is given, assume Principal = ___." |
| One team finishes all four rounds before others start Round 2 | Let them "referee" the next team's board work instead of racing again. |

**Cut rule:** Compress Rounds 1–2 into a single 45-second round if time is tight. Rounds 3–4 (solving for R and confirming the MCQ) are non-negotiable — that's where the actual rate calculation happens.

---

## ⚡ Activity 3 — Trace the Table (49–56 min)

**Format:** Trace the Table · **Exposes:** the jump straight to "some formula" that students attempt on two-part / comparison SI problems, instead of first laying out what's actually known.

**Setup line (say this):**
> *"Before anyone calculates anything, we build the table together. No one writes an equation until every cell that can be filled from the question is filled."*

**Before class:** Draw a blank table with columns: Scheme/Case | Principal | Rate | Time | Interest.

**Problem 1 (4 min)** *(Slide 13):*
> *"Veda invested Rs 13,900 divided in two schemes A and B at simple interest rates of 14% p.a. and 11% p.a. respectively. If the total interest earned in 2 years is Rs 3508, what was the amount invested in Scheme B? A) Rs 6400 B) Rs 6500 C) Rs 7200 D) Rs 7500"*

Build the table live, calling on a different student for each cell:

| Scheme | Principal | Rate | Time | Interest |
|---|---|---|---|---|
| A | 13900 − x | 14% | 2 | (13900−x)(14)(2)/100 |
| B | x | 11% | 2 | x(11)(2)/100 |

Only once every cell is filled, write the one equation that matters:
(13900−x)(28)/100 + x(22)/100 = 3508 → 389200 − 6x = 350800 → x = **6400 → A.**

**Problem 2 (3 min)** *(Slide 15) — faster, same table habit:*
> *"A sum of money was put at SI at a certain rate for 2 years. Had it been at 1% higher rate, it would have fetched Rs 24 more. Find the sum. A) Rs 2400 B) Rs 1200 C) Rs 4800 D) Rs 600"*

| Case | Principal | Rate | Time | Interest |
|---|---|---|---|---|
| Original | P | R | 2 | PR(2)/100 |
| +1% rate | P | R + 1 | 2 | P(R+1)(2)/100 |

Extra interest = P(R+1)(2)/100 − PR(2)/100 = 2P/100 = 24 → **P = 1200 → B.**

Point out explicitly: R cancels out completely — that's why the problem is solvable even though no rate is ever given.

**Debrief line:**
> *"In both problems, the table did the hard part before you touched algebra. If you can't fill a cell, that's the exact quantity the question is testing — it's not a sign you're stuck."*

**When it goes wrong**

| If… | Do this |
|---|---|
| Students want to jump to the equation before the table is full | Physically block it — say "not yet" and point back at the empty cell. |
| Nobody notices R cancels in Problem 2 | After solving, ask: "which value did we never actually need?" |
| Time is short | Run Problem 2 only — it's faster, and "the rate was never needed" is the sharper takeaway of the two. |

**Cut rule:** Run Problem 2 alone if under 4 minutes remain.

---

## Exit Ticket + Homework (56–60 min)

**Exit ticket** — before anyone leaves:

> *(Slide 14)* "What will be the ratio of the simple interests earned by a certain amount, at the same rate of interest, for 8 years and for 14 years?"
> **Answer: 4 : 7** — Principal and Rate are fixed, so SI is directly proportional to Time alone; the ratio of interests equals the ratio of times (8 : 14 = 4 : 7).

Scan answers on the way out. Anyone who reaches for the full PRT/100 formula instead of the direct ratio is the signal to re-open this idea briefly at the start of the next session.

**Homework**

| Task | Instruction |
|---|---|
| Re-work the deck | Redo all 10 problems on Slides 5, 6, 7, 8, 9, 11, 12, 13, 14, 15 of `NIAT_Simple interest.pptx` from a blank page, with no hints, writing out the SI substitution step every time. |
| Self-check | For each problem, note in the margin which one of P, R, T, or Sum/Principal you were solving for — that identification habit is what this session was building. |

No separate MCQ/Coding Practice pool or classroom quiz set exists for this topic yet — say this explicitly, so students don't go looking for a practice set that doesn't exist. Tonight, the deck's own ten problems are the practice set.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| "Sum" in a problem means the final Amount | In everyday language "sum of money" sounds like a total | Slide 9's own hint, "Sum = Principal," stated explicitly before working the problem |
| "Rate increased by 3%" means rate × 1.03 | Percent language is read multiplicatively by default | Activity 1, Problem 1 — writing "5% + 3 = 8%" on the board next to the wrong "5% × 1.03" |
| Doubling/multiplying-sum problems need compound-interest-style reasoning | Doubling "feels like" growth, which many associate with compounding | Activity 1, Problem 2 — showing Amount = 2P → SI = P is a flat, one-step relation, not iterative growth |
| A changing principal (partial withdrawal, or two schemes) can be treated as one single-block SI calculation | The earlier worked examples used one constant principal throughout | Slide Block B's Pragna problem and Activity 3's Veda problem — both solved only by splitting into parts first |
| A problem with no principal or rate stated can't be solved | Students expect every needed number to be handed to them | Activity 2 — modelling the deck's own hint of assuming Principal = 100, then showing the assumed value cancels out |

---

## Instructor Notes

- **Grounding:** this plan is built entirely from a local text-extraction of `NIAT_Simple interest.pptx` (this session) and `NIAT_Discount.pptx` (for the warm-up poll). No platform unit IDs, question IDs, or quiz/MCQ/coding pools exist for this content — none are invented here, and the Resource table above states that plainly.
- **Formula rendering is inferred.** <!-- placement: inferred --> Slide 4 lists P, R, T, I, and "Amount = P + I" but the extraction did not capture an explicit "SI = PRT/100" line — it's likely a graphic/equation object that didn't extract as text. Confirm the exact on-screen formula and layout against the live deck before class; the relation itself is standard and not in doubt.
- **Slide 9's time value is inferred.** <!-- placement: inferred --> The extracted text shows "3 �" for the second time period — read here as 3½ years. This is corroborated by the arithmetic landing exactly on the deck's stated answer (Rs 800), but sanity-check the glyph on the actual slide.
- **Slide 3's agenda text contains a stray "Ranking" label** ("Ranking | Agenda | Terms and Formulas | Ranking | Simple Interest") that does not correspond to any content in this deck — most likely a leftover template artifact from the text extraction. It is not used anywhere in this plan; flagging it so it isn't mistaken for missing content.
- **"Quiz Time" (Slides 10 and 16) are section dividers in the deck**, not additional questions — they mark the boundary between the instructor-led worked examples (Slides 5–9) and the student-facing practice problems (Slides 11–15). This plan treats Slides 5–9 as taught examples (Slide Blocks A/B) and Slides 11–15 as the material for Activities 2–3 and the Exit Ticket.
- **No Classroom Quiz block exists.** Its usual 27–34 min slot has been reallocated across Slide Block A (extended to 23 min) and the activities that follow, exactly as flagged in the Classroom Quiz section above — the 60-minute timeline has no gap.
- **Slides 17–18** ("Give Your Feedback," "Thank You") are session-closing slides with no teaching content; they are not scheduled anywhere in this plan and can be shown after the 60-minute mark if a feedback collection step is required separately.
- **Pacing risk:** Slide Block B carries two multi-step problems (Sum-finding, Pragna) in 12 minutes — don't let either one stretch past 6 minutes each, or Activity 2 loses its runway.
