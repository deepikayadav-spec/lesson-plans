# Session 27b — Merge K Sorted Arrays (Part 2 of 2)

**Duration** 23 min · **Topic** Heaps — Merge K Sorted Arrays: Hands-On Practice · **Prerequisite** Session 27a — Merge K Sorted Arrays, Part 1 (brute force, optimal approach, full dry run) · **Session type** Concept lecture

<!-- Split note: continues session-27 (original 50 min) right after the Classroom Quiz. This part is entirely hands-on — the refill-the-row relay, the unequal-row-length generalization discussion, and the exit ticket. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Merge K Sorted Arrays | https://docs.google.com/presentation/d/1Bu6HdP47N4RTkNWi_ud30zeqyyCN79sKaEAAeMY7ACM/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Independently trace the min-heap merge (pop, refill from the same row, handle exhausted rows) without instructor narration. *(APPLYING)*
2. Contrast `O(k² log k²)` / `O(k²)` (brute force) against `O(k² log k)` / `O(k + k²)` (heap), and generalize the algorithm beyond the deck's square `k × k` framing. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 27a (0–5 min)

Say: *"Four quick ones on the optimal approach before you run it yourself."*

**Q1.** What gets seeded into the heap at the very start?
`A` Every element from every row · `B` The first element of each row · `C` The last element of each row · `D` Only the smallest row's first element
→ *Read:* B.

**Q2.** Each heap entry must carry:
`A` Just the value · `B` The value plus its row and column · `C` Just the row · `D` The value plus a timestamp
→ *Read:* B — this was Part 1's key hurdle.

**Q3.** When a popped element's row has no next column, what happens?
`A` The algorithm errors · `B` Nothing gets pushed; the heap simply has one fewer live candidate · `C` The row restarts from column 0 · `D` A placeholder is pushed
→ *Read:* B.

**Q4.** Why is `k² log k` better than `k² log k²` (brute force)?
`A` They're actually the same · `B` `log k² = 2 log k`, so the heap approach is a real improvement, on top of avoiding a separate full sort · `C` `k²` is smaller in the heap approach · `D` It isn't better
→ *Read:* B.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"You've watched it. Now you drive it — and then we stress-test whether the algorithm actually needs the deck's tidy square-matrix setup."*

---

## ⚡ Activity 1 — Live Trace: "Refill the Row" (7–14 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can track which row a popped value came from and correctly identify what refills the heap — the one genuinely new mental model versus Session 26's single-array heap.

**Setup line (say this):**
> *"Two sorted rows: Row 0 = `[4, 8]`, Row 1 = `[2, 6]`. Seed the heap with the first element of each row. After each pop, tell me what gets pushed back in, and from where — before I confirm."*

Run **one pop at a time**:

```
Seed: heap = {(4,(0,0)), (2,(1,0))}
pop 2 (row 1, col 0) → answer=[2] → row 1 has col 1 → push (6,(1,1))    heap = {(4,(0,0)), (6,(1,1))}
pop 4 (row 0, col 0) → answer=[2,4] → row 0 has col 1 → push (8,(0,1))  heap = {(8,(0,1)), (6,(1,1))}
pop 6 (row 1, col 1) → answer=[2,4,6] → row 1 exhausted → push nothing  heap = {(8,(0,1))}
pop 8 (row 0, col 1) → answer=[2,4,6,8] → row 0 exhausted → heap empty
```

**How it surfaces:** After the third pop, ask before revealing: *"Row 1's `6` just got popped — does anything get pushed back in?"* Correct: no — row 1 only had two elements, columns 0 and 1, and column 1 was the last one; there's nothing left in that row to refill with.

**Debrief line:**
> *"Final answer `[2, 4, 6, 8]` — fully merged, fully sorted, and at every step the heap held exactly one live candidate per row that still had elements remaining. Rows don't all finish at the same time, and the algorithm has to handle that gracefully, not assume every row survives equally long."*

**Cut rule:** If running short, do just the first two pops — one live refill is enough to demonstrate the mechanism; the exhausted-row case can be stated rather than relayed.

---

## ⚡ Activity 2 — Predict & Discuss: "What If a Row Is Longer Than the Others?" (14–20 min)

**Format:** Predict-the-Output / Discussion · **Exposes:** whether students understand the algorithm generalizes beyond the "all rows length `k`" square-matrix framing the deck uses, since real inputs won't always be so tidy.

**Setup line (say this):**
> *"The deck's examples are always a `k × k` square — every row the same length. What actually breaks if one row has 10 elements and another has only 2?"*

**What students do:** Discuss for a minute, then share out.

**Answer:** Nothing breaks. The algorithm never assumes rows are equal length — the only check it ever performs is "does this row have a next column after the one I just popped?" A shorter row simply stops contributing candidates sooner and the heap naturally shrinks; a longer row keeps contributing until its own elements run out.

**How it surfaces:** Ask a follow-up: *"So why does the deck always use a square `k × k` matrix?"* Push toward: it's a simplifying assumption for teaching clarity — the real algorithm only cares about "sorted rows, some finite number of them," not equal lengths.

**Debrief line:**
> *"Whenever a problem statement adds a constraint like 'all rows the same length,' ask whether the algorithm actually *needs* that constraint, or whether it's just making the examples easier to draw. Here, the algorithm doesn't need it at all."*

**Cut rule:** If running short, state the generalization directly and skip the open discussion.

---

## Exit Ticket (20–23 min)

> Three sorted rows: `[1, 9]`, `[2, 3]`, `[5]`. Using the min-heap approach, trace every pop and the final merged array.
> **Answer:** Seed: `{(1,(0,0)), (2,(1,0)), (5,(2,0))}`. Pop `1` → push `(9,(0,1))` → `{(2,(1,0)),(5,(2,0)),(9,(0,1))}`. Pop `2` → push `(3,(1,1))` → `{(3,(1,1)),(5,(2,0)),(9,(0,1))}`. Pop `3` → row 1 exhausted → `{(5,(2,0)),(9,(0,1))}`. Pop `5` → row 2 exhausted → `{(9,(0,1))}`. Pop `9` → row 0 exhausted → heap empty. Final: `[1, 2, 3, 5, 9]`. <!-- placement: inferred exit-ticket rows, built with unequal lengths to exercise the exhausted-row case Activity 2 discusses -->

**Homework:** trace the min-heap merge on rows `[3, 7, 20]`, `[4]`, `[1, 5, 6, 8]`, listing every push and pop in order. <!-- placement: inferred — no homework/practice units exist for this course per deviation #2 -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| All rows must be the same length for this algorithm to work | The deck's `k × k` square matrix framing | Activity 2 — reasoning through unequal row lengths and showing nothing in the algorithm depends on equal length |
| A row that runs out early is an error case that needs special handling | "Exhausted row" sounds like a failure state | Activity 1 — treating an exhausted row as an entirely normal, expected outcome: the heap simply shrinks by one candidate |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split right after the Classroom Quiz. Entirely hands-on** — no new slide content, just the two activities and the exit ticket.
- **Activity 1's exhausted-row moment is the load-bearing beat.** Real inputs won't always be tidy squares; don't let that case pass without an explicit pause.
- **Bridge to Session 28 at the close:** "Today's heap tracked one 'best candidate per row.' Next session, the heap tracks 'best candidate per unique element's frequency' — same tool, another shape of problem entirely."
