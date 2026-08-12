# Session 47b — Intersection of Linked Lists (Part 2 of 2)

**Duration** 38 min · **Topic** Intersection of Two Singly Linked Lists — Length-Difference & Optimal Approach · **Prerequisite** Session 47a — Intersection of Linked Lists, Part 1 (problem contract, brute-force approach) · **Session type** Concept lecture

<!-- Split note: continues session-47 (original 60 min) right after the Classroom Quiz. This part covers the length-difference approach and the optimal two-pointer switching trick — the "one-line-of-genius" solution the session builds toward. This is also the last of the >45-minute Linked List sessions in this block. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Intersection of Linked Lists | https://docs.google.com/presentation/d/1ZUJxVBoauXcUtxsWNqsSvgrgJE-oeeb_sAFOGYW1J10/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Trace and implement the length-difference approach: compute both lengths, advance the longer list's pointer by the difference, then walk both pointers together. *(APPLYING)*
2. Trace and implement the optimal two-pointer approach: walk both pointers one step at a time, redirecting each to the other list's head when it hits `null`, until they meet. *(APPLYING)*
3. Compare the three approaches on time and space complexity and justify why the optimal approach is preferred. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 47a (0–5 min)

Say: *"Four quick ones on the brute-force approach before we drop the map entirely."*

**Q1.** The brute-force map's key is:
`A` The node's data value · `B` The node's pointer/address · `C` The node's index in the list · `D` A hash of the whole list
→ *Read:* B.

**Q2.** In the dry run, list 2's node with value `3` was:
`A` A match — the intersection · `B` Not a match — a different node that happens to share the value 3 · `C` Skipped entirely · `D` The cause of an error
→ *Read:* B.

**Q3.** What is the brute-force approach's space complexity, and why?
`A` O(1) · `B` O(M) — one map entry per node in list 1 · `C` O(M×N) · `D` O(log M)
→ *Read:* B.

**Q4.** In Part 1's sort, "the intersection point is defined by shared memory, not shared data" was sorted as:
→ *Read:* Open response — reconnects to node identity before two more approaches solve it without a map.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"The map worked, but it costs O(M) extra memory. Watch two ways to find the same node without storing a single one of them."*

---

## Slide Block B (7–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide range: Better Approach, dry run, pseudocode, complexity, code -->

Covers: Better Approach (length difference) → Dry Run → Pseudocode → Complexity Analysis → C++ Code.

**Beats to emphasise**

- Trade-off framing up front: *"No map this time. We pay for it with two full traversals instead of one."*
- The dry run computes `length(list1) = 5`, `length(list2) = 7`, `diff = |5 - 7| = 2`.
- The crux step: advance **the longer list's pointer** (`temp2`, list 2) forward by `diff = 2` nodes *before* starting the joint walk. Say explicitly why: it makes both pointers the same distance from their respective tails.
- After alignment, the comparison is `temp1 == temp2` — direct node-identity comparison, no map needed. This is the same "same node, not same value" idea from Part 1, now solved differently.
- Complexity payoff: **O(M + N) time, O(1) space** — better than brute force's O(M) space, same time complexity class.

**Checkpoint (at 19 min)** — cold-call:
> *"List 1 has length 5, List 2 has length 7. Which pointer do we advance first, and by how many nodes, before the synchronized walk starts?"*
> **Answer:** Advance list 2's pointer (the longer list) by `diff = 2` nodes. Then move both pointers one step at a time together.

---

## ⚡ Activity 2 — Dry-Run Relay: Align and Walk (19–24 min)

**Format:** Live Dry-Run Relay (whiteboard) · **Exposes:** advancing the wrong list's pointer, and losing count of the remaining `diff` steps.

**Setup line (say this):**
> *"Three of you, up to the board. Student one draws List 1 (`3→2→6→7→4`) and List 2 (`5→9→3→1→6→7→4`) exactly as shown, and counts each length out loud. Student two says which pointer moves, and how many steps, before anything else happens. Student three moves both pointers one node at a time, calling out each comparison, until they land on the same node."*

**What students do:** Student 1 counts (`length = 5`, `length = 7`); student 2 states `diff = 2` and advances list 2's pointer two nodes; student 3 walks both pointers together, calling matches until intersection at node 6.

**How to handle wrong answers:** If student 2 advances list 1's pointer (the shorter list) instead, stop the relay and ask the room: *"Which list has farther to go before it runs out? That's the one that needs the head start."*

**Debrief line:**
> *"Notice we never touched a map this whole time — just two counts and a head start. That's the entire trade: two extra passes to learn the lengths, in exchange for dropping the O(M) space cost."*

