# Session 20 — Company-Specific MCQs: SI & CI, Ratios & Proportions

**Duration** 60 min · **Topic** Consolidation — SI & CI + Ratios & Proportions (Company-Specific MCQs) · **Prerequisite** Sessions 16–19 (Simple Interest through Proportions)
**Session type** Lecture — consolidation/review session spanning two topic blocks (SI & CI, then Ratios & Proportions). No new concept: applies Sessions 16–19's methods to real placement-test-style questions. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet for this topic.

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `4) NIAT_CSMCQ'S_SI & CI_Ratios & Proportions.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Apply the SI formula (`SI = PRT/100`) to solve for whichever one of P, R, or T is missing, across several real placement-style questions. *(APPLYING)*
2. Apply the CI−SI shortcut (`CI − SI = PR²/100²`) and the compound-growth formula (`A = P(1 + R/100)ⁿ`) interchangeably, choosing whichever route is faster for the question in front of them. *(APPLYING)*
3. Analyze a stated ratio (side lengths, partnership capital, salaries) and correctly introduce a scale variable (`x`) before doing any arithmetic with it. *(ANALYZING)*
4. Analyze partnership/profit-sharing problems to identify when time-weighted capital (capital × months invested) — not the raw investment ratio — determines the actual split. *(ANALYZING)*
5. Evaluate, across today's ten solved questions, which of two candidate methods (direct formula rearrangement, assume-a-variable, or a named shortcut) is fastest for a given SI/CI or ratio question, and justify the choice out loud. *(EVALUATING)*
6. Solve a full placement-style SI/CI or ratio question end-to-end under timed, no-hint conditions, replicating real exam pressure. *(APPLYING)*

---

## Warm-Up Poll — Retrieval Practice (0–7 min)

7 questions on **Session 19 (Proportions)**. Newly authored questions, real numbers and answers from that deck. ~45 s each, project the distribution, never name individuals. Ramp: recall → application → analysis.

**Q1.** Two ratios being equated (`a:b :: c:d`, where `ad = bc`) is called:
`A` Variation · `B` Proportion · `C` Simple ratio · `D` Interest
→ **B.** *Targets:* the core definition opening Session 19.

**Q2.** In a continued proportion `a : b :: b : c`, how many distinct terms are there?
`A` 2 · `B` 3 · `C` 4 · `D` It depends
→ **B** — `a`, `b`, `c`. *Targets:* continued proportion has one fewer independent term than a normal proportion, which is the whole point of the name.

**Q3.** If `0.75 : x :: 5 : 8`, then `x` equals:
`A` 1.2 · `B` 1.0 · `C` 1.5 · `D` 0.6
→ **A.** *Targets:* cross-multiplication (`0.75 × 8 = 5x → x = 1.2`) applied to a decimal ratio — Session 19's own example.

**Q4.** The sum of 3 numbers is 98. The ratio of the first to the second is 2:3, and of the second to the third is 5:8. What is the second number?
`A` 24 · `B` 30 · `C` 36 · `D` 40
→ **B.** *Targets:* chaining two separate ratios into one combined ratio before dividing the total.

**Q5.** Monthly incomes of A and B are in the ratio 4:5, their expenses are in the ratio 5:7, and each saves Rs. 2,400. What is A's income?
`A` 4,800 · `B` 5,600 · `C` 6,400 · `D` 8,000
→ **C.** *Targets:* setting up two ratio equations (income and expense) that share the same "savings" constant.

**Q6.** In a 1,000 m race, A beats B by 200 m and A beats C by 300 m. By how many meters will B beat C?
`A` 100 m · `B` 125 m · `C` 150 m · `D` 175 m
→ **B.** *Targets/misconception:* picking **A (100 m)** means they just subtracted `300 − 200`. Session 19's own hint is explicit: *"Addition & Subtraction is not acceptable for manipulating ratios — prefer multiplication and division."* The real move is a speed ratio (`B:C = 800:700 = 8:7`), giving 125 m. *If >40% pick A, re-teach this before moving on — it resurfaces in today's Ratios block.*

**Q7.** 36 programmers write 36 similar programs in 36 hours. How many **additional** programmers are needed to write 84 programs in 24 hours?
`A` 90 · `B` 126 · `C` 54 · `D` 72
→ **A.** *Targets/misconception:* **126** is a trap — it's the *total* programmers required, not the *additional* ones (`126 − 36 = 90`). Watch for this exact trap; it's the same "total vs. additional/remaining" reading error that shows up in today's SI & CI "sum vs. amount" question.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including reads.

---

## Hook (7–10 min)

**Framing — say this:**

> *"Sessions 16 through 19 gave you every tool you need — SI, CI, ratios, proportions. From today, no new formulas. Today is the real test: can you use those tools under pressure, the way a placement exam actually demands it? Cold. Timed. No hints. Exactly like the real thing."*

Put the deck's own opening question on screen, exactly as written, with **all four options** — do not solve it, do not hint:

> *"In how many years will a principal of Rs. 200 generate the same interest at 6% as a principal of Rs. 800 generates in 2 years at a rate of 4.5%?"*
> `A` 6 · `B` 7 · `C` 8 · `D` 9

> *"Sixty seconds. Silent. Write your answer and your working. Go."*

Time it visibly. At 60 seconds:

> *"Pens down. Hold on to that answer — don't tell me yet. We're coming back to this exact question at the end of the session, and I want to see if the method changes your answer or just your speed."*

Move straight into Slide Block A, which opens by solving this exact question.

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — this block groups the deck's Q1, Q2, Q3, Q4 (its first four questions, slides 3–10), which appear consecutively in the source deck. Q8 (CI−SI difference, slides 17–18) is also SI & CI content but sits later in the deck after a ratio question; it is deliberately held out for Activity 1 rather than delivered here, to keep this block's pace tight. See Instructor Notes. -->

Covers, in this order: the deferred hook question (reveal) → rate-from-SI question → "rate equals time" loan question → principal-from-two-amounts question.

**Beat 1 — reveal the hook.** `P=800, R=4.5%, T=2yr → SI = (800×4.5×2)/100 = Rs. 72`. Second case: `72 = (200×6×T)/100 → T = 7200/1200 = 6 years`. **Answer: 6 years (option A).** Ask for a show of hands on who had 6 written down before the reveal — this is the diagnostic, not a shaming exercise.

**Beat 2 — same formula, different unknown.** `SI=150, P=1500, T=3 → R = (150×100)/(1500×3) = 3.33%`. *Fastest method:* `SI = PRT/100` is one formula with three possible unknowns — don't memorize three formulas, just isolate whichever letter is missing.

**Beat 3 — assume-a-variable.** Abhi's loan: `P=1400, SI=686`, and rate (%) equals time (years) — both unknown but equal. Deck's own hint: *"Assume a random variable to solve this question."* Set both to `x`: `686 = (1400 × x × x)/100 → x² = 49 → x = 7`. **Answer: 7% (and 7 years).** *Fastest method:* the moment a question states two different-looking unknowns are numerically equal, collapse them into one variable immediately.

**Beat 4 — the shortcut for "amounted to" pairs.** Sum amounts to Rs. 815 in 3 years and Rs. 854 in 4 years. Deck's own hint: *"Sum is nothing but principal amount."* SI for 1 year = `854 − 815 = 39`. SI for 3 years = `39 × 3 = 117`. Principal = `815 − 117 = Rs. 698`. *Fastest method:* never solve for R first here — the year-over-year difference IS one year's SI, so skip straight to it.

**Checkpoint (at 22 min)** — cold-call:
> *"Same trick as Beat 4 — if I gave you the amount after 5 years and after 6 years instead, what's your very first calculation?"*
> **Answer:** Subtract the two amounts to get one year's SI — that's always the fastest first move whenever two consecutive-year amounts are given.

---

## ⚡ Activity 1 — Timed Silent Solve → Reveal (22–29 min)

**Format:** Timed Silent Solve → Reveal · **Exposes:** whether students can select the right SI/CI method fast, under the same time pressure as the hook, without the safety net of a slide walking them through it first.

### What this activity is

Three of the deck's own remaining SI & CI questions, delivered one at a time, cold. Each gets 90 seconds of silent solving before you reveal. No discussion until the answer is on screen.

### Why it's here

Slide Block A taught the methods with full narration. This activity removes the narration and checks whether the method actually transferred — the real placement-test condition.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:20 | Setup line | Listen |
| 0:20–1:50 | Show Q5, stay silent | Solve alone, 90 s |
| 1:50–2:20 | Reveal Q5, quick discuss | Check work |
| 2:20–3:50 | Show Q6, stay silent | Solve alone, 90 s |
| 3:50–4:20 | Reveal Q6, quick discuss | Check work |
| 4:20–5:50 | Show Q8, stay silent | Solve alone, 90 s |
| 5:50–6:30 | Reveal Q8, quick discuss | Check work |
| 6:30–7:00 | Debrief | Listen |

### Say this

> *"Three questions. Ninety seconds each, silent, no talking, no partner. I reveal the answer after each one — you're checking your method against mine, not the other way around."*

### The questions

**Q5.** *"When the simple interest on an amount for 3 years is Rs. 50 at a rate of 2% per year, what is the compound interest on the same amount at the same rate and for the same period of time?"*
Options: `Rs. 22.2` · `Rs. 23.5` · `Rs. 33.6` · `Rs. 51.01`

**Q6.** *"A sum of Rs. 8,000 will amount to Rs. 8,820 in 2 years if the interest is calculated every year. The rate of compound interest is:"*
Options: `6%` · `7%` · `3%` · `5%`

**Q8.** *"The difference between the compound interest and the simple interest on a certain sum at 12% per annum for two years is Rs. 90. What will be the amount at the end of 3 years (compounded annually)?"*
Options: `Rs. 9000` · `Rs. 6250` · `Rs. 8530.80` · `Rs. 8780.80`

### Answers

| # | Solution | Answer |
|---|---|---|
| Q5 | `50 = (P×2×3)/100 → P = 2500/3`. Compound 3 yrs at 2%: `2500/3 × 1.02 = 850 → ×1.02 = 867 → ×1.02 = 884.34`. `CI = 884.34 − 2500/3 = 51.01` | **Rs. 51.01** |
| Q6 | `8820 = 8000(1+R/100)² → (21/20)² = (1+R/100)² → R = 5` | **5%** |
| Q8 | `90 = P(12/100)² → P = 6250`. Amount after 3 yrs `= 6250 × 1.12³ = Rs. 8780.80` | **Rs. 8780.80** |

**How it surfaces:** Q5 and Q6 both punish students who default to the SI formula out of habit — flag that explicitly after Q6. Q8 rewards knowing the `CI − SI = PR²/100²` shortcut over deriving both interests from scratch; ask who used the shortcut vs. who computed both years by hand, and note the time difference.

**Debrief line:**
> *"Notice: every one of these had a faster path than 'calculate everything from the start.' That's what today is training — not new maths, just faster recognition of which shortcut applies."*

**Cut rule:** If running long, drop Q8 and keep Q5 and Q6 — they're the two that directly test the SI-vs-CI confusion from Slide Block A.

---

## Classroom Quiz — Not Yet Available (no time allocated)

> Classroom Quiz: not yet available — add once question bank exists for this topic.

The standard 27–34 min classroom-quiz slot has no question bank for this topic yet, so its 7 minutes are reallocated: 2 minutes into Activity 1 (making it a full 7 min instead of 5) and 5 minutes into Slide Block B below (12 min instead of a standard 7). No gap in the clock — Slide Block B starts immediately at minute 29.

---

## Slide Block B (29–41 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — this block groups the deck's three Ratios & Proportions questions (Q7, Q9, Q10 by slide order: salary ratio at slides 15–16, partnership profit ratio at slides 19–20, rectangle area ratio at slides 21–22). In the source deck, the CI−SI question (Q8, held for Activity 1 above) sits physically between the salary-ratio question and the partnership question. This plan regroups by topic rather than slide order so the block has thematic coherence — see Instructor Notes. -->

Covers: salary-ratio question → partnership profit-sharing question → rectangle length:breadth ratio question.

**Beat 1 — ratio-to-variable, always.** Ravi and Sumit's salaries are in ratio 2:3; each rises by Rs. 4,000; new ratio becomes 35:40. Write `Ravi = 2x, Sumit = 3x` immediately: `(2x+4000)/(3x+4000) = 35/40 = 7/8 → 16x+32000 = 21x+28000 → x=800`. **Ravi's salary = 2×800 = Rs. 1,600.** *Fastest method:* the instant you see a ratio, convert it to `ax : bx` before touching any other number in the question.

**Beat 2 — time-weighted capital in partnerships.** Anil invests Rs. 3,000, Biswas Rs. 4,000; Anil **doubles his capital after 6 months**. Naive students take the ratio 3:4 and stop. Correct: Anil's total = `(3000×6)+(6000×6) = 54,000`; Biswas's total = `4000×12 = 48,000`. Ratio = `54,000:48,000 = 9:8`. **Fastest method:** whenever a partner's capital *changes mid-year*, the ratio is never the raw investment ratio — always multiply capital × months for each phase first.

**Beat 3 — introduce the scale variable before the perimeter equation.** Length:breadth = 7:6, perimeter = 260 m. Write `L=7x, B=6x` first: `2(7x+6x)=260 → 26x=260 → x=10`. So `L=70, B=60`, **Area = 70×60 = 4,200 sq. m.** *Fastest method:* solve for `x` from the one linear equation you're given (perimeter), then compute L, B, and area in that order — don't try to shortcut past finding `x`.

**Checkpoint (at 41 min)** — cold-call:
> *"Length:breadth ratio 7:6, perimeter 260 m — what's the area, and what was your very first line of working?"*
> **Answer:** Rs.— *(non-monetary)* **4,200 sq. m**, and the first line must be `L=7x, B=6x` before anything else.

---

## ⚡ Activity 2 — Trace the Table (41–48 min)

**Format:** Trace the Table · **Exposes:** the "ratio-only" shortcut students take on partnership problems — dividing profit by the raw capital ratio and ignoring the time dimension entirely.

### What this activity is

You give students only the raw numbers from Q9 — Anil Rs. 3,000, Biswas Rs. 4,000, Anil doubles his capital after 6 months — with the table **erased**, no ratio shown. They must build the capital × months table themselves before any ratio is taken.

### Why it's here

Slide Block B already delivered the correct answer with full narration. This activity checks whether students can generate the table from scratch — the actual skill, not just recognition of the answer.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, restate the raw numbers only | Listen |
| 0:30–3:00 | Wait, silent | Sketch a 2-row × 3-column table (capital, months, capital×months) individually or in pairs |
| 3:00–6:00 | Cold-call, fill the board table row by row from student answers | Answer, correct each other |
| 6:00–7:00 | Debrief | Listen |

### Say this

> *"Anil put in 3,000, Biswas put in 4,000. Six months in, Anil doubles his capital. I want the table on your page — capital, how many months it stayed at that capital, and capital times months — before anyone says a ratio out loud."*

### The table (built live)

| Partner | Phase 1 capital | Months | Phase 2 capital | Months | Total (capital × months) |
|---|---|---|---|---|---|
| Anil | 3,000 | 6 | 6,000 | 6 | 18,000 + 36,000 = **54,000** |
| Biswas | 4,000 | 12 | — | — | **48,000** |

**Profit ratio = 54,000 : 48,000 = 9 : 8.**

**How it surfaces:** Before revealing the correct table, ask who wrote down "3:4" as their first instinct. That's the naive capital-only ratio — name it as the trap, then show why the table beats it.

**When it goes wrong:**

| If… | Do this |
|---|---|
| Students jump straight to "3:4" | That's expected and is the point — ask "did Anil's capital stay 3,000 for all 12 months?" and let the table correct it |
| Nobody accounts for the "doubles" correctly (some write 3,000+6,000=9,000 flat, no months) | Push: "for how many months was Anil's capital actually 6,000?" |
| Running long | Skip individual sketching, go straight to cold-calling the board table — the table itself is the artifact that matters, not who drew it first |

**Debrief line:**
> *"Any time a partner's capital changes mid-year, 'ratio' is not your first move — the table is. The ratio comes last, after the table, not instead of it."*

**Cut rule:** If time is short, drop the individual sketching (0:30–3:00) and build the table entirely by cold-call from minute 1 — keep the debrief line, it's the whole point.

---

## ⚡ Activity 3 — Think–Pair–Share: Which Method Is Faster? (48–55 min)

**Format:** Think–Pair–Share · **Exposes:** whether students can *justify* a method choice, not just execute one — the EVALUATING-level objective for this session.

### What this activity is

Pairs are given two of today's already-solved questions — Q7 (Ravi/Sumit salary ratio) and Q10 (rectangle area ratio) — and must argue which one's method is "faster to spot," then defend it to the class.

### Why it's here

Both questions use the identical `ax:bx` scale-variable trick, but dressed differently (a % increase vs. a perimeter constraint). Making students compare them directly is what cements the pattern-recognition, rather than leaving it as two isolated worked examples.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, restate both questions side by side | Listen |
| 0:30–2:30 | Wait | Pairs discuss: which method clicks faster, and why |
| 2:30–3:00 | Call for a show of hands vote | Vote for Q7 or Q10 |
| 3:00–6:00 | Take 2–3 pairs' justifications; re-run both solutions on the board as they talk | Defend, listen, compare |
| 6:00–7:00 | Debrief | Listen |

### Say this

> *"Two questions, both already solved today — Ravi and Sumit's salaries, and the rectangle's length and breadth. Same underlying trick in both. Talk to your partner for two minutes: which one would you recognize faster on a real test, and why? I want a reason, not just a pick."*

**Debrief line:**
> *"It doesn't matter which one you picked — what matters is that both collapse to the exact same first line: write the ratio as `ax` and `bx`. That's the pattern today was built to drill into you. Spot it, and both of these stop being 'hard' questions."*

**When it goes wrong:**

| If… | Do this |
|---|---|
| Pairs can't agree | Good — put both justifications on the board, that disagreement is the discussion |
| Everyone picks the same one with no real reason | Push: "what's different about *how* the ratio shows up in the other question?" |
| Running long | Skip the vote, take one pair's justification, deliver the debrief line as written |

**Cut rule:** If time is very short, skip pair discussion and run this as a single class-wide show of hands, then go straight to the debrief line.

---

## Exit Ticket + Homework (55–60 min)

**Exit ticket** — on paper or in chat before anyone leaves:

> Go back to the hook question: *"In how many years will a principal of Rs. 200 generate the same interest at 6% as a principal of Rs. 800 generates in 2 years at a rate of 4.5%?"* Write your answer, and one sentence on whether your method today was different from your method at minute 7.
> **Answer:** **6 years** (`SI = 800×4.5×2/100 = 72`; `72 = 200×6×T/100 → T = 6`).

Scan responses on the way out — a wrong answer here, this late, is the strongest signal that the SI-formula-rearrangement habit from Slide Block A didn't transfer and needs a recap next session.

**Homework**

| Task | Instruction |
|---|---|
| Full deck re-attempt | Re-solve all ten questions in `4) NIAT_CSMCQ'S_SI & CI_Ratios & Proportions.pptx` cold, one at a time, under 90 seconds each, before checking any solution slide. |
| Method log | For each question, write down which shortcut you used (formula rearrangement, assume-a-variable, CI−SI shortcut, or scale-variable ratio) — one line each. |
| Session 16–19 review | Re-read your own notes from Sessions 16–19 for any formula you hesitated on tonight. |

