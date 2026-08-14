# Session 8 — Insertion in Linked List

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Linked List — Insertion (Head, Tail, Kth Position, Before a Value) · **Prerequisite** Session 7 — Introduction to Linked List
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Insertion, Deletion (insertion half) | https://docs.google.com/presentation/d/1q6eByMnLCZNPIFu9IMBzrmpZbQ1GlJ4feddjOeakiTU/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. List the four insertion positions covered for a singly linked list — head, tail, Kth position, before a node with value `x`. *(REMEMBERING)*
2. Explain why inserting at the head is O(1) while inserting at the tail is O(n) on a singly linked list. *(UNDERSTANDING)*
3. Implement insertion at the head, tail, Kth position, and before a node with value `x`. *(APPLYING)*
4. Justify the time complexity of each insertion operation using pointer-traversal reasoning. *(ANALYZING)*
5. Identify the edge cases each operation must guard against — empty list, `k` out of bounds, value not found. *(ANALYZING)*
6. Correctly apply the `count == k - 1` stopping condition for Kth-position insertion, not `count == k`. *(APPLYING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 7 (3–7 min) · ALS: Polling

5 questions on **Session 7 (Introduction to Linked List)**. ~45 s each, project the distribution, never name individuals.

**Q1.** What are the two things every node in a singly linked list stores?
`A` Data and a pointer to the previous node · `B` Data and a pointer to the next node · `C` Only data · `D` Two pointers, no data
→ **B.**

**Q2.** What does the `next` pointer of the LAST node in a singly linked list point to?
`A` The head node · `B` The previous node · `C` `null` · `D` Itself
→ **C.**

**Q3.** What was the time and space complexity of `arraytoLL` (building a list from an array of n elements)?
`A` O(n) time, O(1) space · `B` O(n) time, O(n) space · `C` O(1) time, O(n) space · `D` O(n²) time, O(n) space
→ **B.** *Read:* This is the one operation from last session with O(n) space — flag if the room forgets and defaults to O(1).

**Q4.** Why can `searchLL` sometimes finish faster than `lengthLL`, even though both are "O(n) time"?
`A` `lengthLL` is actually O(1) · `B` `searchLL` can return early the moment it finds a match · `C` `searchLL` uses a different data structure · `D` They're always exactly the same speed
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about a linked list's memory layout?
`A` Nodes can live anywhere in memory · `B` Nodes must be contiguous, like an array · `C` Each node needs to know the address of the next node · `D` No addresses are involved at all
→ **A, C.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Put this on the board:

> *"Array `[20, 30, 40, 50]`. I want to insert `5` at the front. In an array, what has to happen to every other element?"*

Let them say it: everything shifts right by one slot. Then draw the same four values as a linked list: `20 → 30 → 40 → 50 → NULL`.

> *"Now I insert 5 at the front here. How many existing nodes move?"*

Answer: zero.

> *"Nobody moves. One new box, one new arrow, done. That's the entire subject of today — how cheap or expensive it is to insert a node, depending entirely on WHERE."*

---

## Slide Block A (10–23 min) — DELIVER SLIDES AS-IS

Covers: Insertion in a Linked List — the four types (head, tail, Kth position, before a node with value `x`) — each with problem statement, approach, C++ code, and complexity; closing with the Insertion Complexity Summary table.

**Beats to emphasise**

- **Insert at head** is the baseline: create node `n`, `n->next = head`, `head = n`. Three lines, O(1), no traversal — say explicitly that this is *as cheap as insertion ever gets*.
- **Insert at tail**: the expensive part *is* the traversal, not the insertion. Walk node-by-node until `temp->next == nullptr`, and only then attach — that walk is the entire O(n) cost. Flag the empty-list special case (`if head == nullptr`, the new node just becomes head).
- **Insert at Kth position**: this is `insert-at-head` (if `k == 0`) fused with `insert-at-tail`'s traversal style — walk to the `(k-1)`th node using a `count` variable, then splice in. The traversal stops at `count == k - 1`, **not** `count == k`. Underline that distinction on the board; it's the exact bug ALS Activity 1 is built around.
- **Insert before a node with value `x`**: same shape again, but the stopping condition is `temp->next->data == x` — you must look *ahead* one node, because you need to hold the node *before* the target to relink it.
- Close with the **Complexity Summary table**: head O(1)/O(1), tail O(N)/O(1), Kth O(N)/O(1), before-x O(N)/O(1) — every insertion is O(1) *space* (only ever one new node allocated); the time cost is entirely about how far you must walk to reach the insertion point.

**Checkpoint (at 23 min)** — cold-call one student:
> *"Insert-at-head is O(1) and insert-at-tail is O(n) on a singly linked list with only a head pointer — in one sentence, why the gap?"*
> **Answer:** Inserting at head just rewires one pointer at a spot you already have. Inserting at tail means walking the entire list first to even find the last node — no separate tail pointer is kept.

---

## ⚡ ALS Activity 1 — Spot the Bug: The Off-By-One in Insert-Kth (23–32 min)

**ALS format:** Spot the Bug — exposes the `k` vs. `k - 1` off-by-one, the single most common insertion bug, sitting inside the deck's own `insert_kth` traversal condition.

**Setup line:**
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

Trace by hand (or at the board) where `99` lands versus where `k = 2` (0-indexed) should place it — right after `3`, before `5`.

**How it surfaces:** If someone says "it crashes" — it doesn't. It silently inserts one node too late (after `5` instead of after `3`), which is more dangerous than a crash because nothing flags it as wrong.

**Debrief line:**
> *"`count == k - 1` means stop one node early, so you insert AFTER the (k-1)th node, which lands the new node at position k. Change that one character and the bug doesn't crash — it quietly gives you the wrong answer."*

**Cut rule:** Skip the hand-trace and just ask "does node 99 land before or after node 5?" as a show of hands, then reveal.

---

## ⚡ ALS Activity 2 — Predict the Output: Two Chained Insertions (32–41 min)

**ALS format:** Predict-the-Output — students commit to a final list, on paper, before anything is revealed. Chosen as the closing activity because holding two operations in sequence without redrawing the whole list from scratch is exactly the skill multi-step DSA problems demand — and it immediately reuses ALS Activity 1's `k-1` lesson under fresh numbers.

**Setup line:**
> *"Starting list: `1 → 3 → 5 → NULL`. I run `insertAtHead(head, 0)`, then `insert_kth(head, 2, 99)` on the result. Before I show you anything — write down the final list, in order."*

Give 90 seconds individual, silent, then take the answer by show of hands before revealing.

**The trace**

1. `insertAtHead(head, 0)`: `0 → 1 → 3 → 5 → NULL`
2. `insert_kth(head, 2, 99)`: walk to `count == k-1 == 1` — that's the node holding `1`. Insert `99` right after it.

> **Final list: `0 → 1 → 99 → 3 → 5 → NULL`.**

**When it goes wrong**

| If… | Do this |
|---|---|
| Students predict against the *original* 3-node list instead of the post-insert 4-node list | Point out: `insert_kth` ran *second* — it always operates on whatever the list looks like *right now*, not the starting list |
| Someone places `99` at index 2 of the *original* list (landing after `3` instead of after `1`) | Walk the `count == k-1` rule again explicitly on the new 4-node list, node by node |

**Debrief line:**
> *"Same rule as Activity 1, just applied to a list that had already changed once. Sequence matters — every operation runs on the list as it exists at that exact moment, not the list you started with."*

**Cut rule:** Skip the individual write-down and run it as a single cold-call trace on the board instead.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering the four insertion positions, their complexities, and the k-1 stopping condition. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — on paper before anyone leaves:

> Write the two lines of code that insert an already-created node `n` at the head of a non-empty list, starting from `head`.
> **Answer:** `n->next = head;` then `head = n;`

**Homework:** Re-attempt today's four insertion dry runs from memory — write all four functions (head, tail, Kth, before-x) from scratch without looking back at the slides, then check against the deck.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Inserting at the head of a linked list is O(n), "because you have to shift everything" | Habit carried over from array insertion | The Hook — drawing the linked-list version and counting how many *existing* nodes actually move (zero) |
| The traversal for `insert_kth` should stop at `count == k` | "Insert at position k" sounds like "stop when you reach index k" | ALS Activity 1 — tracing exactly where the off-by-one lands the new node |
| Every insertion needs a full traversal | Insert-at-tail and insert-at-Kth both traverse, so it feels universal | Insert-at-head's O(1) case, contrasted explicitly on the Complexity Summary table |
| Once one operation is understood, chaining two together is "just doing them separately" | Each operation is taught and tested in isolation | ALS Activity 2 — the second operation must run on the *already-changed* list, not the original |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Split out from the original 60-min "Session 39 — Insertion, Deletion," which covered both insertion and deletion together — see `sem-3-sequence.md`. Deletion now has its own session (9).
- **Two ALS activities this session:** Activity 1 is Spot the Bug (the `k-1` off-by-one), Activity 2 is Predict the Output (chaining `insertAtHead` then `insert_kth`, reusing Activity 1's lesson under new numbers).
- **The Classroom Quiz now runs last, right before the Exit Ticket** — matching the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank covering the four insertion positions and their complexities.
- **Activity 1 depends on Slide Block A's `count == k - 1` beat landing first** — if that beat got rushed, spend 30 extra seconds re-deriving it before running the activity, or the bug will look arbitrary rather than inevitable.
- **This is session 8 of the Sem-3 sequence** (see `sem-3-sequence.md`), split from the original combined Insertion+Deletion session. Session 9 (Deletion in Linked List) picks up immediately after and assumes today's four insertion operations are solid — particularly the `count == k-1` pattern, which deletion reuses with a one-node-further stopping condition.
- **Original file also had a third activity** (Predict-the-Output: chained insert-then-*delete*) that needed both insertion and deletion taught — it's been moved to Session 9, where it now serves as that session's synthesis activity instead.
