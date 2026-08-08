# Session 23 — Problems on Ages

**Duration** 60 min · **Topic** Problems on Ages · **Prerequisite** Session 22 — Partnerships
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist for this course yet.

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT_Ages.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the two core translation rules for age problems — "X years ago" subtracts from a present age, "Y years from now" adds to it — before writing any equation. *(REMEMBERING)*
2. Convert a descriptive age statement (e.g. "I was as old as you are now, at the time of your birth") into a correct algebraic equation. *(APPLYING)*
3. Distinguish "three times more than" (4x) from "three times as old as" (3x), and identify other phrasing that changes a multiplier or a sign. *(ANALYZING)*
4. Solve a linear age equation for a present age and use it to answer a shifted-time follow-up question ("five years back", "after 6 years"). *(APPLYING)*
5. Set up a three-person ratio of ages by expressing every person's age in terms of one shared variable. *(APPLYING)*
6. Apply the sum-of-observations method (weighted average) to find an unknown group's average age when a combined group's average shifts after new members join. *(APPLYING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

8 questions on **Session 22 (Partnerships)**. Real numbers from that deck. ~45 s each, project the distribution, never name individuals.

**Q1.** When partners invest for the *same* time period, what decides each partner's profit share?
`A` Number of partners · `B` Amount each partner invested · `C` Who manages the business · `D` Alphabetical order of names
→ **B.** *Targets:* Session 22's opening rule — "profit share depends upon the amount invested."

**Q2.** When partners invest for *different* time periods, the profit ratio is calculated using:
`A` Investment only · `B` Time only · `C` Investment × Time · `D` Investment ÷ Time
→ **C.** *Targets:* "Profit ratio = Investment × Time period" — the rule behind Session 22's last worked example.

**Q3.** A and B invested Rs.1,20,000 and Rs.1,50,000. What is the simplified investment ratio?
`A` 4 : 5 · `B` 5 : 4 · `C` 2 : 3 · `D` 3 : 2
→ **A** (120000:150000 = 4:5). *Targets:* reducing capital figures to a ratio before splitting profit.

**Q4.** Using that 4:5 ratio, if the annual profit is Rs.27,000, what is B's share?
`A` Rs.12,000 · `B` Rs.15,000 · `C` Rs.13,500 · `D` Rs.10,000
→ **B** (5/9 × 27,000 = 15,000). *Targets:* applying a ratio to a total, the real Session 22 answer.

**Q5.** A & B invest in the ratio 3:2. 5% of the total profit goes to charity. What fraction of the total profit is actually split between A and B?
`A` 100% · `B` 95% · `C` 90% · `D` It depends which partner
→ **B.** *Targets:* Session 22's charity-deduction problem. *Misconception:* applying the 3:2 ratio to the full profit and forgetting the 5% is removed first — the exact trap the deck's own hint ("only 95% is shared") warns against.

**Q6.** A, B, C invest Rs.2,100, Rs.2,400 and Rs.2,700. What is the simplified investment ratio?
`A` 7 : 8 : 9 · `B` 3 : 4 : 5 · `C` 1 : 2 : 3 · `D` 21 : 24 : 27
→ **A** (divide each by 300). *Targets:* same reduce-the-ratio skill with three partners instead of two.

**Q7.** *(MSQ — select all)* A partner withdraws half their capital partway through the year. Which of these correctly account for that? *Targets:* Session 22's "B took back half the investment" problem.
`A` Split that partner's investment into two time-slices with different capital amounts
`B` Ignore the withdrawal and use the original investment for the full year
`C` Multiply each capital slice by the number of months it was actually invested
`D` Only count investment from the day the business started
→ **A and C.** *Misconception:* B is the shortcut students default to when the numbers get messy.

**Q8.** Before splitting Rs.5,783 among A, B, C in the ratio 4:6:9, Session 22's deck first deducted Rs.28, Rs.37 and Rs.18 from their shares. Why was that deduction step necessary?
`A` The deductions are taxes and unrelated to the ratio
`B` The ratio 4:6:9 applies only to the amount left *after* the deductions are removed
`C` The deductions get added back in at the end regardless of the ratio
`D` The deductions cancel out and can be ignored
→ **B.** *Targets:* the deduct-first-then-ratio sequencing. *Misconception:* applying the ratio to the full Rs.5,783 directly.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–10 min)