Tell them: *"There is no separate practice set for this yet — the deck you just saw in class IS the practice set. Redo it cold tonight while the methods are fresh."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| In "rate = time" questions (Q3), guess-and-check numeric values instead of setting both to one variable `x` | Two different-looking unknowns don't obviously look like "the same thing" | Deck's own hint — *"Assume a random variable to solve this question"* — applied live in Slide Block A Beat 3 |
| "Sum" in Q4 means the same thing as "amount" | Casual English uses the words interchangeably | Deck's own hint — *"Sum is nothing but principal amount"* — Slide Block A Beat 4, subtracting SI before touching the amount |
| Applying the SI formula to a "will amount to" compound-interest question (Q6) | SI is the first formula taught; it's the default reflex | Re-deriving `R` from `(21/20)² = (1+R/100)²` live and contrasting with the SI approach |
| Re-deriving both years' CI from scratch instead of using `CI − SI = PR²/100²` (Q8) | The shortcut formula is easy to forget under time pressure, full derivation feels "safer" | Activity 1 — showing the shortcut and the year-by-year 1.12³ computation side by side, timing both |
| Dividing partnership profit by the raw capital ratio (3:4) and ignoring the mid-year capital change (Q9) | A partnership question "looks like" a plain ratio question | Activity 2's table — forcing capital × months before any ratio is taken |
| Plugging the ratio numbers directly in as length and breadth (7 and 6) instead of `7x` and `6x` (Q10) | The ratio already "looks like" real numbers | Slide Block A Beat 3 / Activity 3 — insisting on the `x` line before the perimeter equation |

