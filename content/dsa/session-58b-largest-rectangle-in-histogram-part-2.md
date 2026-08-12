# Session 58b — Largest Rectangle in Histogram (Part 2 of 2)

**Duration** 30 min · **Topic** Stack & Queue — Largest Rectangle: Optimal One-Pass Approach · **Prerequisite** Session 58a — Largest Rectangle in Histogram, Part 1 (problem, NSE/PSE two-pass approach) · **Session type** Concept lecture

<!-- Split note: continues session-58 (original 55 min) right after the Classroom Quiz. This part covers the optimal one-pass approach (compute area at the moment of pop, no separate NSE/PSE arrays), with two full hands-on live-trace activities. This closes the block's fourth and final monotonic-stack problem. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Largest Rectangle in Histogram | https://docs.google.com/presentation/d/1_OHNtNxlKJdYOX6LT_zqx1NwQnuQF8T6onInuzNhN2I/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Trace the optimal one-pass approach, where a single stack replaces the two separate NSE/PSE passes, and explain why the result is identical. *(ANALYZING)*
2. Independently compute NSE and the one-pass area calculation on a fresh array, without instructor narration. *(APPLYING)*

---

## Warm-Up Poll — Retrieval Practice on Session 58a (0–5 min)

Say: *"Four quick ones on the two-pass approach before we cut it down to one pass."*

**Q1.** Width for bar `i` is computed as:
`A` `NSE[i] + PSE[i]` · `B` `NSE[i] - PSE[i] - 1` · `C` `NSE[i] - PSE[i]` · `D` `PSE[i] - NSE[i]`
→ *Read:* B.

**Q2.** NSE is naturally computed scanning:
`A` Left to right · `B` Right to left · `C` Either direction, doesn't matter · `D` From the middle out
→ *Read:* B — it looks forward from each bar.

**Q3.** When a bar's PSE doesn't exist (nothing smaller to its left), what does that mean for its rectangle?
`A` It has zero width · `B` The rectangle can extend all the way to the start of the array · `C` It's invalid · `D` It defaults to width 1
→ *Read:* B.

**Q4.** In Part 1's Whiteboard Race, what reflex were you drilling?
→ *Read:* Open response — reconnects to "pop while ≥, next top is the answer" before it gets reused in the one-pass version.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"You compute both boundaries, then all the areas. Watch what happens when you compute each bar's area the instant you learn its right boundary — no second array, one pass."*

---

## ⚡ Activity 1 — Live Trace: "Compute NSE Yourself" (7–13 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can build an NSE stack pass themselves on a fresh, smaller array — the exact mechanical skill the optimal one-pass approach folds into its main loop.

**Setup line (say this):**
> *"New array: `[3, 1, 4, 2]`. I want NSE for every index, scanning right to left. Call out what gets popped and what the answer is, before I confirm."*

Run **right to left, one index at a time** (indices 3, 2, 1, 0; values `2, 4, 1, 3`):

```
i=3 (val=2) → stack empty → NSE[3] = 4 (past end) → push 3.        Stack: [3]
i=2 (val=4) → top (idx 3, val 2) < 4 → no pop → NSE[2] = 3 → push 2.   Stack: [3, 2]
i=1 (val=1) → top (idx 2, val 4) ≥ 1 → pop.
              top (idx 3, val 2) ≥ 1 → pop.
              stack empty → NSE[1] = 4 (past end) → push 1.         Stack: [1]
i=0 (val=3) → top (idx 1, val 1) < 3 → no pop → NSE[0] = 1 → push 0.   Stack: [1, 0]
```

Final NSE: `[1, 4, 3, 4]`.

**How it surfaces:** At `i=1` (value `1`), ask before revealing: *"How many pops happen, and why?"* Correct: two pops — both `4` and `2` are `≥ 1`, so both get thrown away before landing on an empty stack.

**Debrief line:**
> *"Same discipline as Next Greater Element two sessions ago — the stack only ever holds bars that could still matter, and anything that can't possibly be someone's answer anymore gets popped immediately."*

**Cut rule:** If running short, do just `i=1` — it's the only step with more than one pop, and it's the step that proves the mechanism.

---

## Slide Block B2 (13–21 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 69–100: Optimal Approach (single stack, one pass), Dry Run on arr = [2, 3, 8, 10, 6, 7, 5], Pseudocode, Complexity, Code -->
Covers: Optimal Approach — one stack, one left-to-right pass. When a bar shorter than the stack's top arrives, pop the top and *immediately* compute its area (using the just-arrived index as its right boundary and the new stack top as its left boundary), instead of precomputing NSE and PSE as separate arrays first.

**Beats to emphasise**

