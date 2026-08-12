# Session 58a — Largest Rectangle in Histogram (Part 1 of 2)

**Duration** 35 min · **Topic** Stack & Queue — Largest Rectangle: NSE/PSE Approach · **Prerequisite** Session 57 — Asteroid Collision · **Session type** Concept lecture

<!-- Split note: original session-58 ran 55 min — the hardest session in the block, with two full approaches. Split right after the Classroom Quiz. Part 1 covers the problem, the core "how far can this bar's rectangle stretch" idea, and the full two-pass NSE/PSE dry run — deliberately not skipped, since it's what makes Part 2's optimal approach make sense. Part 2 (session-58b) covers the one-pass optimal approach and two full hands-on activities. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Largest Rectangle in Histogram | https://docs.google.com/presentation/d/1_OHNtNxlKJdYOX6LT_zqx1NwQnuQF8T6onInuzNhN2I/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the problem: given bar heights of width 1, find the largest rectangular area that fits within the histogram's outline. *(REMEMBERING)*
2. Explain why a rectangle anchored at a given bar's height can only extend as far as the nearest shorter bar on each side. *(UNDERSTANDING)*
3. Compute Next Smaller Element (NSE) and Previous Smaller Element (PSE) arrays using a monotonic stack, and use them to calculate every bar's maximum rectangle area. *(APPLYING)*

