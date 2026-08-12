# Session 25a — Convert Min Heap to Max Heap (Part 1 of 2)

**Duration** 30 min · **Topic** Heaps — Conversion: Approach & First Swap · **Prerequisite** Max Heap Validation (Session 24) · **Session type** Concept lecture

<!-- Split note: original session-25 ran 50 min. Split right after the Classroom Quiz. Part 1 covers the problem statement, the recursive approach overview, and the "find the larger child" prediction activity. Part 2 (session-25b) covers the full recursive dry run, the iterative variant, and their complexity contrast. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Convert Min Heap to Max Heap | https://docs.google.com/presentation/d/1H6jFQA7yOrTxBtqJVy-daT3NTYzsfBtzRlL47CcoLgA/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the problem: given an array that's a valid min-heap, rearrange it in place into a valid max-heap. *(REMEMBERING)*
2. Explain why the conversion starts at the last non-leaf node and moves toward the root, using `downHeapify` at each step. *(UNDERSTANDING)*

*(The full recursive dry run and the recursive-vs-iterative complexity contrast are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 24: Max Heap Validation (0–6 min)

Say: *"Seven on last session's validation problem before we move to fixing a heap instead of just checking one."*

**Q1.** Max Heap Validation checks which indices?
`A` All indices `0` to `n-1` · `B` Only non-leaf nodes, `0` to `n/2 - 1` · `C` Only the root · `D` Only leaf nodes
→ **Answer:** B.

**Q2.** What triggers an immediate `false` return?
`A` Any child value equal to its parent · `B` Any child value greater than its parent · `C` The array being unsorted · `D` The array having odd length
→ **Answer:** B.

**Q3.** *(MSQ — pick 2)* Which are true about the validation algorithm?
`A` It stops at the first violation found · `B` It counts all violations before returning · `C` It needs bounds checks because a node may have 0, 1, or 2 children · `D` It always checks both children even when out of bounds
→ **Answer:** A and C.

**Q4.** Time complexity of Max Heap Validation?
`A` `O(log n)` · `B` `O(n)` · `C` `O(n log n)` · `D` `O(1)`
→ **Answer:** B.

**Q5.** Space complexity of Max Heap Validation?
`A` `O(n)` · `B` `O(log n)` · `C` `O(1)` · `D` `O(n log n)`
→ **Answer:** C.

**Q6.** In `[60, 40, 20, 10, 45, 35, 15, 5, 25]`, which index pair caused the `false` result?
`A` `arr[0]` and `arr[1]` · `B` `arr[1]` and `arr[4]` · `C` `arr[2]` and `arr[5]` · `D` `arr[3]` and `arr[7]`
→ **Answer:** B.

**Q7.** True or False: leaves need checking too, since they might have "grandchildren" violations.
`A` True · `B` False
→ **Answer:** B — leaves have no children by definition, so there is nothing below them to violate.

**Running it** — poll tool, ~35–40 s/question. Total 6 min including reads.

---

## Hook (6–9 min)

Say: *"Last session you checked whether an array was a valid max heap. Today's twist: someone hands you an array that's already a perfectly valid heap — just the wrong kind. It's a min heap, and you need a max heap, same elements, no rebuilding from scratch. What do you actually have to change?"*

Take a guess or two, then: *"Almost nothing about the *shape* — it's still a complete binary tree. What has to change is which value ends up on top at every parent-child pair. That's the entire problem."*

---

## Slide Block A (9–17 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — slides 4–12: Problem Statement, Examples 1–2, Recursive Approach overview -->
Covers: problem statement (convert a min-heap array of `n` integers into a max-heap) → Example 1: `[5, 7, 8, 14, 9, 10]` → `[14, 9, 10, 7, 5, 8]` → Example 2: `[6, 10, 9, 18, 12, 15, 20]` → `[20, 18, 15, 10, 12, 6, 9]` → recursive approach overview (start at the last non-leaf node, move upward toward the root; at each node, find the largest of the node and its children; if it isn't the current node, swap and recurse into the affected subtree).

**Beats to emphasise**

- **This is the exact same `downHeapify` procedure you saw building a heap in Heapsort (Session 23) — except the input here is already a valid heap of the *other* kind, not a raw unsorted array.** Say this connection out loud immediately; it's the fastest way into the algorithm.
- The **"find the largest" step compares the node against *both* children, not just one** — this generalizes the max-heap `down_heapify` idea from Session 22, just applied uniformly across the whole array from the bottom up.

**Checkpoint (at 17 min)** — cold-call two students:
> *"This procedure — start at the last non-leaf node, downHeapify, move toward the root — sounds identical to something from two sessions ago. What's actually different here?"*
> **Answer:** Nothing about the mechanism is different — the algorithm doesn't know or care whether the input started as a min-heap, a max-heap, or a random array. The only difference is what you're told about the starting array; the same bottom-up `downHeapify` sweep restores max-heap order regardless.

---

## ⚡ Activity 1 — Predict-the-Output: First Swap (17–24 min)

**Format:** Predict-the-Output · **Exposes:** whether students can correctly identify the starting index and the *larger* of two children before the deck confirms it — a common failure point is defaulting to "the left child" out of habit.

**Setup line (say this):**
> *"Min-heap array: 6, 10, 9, 18, 12, 15, 20 — that's Example 2. Before I show the deck's answer: which index does the conversion start at, and what swaps with what, first?"*

**What students do:** Compute the last non-leaf index (`⌊7/2⌋ - 1 = 2`, value `9`), identify its children at indices 5 and 6 (values `15` and `20`), and correctly predict that `20` (index 6) is the larger — so `arr[2]` and `arr[6]` swap.

**How it surfaces:** If someone defaults to comparing only the left child (`15`) and swaps `arr[2]` with `arr[5]` instead, stop and ask: *"You have two children — did you check which one is actually bigger?"*

**Debrief line:**
> *"This step always compares both children and picks the larger one before doing anything. Skip that comparison and you can swap with the wrong child — the array stops looking wrong immediately, but the heap property downstream is still broken."*

**Cut rule:** If running late, just have students name the starting index and skip the child-comparison prediction — state it yourself.

---

## Classroom Quiz (24–29 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Turn-and-Teach (29–30 min)

**Why this strategy here:** the whole approach rests on one rule — start at the last non-leaf node, always compare both children before swapping. A fast paired explanation catches the "defaults to left child" habit Activity 1 already flagged, before Part 2's longer dry run assumes it's gone.

**Run it (60 seconds):**
> *"Turn to your partner. In one breath: where does the conversion start, and what do you check before every swap? Go."*

> *"Part 2 runs that rule all the way through a full array — and there's one twist: sometimes a swap isn't the end of the work at that spot."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Converting min-heap to max-heap just means reversing or re-sorting the array | Heaps "feel" ordered, so flipping the order seems intuitive | Point out the final array isn't a simple reversal of the input — Part 2's dry run shows the actual swaps come from comparing each parent against its real children, not from sorting |
| The algorithm needs to know the input was a min-heap to work correctly | It's introduced as "converting a min-heap," which sounds special-cased | State plainly: the exact same `downHeapify`-from-last-non-leaf-node sweep works on *any* array — min-heap, max-heap, or fully random. The starting condition is flavor, not a precondition the algorithm checks |
| The larger child is always the left child by default | Left-first habit from reading arrays left to right | Activity 1 — force students to compare both children explicitly before naming the swap target |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split right after the Classroom Quiz.**
- Part 2 (session-25b) reuses Example 2's array (`[6, 10, 9, 18, 12, 15, 20]`) and this part's first swap directly — no need to re-derive it.
