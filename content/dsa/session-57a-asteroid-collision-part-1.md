# Session 57a — Asteroid Collision (Part 1 of 2)

**Duration** 33 min · **Topic** Stack & Queue — Asteroid Collision: Rules & the Stack Simulation · **Prerequisite** Session 56 — Next Greater Element · **Session type** Concept lecture

<!-- Split note: original session-57 ran 50 min. Split right after the Classroom Quiz. Part 1 covers the collision rules, the two worked examples, and the full stack-based dry run. Part 2 (session-57b) is entirely hands-on — the "collide or not" classification drill and a live multi-step collision-chain trace. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Asteroid Collision | https://docs.google.com/presentation/d/1trHgk2ucVk3foQoA1rsUq-UXjv5dZd2ixi0HQCXhKGc/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the collision rules: smaller asteroid destroyed, equal-size asteroids both destroyed, same-direction asteroids never collide. *(REMEMBERING)*
2. Explain why a stack models this problem naturally — the most recently surviving asteroid is exactly what a new left-moving asteroid must be compared against first. *(UNDERSTANDING)*
3. Trace the stack-based simulation on a given array, correctly handling multi-step collision chains. *(APPLYING)*

*(The classification drill distinguishing collision vs. no-collision cases, and a second live trace, are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 56 (Next Greater Element) (0–6 min)

Say: *"Eight quick ones on Next Greater Element before asteroids start colliding."*

**Q1.** The Next Greater Element for a position is:
`A` The largest element anywhere in the array · `B` The closest larger element to its right · `C` The closest larger element to its left · `D` The average of all elements to its right

**Q2.** The brute-force approach to NGE runs in:
`A` O(n) · `B` O(n log n) · `C` O(n²) · `D` O(1)

**Q3.** The optimal approach scans the array:
`A` Left to right · `B` Right to left · `C` From the middle outward · `D` In sorted order

**Q4.** The optimal approach's monotonic stack is:
`A` Monotonically increasing · `B` Monotonically decreasing · `C` Sorted every step · `D` Not monotonic at all
→ *Read:* B. If this misses, restate the pairing rule in one line — today's stack-based simulation also relies on knowing exactly what's sitting on top of the stack at all times.

**Q5.** In the optimal approach, when does an element get popped from the stack?
`A` Never · `B` When it's smaller-or-equal to the incoming element · `C` When it's larger than the incoming element · `D` Every single step, regardless

**Q6.** For a strictly decreasing array like `[9, 7, 5, 3]`, what's the NGE for every position?
`A` All `-1` · `B` All equal to the next element · `C` All equal to `9` · `D` Undefined

**Q7 (MSQ — pick all correct).** Which are true of both the brute-force and optimal NGE approaches?
`A` They produce identical output on the same input · `B` They both use a stack · `C` The last element's answer is always `-1` · `D` They both run in O(n²)

**Q8.** The optimal approach achieves O(n) because:
`A` It skips some elements entirely · `B` Each element is pushed and popped at most once · `C` It uses recursion · `D` It sorts the array first

**Running it** — poll tool, ~25 s per question. Total 6 min including reads.

---

## Hook (6–9 min)

Write this on the board: `[5, 10, -10, -5]` (positive = moving right, negative = moving left).

Ask: *"Picture these as literally asteroids in a straight line in space, each moving at the same speed in the direction its sign shows. Which two are ever going to meet?"*

Let students reason: `10` (moving right) and `-10` (moving left) are heading toward each other. Then:

> *"When they meet, one of two things happens: the bigger one survives and the smaller one is destroyed, or if they're exactly equal, both are destroyed. Same-direction asteroids never catch each other — they're moving at identical speed. Today we simulate an entire line of these collisions, and it turns out a stack is exactly the right tool, for a very physical reason: the only asteroid a new left-mover can possibly hit is whichever one most recently survived and is still in front of it."*

---

## Slide Block A (9–17 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 4–29: What is an Asteroid, Problem Statement, Examples 1 & 2 (full collision walkthroughs) -->
Covers: Problem Statement (array of integers — size is magnitude, sign is direction; same speed; collisions destroy the smaller, or both if equal; same-direction asteroids never collide) → Example 1 (`[4, 8, -3, 9, 7, -8]` → `[4, 8, 9]`) → Example 2 (`[20, 5, 10, -10, -20]` → `[]`, everything destroyed).

**Beats to emphasise**

- Walk Example 1's chain exactly as the deck does: `8` and `-3` collide (opposite directions) → `|8| > |3|` → `-3` explodes. Then `9` and `7` and `-8`: `7` and `-8` collide → `|-8| > |7|` → `7` explodes. Then `9` and `-8` collide → `|9| > |-8|` → `-8` explodes. Final: `[4, 8, 9]`, all moving right, no more collisions possible.
- **Say explicitly why Example 2 ends empty:** every remaining pair keeps colliding until the very last two (`20` and `-20`) are exactly equal — both explode, leaving nothing.
- Name the three genuinely distinct "nothing happens" cases up front, since they get confused with each other: same direction (never collide), moving apart (e.g. positive then further positive — never meet), and "already resolved" (an asteroid that already exploded is simply gone, not compared again).

**Checkpoint (at 17 min)** — cold-call:
> *"In Example 1, why doesn't `4` ever collide with anything, even though there are several collisions happening to its right?"*
> **Answer:** `4` is moving right, and every asteroid to its right that survives is also eventually moving right (or has already been destroyed) — they're moving apart or in the same direction, so `4` never catches up to anything and nothing catches up to `4`.

---

## Slide Block B1 (17–25 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 30–61: Approach, Dry Run on arr = [7, 5, 4, -5, -6, -8, -9, 12] -->
Covers: Approach (use a stack to track surviving asteroids; push positives directly; for negatives, resolve collisions against the stack top before deciding whether to push) → full dry run on `[7, 5, 4, -5, -6, -8, -9, 12]`.

**Beats to emphasise**

- Narrate the dry run's collision chain exactly as the deck does: `7, 5, 4` all push (all positive, no collisions yet). `-5` arrives: collides with top `4` → `|4| < |-5|` → `4` explodes; compare `-5` against new top `5` → `|5| == |-5|` → **both** explode. `-6` arrives: collides with top `7` → `|7| > |-6|` → `-6` explodes, `7` survives untouched.
- Continue: `-8` arrives: collides with `7` → `|-8| > |7|` → `7` explodes; stack now empty → push `-8` directly (nothing left to collide with). `-9` arrives: top is `-8`, **same direction** (both negative) → no collision → push `-9`. `12` arrives: top is `-9`, moving apart (12 right, -9 already past and moving further left) → no collision → push `12`.
- Final stack, bottom to top: `[-8, -9, 12]` — say clearly this is the survivor list, not sorted, not filtered — exactly whatever was left standing.

**Checkpoint (at 25 min)** — cold-call:
> *"When `-9` arrives and the stack top is `-8`, why is there no collision, even though one is negative-ish and could look like a candidate?"*
> **Answer:** Both `-8` and `-9` are moving in the *same* direction (left) — same-direction asteroids never collide, regardless of size.

---

## Classroom Quiz (25–30 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Collide/No-Collide Sort (30–33 min)

**Why this strategy here:** Part 2's classification drill (a full activity) works better once students have already had one fast, low-stakes pass at sorting scenarios into "collide" vs. "no collision" — this wrap primes exactly that instinct before the harder trap case arrives.

**Run it (3 minutes):**
> *"I'll describe two asteroids. You call out: collide, or no collision — fast, gut reaction."* Call out: *"Both moving right"* (no) · *"One moving right, one moving left, right one is behind"* (collide) · *"Both moving left"* (no) · *"Left one already past, right one arrives after"* (no — moving apart, the trap) · *"Equal magnitude, opposite directions"* (collide, both destroyed).

Don't over-explain the trap case yet — just note who hesitated.

> *"That fourth one — hold onto your gut reaction. Part 2 opens with exactly that trap, and it catches almost everyone the first time."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Equal-magnitude collisions leave one survivor | Most collision intuitions expect a "winner" | Explicit callout in the dry run: equal magnitude means **both** are destroyed, no winner |
| Same-direction asteroids can still collide if one is "catching up" | The problem states all asteroids move at the same speed, which is easy to skim past | Restate explicitly: identical speed means same-direction asteroids maintain constant distance forever — same direction always means no collision |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split right after the Classroom Quiz.**
- **This is a long deck (106 slides) but most of the length is the two full worked examples, not new mechanism** — after Slide Block A's first example, the algorithm itself doesn't change; you're building fluency, not new rules. Pace accordingly and don't feel obligated to narrate every slide.
- Part 2 (session-57b) opens with the trap case previewed in the Part 1 Wrap — don't resolve it here, let it land fresh.
