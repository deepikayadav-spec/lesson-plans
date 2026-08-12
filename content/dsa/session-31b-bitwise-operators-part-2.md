# Session 31b — Bitwise Operators (Part 2 of 2)

**Duration** 32 min · **Topic** Bit Manipulation — XOR, NOT, Shifts & Applications · **Prerequisite** Session 31a — Bitwise Operators, Part 1 (AND, OR, real-world uses) · **Session type** Concept lecture

<!-- Split note: continues session-31 (original 55 min) right after the Classroom Quiz. This part covers XOR, NOT, shifts, applications, and INT_MAX/INT_MIN — including the session's hardest and most counterintuitive idea, why `~5` prints `-6`. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Bitwise Operators | https://docs.google.com/presentation/d/1r3lgW5W1n5JPdDWsRypWIFRPhCqCphmAq205XQhIeVU/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State what XOR and NOT each do, using their truth tables. *(REMEMBERING)*
2. Compute the result of XOR and NOT on given binary numbers by hand. *(APPLYING)*
3. Explain left shift and right shift as multiplication/division by powers of 2 (`n << k = n * 2^k`, `n >> k = n / 2^k`) and predict their output. *(APPLYING)*
4. Explain why `~5` prints as `-6` in code rather than the "obvious" flipped-bits value. *(ANALYZING)*

<!-- placement: inferred from the Key Takeaways slide (55) and the deck's own C++ output slide (53), which is the only slide that surfaces the NOT/negative-number subtlety. -->

---

## Warm-Up Poll — Retrieval Practice on Session 31a (0–5 min)

Say: *"Four quick ones on AND/OR before we add a third operator that disagrees with both of them."*

**Q1.** AND requires:
`A` At least one bit to be 1 · `B` Both bits to be 1 · `C` Exactly one bit to be 1 · `D` Neither bit to be 1
→ *Read:* B.

**Q2.** OR requires:
`A` At least one bit to be 1 · `B` Both bits to be 1 · `C` Exactly one bit to be 1 · `D` Neither bit to be 1
→ *Read:* A.

**Q3.** `1010 & 0110` — what's the result?
`A` `0010` · `B` `1110` · `C` `1100` · `D` `0000`
→ *Read:* A.

**Q4.** Name one real system that packs multiple yes/no flags into a single number, from Part 1's callout.
→ *Read:* Open response — reconnects to the real-world framing before the new operators land.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"You have two people standing means both AND and OR say yes. Here's an operator that says no to that exact case — and it's the one that shows up everywhere from checksums to toggling a single flag."*

---

## Slide Block B (7–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — slides 24-54: XOR, NOT, left shift, right shift, code + output, applications, INT_MAX/INT_MIN -->
Covers: Bitwise XOR (`^`) with truth table, worked example, and the odd/even-count-of-1s rule for multi-value XOR → Bitwise NOT (`~`) with truth table and worked example → Left Shift (`<<`, multiply by 2^k) → Right Shift (`>>`, divide by 2^k) → full code implementation and its printed output → Applications (memory optimization, data compression, cryptography, algorithms/puzzles, low-level hardware control) → INT_MAX / INT_MIN as 32-bit sign-bit boundaries.

**Beats to emphasise**

- XOR: "exactly one must be 1, not both." Show the deck's 3-input XOR truth table (slide 31) and state the general rule out loud: *"XOR of several bits is 1 if the count of 1s among them is odd, 0 if even."*
- NOT: run the deck's own C++ output live — `~0101` on paper looks like `1010` (which would be 10), but the code prints `-6`. Don't resolve this yet — flag it explicitly: *"Hold that thought, we're about to spend an activity on exactly this."*
- Shifts: `n << k = n * 2^k`, `n >> k = n / 2^k` (integer division). Run the deck's own example live: `9 << 2 = 36`, `9 >> 2 = 2`.
- On INT_MAX/INT_MIN: connect directly back to Session 29's sign-bit content — MSB 0 with all other 31 bits set to 1 gives `2^31 - 1` (INT_MAX); MSB 1 with all other bits 0 gives `-2^31` (INT_MIN).

**Checkpoint (at 19 min)** — cold-call:
> *"In one sentence: what does XOR do that AND and OR don't?"*
> **Answer:** XOR is 1 only when the two bits differ (exactly one is 1) — AND needs both, OR needs at least one, XOR needs exactly one.

---

## ⚡ Activity 2 — Predict-the-Output: Fresh Numbers Through AND / OR / XOR (19–24 min)

**Format:** Predict-the-Output · **Exposes:** memorized answers to the deck's own repeated `5` and `3` examples, rather than genuine understanding of the bit-by-bit mechanics.

**Setup line (say this):**
> *"New numbers — not 5 and 3 this time. `1100` and `1010`. Before I write anything, commit out loud to what `1100 & 1010`, `1100 | 1010`, and `1100 ^ 1010` each equal."*

