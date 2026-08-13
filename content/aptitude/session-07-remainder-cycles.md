# Session 7 — Remainder Cycles

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Remainder Cycles · **Prerequisite** Session 6 (Power Cycles)
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet — no quiz block for that reason. · **Format** 50-min recalibrated, 2 ALS activities (this session already had exactly 2 — see Instructor Notes)

**Resources**

| Resource | Status |
|---|---|
| Source deck (local file) | `NIAT Remainder Cycles.pptx` |
| Classroom Quiz | not yet available — add once question bank exists for this topic |
| MCQ / Coding Practice | not yet available — add once problem bank exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Recall the definition of remainder in a division and compute it directly (e.g., the remainder when 140 is divided by 12). *(REMEMBERING)*
2. Explain why a prime number greater than 3 can only leave a remainder of 1 or 5 when divided by 6. *(UNDERSTANDING)*
3. Apply the rule "remainder of a product = product of the remainders" to solve problems such as the remainder when (13 × 15) is divided by 7. *(APPLYING)*
4. Construct the remainder cycle of a base under a fixed divisor and use the exponent's position in that cycle to find the remainder of a large power (e.g., 2^356 divided by 5). *(APPLYING)*
5. Distinguish remainder-of-a-power problems that need the full cycle method from those solvable instantly with a divisibility shortcut. *(ANALYZING)*
6. Differentiate a "power cycle" (the last-digit pattern — i.e., remainders under divisor 10) from a "remainder cycle" (the remainder pattern under any fixed divisor). *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared and ready, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

5 questions on **Session 6 (Power Cycles)**. Newly authored using real numbers from that deck. ~45 s each, project the distribution, never name individuals.

**Q1.** What is the power cycle (last-digit pattern) of 7?
`A` {7,9,3,1} · `B` {7,3,9,1} · `C` {7,1} · `D` {7,9,1,3}
→ **A.** *Targets:* exact order matters. *Read:* If shaky, don't move on — the whole session depends on reading cycles in the correct order.

**Q2.** Which of these digits have a power cycle of length 1? *(MSQ — select all)*
`A` 4 · `B` 5 · `C` 6 · `D` 9
→ **B and C.** *Targets:* {5}, {6} are the two length-1 cycles.

**Q3.** Last digit of 232³²⁹? (2's cycle is {2,4,8,6})
`A` 2 · `B` 4 · `C` 6 · `D` 8
→ **A) 2.** *Targets:* direct real application (329 mod 4 = 1 → 1st position → 2).

**Q4.** Last digit of 234³²⁹? (4's cycle is {4,6})
`A` 2 · `B` 4 · `C` 6 · `D` 8
→ **B) 4.** *Read:* If students answer this by reusing Q3's working, that's the misconception to watch for all session: assuming every base has the same cycle length. Note the number now — it resurfaces today with remainder cycles.

**Q5.** Last digit of the sum (545⁶⁵⁶ + 656⁵⁴⁵)?
`A` 1 · `B` 0 · `C` Can't be determined · `D` None of these
→ **A) 1.** *Targets:* combining two constant cycles.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–11 min)

The deck's own opening two slides are the bridge — use them exactly:

> Slide on screen: **"Recap: Number Systems, Power Cycles."**

Say: *"One-line recap of Session 6: Power Cycles told us how to find the LAST DIGIT of a huge power — because 'last digit' is really just 'remainder when divided by 10.' You just did this in the warm-up: 232 to the power 329, using 2's cycle {2, 4, 8, 6}."*

Ask: *"Now — what if I don't want the remainder on division by 10? What if I want the remainder when 232³²⁹ is divided by 7? Or by 15? Or by 12? Does '2's cycle' still save you?"*

Let a few guesses land — most will hesitate, which is the point.

> Slide on screen: **"Agenda: Remainder Cycles."**

Say: *"Same exact idea as Power Cycles — the remainders of a growing power repeat in a cycle — except now it works for ANY divisor, not only 10. That's a Remainder Cycle. Before we even touch a power, let's make sure 'remainder' itself is solid, because everything today is built on it."*

