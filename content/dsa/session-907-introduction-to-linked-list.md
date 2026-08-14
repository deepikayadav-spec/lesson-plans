# Session 7 — Introduction to Linked List

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Linked List — Structure, Construction, Core Traversal Operations · **Prerequisite** Session 6 — Two Sum Problem (genuinely new territory from here — not a variation on the Hashing/Prefix Sum/Sliding Window block)
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Singly Linked List | https://docs.google.com/presentation/d/1MFFp2bxzh6l6-4LyxaEP2mdk3HiEy2fnB5rPU40ioRg/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the two drawbacks of arrays — fixed size and the contiguous-memory requirement — that motivate linked lists. *(REMEMBERING)*
2. Explain what a node is and how `data` + `next` together form a singly linked list. *(UNDERSTANDING)*
3. Differentiate singly, doubly, and circular linked lists by how their `next`/`prev` pointers are wired. *(ANALYZING)*
4. Construct a singly linked list from an array by tracing and implementing the `arraytoLL` approach. *(APPLYING)*
5. Trace and implement the traverse-and-print, count-length, and search-for-value algorithms on a singly linked list. *(APPLYING)*
6. Determine the time and space complexity of each of the four operations covered this session. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 6 (3–7 min) · ALS: Polling

5 questions on **Session 6 (Two Sum)**. ~45 s each, project the distribution, never name individuals.

**Q1.** In the one-pass Two Sum solution, what does the hash map store?
`A` index → value · `B` value → index · `C` value → value · `D` A sorted copy of the array
→ **B.**

**Q2.** Why must the complement check happen *before* storing the current number?
`A` It doesn't matter · `B` It prevents an index from matching against itself · `C` It's required by Python syntax · `D` It makes the code shorter
→ **B.**

**Q3.** What's the time complexity of the one-pass Two Sum solution?
`A` O(n²) · `B` O(n log n) · `C` O(n) · `D` O(1)
→ **C.**

**Q4.** On `nums = [5, 5, 5]`, `target = 10` — which index pair does the one-pass solution return?
`A` `[1, 2]` · `B` `[0, 1]` · `C` `[0, 2]` · `D` It errors on duplicates
→ **B.**

**Q5.** *(MSQ — select all that apply)* Which of these techniques from the last six sessions used a hash map or hash set?
`A` Hashing (Session 1) · `B` Longest Subarray with Sum K (Session 4) · `C` Largest Subarray Sum / Kadane's (Session 5) · `D` Two Sum (Session 6)
→ **A, B, D.** *(Kadane's uses no extra data structure at all — O(1) space, a deliberate contrast worth noting.)*

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–9 min)

Draw a 5-slot array on the board, boxes touching edge to edge, labelled `arr[0]` through `arr[4]`, with memory addresses underneath (`1024, 1028, 1032...`).

Ask: *"I want to add a 6th element. Show of hands — does it just slide in next door?"*

Erase the "next door" space to show it's already someone else's memory.

> *"This is the array's whole problem: fixed size, and it needs one unbroken block of memory. Everything for the last six sessions — hashing, prefix sums, windows — ran *on top of* arrays without ever questioning that. Today we question it. This new structure fixes both problems, by giving up the one thing arrays had for free: neighbours who are actually next to each other."*

---

## Slide Block A (9–17 min) — DELIVER SLIDES AS-IS

Covers: Drawbacks of Arrays (fixed size, contiguous memory) → Introduction to Linked List → Node structure (data + pointer) → Non-Contiguous Memory Allocation → Types of Linked List (singly, doubly, circular) → Head & Tail → Practical Example (Music Playlist) → Node class in C++ and Python.

**Beats to emphasise**

- **Fixed size vs. dynamic size** is the entire motivation — don't rush past the two array-drawback slides, they're the "why" for everything that follows.
- **Non-contiguous memory** (slide 11): nodes can live anywhere in memory; only the pointers wire them together. Point at the diagram's scattered addresses — this is the direct fix for the array's second drawback from the Hook.
- On **Types of Linked List**: the one differentiator that matters is what the `next` (and `prev`, for doubly) pointers do at the two ends. Singly = last node's `next` is null. Doubly = both ends null, two-way pointers. Circular = last node points back to the first, no null anywhere. One sentence each — doubly and circular get their own full sessions later.
- **Head and Tail** are structural terms, not data terms — head is "the node you start from," tail is "the node with nothing after it."
- Show both the **C++ Node class** and the **Python Node class** side by side — Python's `self.next = address` is the same idea with less ceremony.