- State the conceptual leap plainly: "The two-pass approach computes *both* boundaries for every bar before calculating any area. The optimal approach computes each bar's area the *moment* its right boundary becomes known — during the same single pass that's still running."
- Walk the deck's dry run at the key moment: at `i=4` (value `6`), the stack holds indices for `10` and `8`, both `≥ 6` — pop `10` first (right boundary = current index `4`, left boundary = new stack top), compute its area immediately, then pop `8` the same way, then push `6`.
- At the end of the array, anything still on the stack has **no bar to its right that's ever shorter** — their right boundary is simply the end of the array (`n`), handled in one final cleanup loop.

**Checkpoint (at 21 min)** — cold-call:
> *"In the optimal approach, when exactly does a bar's area get computed — at the start, at the end, or somewhere in between?"*
> **Answer:** The moment it gets popped — which happens exactly when a shorter bar arrives to its right, giving it its right boundary right then and there.

---

## ⚡ Activity 2 — Live Trace: "One Pass, Compute as You Go" (21–27 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can run the optimal one-pass approach themselves, computing an area at the exact moment of a pop rather than deferring it — the core difference from Activity 1's NSE-only trace.

**Setup line (say this):**
> *"Same array as Activity 1: `[3, 1, 4, 2]`. One pass, left to right. Every time something gets popped, tell me its area before I confirm — height × (current index − new top index − 1), or height × current index if the stack goes empty."*

Run **left to right, one index at a time**:

```
i=0 (val=3) → stack empty → push.                                    Stack: [0]
i=1 (val=1) → top (idx 0, val 3) ≥ 1 → pop.
              stack empty → area = 3 × 1 = 3 (width = current index 1)
              → push 1.                                              Stack: [1]
i=2 (val=4) → top (idx 1, val 1) < 4 → no pop → push.                 Stack: [1, 2]
i=3 (val=2) → top (idx 2, val 4) ≥ 2 → pop.
              new top (idx 1, val 1) < 2 → area = 4 × (3 − 1 − 1) = 4
              → push 3.                                              Stack: [1, 3]
End of array → remaining: pop idx 3 (val 2): new top idx 1 → area = 2 × (4 − 1 − 1) = 4
              pop idx 1 (val 1): stack empty → area = 1 × 4 = 4
```

Maximum area across all pops: `4`.

**How it surfaces:** At `i=1`, ask before revealing: *"The stack goes empty after this pop — what's the width?"* Correct: when the stack empties, there's no left boundary at all, so the width is simply the current index itself (everything from the start of the array up to here).

**Debrief line:**
> *"Every bar gets its area computed exactly once, the instant its right boundary is known — no separate NSE and PSE arrays needed. Same answer as Part 1's two-pass method, one pass instead of two."*

**Cut rule:** If running short, do only `i=1` and the end-of-array cleanup — together they cover both the "normal pop" case and the "stack goes empty" edge case.

---

## Exit Ticket (27–30 min)

> In one sentence: what does the optimal one-pass approach do differently from the NSE/PSE approach, given that both produce the same final answer?
> **Answer:** The NSE/PSE approach computes both boundaries for every bar first, in two separate passes, then calculates all areas afterward; the one-pass approach calculates each bar's area immediately when it's popped, using whatever boundary information is available at that exact moment — one pass, not two.

**Homework:** compute the largest rectangle for `[6, 2, 5, 4, 5, 1, 6]` using either approach, by hand. <!-- placement: inferred — no homework/RM/practice units exist for this course per deviation #2 -->

**This is the fourth and final monotonic-stack problem in this block** (after Monotonic Stack itself, Next Greater Element, and Asteroid Collision). Close with an explicit one-line recap tying all four together: "one invariant — pop while the top violates your order — four completely different-looking problems."

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| In the one-pass approach, area is computed once at the very end, for every bar at once | The two-pass method primed this expectation | Activity 2 — each area appears mid-pass, exactly at the pop that reveals a bar's right boundary |
| When the stack empties during a pop, the width is `0` or undefined | No left boundary feels like a broken case rather than a simple one | Activity 2, `i=1` — width is just the current index itself; "no smaller bar to the left" simply means the rectangle reaches all the way to the start |
| The end-of-array cleanup loop is a separate algorithm bolted on | It looks structurally different from the main loop | Frame it as the exact same pop-and-compute logic, just using `n` (the array length) as the right boundary instead of a real index, since nothing shorter ever showed up |

---

## Instructor Notes

- **This is Part 2 of a 55-minute original session, split right after the Classroom Quiz.**
- **Pacing risk:** if behind, compress Activity 1 to its cut rule (the single `i=1` step) rather than cutting Slide Block B2's dry run — the one-pass mechanism has to land solidly before the exit ticket makes sense.
