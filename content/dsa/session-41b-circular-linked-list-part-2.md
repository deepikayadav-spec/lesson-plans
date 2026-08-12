# Session 41b — Circular Linked List (Part 2 of 2)

**Duration** 31 min · **Topic** Linked List — Deletion, Termination Bug & Applications · **Prerequisite** Session 41a — Circular Linked List, Part 1 (structure, insertion) · **Session type** Concept lecture

<!-- Split note: continues session-41 (original 60 min) right after the Classroom Quiz. This part covers all three deletion positions, the deck's own named "Infinite Loop Risk" via a Spot-the-Bug on the traversal termination condition, and the closing traversal/search/applications wrap-up. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Circular Linked List | https://docs.google.com/presentation/d/1DBElXcQ0Nd0rmmYHsmFgI3fd0pxSB-AmTr4_JgWEG30/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Trace deletion of the first node, the last node, and a specific node of a circular singly linked list by hand. *(APPLYING)*
2. Analyze the time and space complexity of every insertion, deletion, traversal, and search operation on a circular linked list. *(ANALYZING)*
3. Evaluate when a circular linked list is the right structure to reach for, using its stated advantages and disadvantages. *(EVALUATING)*

<!-- placement: inferred — phrased from the deck's own Key Takeaways slides (89-93) and Complexity/Applications/Advantages/Disadvantages slides (84-88) -->

---

## Warm-Up Poll — Retrieval Practice on Session 41a (0–5 min)

Say: *"Four quick ones on insertion before we remove nodes instead."*

**Q1.** What's the defining sentence of a circular linked list?
`A` Every node has two pointers · `B` The last node's `next` points back to the first node instead of NULL · `C` It's sorted in a circle · `D` It has no head
→ *Read:* B.

**Q2.** Inserting at the beginning of a circular list is what complexity?
`A` O(1) · `B` O(n) · `C` O(log n) · `D` O(1) amortized
→ *Read:* B — you still must walk to the last node to repoint it.

**Q3.** The loop condition for "insert at end" walks until:
`A` `temp->next == nullptr` · `B` `temp->next == head` · `C` `temp == tail` · `D` `temp->data == 0`
→ *Read:* B.

**Q4.** In Part 1's confidence check, what made circular-list insertion O(n) despite looking like a DLL operation?
→ *Read:* Open response — reconnects to the "still have to find the last node" reasoning before deletion mirrors it.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"Insertion had to find the last node to repoint it forward. Deletion has the same job in reverse — plus a new danger: nothing in this list will ever hand you a NULL to stop on."*

---

## Slide Block C — Deletion: First, Last, Specific Node (7–17 min) — DELIVER SLIDES AS-IS

Covers: Deletion of the first node (dry run + code) → deletion of the last node (dry run + code) → deletion of a specific node (dry run + code).

**Beats to emphasise**

- **Delete first:** same shape as insert-at-beginning — you still must walk to the last node to repoint its `next` at the new head, so it's **O(n)**, not O(1). Contrast explicitly against Session 40: DLL's `delete_head` *was* O(1), because DLL nodes carry their own `prev` pointer — a circular singly list has no such shortcut.
- **Delete last:** walk until `temp->next->next == head` (the deck's own loop condition) — that "look two nodes ahead" condition is easy to get off-by-one on. Say it slowly, twice.
- **Delete a specific node:** the cleanest of the three, and the one the next activity dry-runs live — find `prev` (the node just before the target), redirect `prev->next` to `target->next`, delete `target`.
- All three deletion functions guard the single-node case (`head->next == head`) before doing anything else. Call this out as the edge case students will forget until their own code crashes on it.

**Checkpoint (at 17 min)** — cold-call:
> *"Why does every deletion function in this deck check `if (head->next == head)` before doing anything else?"*
> **Answer:** That's the one-node list — the node is its own `next`. Deleting it just sets `head` to `nullptr`; there are no neighbours to relink.

---

## ⚡ Activity 2 — Dry-Run Relay: Delete a Specific Node (17–23 min)

**Format:** Live Coding / Dry-Run Relay (whiteboard, pairs) · **Exposes:** whether students can hold a `prev` pointer through a circular structure without a NULL to anchor against — using the deck's own worked example: circular list `Head → 10 → 20 → 25 → 30 → (back to 10)`, deleting node `25`.

**Setup line (say this):**
> *"Grab a partner. Draw four boxes in a circle — 10, 20, 25, 30 — with the last arrow curving back to 10, and Head pointing at 10. Now walk your finger through deleting node 25. One of you narrates each step, the other draws the arrow. Three steps only."*

**What students do:** Step 1 — traverse from head, tracking `prev`, until `prev`'s `next` is the target (25); `prev` lands on 20. Step 2 — redirect `prev->next` to `target->next` (20's arrow now points to 30). Step 3 — erase node 25 from the drawing. Walk the room and spot-check 3–4 pairs' drawings.

