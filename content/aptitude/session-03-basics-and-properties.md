# Session 3 — Basics and Properties (Multiples, Factors & LCM/HCF)

**Duration** 60 min · **Topic** Multiples, Factors & LCM/HCF — Basics and Properties · **Prerequisite** Session 2 (Number Systems 1)
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet.

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT Basics and Properties.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define *multiple* and *factor*, and decide from a division/multiplication fact which number is which. *(REMEMBERING)*
2. Explain the prime-factorisation method for finding the LCM and HCF of two or more numbers. *(UNDERSTANDING)*
3. Apply prime factorisation to compute the LCM and HCF of a given set of numbers (e.g. 18 & 30; 24, 36 & 48). *(APPLYING)*
4. Apply the ratio-based shortcut — ratio `a:b`, HCF `H` → LCM `= H × a × b` — to find an unknown number or the LCM of two numbers in a stated ratio, simplifying the ratio first where needed. *(APPLYING)*
5. Verify the relationship **Product of two numbers = LCM × HCF** for a given pair. *(ANALYZING)*
6. Compute the LCM and HCF of a set of fractions, including a case with no directly visible common factor. *(APPLYING)*

---

## Warm-Up Poll — Retrieval Practice on Session 2 (0–7 min)

7 questions on **Session 2 (Number Systems 1)**. Newly authored from that deck's own content. ~45 s each, project the distribution, never name individuals. Ramp: recall → application → analysis.

**Q1.** In last session's number-classification diagram, which statement about `0` is correct?
`A` `0` is a Natural number · `B` `0` is a Whole number but not a Natural number · `C` `0` is neither Whole nor Natural · `D` `0` is irrational
→ **B.** *Targets:* the `I ⊃ W ⊃ N` nesting shown on the number line (Whole numbers start at 0, Natural numbers start at 1). *If <60% correct:* redraw the nested-set diagram before moving on — don't just restate the answer.

**Q2.** Which is the correct divisibility test for **4**?
`A` Last digit divisible by 4 · `B` Last two digits divisible by 4 · `C` Sum of digits divisible by 4 · `D` Last three digits divisible by 4
→ **B.**

**Q3.** Apply the rule of 7: is **343** divisible by 7?
`A` Yes · `B` No
→ **A (Yes).** *Method:* unit digit `3 × 2 = 6`; remaining digits `34`; `34 − 6 = 28`; 28 is divisible by 7. *Targets:* the multi-step rule of 7 — this is the exact worked example from Session 2.

**Q4.** Apply the rule of 11: is **3546** divisible by 11?
`A` Yes · `B` No
→ **B (No).** *Method:* odd-place sum `3+4=7`; even-place sum `5+6=11`; difference `= 4`, not 0 or a multiple of 11.

**Q5.** Is **2122356512** divisible by 11?
`A` Yes · `B` No
→ **B (No).** *Targets:* applying the rule of 11 to a long number, not just a 4-digit toy example.

**Q6.** 2 and 3 are co-primes. What are their HCF and LCM?
`A` HCF = 1, LCM = 5 · `B` HCF = 1, LCM = 6 · `C` HCF = 2, LCM = 6 · `D` HCF = 1, LCM = 3
→ **B** (HCF = 1; LCM = product = 6). *Read:* note this score — today's session opens the door to LCM/HCF properties, and co-primes (HCF = 1) is the exact edge case that makes the ratio shortcut click.

**Q7.** *(MSQ — select all that apply)* Which of these divisibility rules were taught as a **combination** of two smaller rules?
`A` Divisible by 6 (needs 2 and 3) · `B` Divisible by 12 (needs 3 and 4) · `C` Divisible by 8 (its own 3-digit rule) · `D` Divisible by 10 (its own last-digit rule)
→ **A and B.** *If someone picks C or D:* they're right that 8 and 10 have rules, but those rules stand alone in the deck — only 6 and 12 were explicitly taught as "divisible by X **and** Y."

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including reads.

---

## Hook (7–10 min)

Write these three lines on the board, nothing else:

```
10 × 2 = 20
10 × 3 = 30
10 × 4 = 40
```

Ask: *"What do 20, 30 and 40 all have in common with 10?"* Let the answer land: they're all **multiples of 10**.

Now flip the operation. Write:

```
10 ÷ 2 = 5     (an integer  →  2 is a factor of 10)
7 ÷ 2 = 3.5    (not an integer  →  2 is NOT a factor of 7)
```

Ask: *"So if 2 is a factor of 10, is 10 a multiple of 2?"* — Yes. *"A multiple and a factor are the same division fact, looked at from two directions."*

