# Session 13 — Circular Linked List

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Circular Linked List — Structure, Insertion, Deletion, Traversal · **Prerequisite** Session 12 — Deletion in Doubly Linked List
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Circular Linked List | https://docs.google.com/presentation/d/1DBElXcQ0Nd0rmmYHsmFgI3fd0pxSB-AmTr4_JgWEG30/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define a circular linked list and explain why it has no NULL anywhere. *(REMEMBERING)*
2. Explain why a circular list's traversal needs a `do...while (temp != head)` termination condition instead of a NULL check. *(UNDERSTANDING)*
3. Trace insertion at the beginning, end, and a specific position of a circular singly linked list. *(APPLYING)*
4. Trace deletion of the first node, the last node, and a specific node of a circular singly linked list. *(APPLYING)*
5. Explain why insert/delete-at-beginning is O(n) on a circular singly list, unlike a DLL's O(1) head operations. *(ANALYZING)*
6. Evaluate when a circular linked list is the right structure to reach for, using its stated advantages and disadvantages. *(EVALUATING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 12 (3–7 min) · ALS: Polling

5 questions on **Session 12 (Deletion in Doubly Linked List)**. ~45 s each, project the distribution, never name individuals.

**Q1.** What's the time complexity of deleting the head of a DLL?
`A` O(n) · `B` O(1) · `C` O(log n) · `D` O(k)
→ **B.** *Read:* Hold onto this — today's circular list breaks this exact pattern.

**Q2.** Why does `delete_kth` on a DLL branch into three separate cases instead of one general formula?
`A` It doesn't need to · `B` The general formula assumes both neighbours exist, which fails at the head and tail · `C` Because `k` might be negative · `D` To make the code longer
→ **B.**

**Q3.** After deleting the tail of a DLL, what must the new tail's `next` pointer be set to?
`A` Whatever it already was · `B` `NULL`, explicitly · `C` The old tail's address · `D` The head's address
→ **B.**

**Q4.** What's the time complexity of inserting before the Kth node of a DLL?
`A` O(1) · `B` O(k) · `C` O(n²) · `D` O(log k)
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about DLL operations from Sessions 10-12?
`A` Every insertion and deletion is O(1) space · `B` A missing `prev` update is silent until backward traversal · `C` DLL construction is O(n) time, O(1) space · `D` `delete_kth`'s general formula only runs in the true middle case
→ **A, B, D.** *(C is false — construction is O(n) space, one new node per element.)*

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Say: *"A group of friends is playing a board game, sitting in a circle. Player 4 just finished their turn. Whose turn is next?"* Let them answer — Player 1, or whoever's physically next. The point: there's no "last player" who ends the game by finishing.

> *"That's today's entire session. Every linked list you've built so far — singly, doubly — ends. Somewhere, a pointer hits NULL and stops. Today's list doesn't. The last node points straight back to the first, and the game just keeps going."*

---

## Slide Block A — Introduction & Types (10–16 min) — DELIVER SLIDES AS-IS

Covers: What a circular linked list is → Circular Singly LL vs Circular Doubly LL → node template code (singly) → the running example list (10, 20, 30) used through every dry run that follows.

**Beats to emphasise**

- The one sentence that matters: **the last node's `next` points back to the first node, instead of NULL.** Everything else follows from that sentence.
- Contrast against Sessions 10-12 directly: a DLL had two ends with NULL sitting at each. A circular singly list has only a `next` pointer per node — same node shape as a plain singly list — but there is no NULL anywhere in it.
- A Circular Doubly LL also exists (both `prev` and `next`, wrapped both ways) — mention it once, but flag explicitly that every dry run and every line of code from here on is the **singly** version.
- **Quick tie-in:** *"Name one everyday thing that has no real 'first' or 'last' — once you reach the end, you loop right back to the start."* One or two shout-outs (music playlist on repeat, turn order in a game, round-robin scheduling) — this is the whole session's applications list, previewed.

**Checkpoint (at 16 min)** — cold-call:
> *"In a circular singly linked list of 3 nodes, what does the third node's `next` pointer hold?"*
> **Answer:** The address of the first node (head) — never `nullptr`.

---

## Slide Block B — Insertion: Beginning, End, Specific Position (16–22 min) — DELIVER SLIDES AS-IS

Covers: Insertion at the beginning (dry run + code) → insertion at the end (dry run + code) → insertion at a specific position (dry run + code).

**Beats to emphasise**

- **Insert at beginning:** the new node's `next` points to the old head — that part's instant. But you still have to walk the *entire* list once to find the current last node and re-point *its* `next` to the new head. Say clearly this makes it **O(n)**, not O(1) the way DLL head-insert was.
- **Insert at end:** walk from head until `temp->next == head` — that node is the last one. Attach the new node there, then close the circle by pointing the new node's `next` back to head.
- **Insert at a specific position:** walk `position - 1` steps and splice in, same as any singly list — position 1 is special-cased by calling `insertAtBeginning` directly.

**Checkpoint (at 22 min)** — show hands:
> *"Inserting at the beginning of a circular list — O(1) or O(n)?"*
> **Answer:** O(n). Attaching the new node is instant, but you must still walk the whole list to find the old last node and repoint it to the new head.

---

## Slide Block C — Deletion: First, Last, Specific Node (22–28 min) — DELIVER SLIDES AS-IS

Covers: Deletion of the first node (dry run + code) → deletion of the last node (dry run + code) → deletion of a specific node (dry run + code).

**Beats to emphasise**

- **Delete first:** same shape as insert-at-beginning — you still must walk to the last node to repoint its `next` at the new head, so it's **O(n)**, not O(1). Contrast explicitly: DLL's `delete_head` *was* O(1), because DLL nodes carry their own `prev` pointer — a circular singly list has no such shortcut.
- **Delete last:** walk until `temp->next->next == head` — that "look two nodes ahead" condition is easy to get off-by-one on. Say it slowly, twice.
- **Delete a specific node:** the cleanest of the three, and the one ALS Activity 1 dry-runs live — find `prev` (the node just before the target), redirect `prev->next` to `target->next`, delete `target`.
- All three deletion functions guard the single-node case (`head->next == head`) before doing anything else.

**Checkpoint (at 28 min)** — cold-call:
> *"Why does every deletion function in this deck check `if (head->next == head)` before doing anything else?"*
> **Answer:** That's the one-node list — the node is its own `next`. Deleting it just sets `head` to `nullptr`; there are no neighbours to relink.

---

## ⚡ ALS Activity 1 — Live Coding / Dry-Run Relay: Delete a Specific Node (28–34 min)

**ALS format:** Live Coding / Dry-Run Relay (pairs at the board) — using the deck's own worked example: circular list `Head → 10 → 20 → 25 → 30 → (back to 10)`, deleting node `25`. Chosen right after Slide Block C because holding a `prev` pointer through a circular structure, with no NULL to anchor against, only lands once students have physically traced it.

**Setup line:**
> *"Grab a partner. Draw four boxes in a circle — 10, 20, 25, 30 — with the last arrow curving back to 10, and Head pointing at 10. Now walk your finger through deleting node 25. One of you narrates each step, the other draws the arrow. Three steps only."*

Step 1 — traverse from head, tracking `prev`, until `prev`'s `next` is the target (25); `prev` lands on 20. Step 2 — redirect `prev->next` to `target->next` (20's arrow now points to 30). Step 3 — erase node 25 from the drawing. Walk the room and spot-check 3–4 pairs' drawings.

