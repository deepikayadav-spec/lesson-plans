# Session 25b — Convert Min Heap to Max Heap (Part 2 of 2)

**Duration** 26 min · **Topic** Heaps — Full Dry Run, Recursive vs. Iterative · **Prerequisite** Session 25a — Convert Min Heap to Max Heap, Part 1 (approach, first swap) · **Session type** Concept lecture

<!-- Split note: continues session-25 (original 50 min) right after the Classroom Quiz. This part covers the full recursive dry run (including the re-entry into an already-swapped index), the iterative variant, and the O(log n)-vs-O(1) space contrast. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Convert Min Heap to Max Heap | https://docs.google.com/presentation/d/1H6jFQA7yOrTxBtqJVy-daT3NTYzsfBtzRlL47CcoLgA/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Trace the recursive `downHeapify`-based conversion on a given min-heap array, identifying the larger child and each swap. *(APPLYING)*
2. Contrast the recursive and iterative implementations of the same algorithm, and state why the iterative version uses `O(1)` space versus the recursive version's `O(log n)`. *(ANALYZING)*
3. State the overall time complexity, `O(n)`, for both approaches. *(REMEMBERING)*

---

## Warm-Up Poll — Retrieval Practice on Session 25a (0–5 min)

Say: *"Four quick ones on the approach before we run it end to end."*

**Q1.** Conversion starts at:
`A` The root · `B` The last non-leaf node · `C` A random leaf · `D` The first element
→ *Read:* B.

**Q2.** At each node, you compare it against:
`A` Just its left child · `B` Just its right child · `C` Both children, and pick the larger · `D` Its parent
→ *Read:* C — Part 1's Activity 1 takeaway.

**Q3.** True or false: the algorithm needs to know the input started as a min-heap to work correctly.
`A` True · `B` False
→ *Read:* False — it's the same sweep regardless of starting condition.

**Q4.** In Example 2 (`[6, 10, 9, 18, 12, 15, 20]`), what was the first swap?
`A` `arr[0]` and `arr[1]` · `B` `arr[2]` and `arr[6]` (9 and 20) · `C` `arr[2]` and `arr[5]` (9 and 15) · `D` No swap needed
→ *Read:* B.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"You found the first swap. Now finish the sweep — and watch for the one moment where a swap doesn't actually finish the work at that spot."*

---

