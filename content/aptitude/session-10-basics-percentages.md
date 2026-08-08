# Session 10 — Basics Percentages

**Duration** 60 min · **Topic** Percentages — Basic Calculations & Decimal/Fraction Conversion · **Prerequisite** Session 9 (Company-Specific MCQs — LCM & HCF)
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet for this topic — everything below is grounded in the local source deck only.

> **Style flag (read before you teach this):** this deck is genuinely light on solved "Ans:" problems compared to others in the course. That is not a content gap — it's a drill/reference deck. Its real content is (a) the 10%/1% mental building-block method for computing a% of a number, and (b) a fraction↔percentage equivalents table (1/2 through 8/9, plus a "Magic Circle of 1/7" trick for sevenths) meant to be memorised for speed. This plan builds objectives and activities around **fluency and speed with the method and the table**, not manufactured word problems the deck doesn't contain. See Instructor Notes.

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT_ Basics Percentages.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Recall the fraction-to-percentage equivalents for 1/2 through 8/9 from the master table (e.g. `2/3 = 66.66%`, `5/8 = 62.5%`, `7/9 = 77.77%`). *(REMEMBERING)*
2. State the 10%/1% "building-block" method for finding a% of any number — build the needed percentage from `100%`, `10%`, and `1%` of the number, then add or subtract. *(UNDERSTANDING)*
3. Compute a percentage of a number mentally by combining 10% and 1% building blocks (e.g. `51% of 82`, `98% of 82`). *(APPLYING)*
4. Apply fraction shortcuts (`2/3`, `5/8`, `7/9`, `2/7`, etc.) to calculate awkward repeating-decimal percentages such as `66.66%`, `77.77%`, and `28.5714%` of a number, faster than the building-block method allows. *(APPLYING)*
5. Use the Magic Circle of 1/7 pattern to identify `1/7` and `2/7` as percentages without long division. *(ANALYZING)*
6. Distinguish which method — 10%/1% building blocks vs. the fraction-shortcut table — is faster for a given percentage, and justify the choice. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 9, LCM & HCF (0–7 min)

7 questions on **Session 9's Company-Specific MCQs**. Newly authored, grounded in that deck's real worked numbers and answer keys. Mixed MCQ/MSQ, ~45 s each, project the distribution, never name individuals.

**Q1.** *(MSQ — select all)* The LCM of three numbers A, B and C is 1024. Which of the following **could** be the HCF of A, B and C?
`A` 8 · `B` 124 · `C` 32 · `D` 256
→ **A, C, D.** *Targets:* HCF must be a factor of the LCM. `1024 = 2^10`, so any power of 2 up to `2^10` qualifies; `124 = 4 × 31` does not divide 1024 at all. *Misconception:* picking 124 as a valid HCF without checking divisibility.

**Q2.** The HCF of two numbers is 11, and their LCM is 693. One of the numbers is 99. What is the other?
`A` 12 · `B` 45 · `C` 77 · `D` 34
→ **C, 77.** *Targets:* Product of two numbers = HCF × LCM → `(693 × 11) / 99 = 77`.

**Q3.** What is the smallest four-digit number that is divisible by 18, 24, and 32?
`A` 1152 · `B` 1512 · `C` 1216 · `D` 1680
→ **A, 1152.** *Targets:* find LCM(18,24,32) = 288, then adjust the smallest 4-digit number (1000) up to the next multiple of 288.

**Q4.** A number X leaves a remainder 2 when divided by 3, 4, 5, and 6. What is the smallest possible value of X?
`A` 62 · `B` 56 · `C` 128 · `D` 32
→ **A, 62.** *Targets:* LCM(3,4,5,6) = 60, then X = 60 + 2. *If >40% wrong:* re-run it on the board — "same remainder for every divisor" always means LCM + remainder.

**Q5.** A, B, and C run laps of a circular park in 252, 308, and 198 seconds respectively, all starting together from the same point. After what time will they next meet at the starting point?
`A` 46 min 10 sec · `B` 46 min 12 sec · `C` 40 min 45 sec · `D` Cannot be determined
→ **B, 46 min 12 sec.** *Targets:* "meet again at the start" = LCM of the individual lap times → LCM(252, 308, 198) = 2772 seconds = 46 min 12 sec.

