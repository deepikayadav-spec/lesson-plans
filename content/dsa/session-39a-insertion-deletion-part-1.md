# Session 39a — Insertion, Deletion (Part 1 of 2)

**Duration** 35 min · **Topic** Linked List — Insertion: Head, Tail, Kth & Before-X · **Prerequisite** Session 38 — Singly Linked List (node structure, traversal, search) · **Session type** Concept lecture

<!-- Split note: original session-39 ran 60 min. Split right after the Classroom Quiz. Part 1 covers all four insertion positions (head, tail, Kth, before-x) and the off-by-one Spot-the-Bug activity. Part 2 (session-39b) covers all four deletion positions and the two hands-on activities on deletion and sequencing. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Insertion, Deletion | https://docs.google.com/presentation/d/1q6eByMnLCZNPIFu9IMBzrmpZbQ1GlJ4feddjOeakiTU/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. List the four insertion positions covered for a singly linked list. *(REMEMBERING)*
2. Explain why inserting at the head is O(1) while at the tail is O(n) on a singly linked list. *(UNDERSTANDING)*
3. Implement insertion at the head, tail, Kth position, and before a node with value `x`. *(APPLYING)*

*(Deletion at all four positions is covered in Part 2.)*

---

## Warm-Up Poll — Retrieval on Session 38: Singly Linked List (0–7 min)

Say: *"Seven quick ones on last session's linked list basics before we build on top of them."*

**Q1.** What are the two things every node in a singly linked list stores?
`A` Data and a pointer to the previous node · `B` Data and a pointer to the next node · `C` Only data · `D` Two pointers, no data

**Q2.** Why can arrays be a poor fit when the amount of data is unknown or changes often?
`A` Arrays are always slower to read from · `B` Arrays have a fixed size once declared · `C` Arrays cannot store integers · `D` Arrays require pointers

**Q3.** In a singly linked list, what does the `next` pointer of the LAST node point to?
`A` The head node (circular) · `B` The previous node · `C` `null` · `D` Itself

**Q4.** *(MSQ — select all that are TRUE)*
`A` A doubly linked list allows bidirectional traversal · `B` A circular linked list's last node points back to the first node · `C` A singly linked list's last node points to `null` · `D` All three types require contiguous memory
→ *Read:* If many pick D, the core "why linked lists exist" idea from last session hasn't landed — put the non-contiguous-memory diagram back up for 30 seconds before moving on, since today's operations all assume nodes are scattered in memory.

**Q5.** What was the time complexity of building a linked list from an array of `n` elements (`arraytoLL`)?
`A` O(1) · `B` O(log n) · `C` O(n) · `D` O(n²)

**Q6.** What was the space complexity of the search function (`searchLL`) that checks whether a value `x` is present?
`A` O(n) · `B` O(1) · `C` O(log n) · `D` O(n²)
→ *Read:* If the class flips this with the O(n) time answer, that's the classic time-vs-space mixup — hold up one finger ("one pointer, that's it, no matter how far it searches") to reinforce O(1) space.

**Q7.** In the "Print Linked List" algorithm, when does the traversal loop stop?
`A` After a fixed number of steps · `B` When `temp` reaches `null` · `C` When it finds the target value · `D` It never stops

**Running it** — poll tool, ~45 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–11 min)

Put this on the board:

> *"Array `[20, 30, 40, 50]`. I want to insert `5` at the front. In an array, what has to happen to every other element?"*

Let them say it: everything shifts right by one slot. Then draw the same four values as a linked list: `20 → 30 → 40 → 50 → NULL`. *"Now I insert 5 at the front. How many existing nodes move?"*

Answer: zero. *"Nobody moves. One new box, one new arrow, done. That's the entire subject of today — how cheap or expensive it is to insert or remove a node, depending on WHERE."*

---

## Slide Block A (11–22 min) — DELIVER SLIDES AS-IS

Covers: Insertion in a Linked List — the four types (head, tail, Kth position, before a node with value `x`) — each with problem statement, approach, C++ code, and complexity; closing with the Insertion Complexity Summary table.

**Beats to emphasise**

