# Session 22b — Implementation of Binary Heap (Part 2 of 2)

**Duration** 31 min · **Topic** Heaps — Array-Based Insert, extractMax & Complexity · **Prerequisite** Session 22a — Implementation of Binary Heap, Part 1 (array representation, index formulas) · **Session type** Concept lecture

<!-- Split note: continues session-22 (original 60 min) right after the Classroom Quiz. This part covers the full worked insert/extractMax on the array (every index recomputation), size/empty, and the complexity summary table. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Implementation of Binary Heap | https://docs.google.com/presentation/d/1vvJCSr9J7R6iDbHufVqSWLRXYfRDl77iaNVfBakXIcA/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Trace the array-based `insert()` and `extractMax()` operations on a worked example, including every index recomputation. *(APPLYING)*
2. State the time and space complexity of all five heap operations — `insert`, `extractMax`, `getMax`, `size`, `empty`. *(REMEMBERING)* <!-- placement: inferred from the deck's own complexity summary table, slide 47 -->

---

## Warm-Up Poll — Retrieval Practice on Session 22a (0–5 min)

Say: *"Four quick ones on the index formulas before we run them at full speed."*

**Q1.** For index `i`, the left child's index is:
`A` `2i` · `B` `2i+1` · `C` `2i+2` · `D` `i/2`
→ *Read:* B — 0-indexed.

**Q2.** For index `i`, the parent's index is:
`A` `i/2` · `B` `(i-1)/2` · `C` `2i-1` · `D` `i-1`
→ *Read:* B.

**Q3.** `up_heapify()` moves in which direction?
`A` Toward the root · `B` Toward the leaves · `C` Sideways across a level · `D` It doesn't move, it's O(1)
→ *Read:* A — used on insert.

**Q4.** `down_heapify()` moves in which direction?
`A` Toward the root · `B` Toward the leaves · `C` Sideways across a level · `D` It doesn't move, it's O(1)
→ *Read:* B — used on delete/extraction.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"Formulas at speed, checked. Now: the full insert and the full extractMax, run entirely through those formulas, on a real array."*

---

## Slide Block B (7–21 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — slides 11–42: initialization, full worked insert (value 50), insert complexity, getMax, getMax complexity, full worked extractMax, extractMax complexity -->
Covers: heap initialization (capacity + size variable) → worked insert of `50` into a 9-element max heap, tracked through every swap and index recomputation → insert complexity `O(log n)` → `getMax()` (return `arr[0]`, `O(1)`) → worked `extractMax()` on the resulting heap, tracked through every `down_heapify` comparison and swap → extractMax complexity `O(log n)`.

**Beats to emphasise**

- **`capacity` and `size` are two different numbers, both tracked explicitly.** `capacity` is the array's fixed length; `size` is how many elements are currently in use. Point this out on the initialization slide — it resolves the "how does the array know when to stop" question before it gets asked.
- **On the insert walkthrough:** narrate the pattern once — "place at index `size`, then repeatedly compute `parent = (i-1)/2`, compare, swap if the new element is bigger, move `i` to the parent's index, repeat" — then move through the remaining slides at a confirming pace rather than re-deriving the arithmetic each time.
- **On the extractMax walkthrough:** the two-step shape is identical to Session 21's tree version — replace root with the last element, then `down_heapify` — but every single comparison is now driven by computing `2i+1` and `2i+2` for children, checking bounds, and picking whichever child is *larger* before swapping. This is the part that trips students moving from pointers to arrays: they can describe "bubble down" in words but stumble computing which child index actually wins.

**Checkpoint (at 21 min)** — show hands:
> *"getMax() is O(1). extractMax() is O(log n). In one sentence — why the difference?"*
> **Answer:** `getMax()` only reads `arr[0]`; `extractMax()` has to remove the root, promote the last element, and then restore heap order by bubbling it down through up to `log n` levels.

---

## ⚡ Activity 2 — Dry-Run Relay: extractMax() by Index Arithmetic (21–26 min)

