# Session 9 — Deletion in Linked List

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Linked List — Deletion (Head, Tail, Kth Position, Value x) · **Prerequisite** Session 8 — Insertion in Linked List
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Insertion, Deletion (deletion half) | https://docs.google.com/presentation/d/1q6eByMnLCZNPIFu9IMBzrmpZbQ1GlJ4feddjOeakiTU/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. List the four deletion positions covered for a singly linked list — head, tail, Kth position, node with value `x`. *(REMEMBERING)*
2. Explain why deleting at the head is O(1) while deleting at the tail is O(n) on a singly linked list. *(UNDERSTANDING)*
3. Implement deletion at the head, tail, Kth position, and of the node with value `x`. *(APPLYING)*
4. Identify the edge cases each deletion operation must guard against — empty list, single-node list. *(ANALYZING)*
5. Explain why deletion is "rewiring, not erasing" — a node becomes unreachable before it's actually freed. *(UNDERSTANDING)*
6. Trace a sequence of insertion then deletion operations, correctly tracking the list's state between each step. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 8 (3–7 min) · ALS: Polling

5 questions on **Session 8 (Insertion in Linked List)**. ~45 s each, project the distribution, never name individuals.

**Q1.** What are the two lines that insert an already-created node `n` at the head of a non-empty list?
`A` `head = n; n->next = head;` · `B` `n->next = head; head = n;` · `C` `n = head; head->next = n;` · `D` `n->next = null; head = n;`
→ **B.** *Read:* Order matters — swapping these two lines loses the rest of the list. This is the exact class of mistake today's deletion operations will punish just as hard.

**Q2.** For `insert_kth`, what's the correct traversal stopping condition?
`A` `count == k` · `B` `count == k - 1` · `C` `count == k + 1` · `D` There is no stopping condition
→ **B.**

**Q3.** What's the time complexity of inserting at the tail of a singly linked list with only a `head` pointer?
`A` O(1) · `B` O(log n) · `C` O(n) · `D` O(n²)
→ **C.**

**Q4.** In `insert_kth`, why must the stopping condition be `count == k - 1`, not `count == k`?
`A` Because `k` is always 0 · `B` Because you insert AFTER the (k-1)th node, landing the new node at position k · `C` Arbitrary convention · `D` Because arrays are 0-indexed
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about insertion operations from last session?
`A` All four are O(1) space · `B` Insert-before-x needs to look one node ahead · `C` Insert-at-head requires traversal · `D` The Complexity Summary table showed head as the cheapest position
→ **A, B, D.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–9 min)

Put this on the board:

> *"Same list as last session: `1 → 3 → 5 → 7 → 9 → NULL`. I want to remove `5`. What actually has to change?"*

Let guesses land — some will say "just erase the box." Draw it properly: node `3`'s `next` arrow gets redirected to point at node `7`, skipping over `5` entirely.

> *"Node 5 is still sitting there in memory, for a moment. But nothing points to it anymore — it's unreachable. That's the entire idea today: deletion in a linked list is *rewiring*, not erasing. Last session you learned where insertion is cheap or expensive. Today, the exact same question, for removal."*

---

## Slide Block B (9–20 min) — DELIVER SLIDES AS-IS

Covers: Deletion in a Linked List — the four types (head, tail, Kth position, node with value `x`) — each with problem statement, approach, C++ code, and complexity; closing with the Deletion Complexity Summary table.

**Beats to emphasise**

- **Delete head**: store `head` in `temp`, move `head = head->next`, delete `temp`, return the new `head`. O(1) — no traversal needed, mirror of insert-at-head.
- **Delete tail**: two edge cases before the real work — empty list, and single-node list (`head->next == nullptr`, meaning the head IS the tail). Only after both checks does it traverse to the *second-to-last* node, using `temp->next->next != nullptr` as the stopping condition — one node further ahead than `insert-at-tail`'s stopping condition, because deletion needs the node *before* the one being removed.
- **Delete Kth**: same `count == k - 1` traversal pattern as insertion (Session 8), then `temp->next = temp->next->next` skips over (and deletes) the target node.
- **Delete node with value `x`**: check the head first (`head->data == x`), then look ahead with `temp->next->data == x` — same "look one ahead" shape as insert-before-x.
- Every deletion is O(1) **space** (a handful of pointers, nothing that scales); the time cost again tracks how far you must walk: head = O(1), everything else = O(n), except Kth which is technically O(k).

**Checkpoint (at 20 min)** — cold-call one student:
> *"Before you delete the tail, the approach says check if `head->next == NULL`. What breaks if you skip that check?"*
> **Answer:** If there's only one node, that node IS both head and tail. The code that walks to "the node before the last node" has nothing to walk to — `temp->next->next` would dereference a null pointer — so it crashes instead of correctly deleting the list's only node.

---

## ⚡ ALS Activity 1 — Live Coding / Dry-Run Relay: Delete the Kth Node (20–29 min)

**ALS format:** Live Coding / Dry-Run Relay — five volunteers physically become nodes at the board. Chosen right after Slide Block B because correctly identifying and relinking `temp->next` when deleting from the middle is the crux of `delete_kth`, and it only really lands once students have physically traced it, not just watched it.

**Setup line:**
> *"Board time. List is `1 → 3 → 5 → 7 → 9 → NULL`. We're deleting k = 2 (0-indexed — that's the node holding 5). One volunteer per node, draw your box and your `next` arrow. I'll call the moves, you draw."*