**Cut rule:** If short on time, state the lengths and `diff = 2` directly instead of having student 1 count live, and start the relay straight from the alignment step.

---

## Slide Block C (24–31 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide range: Optimal Approach, dry run, pseudocode, complexity, code, Key Takeaways -->

Covers: Optimal Approach (two-pointer switch) → Dry Run → Pseudocode → Complexity Analysis → C++ Code → Key Takeaways.

**Beats to emphasise**

- The approach in one sentence: two pointers start at the two heads, move one step at a time, and whenever a pointer runs off the end of its own list, it redirects to the **head of the other list** and keeps going.
- Walk the dry run's switch moment explicitly: `temp1` hits `null` at the end of list 1 while `temp2` is still mid-list-2 → `temp1` redirects to the head of list 2. Later `temp2` hits `null` and redirects to the head of list 1. They then land on the same node (6) together.
- The insight to say out loud: switching lists **equalizes the total distance each pointer travels** (each ends up walking `M + N` nodes total) — so by the time they've both switched once, they're guaranteed to be the same distance from the intersection, without ever computing a length.
- Complexity: **O(M + N) time, O(1) space** — same complexity class as Slide Block B, but in one pass with no separate length-computation step.
- Key Takeaways slide (deliver as-is): brute force → map; better → align by length; optimal → two pointers that switch lists. Final headline numbers: optimal is O(M + N) time, O(1) space.

**Checkpoint (at 31 min)** — cold-call:
> *"`temp1` just hit `null`, but `temp2` still has nodes left. What happens to `temp1` next?"*
> **Answer:** It's redirected to the head of List 2 (the *other* list) and keeps moving one step at a time — it does not stop, and it does not reset to its own head.

---

## ⚡ Activity 3 — Predict the Output: Does It Ever Stop? (31–35 min)

**Format:** Predict-the-Output · **Exposes:** the belief that the switching trick only works when the lists actually intersect, and uncertainty about what happens when they don't.

**Setup line (say this):**
> *"Same two-pointer, switch-on-null algorithm — but now imagine two completely separate linked lists that never intersect at all. Predict: does this loop ever end? If it does, what does it return?"*

**What students do:** Quick vote — "loops forever" vs. "ends and returns null" vs. "ends and returns garbage" — before you resolve it.

**How to handle wrong answers:** If "loops forever" wins the vote, trace it live: each pointer travels its own list, switches exactly once, then travels the other list. After `M + N` total steps each, both pointers hit `null` **at the same step** — `temp1 == temp2` becomes `null == null`, which is `true`, so the loop's exit condition fires and `null` is returned correctly.

**Debrief line:**
> *"The algorithm never needed to know in advance whether the lists intersect. The switch-and-meet trick handles 'yes' and 'no' with the exact same code — that's what makes it the optimal answer, not just a faster one."*

**Cut rule:** Skip the vote and state the answer directly, but keep the trace of *why* both pointers hit `null` on the same step — that's the point, not the trivia.

---

## Exit Ticket (35–38 min)

> In your own words: why does redirecting a pointer to the *other* list's head — instead of just stopping — make the optimal approach work without ever computing either list's length?
> **Answer:** Redirecting equalizes the total distance both pointers travel (each walks `M + N` nodes by the time it has switched once), so they arrive at the intersection point at the same step — no length calculation required.

Homework: re-attempt the dry run from memory. <!-- placement: inferred -->

This closes the >45-minute sessions of the Linked List block.

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Once a pointer's list ends, the algorithm is done | Every prior traversal pattern this course has taught stops at `null` | Slide Block C's checkpoint — showing `temp1` redirected to List 2's head instead of stopping |
| The switch-trick approach only works if the lists actually intersect | No worked example in the deck shows the non-intersecting case | Activity 3 — tracing that both pointers hit `null` simultaneously and the loop exits cleanly |
| The brute-force map approach is "good enough," since it works | It's the first correct solution students see, so it feels final | Key Takeaways slide's side-by-side complexity comparison: O(M) space vs. O(1) for both later approaches |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz.**
- **The non-intersecting edge case is not shown anywhere in the deck** — both worked examples (and all three approaches' dry runs) assume the lists do intersect, per the Problem Statement's "if there is one; otherwise return null." Activity 3 was built specifically to cover this gap; treat it as required, not optional, since it's the only place students see the `null`-return path. <!-- placement: inferred -->
- **Have all three approaches' complexities on the board simultaneously by the end** (brute force O(M) space, length-difference O(1) space, optimal O(1) space, all O(M+N) time except brute force's map lookups) — the Key Takeaways slide moves fast and students need the visual comparison to stick.