**Q6.** What is the H.C.F. of the fractions `4/9`, `10/21`, and `20/63`?
`A` 4/189 · `B` 20/21 · `C` 6/63 · `D` 2/63
→ **D, 2/63.** *Targets:* HCF of fractions = HCF(numerators) / LCM(denominators) → HCF(4,10,20)=2, LCM(9,21,63)=63. *Misconception:* applying HCF and LCM the wrong way round for fractions — this is the last question, expect the lowest score here.

**Q7.** The ratio of two numbers is 1:2. If their HCF is 10, what is the sum of the two numbers?
`A` 30 · `B` 50 · `C` 35 · `D` 60
→ **A, 30.** *Targets:* Numbers = ratio × HCF → `1×10=10` and `2×10=20` → sum = 30.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–10 min)

Put this on the board, exactly as the deck's own opening example, and nothing else:

> **51% of 82 = ?**

Say: *"Ten seconds. No calculators, no pen-and-paper multiplication. Shout me a number."*

Let a few guesses land — they'll be slow or wrong, that's the point. Then:

> *"Here's the whole trick for today. You already know three easy facts about 82: 100% of 82 is 82. 10% of 82 is 8.2 — just slide the decimal one place. 1% of 82 is 0.82 — slide it again. Now, 51% is just 50% plus 1%. 50% of 82 is half of 82 — 41. Add the 1% — 0.82. **41.82.** That's it. No long multiplication."*

Tie it to yesterday:

> *"Yesterday, on LCM and HCF, you built answers out of prime factors — small, known pieces combined into a big answer. Today you're doing the exact same thing with 10% and 1% as your building blocks. Same idea, different bricks."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

Covers: the percentage formula (`Percent = ÷100`; `a% of b = (a/100) × b`), the Level 1 set of "clean" percent-of-number examples, and the Level 2 worked example (`51% of 82`) plus its harder companion (`98% of 82`).

**Beats to emphasise**

- **The formula is the definition, not the method.** State `a% of b = (a/100) × b` once, then immediately deprioritise it in favour of the building-block method — nobody should be doing that division by hand all session.
- **Level 1 — rapid mental fire on percentages that are clean multiples of 10.** Run through all six live, calling for shouted answers, building speed before the harder Level 2 example:
  - `20% of 200 = 40` · `40% of 50 = 20` · `70% of 70 = 49` · `40% of 30 = 12` · `60% of 40 = 24` · `20% of 1200 = 240`
  - Point out each is just "how many tens" — `20% of 200` is two lots of `10% of 200 (=20)`.
- **Level 2 — the 10%/1% combination for percentages that aren't clean multiples of 10.** Re-run the Hook's `51% of 82 = 41.82` on the slide itself (`(50+1)% of 82`), then hand the class the harder companion cold: `98% of 82 = ?`. Let a student attempt `(100−2)% of 82` before revealing.
  - `98% of 82`: `1% of 82 = 0.82` → `2% of 82 = 1.64` → `100% − 2% = 82 − 1.64 = 80.36`.
  - Say explicitly: *"Subtracting from 100% is exactly as valid as adding to 50% — pick whichever side of the number line is fewer steps away."*

**Checkpoint (at 22 min)** — cold-call:
> *"98% of 82 — go."*
> **Answer:** `80.36` (`100% of 82 = 82`, minus `2% of 82 = 1.64`).

---

## ⚡ Activity 1 — Rapid Fire Board Race (22–29 min)

### What this activity is

Teams race to compute four numbers from the deck's own "Find" slide — `66.66% of 66`, `62.5% of 160`, `77.77% of 198`, `28.5714% of 280` — using **only** the 10%/1% building-block method just taught in Slide Block A. No fraction shortcuts exist yet in this session; that's deliberate.

### Why it's here

This is the deck's own sequencing: it poses this exact "Find" set *before* teaching the fraction-percentage table, then re-poses the identical set *after* teaching the table. The first pass is meant to be painful. Building `66.66%`, `77.77%`, and `28.5714%` out of 10s and 1s produces messy, error-prone intermediate steps — that pain is what makes Slide Block B's fraction shortcuts land as relief rather than as an arbitrary extra thing to memorise.

