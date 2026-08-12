# Session 40a — Doubly Linked List: Traversal & Insertion (Part 1 of 2)

**Duration** 41 min · **Topic** Linked List — DLL Structure & Insertion · **Prerequisite** Session 39 — Insertion, Deletion (singly linked list) · **Session type** Concept lecture

<!-- Split note: original session-40 ran 60 min. Split right after the Classroom Quiz. Part 1 covers the DLL node structure, building one from an array, and all three insertion positions. Part 2 (session-40b) covers all three deletion positions — the densest material, because of Kth-deletion's three-way branching — plus two closing activities. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Doubly Linked List - Traversal, Insertion, Deletion | https://docs.google.com/presentation/d/1CtyEsYixyAXlaQ-wZUaqsxFZx4XQF1JPPIJ18LZ9YKg/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Describe how a doubly linked list node differs from a singly linked list node — it carries both `prev` and `next`. *(UNDERSTANDING)*
2. Construct a doubly linked list from an array, correctly linking both `prev` and `next` at every step. *(APPLYING)*
3. Implement insertion at the head, tail, and Kth position of a doubly linked list. *(APPLYING)*

*(Deletion at all three positions is covered in Part 2.)*

---

## Warm-Up Poll — Retrieval on Session 39: Insertion, Deletion (0–7 min)

Say: *"Seven quick ones on last session's insertion and deletion before we add a second pointer to every node today."*

**Q1.** What is the time complexity of inserting a new node at the HEAD of a singly linked list?
`A` O(1) · `B` O(n) · `C` O(log n) · `D` O(k)

**Q2.** What is the time complexity of inserting a new node at the TAIL of a singly linked list, given only the head pointer?
`A` O(1) · `B` O(n) · `C` O(log n) · `D` O(k)
→ *Read:* If many say O(1), they're forgetting you must walk the entire list to even find the last node, since there's no separate tail pointer kept. Flag this hard — the same "no shortcut to the far end" idea is exactly what today's Doubly Linked List session is about to complicate.

**Q3.** To delete the node at the Kth position, what must you first find?
`A` The Kth node itself, directly · `B` The (K−1)th node — the one just before it · `C` The tail node · `D` The head node

**Q4.** *(MSQ — select all that have O(1) time complexity in a singly linked list)*
`A` Insert at head · `B` Delete at head · `C` Insert at tail · `D` Delete at tail

**Q5.** When deleting the node with a given value `x`, what happens if `x` isn't found anywhere in the list?
`A` The program crashes · `B` The list is returned unchanged, after traversing to the end · `C` The head is deleted anyway · `D` Infinite loop

**Q6.** What must you check BEFORE attempting to delete the tail of a list that might have just one node?
`A` Whether `head->next` is null (single-node list) · `B` Whether `head->data` equals `x` · `C` Whether `k` equals 0 · `D` Nothing — the same code always works
→ *Read:* This exact "does the node have a neighbour on both sides?" question is the seed of nearly every null-pointer bug students will write in today's Doubly Linked List deletion code. Call it out explicitly before Part 2.

**Q7.** What was the space complexity of every insertion and deletion operation from last session — head, tail, Kth, or by value?
`A` O(n) · `B` O(log n) · `C` O(1) · `D` It depends on k

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–11 min)

Draw a 3-node singly linked list on the board: `10 → 20 → 30 → NULL`. Point at node `20`. Ask: *"I'm standing at node 20. Give me the value of the node before me."*

Let the silence land — there's no way to answer without re-traversing from `head`. Then: *"In everything you've built for two sessions, going backward means starting over from the front. Today's data structure gives every node a second arrow, pointing back the way it came — at the cost of one extra pointer to keep correct, every single time you insert or delete."*

---

## Slide Block A (11–19 min) — DELIVER SLIDES AS-IS

Covers: Doubly Linked List introduction — node structure (`prev`, `data`, `next`) → Head and Tail → C++ Node class (three-argument constructor) → Convert an Array into a DLL (`arrayToDLL`): problem statement, approach, code, complexity.

**Beats to emphasise**

- The node picture is the whole idea: **`prev` ← `data` → `next`**. Every node except the head has a real `prev`; every node except the tail has a real `next`. Both ends are `NULL` on their outward side.
- Walk `arrayToDLL`'s approach exactly as staged: create `head` from `arr[0]`, then for each remaining element create `temp`, set `temp->prev = cur` **and** `cur->next = temp`, then move `cur = temp`. Two links per step, not one — say this out loud every time.
- Complexity: **O(n) time** (one pass, same shape as `arraytoLL` from Session 38) and **O(n) space** (one new node per element) — identical complexity to the singly-linked-list version; the only thing that changed is *how much wiring* happens per node, not how many times the loop runs.
- Reuse the deck's own **Music Playlist** framing if time allows — head = first song, tail = last song, same as Session 38, now with the ability to skip back to the previous track.