<!-- placement: inferred — the deck's Agenda slide also lists "Ranking" alongside "Remainder Cycles"; no Ranking problems appear anywhere in the extracted text of this deck, so Ranking is not covered in this plan. Verify whether Ranking is a separate segment/slide the extraction missed, or scheduled elsewhere. -->

---

## Slide Block A (11–19 min) — DELIVER SLIDES AS-IS

Covers: basic remainder → the prime-and-6 property → remainder of a product.

**Beats to emphasise**

- **Slide: "Find the remainder when 140 is divided by 12."** Answer: **8**. Use it to re-anchor the definition: remainder is what's left after removing every full group of the divisor, and it's always smaller than the divisor.
- **Slide: "Find the remainder when a prime number greater than 3 is divided by 6?"** Answer: **5, 1**. The deck's own side question — *"What is a Prime number?"* — is your cue to get a quick definition from the class first. Then show why: a prime greater than 3 can't be divisible by 2 or by 3, and the only remainders mod 6 that avoid both are 1 and 5.
- **Slide: "Find the remainder when (13 × 15) is divided by 7?"** Options A) 6 B) 1 C) 5 D) 0 → Answer **A) 6**. This is the pivot slide. Don't just confirm 13 × 15 = 195 and 195 ÷ 7 = 6 remainder. Show the shortcut: 13 mod 7 = 6, 15 mod 7 = 1, and 6 × 1 mod 7 = 6 — same answer, without ever forming 195. Say explicitly: *"A power is nothing but repeated multiplication. If this shortcut works for one multiplication, it works for a hundred of them in a row — that's the entire idea behind today's cycles."*

**Checkpoint (at 19 min)** — 10 s silent think, cold-call:
> *"Using the shortcut, not long multiplication — what's the remainder when (13 × 15) is divided by 7, and why does taking the remainders first even work?"*
> **Answer:** 6. Because the remainder of a product equals the product of the remainders, taken mod the divisor.

---

## ⚡ ALS Activity 1 — Predict the Remainder (19–27 min)

**ALS format:** Predict, then Verify — two real problems run as guided discovery instead of straight lecture, because this is the session's central new idea. First problem has a small enough exponent that students can out-compute the shortcut, which builds trust in the method. Second problem has an exponent large enough that direct computation is impossible — forcing them to actually use the cycle.

**Setup line:**
> *"Problem one, you can brute-force by hand — do it, and also try the shortcut from the last slide, stretched to a power. Problem two, the exponent is too big to brute-force — the cycle is the only way in. Watch what happens between the two."*

**Problem 1 — "Find the remainder when 4⁵ is divided by 15."**
<!-- placement: inferred — reconstructed as 4^5 (base 4, exponent 5): cycle {4,1}, length 2. 5 is odd → position 1 → remainder 4. Matches the deck's stated answer of 4. Verify against the real slide. -->
**Answer: 4.**

**Problem 2 — "Find the remainder when 2³⁵⁶ is divided by 5."** Options A) 1 B) 2 C) 4 D) 8
<!-- placement: inferred — reconstructed as 2^356. Remainder cycle of 2 mod 5: {2,4,3,1}, length 4. 356 mod 4 = 0 → 4th (last) position → remainder 1. Matches the deck's stated answer A) 1. Verify against the real slide. -->
**Answer: A) 1.**

**When it goes wrong**

| If… | Do this |
|---|---|
| Students try to compute 2³⁵⁶ directly | Let them try for 10 seconds, then stop them: *"That's the point — you can't. The cycle is the only door."* |
| Cycle position arithmetic goes wrong (e.g., using 356 mod 4 = 0 as "0th position") | Write the cycle as a numbered list 1–2–3–4 on the board and show remainder 0 always means "the last slot." |

**Debrief line:**
> *"Same move both times: find the base's remainder cycle under the divisor, then use the exponent's position inside that cycle — not the exponent itself. Problem one you could check by hand. Problem two, there is no other way in. That's why this matters."*

**Cut rule:** If running long, skip the by-hand computation on Problem 1 and go straight to the cycle method for both problems — but do not cut Problem 2; it's the one that proves why the method is necessary.

---

## Slide Block B (27–36 min) — DELIVER SLIDES AS-IS

