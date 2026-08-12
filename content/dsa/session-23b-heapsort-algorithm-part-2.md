# Session 23b — Heapsort Algorithm (Part 2 of 2)

**Duration** 24 min · **Topic** Heaps — Sorting Phase & Overall Complexity · **Prerequisite** Session 23a — Heapsort Algorithm, Part 1 (two-phase framing, construction dry run) · **Session type** Concept lecture

<!-- Split note: continues session-23 (original 50 min) right after the Classroom Quiz. This part covers the sorting phase (repeated extraction, in-place), overall complexity, and the dry-run relay on one full extraction. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Heapsort Algorithm | https://docs.google.com/presentation/d/10rgo7gButuNwI0MsSYl6TOrFvKOci7gKaRJDso0V35A/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Trace the sorting phase — swap root with the last live element, shrink the heap, `down_heapify` from the root — until the array is fully sorted. *(APPLYING)*
2. State Heapsort's overall time complexity `O(n log n)` and auxiliary space complexity `O(1)`. *(REMEMBERING)*

---

## Warm-Up Poll — Retrieval Practice on Session 23a (0–5 min)

Say: *"Four quick ones on the construction phase before we sort."*

**Q1.** Heapsort has two phases. Name them.
`A` Search, then sort · `B` Construction, then sorting · `C` Insert, then delete · `D` Compare, then swap
→ *Read:* B.

**Q2.** Construction starts at:
`A` The root · `B` The last non-leaf node · `C` A random leaf · `D` The last element in the array
→ *Read:* B.

**Q3.** Why is construction `O(n)` and not `O(n log n)`?
`A` It skips most of the array · `B` Most nodes are near the leaves and need little bubble-down work; only a few near the root move far · `C` It uses a different data structure · `D` It isn't actually O(n)
→ *Read:* B.

**Q4.** After construction on `[3, 9, 2, 1, 4, 5, 7]`, what's the resulting max heap?
`A` `[9, 4, 7, 1, 3, 5, 2]` · `B` `[3, 9, 2, 1, 4, 5, 7]` unchanged · `C` `[1, 2, 3, 4, 5, 7, 9]` · `D` `[9, 7, 5, 4, 3, 2, 1]`
→ *Read:* A — Part 1's own worked result.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"You have a valid max heap. Watch what happens when you call extractMax() on it, over and over, and park each result somewhere clever."*

---

## Slide Block B (7–18 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — slides 26–58: the sorting phase dry run (repeated swap-root-with-last, shrink, down_heapify) through to a fully sorted array, overall complexity, Key Takeaways -->
Covers: sorting-phase mechanics — swap the root (current maximum) with the last *live* element of the heap, shrink `heapSize` by one, `down_heapify` from the root to restore heap order, repeat — worked through completely on the max heap `[9, 4, 7, 1, 3, 5, 2]` until the array reads `[1, 2, 3, 4, 5, 7, 9]` → overall time complexity `O(n log n)`, auxiliary space `O(1)` → Key Takeaways.

**Beats to emphasise**

- **Say the loop invariant out loud, once, before diving into slides:** "swap root with the last live slot, shrink the heap by one, `down_heapify` the new root, repeat until one element is left." Every one of the ~30 remaining dry-run slides is just this loop, one iteration per slide-group — narrate the pattern, don't re-derive it each time.
- **The "sorted" region is everything past the current `heapSize`.** Once an element is swapped to the end and the heap shrinks past it, that position is *frozen* — it's never touched again. This is what makes the sort happen in place with zero extra array.
- **Contrast the complexity numbers explicitly:** construction alone is `O(n)` (Part 1), but the sorting phase adds `O(n log n)` on top (n extractions, each `O(log n)`) — so the *overall* algorithm is `O(n log n)`, dominated by the sorting phase, not the construction phase.

**Checkpoint (at 18 min)** — show hands:
> *"Heapsort's auxiliary space complexity — who says O(n), who says O(1)?"*
> **Answer:** `O(1)`. Everything happens by swapping elements within the original array; no second array is ever allocated.

---

## ⚡ Activity 2 — Dry-Run Relay: One Full Extraction (18–22 min)

**Format:** Live Dry-Run Relay · **Exposes:** treating the sorting phase as something new, instead of recognising it as `extractMax()` called on a shrinking heap.

**Setup line (say this):**
> *"We just built this max heap: 9, 4, 7, 1, 3, 5, 2. I'm going to run exactly one iteration of the sorting phase. I move nothing until you tell me the swap, the new heap size, and the down_heapify comparison."*

**What students do:** Call out, in order: *"Swap index 0 (value 9) with index 6 (value 2) — the last live slot."* → *"heapSize drops from 7 to 6 — index 6 is now frozen, sorted."* → *"down_heapify from the new root, value 2: compare its children at index 1 (value 4) and index 2 (value 7) — 7 is bigger, swap."* → *"Now check the new position's child — is a further swap needed?"*

**How it surfaces:** If a student tries to compare the new root against the *frozen* index-6 slot, stop and ask: *"Is that slot still part of the heap, or is it done?"* — reinforcing the `heapSize` boundary from Slide Block B.

**Debrief line:**
> *"That's it. That's the entire sorting phase — extractMax(), the exact operation from Session 22, called n times, with the removed maximum parked at the current heap's last slot each time instead of thrown away. Heapsort isn't a new algorithm bolted onto a heap — it's the heap's own operation, reused."*

**Cut rule:** If running short, relay only the swap and heap-size shrink; state the `down_heapify` comparison yourself.

---

## Exit Ticket (22–24 min)

> On paper or in chat: *"In your own words: why does Heapsort start construction from the last non-leaf node instead of the root, and why is the overall algorithm O(n log n) instead of O(n)?"*
> **Answer:** Starting from the last non-leaf node means most of the work happens near the (cheap) leaves, making construction `O(n)`. But the *sorting* phase still calls the equivalent of `extractMax()` once per element, each costing `O(log n)`, so the overall algorithm is dominated by that phase: `O(n log n)`. <!-- placement: inferred exit-ticket question, built directly from the two complexity beats emphasised in the session -->

**Homework:** re-run the full dry run — construction and sorting — on `[3, 9, 2, 1, 4, 5, 7]` from memory. <!-- placement: inferred; no homework/practice-unit table exists for this course -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Heapsort needs a second array to hold the sorted output | Other sorts they may know (merge sort) use auxiliary arrays | Point at the `heapSize` shrinking each iteration — the "sorted" region is just the tail of the *same* array, frozen in place |
| Once root and last element are swapped, both positions are still "in the heap" together | The swap happens visually within one array, with no visible boundary marker | Emphasise the `heapSize` variable explicitly — anything at or past `heapSize` is finalized and never revisited |
| Heapsort could just as well build its heap by inserting elements one at a time | That's a valid *alternative* construction method, and it's easy to conflate with the one taught in Part 1 | Name it directly: n one-at-a-time insertions would cost `O(n log n)` for construction alone — the last-non-leaf-node method taught in Part 1 is chosen specifically because it's `O(n)` |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split right after the Classroom Quiz.**
- **Pacing risk is highest in the sorting-phase dry run** (slides 27–56) — it's roughly 30 slides re-running the same four-step loop on a shrinking array. State the loop invariant once, explicitly, before starting, and move through the slides confirming rather than re-teaching.
- Keep both complexity numbers on the board simultaneously by the end of class: construction `O(n)` (Part 1), overall `O(n log n)`, space `O(1)`. Students frequently misquote Heapsort as `O(n)` overall because they only remember the construction phase's complexity.