**How it surfaces:** Two errors show up reliably. Most common: students stop the traversal one step too late and point `prev` at 25 itself instead of 20 (an off-by-one). Second: they forget the circular wrap and draw 30's arrow going to NULL instead of back to 10.

**Debrief line:**
> *"Notice you never once wrote NULL. You found `prev`, you re-pointed one arrow, you deleted one box. That's the entire deletion — circularity didn't make it harder, it just took away your usual anchor."*

**Cut rule:** If running short, run it once as a single dry-run on the board with the instructor drawing and the whole class calling out each step, instead of pair work. Keep the debrief line verbatim.

---

## ⚡ Activity 3 — Spot the Bug: Termination Condition (23–27 min)

**Format:** Spot the Bug · **Exposes:** the single most dangerous circular-list mistake — using a NULL check to stop traversal — which the deck's own Disadvantages slide names outright as "Infinite Loop Risk."

**Setup line (say this):**
> *"Here's a traversal function for our circular list. It compiles. It will not stop. Find out why before I run it."*

Show on screen:
```cpp
void display() {
    Node* temp = head;
    while (temp != nullptr) {      // <-- bug
        cout << temp->data;
        temp = temp->next;
    }
}
```

**What students do:** 30 seconds silent, then hands up with the fix.

**How it surfaces:** If someone says "add a NULL at the end of the list" — that's missing the point. Redirect: *"The list isn't broken. In a valid circular list, NULL never appears by design. The stopping condition is what's broken."*

**Debrief line:**
> *"Every traversal and search function in this deck uses `do { ... } while (temp != head)` — never a NULL check. In a circular list, NULL never comes. If your loop is waiting for it, you haven't written a bug you'll get an error for — you've written an infinite loop."*

**Cut rule:** If running out of time, skip the pair discussion — read the code aloud, cold-call one student for the fix, deliver the debrief line, move on.

---

## Slide Block D — Traversal, Search, Complexity, Applications, Key Takeaways (27–30 min) — DELIVER SLIDES AS-IS

Covers: Traversal → Searching → Complexity Analysis tables → Applications / Advantages / Disadvantages → Key Takeaways.

**Beats to emphasise**

- This block is mostly recap of what earlier blocks already showed in code — move fast, deliver the slides as-is, don't re-derive anything.
- The one idea to land formally here: both `display()` and `search()` use `do { ... } while (temp != head)` — a **do-while**, not a `while` — because in a circular list you must process the head node *before* checking whether you've looped back to it. This is the fix from Activity 3; state it plainly.
- Applications slide: Round-Robin Scheduling, circular buffers/queues, multiplayer board games, audio/video playlists — check it against the list students built in Part 1's Activity 1.
- Advantages/Disadvantages is a good "so when do I reach for this" close. Infinite Loop Risk has now come up twice (Activity 3, and again here) — that repetition is deliberate, don't shorten it.

**Checkpoint** — quick, no fixed minute:
> *"One line: what's the time complexity of `search()` on a circular linked list, and why can it never be better?"*
> **Answer:** O(n) — the target could be the very last node before you loop back to head, so worst case you touch every node once.

---

## Exit Ticket (30–31 min)

> On paper: draw a 3-node circular linked list (10 → 20 → 30 → back to 10) and mark exactly where `head` points and where node 30's `next` pointer points. Then answer: is there a NULL anywhere in your drawing?
> **Answers:** `head` points to 10; node 30's `next` points back to 10 (not NULL). No NULL anywhere — that absence *is* the definition of "circular."

Homework: re-attempt the dry run from memory. <!-- placement: inferred -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A `while (temp != NULL)` loop is a safe way to traverse any linked list | It works for every non-circular list they've built so far | Activity 3 — run it and watch it hang |
| The `prev` pointer used in Activity 2's deletion is a stored field on the node | Session 40's DLL really did store a `prev` field, and the name is reused here | Point out in Slide Block C: this `prev` is just a local pointer the function keeps while walking; circular singly nodes only ever store `next` |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz.**
- **Pacing risk:** Slide Block D packs five topics into 3 minutes on purpose — it's pure recap of what's already been taught live in earlier blocks plus Activity 3. Do not slow down to re-teach here, or the session overruns.
- Keep Session 40's DLL summary tables visible or sketched on a side board — the O(1) vs O(n) contrasts only land if students can see last session's numbers next to this session's.
- Have a pre-drawn circle template (or sticky notes) ready before Activity 2 — setting it up live costs minutes you don't have.
- <!-- placement: inferred --> The raw slide text for "Deletion of a Specific Node" and "Searching" carries a stray leftover title ("Deletion of the Last Node — Defining Class Node") on two slides in the source deck; the code shown on those slides is unambiguous (delete-by-value and search-by-value respectively), so the Slide Block descriptions above follow the code, not the mislabeled titles. Worth flagging to the content team.
