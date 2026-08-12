# Session 29b — Binary Operations (Part 2 of 2)

**Duration** 45 min · **Topic** Bit Manipulation — Arithmetic & Complements · **Prerequisite** Session 29a — Binary Operations, Part 1 (bit fundamentals, conversion) · **Session type** Concept lecture

<!-- Split note: continues session-29 (original 75 min) right after the Classroom Quiz. This part covers binary addition, both subtraction methods (no-borrow/XOR shortcut and borrowing), 1's/2's complement, and 2's-complement subtraction — the densest material in the whole Bit Manipulation topic. Runs the full 45 min; protect it from further compression. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Binary Operations | https://docs.google.com/presentation/d/153LZGni1xef_OfEY2p7qdybI5EgPvjxf5IPRvr8konE/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Perform binary addition and binary subtraction (both the no-borrow/XOR shortcut and the borrowing method) by hand. *(APPLYING)*
2. Compute the 1's complement and 2's complement of a binary number. *(APPLYING)*
3. Use 2's complement addition to perform subtraction and correctly interpret a negative result from its sign bit. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 29a (0–4 min)

Say: *"Four quick ones on conversion before we move to arithmetic."*

**Q1.** LSB stands for:
`A` Largest Significant Bit · `B` Least Significant Bit · `C` Left-Side Bit · `D` Last Stored Bit
→ *Read:* B — rightmost.

**Q2.** When converting decimal to binary by dividing by 2, what must you do to the collected remainders at the end?
`A` Nothing, use them as-is · `B` Reverse them · `C` Sort them · `D` Double them
→ *Read:* B.

**Q3.** In `11001` (binary→decimal), the rightmost bit represents:
`A` 2¹ · `B` 2⁰ · `C` 2⁴ · `D` 2⁵
→ *Read:* B.

**Q4.** What is 37 in binary (from Part 1's relay)?
`A` `100101` · `B` `101001` · `C` `110010` · `D` `100110`
→ *Read:* A.

**Running it** — poll tool, ~30 s/question. Total 4 min including reads.

---

## Bridge (4–5 min)

Say: *"You can move between decimal and binary cleanly. Now: what happens when you do arithmetic in binary directly — and how a computer stores a negative number, which is stranger than a minus sign."*

---

## Slide Block B (5–18 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — grouped as "binary arithmetic", slides 24–54 -->
Covers: Binary Addition (carry propagation) → Binary Subtraction Without Borrow (the bit-difference/XOR shortcut) → Binary Subtraction With Borrow (the borrowing method) → how a computer pads a number to 32 bits with a sign bit.

**Beats to emphasise**

- Run the deck's addition example (`1101 + 1011`) live, column by column, narrating each carry the way the deck does: *"1 + 1 = 2, write 0, carry 1."*
- On subtraction without borrow: point out explicitly that `bitA - bitB` with no borrowing is **the same operation as XOR** on those two bits (1-0=1, 0-0=0, 1-1=0) — the deck's own pseudocode literally computes `bitA XOR bitB`. Say this is only valid when no borrowing is ever needed across the whole subtraction (every top bit ≥ corresponding bottom bit) — this sets up Activity 2.
- The 32-bit padding slides (51–52) are a preview, not a distraction — say explicitly: *"File this away, we need it in about fifteen minutes."*

**Checkpoint (at 18 min)** — show of hands:
> *"`1010 - 0101` — can I use the no-borrow/XOR shortcut here, yes or no?"*
> **Answer:** No — the top bits are smaller than the bottom bits in more than one column (this is exactly the deck's Borrowing Method example), so the shortcut breaks and you need the borrowing method.

---

## ⚡ Activity 2 — Spot the Bug: When Does "Subtraction = XOR" Break? (18–24 min)

**Format:** Spot the Bug · **Exposes:** the belief that the no-borrow/XOR trick from Slide Block B works for *any* binary subtraction, not just the special case where no column ever needs to borrow.

**Setup line (say this):**
> *"I'm going to apply the XOR shortcut to a subtraction it was never meant for, and it's going to hand me a wrong answer with total confidence. Your job: catch where it breaks, not just that it's wrong."*

Put this on screen and apply the without-borrow method to it, exactly as if it were valid:

```
  1010   (10)
- 0111   (7)
```

Bit-by-bit XOR gives `1101` (13) — which is nonsense for `10 - 7 = 3`.

**What students do:** 60 seconds to discuss in pairs: is `1101` right? If not, why did the shortcut fail here but work fine for the deck's own `1001 - 1000` example?

**How to handle wrong answers:** If students say "the arithmetic is just wrong," push them to compare column-by-column against `1001 - 1000` (where it worked) — the difference is that here, more than one column has a top bit smaller than the bottom bit, meaning a borrow is required and XOR has no concept of "borrowing from the next column."

**Debrief line:**
> *"XOR-as-subtraction is a shortcut for one specific shape of problem: every column's top bit is already at least as big as the bottom bit, so nothing ever needs to borrow. The moment even one column needs a borrow, XOR gives you a bit pattern, not an answer. That's exactly why the deck has a second method — the Borrowing Method — for the general case."*

**Cut rule:** If running late, skip the pair-discussion and just run the broken example live, then state the debrief line directly — the core catch survives without the discussion step.

---

## Slide Block C (24–35 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — grouped as "complements", slides 55–83 -->
Covers: 1's Complement (invert every bit) → 2's Complement (invert, then add 1) → Binary Subtraction Using 2's Complement (convert to 2's complement of the number being subtracted, add, then interpret the sign bit of the result).

**Beats to emphasise**

- Drill the two-step recipe for 2's complement as a chant: *"Flip every bit. Add one."* Nothing more.
- On the 2's-complement subtraction algorithm, slow down hard on **step 4 — interpreting the result**: if the MSB of the result is 1, the true answer is negative, and you must take the 2's complement of *that result* to find its magnitude. This double-take-the-complement step is where almost everyone drops a step.
- Connect back to Part 1's Hook and the 32-bit padding slides from Slide Block B: this is the actual mechanism — computers represent negative numbers using 2's complement, with the sign bit as the MSB.

**Checkpoint (at 35 min)** — cold-call:
> *"I hand you a 4-bit subtraction result of `1110` from a 2's-complement subtraction. Is the true answer positive or negative, and how do you find its size?"*
> **Answer:** MSB is 1, so negative. Take the 2's complement of `1110` (invert → `0001`, add 1 → `0010` = 2) to get the magnitude: the true answer is **-2**. (This is the deck's own Example 1.)

