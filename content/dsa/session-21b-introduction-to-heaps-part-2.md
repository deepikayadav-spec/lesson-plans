# Session 21b — Introduction to Heaps (Part 2 of 2)

**Duration** 30 min · **Topic** Heaps — Insertion, Extraction & Applications · **Prerequisite** Session 21a — Introduction to Heaps, Part 1 (definition, min/max, properties) · **Session type** Concept lecture

<!-- Split note: continues session-21 (original 60 min) right after the Classroom Quiz. This part covers insertion (bubble up), extractMax (bubble down), getMax, other heap families, and applications — the operational core of the topic. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Introduction to Heaps | https://docs.google.com/presentation/d/17X8ri-v3OXVq0DdZrz0oPcu3hWfNY5EsdYNf1uMqhVU/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Trace the insertion ("bubble up") procedure on a max heap for a given sequence of inserted values. *(APPLYING)*
2. Trace the `extractMax()` ("bubble down") procedure and state why `getMax()` is `O(1)` while `extractMax()` is `O(log n)`. *(APPLYING)*
3. List at least two real-world applications of heaps (priority queues, heap sort, graph algorithms, kth largest/smallest). *(REMEMBERING)*

---

## Warm-Up Poll — Retrieval Practice on Session 21a (0–5 min)

Say: *"Four quick ones on what a heap IS before we learn how to change one."*

**Q1.** What sits at the root of a max heap?
`A` The smallest value · `B` The largest value · `C` A random value · `D` Always the most recently inserted value
→ *Read:* B.

**Q2.** True or false: in a valid max heap, the left child is always smaller than the right child.
`A` True · `B` False
→ *Read:* False — siblings aren't ordered relative to each other, only to their parent. Part 1's Concept Card Sort trick question.

**Q3.** Why is a heap's height always `log(n)`?
`A` It's balanced like a red-black tree · `B` It's always a complete binary tree, so it can never skew · `C` It has a fixed maximum size · `D` It isn't always log(n)
→ *Read:* B.

**Q4.** Which shape rule must every heap satisfy, regardless of min or max?
`A` Every level full, no exceptions · `B` Complete binary tree — full except possibly the last level, filled left to right · `C` Balanced left/right subtree heights · `D` Sorted left-to-right across each level
→ *Read:* B.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"You know what a heap must look like. Now: how a new value gets in without breaking any of that, and how the root gets removed without leaving a hole."*

---

## Slide Block B (7–20 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — slides 10–50: Insertion (bubble up), extractMax (bubble down), getMax -->
Covers: Insertion → worked example (insert 35, then 30, into a 7-node max heap) → insertion complexity → `extractMax()` → worked example (removing root 35, replacing with last element, bubbling down) → `extractMax()` complexity → `getMax()` → `getMax()` complexity.

**Beats to emphasise**

- **Insert always lands in the same place first:** the first vacant slot in the last level — *never* wherever it "should" sort to. Only after landing does it bubble up by comparing against its parent, one level at a time.
- **Walk the two worked inserts (35, then 30) at the board's pace, not the slide's.** There are ~20 slides across the two inserts because each swap gets its own slide — narrate the *pattern* ("compare, swap if bigger, move up, repeat until parent wins or you hit the root") rather than re-deriving arithmetic on every slide.
- **`extractMax()` is a two-part move, not one:** (1) delete the root and pull the *last* element into its place, (2) bubble that element *down*, swapping with whichever child is larger, until it's no longer smaller than either child. Both parts matter — the second part is where students under-deliver if you let this go by fast.
- **`getMax()` costs nothing.** It's `O(1)` — just read `root`. Contrast this hard against `extractMax()`'s `O(log n)`: reading the max is free, *removing* it isn't.

**Checkpoint (at 20 min)** — show hands:
> *"Insertion is O(what), and why?"*
> **Answer:** `O(log n)` — because the heap's height is `log n`, and bubble-up does at most one comparison-and-swap per level on the way up.

---

## ⚡ Activity 2 — Dry-Run Relay: extractMax() (20–25 min)

**Format:** Live Dry-Run Relay · **Exposes:** the "just delete the root, done" misconception — students track step 1 of `extractMax()` (remove root) but drop step 2 (bubble the replacement down through comparisons).

