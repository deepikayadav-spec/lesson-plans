# Session 57b — Asteroid Collision (Part 2 of 2)

**Duration** 27 min · **Topic** Stack & Queue — Asteroid Collision: Classification & Practice · **Prerequisite** Session 57a — Asteroid Collision, Part 1 (rules, stack simulation) · **Session type** Concept lecture

<!-- Split note: continues session-57 (original 50 min) right after the Classroom Quiz. This part is hands-on: the collide/no-collide classification drill (with its key trap case), the pseudocode/complexity/second dry run, and a live multi-step collision-chain trace. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Asteroid Collision | https://docs.google.com/presentation/d/1trHgk2ucVk3foQoA1rsUq-UXjv5dZd2ixi0HQCXhKGc/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Distinguish the three distinct "no collision" cases (same direction, moving apart, one already destroyed) from the two collision-resolution cases (smaller explodes, equal-size both explode). *(ANALYZING)*
2. Execute a multi-step collision chain, including a case where one incoming asteroid destroys more than one stack element in a row. *(APPLYING)*

---

## Warm-Up Poll — Retrieval Practice on Session 57a (0–5 min)

Say: *"Four quick ones on the rules before you classify some trickier cases yourself."*

**Q1.** Two asteroids of equal magnitude, moving toward each other:
`A` The larger survives · `B` Both are destroyed · `C` Neither is affected · `D` They pass through
→ *Read:* B.

**Q2.** In the dry run, what does the stack hold at any given moment?
`A` Every asteroid ever seen · `B` The surviving asteroids so far, bottom to top in order · `C` Only destroyed asteroids · `D` A sorted list
→ *Read:* B.

**Q3.** When a negative asteroid arrives, how many stack elements can it potentially destroy?
`A` Exactly one · `B` Zero or one, never more · `C` As many as are smaller and to its right, in a row · `D` The entire stack, always
→ *Read:* C — this is what Part 2's live trace will test.

**Q4.** In Part 1's Collide/No-Collide sort, which scenario was flagged as the trap?
→ *Read:* Open response — reconnects to "moving apart looks like it should collide but doesn't" before the activity resolves it.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"Time to resolve that trap case for real — and then you run a full collision chain yourself, including the one where a single asteroid takes out two in a row."*

---

## ⚡ Activity 1 — Spot the Bug: "Collide or Not?" (7–13 min)

**Format:** Spot the Bug / Predict-the-Output · **Exposes:** whether students can correctly classify each pairwise interaction into "collide" vs. "no collision," and if colliding, resolve the outcome — the single skill the whole algorithm depends on.

**Setup line (say this):**
> *"Four pairs of asteroids about to meet or not meet. For each: do they collide? If yes, what survives?"*

Put all four on screen at once:

```
1.  Stack top = 6,  incoming = -6
2.  Stack top = -3, incoming = -9
3.  Stack top = 4,  incoming = 9    (incoming is positive)
4.  Stack top = -2, incoming = 8
```

**What students do:** 45 seconds silent, then hands up. Take one pair per student.

**Answers**

| # | Collide? | Outcome |
|---|---|---|
| 1 | Yes | Equal magnitude, opposite directions → both explode |
| 2 | No | Both negative (same direction, moving left) → no collision, both survive, `-9` pushed on top |
| 3 | No | Incoming is positive (moving right) → same direction as everything already on the stack moving right → no collision, `9` just pushed |
| 4 | No | Top is negative (already moving left), incoming is positive (moving right) — they're moving *apart*, not toward each other |

**How it surfaces:** Pair 4 is the trap — students will often assume "opposite signs always means collide," but a `-2` sitting on the stack is already moving *left*, and an `8` arriving after it is moving *right*: they're moving apart, not toward each other. Only a *positive* on the stack (moving right, "waiting") followed by a *negative* incoming (moving left, "approaching") is a real collision setup.

**Debrief line:**
> *"Opposite signs are necessary but not sufficient. The one collision shape that matters is: something on the stack moving right, and something new arriving moving left — anything else is either same-direction or already moving apart."*

**Cut rule:** If running short, do pairs 1 and 4 only — pair 1 is the clean collision case, pair 4 is the trap that catches almost everyone.

---

## Slide Block B2 (13–20 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 62–92: Pseudocode, Complexity Analysis, Code, second dry run example -->
Covers: Pseudocode (while-loop collision resolution against the stack top, per incoming negative) → complexity (O(N) time, O(N) space — each element pushed and popped at most once, plus the final array transfer) → the deck's second full dry run, `[-3, 25, 10, 15, 12, 8, -12, -20]` → `[-3, 25]`.