### Before class

Split the board into two (or more) team halves. Have all four numbers ready to reveal together — this is a timed race against all four, not one at a time.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Split into teams, explain scoring rules | Listen, pick a runner |
| 0:30–1:00 | Reveal all four problems at once | Read |
| 1:00–5:00 | Run the race — teams work using only 10%/1% blocks | Runners write working + answer on the board |
| 5:00–6:30 | Score, reveal correct answers | Watch |
| 6:30–7:00 | Debrief — name the pain, set up Slide Block B | Listen |

### Say this

> *"Four numbers. Same method you just learned — tens and ones, nothing else. First team to all four correct answers, with the working visible, wins. Go."*

### The problems (real numbers, deck's "Find" slide)

1. `66.66% of 66`
2. `62.5% of 160`
3. `77.77% of 198`
4. `28.5714% of 280`

### Answers (via 10%/1% building blocks)

| # | Building-block route | Answer |
|---|---|---|
| 1 | `60% of 66 = 39.6` + `6% of 66 = 3.96` + `0.66% of 66 ≈ 0.44` | **≈ 44** |
| 2 | `60% of 160 = 96` + `2% of 160 = 3.2` + `0.5% of 160 = 0.8` | **100** (exact — 62.5 splits cleanly) |
| 3 | `70% of 198 = 138.6` + `7% of 198 = 13.86` + `0.77% of 198 ≈ 1.52` | **≈ 154** |
| 4 | `20% of 280 = 56` + `8% of 280 = 22.4` + `0.5714% of 280 ≈ 1.6` | **≈ 80** |

**How it surfaces:** #2 comes out clean and fast (62.5% behaves nicely even in tens/ones). #1, #3, and #4 involve repeating decimals at every step — teams will lose time to rounding and arithmetic slips, especially on #4. That contrast is deliberate; call it out.

**Debrief line:**
> *"Numbers 1, 3, and 4 were slow and messy — you were fighting repeating decimals the whole way. There's a faster tool for exactly these. That's what's coming next."*

**Cut rule:** If running long, race only problems 1 and 4 (the two messiest) and skip 2 and 3 — the pain point is what matters, not covering all four.

> **Classroom Quiz:** not yet available — add once question bank exists for this topic. Time reallocated into this activity, Slide Block B, and the Exit Ticket below; the 60-minute timeline has no gap where the quiz would have sat.

---

## Slide Block B (29–41 min) — DELIVER SLIDES AS-IS

Covers: the decimal-to-fraction conversion table (the fraction↔percentage master table, 1/2 through 8/9) and the Magic Circle of 1/7 trick, followed by the deck's own confirmation of `28.5714% of 280 = 80`.

**Beats to emphasise**

- **The master table is the payoff for Activity 1's pain.** Reveal it as the fix, not as a fresh unrelated fact:

  | | 1/2 | 1/3 | 1/4 | 1/5 | 1/6 | 1/8 | 1/9 |
  |---|---|---|---|---|---|---|---|
  | | 50% | 33.33% | 25% | 20% | 16.66% | 12.5% | 11.11% |

  | | 2/3 | 2/4 | 2/5 | 2/6 | 2/8 | 2/9 |
  |---|---|---|---|---|---|---|
  | | 66.66% | 50% | 40% | 33.33% | 25% | 22.22% |

  | | 3/4 | 3/5 | 3/6 | 3/8 | 3/9 |
  |---|---|---|---|---|---|
  | | 75% | 60% | 50% | 37.5% | 33.33% |

  | | 4/5 | 4/6 | 4/8 | 4/9 |
  |---|---|---|---|---|
  | | 80% | 66.66% | 50% | 44.44% |

  | | 5/6 | 5/8 | 5/9 |
  |---|---|---|---|
  | | 83.33% | 62.5% | 55.55% |

  | | 6/8 | 6/9 |
  |---|---|---|
  | | 75% | 66.66% |

  | | 7/8 | 7/9 |
  |---|---|---|
  | | 87.5% | 77.77% |

  | | 8/9 |
  |---|---|
  | | 88.88% |

  Now redo Activity 1's set instantly: `66.66% of 66 = 2/3 × 66 = 44`. `62.5% of 160 = 5/8 × 160 = 100`. `77.77% of 198 = 7/9 × 198 = 154`. One multiplication, no rounding. *"Same four answers you already fought for. Now it's one step."*
