# Session 13 — Profit & Loss: Terms and Relations, Representation

**Duration** 60 min · **Topic** Profit & Loss — Terms and Relations, Representation · **Prerequisite** Session 12 (Percentages 2 — Important Question Types)
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet for this topic.

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT_Profit and loss.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define Cost Price, Selling Price, Marked Price, Profit, Loss, and Discount, and state how each is calculated from the other two. *(REMEMBERING)*
2. Explain why Profit% and Loss% are always calculated on the Cost Price, never the Selling Price. *(UNDERSTANDING)*
3. Convert a stated profit or loss percentage into its `SP = CP × multiplier` representation (e.g. 20% profit → `SP = 1.2 CP`). *(APPLYING)*
4. Apply the CP/SP/Profit%/Loss% relations to solve multi-step word problems, including cases where neither CP nor SP is given directly and a convenient value must be assumed. *(APPLYING)*
5. Analyse compound profit/loss scenarios — two transactions with equal and opposite percentages, or a gain earned on only part of a set of goods — to determine whether the net result is a profit, a loss, or no change. *(ANALYZING)*
6. Distinguish "profit percentage calculated on Selling Price" from "actual profit percentage" (on Cost Price) and convert correctly between the two. *(ANALYZING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 12 (Percentages — Important Question Types)**. Newly authored MCQ options wrapped around the deck's real problems and real answers. ~45 s each, project the distribution, never name individuals.

**Q1.** The sum of boys and girls in a school is 150. If the number of boys is `x`, and the number of girls becomes `x%` of the total number of students, find `x`.
`A` 50 · `B` 60 · `C` 40 · `D` 75
→ **B.** *Targets:* turning a word relation into a percentage equation (`150 − x = (x/100)×150`). *Misconception:* reading "girls = x% of total" as "girls = x% of x."

**Q2.** A candidate who gets 86% of the votes wins by a majority of 576 votes. What is the total number of votes polled?
`A` 600 · `B` 720 · `C` 800 · `D` 900
→ **C.** *Targets:* majority = (winning% − losing%) of the total → 72% of total = 576. *If >40% wrong:* they used 86% of total = 576 directly — show why the margin, not the winning share, equals the majority.

**Q3.** Dheeraj spends 30% of his income on petrol, 25% of the remaining on house rent, and the balance on food. If he spends ₹300 on petrol, what is his expenditure on house rent?
`A` ₹150 · `B` ₹175 · `C` ₹200 · `D` ₹250
→ **B.** *Targets:* a percentage of the *remainder*, not of the original total. *Misconception (option D):* taking 25% of the full income (₹1000) instead of the remaining ₹700.

**Q4.** In an exam, X secures 58% of the maximum marks and Y secures 105 marks less than X. If the maximum marks are 700, what percentage of marks did Y secure?
`A` 36% · `B` 43% · `C` 48% · `D` 51%
→ **B.** *Targets:* converting an absolute mark difference into a percentage of the total — two steps, not one.

**Q5.** To pass an exam a student needs 36% of the maximum marks. A student scores 198 marks and fails by 36 marks. What are the maximum marks?
`A` 600 · `B` 620 · `C` 650 · `D` 680
→ **C.** *Targets:* reconstructing the total from "pass mark" and "shortfall" (`0.36 × max = 198 + 36`).

**Q6.** Two students appear for an exam. One scores 9 marks more than the other, and his score is 56% of their combined total. Find their marks.
`A` 30, 39 · `B` 33, 42 · `C` 35, 44 · `D` 28, 37
→ **B.** *Targets:* setting up two linear relations from a single "percentage of the sum" statement.

**Q7.** In a class, 120 students are male and 100 are female. 25% of the males and 20% of the females are engineering students. Of these, 20% of the male engineering students and 25% of the female engineering students passed the exam. What percentage of engineering students passed?
`A` 18% · `B` 20% · `C` 22% · `D` 25%
→ **C.** *Targets:* the hardest pattern from Session 12 — a percentage-of-a-percentage applied to two unequal subgroups, then combined as a weighted average, not a plain average. *This is today's hardest warm-up item — expect the lowest score here.*

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–10 min)

Write on the board, nothing else:

> **"A shopkeeper buys a shirt for ₹400 and sells it for ₹500."**

Ask: *"Did he make money? How much? Shout it out."*

Let "₹100!" land. Then ask:

> *"Is ₹100 profit on a ₹400 shirt the same size win as ₹100 profit on a ₹4,000 jacket?"*

