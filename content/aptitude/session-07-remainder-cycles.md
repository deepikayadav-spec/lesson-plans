# Session 7 — Remainder Cycles

**Duration** 60 min · **Topic** Remainder Cycles · **Prerequisite** Session 6 (Power Cycles)
**Session type** Lecture. No classroom quiz bank, MCQ pool, or coding/problem-practice unit IDs exist yet for this topic.

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
5. Distinguish remainder-of-a-power problems that need the full cycle method from those solvable instantly with a divisibility shortcut (e.g., mod 4 on the base itself, the digit-sum rule for 9). *(ANALYZING)*
6. Differentiate a "power cycle" (the last-digit pattern — i.e., remainders under divisor 10) from a "remainder cycle" (the remainder pattern under any fixed divisor). *(ANALYZING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 6 (Power Cycles)**. Newly authored using real numbers from that deck. ~45 s each, project the distribution, never name individuals.

**Q1.** What is the power cycle (last-digit pattern) of 7?
`A` {7,9,3,1} · `B` {7,3,9,1} · `C` {7,1} · `D` {7,9,1,3}
→ **A.** *Targets:* exact order matters — you read a position off this list, not just membership.
→ *Read:* If this is shaky, don't move on — the whole session depends on reading cycles in the correct order.

**Q2.** Which of these digits have a power cycle of length 1 — every power ends in the same digit? *(MSQ — select all)*
`A` 4 · `B` 5 · `C` 6 · `D` 9
→ **B and C.** *Targets:* {5}, {6} are the two length-1 cycles from Session 6's table. *Misconception:* picking 4 or 9 — both actually cycle (length 2).

**Q3.** Last digit of 232³²⁹? (2's cycle is {2,4,8,6})
`A` 2 · `B` 4 · `C` 6 · `D` 8
→ **A) 2.** *Targets:* direct real application from the Session 6 deck (329 mod 4 = 1 → 1st position → 2).

**Q4.** Last digit of 234³²⁹? (4's cycle is {4,6})
`A` 2 · `B` 4 · `C` 6 · `D` 8
→ **B) 4.** *Targets:* a shorter cycle (length 2) right next to Q3's length-4 cycle, same exponent.
→ *Read:* If students answer this by reusing Q3's working, that's the misconception to watch for all session: assuming every base has the same cycle length. Note the number now — it resurfaces today with remainder cycles.

**Q5.** Last digit of the sum (545⁶⁵⁶ + 656⁵⁴⁵)?
`A` 1 · `B` 0 · `C` Can't be determined · `D` None of these
→ **A) 1.** *Targets:* 5's cycle is {5} (always 5), 6's cycle is {6} (always 6); 5 + 6 → last digit 1. Analysis-level: combining two constant cycles.

**Q6.** How many trailing zeros in 57 × 45 × 30 × 12?
`A` 2 · `B` 3 · `C` 4 · `D` 1
→ **A) 2.** *Targets:* trailing zeros = min(count of 2s, count of 5s) among the factors — a different but related "find the pattern, don't multiply it all out" skill.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–10 min)

The deck's own opening two slides are the bridge — use them exactly:

> Slide on screen: **"Recap: Number Systems, Power Cycles."**

Say: *"One-line recap of Session 6: Power Cycles told us how to find the LAST DIGIT of a huge power — because 'last digit' is really just 'remainder when divided by 10.' You just did this in the warm-up: 232 to the power 329, using 2's cycle {2, 4, 8, 6}."*

Ask: *"Now — what if I don't want the remainder on division by 10? What if I want the remainder when 232³²⁹ is divided by 7? Or by 15? Or by 12? Does '2's cycle' still save you?"*

Let a few guesses land — most will hesitate, which is the point.

> Slide on screen: **"Agenda: Remainder Cycles."**

Say: *"Same exact idea as Power Cycles — the remainders of a growing power repeat in a cycle — except now it works for ANY divisor, not only 10. That's a Remainder Cycle. Before we even touch a power, let's make sure 'remainder' itself is solid, because everything today is built on it."*

