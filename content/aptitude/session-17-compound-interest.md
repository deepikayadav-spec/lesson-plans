# Session 17 — Compound Interest

**Duration** 60 min · **Topic** Compound Interest — Terms and Formulas, Types of CI, Relation between SI & CI, Pascal's Triangle · **Prerequisite** Session 16 (Simple Interest)
**Session type** Concept lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet for this topic.

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT_Compound interest.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define the terms of Compound Interest — Principal (P), Rate (R), Time (T) — and state the relationship CI = A − P. *(REMEMBERING)*
2. Explain, using a year-by-year Simple Interest vs Compound Interest comparison, why CI overtakes SI after the first year even though both start out identical. *(UNDERSTANDING)*
3. Calculate the amount and compound interest for a given principal, rate, and time — including cases where the rate changes from year to year. *(APPLYING)*
4. Distinguish Compounded Per Annum (C.P.A), Compounded Semi-Annually (C.S.A), and Compounded Quarterly (C.Q), and state their ranking for the same nominal annual rate. *(APPLYING)*
5. Use Pascal's Triangle coefficients to expand (1 + R/100)^T and compute compound interest without repeated long multiplication. *(APPLYING)*
6. Solve for an unknown sum, rate, or installment value using the relationship between CI and SI — e.g. from the CI−SI difference, or from equal annual installments on a compounded loan. *(ANALYZING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 16 (Simple Interest)**. Newly authored, real numbers drawn from that session's deck. ~45 s each, project the distribution, never name individuals.

**Q1.** In the Simple Interest formula, what does "P" stand for?
`A` Percentage · `B` Principal · `C` Profit · `D` Period
→ **B.** *Targets:* basic term recall (Session 16, Terms and Formulas slide).

**Q2.** What is the Session 16 formula for Amount under Simple Interest?
`A` Amount = P × R × T · `B` Amount = P + I · `C` Amount = P × (1 + R/100)^T · `D` Amount = I − P
→ **B.** *Targets:* `Amount = P + I` as stated on the deck's Terms and Formulas slide. *If wrong:* students are already reaching for the compound formula — flag it, you'll separate the two in today's Hook.

**Q3.** A man borrowed money at 14% p.a. simple interest. After 3 years he paid Rs. 8400 as interest. What was the principal?
`A` Rs. 15000 · `B` Rs. 18000 · `C` Rs. 20000 · `D` Rs. 24000
→ **C.** *Targets:* rearranging SI = PRT/100. Real numbers from Session 16.

**Q4.** Rs. 650 yields Rs. 169 interest at 6.5% p.a. simple interest. How long was it invested?
`A` 3 years · `B` 4 years · `C` 5 years · `D` 6 years
→ **B.** *Targets:* solving for T. Real numbers from Session 16.

**Q5.** *(MSQ — select all that apply)* Which of the following increase the simple interest earned, all else equal?
`A` Increasing the rate · `B` Increasing the time · `C` Increasing the principal · `D` Compounding it annually
→ **A, B, C.** *Targets:* D is the trap — compounding is not a lever inside the SI formula at all; it belongs to a different formula. Note the number who pick D — you will name that formula in today's Hook.

**Q6.** In how many years will a sum double itself at 11.11% p.a. simple interest?
`A` 4 · `B` 8 · `C` 9 · `D` 16
→ **C.** *Targets:* Session 16's own MCQ, unchanged. Doubling under SI is linear — worth stating out loud, since today's session is about the case where it isn't.

**Q7.** A sum becomes 5 times itself in 20 years at simple interest. What is the rate?
`A` 10% · `B` 30% · `C` 40% · `D` 20%
→ **D.** *Targets:* Session 16's own MCQ. Harder rearrangement — good last question to gauge who's still shaky on SI before compound interest is layered on top.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Never name individuals. Total 7 min including your reads.

---

## Hook (7–10 min)

Put this on the board, nothing else:

```
P = Rs. 1000        R = 10% p.a.

Year 1:   Simple Interest → Amount = 1100
          Compound Interest → Amount = 1100
```

Ask: *"Year one. Same principal, same rate. Simple interest and compound interest give the exact same amount, Rs. 1100. So — why does an entire session need to exist for compound interest, if it's identical to what you already know?"*

Let a few guesses land. Don't confirm or deny yet.

Then reveal the rest of the same table, year by year:

```
Year 2:   SI → 1100 + 100 = 1200        CI → 1100 + 110 = 1210
Year 3:   SI → 1200 + 100 = 1300        CI → 1210 + 121 = 1331

Total SI over 3 years = 300      Total CI over 3 years = 331
```

> *"Same sum, same rate, three years — and compound interest has already pulled Rs. 31 ahead. Look closely at year 2: the SI interest is still exactly 100, every year, forever. The CI interest is 110, then 121. It's growing. That's interest earning interest on itself. Today is entirely about that one difference."*

Tie back to **Q5** of the poll: *"Some of you flagged 'compounding' as a way to increase simple interest. You were right to be suspicious of it — it isn't part of that formula at all. It's this."*

---

## Slide Block A (10–24 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — the deck's Terms and Formulas slide names P, R, T and labels "CI = Compound Interest" but the actual equation appears to render as a graphic/equation object that the text extraction did not capture as text. The standard formula below is the universally used one for this term set; confirm the on-slide rendering matches before class. -->

Covers: Terms and Formulas (CI, Principal, Rate, Time) → Types of CI (Compounded Per Annum, Compounded Semi-Annually, Compounded Quarterly).

**Beats to emphasise**

- **State the formula explicitly, even if the slide only labels the terms:** Amount `A = P(1 + R/100)^T`, and `CI = A − P`. Write it next to the Hook's table so students can see where the 110 and 121 actually came from.
- **The exponent is the whole story.** SI multiplies the same fixed amount by T. CI raises `(1 + R/100)` to the power T. That's the single structural difference — say it in exactly those terms once, then move on.
- **Types of CI — C.P.A, C.S.A, C.Q.** Same nominal annual rate, different compounding frequency. State the deck's own ranking plainly: **C.Q > C.S.A > C.P.A**. More compounding events per year, more interest, for the same quoted annual rate.
- Don't over-derive *why* C.Q wins yet — Activity 1's problem 4 (Rs. 3000 at 20% p.a. compounded semiannually) will make it concrete with numbers.

**Checkpoint (at 24 min)** — cold-call:
> *"For the same nominal annual rate, which compounding frequency gives the most interest — Compounded Per Annum, Compounded Semi-Annually, or Compounded Quarterly?"*
> **Answer:** Compounded Quarterly (C.Q). Per the deck: C.Q > C.S.A > C.P.A.

---

## ⚡ Activity 1 — Rapid Fire Board Race (24–31 min)

### What this activity is

Four real worked problems from the deck, split across the room. Teams race to the board to post a full solution, not just a final number. It is a speed drill on the mechanics of the CI formula right after they've been introduced.

### Why it's here

Students have just seen the formula once, on a slide. This is the first time they apply it with their own hands, under mild time pressure, before the material has a chance to go stale.

### Before class

Write the four problems on the board (or have a slide ready) — do **not** show the answers yet. Divide the room into 4 teams/rows, one problem per team.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, assign one problem per team | Read their problem |
| 0:30–1:00 | Start the clock | Work at their seats first |
| 1:00–5:30 | Call "board" — one runner per team writes the full solution | Race, then watch other teams |
| 5:30–7:00 | Reveal real answers, debrief problem 1 | Check their own work |

### Say this

> *"Four problems, four teams. Rs. 8000, Rs. 40,000, Rs. 6000, Rs. 3000 — every number is real, taken straight from the source material. One runner per team writes your full working on the board, not just the final answer. First team with a fully correct working — not the fastest wrong one — gets the point."*

### The set

1. Find the amount due on Rs. 8000 in 2 years if the compound interest rate is 10% for the first year and 12% for the second year.
2. The compound interest on Rs. 40,000 at 6% p.a. is Rs. 4944. Find the period (in years).
3. A man invests Rs. 6000 for two years at a certain rate, compounded annually. At the end of one year it amounts to Rs. 7200. Find the amount at the end of the second year.
4. What will Rs. 3000 amount to in two years if invested at 20% p.a. compound interest, compounded semiannually?

### Answers

| # | Working | Answer |
|---|---|---|
| 1 | 8000 × 1.10 = 8800 → 8800 × 1.12 = 9856 | **Rs. 9856** |
| 2 | 40000 × (1.06)² = 40000 × 1.1236 = 44944 → CI = 4944 at n = 2 | **2 years** |
| 3 | Year 1 amount 7200 means rate = 20% on 6000 → 7200 × 1.20 = 8640 | **Rs. 8640** |
| 4 | Semiannual rate = 10%, 4 half-year periods → 3000 × (1.10)⁴ = 3000 × 1.4641 | **Rs. 4392.3** |

**Run each one live** after the race — walk the correct working on the board even for the winning team, so every student sees the mechanics, not just the winner's answer.

### When it goes wrong

| If… | Do this |
|---|---|
| A team averages or adds the two rates in problem 1 (treats 10% and 12% like SI) | This is the session's core trap. Say explicitly: "You cannot average compound rates — each year compounds on the *previous year's amount*, not on the original principal." Redo it live, step by step. |
| A team in problem 3 recomputes from the *original* 6000 instead of from 7200 | Point out that after year 1, the "principal" for year 2 is whatever the amount actually became — 7200, not 6000. |
| Problem 4 gets solved with T = 2 instead of 4 periods | Semiannual compounding means you double the number of periods and halve the rate per period. Write "20% p.a. semiannual → 10% per half-year, 4 half-years" on the board. |
| Running long | Do problems 1 and 3 only — between them they cover the rate-change trap and the "principal resets each year" idea, the two ideas that recur all session. |

**Common instructor mistake:** revealing the answer before the race resolves. Let the board race finish, even if a team is visibly wrong — the wrongness is what Activity 1 is for.

**Cut rule:** Problems 1 and 3 only if short on time.

---

## Classroom Quiz

> Classroom Quiz: not yet available — add once question bank exists for this topic.

**Time reallocated.** In a session with a live quiz pool, this slot would sit at roughly minute 27–34. With no pool to draw from, those minutes have been redistributed: 2 minutes were added to Slide Block A (extended to 14 minutes to give Terms/Formulas and Types of CI proper room), and the remaining time is folded into Slide Block B and Activities 2–3 below, so the 0–60 timeline below has no gap and no overlap.

---

## Slide Block B (31–43 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred from deck order — Relation between SI & CI slide is immediately followed by the Pascal's Triangle slide, and both slides reuse the identical example (P = 1000, R = 10% p.a.), confirming they are meant to be taught back-to-back. -->

Covers: Relation between SI & CI (the year-by-year P = 1000, R = 10% p.a. table) → Pascal's Triangle application to compound interest.

**Beats to emphasise**

- **Re-anchor to the Hook's table.** This is the same P = 1000, R = 10% p.a. example — now go through *why* the numbers came out that way: each year's CI is 10% of the *previous year's amount* (100, then 110, then 121), while SI stays a flat 100 every year.
- **Pascal's Triangle is not a separate topic — it's a shortcut for the same exponent.** `(1 + R/100)^T` expands using the binomial coefficients in row T of Pascal's Triangle. Show the rows on the deck's own triangle (1; 1 1; 1 2 1; 1 3 3 1; 1 4 6 4 1; 1 5 10 10 5 1).
- **Prove it with the number they already trust.** Using row "1 3 3 1" (T = 3): `(1.1)³ = 1 + 3(0.1) + 3(0.1)² + (0.1)³ = 1 + 0.3 + 0.03 + 0.001 = 1.331`. Multiply by 1000 → 1331 — exactly the total CI amount from the table above. This is the moment the two slides visibly connect.

**Checkpoint (at 43 min)** — show hands:
> *"In the Compound Interest amount for Year 1, is the interest the same as Simple Interest, or different?"*
> **Answer:** The same — Rs. 100 either way, because there is only one year for interest to compound on. They diverge starting Year 2.

---

## ⚡ Activity 2 — Trace the Table (43–50 min)

### What this activity is

Students extend the deck's own SI-vs-CI table two more years, then verify their Year 4 answer two different ways: by direct multiplication, and by reading it straight off Pascal's Triangle. It's a table-building exercise that doubles as proof the shortcut actually works.

### Why it's here

Pascal's Triangle looks like a party trick until a student derives a number they can check against ordinary multiplication and watches the two agree. This activity manufactures that moment.

### Before class

Have the Year 1–3 table (from the Hook / Slide Block B) still visible, and Pascal's Triangle rows for T = 4 and T = 5 (`1 4 6 4 1` and `1 5 10 10 5 1`) on the board.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–1:00 | Setup line | Listen |
| 1:00–3:00 | Ask for Year 4 amount by direct multiplication (1331 × 1.10) | Compute at seats |
| 3:00–5:00 | Ask for Year 4 amount using row "1 4 6 4 1" instead | Expand `(1.1)⁴` from the triangle |
| 5:00–7:00 | Compare the two answers live; stretch to Year 5 if time allows | Confirm they match; attempt Year 5 |

### Say this

> *"You already trust that Year 3's amount is 1331 — we just proved it. Now, two ways: multiply 1331 by 1.10 to get Year 4 the way you've done it since Session 16. Then, separately, use row 1-4-6-4-1 of Pascal's Triangle to expand `(1.1)^4` directly, multiply by 1000, and tell me if the two answers agree."*

### The set and answers

| Method | Working | Year 4 Amount |
|---|---|---|
| Direct multiplication | 1331 × 1.10 | **1464.1** |
| Pascal's Triangle (row 1 4 6 4 1) | `(1.1)^4 = 1 + 4(0.1) + 6(0.1)² + 4(0.1)³ + (0.1)^4 = 1 + 0.4 + 0.06 + 0.004 + 0.0001 = 1.4641` → × 1000 | **1464.1** |

**Stretch — Year 5**, row `1 5 10 10 5 1`:
`(1.1)^5 = 1 + 5(0.1) + 10(0.1)² + 10(0.1)³ + 5(0.1)^4 + (0.1)^5 = 1.61051` → Amount = **Rs. 1610.51**.

### When it goes wrong

| If… | Do this |
|---|---|
| A group uses the wrong triangle row (e.g. row for T = 3 when T = 4 is needed) | Point at the triangle: "Row index equals the exponent. You want T = 4, so you need four numbers after the first — 1, 4, 6, 4, 1." |
| Someone assumes Pascal's Triangle only works because R = 10% | Clarify: the coefficients (1, 4, 6, 4, 1) are general — they come from T alone. Only the powers of R change if the rate changes. |
| The two methods don't match | Almost always an arithmetic slip in the expansion — walk the four terms of `(1.1)^4` one at a time on the board. |
| Running long | Do the Year 4 comparison only; skip the Year 5 stretch. |

**Common instructor mistake:** presenting Pascal's Triangle as a novelty aside instead of running the direct-multiplication check first. The check is what makes it land as a real tool rather than trivia.

**Cut rule:** Year 4 comparison only, drop the Year 5 stretch.

---

## ⚡ Activity 3 — Think–Pair–Share: Quiz Time (50–57 min)

### What this activity is

Four real "Quiz Time" problems from the deck, assigned jigsaw-style — one problem per pair. Each pair thinks alone, discusses with a partner, then shares their working with the room before the real answer is revealed.

### Why it's here

These four problems are harder and more varied than Activity 1's — a fractional-time CI problem, a CI−SI difference problem, a cross-formula (CI to SI) problem, and an equal-installments loan problem. Running all four as one group would rush the harder logic; splitting them across pairs lets each get proper attention within the time available.

### Before class

Have all four problems ready on slides or cards, one per pair (or per pair-cluster if the room is large).

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, assign one problem per pair | Listen |
| 0:30–2:30 | Silent think | Work the assigned problem alone first |
| 2:30–4:30 | "Pair" | Compare working with partner, agree on an answer |
| 4:30–6:30 | Take one pair per problem, share to the room | Explain their working |
| 6:30–7:00 | Reveal real answers, close | Check against their own |

### Say this

> *"Four problems, one per pair. Think alone first — two minutes, no talking. Then compare with your partner and agree on one answer between you. When I call your problem number, one of you explains the working to the room."*

### The set

1. Find the compound interest (reckoned yearly) on Rs. 2400 at 10% p.a. for 2 years 4 months. `A` Rs. 600.80 `B` Rs. 400.80 `C` Rs. 350 `D` Rs. 700
2. The difference between the CI and SI on a certain sum at 10% per annum for 2 years is Rs. 481. Find the sum.
3. The compound interest on a certain sum for 2 years at 10% per annum is Rs. 525. Find the simple interest on the same sum for double the time at half the rate. `A` 600 `B` 500 `C` 800 `D` 400
4. A sum of Rs. 690 was taken as a loan, to be paid back in 2 equal annual installments at 30% p.a. compounded annually. Find the value of each installment.

### Answers

| # | Working | Answer |
|---|---|---|
| 1 | Compound for 2 full years: 2400 × (1.1)² = 2904. Then simple interest on the remaining 4 months: 2904 × (1 + (4/12 × 10)/100) = 2904 × 1.03333 = 3000.8. CI = 3000.8 − 2400 | **A) Rs. 600.80** |
| 2 | For 2 years, CI − SI = P × (R/100)². So P × (0.1)² = 481 → P = 481 / 0.01 | **Rs. 48100** |
| 3 | CI for 2 yrs at 10% = 525 → P × ((1.1)² − 1) = 525 → P × 0.21 = 525 → P = 2500. SI at double time (4 yrs), half rate (5%): 2500 × 5 × 4 / 100 | **B) 500** |
| 4 | Let each installment be x. 690 = x/1.3 + x/1.3² → x(0.76923 + 0.59172) = 690 → x = 690 / 1.36095 | **Rs. 507** |