Let the room settle on "no" — most will already reach for percentage without being told to.

> *"That instinct is the entire session. ₹400 is what we're about to start calling the **Cost Price**. ₹500 is the **Selling Price**. ₹100 is the **Profit**. And whether ₹100 is a big win or a small one — that's the **Profit%**, and it's always measured against the ₹400, not the ₹500. Every formula in the next twelve minutes is just precise language for the guess you already made in ten seconds."*

Tie back to the warm-up: *"You just spent seven minutes turning percentages of totals into real answers. Today those same skills get a new job — buying and selling."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — extracted deck groups these on one slide ("Terms and Relation"); confirm the live deck's exact slide split before class -->
Covers: Cost Price (C.P), Selling Price (S.P), Marked Price (M.P), Profit (P), Loss (L), Discount (D), Profit Percentage (P%), Loss Percentage (L%), Discount Percentage (D%), and the relations between them.

**Beats to emphasise**

- **Name the six objects first, formula second.** CP = what the seller paid. SP = what the buyer paid the seller. MP = the sticker/tag price before any discount. Keep these three visually separated on the board — most errors later in the session come from mixing up MP and SP.
- **Profit = SP − CP** (when SP > CP); **Loss = CP − SP** (when CP > SP). Say explicitly: *"Profit and Loss are never both possible on the same sale — one transaction is exactly one or the other."*
- **The relation that decides today's misconception:** `Profit% = (Profit / CP) × 100` and `Loss% = (Loss / CP) × 100`. Say it twice, slowly: *"Always Cost Price on the bottom. Never Selling Price."* <!-- placement: inferred — this exact wording is not in the deck's terms slide, but is confirmed by the deck's own hints on later problem slides ("Profit % = Profit/CP × 100", "Loss % = Loss/CP × 100") -->
- Discount (D) and Discount% (D%) are named here but — flag for yourself — **no worked example in this deck exercises Discount.** State the standard relation (`D = MP − SP`, `D% = D/MP × 100`) briefly and move on; don't over-invest time in a term the rest of the session doesn't use. <!-- placement: inferred — Discount formula supplied by standard convention, not shown explicitly in the extracted deck text -->

**Checkpoint (at 22 min)** — cold-call two students:
> *"If Profit = SP − CP, what do you divide by to get Profit% — CP or SP?"*
> **Answer:** CP. `Profit% = (Profit / CP) × 100`. This is deliberately not SP — hold that thought, it comes back hard in Activity 2.

---

## ⚡ Activity 1 — Predict-Then-Solve (22–30 min)

### What this activity is

Students commit out loud to a prediction (profit, loss, or no change) *before* any arithmetic happens, then the class solves the real numbers together. It exposes the gap between gut instinct and the actual relation.

### Why it's here

The very first worked example in this deck is built to break the instinct that "10% profit and 10% loss on equal-priced sales cancel out." Predicting first, then solving, makes the surprise land as a lesson instead of a correction.

### Before class

Have the two problems below ready to write or project. Nothing else needed — no board pre-work.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–1:00 | Read Problem 1 aloud, ask for a prediction | Shout "profit," "loss," or "no gain no loss" |
| 1:00–4:30 | Solve on the board, taking each step from a different student | Compute, watch the reveal |
| 4:30–5:30 | Debrief the surprise | Listen |
| 5:30–8:00 | Problem 2 — quick, live solve | Follow, answer cold-calls |

### Say this (Problem 1)

> *"A man sells two houses for 198 lakhs each. By selling the first house he got a 10% profit, and by selling the second he got a 10% loss. Before we touch a single number — profit, loss, or no gain no loss overall? Hands up for each."*

Take the show of hands. Expect a strong showing for "no gain no loss" — that's the trap.

**Solve it:**
- House 1: SP = 198 lakhs at **10% profit** → CP₁ = 198 / 1.1 = **180 lakhs**
- House 2: SP = 198 lakhs at **10% loss** → CP₂ = 198 / 0.9 = **220 lakhs**
- Total CP = 180 + 220 = **400 lakhs**; Total SP = 198 + 198 = **396 lakhs**
- **Overall: 4 lakhs Loss, 1% Loss**

> *"Same rupee amount sold, same 10%, opposite directions — and it's still a loss. Why? Because the 10% profit was on a smaller CP and the 10% loss was on a bigger CP. Percentages of different bases don't cancel."*

*(Deck hint: "Read line by line and solve it.")*

### Say this (Problem 2)

> *"Quick one. Find the cost price, when the selling price is Rs 40.95 and the gain is 17%."*