Covers: the deck's "Quiz Time" problem set — two remainder-cycle problems with different cycle lengths under the *same* divisor.

Say, bridging in: *"The deck calls this next stretch Quiz Time — we're going to walk through it together first, because there's one wrinkle left: cycle length isn't always 4."*

**Beats to emphasise**

- **"Find the remainder when 5¹⁸⁷ is divided by 7?"** Options A) 5 B) 4 C) 6 D) 2 → Answer **A) 5**.
  <!-- placement: inferred — reconstructed as 5^187. Remainder cycle of 5 mod 7: {5,4,6,2,3,1}, length 6. 187 mod 6 = 1 → 1st position → remainder 5. Matches the deck's stated answer A) 5. Verify against the real slide. -->
  This is a length-6 cycle — the first students have seen that isn't 2 or 4. Say plainly: *"Cycle length depends on the base's remainder and the divisor together. There is no universal length."* Use the deck's three side-questions as discussion prompts: *"Why divisibility rule 6 here?"* (cycle is length 6, so exponent's remainder mod 6 gives the position), *"Difference between a power cycle and a remainder cycle?"* (power cycle = remainders under divisor 10; remainder cycle = the same idea under any divisor), and *"Which remainder tells you to stop building the cycle?"* (stop as soon as the very first remainder in the sequence reappears).
- **"Find the remainder when 13⁸⁵⁶ is divided by 7?"** Options A) 6 B) 1 C) 5 D) None of these → Answer **B) 1**.
  <!-- placement: inferred — reconstructed as 13^856. 13 mod 7 = 6. Remainder cycle of 6 mod 7: {6,1}, length 2. 856 mod 2 = 0 → 2nd (last) position → remainder 1. Matches the deck's stated answer B) 1. Verify against the real slide. -->
  Same divisor as the slide above (7), but a length-2 cycle instead of length-6 — deliberately placed back to back. The variable is the base's *own* remainder (13 mod 7 = 6), not the divisor.

**Checkpoint (at 36 min)** — cold-call:
> *"5¹⁸⁷ ÷ 7 needed a length-6 cycle. 13⁸⁵⁶ ÷ 7 needed only length 2. Same divisor — why the different length?"*
> **Answer:** Cycle length is determined by the base's remainder mod the divisor, not the divisor alone.

---

## ⚡ ALS Activity 2 — Shortcut or Cycle? (36–44 min)

**ALS format:** Board Race with a Method-Naming Requirement — two teams race to answer the same two deck problems, but the real task is naming *which* method applies before computing anything: full remainder cycle, or an instant shortcut. Chosen as the closing activity because left untaught, students default to building a cycle every time — slow and error-prone under aptitude-test time pressure — even when the base already tells you the answer directly.

**Setup line:**
> *"Two problems. For each one, before you say a single number, tell me: full cycle, or is there a shortcut sitting right there? Team that names the right method AND the right answer first gets the point. Guessing the answer with the wrong method doesn't count."*

**Problem A — "Find the remainder when 477⁸⁵⁶ is divided by 4?"** Options A) 1 B) 0 C) 3 D) 2
<!-- placement: inferred — reconstructed as 477^856. Shortcut: 477 mod 4 = 1, so 1 to any power is still 1 — remainder 1 instantly, no cycle needed. Matches the deck's stated answer A) 1. Verify against the real slide. -->
**Answer: A) 1** — shortcut: the base itself is ≡ 1 mod 4, so every power of it is also ≡ 1.

**Problem B — "Find the remainder when 123456789¹²³⁴⁵⁶⁷⁸⁹ is divided by 9."**
<!-- placement: inferred — same number used as both base and exponent, a deliberate deck trick. Shortcut: digit sum of 123456789 = 45, divisible by 9, so the base ≡ 0 mod 9. Zero to any positive power is 0. Matches the deck's stated answer of 0. Verify against the real slide. -->
**Answer: 0** — shortcut: digit sum of the base is 45 (divisible by 9), so the base ≡ 0 mod 9.

**When it goes wrong**

