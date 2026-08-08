# Session 14 — Company-Specific MCQs: Percentages & Profit/Loss

**Duration** 60 min · **Topic** Company-Specific MCQs — Percentages & Profit/Loss (solved-problem consolidation) · **Prerequisite** Sessions 10–13 (Basics of Percentages through Profit & Loss)
**Session type** Consolidation / review lecture. No new concept is introduced — this session applies percentage identities and profit-loss methods from Sessions 10–13 to ten real placement-test-style questions. No classroom quiz bank, MCQ pool, or coding-practice unit IDs exist yet for this topic.

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `3) NIAT_CSMCQ'S_Percentages_Profit & Loss.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Apply the CP–SP percentage identities (SP = CP × (1 ± %), and the "assume CP = 1" trick) to solve gain/loss-percentage questions without needing real currency values. *(APPLYING)*
2. Apply the successive-percentage-change shortcut (a + b + ab/100) to find the net effect of two back-to-back percentage changes — e.g. a price cut and a sales rise, or two chained discounts — in one step. *(APPLYING)*
3. Solve multi-step "percent more/less than" chains (e.g. Ram → Sham → Priya → Charan) by converting each relation into a multiplier and working backward from the one known value. *(APPLYING)*
4. Apply the "value of 1%" shortcut — find what 1% of the unknown equals, then scale — to skip solving a full equation on percentage-difference questions. *(APPLYING)*
5. Evaluate, for a given placement-style question, which solving path — direct equation, assumed-value shortcut, or per-1% scaling — is fastest, and justify the choice. *(EVALUATING)*
6. Analyze why "equal SP with equal ±% profit and loss" and "successive % changes" problems cannot be solved by simply adding or averaging the percentages, and identify the compounding term the naive approach misses. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 13 (0–7 min)

7 questions on **Session 13 (Profit & Loss)**. Newly authored options around the deck's own real numbers; every number below is taken directly from that deck. ~45 s each, project the distribution, never name individuals.

**Q1.** In Profit & Loss shorthand, if an article is sold at a 20% profit, which expresses SP correctly in terms of CP?
`A` SP = CP + 20 · `B` SP = 1.2 × CP · `C` SP = 0.8 × CP · `D` SP = CP − 20
→ **B.** *Targets:* SP = CP(1 + profit%), straight from Session 13's "Representation" slide. *Misconception:* treating "20%" as a flat 20 rupees (A) instead of a fraction of CP.

**Q2.** A man sells two houses for Rs. 198 lakhs each — one at a 10% profit, the other at a 10% loss. What is his overall result?
`A` No profit, no loss · `B` 1% profit · `C` 1% loss · `D` 2% loss
→ **C.** *Real numbers:* CP totals Rs. 400 lakh, SP totals Rs. 396 lakh, loss = Rs. 4 lakh = 1%. *Targets:* equal-SP-equal-%profit/loss always nets to a loss, never breakeven. *Misconception (A):* assuming +10% and −10% cancel exactly.

**Q3.** Selling price of an item is Rs. 40.95 at a gain of 17%. What is its cost price?
`A` Rs. 33.95 · `B` Rs. 35 · `C` Rs. 47.91 · `D` Rs. 34
→ **B.** CP = SP ÷ (1 + gain%) = 40.95 ÷ 1.17 = 35. *Misconception (A):* subtracting 17% of the SP from the SP instead of dividing.

**Q4.** If a loss is exactly (1/7) of the selling price, what is the loss percentage — on cost price?
`A` 14.3% · `B` 12.5% · `C` 16.7% · `D` 8%
→ **B.** SP = (7/8)CP, so Loss = (1/8)CP = 12.5%. *Misconception (A):* reading 1/7 as ≈14.3% directly and forgetting the fraction is of SP, not CP — loss % must always land on CP as the base.

**Q5.** A trader says "20% profit" but means 20% of the *selling* price, not the cost price. What is the actual profit percentage, relative to CP?
`A` 20% · `B` 16.7% · `C` 25% · `D` 24%
→ **C.** If SP = 100, profit = 20 (of SP) → CP = 80 → actual profit% = 20/80 × 100 = 25%. *Targets:* profit-on-SP vs profit-on-CP — Session 13's own "What is Actual Profit?" hint. This exact distinction resurfaces in today's session.

**Q6 (MSQ — select all that are true).** A dealer sells 3/4 of his articles at a 20% gain and the rest at cost price. Which statements are correct?
`A` Assuming total articles = x, with CP per article = 1, is a valid way to start · `B` Overall gain % is simply the average of 20% and 0%, i.e. 10% · `C` Overall gain % works out to 15% · `D` Overall gain % is 20%, same as the discounted portion
→ **A and C.** *Misconception (B):* naive averaging of two percentages when the two portions are weighted 3:1 — weighted quantities never average like that.

**Q7.** A dishonest trader uses an 800 g weight while claiming to sell a full 1 kg, at the same price he pays for a genuine 1 kg. What is his profit percentage?
`A` 20% · `B` 25% · `C` 12.5% · `D` 200%
→ **B.** Profit% = shortage ÷ what he actually gave × 100 = 200/800 × 100 = 25%. *Misconception (A):* computing 200/1000 (shortage over the claimed weight) instead of 200/800 (shortage over what was actually handed over) — profit % is always on what was actually spent, never on the claim.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–10 min)

Put this on screen, nothing else, no context, no hint column:

> Rohit Sharma scored 110 runs, including 3 boundaries and 8 sixes. By running between the wickets, what percentage of his total score did he make?
> `A` 54.50% · `B` 45.45% · `C` 58% · `D` 50%

Say: *"Seventy-five seconds. Silent, no talking, no calculator beyond what you can do on paper. This is question one of a real company-specific placement set on Percentages — solve it cold, the way you will on test day."*

Run a visible 75-second timer. At time, take a show of hands per option — do not reveal the answer yet.

> *"Hold that answer. This isn't a made-up example — it's literally question one of a real company placement Percentages section. Today we are not learning anything new. Sessions 10 through 13 already gave you every method you need — chain percentages, successive changes, CP–SP identities. Today is ten of these, back to back, exactly the way they'll show up on test day, plus the fastest way to each one."*

Move straight into Slide Block A, which opens by resolving this exact question.

---

## Slide Block A (10–22 min) — DELIVER AS-IS

Covers Company-Specific Questions 1–5 from the deck, each with its real worked solution. For each: state the question, reveal the real answer, then give the fastest method.

**Q1 — Rohit Sharma, 110 runs, 3 boundaries, 8 sixes.** *(resolves the Hook)*
Options: 54.50% · 45.45% · 58% · 50% → **Answer: 45.45%**

- Runs off the bat: (3 × 4) + (8 × 6) = 60. Runs by running = 110 − 60 = 50. Percentage = 50/110 × 100 = 45.45%.
- Beat: compute total boundary-and-six runs in **one** line (12 + 48 = 60), then subtract once — don't subtract each type separately, that's where the arithmetic slips.

**Q2 — Exam of 500 marks. Ram 10% less than Sham; Sham 25% more than Priya; Priya 20% less than Charan. Ram = 360. What % of the total did Charan score?**
**Answer: 80%**

- Convert every relation to a multiplier and chain **backward** from the one known value: Sham = 360 ÷ 0.9 = 400. Priya = 400 ÷ 1.25 = 320. Charan = 320 ÷ 0.8 = 400. Charan% = 400/500 × 100 = 80%.
- Beat: always *divide* by the multiplier of the person described as "X% less/more than" the next name, moving one direction through the chain — this avoids setting up three separate simultaneous equations.

**Q3 — Argentina: population 294,000; men 150,000; 53% of total population literate; 98% of men literate. What % of women are literate?**
**Answer: 6.125%**

- Women = 294,000 − 150,000 = 144,000. Total literates = 53% × 294,000 = 155,820. Male literates = 98% × 150,000 = 147,000. Female literates = 155,820 − 147,000 = 8,820. % = 8,820/144,000 × 100 = 6.125%.
- Beat: work in absolute head-counts (literates), not percentage points — subtracting two real counts is faster and safer than trying to combine percentages of different bases.

**Q4 — Ram picks a number. The difference between 78% and 59% of it is 323. What is 62% of it?**
Options: 1037 · 1178 · 1054 · None of the above → **Answer: 1054**

- 78% − 59% = 19%, and that 19% equals 323. So 1% = 323 ÷ 19 = 17. Then 62% = 17 × 62 = 1054.
- Beat: this "value of 1%" trick turns a percentage-*difference* question into one division plus one multiplication — much faster than solving 0.78x − 0.59x = 323 for x (x = 1700) and then computing 0.62x separately. Same answer, one fewer step.

**Q5 — Samsung cuts refrigerator prices by 25%; sales rise 20%. What happens to total revenue?**
Options: Increased by 20% · Increased by 10% · Decreased by 10% · Decreased by 20% → **Answer: Decreased by 10%**

- Net % change = a + b + (ab/100), with a = −25, b = +20: −25 + 20 + (−25 × 20/100) = −25 + 20 − 5 = **−10%**.
- Beat: never simply add the two percentages (−25 + 20 = −5% is wrong). The cross-term (ab/100) is the piece students forget, and it's exactly what turns a naive "−5%" into the real "−10%".

**Checkpoint (at 22 min)** — cold-call two students:
> *"Using Q4's 'value of 1%' shortcut: if 19% of a number is 323, what's 1% of it — and what's 62%?"*
> **Answer:** 1% = 17. 62% = 17 × 62 = 1054.

---

## ⚡ Activity 1 — 60-Second Solve, Then I Reveal (22–29 min)

### What this activity is

Two more of the deck's own questions go up on screen, one at a time. Students get 60 seconds of silent, individual solving — no talking, no group work — then commit to an answer by a show of hands before you reveal the real worked answer and the one-line reasoning. Mirrors the pressure of the Hook.

### Why it's here

After 12 minutes watching you solve, students need to solve cold themselves before the next block of solutions lands. Framing it as "beat the reveal" keeps it from feeling like a pause in the lecture.

### Before class

Nothing to build — both questions are Company-Specific Qs 6 and 8, straight from the deck.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:15 | Setup line, reveal Q6 | Listen |
| 0:15–1:15 | Silent timer (60 s) | Solve alone, commit to an answer |
| 1:15–1:45 | Take the show of hands, reveal answer + reasoning | Check their own work |
| 1:45–2:00 | Reveal Q8 | Listen |
| 2:00–3:00 | Silent timer (60 s) | Solve alone, commit to an answer |
| 3:00–3:30 | Take the show of hands, reveal answer + reasoning | Check their own work |
| 3:30–7:00 | Debrief both | Listen |

### Say this

> *"Sixty seconds, silent, no talking. Commit to an answer before I say time — hands up for your letter the second I call it. I reveal right after."*

### The questions

**Q6.** The cost price of 20 articles equals the selling price of 10 articles. Find the gain or loss percentage.
Options: Gain 100% · Loss 200% · Loss 100% · Gain 200%
**Real answer: Gain 100%** — 20CP = 10SP → SP = 2CP → gain% = (2CP − CP)/CP × 100 = 100%.

**Q8.** Seema sells two refrigerators for Rs. 18,000 each — one at a 25% profit, the other at a 25% loss. Find her overall gain or loss.
Options: Gain 2400 · Loss 2400 · Loss 1200 · Gain 2500
**Real answer: Loss 2400** — CP₁ = 18,000 ÷ 1.25 = 14,400. CP₂ = 18,000 ÷ 0.75 = 24,000. Total CP = 38,400. Total SP = 36,000. Loss = 2,400.

### When it goes wrong

| If… | Do this |
|---|---|
| Room picks "Loss 100%" for Q6 | They inverted the ratio — ask "if CP of 20 = SP of 10, is each article's SP bigger or smaller than its CP?" Bigger, so it's a gain. |
| Room assumes Q8 must be breakeven | Expected — this is the same shape as Warm-Up Poll Q2's houses. Flag the parallel now; Activity 3 generalizes it. |
| Someone solves Q6 with real rupee values instead of assuming CP = 1 | Fine if they get 100% — ask them to redo it assuming CP = 1 and confirm it's faster. |
| Nobody attempts Q8 in 60 seconds | Expected, it's the meatier one. Give the CP₁ line yourself, then let them finish CP₂ and the subtraction. |

**Common instructor mistake:** revealing the answer without the one-line "why" immediately after — the reveal only lands paired with reasoning in the same breath.

**Cut rule:** If running short, run Q8 only — it's the one that pays off in Activity 3.

---

## Classroom Quiz

> Classroom Quiz: not yet available — add once question bank exists for this topic.

Time reallocated: the slot a concept session would spend on the platform quiz is folded into an extended **Slide Block B** (29–39 min, 10 min instead of the usual ~7) below. The full 60 minutes is re-timed with no gaps — 0–7, 7–10, 10–22, 22–29, 29–39, 39–47, 47–54, 54–60.

---

## Slide Block B (29–39 min) — DELIVER AS-IS

Covers Company-Specific Questions 7, 9, and 10 from the deck, with their real worked solutions.

**Q7 — Find the cost price of a pen, if at a 25% profit, the selling price of two dozen pens is Rs. 130.80.**
**Answer: Rs. 4.36**

- Strip the profit off the total first: CP (total) = 130.80 ÷ 1.25 = 104.64. Then divide by the count: CP per pen = 104.64 ÷ 24 = 4.36.
- Beat: divide by (1 + profit%) *before* dividing by the count, not after — doing the profit-removal once on the total avoids compounding rounding error across 24 pens.

**Q9 — A store offers an off-season discount of x%, plus a further 12.5% if the purchase exceeds Rs. 500. A person pays Rs. 525 for jeans listed at Rs. 750. Find x.**
Options: 30% · 25% · 20% · 35% → **Answer: 20%**

- Peel off the **known** discount first: price before the 12.5% discount = 525 ÷ 0.875 = 600. First discount amount = 750 − 600 = 150 → 150/750 × 100 = 20%.
- Beat: always remove the discount whose % you already know first — it's one clean division. Solving for both discounts at once, with x appearing twice, is slower and easier to mis-set-up.

**Q10 — Arun bought a TV with a 20% discount. A 25% discount would have saved him Rs. 500 more. At what price did he buy the TV?**
Options: Rs. 8000 · Rs. 12000 · Rs. 10000 · Rs. 6000 → **Answer: Rs. 8000**

- Difference-of-discounts shortcut: (25% − 20%) × MRP = 500 → 5% × MRP = 500 → MRP = 10,000. Price paid = 0.8 × 10,000 = **8,000**.
- Beat: this shortcut turns the whole problem into one linear equation in MRP directly — no need to write out both discounted prices and subtract them afterward.

**Checkpoint (at 39 min)** — cold-call:
> *"In Q9, why do we peel off the 12.5% discount before solving for x, instead of the other way round?"*
> **Answer:** 12.5% is a known, fixed percentage — reversing it is one clean division (÷0.875). x is the unknown, so it has to be solved last, from the result of that division.

---

## ⚡ Activity 2 — Trace the Table: Build the Method Reference (39–47 min)

### What this activity is

A blank two-column table — **Question | Fastest Method** — for all ten of today's questions goes on the board with only the Question column filled in (a one-line paraphrase of each stem). Cold-called students fill in the Method column live, in their own words, in under ten words per row. By this point all ten questions have been delivered (Slide Block A, Activity 1, Slide Block B), so this is pure recall-and-name, not re-solving.

### Why it's here

Ten separate solutions don't automatically become a reusable reference. This activity forces the class to compress each solution down to its one-line shortcut — which is exactly what "which method is fastest" (this session's Evaluating objective) requires them to do under real test pressure.

### Before class

Draw or project a 10-row table. Column 1 (Question, one line each) pre-filled; Column 2 (Method) blank.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, reveal table skeleton | Listen |
| 0:30–6:00 | Point at a row, cold-call a name, write what they say | Name the method in ≤10 words |
| 6:00–7:30 | Fill any skipped rows yourself, reading the beat from Slide Blocks A/B | Listen, copy the table |
| 7:30–8:00 | Debrief | Listen |

### Say this

> *"Ten rows, ten questions we just solved. I point, I call a name, you name the fastest method in under ten words — not the answer, the *method*. If you freeze, say 'pass,' I'll take the next hand."*

### The reference (what the table should end up saying)

| # | Question (one line) | Fastest method |
|---|---|---|
| 1 | Rohit Sharma runs | Total boundary-and-six runs in one line, subtract once |
| 2 | Ram/Sham/Priya/Charan chain | Convert each relation to a multiplier, chain backward |
| 3 | Argentina literacy | Compute both literacy totals as absolute counts, subtract |
| 4 | 78%−59% difference = 323 | Value-of-1% shortcut — find 1%, then scale |
| 5 | Samsung price/sales | Successive-%-change formula: a + b + ab/100 |
| 6 | CP of 20 = SP of 10 | Assume CP = 1 (or any convenient value), compare directly |
| 7 | Pen cost price | Strip profit first (÷1.25), then divide by count |
| 8 | Seema's fridges | Equal SP + equal ±% always nets a loss — compare total CP to total SP |
| 9 | Discount-store x% | Peel off the known % discount first, solve for the unknown last |
| 10 | Arun's TV | Difference-of-discount-% × MRP = difference in savings |

### When it goes wrong

| If… | Do this |
|---|---|
| A student states the numeric answer instead of the method | Push once: *"Not the number — the shortcut that got you there."* |
| Room is silent on the harder rows (5, 8, 10) | Give the first three or four words yourself as a starter, let them finish the sentence. |
| Someone gives a correct but overly long method | That's fine — ask them to compress it to one clause before you write it. |
| Running long | Do only rows 2, 4, 5, 8, 9, 10 — skip the more mechanical 1, 3, 6, 7. |

**Common instructor mistake:** writing the method yourself before giving the room a real chance to answer — the value of this activity is entirely in students compressing the idea themselves.

**Cut rule:** Run rows 2, 4, 5, 8, 9, 10 only.

---

## ⚡ Activity 3 — Think–Pair–Share: Why Equal-SP Twins Always Lose (47–54 min)

### What this activity is

Pairs compare two already-solved problems side by side — Warm-Up Poll Q2 (two houses, ±10%, loss 1%) and today's Q8 (two fridges, ±25%, loss Rs. 2,400) — and work out the general pattern connecting the ± percentage to the loss percentage, instead of treating each as a one-off.

### Why it's here

Students have now seen the "equal SP, equal ±% profit and loss" shape twice (poll Q2, deck Q8) and both times it produced a loss, not a breakeven. This activity turns two isolated results into one transferable rule — the session's Analyzing objective.

### Before class

Have both problems' real numbers visible on the board or screen at once:
- Houses: X = 10%, result = 1% loss
- Fridges: X = 25%, result = Rs. 2,400 loss on Rs. 38,400 total CP

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, both problems on screen | Listen |
| 0:30–2:00 | Silent timer | Pairs discuss, no writing yet |
| 2:00–5:00 | Take 2–3 pair share-outs, build toward the pattern | Share, listen to others |
| 5:00–6:30 | Reveal and confirm the rule against both real cases | Check their own reasoning |
| 6:30–7:00 | Close line | Listen |

### Say this

> *"Ninety seconds, pairs. Two questions, same shape: sell two items at the identical price, one at +X%, one at −X%. Houses used X = 10 and lost 1%. Fridges used X = 25. Find the relationship between X and the loss % — don't just recompute today's number, find the pattern."*

### The pattern and how to confirm it

Loss% = X²/100 whenever an item is sold at equal SP with symmetric ±X% profit and loss.

- Houses: X = 10 → 10²/100 = 1%. Matches the real answer exactly.
- Fridges: X = 25 → 25²/100 = 6.25%. Confirm against the real numbers: Rs. 2,400 loss ÷ Rs. 38,400 total CP × 100 = 6.25%. Matches.

### When it goes wrong

| If… | Do this |
|---|---|
| Pairs just recompute today's rupee loss instead of generalizing | Prompt: *"State it as a formula in X, not just today's number."* |
| Nobody reaches X²/100 | Guide it: *"10 squared over 100 is...? Now try 25 squared over 100."* |
| A pair insists it should be breakeven | Have them recheck the fridges' real totals: CP = 38,400, SP = 36,000 — not equal. |
| Running long | Skip deriving the formula; just land on *"always a loss, and a bigger X means a proportionally bigger loss"* and move on. |

**Common instructor mistake:** presenting X²/100 as something to memorize by name. It's a derived shortcut for recognising the pattern fast, not a formula on the syllabus — say this explicitly.

**Cut rule:** Run the share-out and confirm the pattern verbally only; skip writing the general X²/100 form on the board.

---

## Exit Ticket + Homework (54–60 min)

**Exit ticket** — on paper or in chat before anyone leaves:

> The cost price of 20 articles equals the selling price of 10 articles. What is the gain percentage — and in one sentence, what's the fastest way to see it without picking a real currency value?
> **Answer:** Gain = 100%. Fastest way: assume the CP of one article = 1; then SP = 2 follows directly from the 20:10 ratio, without ever needing an actual rupee amount.

Scan responses on the way out. If most students reach for real currency values instead of the assumed-value trick, reopen it for 90 seconds at the start of Session 15.

**Homework**

| Task | Detail |
|---|---|
| Re-attempt all 10 Company-Specific MCQs in today's deck, cold, on paper | `3) NIAT_CSMCQ'S_Percentages_Profit & Loss.pptx` — write the fastest method next to each final answer, not just the answer |
| Revisit Sessions 10–13 material for any identity that felt shaky today | SP = CP(1 ± %), successive-%-change (a + b + ab/100), "% more/less than" chain multipliers, and the value-of-1% scaling — no dedicated practice unit exists yet for this topic |