**Solve it:** Gain = Profit, so `SP = CP × 1.17` → `CP = 40.95 / 1.17 = **35**`.

### When it goes wrong

| If… | Do this |
|---|---|
| Most predicted "no gain no loss" | Good — that's the design. Don't rush the reveal; let the 400 vs 396 lakhs sit on the board for a few seconds before naming the answer. |
| A student computes `(198×0.1) − (198×0.1) = 0`, "proving" no change | Ask: *"That 10% is 10% of what number?"* Point out both computations used 198 (the SP), not the two different CPs. |
| Problem 2 stalls on "gain = profit?" | Confirm explicitly — the deck flags this exact synonym as a hint. Different word, same relation. |

**Cut rule:** If short on time, drop Problem 2 entirely — the houses problem alone carries the session's core misconception and is worth the full 8 minutes on its own.

---

## Classroom Quiz — not yet available

> Classroom Quiz: not yet available — add once question bank exists for this topic.

**Reallocation:** the 7 minutes this slot would have used are redistributed across the remaining blocks: Slide Block B gains 1 minute, Activity 2 gains 2, Activity 3 gains 1, and Activity 1 above already absorbed 3 (its natural length was closer to 5 minutes). The 60-minute timeline below reflects this — there is no gap in the schedule.

---

## Slide Block B (30–41 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — extracted deck presents this as one "Representation (In short format)" slide; confirm slide boundaries against the live deck -->
Covers: the short-format representation of profit/loss as a single multiplier on CP.

**Beats to emphasise**

- Walk the full derivation exactly as the deck sequences it, one line revealed at a time:
  `SP = CP + Profit%` → `SP = CP + (10% of CP)` → `SP = CP + (10/100 × CP)` → `SP = CP + 0.1 CP` → **`SP = 1.1 CP`**
- Say explicitly: *"Profit% is not a number you add to CP directly. It's a fraction of CP that you add to CP. That middle step — turning 10% into 0.1 × CP — is the whole trick."*
- The deck's fill-in-the-blank line then asks for the same conversion at other percentages. Complete each one live, using the exact method just shown — don't skip to the answer:

| Stated | SP in terms of CP |
|---|---|
| 10% Profit | `SP = 1.1 CP` (shown in the derivation above) |
| 20% Profit | `SP = 1.2 CP` |
| 73% Profit | `SP = 1.73 CP` |
| 10% Loss | `SP = 0.9 CP` |
| 30% Loss | `SP = 0.7 CP` |
| 45% Loss | `SP = 0.55 CP` |

- Name the pattern out loud: *"Profit adds to 1. Loss subtracts from 1. That's it — that's the entire representation."*

**Checkpoint (at 41 min)** — show hands:
> *"Convert 30% Loss into the `SP = ___ CP` form."*
> **Answer:** `SP = 0.7 CP`.

---

## ⚡ Activity 2 — Trace the Table (41–49 min)

### What this activity is

One quick individual solve, then a centerpiece problem solved by prediction-first (again), then a problem built entirely by tracing values through a table on the board — CP and SP for each sub-group of goods, totalled at the end.

### Why it's here

This is where the CP-vs-SP misconception named in Slide Block A gets tested directly, and where students meet a profit/loss problem that requires weighting by quantity rather than averaging percentages.

### Before class

Have the three problems ready. For the third, have a blank 4-row table skeleton ready to fill live: **Group | Count | Total CP | Total SP**.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–1:00 | Setup line, read Problem 1 | Listen |
| 1:00–3:00 | Take the solve from a cold-call | Solve, answer |
| 3:00–3:30 | Read Problem 2, ask for a prediction | Predict out loud |
| 3:30–6:00 | Solve Problem 2 on the board | Watch the reveal |
| 6:00–8:00 | Build the table for Problem 3 live | Call out each cell |

### Problem 1 — quick solve

> *"On selling 17 balls at Rs 720, there is a loss equal to the cost price of 5 balls. The cost price of a ball is: ___"*

**Solve it:** Let CP/ball = `x`. Total CP = `17x`. Loss = `17x − 720 = 5x` → `12x = 720` → **`x = 60`**.

### Problem 2 — the centerpiece (say this)

> *"Find the actual profit (%) when the profit on selling price is 20%. Before you calculate — is the answer 20%, more than 20%, or less than 20%?"*

Take the show of hands. Expect many to say "20%" — that's today's misconception, back for round two.