| If… | Do this |
|---|---|
| A team says "digit-sum rule" applies to Problem A too | Correct immediately — the digit-sum shortcut works for divisors 9 (and 3), not 4. Mixing this up is the exact trap this activity is built to catch. |
| Both teams freeze, unsure how to "prove" a shortcut applies | Model it once out loud on Problem A: *"477 mod 4 — is it 0 or 1? It's 1. Done."* Then hand Problem B to them cold. |

**Debrief line:**
> *"Both of these would have worked with a full cycle too — but you'd have burned two minutes proving what one divisibility check told you in five seconds. Before you build a cycle, always check: is the base already 0 or 1 mod the divisor? If yes, you're done before you started."*

**Cut rule:** If short on time, run Problem B only — the same-number-as-its-own-exponent trick is the more memorable takeaway.

---

## Exit Ticket + Homework (44–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> Write the remainder cycle of 2 under divisor 5, and use it to state the remainder when 2³⁵⁶ is divided by 5.
> **Answers:** Cycle = {2, 4, 3, 1}, length 4. 356 mod 4 = 0 → last (4th) position → remainder **1**.

Scan responses on the way out. Anyone who tries to answer without writing the cycle first is the signal to revisit the method, not just the number, at the start of Session 8.

**Homework**

- Rework all of today's deck problems from scratch — direct remainder, the prime-mod-6 fact, the product-remainder shortcut, and all four "Quiz Time" problems — without looking at today's worked answers first. Write out the remainder cycle explicitly for each base before computing.
- Then attempt the four "Quiz Time" problems a second time, timed, aiming under 90 seconds each.
- Review the Session 6 power-cycle list — building a cycle for a fixed divisor is the identical skill, just applied beyond divisor 10.

> *"Next session builds directly on this. If you haven't built a remainder cycle with your own hand by tomorrow, today's method won't have stuck."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Every remainder cycle has length 4 (or 2) | Session 6's power cycles were mostly length 2 or 4, and ALS Activity 1's first example was also length 2 | Slide Block B — placing the length-6 cycle (5 mod 7) directly next to the length-2 cycle (13 mod 7), same divisor |
| "Power cycle" and "remainder cycle" are the same thing | Both involve repeating patterns of powers | The deck's own question on the 5¹⁸⁷ slide — a power cycle is specifically the remainder pattern under divisor 10; a remainder cycle generalises to any divisor |
| You must always build the full cycle, even when a shortcut is faster | The cycle method is the new tool everyone wants to practice | ALS Activity 2 — both problems solved in one line via a divisibility fact on the base itself |
| Remainder of a product needs the full numbers multiplied first | That's the longer method they already trust | Slide Block A — (13 × 15) ÷ 7 solved by taking remainders first |
| A prime divided by 6 could leave any remainder | No reason yet to think otherwise | Slide Block A — showing only 1 or 5 are possible |
| Not knowing when to stop extending a remainder cycle | No stated stopping rule | The deck's own question on the 5¹⁸⁷ slide — stop the moment the first remainder in the sequence reappears |

---

## Instructor Notes

- **This plan is grounded entirely in a local pptx text-extraction** (`NIAT Remainder Cycles.pptx`), not a platform export. No unit IDs, quiz-pool IDs, or question IDs exist to cite for this topic.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **This session already ran exactly 2 activities before this recalibration** — the extracted deck contains exactly 9 real problems, all distributed across Slide Blocks A/B and the two ALS activities. No activity was demoted or folded here; only timing and headers changed.
- **Exponent reconstruction — verify every one of these against the real slide before class.** The extraction tool drops the `^` symbol. Every split was reconstructed by working backward from the deck's own stated correct answer, marked `<!-- placement: inferred -->` at its location.
- **"Ranking" is named on the deck's own Agenda slide alongside "Remainder Cycles," but no Ranking problem appears anywhere in the extracted text.** Not covered in this plan. Confirm with the source deck.
- **"Quiz Time" appears twice in the source deck (as bare title slides)** — these are section dividers, not additional content.
- **Do the cycle arithmetic yourself before class** even though it's shown worked above — a single arithmetic slip while live-teaching a brand-new method is much harder to recover from than in a familiar topic.
- **The deck's own side-questions are the best teaching material it has** — used deliberately as discussion prompts throughout this plan rather than skipped as throwaway captions.