> *"Every single thing we do for the next fifty minutes — LCM, HCF, ratios, fractions — is just multiples and factors, organised. That's the whole session in one board."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

Covers: Multiples → Factors → Methods of finding LCM & HCF (prime factorisation) → the Properties slide (previewed here because Activity 1 needs it immediately).

**Beats to emphasise**

- **Beat 1 — Multiples & Factors.** Use the deck's own examples: `10×2=20`, `10×3=30`, `10×4=40` are multiples of 10; `10/2=5` (2 is a factor of 10), `12/4=3` (4 is a factor of 12), `7/2=3.5` (2 is **not** a factor of 7 — the non-integer result is the tell).
- **Beat 2 — Prime factorisation method for LCM & HCF.** Work both worked examples from the deck, on the board, step by step:
  - LCM & HCF of **18 and 30** → 18 = 2×3², 30 = 2×3×5 → **HCF = 2×3 = 6**, **LCM = 2×3²×5 = 90**.
  - LCM & HCF of **24, 36 & 48** → **HCF = 12**, **LCM = 144**. <!-- placement: inferred — the text extraction split "144" across two runs ("14" / "4,"); reconstructed from the deck's own prime-factorisation method and cross-checked (24=2³×3, 36=2²×3², 48=2⁴×3 → HCF=2²×3=12, LCM=2⁴×3²=144). Confirm against the live slide before teaching. -->
- **Beat 3 — Properties preview.** <!-- placement: inferred — the deck's Properties slide (Product = LCM×HCF; the ratio shortcut; the fraction formulas) sits between the worked-example slides and the practice-problem slides. Activity 1's problems need the ratio shortcut immediately, so it is introduced here rather than held for Slide Block B, which instead deepens/applies it. --> State, without yet drilling: *"If the ratio of two numbers is `a:b`, and their HCF is `H`, then LCM `= H × a × b`."* Also flag that **Product of two numbers = LCM × HCF** — you'll verify this properly in Slide Block B.

**Checkpoint (at 22 min)** — cold-call two students:
> *"Using prime factorisation, what's the HCF of 18 and 30?"*
> **Answer:** 6 (common prime factors 2 and 3).

---

## ⚡ Activity 1 — Rapid Fire Board Race (22–34 min)

### What this activity is

Four real problems from the deck, run back-to-back as a board race, increasing in difficulty. Students solve individually or in pairs and race to the board; you take the first correct method, not the first shout.

### Why it's here

This slot absorbs the time that would otherwise sit idle waiting on a classroom-quiz pool that doesn't exist yet for this topic (see Resources table). Four genuine worked-problem patterns from the deck are enough to fill it properly, and racing them keeps the energy up right after a dense slide block.

### Before class

Have all four problems ready to reveal one at a time. Nothing to set up beyond a clear board.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–1:00 | Setup line, reveal Problem 1 | Listen, then start |
| 1:00–3:00 | Wait | Solve, race to board |
| 3:00–4:00 | Reveal answer + method | Check own work |
| 4:00–5:00 | Reveal Problem 2 | Solve, race to board |
| 5:00–6:00 | Reveal answer + method | Check own work |
| 6:00–7:30 | Reveal Problem 3 | Solve, race to board |
| 7:30–8:30 | Reveal answer + method | Check own work |
| 8:30–10:30 | Reveal Problem 4 (has a trap) | Solve, race to board |
| 10:30–12:00 | Reveal answer, debrief the trap | Listen |

### Say this

> *"Four problems, one at a time. First person to the board with the **right method**, not just a number, wins the round. Method beats speed."*

### The problems

| # | Problem | Property used | Answer |
|---|---|---|---|
| 1 | Find `a`, if the LCM & HCF of `(10, a)` is 30 & 5. | Product = LCM × HCF → `a = (30×5)/10` | **15** |
| 2 | Find `a`, if the LCM & HCF of `(48, a)` is 336 & 16. | Product = LCM × HCF → `a = (336×16)/48` | **112** |
| 3 | The ratio of two numbers is 3:4. Their HCF is 6. Find the LCM. | Ratio shortcut → `LCM = H×a×b = 6×3×4` | **72** |
| 4 | The ratio of two numbers is 4:14. Their HCF is 6. Find the LCM. | **Simplify the ratio first** (4:14 → 2:7), then `LCM = 6×2×7` | **84** |

### The trap in Problem 4

The deck flags this explicitly: *"What is Simplest form of ratios?"* If a student plugs in 4 and 14 directly (`6×4×14 = 336`), that's the exact wrong answer this problem is designed to catch. Ratios must be in simplest form before applying the shortcut.

