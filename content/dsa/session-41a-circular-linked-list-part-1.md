# Session 41a — Circular Linked List (Part 1 of 2)

**Duration** 39 min · **Topic** Linked List — Circular Linked List: Structure & Insertion · **Prerequisite** Doubly Linked List — traversal, insertion, deletion (Session 40) · **Session type** Concept lecture

<!-- Split note: original session-41 ran 60 min. Split right after the Classroom Quiz. Part 1 covers what makes a list circular, the running example, and all three insertion positions. Part 2 (session-41b) covers all three deletion positions, the infinite-loop termination-condition bug, traversal/search, and the applications/advantages close. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Circular Linked List | https://docs.google.com/presentation/d/1DBElXcQ0Nd0rmmYHsmFgI3fd0pxSB-AmTr4_JgWEG30/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define a circular linked list and distinguish circular singly from circular doubly linked lists. *(REMEMBERING)*
2. Explain why a circular list has no NULL anywhere and why its traversal needs a different termination condition than a plain linked list. *(UNDERSTANDING)*
3. Trace insertion at the beginning, end, and a specific position of a circular singly linked list by hand. *(APPLYING)*

*(Deletion, the termination-condition bug, and traversal/search are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval on Session 40 (0–7 min)

Say: *"Eight quick ones on last session's Doubly Linked List before we move on. No names, just show me the room."*

**Q1.** In a Doubly Linked List, each node stores data plus how many pointers?
`A` 0 · `B` 1 · `C` 2 · `D` 3
→ *Read:* If C isn't near-unanimous, redraw the `prev`/`data`/`next` node on the board before starting today's slides — today's node only has one pointer, and that contrast needs to be crisp.

**Q2.** What is the time complexity of inserting a new node at the *head* of a DLL?
`A` O(1) · `B` O(n) · `C` O(k) · `D` O(log n)

**Q3.** The deck's `insert_tail` function walks from `head` until it finds the last node, then attaches the new one there. What's its time complexity?
`A` O(1) · `B` O(n) · `C` O(k) · `D` O(log n)
→ *Read:* If many pick O(1) because "tail" sounds instant, flag it — that exact misconception resurfaces in today's Slide Block B when a circular list's "insert at end" also has to walk the whole list first.

**Q4.** When `delete_head` removes the head node of a DLL, besides moving `head` to `head->next`, what else must it update?
`A` Nothing else · `B` The new head's `prev` pointer, set to nullptr · `C` The old head's `next` pointer · `D` The tail pointer

**Q5.** In `delete_kth`, when the target node has both a `back` neighbour and a `front` neighbour (a true middle node), which pointer updates actually relink the list?
`A` `back->next = front` and `front->prev = back` · `B` `delete_head` and `delete_tail` are both called · `C` only `back->next = front` · `D` only `front->prev = back`

**Q6.** What is the time complexity of inserting a node before the k-th node in a DLL?
`A` O(1) · `B` O(n) · `C` O(k) · `D` O(k²)

**Q7.** *(MSQ — pick up to 2)* Per last session's own summary tables, which of these run in O(1) time on a DLL?
`A` Insert at head · `B` Insert at tail · `C` Delete at head · `D` Delete at k-th position
→ *Read:* If this is shaky, put last session's two summary tables back on screen for 30 seconds before Slide Block A — today's circular-list numbers only land as a contrast to these.

**Q8.** In the deck's "Music Playlist" real-world example, what does the `head` of the list represent?
`A` The last song queued · `B` The first song to play · `C` A randomly chosen song · `D` The song currently playing

**Running it** — poll tool, ~40 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–10 min)

Say: *"A group of friends is playing a board game, sitting in a circle. Player 4 just finished their turn. Whose turn is next?"* Let them answer (Player 1, or whoever's physically next — the point is there's no "last player" who ends the game by finishing).

Then: *"That's today's entire session. Every linked list you've built so far — singly, doubly — ends. Somewhere, a pointer hits NULL and stops. Today's list doesn't. The last node points straight back to the first, and the game just keeps going."*

---

## Slide Block A — Introduction & Types (10–18 min) — DELIVER SLIDES AS-IS

Covers: What a circular linked list is → Circular Singly LL vs Circular Doubly LL → node template code (singly) → the three ways to insert, previewed → the running example list (10, 20, 30) used through every dry run that follows.

**Beats to emphasise**

- The one sentence that matters: **the last node's `next` points back to the first node, instead of NULL.** Everything else this session follows from that sentence.
- Contrast against last session directly: a DLL had two ends (head *and* tail) with NULL sitting at each. A circular singly list has only a `next` pointer per node — same shape as a plain singly list — but there is no NULL anywhere in it.
- A Circular Doubly LL also exists (both `prev` and `next`, with `last->next = first` **and** `first->prev = last`) — mention it, but flag explicitly that every dry run and every line of code from here on is the **singly** version. Don't let students expect `prev` pointers to show up in today's code.
- Point at the running example (10, 20, 30) and say it out loud: "remember these three boxes — every insertion dry run today starts from this exact list."

