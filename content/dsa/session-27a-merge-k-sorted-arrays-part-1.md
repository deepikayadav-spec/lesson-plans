# Session 27a — Merge K Sorted Arrays (Part 1 of 2)

**Duration** 37 min · **Topic** Heaps — Merge K Sorted Arrays: Brute Force & Optimal Approach · **Prerequisite** Kth Largest Element in an Array (Session 26) · **Session type** Concept lecture

<!-- Split note: original session-27 ran 50 min. Split right after the Classroom Quiz. Part 1 covers the problem statement, the brute-force flatten-and-sort approach, and the optimal min-heap approach with its full dry run. Part 2 (session-27b) covers the two hands-on activities (the refill-the-row relay and the unequal-row-length discussion) and the exit ticket. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Merge K Sorted Arrays | https://docs.google.com/presentation/d/1Bu6HdP47N4RTkNWi_ud30zeqyyCN79sKaEAAeMY7ACM/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the problem: given `k` sorted arrays (a `k × k` matrix), merge them into one fully sorted array. *(REMEMBERING)*
2. Explain the brute-force approach — flatten every array into one list, then sort — and its `O(k² log k²)` cost. *(UNDERSTANDING)*
3. Trace the optimal min-heap approach: seed the heap with the first element of every row, then repeatedly pop the smallest and push the next element from that same row. *(APPLYING)*
4. Explain why each heap entry must carry its row and column indices, not just its value — this is what lets the algorithm find "the next element from the same row" after a pop. *(ANALYZING)*