---

## ⚡ Activity 3 — Predict-the-Output: 2's Complement Subtraction (35–41 min)

**Format:** Predict-the-Output · **Exposes:** stopping at the raw XOR/addition result instead of running the sign-bit interpretation step, and forgetting that a 1 in the MSB means "go take the complement again."

**Setup line (say this):**
> *"4-bit numbers, new pair: subtract 6 from 2 using 2's complement — `0010 - 0110`. Before I add anything, commit out loud: is this going to come out positive or negative, and why do you already know that before we've done a single operation?"*

**What students do:** Someone should reason "2 < 6, so the true answer is negative" from plain arithmetic *before* touching binary. Then walk the four steps as a class: convert both to 4-bit binary, find the 2's complement of 6 (`0110` → invert `1001` → +1 → `1010`), add to `0010` (`0010 + 1010 = 1100`), interpret (MSB = 1 → negative → complement of `1100` is `0100` = 4 → answer is **-4**).

**How to handle wrong answers:** If a group reports the raw sum `1100` as the final answer, that's the exact bug this activity is built to catch — send them back to the checkpoint's chant: MSB is 1, so take the complement of the *result*, don't report the raw sum.

**Debrief line:**
> *"Every 2's-complement subtraction ends with a question: is the sign bit 1? If yes, you are not done — you owe the class one more complement operation before you can say what the number actually is."*

**Cut rule:** If very tight on time, drop this activity entirely — Slide Block C's checkpoint already forces the same reasoning once, cold-call style, which covers the highest-risk gap at lower time cost.

---

## Exit Ticket (41–45 min)

> On paper before anyone leaves: Convert **18** to binary using the division-by-2 method. Then write its 1's complement and its 2's complement.
> **Answers:** 18 = `10010`. 1's complement = `01101`. 2's complement = `01101 + 1` = `01110`.

Scan on the way out. A wrong 1's complement (forgetting to invert every bit, including leading zeros to a fixed width) is the signal to open Session 30 with a 2-minute recap of the complement chant.

**Homework:** re-attempt today's dry runs (decimal↔binary conversion, both subtraction methods, both complements) from memory, no notes. <!-- placement: inferred — no homework/practice-unit table exists for this course; this is a natural close, not a platform assignment -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Binary subtraction "without borrow" (the XOR trick) works for any two binary numbers | It worked cleanly on the deck's first example (`1001 - 1000`), so it looks general-purpose | Activity 2 — break it deliberately on a case that needs borrowing |
| MSB means "the biggest bit," so a leading 1 always means a big positive number | Outside of signed representations, more significant digit = bigger, no exceptions | Slide Block C — 32-bit padding slides, then the sign-bit checkpoint |
| 2's complement of a number is just "put a minus sign on it" | The chant ("flip bits, add one") feels like a formality once you know the answer should be negative | Making them actually invert and add 1 in Activity 3 before revealing the answer |
| A 2's-complement subtraction is done once you've added the two numbers | The addition step feels like the "answer," and the sign-bit interpretation step is easy to forget | Checkpoint after Slide Block C, then Activity 3's debrief chant |

---

## Instructor Notes

- **This is Part 2 of a 75-minute original session, split right after the Classroom Quiz. This part runs the full 45 minutes — do not compress it further; it carries the session's hardest content.**
- **Pacing risk:** Slide Block C (complements) is the densest 11 minutes in the session — two complement types plus a 4-step subtraction algorithm plus sign-bit interpretation. If you're behind schedule entering this block, cut Activity 3 per its cut rule rather than rushing the block itself; the complement chant needs to land cleanly or the exit ticket will fail wholesale.
- **Reuse fresh numbers, not the deck's own.** The deck reuses 5, 3, 6, 9, 10 across almost every sub-topic. Every activity above deliberately uses numbers the deck never shows (18, the `1010−0111` break case) — keep doing this in the checkpoints too if you improvise more examples.
- **Have the "flip bits, add one" chant on the board early** in Slide Block C and leave it up — it is the single highest-leverage phrase in the whole session.
