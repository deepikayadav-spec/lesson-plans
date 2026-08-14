# Session 11 — Insertion in Doubly Linked List

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Doubly Linked List — Insertion (Head, Tail, Before Kth Node) · **Prerequisite** Session 10 — Introduction to Doubly Linked List
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Doubly Linked List - Traversal, Insertion, Deletion (insertion half) | https://docs.google.com/presentation/d/1CtyEsYixyAXlaQ-wZUaqsxFZx4XQF1JPPIJ18LZ9YKg/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Implement insertion at the head, tail, and before the Kth node of a doubly linked list. *(APPLYING)*
2. State the time complexity of each DLL insertion position and compare it to its Session 8 singly-linked-list counterpart. *(ANALYZING)*
3. Explain the one DLL-specific extra step needed for head insertion (`head->prev = temp`) that a singly linked list never needs. *(UNDERSTANDING)*
4. Correctly perform all four pointer updates required for inserting before the Kth node. *(APPLYING)*
5. Identify which single missing pointer update breaks backward traversal without affecting forward traversal. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 10 (3–7 min) · ALS: Polling

5 questions on **Session 10 (Introduction to Doubly Linked List)**. ~45 s each, project the distribution, never name individuals.

**Q1.** What two fields does a DLL node have that a singly linked list node doesn't?
`A` `data` and `next` · `B` `prev` only · `C` `prev` and a second `data` field · `D` Nothing — they're identical
→ **B.** *(A DLL node has `prev`, `data`, `next` — the new field is `prev`.)*

**Q2.** In `arrayToDLL`, what are the two links set at each step?
`A` `cur->next = temp` only · `B` `cur->next = temp` and `temp->prev = cur` · `C` `temp->next = cur` and `cur->prev = temp` · `D` Only `temp->prev = cur`
→ **B.**

**Q3.** What's `arrayToDLL`'s time and space complexity?
`A` O(n) time, O(1) space · `B` O(1) time, O(n) space · `C` O(n) time, O(n) space · `D` O(n²) time, O(n) space
→ **C.**

**Q4.** If a DLL is built with every `next` link correct but every `prev` link left as default `null`, what happens when you traverse forward from the head?
`A` It crashes immediately · `B` It works perfectly — forward traversal never touches `prev` · `C` It prints nothing · `D` It loops forever
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about DLL construction from an array?
`A` It touches `prev` and `next` at every step except the first node · `B` It's the same time complexity as the singly-linked-list version · `C` It requires sorting the array first · `D` A missing `prev` link is silent until backward traversal is attempted
→ **A, B, D.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–9 min)

Put this on the board:

> *"Session 8: insert at head of a singly linked list. Two lines — `n->next = head; head = n;`. Today, same operation, doubly linked list. How many lines?"*

Let guesses land. Reveal:

```cpp
n->next = head;
head->prev = n;      // <- the new one
head = n;
```

> *"One more line. That's it, structurally — but that one line is where every mistake in today's session will hide. Every insertion position gets exactly one extra 'don't forget the other direction' step on top of what you already know from Session 8."*

---

## Slide Block B (9–19 min) — DELIVER SLIDES AS-IS

Covers: Insertion in a Doubly Linked List — the three types (head, tail, before the Kth node) — each with problem statement, dry-run diagram, C++ code, and complexity; closing with the Insertion Complexity Summary table.

**Beats to emphasise**