*(The hands-on relay, the unequal-row-length generalization, and the exit ticket are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 26 (Kth Largest Element in an Array) (0–6 min)

Say: *"Six on last session's top-k heap trick, then we scale the same idea up to merging entire arrays instead of tracking single elements."*

**Q1.** In the optimal Kth-Largest solution, the heap used is a:
`A` Max-heap · `B` Min-heap · `C` Either works identically · `D` Neither — a plain array is used
→ **Answer:** B.

**Q2.** The eviction rule in that heap is: whenever the heap's size exceeds `k`, remove:
`A` The most recently added element · `B` The largest element · `C` The smallest element · `D` A random element
→ **Answer:** C.

**Q3.** After processing every element, the answer (`k`-th largest) is found at:
`A` The heap's smallest remaining element (its root) · `B` The heap's largest remaining element · `C` The first element inserted · `D` The last element inserted

**Q4.** Time complexity of the min-heap approach to Kth Largest Element?
`A` `O(n log n)` · `B` `O(n log k)` · `C` `O(n)` · `D` `O(k log k)`
→ **Answer:** B.

**Q5.** The heap-based approach beats sorting the whole array specifically when:
`A` `k` is close to `n` · `B` `k` is small relative to `n` · `C` The array is already sorted · `D` It never beats sorting

**Q6 (MSQ — pick all correct).** Which are true of the min-heap in that session?
`A` It never holds more than `k` elements after the first `k` insertions · `B` Its root is always the current smallest of the surviving top-`k` · `C` It must be rebuilt from scratch for every insertion · `D` Push and pop each cost `O(log k)`

**Running it** — poll tool, ~30 s per question. Total 6 min including reads.

---

## Hook (6–9 min)

Ask: *"You have `k` different sorted playlists, and you want one single sorted playlist out of all of them combined. Do you have to dump every song into one giant list and re-sort everything from scratch, when each individual playlist was already in order?"*

Let students react. Then:

> *"No — and today's heap trick is exactly about not throwing away work that's already done. Each array arrives pre-sorted; the only real question at every step is 'which array currently has the smallest next candidate?' A min-heap answers that question in `O(log k)`, repeatedly, without ever re-sorting anything that was already sorted."*

---

## Slide Block A (9–18 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 4–23: Problem Statement, Examples, Brute Force Approach, Dry Run, Pseudocode, Complexity, Code -->
Covers: problem statement (`k` sorted arrays, each length `k`, arranged as a `k × k` matrix; merge into one sorted array) → Example 1 (`[[1,2,3],[10,15,17],[5,9,11]]` → `[1,2,3,5,9,10,11,15,17]`) → Example 2 (empty input → empty output) → brute force: flatten all arrays into one list, then sort → dry run: traverse each row in turn appending to `answer`, then sort the fully flattened result → pseudocode → complexity (`O(k² + k² log k²)` = `O(k² log k²)` time — flattening is `O(k²)`, dominated by the sort; `O(k²)` space for the flattened array) → C++/Python code.

**Beats to emphasise**

- State the brute force in one line: *"dump every row into one big list, then sort that list once — simple, but it throws away the fact that each row already arrived in order."*
- **Say explicitly what's wasted:** *"the sort has to re-discover ordering information that already existed inside each row — it treats the flattened list as if it were completely random."*
- Complexity: flattening costs `O(k²)` (total elements across all rows), and the sort of that flattened list costs `O(k² log k²)` — the sort dominates.

**Checkpoint (at 18 min)** — cold-call:
> *"What information does the brute-force sort throw away that the input already gave us for free?"*
> **Answer:** Each individual row was already sorted — the brute force ignores that entirely and re-sorts the fully flattened, unordered-looking list from scratch.

---

## Slide Block B (18–29 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 24–54: Optimal Approach, full Dry Run, Pseudocode, Complexity, Code -->
Covers: optimal approach — min-heap seeded with the first element of every row, each entry tagged `(value, (row, column))`; repeatedly pop the smallest, append it to the answer, and if that row has a next element, push it into the heap → full dry run on `[[1,2,3],[10,15,17],[5,9,11]]`: seed heap with `(1,(0,0))`, `(10,(1,0))`, `(5,(2,0))`; pop `1`, push `(2,(0,1))`; pop `2`, push `(3,(0,2))`; pop `3` (row 0 exhausted, nothing pushed); pop `5`, push `(9,(2,1))`; pop `9`, push `(11,(2,2))`; pop `10`, push `(15,(1,1))`; pop `11` (row 2 exhausted); pop `15`, push `(17,(1,2))`; pop `17` — final answer `[1,2,3,5,9,10,11,15,17]` → pseudocode → complexity (`O(k log k)` to seed the heap with the first `k` elements, `O(k² log k)` to process the remaining `k²` push/pop pairs, overall `O(k log k + k² log k)` = `O(k² log k)` time; `O(k)` for the heap plus `O(k²)` for the result array, overall `O(k + k²)` space) → C++/Python code.

**Beats to emphasise**

- **Say the mechanism as one sentence, this is the whole session:** *"seed the heap with one candidate from each row, then every time you pop the smallest, immediately refill from that same row — the heap always holds exactly one live candidate per row that still has elements left."*
- **Narrate why each heap entry needs `(row, column)`, not just the value** — this is the detail students most often skip: *"once you pop a value, you need to know exactly which row and which position it came from, so you can find that row's *next* element to push in its place. The value alone doesn't tell you that."*
- Walk the "row exhausted" case explicitly, at least twice in the dry run: after popping `3` from row 0, there's no next element in that row, so nothing gets pushed — the heap simply shrinks by one live candidate for the rest of the run.
- Complexity: contrast `k² log k` here against `k² log k²` for brute force — note `log k²` = `2 log k`, so the heap approach is a real, not just cosmetic, factor-of-2-in-the-exponent improvement, on top of avoiding a full independent sort.

**Checkpoint (at 29 min)** — cold-call:
> *"After popping the smallest element from the heap, how does the algorithm know what to push back in?"*
> **Answer:** Every heap entry carries the `(row, column)` it came from; after popping, the algorithm checks if `column + 1` is still within that row's bounds, and if so, pushes `(row, column + 1)`'s value next.

---

## Classroom Quiz (29–34 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: 3-2-1 Reflection (34–37 min)

**Why this strategy here:** Part 1 delivered two full approaches back to back (brute force, then optimal). A structured reflection — 3 facts, 2 lingering questions, 1 connection to prior sessions — consolidates before Part 2's faster-paced relay activity, and surfaces confusion while there's still time to address it.

**Run it (3 minutes):**
> *"On paper, thirty seconds each: THREE facts about the optimal approach you're confident on. TWO things still fuzzy. ONE connection to a heap session you've already had — Session 26 counts."*

Ask for a show of hands on the "2 fuzzy things" — if `(row, column)` bookkeeping comes up repeatedly, that's your cue that Part 2's relay activity needs the full time allotted, not the cut-rule version.

> *"Hold onto your fuzzy points. Part 2 is entirely hands-on — you'll run this yourself, one pop at a time."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The heap only needs to store values, not their row/column origin | Session 26's heap only ever tracked plain values | Slide Block B — explicitly showing that without `(row, column)`, there's no way to find "the next element from this same row" after a pop |
| This approach re-sorts anything | The word "merge" sounds adjacent to "sort" | State plainly: every row arrives already sorted, and the heap never reorders elements *within* a row — it only ever decides the relative order *across* rows, one pop at a time |
| `O(k² log k)` and `O(k² log k²)` are basically the same thing | Both have `k²` and `log` in them, so they look similar at a glance | Slide Block B — note `log k² = 2 log k`, a genuine (if modest) improvement layered on top of avoiding an entirely separate full sort of the flattened data |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split right after the Classroom Quiz.**
- **The `(row, column)` bookkeeping is this session's real hurdle, not the heap mechanics themselves.** Students already know min-heap eviction from Session 26 — spend the marginal time here on *why* each entry needs origin metadata, not on re-teaching heap operations from scratch.
- Part 2 (session-27b) reuses the two-row `[4,8]` / `[2,6]` example directly for its live relay — no new setup needed there.