Say nothing yet — write this on the board:

> *"I am three times older than my son."*

Ask: *"Is my age exactly 3 times his, or 4 times his? Vote with fingers — 1 or 2."*

Let the room split. Then say:

> *"Both readings are defensible in plain English — and that's the problem. Mathematically, 'three times older than' means my age *exceeds* his by three times his age: his age plus three times his age. That's **4x**, not 3x. English is sloppy. Algebra is not. Today's entire chapter is one skill: read the sentence precisely, and turn each phrase into one line of an equation."*

Write the two translation rules on the board and leave them up for the whole session:

> **"X years ago" → subtract X from a present age.**
> **"Y years from now / hence" → add Y to a present age.**

Close the hook:

> *"That's it. No new formulas today — just careful translation, one sentence at a time. Last session you converted investment statements into ratios; today every statement about someone's age becomes an equation the exact same way."*

---

## Slide Block A (10–24 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — the deck has no explicit section headers; block boundaries are inferred from the deck's own two "Quiz Time" slides (slide 9 and slide 13), which naturally split the content into two halves -->

Covers: *Ages* title slide → **P1** (father 3x-more-than son Ronit) → **P2** (5 children born at 3-year intervals) → **P3** (father: "I was as old as you are now, at your birth") → **P4** (father+son sum of ages, 6-years-ago condition).

**Beat 1 — "Translate the phrase, not the vibe" (P1, P3)**

