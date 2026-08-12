# Session 23a — Heapsort Algorithm (Part 1 of 2)

**Duration** 33 min · **Topic** Heaps — Heap Construction Phase · **Prerequisite** Implementation of Binary Heap (Session 22) · **Session type** Concept lecture

<!-- Split note: original session-23 ran 50 min. Split right after the Classroom Quiz. Part 1 covers Heapsort's two-phase framing and the full heap-construction dry run (why it starts at the last non-leaf node, and why that's O(n)). Part 2 (session-23b) covers the sorting phase — repeated extraction — and overall complexity. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Heapsort Algorithm | https://docs.google.com/presentation/d/10rgo7gButuNwI0MsSYl6TOrFvKOci7gKaRJDso0V35A/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Describe Heapsort as two phases — heap construction, then repeated extraction — and state which heap type (max/min) produces ascending vs. descending order. *(UNDERSTANDING)*
2. Explain why building a heap from an unsorted array starts at the *last non-leaf node*, not the root, and why this makes construction `O(n)` rather than `O(n log n)`. *(UNDERSTANDING)*
3. Trace the max-heap construction phase on a given unsorted array, computing the last-non-leaf index and each `down_heapify` swap. *(APPLYING)*

*(The sorting phase and overall complexity are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 22: Implementation of Binary Heap (0–6 min)

Say: *"Eight on the array-based heap operations from last session. Heapsort today is built entirely out of one of those operations, so this needs to be automatic."*

**Q1.** Left child index formula for a node at index `i`?
`A` `i*2` · `B` `2i+1` · `C` `2i-1` · `D` `i/2`
→ **Answer:** B.

**Q2.** Parent index formula for a node at index `i`?
`A` `i/2` · `B` `(i-1)/2` · `C` `2i` · `D` `i-1`
→ **Answer:** B.

**Q3.** *(MSQ — pick 2)* Which are true of heapify direction?
`A` `up_heapify` is used on insert · `B` `up_heapify` moves toward the leaves · `C` `down_heapify` is used when removing an element · `D` `down_heapify` moves toward the root
→ **Answer:** A and C.

**Q4.** Time complexity of `insert()` on an array-based binary heap?
`A` `O(1)` · `B` `O(log n)` · `C` `O(n)` · `D` `O(n log n)`
→ **Answer:** B.

**Q5.** Time complexity of `getMax()`?
`A` `O(1)` · `B` `O(log n)` · `C` `O(n)` · `D` `O(n log n)`
→ **Answer:** A.

**Q6.** During `extractMax()`, what replaces the removed root?
`A` The smallest leaf · `B` The last element in the heap · `C` The left child · `D` Nothing — it stays empty until the next insert
→ **Answer:** B. *Read:* This is exactly the step Part 2's sorting phase reuses today — flag it.

**Q7.** `size()` and `empty()` are both what complexity?
`A` `O(log n)` · `B` `O(n)` · `C` `O(1)` · `D` `O(n log n)`
→ **Answer:** C.

**Q8.** True or False: `capacity` and `size` are the same variable.
`A` True · `B` False
→ **Answer:** B — `capacity` is the array's fixed length, `size` is the current element count.

**Running it** — poll tool, ~40 s/question. Total 6 min including reads.

---

## Hook (6–9 min)

Say: *"You now have a fully working max heap — insert, extractMax, all in O(log n). Here's a question I want you to actually think about, not answer instantly: what happens if you just call extractMax() over and over, n times in a row, and write down what comes out each time?"*

Let a few guesses land. Someone will say "the elements in decreasing order."

> *"Exactly. You just described a sorting algorithm using nothing but a tool you already built last session. That's Heapsort. No new data structure, no new operation — just extractMax(), called repeatedly, with one clever trick for where you park each result."*

---

## Slide Block A (9–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — slides 4–25: Heapsort introduction, explanation of the two phases, full Max Heap Construction dry run on [3, 9, 2, 1, 4, 5, 7], construction complexity -->
Covers: Heapsort definition (two phases: heap construction, then sorting) → worked example array `[3, 9, 2, 1, 4, 5, 7]` → full max-heap construction dry run, starting from the *last non-leaf node* (index `⌊7/2⌋ - 1 = 2`) and working backward to the root, `down_heapify`-ing at each node → resulting max heap `[9, 4, 7, 1, 3, 5, 2]` → construction complexity `O(n)`.

**Beats to emphasise**

- **Two phases, say both names every time:** "heap construction" builds a max heap (for ascending output) or min heap (for descending) from the raw array; "sorting" then repeatedly extracts the root and shrinks the heap. Students who only remember "heapsort uses a heap" miss that it's genuinely a two-stage algorithm.
- **Construction starts at the last non-leaf node, not the root.** This is the single most counter-intuitive beat in the whole session — walk through *why*: leaf nodes trivially satisfy the heap property alone, so there's nothing to fix there. Work backward from the last internal node toward the root, `down_heapify`-ing each one.
- **On the O(n) construction complexity (slide 25):** most nodes live near the leaves and need very little bubble-down work; only a few nodes near the root can move the full height. This is why building a heap this way is `O(n)`, not the `O(n log n)` you'd get from `n` naive insertions.

**Checkpoint (at 19 min)** — cold-call two students:
> *"Array has 7 elements. What's the index of the last non-leaf node, and why do we start there?"*
> **Answer:** Index `⌊7/2⌋ - 1 = 2`. We start there because indices after it are leaves, which trivially satisfy the heap property with no children to compare against.

---

## ⚡ Activity 1 — Predict-the-Output: Where Does Construction Start? (19–26 min)

**Format:** Predict-the-Output · **Exposes:** the instinct to start heapifying from the root, which is how insertion works but not how *construction from a raw array* works.

**Setup line (say this):**
> *"Here's the unsorted array again: 3, 9, 2, 1, 4, 5, 7. Before I show you the deck's answer — which index do we start heapifying from, and what's the very first swap?"*

**What students do:** Compute the last non-leaf index (`⌊7/2⌋ - 1 = 2`, value `2`), identify its children at indices 5 and 6 (values `5` and `7`), and predict the swap: `7 > 2`, so swap index 2 and index 6.

**How it surfaces:** If someone starts from index 0 (the root, value `3`) instead, stop and ask: *"Does the root have a heap-property violation to fix yet, or does something below it need fixing first?"* Point back at the last-non-leaf logic from Slide Block A.

**Debrief line:**
> *"You never build a heap top-down from raw data — you fix the bottom first, then work up. That single choice is the entire reason construction is O(n) instead of O(n log n)."*

**Cut rule:** If running late, skip the swap prediction and just confirm the starting index verbally.

---

## Classroom Quiz (26–31 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Peer Quiz Swap (31–33 min)

**Why this strategy here:** the construction phase is done and tested from the instructor side (checkpoint, Activity 1, quiz). Having students write the next question, for a partner, tests whether they can generate a valid construction scenario — not just answer one — which is a stronger proof of understanding heading into Part 2.

**Run it (2 minutes):**
> *"Thirty seconds: write one question for your partner about today's construction phase — a small unsorted array, and ask them for the starting index. Swap, answer, check each other."*

Take one pair's exchange out loud as a class check.

> *"You can now find where a heap sweep starts. Part 2 is what happens once the heap is built — turning it into a fully sorted array, one extraction at a time."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Heap construction starts at the root and heapifies downward from there | That's how *insertion* works (bubble up from a leaf), so root-first feels consistent | Activity 1 — force the last-non-leaf-index computation before revealing the deck's answer |
| Building the heap is `O(n log n)` (reasoning: "n elements, each takes log n") | Naive generalisation from the fact that a single `down_heapify` call is `O(log n)` | Slide 25's explanation — most nodes are near the leaves and do very little work; only a few near the root move far |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split right after the Classroom Quiz.**
- **This session is a payoff session, not a new-concept session** — everything here is `extractMax()` and `down_heapify()` from Session 22, applied in a loop. Lean on that framing to keep energy up; students should feel like they already know this.
- Part 2 (session-23b) reuses the constructed heap `[9, 4, 7, 1, 3, 5, 2]` directly — no need to rebuild it.
