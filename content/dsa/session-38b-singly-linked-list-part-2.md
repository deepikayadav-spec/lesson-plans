# Session 38b — Singly Linked List (Part 2 of 2)

**Duration** 38 min · **Topic** Linked List — Build, Print, Length & Search · **Prerequisite** Session 38a — Singly Linked List, Part 1 (why linked lists exist, node structure) · **Session type** Concept lecture

<!-- Split note: continues session-38 (original 60 min) right after the Classroom Quiz. This part covers the four practice-problem algorithms: constructing a list from an array, printing, counting length, and searching — the pointer-chasing skills the rest of the Linked List unit depends on. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Singly Linked List | https://docs.google.com/presentation/d/1MFFp2bxzh6l6-4LyxaEP2mdk3HiEy2fnB5rPU40ioRg/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Construct a singly linked list from an array by tracing and implementing the `arraytoLL` approach. *(APPLYING)*
2. Trace and implement the traverse-and-print, count-length, and search-for-value algorithms on a singly linked list. *(APPLYING)*
3. Determine the time and space complexity of each of the four operations covered this session. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 38a (0–5 min)

Say: *"Four quick ones on node structure before you build your first list."*

**Q1.** What two fields does a singly linked list node hold?
`A` data and prev · `B` data and next · `C` next and prev · `D` Just data
→ *Read:* B.

**Q2.** What does the last node's `next` point to in a singly linked list?
`A` The head · `B` Itself · `C` `null` · `D` The second-to-last node
→ *Read:* C.

**Q3.** Why don't linked-list nodes need contiguous memory?
`A` They don't actually avoid it · `B` Each node only needs the address of the next node · `C` They're stored on the stack · `D` They're compressed
→ *Read:* B.

**Q4.** In Part 1's Physical Pointer Recap, what was the only thing that changed when inserting before Volunteer 1?
→ *Read:* Open response — reconnects to "head changes, nothing else moves" before today's `arraytoLL` builds exactly that structure.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"You know what a node is. Now you build an entire list out of them, from a plain array — and then walk that list three different ways."*

---

## Slide Block B (7–16 min) — DELIVER SLIDES AS-IS

Covers: Practice Problem 1 — Construct a Linked List from an Array (`arraytoLL`): problem statement, approach, full dry run for `arr = [1, 3, 5, 7, 9]`, C++ and Python code, complexity analysis.

**Beats to emphasise**

