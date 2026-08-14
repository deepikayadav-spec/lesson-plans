# Session 25 — Asteroid Collision

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Stack — Asteroid Collision Simulation · **Prerequisite** Session 24 — Balanced Parenthesis
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Asteroid Collision | https://docs.google.com/presentation/d/1trHgk2ucVk3foQoA1rsUq-UXjv5dZd2ixi0HQCXhKGc/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the collision rules: smaller asteroid destroyed, equal-size asteroids both destroyed, same-direction asteroids never collide. *(REMEMBERING)*
2. Explain why a stack models this problem naturally — the most recently surviving asteroid is exactly what a new left-moving asteroid must be compared against first. *(UNDERSTANDING)*
3. Distinguish the three "no collision" cases (same direction, moving apart, one already destroyed) from the two collision-resolution cases. *(ANALYZING)*
4. Trace the stack-based simulation on a given array, including a case where one incoming asteroid destroys more than one stack element in a row. *(APPLYING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 24 (3–7 min) · ALS: Polling

5 questions on **Session 24 (Balanced Parenthesis)**. ~45 s each, project the distribution, never name individuals.

**Q1.** A closing bracket arrives and the stack is empty. The string is:
`A` Automatically valid · `B` Invalid · `C` Valid if it's the last character · `D` Undetermined
→ **B.**

**Q2.** After scanning the entire string, if the stack is *not* empty, the string is:
`A` Valid · `B` Invalid · `C` Depends on how many are left · `D` Undetermined
→ **B.**

**Q3.** Why isn't counting brackets of each type enough to check validity?
`A` It is enough · `B` Equal counts don't guarantee correct order or matching types · `C` Counting is too slow · `D` Some brackets don't have pairs
→ **B.**

**Q4.** What's the time and space complexity of the balanced-parenthesis check?
`A` O(N) time, O(N) space · `B` O(N²) time, O(1) space · `C` O(1) time, O(N) space · `D` O(N log N) time, O(N) space
→ **A.**

**Q5.** *(MSQ — select all that apply)* True failure modes for bracket validation?
`A` Closing bracket with an empty stack · `B` Closing bracket that doesn't match the top · `C` Leftover unclosed brackets at the end · `D` Too many total characters
→ **A, B, C.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Write this on the board: `[5, 10, -10, -5]` (positive = moving right, negative = moving left).

Ask: *"Picture these as literally asteroids in a straight line in space, each moving at the same speed in the direction its sign shows. Which two are ever going to meet?"*

Let students reason: `10` (moving right) and `-10` (moving left) are heading toward each other.

> *"When they meet, one of two things happens: the bigger one survives and the smaller one is destroyed, or if they're exactly equal, both are destroyed. Same-direction asteroids never catch each other — they're moving at identical speed. Today we simulate an entire line of these collisions, and it turns out a stack is exactly the right tool, for a very physical reason: the only asteroid a new left-mover can possibly hit is whichever one most recently survived and is still in front of it."*

---

## Slide Block A (10–17 min) — DELIVER SLIDES AS-IS

Covers: Problem Statement (array of integers — size is magnitude, sign is direction; same speed; collisions destroy the smaller, or both if equal; same-direction asteroids never collide) → Example 1 (`[4, 8, -3, 9, 7, -8]` → `[4, 8, 9]`) → Example 2 (`[20, 5, 10, -10, -20]` → `[]`, everything destroyed).

**Beats to emphasise**

- Walk Example 1's chain: `8` and `-3` collide (opposite directions) → `|8| > |3|` → `-3` explodes. Then `7` and `-8` collide → `|-8| > |7|` → `7` explodes. Then `9` and `-8` collide → `|9| > |-8|` → `-8` explodes. Final: `[4, 8, 9]`.
- **Say explicitly why Example 2 ends empty:** every remaining pair keeps colliding until the very last two (`20` and `-20`) are exactly equal — both explode, leaving nothing.
- Name the three genuinely distinct "nothing happens" cases up front: same direction (never collide), moving apart (never meet), and "already resolved" (an asteroid that already exploded is simply gone, not compared again).

**Checkpoint (at 17 min)** — cold-call:
> *"In Example 1, why doesn't `4` ever collide with anything, even though there are several collisions happening to its right?"*
> **Answer:** `4` is moving right, and every asteroid to its right that survives is also eventually moving right (or has already been destroyed) — they're moving apart or in the same direction, so `4` never catches up to anything and nothing catches up to `4`.

---

## Slide Block B1 (17–24 min) — DELIVER SLIDES AS-IS

Covers: Approach (use a stack to track surviving asteroids; push positives directly; for negatives, resolve collisions against the stack top before deciding whether to push) → full dry run on `[7, 5, 4, -5, -6, -8, -9, 12]`.

**Beats to emphasise**

- Narrate the dry run's collision chain: `7, 5, 4` all push (all positive, no collisions yet). `-5` arrives: collides with top `4` → `4` explodes; compare `-5` against new top `5` → equal magnitude → **both** explode. `-6` arrives: collides with top `7` → `7` survives, `-6` explodes. `-8` arrives: collides with `7` → `7` explodes; stack now empty → push `-8`. `-9` arrives: top is `-8`, **same direction** → no collision → push `-9`. `12` arrives: top is `-9`, moving apart → no collision → push `12`.
- Final stack, bottom to top: `[-8, -9, 12]` — this is the survivor list, not sorted, not filtered — exactly whatever was left standing.

**Checkpoint (at 24 min)** — cold-call:
> *"When `-9` arrives and the stack top is `-8`, why is there no collision?"*
> **Answer:** Both `-8` and `-9` are moving in the *same* direction (left) — same-direction asteroids never collide, regardless of size.

---

## ⚡ ALS Activity 1 — Spot the Bug: Collide or Not? (24–30 min)

**ALS format:** Spot the Bug / Predict-the-Output — exposes whether students can correctly classify each pairwise interaction into "collide" vs. "no collision," and if colliding, resolve the outcome — the single skill the whole algorithm depends on. Chosen right after Slide Block B1 because this is where the trap case needs to land before students trust their own classification instincts.

**Setup line:**
> *"Four pairs of asteroids about to meet or not meet. For each: do they collide? If yes, what survives?"*

```
1.  Stack top = 6,  incoming = -6
2.  Stack top = -3, incoming = -9
3.  Stack top = 4,  incoming = 9    (incoming is positive)
4.  Stack top = -2, incoming = 8
```

45 seconds silent, then hands up. Take one pair per student.

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

**Cut rule:** Do pairs 1 and 4 only — pair 1 is the clean collision case, pair 4 is the trap that catches almost everyone.

---

## Slide Block B2 (30–36 min) — DELIVER SLIDES AS-IS

Covers: Pseudocode (while-loop collision resolution against the stack top, per incoming negative) → complexity (O(N) time, O(N) space) → the deck's second full dry run, `[-3, 25, 10, 15, 12, 8, -12, -20]` → `[-3, 25]`.

**Beats to emphasise**

- Point directly at the `while` loop in the pseudocode: an incoming negative asteroid doesn't just check the stack top *once* — it keeps colliding and popping as long as the top is positive and smaller, exactly like a monotonic stack's pop loop.
- Complexity: total pushes and pops across the whole run are bounded by roughly `2N` — the same argument from Session 20's activity.
- In the second example, walk the chain quickly: `8` and `-12` collide → `8` explodes. `12` and `-12` collide, equal → both explode. `15` and `-20` collide → `15` explodes. `10` and `-20` collide → `10` explodes. `25` and `-20` collide → `-20` explodes (`25` is bigger). Final: `[-3, 25]`.

**Checkpoint (at 36 min)** — cold-call:
> *"In that second dry run, why does `-3` (the very first element) survive untouched the whole time?"*
> **Answer:** `-3` is moving left with nothing to its left to collide with, and it's never compared against anything after it either — everything to its right that survives ends up moving right or already resolved, so `-3` just sits at the bottom of the stack the entire run.

---

## ⚡ ALS Activity 2 — Live Coding / Dry-Run Relay: Run the Full Chain (36–41 min)

**ALS format:** Live Coding / Dry-Run Relay — exposes whether students can execute a multi-step collision chain themselves, including a case where one incoming asteroid destroys more than one stack element in a row. Chosen as the closing activity because "while, not if" is the last mechanical detail students need before they can implement this alone.

**Setup line:**
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

**Cut rule:** Do only the `-8` step — it's the one that carries the whole "keep colliding until stopped" lesson; `6`, `3`, and `2` are all simple pushes.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering the collision rules and the moving-apart trap case. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> For `arr = [8, -8]`, what survives? For `arr = [8, -9]`? For `arr = [9, -8]`?
> **Answers:** `[8, -8]` → equal magnitude → both explode → `[]`. `[8, -9]` → `|-9| > |8|` → `8` explodes → `[-9]`. `[9, -8]` → `|9| > |-8|` → `-8` explodes → `[9]`.

**Homework:** Trace `arr = [5, -3, -4, 9]` by hand and state the final surviving array.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Equal-magnitude collisions leave one survivor | Most collision intuitions expect a "winner" | Slide Block B1's dry run — equal magnitude means **both** are destroyed, no winner |
| Same-direction asteroids can still collide if one is "catching up" | The problem states all asteroids move at the same speed, which is easy to skim past | Restate: identical speed means same-direction asteroids maintain constant distance forever |
| Opposite signs always means a collision | Feels like the obvious reading of "moving toward each other" | ALS Activity 1, pair 4 — a negative already on the stack (moving left) followed by a positive arriving (moving right) are moving *apart*, not colliding |
| An incoming asteroid only ever resolves one collision before being pushed | Carried over from underestimating pop loops generally (same trap as Sessions 20/21) | ALS Activity 2's `-8` step — one incoming element destroys two stack elements in sequence via a `while`, not an `if` |
| The stack at the end needs sorting or filtering to get the final answer | The final transfer-to-array step looks like extra processing | Point out the transfer only reverses order — no filtering or sorting happens, the stack already holds exactly the survivors |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Merged from two original sessions ("Asteroid Collision" Parts 1 and 2, 33 + 27 min = 60 min) into one 50-min session — see `sem-3-sequence.md`.
- **Two ALS activities this session, both carried over directly:** Activity 1 is Spot the Bug (Collide or Not?, including the moving-apart trap), Activity 2 is the Live Coding / Dry-Run Relay (the full multi-destroy chain). The original Part 1 "Collide/No-Collide Sort" wrap is dropped as redundant with Activity 1, which resolves the same trap case properly rather than just previewing it.
- **The Classroom Quiz now runs last, right before the Exit Ticket** — moved from its original mid-session position to match the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank.
- **This is session 25 of the Sem-3 sequence** (see `sem-3-sequence.md`) — the fourth monotonic-stack-family problem (after Sessions 20, 21, and implicitly reused in 23).
- **ALS Activity 1's pair 4 is the single most important five minutes of this session.** Almost every student will initially say "opposite signs, must collide" — do not rush past the correction. This misconception, uncorrected, breaks every dry run for the rest of the session.
- **This is a long deck (106 slides) but most of the length is the two full worked examples, not new mechanism** — after Slide Block A's first example, the algorithm itself doesn't change; you're building fluency, not new rules. Pace accordingly and don't feel obligated to narrate every slide.
- **Bridge to Session 26:** mention at the close that Largest Rectangle in Histogram uses a monotonic stack again, in yet another physical framing — the pattern recurring for a fifth time by now should be explicit and reassuring, not a surprise.
