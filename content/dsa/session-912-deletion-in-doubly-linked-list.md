# Session 12 — Deletion in Doubly Linked List

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Doubly Linked List — Deletion (Head, Tail, Kth Position) · **Prerequisite** Session 11 — Insertion in Doubly Linked List
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Doubly Linked List - Traversal, Insertion, Deletion (deletion half) | https://docs.google.com/presentation/d/1CtyEsYixyAXlaQ-wZUaqsxFZx4XQF1JPPIJ18LZ9YKg/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Implement deletion at the head, tail, and Kth position of a doubly linked list. *(APPLYING)*
2. Explain why `delete_kth` branches into three cases instead of using one general relink formula. *(ANALYZING)*
3. Identify the exact position (head, middle, or tail) that causes a null-pointer crash when boundary checks are removed. *(ANALYZING)*
4. State that a deleted node's neighbour's outward pointer must be explicitly set to `NULL`, not assumed. *(UNDERSTANDING)*
5. Compare the time complexity of each DLL deletion position to its Session 9 singly-linked-list counterpart. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 11 (3–7 min) · ALS: Polling

5 questions on **Session 11 (Insertion in Doubly Linked List)**. ~45 s each, project the distribution, never name individuals.

**Q1.** How many pointer updates does inserting before the Kth node of a DLL require?
`A` 1 · `B` 2 · `C` 3 · `D` 4
→ **D.**

**Q2.** What's the one extra step DLL insert-at-head needs beyond a singly linked list's insert-at-head?
`A` Sorting the list first · `B` Setting the old head's `prev` to point at the new node · `C` Checking if the list is circular · `D` Nothing extra is needed
→ **B.**

**Q3.** If a Kth-position insertion updates all `next` pointers correctly but misses one `prev` update, what's true?
`A` Nothing works · `B` Forward traversal works, backward traversal is broken near the insertion point · `C` Both directions break · `D` It crashes immediately
→ **B.**

**Q4.** What's the time complexity of inserting at the tail of a DLL with only a head pointer?
`A` O(1) · `B` O(n) · `C` O(log n) · `D` O(k)
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about DLL insertion?
`A` All three positions are O(1) space · `B` Insert-at-tail requires walking from head · `C` Insert-before-Kth touches exactly two existing nodes' pointers · `D` A DLL has a stored tail reference, making tail access O(1)
→ **A, B, C.** *(D is false — no stored tail reference exists in what's been built so far; reaching the tail still requires traversal.)*

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–9 min)

Put this on the board: `NULL ← 10 ⇄ 20 ⇄ 30 → NULL`.

> *"I delete node 20 — the middle one. Two neighbours need to be rewired, not just one. Who can name both?"*

Let the room land on: `10`'s `next` must now point at `30`, and `30`'s `prev` must now point at `10`.

> *"Two rewires for one deletion in the middle. But watch what happens if I ask you to delete node 10 instead — the head. `back` doesn't exist. There's nothing before the head to rewire. That single missing neighbour is where today's entire session lives — the general rule breaks exactly at the two ends, and the real code has to know it."*

---

## Slide Block C (9–19 min) — DELIVER SLIDES AS-IS

Covers: Deletion in a Doubly Linked List — the three types (head, tail, Kth position) — each with problem statement, dry-run diagram, C++ code, and complexity; closing with the Deletion Complexity Summary table.

**Beats to emphasise**

- **Delete head**: handle empty-list and single-node cases first, then `head = head->next` followed by the DLL-specific extra step, `head->prev = nullptr`, before deleting the old head. O(1).
- **Delete tail**: same empty/single-node guards, then walk to the second-to-last node, set both `temp->next = nullptr` and `tail->prev = nullptr` before deleting the old tail. O(n).
- **Delete Kth node**: the one with real branching complexity — walk this one slowly. After finding `temp` at position `k`, save `back = temp->prev` and `front = temp->next`, then branch three ways: **both null** (only node in the list — delete and return `nullptr`), **`back` null** (`temp` is the head — hand off to `delete_head`), **`front` null** (`temp` is the tail — hand off to `delete_tail`), and only in the **true middle case** does the general relink formula run: `back->next = front; front->prev = back`.
- Emphasise *why* the branching exists: the general formula assumes both neighbours are real nodes. Head and tail are exactly the two positions where that assumption breaks.
- Close with the **Complexity Summary**: head O(1)/O(1), tail O(N)/O(1), Kth O(k)/O(1) — identical shape to insertion (Session 11).

**Checkpoint (at 19 min)** — cold-call one student:
> *"In `delete_kth`, why does the code branch into three separate cases instead of using one general formula?"*
> **Answer:** The general formula `back->next = front; front->prev = back` assumes both neighbours exist. If the node being deleted is the head, `back` is null; if it's the tail, `front` is null; if it's the only node, both are null. Each of those would crash the general formula, so they're handed off to `delete_head` / `delete_tail` instead of forcing one formula to cover every case.

---

## ⚡ ALS Activity 1 — Silent Diagnose, Named Reveal: Delete-Kth Without Boundary Checks (19–27 min)

**ALS format:** Silent Diagnose, Named Reveal — exposes the null-pointer crash that happens when the general "relink neighbours" logic runs on a node at the head or tail without the deck's own boundary branching. Chosen right after Slide Block C because the three-way branch is easy to nod along to and easy to forget the moment it's not enforced — this is where that gets tested directly.

