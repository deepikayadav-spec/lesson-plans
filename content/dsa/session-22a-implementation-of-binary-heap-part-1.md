# Session 22a — Implementation of Binary Heap (Part 1 of 2)

**Duration** 35 min · **Topic** Heaps — Array Representation & Index Formulas · **Prerequisite** Introduction to Heaps (Session 21) · **Session type** Concept lecture

<!-- Split note: original session-22 ran 60 min. Split right after the Classroom Quiz. Part 1 covers the array representation, the three index formulas, and the index-arithmetic drilling activity — the foundation every later operation depends on. Part 2 (session-22b) covers the full worked insert/extractMax on the array, plus size/empty and the complexity summary. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Implementation of Binary Heap | https://docs.google.com/presentation/d/1vvJCSr9J7R6iDbHufVqSWLRXYfRDl77iaNVfBakXIcA/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the two conditions a Binary Heap must satisfy (complete binary tree + heap property). *(REMEMBERING)*
2. Compute the array-index formulas for a node's left child, right child, and parent (`2i+1`, `2i+2`, `(i-1)/2`), given an arbitrary index. *(APPLYING)*
3. Distinguish `up_heapify()` (used on insert) from `down_heapify()` (used on delete), and state which direction each moves through the heap. *(UNDERSTANDING)*