- **1/7 is deliberately missing from that table** — sevenths repeat over six digits, not one or two, so the deck gives them a separate trick: the **Magic Circle of 1/7**. `1/7 = 14.2857%`, and `2/7 = 28.5714%` — the same six digits (`1,4,2,8,5,7`), just starting from a different point in the cycle. <!-- placement: inferred --> The exact circular diagram's layout could not be recovered from text extraction (it's a diagram, not text); confirm the real slide's arrangement before drawing it live. The underlying fact — `2/7 = 28.5714%` — is confirmed by the deck's own next slide, so teach that fact with confidence even if the circle's exact drawing needs checking.
- **Close the loop on Activity 1, problem 4:** `28.5714% of 280` — the deck confirms this directly: **Ans: 80** (`2/7 × 280 = 80`), matching the messy `≈80` the class fought for by hand.

**Checkpoint (at 41 min)** — show hands:
> *"Using the Magic Circle, what is 2/7 as a percentage?"*
> **Answer:** `28.5714%` — confirmed on the deck's own slide, and it's exactly the percentage you'll use again in a moment.

---

## ⚡ Activity 2 — Human Calculator (41–48 min)

### What this activity is

A rapid-fire oral chain: you (or a student) call out a fraction from the master table, the next student has one second to shout back its percentage — or vice versa, percentage to fraction. No working, no pen. Pure recall speed on the table just taught.

### Why it's here

The whole point of Slide Block B's table is that these equivalents should be *known*, not recalculated, every time they're needed. This activity is the first rep at converting the table from "something I just saw" to "something I can say instantly," which Activity 1 already proved is worth doing.

### Before class

Have the full table (1/2 through 8/9) visible on the board or slide as a safety net for the first round only — cover it for round two.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, explain the chain rule | Listen |
| 0:30–5:30 | Call fractions/percentages rapid-fire down rows/across the class | Answer instantly, pass to next student |
| 5:30–6:30 | Cover the table, repeat with the trickier entries (`1/6`, `5/9`, `7/8`) | Answer from memory, no table visible |
| 6:30–7:00 | Debrief | Listen |

### Say this

> *"I say a fraction, you say its percentage — instantly, no working. Get it wrong or freeze, and it passes to the next person. We're not testing whether you can calculate this. We're testing whether you already know it."*

### The set (real table entries)

Round 1 (table visible): `1/2, 1/3, 1/4, 2/3, 3/4, 4/5, 5/6, 7/8` → `50%, 33.33%, 25%, 66.66%, 75%, 80%, 83.33%, 87.5%`

Round 2 (table covered — the harder ones): `1/6, 5/8, 5/9, 7/9, 2/9, 4/9` → `16.66%, 62.5%, 55.55%, 77.77%, 22.22%, 44.44%`

**When it goes wrong**

| If… | Do this |
|---|---|
| The chain stalls repeatedly on the ninths (`1/9` through `8/9`) | Point out the pattern: `n/9 = n × 11.11%` — `4/9 = 44.44%` because `4 × 11.11 ≈ 44.44`. This is a genuine shortcut inside the table, not just memorisation. |
| Students answer correctly but slowly (counting on fingers, muttering) | That's still progress from Activity 1, but push pace — the goal is instant, not eventually-correct. Run round 2 again faster. |
| Someone answers `1/6` as `16.6%` instead of `16.66%` | Minor — accept it, but note that the repeating decimal never actually terminates; the table's convention is two decimal places. |

**Common instructor mistake:** letting students glance at the table during round 2. Covering it is the entire point — round 1 is warm-up, round 2 is the actual test.

**Cut rule:** If running short, do round 1 only and skip round 2 — recognition with the table visible is still worth having, even without the recall-under-pressure round.

---

## ⚡ Activity 3 — Fill the Blank Live (48–55 min)

### What this activity is

Put the master table on the board with several cells blanked out. Cold-call students to fill the missing cells live. Close by re-solving Activity 1's four numbers one more time, now completely from memory, as the session's "payoff lap."

### Why it's here