<!-- placement: inferred — the deck's Agenda slide also lists "Ranking" alongside "Remainder Cycles"; no Ranking problems appear anywhere in the extracted text of this deck, so Ranking is not covered in this plan. Verify whether Ranking is a separate segment/slide the extraction missed, or scheduled elsewhere. -->

---

## Slide Block A (10–24 min) — DELIVER SLIDES AS-IS

Covers: basic remainder → the prime-and-6 property → remainder of a product.

**Beats to emphasise**

- **Slide: "Find the remainder when 140 is divided by 12."** Answer: **8**. Use it to re-anchor the definition: remainder is what's left after removing every full group of the divisor, and it's always smaller than the divisor. No power involved yet — this is the floor everything else stands on.
- **Slide: "Find the remainder when a prime number greater than 3 is divided by 6?"** Answer: **5, 1**. The deck's own side question — *"What is a Prime number?"* — is your cue to get a quick definition from the class first. Then show why: a prime greater than 3 can't be divisible by 2 or by 3, and the only remainders mod 6 that avoid both are 1 and 5. This is a property they'll reuse constantly in aptitude problems, not just today.
- **Slide: "Find the remainder when (13 × 15) is divided by 7?"** Options A) 6 B) 1 C) 5 D) 0 → Answer **A) 6**. This is the pivot slide. Don't just confirm 13 × 15 = 195 and 195 ÷ 7 = 6 remainder. Show the shortcut: 13 mod 7 = 6, 15 mod 7 = 1, and 6 × 1 mod 7 = 6 — same answer, without ever forming 195. Say explicitly: *"A power is nothing but repeated multiplication. If this shortcut works for one multiplication, it works for a hundred of them in a row — that's the entire idea behind today's cycles."*

**Checkpoint (at 24 min)** — cold-call:
> *"Using the shortcut, not long multiplication — what's the remainder when (13 × 15) is divided by 7, and why does taking the remainders first even work?"*
> **Answer:** 6. Because the remainder of a product equals the product of the remainders, taken mod the divisor — 13 mod 7 = 6, 15 mod 7 = 1, 6 × 1 mod 7 = 6.

---

## ⚡ Activity 1 — Predict the Remainder (24–32 min)

**Format:** Predict the Output, adapted · **Exposes:** the jump from "remainder of a product" (just taught) to "remainder of a power," and the fact that a power's remainders repeat in a cycle just like a power's last digits did in Session 6.

### What this activity is

Two real problems from the deck, run as guided discovery instead of straight lecture, because this is the session's central new idea. First problem has a small enough exponent that students can out-compute the shortcut, which builds trust in the method. Second problem has an exponent large enough that direct computation is impossible — forcing them to actually use the cycle.

### Why it's here

Slide Block A ended on "remainder of a product." This activity is the bridge that turns that one-step shortcut into a repeatable *cycle* method for powers — the core technique of the whole session.

### Before class

Have both problems ready to reveal one at a time. A whiteboard or slide space for building a remainder table (exponent → remainder) helps for Problem 2.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, reveal Problem 1 | Listen |
| 0:30–2:30 | Wait | Compute 4⁵ directly by hand and find the remainder on their own |
| 2:30–3:00 | Reveal the cycle method alongside their direct answer | Check the two match |
| 3:00–3:30 | Reveal Problem 2 | Listen |
| 3:30–5:30 | Prompt them to build the remainder cycle of 2 mod 5 | Build the cycle, find the exponent's position in it |
| 5:30–6:30 | Take answers, confirm | Answer, watch |
| 6:30–8:00 | Debrief | Listen |

### Say this

> *"Problem one, you can brute-force by hand — do it, and also try the shortcut from the last slide, stretched to a power. Problem two, the exponent is too big to brute-force — the cycle is the only way in. Watch what happens between the two."*

### The problems

**Problem 1 — "Find the remainder when 4⁵ is divided by 15."**
<!-- placement: inferred — extracted text reads "Find the remainder when 4 | 5 | is divided by 15", i.e. the exponent lost its caret. Reconstructed as 4^5 (base 4, exponent 5): 4^1=4, 4^2=16→1, 4^3=4, 4^4=1 mod 15 — cycle {4,1}, length 2. 5 is odd → position 1 → remainder 4. This matches the deck's stated answer of 4, confirming the split. Direct check: 4^5 = 1024, 1024 ÷ 15 = 68 remainder 4 — same answer either way. Verify against the real slide. -->
**Answer: 4.**