*(The optimal one-pass approach is covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 57 (Asteroid Collision) (0–6 min)

Say: *"Eight quick ones on asteroid collisions before we hit the hardest problem in this block."*

**Q1.** Two asteroids of equal magnitude, moving toward each other:
`A` The larger one survives · `B` Both are destroyed · `C` Neither is affected · `D` They pass through each other

**Q2.** Two asteroids moving in the same direction:
`A` Always collide · `B` Never collide · `C` Collide only if adjacent · `D` Collide only if equal size

**Q3.** In the stack-based simulation, when a negative (left-moving) asteroid arrives, it's compared against:
`A` Every element in the array · `B` The stack top, repeatedly, until stopped or the stack empties · `C` Only the very first element pushed · `D` Nothing — it's always pushed directly

**Q4.** What is the overall time complexity of the stack-based asteroid simulation?
`A` O(1) · `B` O(N) · `C` O(N²) · `D` O(N log N)
→ *Read:* B. If this misses, restate the "each element pushed and popped at most once" argument in one line — today's problem reuses that exact argument twice, for two separate passes.

**Q5.** A positive (right-moving) asteroid meeting a negative asteroid already on the stack that's also moving left:
`A` Collides — opposite signs · `B` Doesn't collide — they're moving apart · `C` Always destroys the negative one · `D` Is an invalid input

**Q6 (MSQ — pick all correct).** Which are true of the collision simulation?
`A` It uses a stack · `B` A single incoming asteroid can destroy more than one stack element · `C` The final stack, transferred to an array, is the answer · `D` It requires sorting the input first

**Q7.** For `arr = [3, -3]`, what survives?
`A` `[3]` · `B` `[-3]` · `C` `[]` · `D` `[3, -3]`

**Q8.** True or false: same-speed movement is why same-direction asteroids never collide.
`A` True · `B` False

**Running it** — poll tool, ~25 s per question. Total 6 min including reads.

---

## Hook (6–9 min)

Draw a rough skyline on the board — bars of heights `2, 1, 5, 6, 2, 3` sitting side by side, each width 1.

Ask: *"Somewhere in this skyline is the single largest rectangle that fits entirely under the outline — not a rectangle that goes outside any bar's height. Just eyeball it — where do you think it is, and how big?"*

Let a few guesses land (the actual answer here is height 5, width 2, area 10 — bars at height 5 and 6). Then:

> *"You just did that by squinting at the whole picture at once. A computer can't squint — it needs a rule. And the rule turns out to depend on something you already know how to compute: for every single bar, how far can a rectangle at *that bar's height* stretch left and right before it hits something shorter? That 'how far' is exactly Previous Smaller Element and Next Smaller Element — the same monotonic stack from three sessions ago, run twice."*

---

## Slide Block A (9–18 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 4–22: Problem Statement, Examples 1 & 2 (manual rectangle enumeration), Better Approach intro (NSE/PSE) -->
Covers: Problem Statement (bars of width 1, find the largest enclosed rectangular area) → Example 1 (`[4, 2, 7, 6, 1, 5]` → area `12`) → Example 2 (`[2, 6, 4, 1, 5, 2, 7, 3]` → area `8`) → Better Approach: precompute Next Smaller Element and Previous Smaller Element for every bar using stacks, then use them to compute each bar's maximum area.

**Beats to emphasise**

- Walk Example 1's winning rectangle exactly as the deck builds it: height `6`, width `2` (bars at index 2 and 3, heights `7` and `6`) → area `12`. Say explicitly: the rectangle's height is capped by the *shorter* of the two bars it spans.
- **State the core idea as one sentence, this is the entire session:** "for every bar, if I use *its own height* as the rectangle's height, how wide can that rectangle get before it hits a shorter bar on the left, and a shorter bar on the right?"
- Name the two arrays before the dry run touches them: NSE (Next Smaller Element — nearest shorter bar to the right) and PSE (Previous Smaller Element — nearest shorter bar to the left). Width for bar `i` = `NSE[i] - PSE[i] - 1`.

**Checkpoint (at 18 min)** — cold-call:
> *"If a bar's PSE is at index 2 and its NSE is at index 7, how wide is the rectangle anchored at that bar?"*
> **Answer:** `7 - 2 - 1 = 4` — the rectangle spans strictly between the two boundary indices, not including them.

---

## Slide Block B1 (18–27 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 23–68: Dry Run computing NSE then PSE via two stack passes on arr = [2, 3, 8, 10, 6, 7, 5], area calculation per bar, Pseudocode, Complexity, Code -->
Covers: Full dry run on `arr = [2, 3, 8, 10, 6, 7, 5]` — first pass right-to-left builds NSE using a stack of indices; second pass left-to-right builds PSE the same way; then area is computed per index using `height × (NSE − PSE − 1)`.

**Beats to emphasise**

- Narrate the NSE pass exactly as the deck does: scanning right to left, at each index pop any stack index whose value is `≥` the current bar, then the new top (if any) is the NSE index. For `arr[6] = 5`: stack empty → `NSE[6] = 7` (past the end, meaning "nothing smaller to the right"). For `arr[4] = 6`: pop index 5 (`arr[5]=7 ≥ 6`), top becomes index 6 (`arr[6]=5 < 6`) → `NSE[4] = 6`.
- Then the PSE pass, same mechanism, left to right: for `arr[4] = 6`: pop indices where `arr[stk.top()] ≥ 6` (pops `10` at index 3, pops `8` at index 2), top becomes index 1 (`arr[1]=3 < 6`) → `PSE[4] = 1`.
- Compute one area together on the board: bar at index 4, height `6`, `NSE[4]=6, PSE[4]=1` → width `6-1-1=4` → area `6×4=24`. The deck's final max across all bars is `25` (bar at index 6, height `5`, spanning the full remaining width).

**Checkpoint (at 27 min)** — cold-call:
> *"Why do we need two separate passes — one for NSE, one for PSE — instead of one?"*
> **Answer:** NSE looks *forward* from each bar (nearest shorter bar to its right), so it's naturally computed scanning right-to-left; PSE looks *backward*, so it's naturally computed scanning left-to-right. They're mirror-image questions needing mirror-image scan directions.

---

## Classroom Quiz (27–32 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Whiteboard Race (32–35 min)

**Why this strategy here:** NSE/PSE index arithmetic has to become fast and reliable before Part 2's optimal approach folds both computations into a single pass — if students are still slow at "pop while ≥, then the new top is the answer," the one-pass version will look like magic instead of a genuine simplification.

**Run it (3 minutes):**
> *"Two teams, two board halves. Array `[5, 2, 6, 3]`. I call an index — first team to correctly state its NSE index (scanning right to left) scores a point."*

Call 2-3 indices fast. Keep score loosely.

> *"That reflex — pop while ≥, next top is your answer — is the exact same reflex Part 2's optimal approach uses, just now computing an area the instant that pop happens instead of writing it to an array."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The largest rectangle must use the tallest bar in the array | Instinct: "biggest number should matter most" | Session hook — the tallest bar is often narrow, and a shorter-but-wider rectangle can beat it (Example 1: `6` beats `10`'s isolated width of 1) |
| NSE and PSE can both be computed in a single pass | Feels redundant to scan the array twice | Slide Block B1's checkpoint — NSE looks forward, PSE looks backward; they need opposite scan directions in this two-pass method |

---

## Instructor Notes

- **This is Part 1 of a 55-minute original session, split right after the Classroom Quiz. This is the hardest session in the block** — protect its time elsewhere in the week if the schedule allows.
- **Do not skip this NSE/PSE approach to save time and jump straight to Part 2's optimal approach.** Students need the "compute boundaries first, then areas" version to appreciate what the one-pass approach is actually optimising away.