**How it surfaces:** Two errors show up reliably. Most common: students stop the traversal one step too late and point `prev` at 25 itself instead of 20 (an off-by-one). Second: they forget the circular wrap and draw 30's arrow going to NULL instead of back to 10.

**Debrief line:**
> *"Notice you never once wrote NULL. You found `prev`, you re-pointed one arrow, you deleted one box. That's the entire deletion — circularity didn't make it harder, it just took away your usual anchor."*

**Cut rule:** Run it once as a single dry-run on the board with the instructor drawing and the whole class calling out each step, instead of pair work. Keep the debrief line verbatim.

---

## ⚡ ALS Activity 2 — Spot the Bug: Termination Condition (34–39 min)

**ALS format:** Spot the Bug — exposes the single most dangerous circular-list mistake: using a NULL check to stop traversal, which the deck's own Disadvantages slide names outright as "Infinite Loop Risk." Chosen as the closing activity because it's this session's highest-stakes idea and needs to be caught live, not just read about.

**Setup line:**
> *"Here's a traversal function for our circular list. It compiles. It will not stop. Find out why before I run it."*

```cpp
void display() {
    Node* temp = head;
    while (temp != nullptr) {      // <-- bug
        cout << temp->data;
        temp = temp->next;
    }
}
```

30 seconds silent, then hands up with the fix.

**How it surfaces:** If someone says "add a NULL at the end of the list" — that's missing the point. Redirect: *"The list isn't broken. In a valid circular list, NULL never appears by design. The stopping condition is what's broken."*