**Setup line (say this):**
> *"We just built this max heap by inserting 35 and 30: root 35, then 30, 20, 25, 8, 15, 13, 10, 17. I'm going to call extractMax() on it. I will not move a single node unless one of you tells me exactly which comparison to make and which swap to do. If you skip a step, I stop."*

**What students do:** Walking through the deck's own worked extractMax example — root 35 removed, last element 17 moved to the root — call out, one step at a time: *"Compare 17 with its children, 30 and 20 — which is bigger?"* (30) *"Swap 17 and 30."* Continue: *"Compare 17 with its new children, 25 and 8 — which is bigger?"* (25) *"Swap."* Continue: *"Compare 17 with its new child, 13 — is a swap needed?"* (No — 17 > 13, done.)

**How it surfaces:** If a student says "just remove 35 and we're done" or tries to skip straight to declaring the new root, stop and ask: *"What's sitting at the root right now, and does it belong there?"* Make them state the comparison before you'll move a node.

**Debrief line:**
> *"`extractMax()` is never a one-step delete. It's delete-and-replace, then bubble the replacement down until it earns its position by being bigger than both children. Skip the bubble-down and your 'heap' is just a tree that used to be one."*

**Cut rule:** If running short, do only the first two bubble-down comparisons (17 vs. 30/20, then 17 vs. 25/8) and state the final step ("17 vs. 13, no swap, done") yourself rather than relaying it. Do not cut the debrief line.

---

## Slide Block C (25–28 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — slides 51–54: other heap families, applications, Key Takeaways -->
Covers: other heap families that exist (Binomial, Fibonacci, Leftist, K-ary — names only, no mechanics) → applications (priority queue implementation, heap sort, graph algorithms, kth largest/smallest) → Key Takeaways.

**Beats to emphasise**

- Deliver the other-heap-family slide as a *map*, not a lecture: "these exist, you'll never implement them by hand in this course, know the names." Do not open a tangent on Fibonacci heaps.
- Land hard on **Applications** — heap sort and kth-largest/smallest are literally the next several sessions in this course. Say that explicitly: *"Sessions 23, 26, and 27 are three of these four bullet points."*

---

## Exit Ticket (28–30 min)

> On paper or in chat: *"This is a max heap: root 25, children 20 and 18, and 20's children are 10 and 8. I insert 30. Which nodes get compared against 30, in order, and which get swapped?"*
> **Answer:** 30 lands as the next left-to-right vacant slot (as 20's left child, replacing where 10 was — i.e., final shape has 30 where 10 was). Compare 30 vs. parent 20 → 30 > 20, swap. Compare 30 vs. parent 25 → 30 > 25, swap. 30 is now root; stop, no parent left to compare. <!-- placement: inferred exit-ticket scenario, built from the same insertion mechanics as the deck's worked example -->

**Homework:** re-attempt today's two dry runs (insertion of 35 & 30, extraction of 35) from memory, without looking at the slides. <!-- placement: inferred; no homework/practice-unit table exists for this course -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A new element gets inserted wherever it "should" sort to | BST insertion habit — search down to find the correct spot | Insertion always lands in the last level's first vacant slot; the sorting work happens *after*, via bubble-up |
| `extractMax()` is just "delete the root" | Attention naturally lands on the dramatic step (removing the max) and drops the quieter one | Activity 2's dry-run relay — force the bubble-down comparisons to be stated aloud, step by step |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz.**
- **Pacing risk:** the insert-35-then-30 walkthrough spans roughly 20 slides for what is really two repeated steps ("compare and swap while bigger than parent"). Narrate the pattern once explicitly, then move through the remaining slides at a brisk, confirming pace — don't re-derive the comparison logic from scratch on every slide.
- Have the two worked examples (insert 35 & 30; extractMax on the resulting heap) sketched on the board or a handout before class — the numbers repeat across many slides and are easy for students to lose track of if they're copying from a fast-moving screen.
- **Session 22 opens by rebuilding these same operations on an array** — the array representation of a heap and every problem after it assumes fluency with bubble-up/bubble-down. If Activity 2's dry run went badly, flag it for a quick re-anchor at the start of Session 22.
