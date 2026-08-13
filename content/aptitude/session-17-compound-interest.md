# Session 17 — Compound Interest

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Compound Interest — Terms and Formulas, Types of CI, Relation between SI & CI, Pascal's Triangle · **Prerequisite** Session 16 (Simple Interest)
**Session type** Concept lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet — a 5-min quiz slot is reserved but empty for that reason. · **Format** 50-min recalibrated, 2 ALS activities

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT_Compound interest.pptx` |
| Classroom Quiz | not yet available — 5-min slot reserved at end of session, add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define the terms of Compound Interest — Principal (P), Rate (R), Time (T) — and state CI = A − P. *(REMEMBERING)*
2. Explain why CI overtakes SI after the first year even though both start out identical. *(UNDERSTANDING)*
3. Calculate the amount and compound interest for a given principal, rate, and time — including cases where the rate changes from year to year. *(APPLYING)*
4. Distinguish Compounded Per Annum, Compounded Semi-Annually, and Compounded Quarterly, and state their ranking for the same nominal annual rate. *(APPLYING)*
5. Use Pascal's Triangle coefficients to expand (1 + R/100)^T and compute compound interest without repeated long multiplication. *(APPLYING)*
6. Solve for an unknown sum, rate, or installment value using the relationship between CI and SI. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

5 questions on **Session 16 (Simple Interest)**. Newly authored, real numbers drawn from that session's deck. ~45 s each, project the distribution, never name individuals.

**Q1.** In the Simple Interest formula, what does "P" stand for?
`A` Percentage · `B` Principal · `C` Profit · `D` Period
→ **B.**

**Q2.** What is the Session 16 formula for Amount under Simple Interest?
`A` Amount = P × R × T · `B` Amount = P + I · `C` Amount = P × (1 + R/100)^T · `D` Amount = I − P
→ **B.** *If wrong:* students are already reaching for the compound formula — flag it, you'll separate the two in today's Hook.

**Q3.** A man borrowed money at 14% p.a. simple interest. After 3 years he paid Rs. 8400 as interest. What was the principal?
`A` Rs. 15000 · `B` Rs. 18000 · `C` Rs. 20000 · `D` Rs. 24000
→ **C.**

**Q4.** *(MSQ — select all that apply)* Which of the following increase the simple interest earned, all else equal?
`A` Increasing the rate · `B` Increasing the time · `C` Increasing the principal · `D` Compounding it annually
→ **A, B, C.** *Targets:* D is the trap — compounding is not a lever inside the SI formula at all. Note who picks D — you will name that formula in today's Hook.

**Q5.** In how many years will a sum double itself at 11.11% p.a. simple interest?
`A` 4 · `B` 8 · `C` 9 · `D` 16
→ **C.** *Targets:* doubling under SI is linear — worth stating out loud, since today's session is about the case where it isn't.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–9 min)

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

Tie back to **Q4** of the poll: *"Some of you flagged 'compounding' as a way to increase simple interest. You were right to be suspicious of it — it isn't part of that formula at all. It's this."*

---

## Slide Block A (9–17 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — the deck's Terms and Formulas slide names P, R, T and labels "CI = Compound Interest" but the actual equation appears to render as a graphic/equation object. Confirm the on-slide rendering matches before class. -->

Covers: Terms and Formulas → Types of CI (Compounded Per Annum, Compounded Semi-Annually, Compounded Quarterly).

**Beats to emphasise**

- **State the formula explicitly:** Amount `A = P(1 + R/100)^T`, and `CI = A − P`. Write it next to the Hook's table so students see where the 110 and 121 actually came from.
- **The exponent is the whole story.** SI multiplies the same fixed amount by T. CI raises `(1 + R/100)` to the power T.
- **Types of CI — C.P.A, C.S.A, C.Q.** Same nominal annual rate, different compounding frequency. State the deck's own ranking: **C.Q > C.S.A > C.P.A.**
- Don't over-derive *why* C.Q wins yet — ALS Activity 1's problem 4 will make it concrete with numbers.

**Checkpoint (at 17 min)** — 10 s silent think, cold-call:
> *"For the same nominal annual rate, which compounding frequency gives the most interest?"*
> **Answer:** Compounded Quarterly (C.Q). C.Q > C.S.A > C.P.A.

---

## ⚡ ALS Activity 1 — Rapid Fire Board Race (17–24 min)

**ALS format:** Board Race — four real worked problems, split across the room, teams race to post a full solution not just a final number. Chosen as the first activity because students have just seen the formula once, on a slide, and this is the first time they apply it with their own hands, under mild time pressure, before the material goes stale.

**Setup line:**
> *"Four problems, four teams. Rs. 8000, Rs. 40,000, Rs. 6000, Rs. 3000 — every number is real. One runner per team writes your full working on the board, not just the final answer. First team with a fully correct working gets the point."*

**The set**

1. Find the amount due on Rs. 8000 in 2 years if the compound interest rate is 10% for the first year and 12% for the second year.
2. The compound interest on Rs. 40,000 at 6% p.a. is Rs. 4944. Find the period (in years).
3. A man invests Rs. 6000 for two years at a certain rate, compounded annually. At the end of one year it amounts to Rs. 7200. Find the amount at the end of the second year.
4. What will Rs. 3000 amount to in two years if invested at 20% p.a. compound interest, compounded semiannually?

**Answers**

| # | Working | Answer |
|---|---|---|
| 1 | 8000 × 1.10 = 8800 → 8800 × 1.12 = 9856 | **Rs. 9856** |
| 2 | 40000 × (1.06)² = 44944 → CI = 4944 at n = 2 | **2 years** |
| 3 | Year 1 amount 7200 means rate = 20% on 6000 → 7200 × 1.20 = 8640 | **Rs. 8640** |
| 4 | Semiannual rate = 10%, 4 half-year periods → 3000 × (1.10)⁴ | **Rs. 4392.3** |

**When it goes wrong**

| If… | Do this |
|---|---|
| A team averages or adds the two rates in problem 1 | This is the session's core trap. Say explicitly: "You cannot average compound rates — each year compounds on the *previous year's amount*." Redo it live. |
| A team in problem 3 recomputes from the *original* 6000 instead of 7200 | Point out that after year 1, the "principal" for year 2 is whatever the amount actually became. |
| Problem 4 gets solved with T = 2 instead of 4 periods | Semiannual compounding means double the periods, halve the rate per period. |

**Debrief line:**
> *"Every trap today was the same idea: compound interest never resets to the original principal — it always builds on what came just before."*

**Cut rule:** Problems 1 and 3 only if short on time — between them they cover the rate-change trap and the "principal resets each year" idea.

---

## Slide Block B (24–33 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred from deck order — Relation between SI & CI slide is immediately followed by the Pascal's Triangle slide, both reuse the identical example (P = 1000, R = 10% p.a.), confirming they are meant to be taught back-to-back. -->

Covers: Relation between SI & CI (the year-by-year P = 1000, R = 10% p.a. table) → Pascal's Triangle application to compound interest.

**Beats to emphasise**

- **Re-anchor to the Hook's table.** Same P = 1000, R = 10% p.a. example — now go through *why* the numbers came out that way: each year's CI is 10% of the *previous year's amount*, while SI stays a flat 100 every year.
- **Pascal's Triangle is not a separate topic — it's a shortcut for the same exponent.** `(1 + R/100)^T` expands using the binomial coefficients in row T of Pascal's Triangle (1; 1 1; 1 2 1; 1 3 3 1; 1 4 6 4 1; 1 5 10 10 5 1).
- **Prove it with the number they already trust.** Row "1 3 3 1" (T=3): `(1.1)³ = 1 + 0.3 + 0.03 + 0.001 = 1.331`. × 1000 → 1331 — exactly the Hook's total CI amount.

**Checkpoint (at 33 min)** — show hands:
> *"In the Compound Interest amount for Year 1, is the interest the same as Simple Interest, or different?"*
> **Answer:** The same — Rs. 100 either way. They diverge starting Year 2.

---

## ⚡ ALS Activity 2 — Think-Pair-Share: Quiz Time (33–40 min)

**ALS format:** Jigsaw Think-Pair-Share — four real "Quiz Time" problems, one per pair, each pair thinks alone, discusses, then shares with the room. Chosen as the closing activity because these four problems are harder and more varied than ALS Activity 1's — a fractional-time CI problem, a CI−SI difference problem, a cross-formula problem, and an equal-installments loan problem — running all four as one group would rush the harder logic.

**Setup line:**
> *"Four problems, one per pair. Think alone first — two minutes, no talking. Then compare with your partner and agree on one answer between you. When I call your problem number, one of you explains the working to the room."*

**The set**

1. Find the compound interest (reckoned yearly) on Rs. 2400 at 10% p.a. for 2 years 4 months. `A` Rs. 600.80 `B` Rs. 400.80 `C` Rs. 350 `D` Rs. 700
2. The difference between the CI and SI on a certain sum at 10% per annum for 2 years is Rs. 481. Find the sum.
3. The compound interest on a certain sum for 2 years at 10% per annum is Rs. 525. Find the simple interest on the same sum for double the time at half the rate.
4. A sum of Rs. 690 was taken as a loan, to be paid back in 2 equal annual installments at 30% p.a. compounded annually. Find the value of each installment.

**Answers**

| # | Working | Answer |
|---|---|---|
| 1 | Compound for 2 full years: 2400×(1.1)²=2904. Simple interest on the remaining 4 months: 2904×1.03333=3000.8. CI=3000.8−2400 | **A) Rs. 600.80** |
| 2 | For 2 years, CI−SI = P×(R/100)². P×0.01=481 | **Rs. 48100** |
| 3 | CI for 2yrs at 10%=525 → P×0.21=525 → P=2500. SI at 4yrs, 5%: 2500×5×4/100 | **500** |
| 4 | x/1.3 + x/1.3² = 690 → x×1.36095... | **Rs. 507** |

**When it goes wrong**

| If… | Do this |
|---|---|
| Problem 1's pair compounds the 4 months as a fractional exponent | Real trap — correct method compounds whole years, then *simple* interest for the leftover months. State the rule explicitly. |
| Problem 2's pair tries the ordinary SI formula on "481" directly | Redirect: `P(R/100)²` only exists because CI and SI diverge from year 2 — it's what's left after SI cancels out of the CI expansion. |
| Problem 3's pair reuses the CI rate (10%) for the SI part | Reread aloud: "double the time" and "half the rate" are both changes from the original — only the sum (P) carries over. |

**Debrief line:**
> *"Problems 2 and 3 are solved by rereading exactly what changed between the CI part and the SI part — that's the skill, not formula recall."*

**Cut rule:** Problems 1 and 4 only if short on time — a fractional-time CI problem and the installments problem are the formats students are least likely to have met before.

---

## Classroom Quiz (40–45 min) · Reserved — not yet available

No quiz bank exists yet for this Aptitude course (see Resources table). This 5-minute slot is reserved here, at the end of the session and right before the Exit Ticket, so the plan doesn't need restructuring once a quiz bank is added. Until then, run the dropped Pascal's-Triangle verify beat here instead — compute Year 4's amount from row 1-4-6-4-1 and check it against 1331 × 1.10 — or fold the slot into Buffer and end early.

---

## Exit Ticket + Homework (45–48 min)

**Exit ticket** (~1 min) — on paper or in chat before anyone leaves:

> Write the compound interest formula for the amount A, and state which compounding type gives the most interest for the same nominal annual rate.
> **Answer:** A = P(1 + R/100)^T, and CI = A − P. Compounded Quarterly gives the most: C.Q > C.S.A > C.P.A.

Scan responses on the way out. If the ranking direction is wrong or reversed, open Session 18 with a 60-second recap.

**Homework**

| Task | Instruction |
|---|---|
| Re-solve independently | Whichever two of ALS Activity 2's four Quiz Time problems your pair did **not** present live — redo from scratch, full working. |
| Extend the Pascal's Triangle table | Using row `1 6 15 20 15 6 1` (T=6), compute Year 6's amount for the P=1000, R=10% example, and check against Year 5 × 1.10. |
| Review | Be ready to explain, in one sentence, why more frequent compounding produces more interest at the same nominal rate. |

Tell them: *"Next session builds on today's relation between SI and CI. If Activity 2's problems 2 or 3 gave your pair trouble, that's exactly what to redo tonight."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock and want an extension instead of ending early, compute Year 5's amount from row `1 5 10 10 5 1`: `(1.1)^5 = 1.61051` → **Rs. 1610.51**, and check it against Year 4 × 1.10. Never required.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Compound interest grows the same fixed amount every year, like SI | The Hook's own example gives SI = CI = 100 in Year 1 — divergence only appears from Year 2 | The Hook's full 3-year table, and the checkpoint after Slide Block B |
| When the CI rate changes year to year, average or add the two rates instead of compounding sequentially | Muscle memory from SI, where rate and time combine additively | ALS Activity 1, problem 1 |
| The CI−SI difference for 2 years can be found using the ordinary SI formula | It "looks like" a simple interest problem | ALS Activity 2, problem 2 — deriving `P(R/100)²` |
| Same nominal annual rate means same total interest regardless of compounding frequency | "The rate hasn't changed, so why would the answer change?" | Slide Block A's Types of CI ranking, made concrete by ALS Activity 1 problem 4 |
| For "2 years 4 months," you can just compound for the fractional years too | Feels more "consistent" than switching formulas mid-problem | ALS Activity 2, problem 1 — compound whole years, then simple interest for the leftover months |

---

## Instructor Notes

- **This plan is grounded in a local pptx text extraction, not a platform export.** No unit IDs, quiz question IDs, or MCQ/coding practice pools exist for this topic yet.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is the Board Race (core CI mechanics), Activity 2 is Jigsaw Think-Pair-Share (four harder, varied problems). The original Trace-the-Table Pascal's Triangle verification activity is folded into a 2-minute beat inside Slide Block B, with the Year 5 extension demoted to an optional buffer closer.
- <!-- placement: inferred --> **The exact rendering of the CI formula on the Terms and Formulas slide is unconfirmed** — the equation is almost certainly an embedded image object.
- **The source deck's own apostrophe in "Pascal's Triangle" appears as a mojibake character in the raw text extraction.** Present it correctly on slides.
- **The Pascal's Triangle slide reuses the identical P=1000, R=10% example from the Relation between SI & CI slide** — the strongest signal the two are meant to be taught as one continuous idea.
- **All worked-example and Quiz Time answers were independently re-derived and checked against the deck's stated answers.**