**Debrief line:**
> *"Every traversal and search function on a circular list uses `do { ... } while (temp != head)` — never a NULL check. In a circular list, NULL never comes. If your loop is waiting for it, you haven't written a bug you'll get an error for — you've written an infinite loop."*

**Cut rule:** Skip the pair discussion — read the code aloud, cold-call one student for the fix, deliver the debrief line, move on.

---

## Slide Block D — Traversal, Search, Complexity, Applications (39–41 min) — DELIVER SLIDES AS-IS

Covers: Traversal → Searching → Complexity Analysis → Applications / Advantages / Disadvantages. Mostly recap of what Blocks A–C already showed in code — move fast, don't re-derive.

**Beats to emphasise**

- The one idea to land formally: both `display()` and `search()` use `do { ... } while (temp != head)` — a **do-while**, because you must process the head node *before* checking whether you've looped back to it. This is the fix from ALS Activity 2 — state it plainly.
- Applications: Round-Robin Scheduling, circular buffers/queues, multiplayer board games, audio/video playlists — check against Slide Block A's quick tie-in examples.
- Search is **O(n)** — the target could be the very last node before looping back to head, so worst case you touch every node once.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering circular-list structure, the do-while termination condition, and insertion/deletion complexities. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — on paper before anyone leaves:

> Draw a 3-node circular linked list (10 → 20 → 30 → back to 10) and mark exactly where `head` points and where node 30's `next` pointer points. Then answer: is there a NULL anywhere in your drawing?
> **Answers:** `head` points to 10; node 30's `next` points back to 10 (not NULL). No NULL anywhere — that absence *is* the definition of "circular."

**Homework:** Re-attempt today's insertion and deletion dry runs from memory, on the same `10 → 20 → 30` starting list.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A circular list must have a NULL somewhere, "just at the end" | Every prior list (singly, doubly) they've built ended in NULL | Slide Block A's checkpoint — the last node's `next` IS the head's address, never `nullptr` |
| Inserting/deleting at the "start" of a circular list is O(1), same as a DLL | Sessions 10-12's DLL `insert_head`/`delete_head` really were O(1) | Slide Block B and C checkpoints — a circular singly list still needs a full traversal to find and repoint the last node |
| A `while (temp != NULL)` loop is a safe way to traverse any linked list | It works for every non-circular list built so far | ALS Activity 2 — run it and watch it hang |
| Circular Doubly LL and Circular Singly LL are interchangeable in the code shown | Both were introduced back-to-back on the same slides | Flagged explicitly in Slide Block A: every dry run and code sample after the node template is the singly version only |
| The `prev` pointer used in ALS Activity 1's deletion is a stored field on the node | Sessions 10-12's DLL really did store a `prev` field, and the name is reused here | Point out: this `prev` is just a local pointer the function keeps while walking; circular singly nodes only ever store `next` |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Converted from the original 60-min version, which covered six distinct operations plus traversal/search/complexity/applications — see below for what changed.
- **Two ALS activities this session:** Activity 1 is the Live Coding / Dry-Run Relay (delete a specific node, pairs at the board), Activity 2 is Spot the Bug (the NULL-check termination trap). The original third activity (Real-World Callout) is folded into a one-line quick tie-in inside Slide Block A instead of running as its own block.
- **The Classroom Quiz now runs last, right before the Exit Ticket** — moved from its original mid-session position (after Slide Block B) to match the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank covering circular-list structure, the do-while termination condition, and insertion/deletion complexities.
- **This is session 13 of the Sem-3 sequence** (see `sem-3-sequence.md`) — the first genuinely new-territory session after six sessions of linked-list basics (Sessions 7-12).
- **The NULL-check termination bug (ALS Activity 2) is the single most dangerous idea in this session** — the deck itself names "Infinite Loop Risk" as a named disadvantage. Protect this activity over Slide Block D's recap content if the session runs behind.
- **Keep Session 12's DLL complexity numbers visible or sketched on a side board during Slide Blocks B/C** — the O(1)-vs-O(n) contrasts only land if students can see the DLL numbers next to today's.
- **Have a pre-drawn circle template (or sticky notes) ready before ALS Activity 1** — setting it up live costs minutes you don't have.
- <!-- placement: inferred --> The raw slide text for "Deletion of a Specific Node" and "Searching" carries a stray leftover title ("Deletion of the Last Node — Defining Class Node") on two slides in the source deck; the code shown is unambiguous (delete-by-value and search-by-value respectively), so the descriptions above follow the code, not the mislabeled titles.