**Checkpoint (at 18 min)** — cold-call:
> *"In a circular singly linked list of 3 nodes, what does the third node's `next` pointer hold?"*
> **Answer:** The address of the first node (head) — never `nullptr`.

---

## ⚡ Activity 1 — Real-World Callout (18–23 min)

**Format:** Real-World Callout · **Exposes:** whether students can generalise "no beginning, no end, last connects back to first" beyond the node diagram they just saw.

**Setup line (say this):**
> *"Thirty seconds — think of one everyday system that has no real 'first' or 'last' turn, where once you reach the end you go right back to the start. Shout it out."*

**What students do:** Call out examples. You write them on the board — no more than 8. (Expect things like a music playlist on repeat, turn order in a board game, a merry-go-round, CPU round-robin scheduling if someone's technical.)

**How to handle wrong answers:** If someone names something linear — e.g. "a queue at a ticket counter" — push once: *"Does it loop back to the first person once the last one is served? No? Then that's linear, not circular. What's the loop-back?"*

**Debrief line:**
> *"Every one of those is a circular linked list in disguise — a node, or a person, or a turn, whose 'next' eventually points back to where you started. That's the entire definition, and there's no NULL in it anywhere. Hold onto your list — we'll check it against the textbook version near the end of Part 2."*

**Cut rule:** If running late, take 3 callouts instead of an open floor and skip the push-for-linear step. Do not cut the debrief line.

---

## Slide Block B — Insertion: Beginning, End, Specific Position (23–31 min) — DELIVER SLIDES AS-IS

Covers: Insertion at the beginning (dry run + code) → insertion at the end (dry run + code) → insertion at a specific position (dry run + code).

**Beats to emphasise**

- **Insert at beginning:** the new node's `next` points to the old head — that part's instant. But you still have to walk the *entire* list once to find the current last node and re-point *its* `next` to the new head. That traversal is the part students forget; say clearly that this makes it **O(n)**, not O(1) the way DLL head-insert was last session.
- **Insert at end:** walk from head until `temp->next == head` (the deck's own loop condition) — that node is the last one. Attach the new node there, then close the circle by pointing the new node's `next` back to head.
- **Insert at a specific position:** same idea as any singly list — walk `position - 1` steps and splice in — but flag that position 1 is special-cased by calling `insertAtBeginning` directly (the deck's own code) rather than looping into it.
- Run at least the "insert at beginning" C++ snippet live on screen; the walk-to-last-node loop is the one line worth typing out loud, word by word.

<!-- placement: inferred — the code shown on the "Insertion at the Beginning" slide appears to have two code panels merged by the raw extraction (an if/else block, followed by a second, seemingly redundant traversal block); the approach description above is taken from the deck's own numbered steps (Create node → set next → traverse to last node → update last node's next), not from that specific garbled snippet -->

**Checkpoint (at 31 min)** — show hands:
> *"Inserting at the beginning of a circular list — O(1) or O(n)?"*
> **Answer:** O(n). Attaching the new node is instant, but you must still walk the whole list to find the old last node and repoint it to the new head (deck's own complexity table, "Insertion At Beginning" — O(n) time, O(1) space).

---

## Classroom Quiz (31–36 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Fist-to-Five Confidence Check (36–39 min)

**Why this strategy here:** Part 1's biggest surprise is that circular-list insertion is O(n), not O(1), despite superficially resembling DLL operations that were O(1). A quick confidence check catches whether that contrast actually landed before Part 2 adds deletion's extra branching on top.

**Run it (3 minutes):**
> *"Fist to five: how confident are you that you could explain, right now, why inserting at the beginning of a circular list is O(n) and not O(1)? Show me."*

If the average is below 3, spend 30 seconds re-walking the "you still have to find the last node to repoint it" idea before moving on.

> *"Hold that number. Part 2 does the same operation in reverse — deletion — and adds one more wrinkle: how do you even know when to stop, if there's no NULL to stop at?"*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A circular list must have a NULL somewhere, "just at the end" | Every prior list (singly, doubly) they've built ended in NULL | Block A checkpoint — the last node's `next` IS the head's address, never `nullptr` |
| Inserting at the "start" of a circular list is O(1), same as a DLL | Session 40's DLL `insert_head` really was O(1) | Block B checkpoint — walk through why a circular singly list still needs a full traversal to find and repoint the last node |
| Circular Doubly LL and Circular Singly LL are interchangeable in the code shown | Both were introduced back-to-back on the same slides | Flagged explicitly in Block A: every dry run and code sample after the node template is the singly version only |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz.**
- **This is the fourth linked-list session in a row** — lean on direct contrast against Session 40's DLL numbers rather than fresh framing; the "wait, that's O(n) now?" surprise is the actual hook keeping attention up.
- Part 2 (session-41b) reuses the running example list (10, 20, 30) directly for its deletion dry runs.