- Name the three roles out loud every single time they appear in the dry run: **head** (fixed, never moves), **cur** (the pointer that's always at the "end so far," used to link the next node), **temp** (the brand-new node just created, about to be linked in).
- Walk the dry run's own sequence exactly as the slides show it: create node → link `cur->next = temp` → move `cur = temp` → repeat. This three-step rhythm is the pattern the class needs to internalise before Activity 2.
- On complexity: **O(n)** time because the loop runs once per array element; **O(n)** space because you allocate one new node per element — this is a rare case where an operation costs both O(n) time *and* O(n) space, worth calling out explicitly since most of today's later operations will be O(n) time but only O(1) space.

**Checkpoint (at 16 min)** — cold-call one student:
> *"In the `arraytoLL` dry run, what does the `cur` pointer do that the `head` pointer doesn't?"*
> **Answer:** `head` stays fixed at the first node forever, so you can always find your way back into the list. `cur` is the one that actually moves forward, getting re-linked to each new node as it's created — head never moves, cur always moves.

---

## ⚡ Activity 2 — Live Coding / Dry-Run Relay: Build the List (16–24 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can correctly track the head-vs-cur-vs-temp roles while pointer-chasing — the one skill the rest of the linked-list unit depends on.

**Setup line (say this):**
> *"I need 5 volunteers at the board, one per number in `arr = [2, 4, 6, 8, 10]`. Each of you IS a node — draw your own box with your data value inside. The rest of the class calls out what pointer to draw next, and where."*

**What students do:** Volunteer 1 draws `head` pointing at themselves (this is also `cur`). The class calls out the next step; volunteer 2 draws their box, the class decides whether `cur->next` should point to them, then `cur` moves. Repeat through node 5, ending with an arrow from the last node to `NULL`.

**How it surfaces:** If the class tries to move `cur` forward *before* wiring `cur->next` to the new node, stop and rewind: *"You just orphaned your new node — nothing points to it anymore. What has to happen first?"* The other common miss is forgetting the final `NULL` arrow — don't let the relay end without it.

**Debrief line:**
> *"Head never moved once, the whole relay — that's the one pointer callers need to find the list again. Everything else was `cur` doing the work and `temp` being temporary. If you can run this relay in your head, you can code `arraytoLL` from scratch."*

**Cut rule:** If running short, drop to 3 volunteers instead of 5 and skip the discussion of the final `NULL` arrow — keep the head-vs-cur-vs-temp distinction, that's the whole point.

---

## Slide Block C (24–28 min) — DELIVER SLIDES AS-IS

Covers: Practice Problems 2–4 — Print the Linked List (`printLL`), Count the Nodes (`lengthLL`), Search for a Value (`searchLL`) — approach, code, and complexity for each, plus the Key Takeaways recap slides.

**Beats to emphasise**

- All three share the same skeleton: start a temp pointer at `head`, loop `while (temp != nullptr)`, do one small thing per node, advance `temp = temp->next`. Say this explicitly — it's the same shape three times with a different "one small thing" in the middle (print / count++ / compare-to-target).
- `searchLL` is the one with a branch: it can `return true` and exit *early*, the moment it finds a match — the other two must always walk the full list.
- All three are **O(n) time**; all three are **O(1) space** — exactly one pointer (plus a counter for `lengthLL`) regardless of how long the list is. Contrast this with Slide Block B's `arraytoLL`, which was O(n) space.

**Checkpoint (at 28 min)** — show of hands:
> *"`printLL`, `lengthLL`, and `searchLL` are all O(n) time — but why is `lengthLL`'s O(n) unavoidable, while `searchLL`'s O(n) is only a worst case?"*
> **Answer:** `lengthLL` must visit every node no matter what, because you can't know the count until you hit `null`. `searchLL` can return early the instant it finds a match — it's only forced to walk the entire list when the value isn't there at all (or is the very last node).

---

## ⚡ Activity 3 — Spot the Bug (28–35 min)

**Format:** Spot the Bug · **Exposes:** that students copy the `while (temp != nullptr)` pattern without registering *why* the pointer-advance line inside the loop is what makes it eventually terminate.

**Setup line (say this):**
> *"This is `printLL` straight from the slides, except I removed exactly one line on purpose. Tell me what happens when you run it, and why — first correct explanation wins, not the first shout."*

```cpp
void printLL(Node* head){
    Node* temp = head;
    while (temp != nullptr){
        cout << temp->data << " ";
    }
}
```

**What students do:** 60 seconds silent, then hands up.

**How to handle wrong answers:** If they say "SyntaxError" — no, this compiles and runs fine, the bug only shows at runtime. If they say "it prints nothing" — no, it prints the first value... and keeps printing it. Push until someone says the words "infinite loop."

**Debrief line:**
> *"`temp` never moves, so the condition `temp != nullptr` never changes. This is the linked-list version of forgetting `i++` in a for-loop — except here it doesn't just skip an iteration, it hangs your program forever."*

**Cut rule:** If running long, skip the 60-second silent think, go straight to a show-of-hands vote on "infinite loop vs. crash vs. prints nothing," then debrief immediately.

---

## Exit Ticket (35–38 min)

**Exit ticket** — on paper before anyone leaves:

> Draw a 3-node singly linked list holding any three numbers of your choice, then write what `lengthLL(head)` would return for it.
> **Answer:** `3` — regardless of the values, the count is the number of nodes.

**Homework:** Re-attempt today's array-to-linked-list dry run from memory — build the list for `arr = [2, 4, 6, 8]` on paper, one node at a time, labelling `head`, `cur`, and `temp` at every step. <!-- placement: inferred -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `searchLL` returns the position/index of the value | Arrays train students to think "search = index" | Re-reading the code: it returns `true`/`false` (a boolean), not an index |
| Building the list from an array is "just linking," so it should be O(1) | The per-step work (one link) looks trivial in isolation | Counting the loop iterations in the dry run — n elements, n iterations, so O(n) |
| Forgetting the `temp = temp->next` advance causes "a small bug," not a crash-level problem | School debugging experience is mostly about wrong *values*, not infinite execution | Activity 3 — let the infinite loop actually run (or trace it far enough) so it stops being hypothetical |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz.**
- **Activity 2 is the load-bearing activity of this session.** If you must cut something else to protect its 8 minutes, do that — everything from Session 39 onward assumes students can pointer-chase confidently.
- **Have the head/cur/temp vocabulary on the board before Activity 2 starts** — writing it fresh mid-relay costs time you don't have.
- **Search example numbers in the deck (slides 51-52) are visually garbled in the source extraction** — the dry-run diagrams show inconsistent list values between the "found" and "not found" examples. Rebuild your own clean example on the board (e.g., list `1, 3, 5, 7, 9`, search for `5` → true, search for `4` → false) rather than trying to reproduce the slide's numbers exactly. <!-- flagged for review -->