Activity 2 tested oral recall. This activity tests recall in the table's actual written form — the shape students will actually see it in on a real problem — and then immediately spends that recall on a real calculation, closing the loop the deck itself opened back in Activity 1.

### Before class

Draw or project the full table with roughly a third of the percentage cells blanked out, spread across rows (not clustered on the "easy" halves/quarters).

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Reveal the blanked table, explain the format | Listen |
| 0:30–3:00 | Cold-call students to fill missing cells one at a time | Come to the board, fill a cell, explain briefly |
| 3:00–5:30 | Re-pose Activity 1's four numbers, from memory, fraction-only this time | Solve individually or as one class-wide pass |
| 5:30–7:00 | Reveal final answers, debrief the full arc | Listen |

### Say this

> *"Table's up, some cells are missing. I'll point, you fill it and tell me why. Once it's complete, we're doing Activity 1's four numbers one more time — except this time you already have the tool, so watch how fast it goes."*

### The blanked cells (sample — vary which you blank)

`1/6 = ___` → `16.66%` · `3/8 = ___` → `37.5%` · `5/9 = ___` → `55.55%` · `___= 44.44%` → `4/9` · `___ = 87.5%` → `7/8`

### The payoff — Activity 1's set, solved from the table

| # | Problem | Fraction | Answer |
|---|---|---|---|
| 1 | `66.66% of 66` | `2/3` | **44** |
| 2 | `62.5% of 160` | `5/8` | **100** |
| 3 | `77.77% of 198` | `7/9` | **154** |
| 4 | `28.5714% of 280` | `2/7` (Magic Circle) | **80** |

**When it goes wrong**

| If… | Do this |
|---|---|
| A student fills a cell with the wrong fraction-family value (e.g. confuses `3/8` with `3/9`) | Point at the denominator column, not the percentage — the mistake is always in matching the right family, not the arithmetic. |
| The class solves the payoff set slower than expected | That's useful data, not a failure — it tells you the table isn't fully memorised yet. Say so plainly and assign Activity 2's round 2 set as extra homework drill. |
| Someone reaches for 10%/1% building blocks again out of habit for problem 4 | Let them — then time it against a neighbour who used `2/7` directly. The speed gap makes the point better than you saying it. |

**Common instructor mistake:** rushing straight to the payoff set without genuinely blanking and cold-calling the table first — the fill-in step is what proves the table is memorised, not just seen.

**Cut rule:** If running short, blank only 3 cells instead of 5, and go straight to the payoff set — problems 1 and 4 only (the two that show the biggest before/after speed contrast).

---

## Exit Ticket + Homework (55–60 min)

**Exit ticket** — on paper before anyone leaves:

> What is 40% of 66.66% of 25% of 75% of 1200?
> **Answer: 60.** (`75% of 1200 = 900` → `25% of 900 = 225` → `66.66% (2/3) of 225 = 150` → `40% of 150 = 60`.) This is the deck's own closing problem — it chains three table fractions and one building-block step in a single line, which is exactly today's two skills used together.

Scan responses on the way out. If the chaining (working left-to-right, one step feeding the next) is the sticking point rather than any individual percentage, open the next session with a 2-minute recap of just that chaining habit.

**Homework**

> Memorise the fraction-percentage table — 1/2 through 8/9 — cold, for tomorrow. No table, no notes: you should be able to say `5/8` as `62.5%` and `77.77%` as `7/9` without pausing. Also re-attempt, from memory, `28.5714% of 280` using the Magic Circle of 1/7, and re-derive `51% of 82` and `98% of 82` using the 10%/1% building blocks. Bring your working — you already have every answer from today's board work.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Defaulting to long multiplication (`51 × 82 ÷ 100`) instead of the 10%/1% building blocks | It's the method taught in school; feels "safer" even though it's slower | The Hook and Slide Block A's checkpoint — visibly build `51%` and `98%` from `100%`, `10%`, `1%` on the board instead of multiplying out |
| Trying to build every awkward percentage (`66.66%`, `77.77%`, `28.5714%`) out of 10%/1% blocks, even after the fraction table is taught | It's the only tool available in Activity 1, and old habits stick | Activity 1's deliberately exposed pain, contrasted directly with Activity 3's payoff lap on the same four numbers |
| Believing fraction-percentage equivalents beyond `1/2`, `1/4`, `3/4` must be recalculated each time rather than simply known | Never previously told these are fixed, memorisable facts | Activity 2 (Human Calculator) drilling the table with the reference covered, until responses are instant |
| Losing track of place value when scaling a percentage (e.g. computing `28.5714% of 28` instead of `28.5714% of 280`) | The deck's own two presentations of this exact problem show the slip — slide 6 says "of 28", the corrected re-ask after the table says "of 280" | Point out the correction directly in Slide Block B / Activity 3, and re-derive `2/7 of 280 = 80` so the corrected number is the one that sticks |
| Assuming `100% − 2%` requires recomputing `98 × 82` from scratch, rather than subtracting `2 × (1%)` from the whole | Subtraction-from-100 isn't the "default" direction taught first | Slide Block A's `98% of 82` checkpoint — show the full working, then ask which was faster |