## Slide Block B (7–18 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — slides 13–44: full recursive dry run, pseudocode, complexity (recursive), then the iterative approach's pseudocode and complexity -->
Covers: full recursive dry run on `[6, 10, 9, 18, 12, 15, 20]` — index 2 (swap with index 6, value 20) → index 1 (swap with index 3, value 18) → index 0 / root (swap with index 2, value 20) → recurse back into index 2 (swap with index 5, value 15) → final array `[20, 18, 15, 10, 12, 6, 9]` → recursive pseudocode (`downHeapify` + `minToMaxHeap`) → recursive complexity: `O(n)` time overall (each `downHeapify` call is `O(log n)`, but summed across all non-leaf nodes the total is `O(n)`, same amortized argument as Heapsort's construction phase), `O(log n)` space (recursion stack) → iterative approach (same logic, expressed as a `while` loop instead of recursive calls) → iterative complexity: `O(n)` time, `O(1)` space.

**Beats to emphasise**

- **Narrate the dry run as one continuous sweep, not four separate examples:** index 2, then index 1, then index 0 (root) — and *then*, because the root's swap disturbed the subtree at index 2 again, the algorithm recurses back down into index 2 a second time. That re-entry into index 2 is the step students most often miss — it's not a bug, it's the point of recursing into "the affected subtree."
- **On complexity:** the recursive version's `O(log n)` space comes purely from the call stack — one stack frame per level of recursive depth. The iterative version reaches the *identical* final array with the *identical* time complexity, but replaces the call stack with loop variables, dropping space to `O(1)`.
- Say explicitly: **the two approaches are not two different algorithms** — they produce the exact same sequence of swaps on the exact same input. The only thing that changes is how the "keep going deeper" step is implemented.

**Checkpoint (at 18 min)** — show hands:
> *"Recursive version: O(log n) space. Iterative version: O(1) space. Why does dropping recursion save space here?"*
> **Answer:** The recursion stack holds one frame per level of the `downHeapify` call chain; the iterative version reuses the same loop variables instead of stacking a new frame for every recursive call.

---

## ⚡ Activity 2 — Dry-Run Relay: Finish the Conversion (18–23 min)

**Format:** Live Dry-Run Relay · **Exposes:** whether students correctly recurse into the *swapped-into* subtree instead of stopping after one swap or moving on to an unrelated index.

**Setup line (say this):**
> *"We just swapped index 2 and index 6 — the array is now 6, 10, 20, 18, 12, 15, 9. I will not move another element until you tell me exactly which index to process next, and why."*

**What students do:** Call out, in order: *"Move to index 1 — parent 10, children at index 3 (value 18) and index 4 (value 12) — 18 is larger, swap index 1 and index 3."* Then: *"Move to index 0, the root — parent 6, children at index 1 (value 18) and index 2 (value 20) — 20 is larger, swap index 0 and index 2."* Then, critically: *"That swap just placed 6 at index 2 — does index 2 need to be checked again?"* (Yes — recurse: parent 6 at index 2, children at index 5 (value 15) and index 6 (value 9) — 15 is larger, swap index 2 and index 5.)

**How it surfaces:** If a student stops after the root swap and declares the array done, stop and ask: *"The value you just moved down to index 2 — does it still satisfy the heap property against *its* children?"* Force the re-check.

**Debrief line:**
> *"A swap doesn't end the work at that index — it just relocates the problem one level down. `downHeapify` isn't finished until the node it swapped into either wins against both its children, or has none left to compare against."*

**Cut rule:** If running short, relay only the index-1 and root-level swaps; state the final recursive re-check into index 2 yourself.

---

## Exit Ticket (23–26 min)

> On paper or in chat: *"Min-heap array: 4, 8, 6 (n = 3). Convert it to a max-heap. Which index do you start at, what swap happens, and what's the final array?"*
> **Answer:** Last non-leaf index = `⌊3/2⌋ - 1 = 0` (the root, value `4`). Its children are `arr[1] = 8` and `arr[2] = 6`; the larger is `8`. Swap `arr[0]` and `arr[1]`. Final array: `[8, 4, 6]`. Index 1 is now a leaf, so no further recursion is needed. <!-- placement: inferred exit-ticket array, built to exercise the same start-index and larger-child logic with a minimal 3-element case -->

**Homework:** re-run the full recursive dry run on `[6, 10, 9, 18, 12, 15, 20]` from memory, then re-derive it using the iterative pseudocode instead. <!-- placement: inferred; no homework/practice-unit table exists for this course -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A swap ends the work at that index | Earlier problems (e.g., Max Heap Validation) had single-step, non-recursive comparisons | Activity 2's relay — force students to re-check the node that was just swapped *into* against its own children before declaring the conversion done |
| The recursive and iterative approaches can produce different results | Different code structure (function calls vs. a loop) looks like a different algorithm | State explicitly, with the dry run as evidence: both approaches perform the identical sequence of swaps on the identical input — only the space complexity differs |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split right after the Classroom Quiz.**
- **The recursive re-entry into an already-processed index (index 2, twice, in the main dry run) is the single hardest idea in this session.** Slow down specifically at that transition in Slide Block B and again in Activity 2 — it's the point students are most likely to silently misunderstand.
- **Don't let "recursive vs. iterative" become a code-syntax lecture.** The complexity contrast (`O(log n)` vs `O(1)` space) is the entire pedagogical point — keep returning to that, not to line-by-line code differences.
- This session's algorithm — sweep from the last non-leaf node to the root, `downHeapify` at each — is the third time students have seen this exact pattern (Heapsort's construction phase, and now heap-type conversion). If a student is still lost here, the gap is likely in Session 23, not this session — consider a 2-minute callback to the Heapsort construction dry run before pressing on.
