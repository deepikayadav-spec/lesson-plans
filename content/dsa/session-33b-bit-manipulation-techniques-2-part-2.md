# Session 33b — Bit Manipulation Techniques 2 (Part 2 of 2)

**Duration** 43 min · **Topic** Bit Manipulation — N & (N-1) in Three Disguises · **Prerequisite** Session 33a — Bit Manipulation Techniques 2, Part 1 (XOR swap) · **Session type** Concept lecture

<!-- Split note: continues session-33 (original 65 min) right after the Classroom Quiz. This part covers the shared `N & (N-1)` formula wearing three hats: removing the rightmost set bit, the power-of-2 check, and counting set bits (check-and-shift vs. Brian Kernighan's trick). -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Bit Manipulation Techniques 2 | https://docs.google.com/presentation/d/1y-24MHseXfRzFL0upADHstJHa8pxXdyQtnlx0t8KLU0/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State and apply the formula to remove a number's rightmost set bit: `N & (N - 1)`. *(APPLYING)*
2. Determine whether a number is a power of 2 using `N & (N - 1) == 0` (with `N > 0`), and explain why exactly-one-set-bit is the defining property of powers of 2. *(ANALYZING)*
3. Count the set bits in an integer using two approaches — check-and-shift bit by bit (O(log₂ N)) and Brian Kernighan's repeated `N & (N-1)` (O(number of set bits)). *(APPLYING)*
4. Compare the two set-bit-counting approaches and state when Kernighan's approach is actually faster (and when it isn't). *(ANALYZING)*

<!-- placement: inferred from the Key Takeaways slide (38), which lists these four techniques as the session's summary. -->

---

## Warm-Up Poll — Retrieval Practice on Session 33a (0–5 min)

Say: *"Four quick ones on the XOR swap before we move to a formula that reappears three times today."*

**Q1.** The XOR swap's three lines rely on which two identities?
`A` `a+a=2a` and `a-a=0` · `B` `a^a=0` and `a^0=a` · `C` `a|a=a` and `a&a=a` · `D` `a<<1=2a` and `a>>1=a/2`
→ *Read:* B.

**Q2.** What breaks the XOR swap idiom in practice?
`A` Negative numbers · `B` Swapping a variable with itself (same memory location) — it zeroes out · `C` Numbers larger than 100 · `D` Nothing breaks it
→ *Read:* B.

**Q3.** After `a = a^b` (line 1) and `b = a^b` (line 2), what does `b` now hold?
`A` The original `b` · `B` The original `a` · `C` Zero · `D` `a^b^a^b`
→ *Read:* B.