- **P1:** *"Father is aged three times more than his son Ronit. After 8 years, he would be two and a half times of Ronit's age. After further 8 years, how many times would he be of Ronit's age?"* Set Ronit = x, father = **4x** (the hook's trap). Equation: `4x + 8 = 2.5(x + 8)` → x = 8. After a further 8 years (16 years from now): father = 48, Ronit = 24 → ratio = **2 times**. Deck's own hint: *"Understand the sentence 'three times more than.'"*
- **P3:** *"A father said to his son, 'I was as old as you are at the present at the time of your birth.' If the father's age is 38 now, the son's age five years back was?"* Translate: father's age at son's birth = son's present age → `father − son = son` → father = 2 × son → son = 19. Five years back: **14**. Deck's hint: *"Understand the sentence and convert it into an equation."*

**Beat 2 — "One variable, several people" (P2, P4)**

- **P2:** *"The sum of ages of 5 children born at intervals of 3 years each is 50. What is the age of the youngest child?"* Let youngest = x: `x + (x+3) + (x+6) + (x+9) + (x+12) = 50` → 5x + 30 = 50 → **x = 4**.
- **P4:** *"The sum of the present ages of a father and his son is 60. Six years ago, father's age was five times the son's. After 6 years, son's age will be?"* `f + s = 60` and `f − 6 = 5(s − 6)`. Solving: s = 14, f = 46. After 6 years, son's age = **20**.

**Checkpoint (at 24 min)** — cold-call one student:
> *"For P4 — write me the second equation, the one from 'six years ago.' Don't solve it, just write it."*
> **Answer:** `f − 6 = 5(s − 6)`. (If the student instead writes `f = 5(s − 6) − 6` or `f − 6 = 5s − 6`, that's the sign/distribution trap Activity 3 is built around — flag it now, resolve it later, don't over-explain.)

---

## ⚡ Activity 1 — Rapid Fire Board Race (24–30 min)

**Format:** Rapid Fire Board Race · **Built from:** the deck's own **P1** and **P2**, already delivered in Slide Block A · **Exposes:** whether the "4x, not 3x" translation rule actually stuck, under time pressure.

**Why here:** The real deck places a "Quiz Time" slide (slide 9) at exactly this point, right after these four problems. No question text survives in the extraction for that slide, so this activity rebuilds that same checkpoint moment using the deck's own already-taught problems, in a race format rather than a re-lecture.

**Before class:** Split the board into two halves, one per team. Do not project P1 or P2's text — you will read it aloud.

**Run it**

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line | Listen |
| 0:30–1:00 | Read P1 aloud, twice | Listen only, no writing yet |
| 1:00–2:30 | Say "go" | One runner per team writes only the **equation**, not the answer |
| 2:30–3:00 | Reveal correct equation, award point | Watch |
| 3:00–3:30 | Read P2 aloud, twice | Listen |
| 3:30–5:00 | Say "go" | Second runner per team writes the equation |
| 5:00–6:00 | Reveal, tally, debrief | Watch |

**Say this:**
> *"Two teams, one board each. I read a problem aloud twice — no repeats after that. Your runner writes the equation, not the answer. First correct equation on the board wins the point. Ready?"*

**Answers**

| # | Correct equation | Common wrong equation (the trap) |
|---|---|---|
| P1 | `4x + 8 = 2.5(x + 8)` | `3x + 8 = 2.5(x + 8)` — reading "3 times more than" as 3x |
| P2 | `x + (x+3) + (x+6) + (x+9) + (x+12) = 50` | `5x = 50` — forgetting the interval offsets entirely |

**When it goes wrong**

| If… | Do this |
|---|---|
| A team writes `3x` for P1 | Don't correct immediately — let the other team finish, then run both equations' final answers live so the numbers themselves expose the error. |
| Both teams stall on P2 | Give a 15-second hint: "how many children come after the youngest, and by how much each?" |
| One team finishes instantly | Ask them to explain their equation out loud before awarding the point — speed without reasoning doesn't count. |

**Common instructor mistake:** revealing "it's 4x, not 3x" before both runners commit to the board — this kills the diagnostic value of the race.

**Cut rule:** If short on time, run only the P1 race and skip P2 — P1 carries the session's core trap; P2 is reinforcement.

---

> **Classroom Quiz: not yet available — add once question bank exists for this topic.**
> *(0 min — this slot's usual 27–34 min allocation has been redistributed into Slide Block A, Slide Block B, and Activities 1–3 above and below, so the 60-minute timeline below has no gap where it would have sat.)*

---

## Slide Block B (30–42 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — second half of the deck, bounded by the deck's second "Quiz Time" slide (slide 13) -->

Covers: **P5** (person is 2/5 of mother's age) → **P6** (Sam, Rita, father ratio) → **P7** (average age of boys, class of 30).

**Beat 1 — "Fractions of someone else's age" (P5, P6)**

- **P5:** *"A person's present age is two-fifths of his mother's. After 8 years, he will be one-half of his mother's age. How old is the mother at present?"* Let mother = m, person = 2m/5. `2m/5 + 8 = (m + 8)/2` → **m = 40**. Deck's hint: *"Convert statements into the mathematical equation."*
- **P6:** *"Sam's age is one-fourth of his father's age and two-thirds of his sister Rita's. What is the ratio of Sam, Rita, and father's ages respectively?"* Sam = x → father = 4x (Sam = ¼ father) and Rita = 1.5x (Sam = ⅔ Rita). Ratio Sam : Rita : Father = x : 1.5x : 4x = **2 : 3 : 8**. Deck's hint: *"Express the ages of Father and Rita in terms of Sam."*

**Beat 2 — "When the ages belong to a group, not a person" (P7 — the deck's own "Weighted average" bridge from Mixtures & Alligations, per the speaker notes on the Agenda slide)**

- **P7:** *"The average age of boys in a class of 30 is 15 years. If 10 more boys join, the average of the whole class reduces by a year. What is the average age of the newcomers?"* Total age of original 30 = 30 × 15 = 450. New average = 14, new total students = 40 → new total age = 560. Newcomers' total age = 560 − 450 = 110. Newcomers' average = 110 / 10 = **11**. Deck's hint: *"Average = Sum of observations / Total number of observations."*
- Say explicitly: *"This is the same weighted-average logic from Mixtures & Alligations — you never average two averages directly. You go back to totals every time."*

**Checkpoint (at 42 min)** — show hands:
> *"For P7 — can I just average 15 and the newcomers' average directly to get the class's new average? Yes or no, and why?"*
> **Answer:** No — the two groups are different sizes (30 vs 10), so a simple average of the two averages is wrong. You must work with total sums (450 and 560), because that's the only thing that adds correctly across differently-sized groups.

---

## ⚡ Activity 2 — Trace the Table (42–49 min)

**Format:** Trace the Table · **Built from:** **P6** (Sam, Rita, father) · **Exposes:** the shortcut of writing every person's age directly instead of anchoring all of them to one shared variable.

**Why here:** Three-person ratio problems are exactly where students skip the anchor variable and try to juggle two fractions in their head at once. A table forces the anchor.

**Before class:** Draw a 2-row table on the board: columns **Sam | Rita | Father**, one row for "in terms of Sam", one row for "ratio".

**Run it**

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, re-read P6's exact statement | Listen |
| 0:30–1:30 | Point at the "Sam" cell | Say: "Let Sam = x" |
| 1:30–3:30 | Point at "Father" cell, then "Rita" cell | Fill each in terms of x, justifying from the sentence |
| 3:30–5:30 | Point at the ratio row | Convert x : 1.5x : 4x into whole-number ratio |
| 5:30–7:00 | Debrief | Listen |

**Say this:**
> *"One student, one cell. I point, you fill it in — in terms of Sam, using the exact wording of the problem. No ratios yet, just algebra."*

**Answers**

| | Sam | Rita | Father |
|---|---|---|---|
| In terms of Sam | x | 1.5x (since Sam = ⅔ Rita → Rita = 1.5 Sam) | 4x (since Sam = ¼ Father → Father = 4 Sam) |
| Ratio (×2 to clear the decimal) | 2 | 3 | 8 |

Final ratio: **2 : 3 : 8**.

**When it goes wrong**

| If… | Do this |
|---|---|
| A student writes Father = x/4 instead of 4x | Re-read the sentence aloud: "Sam's age is one-fourth of his father's age" → Sam = ¼ Father → Father must be *bigger*. Don't just correct the algebra — make them re-hear the sentence. |
| Someone tries to write Rita or Father's age without going through Sam | Stop them: "In terms of *Sam*, not in terms of anything else." The constraint is the point. |
| Table fills too fast, no discussion | Ask a second student to justify each cell before moving to the next. |

**Common instructor mistake:** filling in the algebra yourself when a student stalls — wait the full 60 seconds before rescuing.

**Cut rule:** If short on time, skip converting the ratio to whole numbers verbally — just state 2:3:8 and move on.

---

## ⚡ Activity 3 — Spot the Bug (49–57 min)

**Format:** Spot the Bug · **Built from:** **P4**'s "six years ago" condition, re-used to isolate the sign trap, plus a quick **Predict the Output** round on **P5** as the closer (tying into the deck's second "Quiz Time" slide 13, which sits at this point in the real deck) · **Exposes:** the exact misconception flagged for this session — setting up "X years ago" with the wrong sign or without distributing it to both people.

**Why here:** P4 was solved correctly in Slide Block A, but students rarely notice *why* their own first attempt at these problems tends to go wrong. Showing two competing wrong setups side-by-side against the correct one makes the trap visible rather than abstract.

**Before class:** Write all three equations for P4's "six years ago" condition on the board, unlabelled:

```
(a)  f − 6 = 5(s − 6)
(b)  f = 5(s − 6)
(c)  f − 6 = 5s − 6
```

**Run it**

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, restate P4 ("father+son=60, six years ago father was 5× son") | Listen |
| 0:30–2:00 | Show all three equations | Diagnose silently, no talking |
| 2:00–5:00 | Take votes on which is correct, then take the reasoning | Explain why (b) and (c) fail |
| 5:00–7:00 | Quick Predict round: read P5 aloud, ask for the mother's age before solving | Call out predictions |
| 7:00–8:00 | Reveal P5's answer, debrief | Listen |

**Say this:**
> *"Three versions of the same 'six years ago' condition. Only one is correct. Vote a, b, or c — then tell me exactly what's wrong with the other two, in words, not symbols."*

**Answers**

| # | Verdict | What's wrong |
|---|---|---|
| (a) | **Correct** | Both the father's and the son's ages are shifted back 6 years before the ×5 relationship is applied |
| (b) | Wrong | Forgot to subtract 6 from the father's *own* age — only the son's age was shifted back |
| (c) | Wrong | Distributed the ×5 onto `s` but not onto the `−6` inside the bracket — a distribution error, not a translation error |

Then run the Predict round on **P5** (*"present age is two-fifths of mother's; after 8 years, half of mother's age — how old is the mother?"*). Take votes, then reveal: **40**.

**When it goes wrong**

| If… | Do this |
|---|---|
| Nobody picks (b) or (c) as wrong, both look "fine" | Plug s = 14 into all three and show only (a) gives f = 46, matching `f + s = 60`. Let the numbers argue for you. |
| Room fixates on symbol-shuffling instead of the sentence | Pull them back: "six years ago, whose age changes? Both people's, or just one's?" |
| Predict round on P5 runs long | Cap votes at three call-outs, then reveal immediately. |

**Common instructor mistake:** explaining the distribution error in (c) using only algebra vocabulary ("you didn't distribute") without re-reading the plain-English sentence — students who are shaky on algebra need the sentence, not the jargon, to catch it.

**Cut rule:** If short on time, drop the Predict round on P5 and go straight to the exit ticket — the sign-trap diagnosis (a)/(b)/(c) is the non-negotiable part of this activity.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — on paper or in chat before anyone leaves:

> A person's present age is two-fifths of his mother's age. After 8 years, he will be one-half of his mother's age. How old is the mother at present?
> **Answer:** 40.

Scan responses on the way out — this is P5, already revealed in Activity 3's Predict round, so it's a genuine recall check on whether the reveal actually landed, not a new problem.

**Homework**

- Re-attempt **P1, P2, P3, P4, and P6** from today's deck (`NIAT_Ages.pptx`) from scratch, without looking at the on-slide hints. Write the equation *before* solving, every time — that ordering is the entire point of this session.
- Revisit Session 22's (`NIAT_Partnerships.pptx`) time-weighted investment-ratio problem (Investment × Time). It's the same "go back to the totals, don't shortcut the average" logic as today's P7 — comparing the two side by side is deliberate reinforcement.

Tell them: *"Every one of these problems is solvable in under two minutes once the equation is right. If you're stuck for longer than that, the equation — not the arithmetic — is where to look."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| "Three times more than" means 3x | Everyday speech uses "times more" and "times as much" interchangeably | The Hook, then P1 in Slide Block A and Activity 1's board race |
| "X years ago" only shifts one person's age, not both | Students shift the person named in the sentence's second half and forget the first | Activity 3's Spot the Bug — equation (b), plugging numbers back in |
| Distributing a multiplier across a bracket is optional bookkeeping | Weak algebra fluency, not an ages-specific gap | Activity 3's equation (c), read aloud as a sentence, not just symbols |
| In a 3-person ratio, each person's age can be written straight from the sentence they're mentioned in | Feels faster than routing everything through one shared variable | Activity 2 — Trace the Table forces the Sam-anchor |
| You can average two group averages directly | Averaging averages "feels" like averaging | Slide Block B checkpoint and P7 — insist on totals (sum ÷ count) every time |

---

## Instructor Notes

<!-- placement: inferred -->
- **Slide Block A / B split is inferred, not marked in the deck.** The extraction has no section headers; the split follows the deck's own two "Quiz Time" slides (slide 9 after P1–P4, slide 13 after P5–P7), which is the only structural signal available. Confirm against the live deck and adjust if the actual delivery order differs.
- **This plan is grounded entirely in local pptx text-extraction** (`NIAT_Ages.pptx` via its extracted text, and `NIAT_Partnerships.pptx` for the warm-up poll) — there is no platform export for this Aptitude course yet, so no unit IDs, quiz-bank IDs, or question IDs exist to cite. None have been invented anywhere in this plan.
- **The deck's own "Quiz Time" slides (9 and 13) carry no extractable question text** — likely interactive or image-based elements the text extraction couldn't capture. Rather than invent quiz content for those slots, Activities 1 and 3 rebuild the same checkpoint *moment* using the deck's own already-taught worked examples (P1/P2 and P4/P5 respectively).
- **The "Weighted average" bridge is the deck's own idea, not an addition.** The Agenda slide's speaker notes name it explicitly as the link from Mixtures & Alligations into this session; it's surfaced deliberately in Slide Block B / P7 rather than left as a throwaway note.
- **Classroom Quiz time has been fully redistributed**, not dropped silently — see the placeholder block between Activity 1 and Slide Block B. The 60-minute timeline above has no gap: 7+3+14+6+12+7+8+3 = 60.
- **Closing note — this is the last session (23) of the current batch.** This lesson-plan set covers the first 23 decks in this Aptitude course exactly as they currently exist in the source folder. Any decks added to that folder later (Session 24 onward) will need this same text-extraction-and-plan treatment from scratch — they are not covered by anything produced so far, and no unit IDs or quiz pools should be assumed to exist for them either, absent evidence.