**Quick tie-in beat (~1 min, folded in here):** *"Last playlist you added a song to — did you ever tell the app in advance how many songs you'd add?"* Take 2 shout-outs. *"That's exactly this: the playlist's head is the first song, the tail is the last, and adding a song is just wiring one more node. No resizing, no shifting."*

**Checkpoint (at 17 min)** — cold-call one student:
> *"Give me one sentence on why a linked list doesn't need contiguous memory the way an array does."*
> **Answer:** Because each node only needs to know the *address* of the next node — the nodes themselves can live anywhere in memory, wired together by pointers instead of by sitting side by side.

---

## ⚡ ALS Activity 1 — Live Coding / Dry-Run Relay: Build the List (17–24 min)

**ALS format:** Live Coding / Dry-Run Relay — five volunteers physically become nodes at the board. Chosen as the session's one protected activity because tracking the head-vs-cur-vs-temp roles while pointer-chasing is the one skill the rest of the linked-list unit depends on. **If anything gets cut this session, protect this slot first.**

**Setup line:**
> *"I need 5 volunteers at the board, one per number in `arr = [2, 4, 6, 8, 10]`. Each of you IS a node — draw your own box with your data value inside. The rest of the class calls out what pointer to draw next, and where."*

Volunteer 1 draws `head` pointing at themselves (also `cur`). The class calls out the next step; volunteer 2 draws their box, the class decides whether `cur->next` should point to them, then `cur` moves. Repeat through node 5, ending with an arrow from the last node to `NULL`.

**How it surfaces:** If the class tries to move `cur` forward *before* wiring `cur->next` to the new node, stop and rewind: *"You just orphaned your new node — nothing points to it anymore. What has to happen first?"* The other common miss is forgetting the final `NULL` arrow — don't let the relay end without it.

**Debrief line:**
> *"Head never moved once, the whole relay — that's the one pointer callers need to find the list again. Everything else was `cur` doing the work and `temp` being temporary. If you can run this relay in your head, you can code `arraytoLL` from scratch."*

**Cut rule:** Drop to 3 volunteers instead of 5 and skip the discussion of the final `NULL` arrow — keep the head-vs-cur-vs-temp distinction, that's the whole point. This is the last thing to cut in the whole session, not the first.

---

## Slide Block B (24–30 min) — DELIVER SLIDES AS-IS

Covers: Practice Problem 1 — Construct a Linked List from an Array (`arraytoLL`): problem statement, approach, full dry run for `arr = [1, 3, 5, 7, 9]`, C++ and Python code, complexity analysis.

**Beats to emphasise**

- Name the three roles every time they appear in the dry run: **head** (fixed, never moves), **cur** (the pointer always at the "end so far"), **temp** (the brand-new node just created, about to be linked in).
- Walk the dry run's own sequence: create node → link `cur->next = temp` → move `cur = temp` → repeat. Same three-step rhythm the relay just built by hand.
- On complexity: **O(n)** time, **O(n)** space — one new node allocated per array element. Flag this explicitly as a rare case where an operation costs both O(n) time *and* O(n) space; most of today's remaining operations will be O(n) time but only O(1) space.

**Checkpoint (at 30 min)** — cold-call one student:
> *"In the `arraytoLL` dry run, what does the `cur` pointer do that the `head` pointer doesn't?"*
> **Answer:** `head` stays fixed at the first node forever, so you can always find your way back into the list. `cur` is the one that actually moves forward, getting re-linked to each new node as it's created.

---

## Slide Block C (30–35 min) — DELIVER SLIDES AS-IS

Covers: Practice Problems 2–4 — Print the Linked List (`printLL`), Count the Nodes (`lengthLL`), Search for a Value (`searchLL`) — approach, code, and complexity for each.

**Beats to emphasise**

- All three share the same skeleton: start a temp pointer at `head`, loop `while (temp != nullptr)`, do one small thing per node, advance `temp = temp->next`. Same shape three times with a different "one small thing" in the middle (print / count++ / compare-to-target).
- `searchLL` is the one with a branch: it can `return true` and exit *early*, the moment it finds a match — the other two must always walk the full list.
- All three are **O(n) time**; all three are **O(1) space** — exactly one pointer (plus a counter for `lengthLL`) regardless of list length. Contrast this with Slide Block B's `arraytoLL`, which was O(n) space.

**Checkpoint (at 35 min)** — show hands:
> *"`printLL`, `lengthLL`, and `searchLL` are all O(n) time — but why is `lengthLL`'s O(n) unavoidable, while `searchLL`'s O(n) is only a worst case?"*
> **Answer:** `lengthLL` must visit every node no matter what, because you can't know the count until you hit `null`. `searchLL` can return early the instant it finds a match — it's only forced to walk the entire list when the value isn't there at all.