**What students do:** Predict all three results before you reveal. Work column by column live: AND → `1000`, OR → `1110`, XOR → `0110`.

**How to handle wrong answers:** If someone gives the same answer for OR and XOR, that's the exact AND-vs-OR-vs-XOR conflation this activity targets — go back to column 4 (leftmost: both bits are 1) and ask what OR gives there versus what XOR gives there.

**Debrief line:**
> *"OR and XOR only disagree in exactly one situation — both bits are 1. OR still says yes (1), XOR says no (0) because 'exactly one' isn't satisfied. That single column is the entire difference between the two operators — check it first whenever you're unsure which one you're looking at."*

**Cut rule:** If short on time, do only AND and XOR (skip OR) — the AND/XOR pairing carries more of the confusion than OR does.

---

## ⚡ Activity 3 — Spot the Bug: Why Does `~5` Print `-6`? (24–29 min)

**Format:** Spot the Bug · **Exposes:** the assumption that NOT is a simple visible-bit flip (`0101` → `1010` = 10), ignoring that integers are stored as fixed-width 32-bit two's-complement values, so *every* bit flips, including the 28 leading zeros — and the result's sign bit determines how it prints.

**Setup line (say this):**
> *"By hand, `~0101` looks like `1010`, which is 10. The deck's own C++ code runs `bitwiseNOT(5)` and prints `-6`. Somebody is wrong — is it the deck, or is it your hand calculation? Sixty seconds, then defend your answer."*

**What students do:** Discuss in pairs. The deck's own note (slide 49) is the resolving evidence: 5 as a 32-bit integer is `00000000 00000000 00000000 00000101`; NOT flips *all 32 bits*, including every leading zero, giving `11111111 11111111 11111111 11111010`. That bit pattern, interpreted as a signed 32-bit integer (sign bit 1 → negative, take 2's complement to find magnitude), is `-6`.

**How to handle wrong answers:** If a pair insists the deck's output is wrong, walk them through interpreting `11111111...11111010` as a signed integer using the same sign-bit method from Session 29's complement content — MSB is 1, so it's negative; 2's complement of the pattern gives magnitude 6.

**Debrief line:**
> *"Your hand calculation wasn't wrong on the bits you wrote down — it was incomplete. You only flipped the 4 bits you could see, but a computer's integer has 32 bits, and NOT flips every single one, including all those invisible leading zeros. Once you flip all 32 and read the sign bit, `-6` is exactly correct."*

**Cut rule:** If very tight on time, skip the pair discussion and present the resolution directly — the debrief line is the actual payoff and stands alone.

---

## Exit Ticket (29–32 min)

> On paper before anyone leaves: Compute `1011 & 0110`, `1011 | 0110`, and `1011 ^ 0110`. Then in one sentence, say what `9 >> 1` equals and why.
> **Answers:** AND = `0010`, OR = `1111`, XOR = `1101`. `9 >> 1 = 4` (integer division of 9 by 2, dropping the remainder — right shift discards the bit that falls off the end).

Scan on the way out. If OR and XOR answers match, reopen Activity 2's debrief for 60 seconds at the start of Session 32.

**Homework:** re-derive today's `~5 = -6` result from scratch, writing out all 32 bits. <!-- placement: inferred — no homework/practice-unit table exists for this course; this is a natural close, not a platform assignment -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| OR and XOR give the same result | Both only differ from AND by "needing fewer 1s" and feel interchangeable at a glance | Activity 2 — isolating the exact column where both bits are 1, the only place they diverge |
| `~5` should just be the visible bits flipped (`1010` = 10) | Students only write down the 4 bits they can see, forgetting integers are fixed-width (32-bit) | Activity 3 — flipping all 32 bits including leading zeros, then reading the sign bit |
| XOR-ing three or more values always cancels to 0 | Generalizing from `a ^ a = 0`, without checking the odd/even-count-of-1s rule | Slide Block B's 3-input XOR truth table — showing cases where the XOR of three bits is 1, not 0 |
| Left shift is always safe and never loses information | The deck's own examples (`9 << 1`, `9 << 2`) stay comfortably within normal integer range | Connecting forward to INT_MAX — a left shift that pushes past `2^31 - 1` overflows into undefined/negative territory |

---

## Instructor Notes

- **This is Part 2 of a 55-minute original session, split right after the Classroom Quiz.**
- **The `~5 = -6` result (Activity 3) is the single most counterintuitive fact in the session** — budget the full 5 minutes for it even if something else needs to be cut. It also doubles as spaced retrieval practice on Session 29's 2's-complement content.
- **Have a second pair of fresh numbers ready** beyond `1100`/`1010` for Activity 2 in case a section finishes early or a re-run is needed with a different cohort.
