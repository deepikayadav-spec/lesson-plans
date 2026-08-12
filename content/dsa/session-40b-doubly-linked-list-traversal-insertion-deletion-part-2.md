# Session 40b — Doubly Linked List: Deletion (Part 2 of 2)

**Duration** 29 min · **Topic** Linked List — DLL Deletion & Boundary Cases · **Prerequisite** Session 40a — Doubly Linked List, Part 1 (DLL structure, insertion) · **Session type** Concept lecture

<!-- Split note: continues session-40 (original 60 min) right after the Classroom Quiz. This part covers all three deletion positions — the densest material in the session, because of Kth-deletion's three-way branching — plus two closing activities. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Doubly Linked List - Traversal, Insertion, Deletion | https://docs.google.com/presentation/d/1CtyEsYixyAXlaQ-wZUaqsxFZx4XQF1JPPIJ18LZ9YKg/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Implement deletion at the head, tail, and Kth position of a doubly linked list, correctly handling the head/tail boundary cases. *(APPLYING)*
2. Compare the time complexity of each DLL operation against its singly-linked-list counterpart from Session 39. *(ANALYZING)* <!-- placement: inferred -->
3. Explain why every DLL insertion or deletion must update two pointers instead of one. *(UNDERSTANDING)*

---

## Warm-Up Poll — Retrieval Practice on Session 40a (0–5 min)

Say: *"Four quick ones on insertion before we do the mirror-image operation."*

**Q1.** Insert-at-head in a DLL needs one extra step beyond the singly-linked-list version. What is it?
`A` Nothing extra · `B` Setting the old head's `prev` to point at the new node · `C` Allocating two nodes instead of one · `D` Traversing the whole list
→ *Read:* B.

**Q2.** Insert-at-head in a DLL is still what complexity, despite the extra step?
`A` O(n) · `B` O(1) · `C` O(log n) · `D` O(k)
→ *Read:* B — one extra constant-time line, not a new order of growth.

**Q3.** Inserting before the Kth node touches how many pointers total?
`A` 1 · `B` 2 · `C` 4 · `D` 8
→ *Read:* C — `back->next`, `temp->prev`, plus the new node's own `next` and `prev`.

**Q4.** In Part 1's Prev/Next Sort, which steps needed BOTH pointers fixed?
→ *Read:* Open response — reconnects to "the DLL tax" before deletion's harder branching arrives.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"Insertion always had somewhere safe to attach. Deletion has to ask a harder question first: does the node I'm removing actually have a neighbour on both sides?"*

---

## Slide Block C (7–17 min) — DELIVER SLIDES AS-IS

Covers: Deletion in a Doubly Linked List — the three types (head, tail, Kth position) — each with problem statement, dry-run diagram, C++ code, and complexity; closing with the Deletion Complexity Summary table.

**Beats to emphasise**

- **Delete head**: handle empty-list and single-node cases first, then `head = head->next` followed by the DLL-specific extra step, `head->prev = nullptr`, before deleting the old head. O(1).
- **Delete tail**: same empty/single-node guards, then walk to the second-to-last node, set both `temp->next = nullptr` and `tail->prev = nullptr` before deleting the old tail. O(n).
- **Delete Kth node**: this is the one with real branching complexity — walk this one slowly. After finding `temp` at position `k`, save `back = temp->prev` and `front = temp->next`, then branch three ways: **both null** (only node in the list — delete and return `nullptr`), **`back` null** (`temp` is the head — hand off to `delete_head`), **`front` null** (`temp` is the tail — hand off to `delete_tail`), and only in the **true middle case** does the general relink formula run: `back->next = front; front->prev = back`.
- Emphasise *why* the branching exists: the general formula assumes both neighbours are real nodes. Head and tail are exactly the two positions where that assumption breaks.
- Close with the **Complexity Summary**: head O(1)/O(1), tail O(N)/O(1), Kth O(k)/O(1) — identical shape to insertion.