**Problem 2 — "Find the remainder when 2³⁵⁶ is divided by 5."** Options A) 1 B) 2 C) 4 D) 8
<!-- placement: inferred — extracted text reads "Find the remainder when 2 | 356 | is divided by 5", reconstructed as 2^356 (base 2, exponent 356). Remainder cycle of 2 mod 5: 2^1=2, 2^2=4, 2^3=8→3, 2^4=16→1 — cycle {2,4,3,1}, length 4. 356 mod 4 = 0 → 4th (last) position → remainder 1. Matches the deck's stated answer A) 1, confirming the split. The deck's own side question here — "Why are we using divisibility rule 4?" — is exactly this: checking the exponent's divisibility by 4 because the cycle length is 4. Verify against the real slide. -->
**Answer: A) 1.**

### Debrief line

> *"Same move both times: find the base's remainder cycle under the divisor, then use the exponent's position inside that cycle — not the exponent itself. Problem one you could check by hand. Problem two, there is no other way in. That's why this matters."*

### When it goes wrong

| If… | Do this |
|---|---|
| Students try to compute 2³⁵⁶ directly | Let them try for 10 seconds, then stop them: *"That's the point — you can't. The cycle is the only door."* |
| A student assumes the cycle length is always 4 (carried over from Session 6, where most digits cycled at length 4) | Don't correct yet — flag it and say Slide Block B breaks this assumption on purpose. |
| Cycle position arithmetic goes wrong (e.g., using 356 mod 4 = 0 as "0th position" instead of the last/4th position) | Write the cycle as a numbered list 1–2–3–4 on the board and show that remainder 0 always means "the last slot," never a zeroth slot. |
| Room is fast and bored | Ask them to also state the remainder cycle of 4 mod 15 out loud before moving to Problem 2 — reinforces the pattern without new content. |

**Common instructor mistake:** revealing the cycle-method answer before students finish the by-hand computation on Problem 1. The trust-building only works if they get there themselves first.

**Cut rule:** If running long, skip the by-hand computation on Problem 1 and go straight to the cycle method for both problems — but do not cut Problem 2; it's the one that proves why the method is necessary, not just convenient.

---

## Classroom Quiz

> Classroom Quiz: not yet available — add once question bank exists for this topic.

**Time reallocated.** The standard 60-minute template gives this slot 7 minutes (normally 27–34 min) and a third activity 7 minutes. Neither runs this session (see Instructor Notes for why). Those 14 minutes are folded into the blocks below with no gap in the timeline: Slide Block A +2 min, Activity 1 +3 min, Slide Block B +4 min, Activity 2 +2 min, Exit Ticket + Homework +3 min.

---

## Slide Block B (32–46 min) — DELIVER SLIDES AS-IS

Covers: the deck's "Quiz Time" problem set — two remainder-cycle problems with different cycle lengths under the *same* divisor.

Say, bridging in: *"The deck calls this next stretch Quiz Time — we're going to walk through it together first, because there's one wrinkle left: cycle length isn't always 4."*

**Beats to emphasise**

- **"Find the remainder when 5¹⁸⁷ is divided by 7?"** Options A) 5 B) 4 C) 6 D) 2 → Answer **A) 5**.
  <!-- placement: inferred — extracted text reads "Find the remainder when 5 | 187 | is divided by 7", reconstructed as 5^187. Remainder cycle of 5 mod 7: 5^1=5, 5^2=25→4, 5^3=125→6, 5^4=30→2, 5^5=10→3, 5^6=15→1 — cycle {5,4,6,2,3,1}, length 6. 187 mod 6 = 1 → 1st position → remainder 5. Matches the deck's stated answer A) 5, confirming the split. Verify against the real slide. -->
  This is a length-6 cycle — the first one students have seen that isn't 2 or 4. Say it plainly: *"Cycle length depends on the base's remainder and the divisor together. There is no universal length."* The deck stacks three side-questions on this exact slide — use all three as discussion prompts, not throwaways: *"Why divisibility rule 6 here?"* (because the cycle is length 6, so the exponent's remainder mod 6 gives the position), *"What's the difference between a power cycle and a remainder cycle, in terms of remainders?"* (power cycle = the special case of remainders under divisor 10; remainder cycle = the same idea under any divisor), and *"Which remainder tells you to stop building the cycle?"* (stop as soon as the very first remainder in the sequence reappears — that's where it starts repeating).