---

## ⚡ ALS Activity 2 — Spot the Bug (35–41 min)

**ALS format:** Spot the Bug — exposes that students copy the `while (temp != nullptr)` pattern without registering *why* the pointer-advance line inside the loop is what makes it eventually terminate.

**Setup line:**
> *"This is `printLL` straight from the slides, except I removed exactly one line on purpose. Tell me what happens when you run it, and why — first correct explanation wins, not the first shout."*

```cpp
void printLL(Node* head){
    Node* temp = head;
    while (temp != nullptr){
        cout << temp->data << " ";
    }
}
```

60 seconds silent, then hands up.

**How to handle wrong answers:** If they say "SyntaxError" — no, this compiles and runs fine, the bug only shows at runtime. If they say "it prints nothing" — no, it prints the first value... and keeps printing it. Push until someone says the words "infinite loop."

**Debrief line:**
> *"`temp` never moves, so the condition `temp != nullptr` never changes. This is the linked-list version of forgetting `i++` in a for-loop — except here it doesn't just skip an iteration, it hangs your program forever."*

**Cut rule:** Skip the 60-second silent think, go straight to a show-of-hands vote on "infinite loop vs. crash vs. prints nothing," then debrief immediately.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering drawbacks-of-arrays, node structure, and the four practice-problem complexities. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — on paper before anyone leaves:

> Draw a 3-node singly linked list holding any three numbers of your choice, then write what `lengthLL(head)` would return for it.
> **Answer:** `3` — regardless of the values, the count is the number of nodes.

**Homework:** Re-attempt today's array-to-linked-list dry run from memory — build the list for `arr = [2, 4, 6, 8]` on paper, one node at a time, labelling `head`, `cur`, and `temp` at every step.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A linked list's nodes sit next to each other in memory, like an array | The diagrams draw nodes left-to-right in a row | Slide 11's scattered-address diagram, reinforced in the Hook by erasing the array's "next door" slot |
| Traversal in a singly linked list can go backward if needed | Students haven't yet seen a doubly linked list to contrast against | Pointing out there is no `prev` field in the C++/Python Node class shown this session — only `next` exists |
| `searchLL` returns the position/index of the value | Arrays train students to think "search = index" | Re-reading the code: it returns `true`/`false` (a boolean), not an index |
| Building the list from an array is "just linking," so it should be O(1) | The per-step work (one link) looks trivial in isolation | Counting the loop iterations in the dry run — n elements, n iterations, so O(n) |
| Forgetting the `temp = temp->next` advance causes "a small bug," not a crash-level problem | School debugging experience is mostly about wrong *values*, not infinite execution | ALS Activity 2 — let the infinite loop actually run (or trace it far enough) so it stops being hypothetical |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Converted from the original 60-min version — see below for what changed.
- **Two ALS activities this session:** Activity 1 is the Live Coding / Dry-Run Relay (protected — the load-bearing activity of the whole session), Activity 2 is Spot the Bug (the infinite-loop debugging skill). The original third activity (Real-World Callout, the music-playlist tie-in) is folded into a 1-minute quick beat inside Slide Block A instead of running as its own block — its content survives, just compressed.
- **The Classroom Quiz now runs last, right before the Exit Ticket** — moved from its original mid-session position (after Activity 1) to match the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank covering drawbacks-of-arrays, node structure, and the four practice-problem complexities before class starts.
- **Warm-Up Poll was fully rewritten.** The original polled Session 37 (Bitwise XOR), which is no longer this session's prerequisite — Bit Manipulation was moved out of the Sem-3 sequence entirely (see `sem-3-sequence.md`). This session now follows Session 6 (Two Sum), and the poll reflects that.
- **Activity 1 (the relay) is the load-bearing activity of this session.** If you must cut something else to protect its 7 minutes, do that — everything from the next several sessions assumes students can pointer-chase confidently.
- **Have the head/cur/temp vocabulary on the board before Activity 1 starts** — writing it fresh mid-relay costs time you don't have.
- **Search example numbers in the deck (slides 51-52) are visually garbled in the source extraction** — the dry-run diagrams show inconsistent list values between the "found" and "not found" examples. Rebuild your own clean example on the board (e.g., list `1, 3, 5, 7, 9`, search for `5` → true, search for `4` → false) rather than trying to reproduce the slide's numbers exactly.
- **This is session 7 of the Sem-3 sequence** (see `sem-3-sequence.md`) — the first of the Linked List block, following the six-session Hashing/Prefix Sum/Sliding Window/Subarray block.