**Format:** Live Dry-Run Relay · **Exposes:** students who can describe "bubble down" correctly in words but stumble translating it into which array index actually gets compared and swapped next.

**Setup line (say this):**
> *"Same extractMax() operation you just watched, one more time — but I move nothing unless you give me the exact index math. Not 'swap with the bigger child.' Tell me the index."*

**What students do:** Using the deck's own worked extractMax example (root value replaced by the last element, size drops from 10 to 9): at index `0`, call out `left = 2(0)+1 = 1`, `right = 2(0)+2 = 2`, then state which of those two array positions holds the larger value and that a swap with that index is needed. After the swap, recompute for the new index and repeat.

**How it surfaces:** If a student says "swap with the left child" without computing `2i+1` and checking it against `2i+2`'s value, stop and make them state both indices and both values before allowing the swap. This is the exact gap the activity exists to catch.

**Debrief line:**
> *"The idea — bubble the replacement down until it's no longer smaller than either child — is exactly what you did with pointers last session. The only thing that changed is that 'child' is now a formula, not something you can just point at. If the formula's wrong, nothing crashes — the heap just quietly stops being a heap."*

**Cut rule:** If running short, relay only the first swap (index 0 → its larger child) and state the remaining down-heapify steps yourself.

---

## Slide Block C (26–28 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — slides 43–49: size(), empty(), complexity summary table, Key Takeaways -->
Covers: `size()` (return the `size` variable, `O(1)`) → `empty()` (check `size == 0`, `O(1)`) → complexity summary table for all five operations → Key Takeaways.

**Beats to emphasise**

- `size()` and `empty()` are the two operations students are most likely to over-think — both are a single variable read/comparison, `O(1)`, no traversal involved. Say this plainly; don't let the slide's brevity make it feel like there's a catch.
- Put the complexity summary table (Insert `O(log n)`, extractMax `O(log n)`, getMax `O(1)`, size `O(1)`, empty `O(1)`, all `O(1)` space) on the board and leave it up — it's the single most quotable slide of the session.

---

## Exit Ticket (28–31 min)

> On paper or in chat: *"Array-based max heap: `[45, 30, 20, 10, 25, 15]` (indices 0–5). What are the left child, right child, and parent index of the node at index 2? Is `insert()` or `extractMax()` more expensive, and why?"*
> **Answer:** For index 2: left = `2(2)+1 = 5`, right = `2(2)+2 = 6` (out of range — no right child), parent = `(2-1)/2 = 0`. Both `insert()` and `extractMax()` are the same order of growth, `O(log n)` — neither is "more expensive" in Big-O terms, though `extractMax()` does strictly more work per level (two comparisons per step vs. one). <!-- placement: inferred exit-ticket scenario, built on the same index formulas taught in the session -->

**Homework:** re-derive the three index formulas from scratch and re-run the extractMax dry run on paper, without looking at the slides. <!-- placement: inferred; no homework/practice-unit table exists for this course -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Arrays need shifting/resizing on every insert, like a sorted array | Prior experience with sorted arrays where insertion is expensive | Point out insertion here places the new element at `arr[size]` (the next open slot) and only *swaps* upward — no shifting of other elements |
| `size()` and `empty()` require some kind of traversal or computation | Unfamiliarity with a data structure that tracks its own count explicitly | Point at the `capacity`/`size` variables from the initialization slide — both are `O(1)` reads of a variable that's already being maintained |
| During `down_heapify`, swap with whichever child "looks bigger" without checking both | Bubble-down in words sounds like "compare with a child," singular | Activity 2's dry-run relay — force students to state both child indices and both values before naming the swap target |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz.**
- **Pacing risk:** the worked insert (slides 12–24) and worked extractMax (slides 30–41) are each roughly a dozen slides for a handful of repeated comparisons. State the pattern once per operation, then move briskly — dwelling on each slide's arithmetic will run the session long.
- Have the complexity summary table (slide 47) written on the board by the end of class and left visible — it's the cleanest single artifact from this session and the one most likely to show up again in Sessions 26–28.