### When it goes wrong

| If… | Do this |
|---|---|
| Everyone uses Product=LCM×HCF for Problems 3–4 too | That's fine as a cross-check, but push them to also state the ratio shortcut — it's the faster tool and the one being taught. |
| Room gets stuck on Problem 4's `336` | Ask: *"Is 4:14 in its simplest form?"* Let them spot the common factor of 2 themselves. |
| Running long | Cut to Problems 1 and 4 only — one Product-property problem, one ratio-shortcut-with-a-trap problem. Do not cut Problem 4; the simplification trap is the point of the activity. |

**Common instructor mistake:** revealing the "simplify the ratio" hint before students attempt Problem 4. Let them fall into it — the correction lands harder than the warning.

**Cut rule:** Problems 1 and 4 only, ~6 minutes, if the warm-up poll or Slide Block A overran.

---

## Classroom Quiz (would-be 27–34 min slot)

> Classroom Quiz: not yet available — add once question bank exists for this topic.

This slot's time has already been folded into Activity 1 above (22–34 min) rather than left as a gap — there is no question bank for this topic yet, so a genuine practice activity replaces it, per the same pattern used for support sessions elsewhere in this course.

---

## Slide Block B (34–44 min) — DELIVER SLIDES AS-IS

Covers: Product of two numbers = LCM × HCF (verified) → LCM/HCF of fractions → the harder worked fraction example.

**Beats to emphasise**

- **Beat 1 — Verify Product = LCM × HCF.** Don't just state it — check it against a number the class already trusts: 18 and 30, from Slide Block A. `18 × 30 = 540`. `LCM × HCF = 90 × 6 = 540`. ✅ Matches.
- **Beat 2 — LCM/HCF of fractions.** State the formulas: **LCM of fractions = LCM(numerators) / HCF(denominators)**; **HCF of fractions = HCF(numerators) / LCM(denominators)**. <!-- placement: inferred — the deck's Properties slide shows only the blank labels "LCM of fractions =" / "HCF of fractions =" with no formula text captured in extraction (likely filled live or built in on the original slide). Reconstructed here and verified against the deck's own worked answer below, which it reproduces exactly — confirm against the live slide before teaching. -->
- **Beat 3 — Harder worked example.** Find LCM & HCF of `20/16`, `16/15`, `20/21`. The deck flags this exact sticking point: *"What is the HCF when there is no direct common factor in the given numbers?"* Work it on the board:
  - Numerators 20, 16, 20 → LCM = 80. Denominators 16, 15, 21 → HCF = 1. → **LCM of fractions = 80/1 = 80.** <!-- placement: inferred — extraction split "80" across two runs ("8" / "0,"); reconstructed and confirmed by recomputing LCM(20,16,20)=80, consistent with the deck's stated answer. -->
  - Numerators 20, 16, 20 → HCF = 4. Denominators 16, 15, 21 → LCM = 1680. → **HCF of fractions = 4/1680 = 1/420.**

**Checkpoint (at 44 min)** — show hands:
> *"Why is the HCF of those three fractions `1/420` and not a whole number, when none of them looks like it shares an obvious common factor?"*
> **Answer:** Because HCF of fractions isn't found by inspection — it's `HCF(numerators) ÷ LCM(denominators)`. The formula still gives a clean answer even when nothing is "directly" common.

---

## ⚡ Activity 2 — Predict the Output (44–50 min)

### What this activity is

Three number pairs the class has already solved today, each shown again as a bare pair. Before you reveal anything, students predict the product, then check it against `LCM × HCF`.

### Why it's here

Product = LCM × HCF was just stated and verified once (18, 30). One example is not enough to trust a property — this activity re-tests it on pairs the class derived themselves earlier in the session, which is a stronger form of proof to a room of skeptics than a fresh example would be.

### Before class

Have the three pairs and their already-known LCM/HCF ready to reveal.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line | Listen |
| 0:30–1:30 | Reveal Pair 1, ask for product prediction | Predict, commit out loud |
| 1:30–2:30 | Reveal LCM×HCF, compare | Check |
| 2:30–3:30 | Pair 2: predict, then reveal | Predict, check |
| 3:30–4:30 | Pair 3: predict, then reveal | Predict, check |
| 4:30–6:00 | Debrief | Listen |

### Say this

> *"Three pairs of numbers you already worked out today. I'm not giving you the product — you predict it first, out loud. Then we check it against LCM times HCF."*

### The pairs