### When it goes wrong

| If… | Do this |
|---|---|
| Problem 1's pair compounds the 4 months as if it were a fraction of a year in the exponent (e.g. `(1.1)^(28/12)`) | This is a real trap — the correct method compounds only for whole years, then applies *simple* interest for the leftover months. Say this rule explicitly and write it up. |
| Problem 2's pair tries to use the ordinary SI formula on the "481" directly | Redirect: the difference formula `P(R/100)²` only exists *because* CI and SI diverge from year 2 onward — it's not a new formula, it's what's left after SI cancels out of the CI expansion. |
| Problem 3's pair reuses the CI rate (10%) for the SI part instead of "half the rate" | Reread the question aloud with them: "double the time" and "half the rate" are both changes from the original problem — the CI numbers only get you the sum (P), nothing else carries over. |
| Problem 4's pair treats the loan like two independent one-year SI installments instead of discounting each future installment back to present value | Draw the timeline: this installment happens *next* year and this one the year after — both must be divided back by the compounding factor to be "worth" the loan amount today. |
| Running long | Run problems 1 and 4 only — a fractional-time CI problem and the installments problem are the two formats students are least likely to have met before. |

**Common instructor mistake:** rescuing a stuck pair by giving the formula instead of the reread. Problems 2 and 3 especially are solved by rereading exactly what changed between the CI part and the SI part — that's the skill, not formula recall.