- **"Find the remainder when 13⁸⁵⁶ is divided by 7?"** Options A) 6 B) 1 C) 5 D) None of these → Answer **B) 1**.
  <!-- placement: inferred — extracted text reads "Find the remainder when 13 | 856 | is divided by 7", reconstructed as 13^856. 13 mod 7 = 6. Remainder cycle of 6 mod 7: 6^1=6, 6^2=36→1 — cycle {6,1}, length 2. 856 mod 2 = 0 → 2nd (last) position → remainder 1. Matches the deck's stated answer B) 1, confirming the split. Verify against the real slide. -->
  Same divisor as the slide above (7), but a length-2 cycle instead of length-6 — deliberately place these two back to back. The variable is the base's *own* remainder (13 mod 7 = 6), not the divisor.

**Checkpoint (at 46 min)** — cold-call:
> *"5¹⁸⁷ ÷ 7 needed a length-6 cycle. 13⁸⁵⁶ ÷ 7 needed only length 2. Same divisor — why the different length?"*
> **Answer:** Cycle length is determined by the base's remainder mod the divisor, not the divisor alone. 5's remainder pattern under mod 7 takes 6 steps to return to 1; 6's (13 mod 7 = 6) takes only 2.

---

## ⚡ Activity 2 — Shortcut or Cycle? (46–54 min)

**Format:** Rapid Fire Board Race, adapted · **Exposes:** the assumption that every remainder-of-a-power question requires building a full cycle — when sometimes a plain divisibility fact settles it instantly.

### What this activity is

Two teams race to answer the same two deck problems, but the real task is naming *which* method applies before computing anything: full remainder cycle, or an instant shortcut. First team to correctly name the method **and** the answer scores; naming the wrong method but the right answer doesn't count.

### Why it's here

Objective 5 is explicitly this judgment call. Left untaught, students default to building a cycle every time — slow and error-prone under aptitude-test time pressure — even when the base already tells you the answer directly.

### Before class

Have both problems on slides, hidden until revealed. Keep a simple team scoreboard on the board.

### Run it

| Time | You do | Students do |
|---|---|---|
| 0:00–0:30 | Setup line, reveal Problem A | Listen |
| 0:30–2:30 | Wait, take first raised hand per team | Decide: cycle needed, or shortcut? Shout method + answer |
| 2:30–3:30 | Confirm, run the shortcut live on the board | Watch |
| 3:30–4:00 | Reveal Problem B | Listen |
| 4:00–6:00 | Wait, take first raised hand per team | Decide: cycle needed, or shortcut? Shout method + answer |
| 6:00–7:00 | Confirm, run the shortcut live on the board | Watch |
| 7:00–8:00 | Debrief | Listen |

### Say this

> *"Two problems. For each one, before you say a single number, tell me: full cycle, or is there a shortcut sitting right there? Team that names the right method AND the right answer first gets the point. Guessing the answer with the wrong method doesn't count."*

### The problems

**Problem A — "Find the remainder when 477⁸⁵⁶ is divided by 4?"** Options A) 1 B) 0 C) 3 D) 2
<!-- placement: inferred — extracted text reads "Find the remainder when 477 | 856 | is divided by 4", reconstructed as 477^856. Shortcut: 477 mod 4 = 1 (4 × 119 = 476), so 1 raised to any power is still 1 — remainder 1 instantly, no cycle needed. Matches the deck's stated answer A) 1, confirming the split. Verify against the real slide. -->
**Answer: A) 1** — shortcut: the base itself is ≡ 1 mod 4, so every power of it is also ≡ 1. No cycle required.