| Pair | Source | LCM × HCF | Actual product | Match? |
|---|---|---|---|---|
| 18, 30 | Slide Block A | 90 × 6 = 540 | 18 × 30 = 540 | ✅ |
| 10, 15 | Activity 1, Problem 1 (`a = 15`) | 30 × 5 = 150 | 10 × 15 = 150 | ✅ |
| 18, 24 | Activity 1, Problem 3 (ratio 3:4, HCF 6 → 3×6=18, 4×6=24) | 72 × 6 = 432 | 18 × 24 = 432 | ✅ |

### Debrief line

> *"Three for three. This isn't a coincidence — for **any** two numbers, their product always equals their LCM times their HCF. That's why Problems 1 and 2 in the board race worked: you were solving for the missing number using exactly this rule."*

### When it goes wrong

| If… | Do this |
|---|---|
| Predictions are wildly off | Fine — that's the point of predicting before checking. Don't correct mid-prediction. |
| Someone asks if it works for 3+ numbers | Say clearly: no — this property is defined for **two** numbers only. That's why 24/36/48 was solved by prime factorisation, not this shortcut. |
| Running long | Do Pairs 1 and 3 only — one from the slide block, one from the ratio shortcut. |

**Common instructor mistake:** presenting this as a brand-new fact instead of a re-confirmation of something already stated in Slide Block B. The value here is the repetition landing as proof, not new information.

**Cut rule:** Two pairs (18,30 and 18,24), ~4 minutes.

---

## ⚡ Activity 3 — Write the Question (50–57 min)

### What this activity is

Students write their **own** ratio-based LCM/HCF question using today's exact template — pick a ratio `a:b`, pick an HCF `H`, then either ask for the LCM or ask for the two actual numbers — swap with a partner, solve each other's question, and check.

### Why it's here

Activity 1 tested whether students can apply the ratio shortcut to a given problem. This tests whether they understand it well enough to **construct** a valid one — a harder, generative check, and a different task shape from the board race so nothing repeats.

### Before class

Write the template on the board:
```
Ratio of two numbers = a : b
HCF of the two numbers = H
→ LCM = H × a × b
→ the two numbers themselves = H×a and H×b
```

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, show template | Listen |
| 0:30–2:30 | Wait | Each student picks `a:b` and `H`, writes one question |
| 2:30–4:00 | Signal swap | Swap with a partner |
| 4:00–6:00 | Circulate | Solve partner's question |
| 6:00–7:00 | Debrief, cold-call 2 pairs | Share question + answer |

### Say this

> *"You've solved four of these today. Now you write one. Pick a ratio, pick an HCF, decide what you're asking for — the LCM, or the two actual numbers. Give it to your partner. If their question doesn't have a clean answer, that's useful information too."*

### Answers

There is no single answer key — correctness is checked by re-deriving from the template: any `a:b` (in simplest form) and any `H` produces a valid `LCM = H×a×b` and numbers `H×a`, `H×b`. Model one on the board first if the room hesitates, e.g. ratio `2:5`, `H=4` → numbers `8, 20`, LCM `= 4×2×5 = 40`.

### When it goes wrong

| If… | Do this |
|---|---|
| A student picks a ratio not in simplest form (e.g. `4:14`) | Don't correct it — let their partner hit the exact trap from Activity 1 and self-correct. |
| Pairs finish early | Ask them to write a second question starting from the *numbers* instead of the ratio (i.e., reverse-engineer `a:b` and `H` from two chosen numbers). |
| Nobody knows where to start | Model the `2:5, H=4` example above, live, before releasing them again. |

**Common instructor mistake:** treating this as free time instead of circulating. The value is in catching a wrong ratio or a miscomputed HCF while a partner is still working, not after.

**Cut rule:** Skip the swap-and-solve step; have 3 students share their question and solve it as a class instead. ~3 minutes.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — on paper before anyone leaves:

> 1. In one line, what is a factor?
> 2. Find `a`, if the LCM & HCF of `(10, a)` is 30 & 5.

**Answers:** 1. A factor is a number that divides another exactly, leaving no remainder (e.g. `10 ÷ 2 = 5`, an integer, so 2 is a factor of 10). 2. `a = 15`.

Scan responses on the way out. A wrong answer on Q2 is the signal to reopen the Product=LCM×HCF property at the start of Session 4.

**Homework**

| Task |
|---|
| Redo, cold, with no notes: Find LCM & HCF of `20/16`, `16/15`, `20/21`. Check against today's answer — LCM = 80, HCF = 1/420. |
| Redo, cold: the ratio 4:14, HCF 6 problem. Check that you simplified the ratio to 2:7 *before* multiplying — the answer is LCM = 84. |