**Solve it:** *(Deck hint: "Assume a simple value when nothing is given directly.")* Assume **SP = 100**. Profit on SP = 20% → Profit = 20 → **CP = 100 − 20 = 80**. Actual profit% (always on CP) = `20 / 80 × 100` = **25%**.

> *"20% was never the answer — it can't be, because 20% of SP is not the same fraction as 20-of-something is of CP. Profit% always means profit over CP. Say it with me one more time."*

### Problem 3 — Trace the Table

> *"A dealer sold three-fourths of his articles at a gain of 20% and the remaining at cost price. Find the gain (%) earned by him in the whole transaction. Assume the total number of articles is a convenient number — call it out."*

Take a suggestion (e.g. 4, so three-fourths and one-fourth are whole numbers). Build the table live, CP = 100 per article:

| Group | Count | Total CP | Total SP |
|---|---|---|---|
| Sold at 20% gain | 3 | 300 | 360 |
| Sold at cost | 1 | 100 | 100 |
| **Total** | **4** | **400** | **460** |

Gain = 460 − 400 = 60. Gain% = `60 / 400 × 100` = **15%**.

> *"Notice it's not the average of 20% and 0%, which would be 10%. It's weighted — three-quarters of the goods carried the gain, so the answer sits closer to 20% than to 0%."*

### When it goes wrong

| If… | Do this |
|---|---|
| Problem 2 — someone insists 20% is correct | Walk the assumed-SP-=-100 arithmetic slowly on the board; the CP = 80 step is where it clicks. |
| Problem 3 — someone averages 20% and 0% to get 10% | Point at the table: *"Is one-quarter of the goods equal in value to three-quarters? Then why would they count equally?"* |
| Table-building stalls on "why CP = 100 per article" | Clarify: any convenient number works because the answer is a percentage — it cancels out. Offer to redo with CP = 200 if anyone wants proof. |

**Cut rule:** If short on time, drop Problem 1 (the balls quick-solve) — Problems 2 and 3 carry the session's real content and must not be rushed.

---

## ⚡ Activity 3 — Rapid Fire Board Race (49–57 min)

### What this activity is

Split the room into rows or teams. Read one problem at a time; first team with a correct, *explained* answer scores a point. Move fast — this is a closer, not a teaching moment.

### Why it's here

By this point in the session every relation has been taught and drilled once. This activity is pure retrieval speed on three more of the deck's own problems, under mild competitive pressure, right before the exit ticket.

### Before class

Have all three problems ready to reveal one at a time. Decide teams/rows before you start — don't burn race time on logistics.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, assign teams | Listen |
| 0:30–3:00 | Round 1 | Race, answer |
| 3:00–5:30 | Round 2 | Race, answer |
| 5:30–8:00 | Round 3 | Race, answer |

### Say this

> *"Three rounds. I read the problem once. First team to raise a hand with the right answer AND the reason gets the point — a right number with no reason doesn't count. Go."*

### Round 1

> *"A dishonest salesman uses an 800gm weight instead of 1 kg weight. Find his profit percentage if he sells per kilogram at the same price as he buys a kilogram."*

**Answer:** He gets 1000g true weight for the price of what he calls "1kg," then sells 800g labelled as 1kg for that same price. Profit = `(1000 − 800)/800 × 100` = **25%**.

### Round 2

> *"The cost price of 20 articles is the same as the selling price of x articles. If the profit is 25%, then the value of x is:"*

**Answer:** `20 × CP = x × SP`, and `SP = 1.25 CP` → `20 CP = 1.25 CP × x` → `x = 20/1.25` = **16**.

### Round 3

> *"A table was sold at a gain of 10%. Had it been sold for Rs 30 more, the gain would have been 15%. Find the CP of the table."*

**Answer:** Let CP = `x`. `1.10x + 30 = 1.15x` → `30 = 0.05x` → **`x = 600`**.

### When it goes wrong

| If… | Do this |
|---|---|
| One team dominates every round | Rotate which row answers first, or require a different student per round. |
| A team shouts the right number with a wrong reason | No point. Say why out loud — the reasoning is the actual skill being scored. |
| Running long | Drop Round 2 — Rounds 1 and 3 are the more classic, more frequently recurring problem types. |

**Common instructor mistake:** letting the race slow down into full board-worked solutions. Keep each reveal under 60 seconds; the depth already happened in Activities 1 and 2.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — on paper or in chat before anyone leaves:

> A vendor bought toffees at 6 for a rupee. How many must he sell for a rupee to gain 20%?
> **Answer:** 5. *(CP/toffee = 1/6. Required SP/toffee = 1.2 × 1/6 = 1/5, so 5 toffees per rupee.)*

Scan responses on the way out. A wrong answer here usually means the CP-per-unit step was skipped — flag it for a 60-second recap at the start of Session 14.

**Homework**

| Task | Instruction |
|---|---|
| Slide 9 problem | *"If the loss is (1/7)th of S.P, the loss percentage is ___?"* — solve from scratch. **Answer: 12.5%** (`Loss% = Loss/CP × 100`; work CP from the given SP–loss relation first.) |
| Bonus problem A | *"Lohi sold her pendant at a loss of 8%. Had she sold it for 900 more, she would have made a profit of 10%. Find the cost price."* **Answer: 5000.** |
| Bonus problem B | *"A shopkeeper buys some pens. Selling at Rs 13/pen gives a total loss of Rs 150; selling at Rs 15/pen gives a total gain of Rs 100. How many pens did he sell?"* **Answer: 125.** |

Tell them: *"These three were in today's deck but we didn't reach them live. Same relations as everything we did in class — no new formula. Bring your working to Session 14."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Profit% / Loss% is calculated on Selling Price | The "profit on SP" phrasing in Activity 2's centerpiece problem sounds like it's asking for a normal profit% | Assume-SP-=-100 walkthrough in Activity 2, Problem 2 — 20% on SP becomes 25% on CP |
| Two equal, opposite percentages (10% profit, 10% loss) cancel to no net change | Both transactions used the same SP (198 lakhs each), so the percentages *look* symmetric | Activity 1's houses problem — showing the two different CPs (180 and 220 lakhs) that the equal SPs hide |
| A gain% earned on only part of a batch can be averaged with the rate on the rest | "20% and 0%, so somewhere in the middle" feels intuitive | Activity 2's Trace-the-Table — the 3:1 count split visibly outweighs the average |
| `SP = CP + Profit%` means literally adding the percentage number to CP | The formula reads like simple addition until the multiplier step is shown | Slide Block B's full derivation, one line at a time, ending at `SP = 1.1 CP` |
| "I can't solve this, CP/SP isn't given" | Most school problems hand over both values directly | The deck's own hint — "Assume a simple value when nothing is given directly" — demonstrated live in Activity 2 |

---

## Instructor Notes

- **Grounding:** this plan is built entirely from a local text-extraction of `NIAT_Profit and loss.pptx`. There is no platform export for this course yet, so — unlike the Programming Foundations plans — **no unit IDs, question IDs, or quiz-pool counts appear anywhere in this document.** Nothing here should be treated as a live platform reference.
- **Two "Quiz Time" slides exist in the deck (originally slides 10 and 19) with no extractable question text** — they are very likely image-based or interactive quiz widgets that the text extraction cannot see. This plan does **not** treat them as source material and does not invent questions for them; if the live deck reveals real content on those slides when delivered, treat it as a bonus and slot it into Activity 3's cut-rule buffer.
- <!-- placement: inferred --> **Slide grouping is inferred.** The extracted text shows "Terms and Relation" (Slide Block A) and "Representation" (Slide Block B) as single dense slides rather than a clean multi-slide sequence. Confirm the actual slide-by-slide breakdown in the live deck before class and adjust beat timing if the terms and the relations formulas turn out to be on separate slides.
- <!-- placement: inferred --> **Discount / Discount% formulas are not exercised anywhere in this deck's worked examples.** The standard relations (`D = MP − SP`, `D% = D/MP × 100`) are supplied by convention in Slide Block A, not lifted from the source file. Keep that beat brief; don't let it compete for time with content the deck actually tests.
- **Warm-up poll MCQ options are newly authored** (per this course's convention for warm-up polls) — only the underlying word problems and correct answers come from the Session 12 deck (`NIAT_Percentages 2.txt`). Distractors were built to represent the most predictable calculation slip for each problem.
- **The missing Classroom Quiz was reallocated, not skipped over.** Total contact time still sums to 60 minutes with no gap; see the reallocation note between Activity 1 and Slide Block B for exactly where those 7 minutes went. Adjust the split further if your class runs faster or slower through the houses problem in Activity 1 — that's the one beat most likely to overrun.
- **Every numeric answer in every problem above is quoted from the source deck's own "Answer:" lines.** Where a problem required an assumed convenience value (e.g. assumed SP = 100, or a chosen article count for the table), that assumption is flagged inline as the deck's own suggested technique, not an invented data point.