- **Insert at head**: create the new node with `next = head`, then the one DLL-specific extra step — `head->prev = temp` — before making `temp` the new head. Still O(1); the only change from Session 8's singly-linked-list version is that one extra pointer fix.
- **Insert at tail**: walk from `head` until `tail->next == nullptr` (same O(n) walk as Session 8's `insertAtTail`), then link both directions: `temp->prev = tail` and `tail->next = temp`.
- **Insert before the Kth node**: traverse to the node currently *at* position `k` (`temp`), grab its `prev` as `back`, then splice the new node in between — `back->next = n`, `temp->prev = n`, plus the new node's own `n->next = temp` and `n->prev = back`. **Four pointer updates total** — walk through each one on the board rather than skipping to the finished diagram.
- Close with the **Complexity Summary**: head O(1)/O(1), tail O(N)/O(1), Kth position O(k)/O(1) — same time-complexity shape as Session 8's singly-linked-list insertions, but every single one now touches two pointers per link instead of one.

**Checkpoint (at 19 min)** — show of hands:
> *"Insert-at-head in a DLL is still O(1), same as a singly linked list — what's the one extra step a DLL insert-at-head needs that a singly linked list doesn't?"*
> **Answer:** You must also set the old head's `prev` pointer to point back at the new node (`head->prev = temp`). A singly linked list has no `prev` to fix, so this is the one genuinely new step.

---

## ⚡ ALS Activity 1 — Guided Table Build: Trace Insert-Before-Kth (19–28 min)

**ALS format:** Guided Table Build — the class fills in all four pointer updates for a Kth-position insertion, cell by cell, cold-called for each one. Chosen right after Slide Block B because four simultaneous pointer updates is the densest single step in this session, and it only becomes procedural (rather than intimidating) once students have written each one out themselves, in order.

**Setup line:**
> *"DLL: `10 ⇄ 20 ⇄ 30 ⇄ 40`. Insert `99` before the node currently at position 2 (0-indexed — that's `30`). Four pointer updates, one at a time. I point at a row, you tell me the line of code."*

**The completed table**

| Step | What it does | Code |
|---|---|---|
| 1 | Find `temp` at position 2 and its predecessor `back` | `temp = node holding 30; back = temp->prev` (node holding `20`) |
| 2 | Link `back` forward to the new node | `back->next = n` |
| 3 | Link the new node forward to `temp` | `n->next = temp` |
| 4 | Link the new node backward to `back` | `n->prev = back` |
| 5 | Link `temp` backward to the new node | `temp->prev = n` |

> **Result:** `10 ⇄ 20 ⇄ 99 ⇄ 30 ⇄ 40`.

**How it surfaces:** ask, before revealing row 5: *"We've linked the new node in both directions already — rows 2, 3, 4. Is anything still missing?"* Most rooms miss that `temp->prev` still points at `back`, not at the new node, until this is asked directly.

**When it goes wrong**

| If… | Do this |
|---|---|
| Students think 4 links means 4 nodes change | Only 2 existing nodes (`back` and `temp`) plus the new node get pointer updates — count the actual lines, not the node count |
| Row order gets confused | Emphasise: order doesn't actually matter for correctness here, *as long as* `back` and `temp` are captured before any pointer is overwritten — but doing it in a fixed order avoids losing track |

**Debrief line:**
> *"Four lines, every single time you insert into the middle of a DLL. Miss row 5 specifically and forward traversal still looks perfect — it's only backward traversal that quietly breaks, exactly like Session 10's construction bug."*

**Cut rule:** Skip rows 3-4 verbally (state them directly) and focus the cold-calling on rows 2 and 5 — those are the ones most often forgotten.

---

## ⚡ ALS Activity 2 — Silent Diagnose, Named Reveal: The Missing Fourth Line (28–37 min)

**ALS format:** Silent Diagnose, Named Reveal — an insert-before-Kth implementation with one of the four pointer updates removed goes on the board; students must identify exactly which line is missing and what breaks. Chosen as the closing activity because it stress-tests ALS Activity 1's four-update discipline against real code, immediately after building the muscle memory for it.

**Setup line:**
> *"This is insert-before-Kth, except one of the four lines from the table we just built is missing. Tell me which one, and exactly what breaks."*

```cpp
void insertBeforeKth(Node*& head, int k, int val){
    Node* temp = head;
    for (int i = 0; i < k; i++) temp = temp->next;
    Node* back = temp->prev;
    Node* n = new Node(val);

    back->next = n;
    n->next = temp;
    n->prev = back;
    // missing: temp->prev = n;
}
```

Give 60 seconds silent, then cold-call: *"Trace forward from head, then trace backward from `temp`. What do you see each time?"*

**The diagnosis:** Forward traversal from `head` is completely correct — every `->next` link was set. Backward traversal starting *at or after* `temp` is broken: `temp->prev` still points at `back`'s old predecessor relationship, not at the newly inserted node `n` — so walking backward from `temp` skips `n` entirely, as if it were never inserted.

**When it goes wrong**

| If… | Do this |
|---|---|
| Students expect forward traversal to also break | Walk the forward trace live — every `->next` pointer really was set correctly; only one of four lines is missing, and it's a `prev` line |
| Nobody can name which specific line is missing | Point back at ALS Activity 1's table, row 5 — the exact line that's absent here |

**Debrief line:**
> *"Same bug family as Session 10, one session later, in a denser operation. Forward traversal is not proof that a DLL is correctly wired — only checking `prev` in both directions actually proves it."*

**Cut rule:** Skip the silent diagnose phase, walk the forward/backward trace as a class discussion, then reveal the missing line directly.

---

## Classroom Quiz (37–42 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering the three DLL insertion positions, their complexities, and the four-pointer-update pattern for Kth-position insertion. -->

---

## Exit Ticket + Homework (42–48 min)

**Exit ticket** (~1 min) — on paper before anyone leaves:

> List all four pointer updates needed to insert a new node before the node currently at position k in a DLL.
> **Answer:** `back->next = n`, `n->next = temp`, `n->prev = back`, `temp->prev = n` (where `back = temp->prev` and `temp` is the node currently at position k).

**Homework:** Re-attempt today's three insertion dry runs from memory — head, tail, and before-Kth — on a DLL of your own choosing, drawing every `prev` and `next` arrow explicitly.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| DLL insertion at the head costs more than a singly linked list's, since there's an extra pointer | Reasonable-sounding intuition that "more pointers = more complexity class" | Slide Block B's checkpoint — it's still O(1), just one more *constant-time* line, not a new order of growth |
| Inserting before the Kth node only needs to update the new node's own two pointers | The new node's links feel like "the point" of insertion | ALS Activity 1 — rows 2 and 5 update the *existing* neighbours, not just the new node |
| Forward traversal working correctly proves an insertion was done right | Forward traversal is the default way most people sanity-check a list | ALS Activity 2 — forward is perfect, backward is silently broken |
| A DLL gives O(1) access to the tail because "you have two pointers now" | Confusing "bidirectional traversal" with "instant access to both ends" | Insert-at-tail's checkpoint — still O(n) to walk there in the first place, without a stored tail reference |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Split out from the original 60-min "Session 40 — Doubly Linked List - Traversal, Insertion, Deletion" — see `sem-3-sequence.md`. Session 10 (Introduction) covers construction; Session 12 (Deletion) covers deletion.
- **Two ALS activities this session:** Activity 1 is Guided Table Build (all four pointer updates, traced together), Activity 2 is Silent Diagnose → Named Reveal (finding the missing fourth line in real code). Both new — the original file's activities were split between construction (now Session 10) and deletion (now Session 12), leaving this insertion-focused session without dedicated activities of its own.
- **This is session 11 of the Sem-3 sequence** (see `sem-3-sequence.md`) — the second of three sessions replacing the original combined DLL session.
- **The four-pointer-update pattern (ALS Activity 1) is this session's single highest-value idea** — it's exercised twice (the guided trace, then the bug hunt) by design. Protect both over the Slide Block B walkthrough if the session runs behind — the checkpoint questions there can be answered in one sentence without the full dry run if time is tight.
