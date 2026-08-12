# Session 39b — Insertion, Deletion (Part 2 of 2)

**Duration** 35 min · **Topic** Linked List — Deletion: Head, Tail, Kth & Value-X · **Prerequisite** Session 39a — Insertion, Deletion, Part 1 (four insertion positions) · **Session type** Concept lecture

<!-- Split note: continues session-39 (original 60 min) right after the Classroom Quiz. This part covers all four deletion positions (head, tail, Kth, value-x) and closes with two hands-on activities: a live deletion relay and a chained insert-then-delete prediction. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Insertion, Deletion | https://docs.google.com/presentation/d/1q6eByMnLCZNPIFu9IMBzrmpZbQ1GlJ4feddjOeakiTU/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Implement deletion at the head, tail, Kth position, and of the node with value `x`. *(APPLYING)*
2. Justify the time complexity of each deletion operation using pointer-traversal reasoning. *(ANALYZING)*
3. Identify the edge cases — empty list, single-node list, k out of bounds, value not found — that each operation must guard against. *(ANALYZING)* <!-- placement: inferred from the "Check if List is Empty" step repeated at the start of every Approach slide -->

---

## Warm-Up Poll — Retrieval Practice on Session 39a (0–5 min)

Say: *"Four quick ones on insertion before we do the mirror-image operation."*

**Q1.** Insert at head is what complexity?
`A` O(1) · `B` O(n) · `C` O(log n) · `D` O(n²)
→ *Read:* A.

**Q2.** Why is insert at tail O(n) on a singly linked list?
`A` It isn't, it's O(1) · `B` You must walk the whole list to find the last node — no shortcut without a tail pointer · `C` Tail nodes are slower to allocate · `D` It requires sorting
→ *Read:* B.

**Q3.** The traversal for `insert_kth` stops at:
`A` `count == k` · `B` `count == k - 1` · `C` `count == k + 1` · `D` The end of the list, always
→ *Read:* B — Part 1's off-by-one activity.

**Q4.** In Part 1's Muddiest-Point check, which insertion position did you flag as least confident?
→ *Read:* Open response — reconnects to individual gaps before deletion's four positions arrive.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"Insertion added a node without moving anyone. Deletion removes one the same way — by rewiring, not erasing. Same four positions, mirror image."*

---

## Slide Block B (7–17 min) — DELIVER SLIDES AS-IS

Covers: Deletion in a Linked List — the four types (head, tail, Kth position, node with value `x`) — each with problem statement, approach, C++ code, and complexity; closing with the Deletion Complexity Summary table.

**Beats to emphasise**

- **Delete head**: store `head` in `temp`, move `head = head->next`, delete `temp`, return the new `head`. O(1) — no traversal needed, mirror of insert-at-head.
- **Delete tail**: two edge cases before the real work — empty list, and single-node list (`head->next == nullptr`, meaning the head IS the tail). Only after both checks does it traverse to the *second-to-last* node, using `temp->next->next != nullptr` as the stopping condition — one node further ahead than `insert-at-tail`'s stopping condition, because deletion needs the node *before* the one being removed.
- **Delete Kth**: same `count == k - 1` traversal pattern as insertion, then `temp->next = temp->next->next` skips over (and deletes) the target node.
- **Delete node with value `x`**: check the head first (`head->data == x`), then look ahead with `temp->next->data == x` — same "look one ahead" shape as insert-before-x.
- Every deletion is O(1) **space** (a handful of pointers, nothing that scales); the time cost again tracks how far you must walk: head = O(1), everything else = O(n) except Kth which is technically O(k).

**Checkpoint (at 17 min)** — cold-call one student:
> *"Before you delete the tail, the approach says check if `head->next == NULL`. What breaks if you skip that check?"*
> **Answer:** If there's only one node, that node IS both head and tail. The code that walks to "the node before the last node" has nothing to walk to — `temp->next->next` would dereference a null pointer — so it crashes instead of correctly deleting the list's only node.

---

