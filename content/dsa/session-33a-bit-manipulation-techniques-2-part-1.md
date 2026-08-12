# Session 33a — Bit Manipulation Techniques 2 (Part 1 of 2)

**Duration** 32 min · **Topic** Bit Manipulation — XOR Swap · **Prerequisite** Session 32 (Bit Manipulation Techniques 1) · **Session type** Concept lecture

<!-- Split note: original session-33 ran 65 min across four techniques. Split right after the Classroom Quiz. Part 1 covers the XOR swap trick end to end. Part 2 (session-33b) covers the shared `N & (N-1)` formula in its three disguises: removing the rightmost set bit, the power-of-2 check, and counting set bits (including Brian Kernighan's trick). -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Bit Manipulation Techniques 2 | https://docs.google.com/presentation/d/1y-24MHseXfRzFL0upADHstJHa8pxXdyQtnlx0t8KLU0/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Swap two numbers without a temporary variable using three XOR operations, and explain why it works using `a ^ a = 0` and `a ^ 0 = a`. *(APPLYING / ANALYZING)*

*(The `N & (N-1)` formula and its three applications are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 32 (0–6 min)

> Retrieval practice on **Bit Manipulation Techniques 1**. Solo answers, no discussion yet.

**Q1.** Formula to check if bit `i` of `N` is set?
`A` `N | (1 << i)` · `B` `N & (1 << i)` · `C` `N ^ (1 << i)` · `D` `N & ~(1 << i)`
→ *Read:* Answer B.

**Q2.** Formula to set bit `i` of `N`?
`A` `N & (1 << i)` · `B` `N | (1 << i)` · `C` `N ^ (1 << i)` · `D` `~N`
→ *Read:* Answer B.

**Q3.** Formula to clear bit `i` of `N`?
`A` `N ^ (1 << i)` · `B` `N | (1 << i)` · `C` `N & ~(1 << i)` · `D` `N & (1 << i)`
→ *Read:* Answer C.

**Q4.** True or false: the check-bit formula always returns exactly `1` when the bit is set.
`A` True · `B` False — it returns `2^i`, which is non-zero but not necessarily 1
→ *Read:* Answer B.

**Q5.** What happens if you toggle the same bit twice in a row?
`A` It ends up cleared regardless of its starting value · `B` It returns to its original value · `C` It's undefined behavior · `D` It sets the adjacent bit
→ *Read:* Answer B — `x ^ x = 0`, so the second toggle cancels the first.

**Q6.** *(MSQ — pick 2)* Which are true of `N & ~1 << i` (parentheses removed) versus `N & ~(1 << i)` (as taught)?
`A` They are always identical · `B` `~` binds tighter than `<<`, so they can evaluate differently · `C` The un-parenthesized version can silently compute the wrong mask · `D` Parentheses are purely stylistic here
→ *Read:* B and C.

**Running it** — poll tool, ~40 s per question. Total 6 min.

---

## Hook (6–9 min)

Say: *"Classic interview puzzle. Swap the values of two variables, `a` and `b`, without using a third variable anywhere. Thirty seconds, shout your approach."*

Let a few attempts land — some will try arithmetic (`a = a+b; b = a-b; a = a-b`), which works but risks overflow. Say: *"There's a bitwise version of this that never risks overflow, and it's built entirely out of one property you already know: XOR-ing something with itself gives zero. That's today's whole focus — Part 2 hands you three more techniques that all reuse a single formula, `N & (N-1)`, in three different disguises."*

---

## Slide Block A (9–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — slides 4-10, 44-59: swap two numbers via XOR, contrasted with the third-variable swap -->
Covers: Swap Two Numbers using XOR (`a = a^b; b = a^b; a = a^b`) → worked example (`a=5, b=10` → swapped to `a=10, b=5`) → contrast against the traditional third-variable (`temp`) swap, shown step by step.

**Beats to emphasise**

- Derive the three lines live using the identities from Sessions 29/31, don't just state them: after `a = a^b`, `a` holds `a^b`. Then `b = a^b = (a^b)^b = a^(b^b) = a^0 = a` (original a!) — so `b` now holds the original `a`. Then `a = a^b = (a^b)^a = b^(a^a) = b^0 = b` (original b!) — so `a` now holds the original `b`.
- Show the third-variable version immediately after, side by side, so students see both are valid — the XOR version is the "no extra memory" flex, not a strictly superior replacement.
- Flag the real-world caveat explicitly (this is not on the deck, but is the standard danger of this idiom): *"If `a` and `b` ever refer to the exact same memory location, this trick zeroes the value out instead of swapping it — a genuine bug people hit in practice."*

**Checkpoint (at 19 min)** — cold-call:
> *"Why does `b = a ^ b` (the second line) end up holding the original value of `a`?"*
> **Answer:** At that point `a` already holds `a^b` and `b` still holds the original `b`. So `a ^ b = (a^b) ^ b = a ^ (b^b) = a ^ 0 = a` — the original `a`.

---

## ⚡ Activity 1 — Live Coding / Dry-Run Relay: Swap 12 and 7 (19–24 min)

**Format:** Dry-Run Relay · **Exposes:** treating the XOR-swap lines as a memorized incantation rather than tracking what each variable actually holds at each step.

**Setup line (say this):**
> *"New numbers, not from the slides — `a = 12`, `b = 7`. Row by row, you tell me what each line computes and what `a` and `b` hold after it runs. I only write what you say."*

**What students do:** Relay through the three lines: `a = 12^7 = 11` (binary `1100^0111=1011`); `b = a^b = 11^7 = 12` (original `a`!); `a = a^b = 11^12 = 7` (original `b`!). Final: `a=7, b=12`.

**How to handle wrong answers:** If a student re-substitutes the *original* value of `a` or `b` instead of the *current* value after each line, stop and rewrite that line's inputs explicitly — the whole trick depends on using each variable's live value, not its starting value.

**Debrief line:**
> *"Every bug in this idiom comes from forgetting that `a` and `b` change after every line. Track current values, not original ones, and the three lines just fall out of the XOR identities you already know."*

**Cut rule:** If running short, skip the full relay and do only the first and third lines out loud, taking the middle line as given — the third line is where most tracking errors surface anyway.

---

## Classroom Quiz (24–29 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Peer Teach-Back (29–32 min)

**Why this strategy here:** the XOR swap is a genuine "aha" trick, and the surest sign it's landed (not just been watched) is a student explaining the three-line derivation to someone else, cold, without the board.

**Run it (3 minutes):**
> *"Turn to your partner. Derive the swap out loud from scratch — no notes — using `a^a=0` and `a^0=a`. Partner checks each line against those two identities before you move to the next."*

Cold-call one pair to report where their partner got stuck, if anywhere.

> *"That's one formula, three techniques left, all built on `N & (N-1)`. Part 2 shows you the same formula wearing three different hats."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The XOR-swap trick works safely in every situation | The three-line derivation looks clean and general | Naming the same-variable edge case explicitly in Slide Block A (swapping a variable with itself zeroes it out) |

---

## Instructor Notes

- **This is Part 1 of a 65-minute original session, split right after the Classroom Quiz.**
- **The deck itself is almost entirely repeated dry-run animation slides** (119 total, but only 4 distinct techniques across both parts) — do not attempt to "deliver every slide" at face value; deliver the technique, the formula, one worked example, and move on.
- **Have `N = 12` and the swap example worked out on scratch paper before class starts** — you'll want to move through the bit patterns without hesitation live.