**Checkpoint (at 19 min)** — cold-call one student:
> *"When you build a doubly linked list from an array, why do you need `temp->prev = cur` in addition to `cur->next = temp`?"*
> **Answer:** A DLL node needs both directions wired. `cur->next` lets you walk forward from `cur` to `temp`, but without `temp->prev = cur` there's no way to walk backward from `temp` to `cur` — skip it, and you've quietly built a singly linked list with an unused second pointer.

---

## ⚡ Activity 1 — Live Coding / Dry-Run Relay: Build the DLL, Both Pointers (19–24 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** the single new failure mode a doubly linked list introduces — wiring `next` and forgetting `prev`.

**Setup line (say this):**
> *"Same relay you know from linked lists, one new rule. `arr = [10, 20, 30, 40]`. Four volunteers, one box each. This time, every arrow needs a partner — for every `next` arrow you draw, the `prev` arrow going the other way gets drawn immediately after, before we move to the next node."*

**What students do:** Volunteer 1 is `head` (`prev = NULL`). Volunteer 2 draws the `next` arrow from node 1 to node 2, and must immediately draw the `prev` arrow from node 2 back to node 1 before the class moves to volunteer 3. Continue through node 4, whose `next` is `NULL`.

**How it surfaces:** If the class rushes ahead and draws all four `next` arrows first, stop everything: *"Count the `prev` arrows on the board right now."* Let them see the gap themselves before you let them fix it — that's the entire point of the activity.

**Debrief line:**
> *"Every insertion or deletion you do on a DLL for the rest of this unit has this exact shape — one `next` fix, one `prev` fix. Forget the second one, and you've built a singly linked list wearing a doubly linked list's clothes."*

**Cut rule:** If running short, drop to 3 nodes instead of 4, but do not skip the "count the `prev` arrows" trap — that's the whole teaching point.

---

## Slide Block B (24–33 min) — DELIVER SLIDES AS-IS

Covers: Insertion in a Doubly Linked List — the three types (head, tail, before the Kth node) — each with problem statement, dry-run diagram, C++ code, and complexity; closing with the Insertion Complexity Summary table.

**Beats to emphasise**

- **Insert at head**: create the new node with `next = head`, then the one DLL-specific extra step — `head->prev = temp` — before making `temp` the new head. Still O(1); the only change from Session 39's singly-linked-list version is that one extra pointer fix.
- **Insert at tail**: walk from `head` until `tail->next == nullptr` (same O(n) walk as Session 39's `insertAtTail`), then link both directions: `temp->prev = tail` and `tail->next = temp`.
- **Insert before the Kth node**: traverse to the node currently *at* position `k` (`temp`), grab its `prev` as `back`, then splice the new node in between — `back->next = n`, `temp->prev = n`, plus the new node's own `n->next = temp` and `n->prev = back`. Four pointer updates total; walk through each one on the board rather than skipping to the finished diagram.
- Close with the **Complexity Summary**: head O(1)/O(1), tail O(N)/O(1), Kth position O(k)/O(1) — same time-complexity shape as Session 39's singly-linked-list insertions, but every single one now touches two pointers per link instead of one.

**Checkpoint (at 33 min)** — show of hands:
> *"Insert-at-head in a DLL is still O(1), same as a singly linked list — what's the one extra step a DLL insert-at-head needs that a singly linked list doesn't?"*
> **Answer:** You must also set the old head's `prev` pointer to point back at the new node (`head->prev = temp`). A singly linked list has no `prev` to fix, so this is the one genuinely new step.

---

## Classroom Quiz (33–38 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Prev/Next Sort (38–41 min)

**Why this strategy here:** the entire DLL unit is one discipline — every fix comes in pairs. A quick sort of "which pointer(s) does this step touch" cements the pairing before Part 2's deletion logic gets genuinely branchy.

**Run it (3 minutes):**
> *"I'll name a step from today. You tell me: `next` only, `prev` only, or both. Go fast."* Call out: *"Making the new head point to the old head"* (next only) · *"Making the old head point back to the new head"* (prev only) · *"A full insert-at-head, start to finish"* (both) · *"Building the array-to-DLL loop, one element"* (both).

> *"Every 'both' answer is the DLL tax — one extra fix, every single operation. Part 2's deletion has three branches instead of one formula, precisely because head and tail are the two spots where one side of that pair doesn't exist."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Updating `next` is enough; `prev` will "just follow along" | Two sessions of singly-linked-list muscle memory, where only `next` ever mattered | Activity 1's "count the `prev` arrows" trap |
| DLL insertion/deletion at the head costs more than a singly linked list's, since there's an extra pointer | Reasonable-sounding intuition that "more pointers = more complexity class" | Slide Block B's checkpoint — it's still O(1), just one more *constant-time* line, not a new order of growth |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz.**
- **Activity 1's "both arrows" discipline is worth over-investing in early** — every later activity and checkpoint in Part 2 assumes students already flinch at a lone `next` arrow with no `prev` partner.
- **This is the third linked-list session in a row** — if energy is flagging, lean on the direct Session 39 comparisons built into the Learning Objectives and Slide Blocks (same complexity shapes, one new pointer) rather than introducing new framing from scratch.