**Setup line:**
> *"This is `delete_kth`, except I deleted the three boundary `if` branches and left only the general case. Tell me exactly which position — head, middle, or tail — makes this crash, and why."*

```cpp
// deck's boundary branches removed:
// if (back == nullptr && front == nullptr) { delete temp; return nullptr; }
// else if (back == nullptr) return delete_head(head);
// else if (front == nullptr) return delete_tail(head);
Node* back = temp->prev;
Node* front = temp->next;
back->next = front;
front->prev = back;
delete temp;
return head;
```

Trace `k = 0` (deleting the head) mentally: `back = temp->prev` is `nullptr` because the head has no previous node, so `back->next` dereferences a null pointer on the very next line.

**How it surfaces:** If someone says "it just doesn't delete anything" — no, it crashes. A null-pointer dereference in C++ is not a silent no-op.

**Debrief line:**
> *"The general relink formula only works when the node being deleted has neighbours on both sides. The head and tail are exactly the nodes that don't — which is why the real code hands those two cases off to `delete_head` and `delete_tail` instead of trying to force one formula to cover everything."*

**Cut rule:** Skip tracing `k = 0` by hand and just ask "which position breaks this — head, middle, or tail?" as a show of hands, then reveal why.

---

## ⚡ ALS Activity 2 — Predict the Output: The Stale Pointer (27–36 min)

**ALS format:** Predict-the-Output — a fast, precise check of whether the `prev`/`next` discipline from Sessions 10-11 has actually stuck. Chosen as the closing activity because it's the fastest possible test of the exact misconception this three-session DLL block exists to prevent — a pointer left silently stale after a deletion.

**Setup line:**
> *"Doubly linked list: `NULL ← 10 ⇄ 20 ⇄ 30 → NULL`. I delete the head. One line, everyone: what does node 20's `prev` pointer equal now?"*

Call out the answer — `NULL`.

**How it surfaces:** If someone says "10" (the old head), that's the exact stale-pointer bug — point at it directly: *"10 was just deleted. You cannot point at deleted memory."*

**Debrief line:**
> *"That's the one line every DLL deletion has to get right — the new boundary node's outward-facing pointer must become `NULL`, not just keep pointing at whatever used to be there."*

**Second round, if time allows:** *"Same list. I delete the tail (30) instead. What does node 20's `next` pointer equal now?"* — **Answer: `NULL`.** Same lesson, opposite end.

**Cut rule:** Run the first round only; skip the second round if short on time.

---

## Classroom Quiz (36–41 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering the three DLL deletion positions, the delete-kth branching logic, and stale-pointer edge cases. -->

---

## Exit Ticket + Homework (41–48 min)

**Exit ticket** (~1 min) — on paper before anyone leaves:

> A doubly linked list is `10 ⇄ 20 ⇄ 30`, with `NULL` on both outer ends. You delete the tail (30). What is node 20's `next` pointer immediately after?
> **Answer:** `NULL` — 20 is now the tail, and its outward-facing pointer must be explicitly set, not left pointing at the deleted node.

**Homework:** Re-attempt today's three deletion dry runs from memory — head, tail, and Kth position, including all three branches of `delete_kth` — on a DLL of your own choosing.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `delete_kth` can use the same general relink formula regardless of position | The formula looks clean and "the same" for every node in the middle | ALS Activity 1 — running the general formula on `k = 0` and hitting the null-pointer crash directly |
| After deleting a node, the neighbour's old pointer to it will resolve to `NULL` automatically | Deleted nodes disappear from the diagram, so it *looks* automatic | ALS Activity 2 — forcing the explicit statement that the new boundary node's pointer must be *set* to `NULL`, not assumed |
| DLL deletion at the head costs more than a singly linked list's, since there's an extra pointer to clear | "More pointers" intuition, same family as Session 11's misconception | Slide Block C — still O(1), one more constant-time line |
| The three-way branch in `delete_kth` is defensive over-engineering | The middle-case formula "looks like it should just work everywhere" | ALS Activity 1 — the crash is real and immediate, not hypothetical |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Split out from the original 60-min "Session 40 — Doubly Linked List - Traversal, Insertion, Deletion" — see `sem-3-sequence.md`. Session 10 covers construction, Session 11 covers insertion.
- **Two ALS activities this session, both carried over from the original combined session:** Activity 1 is Silent Diagnose → Named Reveal (delete-Kth without boundary checks), Activity 2 is Predict-the-Output (the stale pointer). Both were already deletion-specific in the original file and map directly here.
- **This is session 12 of the Sem-3 sequence** (see `sem-3-sequence.md`) — the last of three sessions replacing the original combined DLL session (10: Introduction, 11: Insertion, 12: Deletion).
- **Do not rush Slide Block C to protect ALS Activity time.** `delete_kth`'s three-way branching is the densest single idea in this session — if it isn't clear before ALS Activity 1, that activity's crash will look arbitrary rather than inevitable.
- **This is the sixth linked-list session in a row** (Sessions 7-12). If energy is flagging, lean on the direct comparisons already built into this session's Learning Objectives and Slide Block (same complexity shapes as Sessions 8-9, one new pointer) rather than introducing new framing from scratch. Session 13 (Circular Linked List) is genuinely new territory again.