Five volunteers draw the chain. The class walks `temp` to `count == k - 1` (the node holding `3`). That volunteer draws the new arrow skipping over node `5`, and node `5` gets crossed out as "deleted."

**How it surfaces:** The common mistake is relinking `temp->next` to point at `temp->next` itself (a no-op) instead of `temp->next->next`. Stop and ask: *"If you only change what `temp` points to without skipping ahead, does anything still point at node 5?"* Walk them to seeing node 5 is still fully wired into the list.

**Debrief line:**
> *"One pointer changed — `temp->next` — and node 5 is gone from the list, even though it might still exist in memory until it's explicitly deleted. That's the whole trick: deletion in a linked list is rewiring, not erasing."*

**Cut rule:** Drop the volunteer relay and sketch it on the whiteboard while narrating the same two steps (find `count == k-1`, then skip one node ahead).

---

## ⚡ ALS Activity 2 — Predict the Output: Chained Insert Then Delete (29–38 min)

**ALS format:** Predict-the-Output — students commit to a final list, on paper, before anything is revealed. Chosen as the closing activity because it's the first moment insertion (Session 8) and deletion (today) meet in one sequence — holding both operations across two sessions of content without redrawing the list from scratch is exactly the skill multi-step DSA problems demand.

**Setup line:**
> *"Starting list: `1 → 3 → 5 → 7 → 9 → NULL`. I run `insertAtHead(head, 0)`, then `deleteTail(head)` on the result. Before I show you anything — write down the final list."*

Give 90 seconds individual, silent, then take the answer before revealing.

**The trace**

1. `insertAtHead(head, 0)`: `0 → 1 → 3 → 5 → 7 → 9 → NULL` (6 nodes)
2. `deleteTail(head)`: removes whichever node is last **right now** — that's `9`, not `1` or anything from the original list.

> **Final list: `0 → 1 → 3 → 5 → 7 → NULL`.**

**When it goes wrong**

| If… | Do this |
|---|---|
| Students predict deletion removes `9` from the *original* 5-node list, giving something like `3, 5, 7, 9` | Point out: the insert ran *first* — the list was already 6 nodes long by the time `deleteTail` ran |
| Someone flips which end `deleteTail` removes from | Remind them `deleteTail` always removes from the end, regardless of what was just inserted at the front |

**Debrief line:**
> *"Insert happened first, so the list was 6 nodes long by the time delete-tail ran — it removes whichever node is last AFTER the insert, not before. Sequence matters. This is exactly how multi-step problems get misread under time pressure."*

**Cut rule:** Skip the individual write-down and run it as a single cold-call trace on the board instead.

---

## Classroom Quiz (38–43 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering the four deletion positions, their edge cases, and complexities. -->

---

## Exit Ticket + Homework (43–48 min)

**Exit ticket** (~1 min) — on paper before anyone leaves:

> Write the two lines of code that delete the head node of a non-empty list, starting from `head`.
> **Answer:** `Node* temp = head;` then `head = head->next;` (then `delete temp;`).

**Homework:** Re-attempt today's four deletion dry runs from memory — write all four functions (head, tail, Kth, value-x) from scratch without looking back at the slides, then check against the deck. Also re-run this session's chained insert-then-delete trace on a fresh list of your own choosing.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `deleteTail` needs to check for an empty list, but not for a single-node list | The empty-list check is the obvious one; the single-node case looks like "just another case of the loop" | Slide Block B's checkpoint — showing that `temp->next->next` would dereference `null` on a one-node list |
| Deletion "erases" the node from memory automatically | The node visually disappears from the diagram once unlinked | ALS Activity 1's debrief — the node is unreachable, not gone; explicit `delete` is what frees it |
| `head` changes after every insertion or deletion | Some operations (head-insert, head-delete) genuinely do change `head`, so students overgeneralise | Pointing out that `deleteTail` returns `head` unchanged, except in its empty-list/single-node edge cases |
| A chained insert-then-delete can be predicted by reasoning about each operation on the *original* list | Each operation was taught and tested in isolation, across two separate sessions | ALS Activity 2 — deletion must run on the *already-changed* list from the insert, not the starting one |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Split out from the original 60-min "Session 39 — Insertion, Deletion," which covered both insertion and deletion together — see `sem-3-sequence.md`. Insertion has its own session (8), immediately before this one.
- **Two ALS activities this session:** Activity 1 is the Live Coding / Dry-Run Relay (delete-Kth, hands-on pointer relinking), Activity 2 is Predict the Output (chaining an insertion from Session 8 with a deletion from today — the session's synthesis moment).
- **The Classroom Quiz now runs last, right before the Exit Ticket** — matching the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank covering the four deletion positions, their edge cases, and complexities.
- **This is session 9 of the Sem-3 sequence** (see `sem-3-sequence.md`), the second half of the original combined Insertion+Deletion session — Session 8 covers insertion. ALS Activity 2 here is the original file's third activity, moved from the combined session into this one since it needs both insertion and deletion already taught.
- **Protect the single-node `deleteTail` edge case (Slide Block B's checkpoint) over anything else if the session runs behind.** It's the deletion-side equivalent of insertion's off-by-one — a real, common, silent failure mode, not a hypothetical.