**Beats to emphasise**

- Point directly at the `while` loop in the pseudocode: an incoming negative asteroid doesn't just check the stack top *once* — it keeps colliding and popping as long as the top is positive and smaller, exactly like a monotonic stack's pop loop.
- Complexity: total pushes and pops across the whole run are bounded by roughly `2N` (each element enters the stack at most once, leaves at most once) — same argument students built for themselves back in Session 53's Activity 2.
- In the second example, walk the chain once quickly: `8` and `-12` collide → `8` explodes. `12` and `-12` collide, equal → both explode. `15` and `-20` collide → `15` explodes. `10` and `-20` collide → `10` explodes. `25` and `-20` collide → `-20` explodes (`25` is bigger). Final: `[-3, 25]`.

**Checkpoint (at 20 min)** — cold-call:
> *"In that second dry run, why does `-3` (the very first element) survive untouched the whole time?"*
> **Answer:** `-3` is moving left with nothing to its left to collide with, and it's never compared against anything after it either — everything to its right that survives ends up moving right or already resolved, so `-3` just sits at the bottom of the stack the entire run.

---

## ⚡ Activity 2 — Live Trace: "Run the Full Chain" (20–25 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can execute a multi-step collision chain themselves, including a case where one incoming asteroid destroys more than one stack element in a row.

**Setup line (say this):**
> *"New array: `[6, 3, -8, 2]`. Walk it with me, one element at a time — tell me what's pushed, what collides, and what survives, before I confirm."*

Run **one element at a time**:

```
6   → stack empty → push.                                  Stack: [6]
3   → 3 moving right, same direction as top → push.         Stack: [6, 3]
-8  → collides with top 3: |3| < |-8| → 3 explodes.
      collides with new top 6: |6| < |-8| → 6 explodes.
      Stack now empty → push -8.                            Stack: [-8]
2   → 2 moving right, top is -8 moving left → moving apart, no collision → push.   Stack: [-8, 2]
```

Final stack: `[-8, 2]`.

**How it surfaces:** At `-8`, ask before revealing each step: *"Does it stop after destroying `3`, or keep going?"* Correct: it keeps going — `-8` is not yet resolved, so it must keep checking the new top (`6`) until either something bigger stops it or the stack empties.

**Debrief line:**
> *"One incoming asteroid destroyed two stack elements in a row, in a single step of the outer loop — that's the `while`, not `if`, doing its job. It only stops early if it meets something bigger than itself, or something moving the same direction."*

**Cut rule:** If running short, do only the `-8` step — it's the one that carries the whole "keep colliding until stopped" lesson; `6`, `3`, and `2` are all simple pushes.

---

## Exit Ticket (25–27 min)

> For `arr = [8, -8]`, what survives? For `arr = [8, -9]`? For `arr = [9, -8]`?
> **Answers:** `[8, -8]` → equal magnitude → both explode → `[]`. `[8, -9]` → `|-9| > |8|` → `8` explodes → `[-9]`. `[9, -8]` → `|9| > |-8|` → `-8` explodes → `[9]`.

**Homework:** trace `arr = [5, -3, -4, 9]` by hand and state the final surviving array. <!-- placement: inferred — no homework/RM/practice units exist for this course per deviation #2 -->

This closes session 57. Next: Largest Rectangle in Histogram — a fourth monotonic-stack problem in a new physical framing.

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Opposite signs always means a collision | Feels like the obvious reading of "moving toward each other" | Activity 1, pair 4 — a negative already on the stack (moving left) followed by a positive arriving (moving right) are moving *apart*, not colliding |
| An incoming asteroid only ever resolves one collision before being pushed | Carried over from underestimating pop loops generally (same trap as Session 53/56) | Activity 2's `-8` step — one incoming element destroys two stack elements in sequence via a `while`, not an `if` |
| The stack at the end needs sorting or filtering to get the final answer | The final transfer-to-array step looks like extra processing | Point out the transfer only reverses order (stack is LIFO, answer needs left-to-right) — no filtering or sorting happens, the stack already holds exactly the survivors |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split right after the Classroom Quiz.**
- **Activity 1's pair 4 is the single most important five minutes of this session.** Almost every student will initially say "opposite signs, must collide" — do not rush past the correction. This misconception, uncorrected, breaks every dry run for the rest of the session.
- **Bridge to Session 58:** mention at the close that Largest Rectangle in Histogram uses a monotonic stack again, in yet another physical framing — the pattern recurring for a fourth time by now should be explicit and reassuring, not a surprise.