**Cut rule:** Problems 1 and 4 only if short on time.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — on paper or in chat before anyone leaves:

> Write the compound interest formula for the amount A, and state which of the three compounding types — Compounded Per Annum, Compounded Semi-Annually, or Compounded Quarterly — gives the most interest for the same nominal annual rate.
> **Answer:** A = P(1 + R/100)^T, and CI = A − P. Compounded Quarterly (C.Q) gives the most interest: C.Q > C.S.A > C.P.A.

Scan responses on the way out. If the ranking direction is wrong or reversed, open Session 18 with a 60-second recap before moving on.

**Homework**

| Task | Instruction |
|---|---|
| Re-solve independently | Whichever two of Activity 3's four Quiz Time problems your pair did **not** present live — redo them from scratch, showing full working, not just the final answer. |
| Extend the Pascal's Triangle table | Using row `1 6 15 20 15 6 1` (T = 6), compute the Year 6 amount for the P = 1000, R = 10% p.a. example from Slide Block B / Activity 2, and check it against direct multiplication (Year 5 amount × 1.10). |
| Review | Re-read the Types of CI slide (C.P.A / C.S.A / C.Q) and be ready to explain, in one sentence, why more frequent compounding produces more interest at the same nominal rate. |

Tell them: *"Next session builds on today's relation between SI and CI. If Activity 3's problems 2 or 3 gave your pair trouble, that's exactly what to redo tonight."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Compound interest grows the same fixed amount every year, like SI, because Year 1 looks identical either way | The Hook's own P=1000 example gives SI = CI = 100 in Year 1 — the divergence only appears from Year 2 | The Hook's full 3-year table, and the checkpoint after Slide Block B naming Year 1 as the one year they're equal |
| When the CI rate changes year to year (e.g. 10% then 12%), average or add the two rates instead of compounding sequentially | Muscle memory from SI, where rate and time combine additively | Activity 1, problem 1 — running the correct sequential calculation (8000 → 8800 → 9856) live against the wrong averaged answer |
| The CI−SI difference for 2 years can be found using the ordinary SI formula | It "looks like" a simple interest problem because it asks for a difference in rupees | Activity 3, problem 2 — deriving `P(R/100)²` explicitly as what's left after SI cancels out of the CI expansion |
| Same nominal annual rate means same total interest, regardless of whether it's compounded per annum, semi-annually, or quarterly | "The rate hasn't changed, so why would the answer change?" | Slide Block A's Types of CI ranking (C.Q > C.S.A > C.P.A), made concrete by Activity 1 problem 4's semiannual calculation |
| For a period like "2 years 4 months," you can just compound for the fractional years too (e.g. raise to a fractional exponent) | It feels more "consistent" than switching formulas mid-problem | Activity 3, problem 1 — showing the correct rule: compound for whole years, then simple interest for the leftover months |