**Problem B — "Find the remainder when 123456789¹²³⁴⁵⁶⁷⁸⁹ is divided by 9."**
<!-- placement: inferred — extracted text reads "Find the remainder when 123456789 | 123456789 | is divided by 9", reconstructed as the same number, 123456789, used as both base and exponent. This is a deliberate deck "trick," not an extraction duplication artifact. Shortcut: digit sum of 123456789 = 45, and 45 is divisible by 9, so the base itself is ≡ 0 mod 9. Zero raised to any positive power is 0 — remainder 0 instantly. Matches the deck's stated answer of 0, confirming the reading. Verify against the real slide. -->
**Answer: 0** — shortcut: digit sum of the base is 45 (divisible by 9), so the base ≡ 0 mod 9, and a positive power of 0 stays 0.

### Debrief line

> *"Both of these would have worked with a full cycle too — but you'd have burned two minutes proving what one divisibility check told you in five seconds. Before you build a cycle, always check: is the base already 0 or 1 mod the divisor? If yes, you're done before you started."*

### When it goes wrong

| If… | Do this |
|---|---|
| A team builds the full cycle for Problem A anyway (477¹, 477², … mod 4) | Let them finish — they'll land on 1 every time since 1 to any power is 1. Point out they got the right answer the slow way, and ask what they noticed. |
| A team says "digit-sum rule" applies to Problem A too | Correct immediately — the digit-sum shortcut works for divisors 9 (and 3), not 4. Mixing this up is the exact trap this activity is built to catch. |
| A team answers Problem B instantly without checking the exponent is positive | Praise the shortcut, then ask: *"What if the exponent were 0 instead?"* — flag that 0 to the power 0 is a special case, so always glance at the exponent before declaring 0. |
| Both teams freeze, unsure how to "prove" a shortcut applies | Model it once out loud on Problem A: *"477 mod 4 — is it 0 or 1? It's 1. Done."* Then hand Problem B to them cold. |

**Common instructor mistake:** naming the shortcut for the class instead of making them justify *why* it works. If you skip the "why," this activity becomes a lecture with extra shouting.

**Cut rule:** If short on time, run Problem B only — the same-number-as-its-own-exponent trick is the more memorable takeaway and covers the digit-sum shortcut, the rarer of the two skills.

---

## Exit Ticket + Homework (54–60 min)

**Exit ticket** — before anyone leaves:

> Write the remainder cycle of 2 under divisor 5, and use it to state the remainder when 2³⁵⁶ is divided by 5.
> **Answers:** Cycle = {2, 4, 3, 1}, length 4. 356 mod 4 = 0 → last (4th) position → remainder **1**.

Scan responses on the way out. Anyone who tries to answer without writing the cycle first is the signal to revisit the method, not just the number, at the start of Session 8.

**Homework**

- Rework all of today's deck problems from scratch — direct remainder, the prime-mod-6 fact, the product-remainder shortcut, and all four "Quiz Time" problems (5¹⁸⁷ ÷ 7, 13⁸⁵⁶ ÷ 7, 477⁸⁵⁶ ÷ 4, 123456789^123456789 ÷ 9) — without looking at today's worked answers first. Write out the remainder cycle explicitly for each base before computing.
- Then attempt the four "Quiz Time" problems a second time, timed, aiming under 90 seconds each — that is aptitude-test pace, not classroom pace.
- Review the Session 6 power-cycle list ({2,4,8,6}, {3,9,7,1}, {4,6}, {5}, {6}, {7,9,3,1}, {8,4,2,6}, {9,1}) — building a cycle for a fixed divisor is the identical skill, just applied beyond divisor 10.