Tell them: *"Nothing on the real test will look exactly like today's ten questions — but the four moves you used today (assumed-value CP–SP tricks, backward multiplier chains, the successive-change formula, and value-of-1% scaling) will cover almost everything you see. Redo all ten unaided before next session."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Miscounting "runs off the bat" in Q1 — dropping either the boundaries or the sixes | Boundaries and sixes are used almost interchangeably in casual cricket talk | Q1's own wrong options (58%, 50%) are exactly what you get from dropping one run type — write out (3×4)+(8×6)=60 explicitly in Slide Block A |
| Adding/subtracting percentages directly across a "% more/less than" chain (Q2, Q3-style) instead of chaining multipliers | Percentages "feel" additive because ordinary arithmetic is | Slide Block A's backward-multiplier chain for Q2 — show that adding 10+25+20 gives a meaningless number, while ÷0.9, ÷1.25, ÷0.8 gives the real chain |
| Treating two successive % changes as a simple sum (Q5's wrong options "Increased by 10%" and "Decreased by 20%" both come from adding/subtracting −25 and +20 without the cross-term) | The compounding term (ab/100) is invisible until the actual multipliers are multiplied out | Running the compounding formula live: −25+20+(−5)=−10%, contrasted with the naive −5% |
| Discounts applied additively in a chain (Q9's wrong options 25%, 30%, 35% all come from mis-combining the 12.5% with x) | Same additive instinct as above, applied to discounts | Peeling off the known 12.5% discount first via division (÷0.875), shown in Slide Block B |
| Profit % computed on selling price instead of cost price (carried from Session 13's own hint, "What is Actual Profit?", retested in today's Warm-Up Poll Q5) | The word "profit" doesn't specify its base, and SP is often the only number quoted aloud | Poll Q5's reveal — the same 20%-of-SP trap, shown to equal 25% of CP |
| Assuming equal SP with equal +X%/−X% profit and loss breaks even (Q8's fridges, and Warm-Up Poll Q2's houses) | "+25 and −25 cancel" is true of the percentages themselves but not of the rupee amounts they're applied to | Activity 3's Think–Pair–Share, deriving Loss% = X²/100 from both real cases side by side |

---

## Instructor Notes

- **Grounding.** This plan is built entirely from local pptx text-extraction of two decks — `3) NIAT_CSMCQ'S_Percentages_Profit & Loss.pptx` (this session) and the Session 13 Profit & Loss deck (used only for the Warm-Up Poll). No platform unit IDs, classroom quiz bank, or MCQ/coding-practice pool exist yet for either topic — both gaps are flagged in the header table and the Classroom Quiz block above.
- **Consolidation, not new content.** Session 14 of 23. Nothing here is a new concept — it is Sessions 10–13's percentage identities and profit/loss methods applied to ten real solved placement-style questions. Judge this session by whether students get *faster* at methods they already have, not by new recall.
- <!-- placement: inferred --> **Slide Block A / Activity 1 / Slide Block B split is a judgment call.** The source deck's own slide order (questions 1 through 10, sequential) is ground truth for content and answers, but which five questions open Slide Block A, which two move into Activity 1, and which three close out Slide Block B is this plan's pacing decision, not a confirmed instructor delivery order. Adjust freely if the actual classroom pacing groups them differently — nothing about the math depends on this grouping.
- **No "Hint :-" lines in this deck.** Unlike the Session 13 Profit & Loss deck (which annotates several questions with explicit "Hint :-" lines) and unlike the CSMCQ Numbers deck used in Session 8 (which also carries hints), this CSMCQ Percentages & P&L deck's extracted text has no hint annotations on any of its 10 questions. The Common Misconceptions table above is grounded instead in (a) this deck's own wrong MCQ options and (b) one hint carried over from the Session 13 deck ("What is Actual Profit?") for the profit-on-SP-vs-CP misconception, since that exact distinction is retested in today's Warm-Up Poll Q5.
- **Classroom Quiz gap:** absorbed into an extended Slide Block B (29–39 min, 10 min instead of the ~7 a concept session would use) rather than left as dead time. Full 60 minutes, no gaps: 0–7, 7–10, 10–22, 22–29, 29–39, 39–47, 47–54, 54–60.
- **Pacing risk:** Slide Block A covers 5 questions in 12 minutes (~2.4 min each) — the same density as Session 8. If running long, state Q3 (Argentina) and Q4 (random number) as one-line results with the shortcut named, rather than full board derivations; Q1, Q2, and Q5 carry the session's real teaching weight (careful boundary-run counting, the backward-multiplier chain, and the successive-%-change formula).
- **Activity 3's generalization (Loss% = X²/100 for equal-SP twin transactions) is authored for this plan** — it does not appear in either source deck. It was verified against both real cases before inclusion (Warm-Up Poll Q2's houses: X=10 → 1% loss; today's Q8 fridges: X=25 → Rs. 2,400 loss on Rs. 38,400 total CP = 6.25% loss). Treat it as a correct, useful pattern, but tell students explicitly it's a derived shortcut for spotting the shape fast, not a named formula to memorize for its own sake.
- **No separate practice pool:** homework deliberately reuses the same 10 deck questions rather than pointing to a coding/MCQ practice unit, since none exists yet for this topic — consistent with how Session 8's consolidation session handled the same gap.