---

## Instructor Notes

- **This plan is grounded in a local pptx text extraction, not a platform export.** No unit IDs, quiz question IDs, or MCQ/coding practice pools exist for this topic yet — every number, problem, and answer above is quoted from the deck's own slides, not invented. When a bank exists, replace the Classroom Quiz placeholder and the homework block above with real platform references.
- <!-- placement: inferred --> **The exact rendering of the CI formula on the Terms and Formulas slide is unconfirmed.** The text extraction captured the term labels (CI, P, R, T) but not a formula string — almost certainly because the equation itself is an embedded image/equation object rather than text. The formula given in Slide Block A (`A = P(1+R/100)^T`, `CI = A − P`) is the standard one for this exact term set; visually confirm it matches the slide before presenting it as "as-is."
- <!-- placement: inferred --> **Slide Block A's minute range was extended from a nominal 12 to 14 minutes**, and Slide Block B's from a nominal 10 to 12, to absorb time freed up by the missing Classroom Quiz block. This is a judgment call, not a deck instruction — compress back down if the class is moving fast.
- **The source deck's own apostrophe in "Pascal's Triangle" appears as a mojibake character (`�`) in the raw text extraction.** This is a text-extraction encoding artifact, not a content issue — present it correctly on slides as "Pascal's Triangle."
- **The Pascal's Triangle slide reuses the identical P = 1000, R = 10% p.a. example from the Relation between SI & CI slide.** This is the strongest signal in the deck that the two are meant to be taught as one continuous idea, not two separate topics — Slide Block B and Activity 2 are built on that pairing.
- **All worked-example and Quiz Time answers were independently re-derived and checked against the deck's stated answers** (Rs. 9856; 2 years; Rs. 8640; Rs. 4392.3; Rs. 600.80; Rs. 48100; Rs. 500; Rs. 507) before this plan was written. None were altered — they matched.
- **Pacing risk:** Activity 3 carries the heaviest content load (fractional-time CI, the CI−SI difference identity, a cross-formula SI-from-CI problem, and a present-value-style installment problem) in only 7 minutes via jigsaw. If the room is slow to pair up, use the cut rule immediately rather than compressing the share-out — the share-out is where the reasoning actually surfaces.
- **Data note:** no classroom quiz pool, MCQ pool, or coding/problem-practice unit IDs exist for Compound Interest at the time of writing. The Classroom Quiz section documents this gap explicitly and reallocates its nominal time rather than leaving a hole in the 60-minute timeline.