> *"Next session builds directly on this. If you haven't built a remainder cycle with your own hand by tomorrow, today's method won't have stuck."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Every remainder cycle has length 4 (or 2) | Session 6's power cycles were mostly length 2 or 4, and Activity 1's first example was also length 2 | Slide Block B — placing the length-6 cycle (5 mod 7) directly next to the length-2 cycle (13 mod 7, i.e. 6 mod 7), same divisor |
| "Power cycle" and "remainder cycle" are the same thing | Both involve repeating patterns of powers | The deck's own question on the 5¹⁸⁷ slide — a power cycle is specifically the remainder pattern under divisor 10 (last digit); a remainder cycle generalises to any divisor |
| You must always build the full cycle, even when a shortcut is faster | The cycle method is the new tool everyone wants to practice | Activity 2 — 477⁸⁵⁶ ÷ 4 and 123456789^123456789 ÷ 9, both solved in one line via a divisibility fact on the base itself |
| Remainder of a product needs the full numbers multiplied first | That's the longer method they already trust | Slide Block A — (13 × 15) ÷ 7 solved by taking remainders first, then multiplying |
| A prime divided by 6 could leave any remainder | No reason yet to think otherwise | Slide Block A — showing only 1 or 5 are possible, tied to the definition of prime (not divisible by 2 or 3) |
| Not knowing when to stop extending a remainder cycle | No stated stopping rule | The deck's own question on the 5¹⁸⁷ slide — stop the moment the first remainder in the sequence reappears |

---

## Instructor Notes

- **This plan is grounded entirely in a local pptx text-extraction** (`NIAT Remainder Cycles.pptx`), not a platform export. There are no unit IDs, quiz-pool IDs, or question IDs to cite for this topic — none have been invented anywhere in this document.
- **Exponent reconstruction — verify every one of these against the real slide before class.** The extraction tool drops the `^` symbol, turning e.g. "5^195" into "5195." Every split below was reconstructed by working backward from the deck's own stated correct answer, and each is marked `<!-- placement: inferred -->` at its location in this document:
  - Slide "4|5|÷15" → 4^5 ÷ 15 = 4 ✓ (confirmed against stated answer 4)
  - Slide "2|356|÷5" → 2^356 ÷ 5 = 1 ✓ (confirmed against stated answer A/1)
  - Slide "5|187|÷7" → 5^187 ÷ 7 = 5 ✓ (confirmed against stated answer A/5)
  - Slide "13|856|÷7" → 13^856 ÷ 7 = 1 ✓ (confirmed against stated answer B/1)
  - Slide "477|856|÷4" → 477^856 ÷ 4 = 1 ✓ (confirmed against stated answer A/1)
  - Slide "123456789|123456789|÷9" → 123456789^123456789 ÷ 9 = 0 ✓ (confirmed against stated answer 0). This one is a deliberate deck trick — same number as both base and exponent — not a duplication artifact of the extraction.
- **The exponent 856 appears twice** (13^856 and 477^856), on two different slides with two different bases and divisors. Checked independently — both are real, distinct problems; this is not an extraction error.
- **"Ranking" is named on the deck's own Agenda slide alongside "Remainder Cycles," but no Ranking problem appears anywhere in the extracted text.** Not covered in this plan. Confirm with the source deck whether this is a separate short segment the text-extraction missed, or content scheduled elsewhere. `<!-- placement: inferred: out of scope for this plan -->`
- **This session runs 2 activities, not 3.** The extracted deck contains exactly 9 real problems; all 9 are already distributed across Slide Blocks A/B and Activities 1–2. A third activity would either repeat numbers already used or invent new ones — both against the grounding rule for this plan. The time a third activity would have used is folded into the retimed blocks instead (see the Classroom Quiz section above for the exact reallocation).
- **"Quiz Time" appears twice in the source deck (as bare title slides)** — these are section dividers, not additional content. The problems that sit between and after them are the ones already placed in Slide Block B and Activity 2.
- **Do the cycle arithmetic yourself before class** (e.g. 187 mod 6, 856 mod 2, 356 mod 4) even though it's shown worked above — a single arithmetic slip while live-teaching a brand-new method is much harder to recover from than in a familiar topic.
- **The deck's own side-questions are the best teaching material it has** — "What is a Prime number?", "Why divisibility rule 4/6?", "Difference between power cycle and remainder cycle?", "Which remainder tells you to stop?", "What is the divisibility rule of 9?" — all five are used deliberately as discussion prompts in this plan rather than skipped as throwaway captions.