---

## Instructor Notes

<!-- placement: inferred -->

- **This entire plan is grounded in a local text-extraction of the source `.pptx`**, not a platform export. There is no unit ID, quiz-bank ID, or MCQ-pool ID for this session because none exists yet for this topic — every "Resource" row above says so explicitly. Do not substitute IDs from the Programming Foundations set; they belong to a different course.
- **The A/B topical split is a judgment call, not the deck's literal slide order.** The source deck's actual sequence is: six SI & CI questions (slides 3–14) → one ratio question (salary ratio, slides 15–16) → one more SI & CI question (CI−SI difference, slides 17–18) → two more ratio questions (slides 19–22). This plan regroups by topic — all SI & CI content into Slide Block A / Activity 1, all Ratios & Proportions content into Slide Block B / Activities 2–3 — so each block has thematic coherence, per session design intent. If you deliver the deck slide-by-slide instead of by this plan's grouping, the CI−SI question (Q8) will appear between the two ratio blocks; either order is content-accurate, just narrate the transition if you follow slide order.
- **This is a consolidation session, not a concept session.** Nothing new is taught. All six Learning Objectives are APPLYING/ANALYZING/EVALUATING because the entire point of Session 20 is fluency and speed on Sessions 16–19's methods under placement-test conditions — judge the session by speed and method-selection, not by whether students learned a new formula.
- **The Classroom Quiz slot has no gap.** Its standard 7 minutes are reallocated: 2 into Activity 1 (5→7 min) and 5 into Slide Block B (7→12 min), so all ten of the deck's real questions get proper class time despite there being no quiz bank yet. Re-verify this reallocation if you trim any block on the fly — the running total must still hit exactly 60.
- **Every number, question, option set, and answer in this plan is quoted from the two source decks** (this session's CSMCQ deck and Session 19's Proportions deck) — nothing was invented. Warm-up poll distractors (the wrong options) are newly authored, per the course's standing rule that warm-up polls are always freshly written; the *correct* answers and all worked numbers are real.
- **Have all ten of this session's problems (and the seven Session-19 poll problems) already retyped or on slides before class starts.** With three activities plus two slide blocks, there's no slack to hunt for a number mid-session.