- **Insert at head** is the baseline: create node `n`, `n->next = head`, `head = n`. Three lines, O(1), no traversal — say explicitly that this is *as cheap as insertion ever gets*.
- **Insert at tail**: the expensive one *is* the traversal, not the insertion. You walk node-by-node until `temp->next == nullptr`, and only then do you attach — that walk is the entire O(n) cost. Flag the empty-list special case (`if head == nullptr`, the new node just becomes head).
- **Insert at Kth position**: this is `insert-at-head` (if `k == 0`) fused with `insert-at-tail`'s traversal style — walk to the `(k-1)`th node using a `count` variable, then splice in. The traversal stops at `count == k - 1`, **not** `count == k`. Underline that distinction on the board; it's the exact bug Activity 1 is built around.
- **Insert before a node with value `x`**: same shape again, but the stopping condition is `temp->next->data == x` (you must look *ahead* one node, because you need to hold the node *before* the target to relink it).
- Close with the **Complexity Summary table**: head O(1)/O(1), tail O(N)/O(1), Kth O(N)/O(1), before-x O(N)/O(1) — every insertion is O(1) *space* because only ever one new node is allocated; the time cost is entirely about how far you must walk to reach the insertion point.

**Checkpoint (at 22 min)** — cold-call one student:
> *"Insert-at-head is O(1) and insert-at-tail is O(n) on a singly linked list with only a head pointer — in one sentence, why the gap?"*
> **Answer:** Inserting at head just rewires one pointer at a spot you already have. Inserting at tail means walking the entire list first to even find the last node, because there's no shortcut to it — no separate tail pointer is kept.

---

## ⚡ Activity 1 — Spot the Bug: The Off-By-One in Insert-Kth (22–27 min)

**Format:** Spot the Bug · **Exposes:** the `k` vs. `k - 1` off-by-one, the single most common insertion bug, sitting inside the deck's own `insert_kth` traversal condition.

**Setup line (say this):**
> *"Here's `insert_kth` from the slides, except I changed exactly one character. List is `1 → 3 → 5 → 7 → 9`, I call `insert_kth(head, 2, 99)`. Trace where `99` actually lands — before I tell you what I changed."*

```cpp
Node* temp = head;
int count = 0;
while (temp != nullptr){
    if (count == k){          // was: count == k - 1
        Node* n = new Node(a);
        n->next = temp->next;
        temp->next = n;
        break;
    }
    temp = temp->next;
    count++;
}
```

**What students do:** Trace by hand (or at the board) where `99` lands versus where `k = 2` (0-indexed) should place it — right after `3`, before `5`.

**How it surfaces:** If someone says "it crashes" — it doesn't. It silently inserts one node too late (after `5` instead of after `3`), which is more dangerous than a crash because nothing flags it as wrong.

**Debrief line:**
> *"`count == k - 1` means stop one node early, so you insert AFTER the (k-1)th node, which lands the new node at position k. Change that one character and the bug doesn't crash — it quietly gives you the wrong answer. That's worse, and it's exactly the kind of bug you'll spend an hour hunting later if you don't get it right the first time."*

**Cut rule:** If running short, skip the hand-trace and just ask "does node 99 land before or after node 5?" as a show of hands, then reveal.

---

## Classroom Quiz (27–32 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Muddiest-Point Cards (32–35 min)

**Why this strategy here:** insertion's four positions share a lot of structural DNA (find the spot, relink), which makes it easy to feel like you followed along without being able to reproduce any one of them cold. A muddiest-point card surfaces which specific position is still shaky before Part 2 layers deletion — a mirror-image set of four operations — on top.

**Run it (3 minutes):**
> *"One sentence, on paper or in chat: which of the four insertion positions — head, tail, Kth, before-x — would you NOT be confident coding cold right now? No names needed."*

Skim a few responses out loud (anonymously). If Kth or before-x dominates, that's expected — they're the densest two — but note it for a 30-second callback before Part 2's deletion-Kth activity, which reuses the identical `count == k - 1` logic.

> *"Hold onto whichever one felt shakiest. Part 2 mirrors all four positions for deletion — and Kth deletion uses the exact same off-by-one trap you just debugged."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Inserting at the head of a linked list is O(n), "because you have to shift everything" | Habit carried over from array insertion | The Hook — drawing the linked-list version and counting how many *existing* nodes actually move (zero) |
| The traversal for `insert_kth` should stop at `count == k` | "Insert at position k" sounds like "stop when you reach index k" | Activity 1 — tracing exactly where the off-by-one lands the new node |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz.**
- **Pacing risk:** Slide Block A has four sub-operations in 11 minutes — don't let `insert-before-x` run long just because it's the last one covered; it's structurally identical to `insert_kth` with a different stopping condition, say that explicitly and move on.
- **The deck's own slides mark a natural quiz break** right after the Insertion summary table — this plan uses it as the Classroom Quiz slot.
- **Activity 1 depends on Slide Block A's `count == k - 1` beat landing first** — if that beat got rushed, spend 30 extra seconds re-deriving it before running the activity, or the bug will look arbitrary rather than inevitable.
