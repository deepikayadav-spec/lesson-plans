# Session 11 — Percentages: Percentage Change & Successive Increment/Decrement

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Percentage Change & Successive Increment/Decrement · **Prerequisite** Session 10 (Basics Percentages)
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet — a 5-min quiz slot is reserved but empty for that reason. · **Format** 50-min recalibrated, 2 ALS activities

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT_Percentages 1.pptx` |
| Classroom Quiz | not yet available — 5-min slot reserved at end of session, add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the percentage-change formula and identify the two successive-change scenarios covered today. *(REMEMBERING)*
2. Explain why a percentage increase and the percentage decrease that reverses it are **not** equal in magnitude. *(UNDERSTANDING)*
3. Apply the shortcut formula for two successive percentage changes, Net% = a + b + (ab/100), to compute the combined effect of two hikes/cuts in one step. *(APPLYING)*
4. Solve multi-step percentage-change word problems by identifying which quantity stays fixed. *(APPLYING)*
5. Analyze "A is x% more than B" statements to correctly derive "B is less than A by [x/(100+x)]×100 %" instead of assuming the reverse percentage is the same number. *(ANALYZING)*
6. Evaluate ratio-based multi-person word problems by structuring unknowns in a table before solving. *(EVALUATING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

5 questions on **Session 10 (Basics Percentages)**. Newly authored from that deck's own content. ~45 s each, project the distribution, never name individuals.

**Q1.** In the building-block method, what is 10% of 82?
`A` 0.82 · `B` 8.2 · `C` 41 · `D` 82
→ **B.** *Targets:* the 100% / 10% / 1% breakdown.

**Q2.** And what is 1% of 82?
`A` 0.082 · `B` 0.82 · `C` 8.2 · `D` 1.82
→ **B.** *If Q1+Q2 combined miss rate >40%:* re-run the chain on the board before Q3 — everything else in the poll depends on it.

**Q3.** Using 50% of 82 = 41 and 1% of 82 = 0.82, what is 51% of 82?
`A` 41.82 · `B` 51.82 · `C` 40.18 · `D` 42.64
→ **A.** *Targets:* combining building blocks — this is the exact skill today's shortcut percentage-change formula is built on.

**Q4.** The "Magic Circle of 1/7" showed 1/7 = 14.2857%. Using that, what is 28.5714% of 280?
`A` 40 · `B` 60 · `C` 80 · `D` 100
→ **C.** *Targets:* recognising 28.5714% as 2/7 and applying it directly instead of long division.

**Q5.** What is 40% of 66.66% of 25% of 75% of 1200?
`A` 40 · `B` 50 · `C` 60 · `D` 70
→ **C.** *Targets:* chaining several "percentage of a percentage" steps in one problem — this is the multi-step muscle today's successive-change problems also need.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–9 min)

Write this on the board, nothing else:

```
40 kmph  →  60 kmph
```

Say: *"A car speeds up from 40 to 60 kmph. That's a 50% increase — everyone agree?"* (They will.)

Now add:

```
60 kmph  →  40 kmph
```

Say: *"Same car, slows back down to exactly 40 kmph. What percentage decrease was that? Shout a number."*

Let the guesses land — most of the room will say "50%." Reveal:

> *"It's 33.33%. Same two speeds, same road, and the increase and the decrease are different numbers. Nobody's arithmetic is wrong — the rule that explains this is what today is for."*

Tie back to the poll: *"You just spent five minutes doing 51% of 82 in building blocks. Today those same building blocks explain why 40-to-60 and 60-to-40 don't cancel out."*

---

## Slide Block A (9–16 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — slide 4's "Percentage Change | %" is a title/formula slide; the text extraction did not capture a worked numeric example on it, only the header. Confirm the live slide's content before presenting the formula below as its content. -->

Covers (slides 4–7): Percentage Change → Successive increment/decrement (conventional vs. shortcut) → the 40/60/40 kmph illustration → Sai's salary worked example.

**Beats to emphasise**

- **Percentage change formula:** %Change = ((New − Old) / Old) × 100. State it once, plainly, before touching successive changes.
- **The successive-change rule from the deck's own speaker notes:** a (1/n) increase requires a (1/n+1) decrease to undo it, and a (1/n) decrease requires a (1/n−1) increase to undo it. Walk the class back through the hook's 40→60 (a 1/2 increase, n=2) and 60→40 (a 1/3 decrease, n+1=3).
- **Sai's example (slide 7):** initial salary Rs. 20000, 10% annual hike for two years. Show **both** columns — conventional (20000 → 22000 → 24200, year by year) and shortcut (10 + 10 + (10×10/100) = 21%). Land the point hard: *"Ten percent plus ten percent is not twenty percent. It's twenty-one, because the second hike lands on a bigger number."* Final answer: **Rs. 24200, a 21% change.**

**Checkpoint (at 16 min)** — 10 s silent think, cold-call:
> *"Using a + b + ab/100 — why isn't two 10% hikes just 20%?"*
> **Answer:** The second 10% is calculated on the already-increased salary, not the original.

---

## ⚡ ALS Activity 1 — Think-Pair-Share: Lohitha's Salary (16–23 min)

**ALS format:** Think-Pair-Share. Chosen right after Slide Block A because the shortcut formula only sticks if students use it once under their own effort, with a mixed-sign case (one increase, one decrease) — Sai's example was watched, this one is attempted.

**Setup line:**
> *"Lohitha's salary is 30000. Year one: 20% hike. Year two: 10% decrement. Using the formula from Sai's example, work out the overall percentage change on your own — sixty seconds, no talking."*

**Timing:** 1 min silent · 2 min pairs · cold-call 2 pairs.

**The problem:**
> Lohitha got selected in a company with an initial salary of 30000. In the first year she got a hike of 20%, second year she got a decrement of 10%. After two years what is the percentage change in her salary?

**Answer: 8% increase.**
Shortcut: 20 + (−10) + (20 × −10 / 100) = 20 − 10 − 2 = **8**.
Conventional check: 30000 → 36000 → 32400, which is 2400 more than 30000 → 8%.

**When it goes wrong**

| If… | Do this |
|---|---|
| They answer 10% (just 20 − 10) | They dropped the cross-term — the exact trap Sai's example warned about. |
| They answer −8% (sign flip) | Sign confusion on the decrement. Recompute term by term on the board. |
| Pairs disagree on whether decrement is negative | Standardise immediately: increase = positive, decrement = negative. |

**Debrief line:**
> *"Students trust the shortcut only once they've seen it match the long way, live, at least twice — that's exactly what you just did."*

**Cut rule:** if short on time, skip the pair-compare step — go straight from individual thinking to cold-calling two students.

---

## Slide Block B (23–32 min) — DELIVER SLIDES AS-IS

Covers (slides 9–11): the fraction problem → the dal price/consumption problem → the Pavan/Prudhvi salary-comparison problem.

**Beats to emphasise**

- **Fraction problem (slide 9):** numerator +40%, denominator −20%, resulting fraction 21/16 — find the original. Show the factor method: new fraction = (1.4/0.8) × original = 1.75 × original = 21/16, so original = (21/16) ÷ 1.75 = **3/4**.
- **Dal problem (slide 10):** price rises 10%; by how much must consumption fall to keep expenditure unchanged? Deck's answer: **9 1/11%**, not 10%. Formula: %decrease = (x / (100 + x)) × 100 = (10/110) × 100 = 9 1/11%. Say explicitly: *"The decrease needed is always smaller than the increase that caused it — because it's calculated on the new, bigger price."*
- **Pavan/Prudhvi problem (slide 11):** Pavan's salary is 40% more than Prudhvi's. By what % is Prudhvi's less than Pavan's? Deck's answer: **28.5714%**, not 40%. The two percentages are measured against **different bases**.

**Checkpoint (at 32 min)** — cold-call:
> *"If A is 40% more than B, is B automatically 40% less than A? What's the real number, and why?"*
> **Answer:** No — 28.5714% less. The base is different each way.

---

## ⚡ ALS Activity 2 — Trace the Table: Varshith, Ayush & Tarun (32–40 min)

**ALS format:** Guided Table Build — a multi-person ratio-and-percentage word problem, solved by building a variable table together as a class before any arithmetic starts. Chosen as the closing activity because these "three people, two relationships, one average" problems are where students give up — not because the maths is hard, but because they never structure the unknowns first.

**Setup line:**
> *"Three people, two relationships, one average. Before anyone touches a calculator, we're filling this table one column at a time — and we start with whoever has nothing to compare to."*

Draw three empty columns on the board: **Tarun | Ayush | Varshith**.

**The problem:**
> Varshith has thrice as much money as Ayush. Ayush has 20% more than Tarun has. If the average of the amounts they have is Rs 116, how much money does Varshith have?

Build the table together: *"Who has no comparison — start there."* Tarun = x. *"Ayush has 20% more than Tarun."* Ayush = 1.2x. *"Varshith has thrice Ayush."* Varshith = 3.6x. Then solve for the average together.

**Answer: 216.**
Average: (x + 1.2x + 3.6x) / 3 = 116 → 5.8x = 348 → x = 60. Varshith = 3.6 × 60 = **216**.

**When it goes wrong**

| If… | Do this |
|---|---|
| Students start with Varshith's column first | It depends on Ayush, which depends on Tarun — reorder: always start from the variable with no dependency. |
| Students write Ayush = Tarun + 20 (flat addition) | They're treating "20% more" as "+20" instead of ×1.2. Point back to the percentage-change formula. |
| Students set sum = 116 instead of sum/3 = 116 | Remind: average = sum ÷ count. |

**Debrief line:**
> *"The table-building was the actual work. Once the columns were right, the equation solved itself."*

**Cut rule:** if running short, skip the bonus % error problem entirely — the ratio-table problem alone carries the session's content.

---

## Classroom Quiz (40–45 min) · Reserved — not yet available

No quiz bank exists yet for this Aptitude course (see Resources table). This 5-minute slot is reserved here, at the end of the session and right before the Exit Ticket, so the plan doesn't need restructuring once a quiz bank is added. Until then, run the dropped vendor/oranges base-switching problem here instead — "sells 70%, throws away 20% of what's left, sells 50% next day..." — or fold the slot into Buffer and end early.

---

## Exit Ticket + Homework (45–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> Pavan's salary is 40% more than Prudhvi's. By what percentage is Prudhvi's salary less than Pavan's?
> **Answer: 28.5714%** (not 40% — different bases).

Scan responses on the way out. Anyone who writes 40% has not yet absorbed today's central trap — flag them for a quick recheck at the start of Session 12.

**Homework**

No MCQ or coding-practice bank exists yet for this topic, so homework is the deck's own problem set, reworked from scratch:

| Task | Source |
|---|---|
| Rework Sai's salary problem and Lohitha's salary problem without looking at today's board work | `NIAT_Percentages 1.pptx` — slides 7–8 |
| Rework the fraction problem, the dal problem, and the Pavan/Prudhvi problem | `NIAT_Percentages 1.pptx` — slides 9–11 |
| Redo the vendor-oranges, dried-grapes, and Varshith/Ayush/Tarun problems, plus the 3/5-vs-5/3 error problem | `NIAT_Percentages 1.pptx` — slides 13–16 |

Tell them: *"Every number in tonight's homework is a problem you already saw today. If you can't get the same answer twice, that's exactly what to bring to me before Session 12."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock and want an extra problem instead of ending early, run the optional dried-grapes problem: *"Fresh grapes contain 80% water by weight, dried grapes 40% water by weight. What is the weight of dry grapes from 20 kg of fresh grapes?"* Solid matter = 20% of 20kg = 4kg, unchanged on drying. In dried grapes, solids = 60% of dried weight → dried weight = 4 ÷ 0.6 = **6.66 kg**. Never required.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Two successive % changes just add up (10% + 10% = 20%) | Percentages "feel" additive from school arithmetic | Sai's example (Slide Block A) — 10% then 10% is 21%, not 20% |
| A % increase and the % decrease that undoes it are the same number | 40→60 "looks like" it should reverse at the same rate | The hook and Slide Block A's 40/60/40 kmph illustration |
| "A is x% more than B" means "B is x% less than A" | Both statements use the same number x | The Pavan/Prudhvi problem — 40% more only means 28.5714% less |
| To keep expenditure flat after a price rise, cut consumption by the same % | The rise and the needed cut "should" cancel symmetrically | The dal problem — a 10% price rise needs only a 9 1/11% consumption cut |
| In multi-step % problems, percentages of different remaining amounts can just be added | No visible cue that the "20%" and the "50%" are of different bases | Slide Block B's chained-remainder beat — 20% of 30% and 50% of 24% are not interchangeable with 20% and 50% of the original |

---

## Instructor Notes

- **This plan is grounded entirely in local pptx text-extraction** (`NIAT_Percentages 1.pptx` for this session, Session 10's deck for the warm-up poll). No platform unit IDs, classroom quiz bank, or MCQ/coding-practice bank exist yet.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Think-Pair-Share (Lohitha's mixed-sign case), Activity 2 is Guided Table Build (the ratio problem). The original Rapid Fire Board Race activity is folded into a 2-minute chained-remainder beat inside Slide Block B, with the dried-grapes problem demoted to an optional buffer closer.
- <!-- placement: inferred --> Slide 4's formula slide and the successive-change rule's speaker-note wording — confirm the live slide's actual content before class.
- <!-- placement: inferred --> Slide 3's extracted text repeats "Ranking" twice — almost certainly a template artifact, not real agenda content.
- **The classic successive-change trap is the spine of this session.** Sai's example (10%+10%≠20%) is the first and clearest demonstration — don't rush past it.
- **No classroom quiz means the two cold-call checkpoints (19 min, 37 min) are your only real-time read on the room.** Don't skip them even if running behind.