**Q4.** For `a=12, b=7`, what is `a^b` (line 1's result)?
`A` `19` · `B` `11` · `C` `5` · `D` `84`
→ *Read:* B — `1100 ^ 0111 = 1011 = 11`.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"New formula, three jobs. `N & (N-1)` removes exactly one bit. What you do with that removal — once, as a test, or in a loop — is the entire rest of today."*

---

## Slide Block B (7–17 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — slides 11-24, 60-82: remove the rightmost set bit, and check if a number is a power of 2 -->
Covers: Remove the Rightmost Set Bit (`N & (N-1)`) → worked examples (`12 → 8`, `21 → 20`, `72 → 64`) → Check if a Number is a Power of 2 (verify `N > 0`, then `N & (N-1) == 0`) → worked examples (`16` → true, `10` → false, `5` → false).

**Beats to emphasise**

- Derive `N & (N-1)` concretely: subtracting 1 from `N` flips the rightmost set bit to 0 and every bit *after* it (to its right) to 1. ANDing with the original `N` then cancels that rightmost set bit while leaving everything to its left untouched. Walk this on `12 = 1100` → `11 = 1011` → AND gives `1000 = 8`.
- The power-of-2 check is a direct *application* of the same formula: a power of 2 has **exactly one set bit** — so removing its (only) rightmost set bit must leave zero. Any number with more than one set bit will have something left over.
- Flag the `N > 0` guard explicitly: `0 & (0-1)` also evaluates to 0 in most languages' bit representations, but 0 is **not** a power of 2 — the guard exists specifically to rule this edge case out.

**Checkpoint (at 17 min)** — show of hands:
> *"Is `18` a power of 2? Walk the formula, don't just guess."*
> **Answer:** `18 = 10010`, `17 = 10001`. `10010 & 10001 = 10000 ≠ 0` → not a power of 2 (correctly — 18 isn't).

---

## ⚡ Activity 2 — Predict-the-Output: Power-of-2 Check Under Time Pressure (17–22 min)

**Format:** Predict-the-Output · **Exposes:** forgetting the `N > 0` guard, and applying the formula without actually checking the bit pattern (guessing from familiarity with small powers of 2 instead).

**Setup line (say this):**
> *"Four numbers, one formula, no calculators: `32`, `24`, `1`, `0`. For each, is it a power of 2? You must justify with the `N & (N-1)` result, not just 'I know 32 is a power of 2.'"*

**What students do:** `32 = 100000`, `31 = 011111`, AND = `0` → power of 2. `24 = 11000`, `23 = 10111`, AND = `10000 ≠ 0` → not a power of 2. `1 = 1`, `0 = 0`, AND = `0` → power of 2 (`2^0 = 1`, correctly). `0`: the guard `N > 0` fails immediately, so it's **not** a power of 2 by definition, regardless of what `0 & (-1)` would compute to.

**How to handle wrong answers:** If someone says `0` is a power of 2 "because the formula gives 0," that's exactly the edge case this activity targets — walk back to the checkpoint's `N > 0` guard and ask what property of 0 (no set bits at all, not exactly one) makes it fail the actual definition.

**Debrief line:**
> *"'Exactly one set bit' is stricter than 'the formula returns zero.' Zero has *no* set bits, so it accidentally satisfies the arithmetic without satisfying the definition — that's precisely why the algorithm's very first step is a plain `N > 0` check, before any bit trick runs at all."*

**Cut rule:** If short on time, drop `1` from the list (it's the least error-prone case) and keep `32`, `24`, and `0` — the `0` edge case is the load-bearing part of this activity.

---

## Slide Block C (22–32 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — slides 21-38, 79-120: counting set bits, two approaches -->
Covers: Count Set Bits — Approach 1 (loop, check `N & 1`, right-shift, repeat until N is 0 — O(log₂ N) time) → Approach 2 (Brian Kernighan's trick: repeatedly apply `N = N & (N-1)` and count iterations until N is 0 — O(number of set bits) time) → both traced on `N = 13` (binary `1101`, 3 set bits).

**Beats to emphasise**

- Approach 1 runs once **per bit position** in N, whether that bit is 0 or 1 — that's why it's O(log₂ N) (proportional to the total number of bits, i.e. the size of N, not how many are actually set).
- Approach 2 runs once **per set bit**, because each `N & (N-1)` application removes exactly one set bit and nothing else — that's the same removal mechanic from Slide Block B, just looped until N hits 0.
- The direct payoff: for a **sparse** number (few 1s, e.g. `10000000`), Approach 2 finishes in 1 iteration where Approach 1 needs 8. For a **dense** number (all 1s, e.g. `11111111`), the two approaches do the *same* number of iterations — there's no free lunch when every bit is set.

**Checkpoint (at 32 min)** — cold-call:
> *"For `N = 8` (binary `1000`, one set bit), how many loop iterations does Approach 1 need? How many does Approach 2 need?"*
> **Answer:** Approach 1: 4 iterations (it walks all 4 bit positions before N becomes 0). Approach 2: 1 iteration (`1000 & 0111 = 0000` immediately).

---

## ⚡ Activity 3 — Spot the Bug: "Kernighan's Trick Is Always Faster" (32–37 min)

**Format:** Spot the Bug · **Exposes:** the over-generalization that `N & (N-1)` counting is unconditionally faster than the check-and-shift approach, when in fact its advantage depends entirely on how many bits are actually set.

**Setup line (say this):**
> *"A student tells you: 'Always use the `N & (N-1)` approach for counting set bits — it's strictly faster than checking every bit.' Is that a true statement? Test it on `N = 255` (binary `11111111`, all 8 bits set) before you answer."*

**What students do:** Trace both approaches for `N = 255`. Approach 1: 8 iterations (one per bit position, all the way down). Approach 2: also 8 iterations — every single `N & (N-1)` step removes exactly one set bit, and there are 8 of them to remove. Neither approach is faster here.

**How to handle wrong answers:** If a group insists Kernighan's approach "must" still be faster because it's the more advanced technique, have them count the actual loop iterations for both, side by side, rather than reasoning from the technique's reputation.

**Debrief line:**
> *"Kernighan's trick is O(number of set bits), not O(1) and not unconditionally faster than O(log₂ N). Its real advantage only shows up for sparse numbers — few 1s scattered in a wide number. For a dense number like `255`, the two approaches tie exactly. 'Advanced-sounding' and 'always faster' are not the same claim — check the actual bit pattern before you pick an approach."*

**Cut rule:** If very tight on time, skip the group trace and present `N = 255` as a worked example directly, stating both iteration counts — the core "no free lunch on dense numbers" lesson survives.

---

## Exit Ticket (37–43 min)

> On paper before anyone leaves: For `N = 40` (binary `101000`), (a) what does `N & (N-1)` give you, and what did it remove? (b) Is 40 a power of 2? (c) How many set bits does 40 have, and which approach would reach the answer in fewer iterations?
> **Answers:** (a) `40 = 101000`, `39 = 100111`, AND = `100000 = 32` — removed the rightmost set bit (the `8`'s place). (b) No — `N & (N-1) = 32 ≠ 0`, so more than one set bit remains. (c) 2 set bits (`101000`); Kernighan's approach reaches the answer in 2 iterations versus Approach 1's 6 (one per bit position up to bit 5) — Kernighan's is faster here because the number is sparse.

Scan responses on the way out. If most students still pick Approach 1 as "faster" for part (c) without checking the actual bit count, Activity 3's lesson needs a 2-minute recap at the start of Session 34.

**Homework:** re-derive `N & (N-1)`'s effect from scratch for a number of your own choosing, and use it to confirm whether that number is a power of 2. <!-- placement: inferred — no homework/practice-unit table exists for this course; this is a natural close, not a platform assignment -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `N & (N-1)` removes the "leftmost" or "most significant" set bit | "Rightmost" and "leftmost" get swapped easily when reading bit diagrams left to right on screen | Tracing the mechanic explicitly: subtracting 1 only ever affects the rightmost set bit and the bits after it |
| `0` counts as a power of 2 because `0 & (0-1) == 0` | The arithmetic "passes" the core formula without the `N > 0` guard being visible in memory | Activity 2 — walking the `N > 0` guard as the actual first step of the algorithm, separate from the AND check |
| Brian Kernighan's `N & (N-1)` bit-counting approach is always faster than the check-and-shift approach | It's presented as the "optimized" version, and optimized things are assumed to always win | Activity 3 — tracing both approaches on `N = 255` (all bits set) and finding identical iteration counts |
| "Number of set bits" (Hamming weight) is the same thing as the number's value | Both are just "a number associated with N," and it's easy to conflate the two without a clear worked contrast | Slide Block C's own Hamming-weight framing — explicitly counting *how many* bits are 1, not *what* the bits represent as a value |

---

## Instructor Notes

- **This is Part 2 of a 65-minute original session, split right after the Classroom Quiz.**
- **This session's three remaining techniques share one formula (`N & (N-1)`) wearing three different hats** (remove rightmost bit → power-of-2 check → Kernighan's counting) — say this explicitly early in Slide Block B, it's the single biggest pacing and retention win available in this part.
- **Activity 3 (dense vs. sparse numbers) is the highest-value catch in the session** — it's the only place students are forced to check a claim about performance against an actual trace, rather than trusting which technique "sounds" more advanced. Protect this over Activity 2 if time is short.
- **Have `N = 40` and `N = 255` worked out on scratch paper before class starts** — these are the numbers used in the activities and exit ticket.