*(The full worked insert/extractMax on the array, and the complexity summary, are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 21: Introduction to Heaps (0–7 min)

Say: *"Eight quick ones on last session's heap basics. We're about to rebuild everything you learned on top of a plain array, so I need to know it's solid."*

**Q1.** What are the two properties every heap must satisfy?
`A` Complete binary tree + heap-order property · `B` Balanced binary tree + sorted order · `C` Binary-search property + complete tree · `D` No properties — any tree qualifies
→ **Answer:** A.

**Q2.** In a max heap, where is the largest element always located?
`A` Any leaf · `B` The root · `C` Wherever it was last inserted · `D` The middle level
→ **Answer:** B.

**Q3.** *(MSQ — pick 2)* Which are true about heap shape?
`A` All levels are full except possibly the last, filled left to right · `B` Left and right children are sorted relative to each other · `C` Height is always `log(n)` · `D` Height can be `O(n)` for a skewed heap
→ **Answer:** A and C. *Read:* D is the BST-carryover trap from two sessions ago — if anyone picks it, that's still unresolved and worth a 10-second correction before moving on.

**Q4.** When inserting a new element, where does it first get placed?
`A` Wherever it belongs in sorted order · `B` The first vacant slot in the last level · `C` As the new root · `D` As a randomly chosen leaf
→ **Answer:** B.

**Q5.** What happens immediately after that placement?
`A` Nothing — insertion is done · `B` Compare against its parent and swap upward while it's bigger ("bubble up") · `C` Compare against both children and swap downward · `D` Rebuild the whole heap from scratch
→ **Answer:** B.

**Q6.** Why is `extractMax()` `O(log n)`?
`A` It isn't — it's `O(1)` · `B` It has to scan the entire heap · `C` Replacing the root and bubbling the replacement down costs at most one swap per level, and there are `log n` levels · `D` It's `O(n log n)`
→ **Answer:** C.

**Q7.** Why is `getMax()` cheaper than `extractMax()`?
`A` `getMax()` just reads the root; `extractMax()` has to remove it and restore heap order · `B` They cost the same · `C` `getMax()` needs to search, `extractMax()` doesn't · `D` There's no real difference
→ **Answer:** A.

**Q8.** Name one real-world application of heaps from last session's deck.
`A` Binary search · `B` Priority queues / heap sort / graph algorithms / kth largest-smallest · `C` Hashing · `D` Recursion
→ **Answer:** B.

**Running it** — poll tool, ~40 s/question. Total 7 min including reads.

---

## Hook (7–11 min)

Say: *"Last session, every heap you saw was drawn as a tree — circles and lines, parent pointers, child pointers. Here's the twist: almost nobody actually implements a heap that way. In real code, a heap usually lives in one flat array, with no pointers at all."*

Draw a max heap tree quickly (or reuse the board from last session), then next to it write a plain array: `[40, 25, 20, 10, 5, 30, 15, 35]`.

Ask: *"Same heap. No pointers anywhere. How does the array know who's whose parent and whose child?"*

Take one or two guesses, then land it: *"Three formulas. That's the entire trick, and it's what today's session is really about."*

---

## Slide Block A (11–22 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — slides 4–10: Binary Heap definition, array representation, index formulas, operations overview, heapify concept -->
Covers: Binary Heap definition → array representation with root at `arr[0]` → index formulas (`left = 2i+1`, `right = 2i+2`, `parent = (i-1)/2`) → the six operations (heapify, insert, getMax, extractMax, size, empty) → `up_heapify()` vs `down_heapify()`.

**Beats to emphasise**

- **Zero-indexed, always.** Write all three formulas on the board and keep them visible for the whole session — `left = 2i+1`, `right = 2i+2`, `parent = (i-1)/2`. This single set of formulas drives every operation for the rest of the session.
- **`up_heapify()` runs on insert, `down_heapify()` runs on delete.** Name both explicitly and tie each to a direction: up_heapify walks *toward the root*, down_heapify walks *toward the leaves*. Students conflated "heapify" with "just the insert thing" last session — this slide is where that gets corrected.
- The **operations list (slide 7)** is your map for Part 2 — insert, getMax, extractMax, size, empty, all built on the same three index formulas.

**Checkpoint (at 22 min)** — cold-call two students:
> *"Node at index 3. What's its left child index, right child index, and parent index?"*
> **Answer:** left = `2(3)+1 = 7`, right = `2(3)+2 = 8`, parent = `(3-1)/2 = 1`.

---

## ⚡ Activity 1 — Predict-the-Output: Index Arithmetic (22–27 min)

**Format:** Predict-the-Output · **Exposes:** shaky or off-by-one index arithmetic — the one thing every later operation in this session (and course) depends on.

**Setup line (say this):**
> *"I'll give you an index. Before I write the formula's answer, you compute left child, right child, and parent — out loud, no calculators, just the three formulas on the board."*

Use the deck's own array `[40, 25, 20, 10, 5, 30, 15, 35]` (indices 0–7).

**What students do:** For index `1` (value 25): predict left = 3, right = 4, parent = 0. For index `3` (value 10): predict left = 7, right = 8, parent = 1 — then flag that right child index 8 is out of range (array only has indices 0–7), so node 10 has only one child.

**How it surfaces:** If someone answers with `2i` and `2i+1` instead of `2i+1` and `2i+2`, they're using the 1-indexed formulas some textbooks teach. Correct it immediately and re-anchor: *"We are always 0-indexed here — `arr[0]` is the root."*

**Debrief line:**
> *"Every operation in Part 2 — insert, extractMax, heapify — is just these three formulas, applied over and over. Get the formula wrong once and the heap silently breaks; it won't crash, it'll just quietly stop being a heap."*

**Cut rule:** If running late, do index `1` only and state the index-`3` out-of-range case yourself rather than asking students to spot it.

---

## Classroom Quiz (27–32 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Whiteboard Race (32–35 min)

**Why this strategy here:** the index formulas are the entire session's foundation — Part 2 assumes fluency, not just recognition. A timed, competitive drill under mild pressure is a better fluency check than one more calm prediction question, and it surfaces exactly who needs a 1-indexed-formula correction before Part 2's full worked examples depend on speed.

**Run it (3 minutes):**
> *"Two teams, two board halves. I call an index, first team to correctly write all three — left, right, parent — for that index scores a point. Formulas are ON the board the whole time; this is about applying them fast, not memorizing them."*

Call 3-4 indices in quick succession (e.g., 0, 2, 4, 6). Keep score loosely, don't let it eat the clock.

> *"That speed is exactly what Part 2's worked insert and extractMax assume — dozens of these computations back to back. If that felt slow just now, say so, and we'll re-anchor before moving on."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Left child = `2i`, right child = `2i+1` | Some references use 1-indexed heap formulas (`2i`, `2i+1`, `i/2`) | Keep the 0-indexed formulas (`2i+1`, `2i+2`, `(i-1)/2`) on the board all session; Activity 1 and the Whiteboard Race force students to apply them, not just recite them |
| "Heapify" only means the bubble-up step from insertion | The previous session spent more airtime on insertion's bubble-up than on extraction's bubble-down | Name both explicitly on Slide Block A: `up_heapify()` for insert, `down_heapify()` for delete — different directions, different triggers |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz.**
- **The index formulas are the whole session.** If Activity 1 or the Part 1 Wrap reveals the class is shaky on `2i+1`/`2i+2`/`(i-1)/2`, do not proceed into Part 2's worked insert until it's solid — every subsequent slide assumes fluency with it.
- **Contrast with Session 21 explicitly.** Students just spent a session reasoning about heaps with tree pointers; this session's entire cognitive load is *translating* that same logic into array indices. Say out loud, more than once, "same idea, different representation."
