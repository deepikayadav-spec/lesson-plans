# Session 8 — Company-Specific MCQs: Numbers

**Duration** 60 min · **Topic** Company-Specific MCQs — Numbers (solved-problem consolidation) · **Prerequisite** Sessions 2–7 (Number Systems through Remainder Cycles)
**Session type** Consolidation / review lecture. No new concept is introduced — this session applies divisibility, decimals-as-fractions, remainders, power cycles, and co-primes (Sessions 2, 6, 7) to ten real placement-test-style questions. No classroom quiz bank, MCQ pool, or coding-practice unit IDs exist yet for this topic.

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `1) NIAT_CSMCQ'S_Numbers.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Apply the digit-sum divisibility identity (a number minus its digit sum is always a multiple of 9, and therefore of 3) to justify an answer without testing a specific number. *(APPLYING)*
2. Convert decimals — both terminating products and a pure recurring decimal — into fractions to simplify a calculation or express an exact value. *(APPLYING)*
3. Apply power-cycle patterns to find units digits and remainders for large exponents (e.g. 3^65, 6^53, 9^5, 5^195) without direct computation. *(APPLYING)*
4. Analyze a small set of candidate numbers or options to identify which pair is co-prime, by testing common factors directly rather than deriving from scratch. *(ANALYZING)*
5. Evaluate which solving method — direct computation, option verification, or a general identity — is fastest for a given placement-style question, and justify the choice. *(EVALUATING)*
6. Distinguish questions that require substituting a specific value (e.g. the least valid `n`) from questions solvable by a general rule, and choose the faster strategy under time pressure. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 7 (0–7 min)

8 questions on **Session 7 (Remainder Cycles)**. Newly authored options around the deck's own real numbers; every number below is taken directly from that deck. ~45 s each, project the distribution, never name individuals.

<!-- placement: inferred — six exponents below were reconstructed from a pptx extraction artifact; see Instructor Notes -->

**Q1.** Find the remainder when 140 is divided by 12.
`A` 6 · `B` 8 · `C` 4 · `D` 10
→ **B.** *Targets:* plain remainder recall (140 = 11×12 + 8). Warm-up floor question — if this is missed by more than a couple of students, slow down for the rest of the poll.

**Q2.** Find the remainder when (13 × 15) is divided by 7?
`A` 6 · `B` 1 · `C` 5 · `D` 0
→ **A.** *Targets:* compute-then-reduce (13×15=195, 195÷7 remainder 6). *Misconception:* reducing 13 and 15 mod 7 first (to 6 and 1) and forgetting to multiply those reduced values together (6×1=6 — actually still correct here, but flag that skipping the multiplication step entirely is the real error some students make).

**Q3.** Find the remainder when 4^5 is divided by 15.
`A` 1 · `B` 4 · `C` 8 · `D` 11
→ **B.** *Targets:* small-exponent case where direct computation (4^5 = 1024, 1024÷15 remainder 4) is still faster than building a cycle — sets up the contrast with Q4–Q6 below.

**Q4.** Find the remainder when 2^356 is divided by 5?
`A` 1 · `B` 2 · `C` 4 · `D` 8
→ **A.** *Targets:* remainder-cycle of 2 mod 5 is {2,4,3,1}, length 4; 356÷4 leaves remainder 0, so it lands on the last term of the cycle, 1. *If wrong:* the off-by-one on "remainder 0 means last term of the cycle" is the exact mistake to re-teach here.

**Q5.** Find the remainder when 5^187 is divided by 7?
`A` 5 · `B` 4 · `C` 6 · `D` 2
→ **A.** *Targets:* longer cycle (5 mod 7 cycle is {5,4,6,2,3,1}, length 6); 187÷6 leaves remainder 1 → first term, 5.

**Q6.** Find the remainder when 13^856 is divided by 7?
`A` 6 · `B` 1 · `C` 5 · `D` None of these
→ **B.** *Targets:* reduce the base first (13 mod 7 = 6), then cycle on 6 (cycle {6,1}, length 2); 856÷2 leaves remainder 0 → last term, 1.

**Q7.** Find the remainder when 477^856 is divided by 4?
`A` 1 · `B` 0 · `C` 3 · `D` 2
→ **A.** *Targets:* the same "reduce the base first" shortcut, taken further — 477 mod 4 = 1, and 1 raised to anything is 1. *If wrong:* students who skip the base-reduction step and try to cycle on 477 directly will run out of time; this is the moment to name that shortcut explicitly.

**Q8 (MSQ — select all).** A prime number greater than 3 is divided by 6. Which remainders are possible?
`A` 1 · `B` 2 · `C` 4 · `D` 5
→ **A and D.** *Targets:* any prime greater than 3 is coprime to 6, so it must land on 1 or 5 mod 6 — never 0, 2, 3, or 4, since those share a factor with 6. *Misconception:* picking only one of the two, or picking an even/multiple-of-3 remainder because "primes are just odd numbers." This is the session's hardest poll item — deliberately last.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–10 min)

Put this on screen, nothing else, no context, no hint column:

> X is a 5-digit number. When we subtract the sum of the digits from X, it becomes divisible by?
> `A` 3 and 9 · `B` 4 · `C` 7 · `D` 6

Say: *"Sixty seconds. Silent. No talking, no notes. This is question one of a real company-specific placement set — solve it cold, the way you will on test day."*

Run a visible 60-second timer. At time, take a show of hands per option — do not reveal the answer yet.

> *"Hold that answer in your head. Here's the thing: that's not a made-up example. That is literally question one of a real company placement Numbers section. Today we are not learning anything new — Sessions 2 through 7 already gave you every tool you need. Today is ten of these, back to back, exactly the way they'll show up on test day, plus the fastest way to each answer."*

Move straight into Slide Block A, which opens by resolving this exact question.

---

## Slide Block A (10–22 min) — DELIVER AS-IS

Covers Company-Specific Questions 1–5 from the deck, each with its real worked solution. For each: state the question, reveal the real answer, then give the fastest method — don't re-derive from scratch on the board when the deck's own shortcut is faster.

**Q1 — X is a 5-digit number. When we subtract the sum of the digits from X, it becomes divisible by?**
Options: 3 and 9 · 4 · 7 · 6 → **Answer: 3 and 9**

- Fastest method: you never need a real number. Every digit's place value is a power of 10, and every power of 10 ≡ 1 (mod 9). So any number ≡ its own digit sum (mod 9) — meaning the *difference* between them is always a multiple of 9, and therefore of 3.
- The deck's own worked example (X = 43,269 → sum = 24 → 43,269 − 24 = 43,245, divisible by 9) is an illustration, not a required step. Show it once, then say explicitly: "you do not need to pick a number on the real test — this is always true."
- Deck's own Note: *"X − (sum of digits of X) is always divisible by 9 (so it will also be divisible by 3)."*

**Q2 — What number should be divided by (0.81)^1/2 to give the result as 81?**
**Answer: 72.9**

- Fastest method: recognise 0.81 = 0.9² immediately, so (0.81)^1/2 = 0.9 — don't reach for a calculator.
- Then it's one multiplication, not a division: the number = 81 × 0.9 = 72.9.
- Beat: "dividing by a square root" is really just "multiply by the square root" once you flip the question — say this out loud, it's the shortcut.

**Q3 — Which is the closest approximation to the product 0.3333 × 0.25 × 0.499 × 0.125 × 24?**
Options: 0.128 · 0.12 · 0.126 · 0.125 → **Answer: 0.125**
Deck's own Hint: *"Convert the decimals into fractions."*

- Fastest method: recognise each decimal as a familiar fraction before multiplying anything — 0.3333 ≈ 1/3, 0.25 = 1/4, 0.499 ≈ 1/2, 0.125 = 1/8.
- Multiply the fractions and cancel: (1/3)(1/4)(1/2)(1/8)(24) = 24/192 = 1/8 = 0.125.
- Beat: multiplying five decimals directly is slow and error-prone under time pressure — fractions cancel, decimals don't.

**Q4 — When an integer n is divided by 8, the remainder is 3. What is the remainder when 6n is divided by 8?**
Options: 2 · 3 · 4 · 6 → **Answer: 2**

- Fastest method: don't solve algebraically — plug in the *least* valid value of n. Here n = 3 (smallest number leaving remainder 3 on division by 8).
- 6n = 18; 18 ÷ 8 leaves remainder 2.
- Beat: the deck explicitly notes this holds for any valid n (n = 11, 19, …), not just 3 — the least-value substitution is a shortcut, not a special case.

**Q5 — What smallest number should be added to 1056 so that the number is completely divisible by 23?**
Options: 2 · 0 · 1 · 3 → **Answer: 2**

- Fastest method: find the remainder first (1056 ÷ 23 leaves remainder 21), then subtract that remainder from the divisor: 23 − 21 = 2.
- Verify: 1056 + 2 = 1058 = 23 × 46. Exact.
- Deck's own Note (edge case, worth stating out loud): *"If the remainder is 0, the smallest number to add would be 0"* — not the divisor itself.

**Checkpoint (at 22 min)** — cold-call two students:
> *"Why is X minus the sum of its digits always divisible by 9, for any 5-digit number at all — not just 43,269?"*
> **Answer:** Every digit's place value is a power of 10, and every power of 10 leaves remainder 1 when divided by 9. So the number itself always has the same remainder mod 9 as its digit sum — subtracting them cancels that remainder, leaving a clean multiple of 9 (and hence of 3).

---

## ⚡ Activity 1 — 60-Second Solve, Then I Reveal (22–29 min)

### What this activity is

Two more of the deck's own questions go up on screen, one at a time. Students get 60 seconds of silent, individual solving — no talking, no group work — then commit to an answer by a show of hands (or finger-count for the option letter) before you reveal the deck's real worked answer. Run it as a lightweight two-team tally, not a full competition — the point is the pressure of committing before the reveal, mirroring the Hook.

### Why it's here

After 12 minutes watching you solve, students need to solve cold themselves before you hand them the next block of solutions. Framing it as "beat the reveal" keeps it from feeling like a pause in the lecture.

### Before class

Nothing to build — both questions are Company-Specific Qs 6 and 8, straight from the deck. Draw two columns on the board (Team Left / Team Right, split the room down the middle) for a simple correct-and-fastest tally.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:15 | Setup line, reveal Q6 | Listen |
| 0:15–1:15 | Silent timer (60 s) | Solve alone, commit to an answer |
| 1:15–1:45 | Take the show of hands, reveal real answer + one-line reasoning | Check their own work |
| 1:45–2:00 | Reveal Q7 | Listen |
| 2:00–3:00 | Silent timer (60 s) | Solve alone, commit to an answer |
| 3:00–3:30 | Take the show of hands, reveal real answer + one-line reasoning | Check their own work |
| 3:30–7:00 | Debrief both, mark the tally | Listen |

### Say this

> *"Sixty seconds, silent, no talking. Commit to an answer before I say time — hands up for your letter the second I call it. I reveal right after. This is exactly the pressure of the real thing."*

### The questions

**Q6.** What is the remainder when (2p + 2)² is divided by 4, where p is any integer?
Options: 1 · 2 · 3 · None of the above
**Real answer: None of the above** — (2p + 2) is always even, and the square of an even number is always divisible by 4, so the remainder is 0 (not listed, hence "None of the above" is correct).

**Q8.** Find the remainder when 5^195 is divided by 3.
Options: 1 · 3 · 4 · 2
**Real answer: 2** — 5^n mod 3 cycles {2, 1}; 195 ÷ 2 leaves remainder 1, landing on the first term of the cycle, 2.

### When it goes wrong

| If… | Do this |
|---|---|
| Most of the room picks 1, 2, or 3 for Q6 | Expected — that's the trap. Reveal that "None of the above" is correct *because* the real remainder (0) was never printed as an option. Say this explicitly: real placement tests do this on purpose. |
| Nobody attempts a cycle for Q8 in 60 seconds | Fine — it's meant to feel tight. Ask "what would you have needed to know in advance?" and answer: the cycle {2,1}, memorised, not derived live. |
| One side of the room dominates the tally | Ignore the score, it's decoration. Redirect: "the score doesn't matter, the method does — who can say it back to me?" |
| Someone finishes Q6 instantly by computing an actual value of p | Ask them to prove it holds for a *second* value of p too — that's the general-identity habit Q1 already built. |

**Common instructor mistake:** revealing the answer without the one-line "why" immediately after. The reveal is only useful if it's paired with the reasoning in the same breath — otherwise this becomes a guessing game.

**Cut rule:** If running short, run Q8 only. Power-cycle remainders are the more test-relevant shortcut of the two and recur in Slide Block B and Activity 3.

---

## Classroom Quiz

> Classroom Quiz: not yet available — add once question bank exists for this topic.

Time reallocated: the 27–34 min slot a concept session would spend on the platform quiz is folded into an extended **Slide Block B** (29–39 min, 10 min instead of the usual ~7) below. The full 60 minutes is re-timed with no gaps — see the block-by-block times used throughout this plan (0–7, 7–10, 10–22, 22–29, 29–39, 39–47, 47–54, 54–60).

---

## Slide Block B (29–39 min) — DELIVER AS-IS

Covers Company-Specific Questions 7, 9, and 10 from the deck, with their real worked solutions.

**Q7 — What will be the units digit in the result of the expression (3^65) x (6^53) x (9^5)?**
Options: 6 · 2 · 3 · 7 → **Answer: 2**
Deck's own Hint: *"Recall the power cycle concept."*

- Fastest method: never compute the actual powers — track each base's units-digit cycle and reduce the exponent by the cycle length.
  - 3's units-digit cycle: {3, 9, 7, 1}, length 4. 65 ÷ 4 leaves remainder 1 → units digit of 3^65 is 3.
  - 6's units digit is 6 at every power, no cycle needed.
  - 9's units-digit cycle: {9, 1}, length 2. 5 ÷ 2 leaves remainder 1 → units digit of 9^5 is 9.
- Multiply the three units digits: 3 × 6 × 9 = 162 → units digit **2**.

**Q9 — Out of the three numbers 26, 13, and 34, which two are the co-prime numbers?**
Options: 26 and 13 · 26 and 34 · 13 and 34 · None of these → **Answer: 13 and 34**
Deck's own Hint: *"Go for option verification."*

- Fastest method: don't factorise all three numbers from first principles — test the three *given* pairs directly for a shared factor.
  - (26, 13): 13 divides 26 → common factor 13 → not co-prime.
  - (26, 34): both even → common factor 2 → not co-prime.
  - (13, 34): only common factor is 1 → co-prime.
- Deck's own Note: *"If one number is a factor of the other (like 13 divides 26), that pair cannot be co-prime."*

**Q10 — Express 1.0232323….. as a fraction?**
Options: 1023/1000 · 1013/990 · 1023/99 · 1013/99 → **Answer: 1013/990**

- Fastest method: identify the repeating block first — here it's "23", and there's one non-repeating digit ("0") right after the decimal point.
- Let x = 1.0232323…. Multiply to align the repeat: 10x = 10.2323…, and 1000x = 1023.2323… (shift by one more full repeat block).
- Subtract: 1000x − 10x = 1013 → 990x = 1013 → x = 1013/990.

**Checkpoint (at 39 min)** — show hands:
> *"6 raised to any positive power — what's the units digit, always?"*
> **Answer:** 6. Every power of 6 ends in 6 — no cycle to track, unlike 3 or 9.

---

## ⚡ Activity 2 — Fastest Method Board Race: Option Verification vs Direct Calculation (39–47 min)

### What this activity is

Two teams race on the whiteboard to answer the *same* question — Company-Specific Q9 (the co-prime pick) — using two different assigned methods. Team A must use **option verification** (test only the three given pairs for a common factor). Team B must use **full factorization first** (factorise 26, 13, and 34 completely, then reason about which pairs are co-prime from the factorizations). Both should land on the correct answer; the race exposes which method gets there faster.

### Why it's here

The deck flags this exact shortcut with its own Hint — "Go for option verification" — but telling students a method is faster doesn't land the way *watching* it win a race does.

### Before class

Split the room into two halves. Each half nominates one board-writer; the rest of that half can shout instructions to their writer but may not touch the board themselves.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, assign methods, reveal question | Listen |
| 0:30–3:30 | Start the clock, stay silent | Team A verifies pairs; Team B factorises then reasons |
| 3:30–5:00 | Call time on whichever team finishes first, check their board | Watch |
| 5:00–6:30 | Let the second team finish regardless, check their board | Watch |
| 6:30–8:00 | Debrief the time gap | Listen |

### Say this

> *"Same question, same answer, two different roads. Team A — you're only allowed to test the three pairs I give you for a common factor, nothing else. Team B — you have to fully factorise all three numbers first, then decide. Board writers only touch the marker. Go."*

### The question and real answer

**Q9.** Out of the three numbers 26, 13, and 34, which two are the co-prime numbers?
**Answer: 13 and 34** — only shared factor is 1. (26,13) share 13; (26,34) share 2.

### When it goes wrong

| If… | Do this |
|---|---|
| Team B finishes just as fast | Ask them to defend it: "would that still be true if I gave you five numbers instead of three?" Verification degrades much faster than factorization as the option count grows — say this. |
| Team A gets the right answer but can't explain *why* 13 and 34 have no shared factor | Push once: "13 is prime — what does that mean for anything that isn't a multiple of 13?" |
| One team writes the wrong pair | Don't correct silently — have the class check it live against the deck's Note (13 divides 26 → automatically disqualified). |
| Neither team is actually racing, both just calculating quietly | Restart with a louder countdown. The race framing is what makes the time difference land — without urgency this is just two students doing homework at the board. |

**Common instructor mistake:** declaring a "winner" and moving on before debriefing *why* Team A almost always wins. The race is a setup for the debrief, not the point itself.

**Cut rule:** If short on time, run only Team A's method live and simply state the factorization-first time cost verbally instead of having Team B race it out.

---

## ⚡ Activity 3 — Fill the Blank Live: Power Cycle Shortcut (47–54 min)

### What this activity is

Put the real worked solution to Company-Specific Q7 (units digit of (3^65)(6^53)(9^5)) on screen with the key numbers blanked out. Students call out the missing values live, one at a time, rebuilding the shortcut method as a class instead of watching you write it.

### Why it's here

Q7 already appeared once in Slide Block A's family of questions conceptually (power cycles were introduced in Session 7) and is delivered formally in Slide Block B — this activity is the students' turn to reproduce the method themselves, which is the real test of whether the shortcut landed.

### Before class

Write or project the solution skeleton with blanks (shown below). Cover the blanked numbers with a sticky note, a text box, or simply don't reveal that row of the slide yet.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, reveal skeleton | Listen |
| 0:30–1:00 | Reveal blank 1 (cycle for 3) | Call out the answer |
| 1:00–3:00 | Reveal blanks 2–6 one at a time, taking a different student each time | Call out each answer |
| 3:00–5:00 | Reveal blank 7 (final units digit), confirm against the real deck answer | Check their own work |
| 5:00–7:00 | Debrief: contrast with "what if you tried to actually compute 3^65?" | Listen |

### Say this

> *"I'm not writing this one — you are, out loud. I'll point, you fill the blank. One number at a time, and I want the reasoning, not just the digit."*

### The skeleton (blanks in bold, real answers given here for you)

> 3's units-digit cycle: {3, 9, 7, 1}, length **4**.
> 65 ÷ 4 leaves remainder **1** → units digit of 3^65 is **3**.
> 6 to any power always ends in **6**.
> 9's units-digit cycle: {9, 1}, length **2**.
> 5 ÷ 2 leaves remainder **1** → units digit of 9^5 is **9**.
> Multiply the units digits: 3 × 6 × 9 = **162** → final units digit is **2**.

### When it goes wrong

| If… | Do this |
|---|---|
| Class stalls on "why does the cycle length matter" | Ask: "if I told you the exponent was exactly the cycle length, what would the units digit be?" — it's always the *last* term of the cycle. Rebuild from there. |
| Someone tries to actually multiply out 3^65 | Let them start, then stop after ten seconds: "that's the point — this is why the cycle exists." |
| The room fills blanks correctly but mechanically, no one can explain "remainder 1 → first term" | Ask explicitly: "if the remainder were 0 instead of 1, which term would we use?" (Answer: the last term of the cycle, not a zeroth term — this is the same off-by-one flagged in warm-up Q4.) |
| Running long | Skip the 9^5 sub-cycle and only fill blanks for the 3^65 portion plus the final multiplication — the method is fully demonstrated either way. |

**Common instructor mistake:** filling in a blank yourself when the class is slow to answer. Wait the full silence out — the value of this activity is entirely in students producing the number, not hearing it from you a second time.

**Cut rule:** Run only the 3^65 portion (skip 6^53 and 9^5 detail) and jump straight to "multiply the three units digits" using 3, 6, and 9 as givens.

---

## Exit Ticket + Homework (54–60 min)

**Exit ticket** — on paper or in chat before anyone leaves:

> Out of the three numbers 26, 13, and 34, which two are co-prime, and why in one sentence?
> **Answer:** 13 and 34 — their only common factor is 1 (26 shares 13 with 13, and shares 2 with 34).

Scan responses on the way out. If most students still reach for full factorization instead of testing the given pairs, that's the signal to reopen Activity 2's method for 90 seconds at the start of Session 9.

**Homework**

| Task | Detail |
|---|---|
| Redo Company-Specific Q3, Q7, and Q10 cold, no notes | The decimal-product conversion, the three-base units-digit cycle, and the recurring-decimal-to-fraction — the three questions with the most steps in today's deck |
| Revisit Session 2 (Number Systems), Session 6, and Session 7 (Remainder Cycles) material for any rule used today that felt shaky | No dedicated practice unit exists yet for this topic — homework is the same 10 real questions, attempted a second time unaided |

Tell them: *"Nothing on the actual test will look exactly like today's ten questions — but the four moves you used today (digit-sum identity, decimals-to-fractions, power cycles, option verification) will cover almost everything you see. Redo the hard three before next session."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Multiply the decimals directly (0.3333 × 0.25 × 0.499 × 0.125 × 24) instead of converting to fractions first | Decimals feel more "exact" and immediate than fractions | The deck's own Hint on Q3 — "Convert the decimals into fractions" — Slide Block A runs the fraction cancellation live |
| Try to compute 3^65 or 6^53 as an actual number | No instinct yet that huge exponents are a signal to shortcut, not calculate | The deck's own Hint on Q7 — "Recall the power cycle concept" — reinforced by Activity 3's fill-the-blank |
| Fully factorise all candidate numbers before comparing, instead of testing the given pairs | Feels more rigorous than "just checking" the options in front of you | The deck's own Hint on Q9 — "Go for option verification" — proven live by Activity 2's timed board race |
| Assume the correct answer to "(2p+2)² mod 4" must be one of the printed numeric options | Trusting that the right answer is always literally on the list | Activity 1's reveal on Q6 — "None of the above" is correct because the true remainder (0) was deliberately not printed |
| Always add (divisor − remainder) to reach the next multiple, even when the remainder is already 0 | Pattern-matching Q5's rule without checking the edge case | The deck's own Note under Q5 — "If the remainder is 0, the smallest number to add would be 0" — state this explicitly in Slide Block A |
| Treat "X − sum of digits is divisible by 9" as something that needs a real number to check each time | The deck's worked example uses one specific X (43,269), which reads like "the" method rather than an illustration | The 22-minute checkpoint — force the general mod-9 identity into words, not just the one worked case |

---

## Instructor Notes

- **Grounding.** This plan is built entirely from local pptx text-extraction of two decks — `1) NIAT_CSMCQ'S_Numbers.pptx` (this session) and the Session 7 deck (`NIAT Remainder Cycles.pptx`, used only for the warm-up poll). No platform unit IDs, classroom quiz bank, or MCQ/coding-practice pool exist yet for either topic — both gaps are flagged in the header table and the Classroom Quiz block above.
- **Consolidation, not new content.** Session 8 of 23. Nothing here is a new concept — it is Sessions 2, 6, and 7's tools (divisibility, decimals-as-fractions, remainders, power cycles, co-primes) applied to ten real solved placement-style questions. Judge this session by whether students get *faster* at methods they already have, not by new recall.
- <!-- placement: inferred --> **Warm-up poll exponents were reconstructed.** The Session 7 deck's raw text-extraction split superscript exponents into separate text runs joined by `" | "` instead of a caret — e.g. the raw extracted line `"Find the remainder when 4 | 5 | is divided by 15"` was reconstructed as **4^5 ÷ 15**; similarly `"2 | 356 |"` → 2^356, `"5 | 187 |"` → 5^187, `"13 | 856 |"` → 13^856, `"477 | 856 |"` → 477^856, and `"123456789 | 123456789 |"` → 123456789^123456789 (not used in the final poll, kept in the source deck only). Each reconstruction was verified by recomputing the stated remainder and confirming it matches the deck's own listed answer before it went into this plan — treat the numbers as confirmed, but the tag is kept because the exponent itself had to be inferred from formatting, not read directly.
- **This session's own deck did not show that artifact.** All exponents in the CSMCQ Numbers deck itself — 3^65, 6^53, 9^5 (Q7), 5^195 (Q8), (0.81)^1/2 (Q2) — extracted intact with carets and were cross-checked against the deck's own "Solution:" prose, which independently confirms each expression. No inference was needed for any of the ten main questions in Slide Blocks A/B or the activities.
- **Pacing risk:** Slide Block A covers 5 full questions in 12 minutes (~2.4 min each). If running long, compress Q2 and Q4 to a single stated line each ("0.81's square root is 0.9, multiply" / "plug in n=3, get remainder 2") rather than full board derivations — Q1, Q3, and Q5 carry the session's real teaching weight (the mod-9 identity, the fractions shortcut, and the edge-case Note).
- **Classroom Quiz gap:** absorbed into an extended Slide Block B (29–39 min, 10 min instead of a typical ~7) rather than left as dead time. The full 60 minutes has no gaps: 0–7, 7–10, 10–22, 22–29, 29–39, 39–47, 47–54, 54–60.
- **No separate practice pool:** homework deliberately reuses the same 10 deck questions rather than pointing to a coding/MCQ practice unit, since none exists yet for this topic — consistent with how support sessions without a pool are handled elsewhere in this course.