---

## Instructor Notes

- **This deck is intentionally light on solved "Ans:" problems.** It's a drill/reference deck teaching one method (10%/1% building blocks) and one lookup table (fraction↔percentage equivalents plus the Magic Circle of 1/7), not a word-problem deck. Every objective and activity in this plan targets fluency and speed with that method and table — no word problems were manufactured to pad out the session, per the source.
- **No platform unit IDs, classroom quiz bank, or MCQ/coding-practice pool exist for this topic yet.** This plan is grounded entirely in local text-extraction of `NIAT_ Basics Percentages.pptx` (this session) and `2) NIAT_CSMCQ'S_LCM & HCF.txt` (Session 9, used only to ground the warm-up poll). No unit IDs were invented anywhere in this document.
- **Both "Quiz Time" slides in the deck (after the Level-2 "Find" set, and again near the end) contain no extractable question text** — likely images or an interactive polling element that text-extraction can't recover. These are not the missing classroom-quiz block referenced above; they simply couldn't be read, so nothing from them appears in this plan. <!-- placement: inferred -->
- **The deck's own drill set has two versions of item 4**, and this plan uses the corrected one throughout (Activity 1 and Activity 3): the first "Find" slide (before the fraction table is taught) says `28.5714% of 28`; the second "Find" slide (after the table is taught) corrects it to `28.5714% of 280`, and a later slide confirms the answer as `80` — which only works for `280`, not `28`. Use `280`. <!-- placement: inferred -->
- **The Magic Circle of 1/7's exact circular diagram could not be recovered from text extraction** — a diagram's spatial layout doesn't survive as text. The underlying facts used in this plan (`1/7 = 14.2857%`, `2/7 = 28.5714%`, six repeating digits `1,4,2,8,5,7`) are confirmed by the deck's own adjacent slides and are safe to teach; only the physical circle drawing needs verifying against the real slide before you draw it live. <!-- placement: inferred -->
- **Warm-up poll selection:** 7 of the available Session 9 problems were chosen for a recall → application → analysis ramp. Two Session 9 problems were deliberately left out of the poll and are available as backups if you want extra retrieval practice: the co-prime "sum of three numbers" problem (answer 65), and the "ratio 3:2, LCM=60" problem — flagged here because the deck's own question states the ratio as 3:2 but its worked solution proceeds using 2:3 to reach the answer (20 and 30); if you use it live, be ready for a sharp student to notice the mismatch, and don't silently "fix" the deck's wording without saying so.
- **Timeline reallocation:** with no classroom quiz to run, its usual 7 minutes were redistributed rather than left as a gap — Activity 1 gained 2 minutes (to let the "painful" building-block race actually play out on all four numbers), Slide Block B gained 2 minutes (the master table is dense), Activity 2 gained 1 minute, and the Exit Ticket gained 2 minutes (the closing chained problem needs room to work through, not just state). Total is still 60 with no gaps: Warm-Up 0–7, Hook 7–10, Slide Block A 10–22, Activity 1 22–29, Slide Block B 29–41, Activity 2 41–48, Activity 3 48–55, Exit Ticket + Homework 55–60.
- **Have the master table already drawn on a spare board or slide before class starts.** Activities 2 and 3 both depend on it being instantly available (or instantly coverable) — building it live from scratch mid-activity burns minutes you don't have.