**Checkpoint (at 17 min)** — cold-call one student:
> *"In `delete_kth`, why does the code branch into three separate cases instead of using one general formula?"*
> **Answer:** The general formula `back->next = front; front->prev = back` assumes both neighbours exist. If the node being deleted is the head, `back` is null; if it's the tail, `front` is null; if it's the only node, both are null. Each of those would crash the general formula, so they're handed off to `delete_head` / `delete_tail` instead of forcing one formula to cover every case.

---

## ⚡ Activity 2 — Spot the Bug: Delete-Kth Without Boundary Checks (17–22 min)

**Format:** Spot the Bug · **Exposes:** the null-pointer crash that happens when the general "relink neighbours" logic runs on a node at the head or tail without the deck's own boundary branching.

**Setup line (say this):**
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

**What students do:** Trace `k = 0` (deleting the head) mentally: `back = temp->prev` is `nullptr` because the head has no previous node, so `back->next` dereferences a null pointer on the very next line.

**How it surfaces:** If someone says "it just doesn't delete anything" — no, it crashes. A null-pointer dereference in C++ is not a silent no-op.

**Debrief line:**
> *"The general relink formula only works when the node being deleted has neighbours on both sides. The head and tail are exactly the nodes that don't — which is why the real code hands those two cases off to `delete_head` and `delete_tail` instead of trying to force one formula to cover everything."*

**Cut rule:** If running short, skip tracing `k = 0` by hand and just ask "which position breaks this — head, middle, or tail?" as a show of hands, then reveal why.

---

## ⚡ Activity 3 — Predict-the-Output: The Stale Pointer (22–26 min)

**Format:** Predict-the-Output · **Exposes:** whether the `prev`/`next` distinction from Part 1's Activity 1 has actually stuck by the end of the session.

**Setup line (say this):**
> *"Doubly linked list: `NULL ← 10 ⇄ 20 ⇄ 30 → NULL`. I delete the head. One line, everyone: what does node 20's `prev` pointer equal now?"*

**What students do:** Call out the answer — `NULL` — a fast, low-stakes closing check.

**How it surfaces:** If someone says "10" (the old head), that's the exact stale-pointer bug from the misconceptions table — point at it directly: *"10 was just deleted. You cannot point at deleted memory."*

**Debrief line:**
> *"That's the one line every DLL deletion has to get right — the new boundary node's outward-facing pointer must become `NULL`, not just keep pointing at whatever used to be there."*

**Cut rule:** If out of time, cut this activity entirely and fold the same question into the Exit Ticket instead.

---

## Exit Ticket (26–29 min)

**Exit ticket** — on paper before anyone leaves:

> A doubly linked list is `10 ⇄ 20 ⇄ 30`, with `NULL` on both outer ends. You insert a new node with value `5` before the old head. What is `head->prev` immediately after the insertion?
> **Answer:** It is no longer `NULL` — it now points at the new node holding `5` (and `5`'s own `prev` is `NULL`, since `5` is now the true head).

**Homework:** Re-attempt today's doubly linked list construction and Kth-position insertion/deletion dry runs from memory, drawing both the `prev` and `next` arrows at every single step. <!-- placement: inferred -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `delete_kth` can use the same general relink formula regardless of position | The formula looks clean and "the same" for every node in the middle | Activity 2 — running the general formula on `k = 0` and hitting the null-pointer crash directly |
| After deleting a node, the neighbour's old pointer to it will resolve to `NULL` automatically | Deleted nodes disappear from the diagram, so it *looks* automatic | Activity 3 — forcing the explicit statement that the new boundary node's pointer must be *set* to `NULL`, not assumed |
| A DLL gives O(1) access to the tail because "you have two pointers now" | Confusing "bidirectional traversal" with "instant access to both ends" | Slide Block C — walking through `delete_tail` and showing the traversal from `head` is still required; two-way links do not create a stored tail reference |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz.**
- **Pacing risk:** Slide Block C is the densest block in this part because of `delete_kth`'s three-way branching — do not rush it to protect Activity 2's time; if the branching logic isn't clear here, Activity 2 will look arbitrary rather than inevitable.
- Keep Session 39's summary tables visible or sketched on a side board — the O(1) vs O(n) contrasts only land if students can see the singly-linked-list numbers next to today's.