> *"Both of these have already been solved on the board today. If you get a different answer at home, that's not bad luck — it means you skipped a step. Find which one."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Not sure what "prime factorisation" actually means as a method (rather than just a term) | The deck itself flags this directly — *"What is Prime Factorisation?"* is posed as a sticking point right where the method is first used | Working the 18 & 30 example fully on the board in Slide Block A, showing the factor tree, not just the final answer |
| Using a ratio directly in the LCM shortcut without simplifying it (e.g. `6×4×14` instead of `6×2×7`) | The shortcut looks like a formula to plug numbers into, and 4:14 doesn't obviously look "unsimplified" | Activity 1, Problem 4 — deliberately using an unsimplified ratio so the wrong answer surfaces, then asking *"is 4:14 in its simplest form?"* |
| Assuming HCF of a set of fractions must be found by inspecting the fractions for an obvious shared factor, and concluding "there isn't one" | The deck flags this directly — *"What is the HCF when there is no direct common factor in the given numbers?"* — right at the hardest worked example | Slide Block B, Beat 3 — showing the HCF-of-fractions formula (`HCF(numerators)/LCM(denominators)`) produces a clean `1/420` even though nothing looks "directly" common |
| Treating *multiple* and *factor* as unrelated ideas rather than the same division fact read in two directions | <!-- placement: inferred — not a hint literally flagged in the deck, but a standard early confusion given the deck defines the two on back-to-back slides with no explicit link between them --> Definitions are taught on separate slides with separate examples | The Hook — flipping `10÷2=5` (factor) against `10×2=20` (multiple) on the same board, side by side |

---

## Instructor Notes

- **This plan is grounded entirely in a local pptx text-extraction** (`NIAT Basics and Properties.pptx`), not a platform export. No platform unit IDs, question IDs, or quiz/MCQ/coding pools exist yet for this topic — the Resources table reflects that honestly rather than inventing any.
- **Two numeric reconstructions were needed** because the text extraction split multi-digit numbers across separate text runs: `144` (LCM of 24, 36, 48) and `80` (LCM of the fraction set). Both are flagged inline with `<!-- placement: inferred -->` and were independently re-derived by hand from the deck's own prime-factorisation method — both check out — but confirm against the live slide before teaching.
- **The fraction LCM/HCF formulas are reconstructed**, not read directly off the slide — the deck's Properties slide shows the labels "LCM of fractions =" / "HCF of fractions =" with the formula itself apparently blank or built-in live and not captured by extraction. The reconstructed formulas were verified by recomputing the deck's own stated answer (LCM=80, HCF=1/420) for the (20/16, 16/15, 20/21) example, and they reproduce it exactly.
- **The Properties slide (Product=LCM×HCF, the ratio shortcut, the fraction formulas) is split across both slide blocks** rather than delivered once: the ratio shortcut is previewed at the end of Slide Block A because Activity 1's problems need it immediately, and Product=LCM×HCF is verified there too, in brief. Slide Block B then re-verifies Product=LCM×HCF properly and focuses fully on the fraction formulas. This is a judgment call about pacing, not a change to slide content — flag it if the live deck's actual slide order differs from what this plan assumes.
- **Activity 1 absorbs the would-be Classroom Quiz slot (27–34 min).** There is no question bank for this topic, so rather than leaving a gap or a thin placeholder, the four ratio/product problems the deck already provides were extended into a full 12-minute board race. This mirrors how other quiz-less sessions in this course's companion set handle the same gap.
- **Activity 3 ("Write the Question") is the one activity not pulled from a specific numbered deck problem** — it's built from the deck's own stated *template* (ratio `a:b`, HCF `H` → LCM `= H×a×b`), which is real content, but the specific numbers students generate are theirs, not the deck's. This is flagged as a deliberate design choice to fill the second "Quiz Time" slot the deck itself marks (slide 15) without inventing a fixed problem/answer that isn't in the source.
- **Pacing risk:** the fraction example in Slide Block B (Beat 3) has two separate LCM and HCF computations, each with its own numerator/denominator step. Don't rush it — if the class doesn't cleanly get the 90/30/6 style examples in Block A, this one will lose them. Consider trimming Activity 3 rather than this beat.
- **Warm-up Q7 (MSQ)** deliberately excludes 8 and 10 as "combination rules" even though a mathematically inclined student might argue 10 = 2×5. The deck only ever states 6 and 12 as explicit combinations ("divisible by 2 & 3" / "divisible by 3 & 4"); 8 and 10 are taught with their own independent rules. If a sharp student pushes back, acknowledge the math is technically fine but the deck's own framing is what's being tested.