## ⚡ Activity 2 — Live Coding / Dry-Run Relay: Delete the Kth Node (17–25 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can correctly identify and relink `temp->next` when deleting from the middle of the list — the crux of `delete_kth`.

**Setup line (say this):**
> *"Board time. List is `1 → 3 → 5 → 7 → 9 → NULL`. We're deleting k = 2 (0-indexed — that's the node holding 5). One volunteer per node, draw your box and your `next` arrow. I'll call the moves, you draw."*

**What students do:** Five volunteers draw the chain. The class walks `temp` to `count == k - 1` (the node holding `3`). That volunteer draws the new arrow skipping over node `5`, and node `5` gets crossed out as "deleted."

**How it surfaces:** The common mistake is relinking `temp->next` to point at `temp->next` itself (a no-op) instead of `temp->next->next`. Stop and ask: *"If you only change what `temp` points to without skipping ahead, does anything still point at node 5?"* Walk them to seeing node 5 is still fully wired into the list.

**Debrief line:**
> *"One pointer changed — `temp->next` — and node 5 is gone from the list, even though it might still exist in memory until it's explicitly deleted. That's the whole trick: deletion in a linked list is rewiring, not erasing."*

**Cut rule:** If running short, drop the volunteer relay and sketch it yourself on the whiteboard while narrating the same two steps (find `count == k-1`, then skip one node ahead).

---

## ⚡ Activity 3 — Predict-the-Output: Chained Insert Then Delete (25–32 min)

**Format:** Predict-the-Output · **Exposes:** whether students can hold two operations in sequence without redrawing the whole list from scratch — the same skill multi-step DSA problems demand.

**Setup line (say this):**
> *"Starting list: `1 → 3 → 5 → 7 → 9 → NULL`. I run `insertAtHead(head, 0)`, then `deleteTail(head)` on the result. Before I show you anything — write down the final list."*

**What students do:** Write their predicted final list individually, then share out.

**How it surfaces:** The most common wrong answer forgets the insert happened first, and predicts deletion removes `9` from the *original* 5-node list — giving `3, 5, 7, 9` or similar instead of the correct `0, 1, 3, 5, 7`. Some will also flip which end `deleteTail` removes from — remind them `deleteTail` always removes from the end, regardless of what was just inserted at the front.

**Debrief line:**
> *"Insert happened first, so the list was 6 nodes long by the time delete-tail ran — it removes whichever node is last AFTER the insert, not before. Sequence matters. This is exactly how multi-step problems get misread under time pressure."*

**Cut rule:** If short on time, skip the individual write-down and run it as a single cold-call trace on the board instead.

---

## Exit Ticket (32–35 min)

**Exit ticket** — on paper before anyone leaves:

> Write the two lines of code that insert an already-created node `n` at the head of a non-empty list, starting from `head`.
> **Answer:** `n->next = head;` then `head = n;`

**Homework:** Re-attempt today's insertion and deletion dry runs from memory — write all eight functions (4 insert + 4 delete) from scratch without looking back at the slides, then check against the deck. <!-- placement: inferred -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `deleteTail` needs to check for an empty list, but not for a single-node list | The empty-list check is the obvious one; the single-node case looks like "just another case of the loop" | Slide Block B's checkpoint — showing that `temp->next->next` would dereference `null` on a one-node list |
| Deletion "erases" the node from memory automatically | The node visually disappears from the diagram once unlinked | Activity 2's debrief — the node is unreachable, not gone; explicit `delete` is what frees it |
| `head` changes after every insertion or deletion | Some operations (head-insert, head-delete) genuinely do change `head`, so students overgeneralise | Pointing out that `insertAtTail` and `deleteTail` both `return head` unchanged, except in their empty-list/single-node edge cases |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz.**
- **The deck's own slides mark a second natural quiz break** right after the Deletion summary table — a good spot for a quick recap question if you're ahead of pace, even though the Classroom Quiz proper ran in Part 1.
- **Watch the clock at the Slide Block B → Activity 2 handoff** — this is the largest content block of this part; if you're behind, use Activity 2's cut rule immediately rather than trimming Slide Block B's content.
