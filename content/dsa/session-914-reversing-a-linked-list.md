# Session 14 — Reversing a Linked List

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Linked List — Reversing a Singly Linked List · **Prerequisite** Session 13 — Circular Linked List
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Reversing a Linked List | https://docs.google.com/presentation/d/1j5mSD-AHioG60i9N5UzCNAIHsU4oRws3JDWTMfcQnsA/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the problem: given the head of a singly linked list, reverse the list and return the new head. *(REMEMBERING)*
2. Explain why the brute-force (stack) approach needs O(n) extra space, tracing how it rewrites node *data*, not links. *(UNDERSTANDING)*
3. Trace the optimal three-pointer (`prev`, `cur`, `front`) in-place reversal by hand on a 5-node list. *(APPLYING)*
4. Predict the state of `prev`, `cur`, and `front` at any point mid-traversal, given a starting list. *(APPLYING)*
5. Compare the time/space complexity of the brute-force and optimal approaches and justify why in-place reversal is preferred. *(ANALYZING / EVALUATING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 13 (3–7 min) · ALS: Polling

5 questions on **Session 13 (Circular Linked List)**. ~45 s each, project the distribution, never name individuals.

**Q1.** In a circular singly linked list, what does the last node's `next` pointer point to?
`A` `nullptr` · `B` The head (first node) · `C` Itself · `D` The second-to-last node
→ **B.**

**Q2.** What's the time complexity of inserting a new node at the beginning of a circular singly linked list?
`A` O(1) · `B` O(n) · `C` O(k) · `D` O(log n)
→ **B.** *Read:* If many still say O(1), give it one sentence — today's session doesn't need it, but it's worth not letting this misconception harden.

**Q3.** Which loop condition does a circular list's traversal function actually use to stop?
`A` `while (temp != NULL)` · `B` `do { ... } while (temp != head)` · `C` `while (temp->next != NULL)` · `D` `for (int i = 0; i < n; i++)`
→ **B.**

**Q4.** Why would `while (temp != NULL)` be a bug on a circular linked list?
`A` It skips the first node · `B` It causes an infinite loop, since NULL never appears · `C` It stops one node too early · `D` It's not a bug — both work
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about circular linked lists?
`A` No NULL appears anywhere in a valid one · `B` Insert-at-beginning is O(n), not O(1) · `C` They require contiguous memory · `D` Round-robin scheduling is a real-world application
→ **A, B, D.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Line up 5 volunteers at the front, each one physically pointing at the next: 1 → 2 → 3 → 4 → 5, volunteer 5 pointing at nothing (NULL).

Ask: *"I want this line reversed — 5 pointing at 4, 4 at 3, and so on, ending with 1 pointing at nothing. Nobody moves position. Only pointing-arms change. What's the minimum number of arms that need to change direction?"*

Let them land on **five** — every single node's `next` has to flip, exactly once each.

> *"That's the whole session. Today you learn two ways to make five arms change direction: one that needs a helper holding all your old positions written down [gesture at a notepad — the stack], and one that needs nothing extra at all."*

---

## Slide Block A — Brute-Force Approach: Stack (10–19 min) — DELIVER SLIDES AS-IS

Covers: Problem statement (reverse `1→2→3→4→5→NULL` to `5→4→3→2→1→NULL`) → brute-force explanation → dry run pushing/popping a LIFO stack → pseudocode / C++ / Python code → complexity.

**Beats to emphasise**

- State the problem plainly first: given the head of a singly linked list, reverse it, return the new head.
- The brute force **never touches a single link**. It pushes every node's data onto a stack, then walks the list a *second* time, overwriting each node's `data` field with a pop from the stack. The nodes stay exactly where they are, in the same order — only the values inside them change. Everything else about this approach follows from that.
- Two full traversals (push loop + pop loop) → O(n) time. The stack holding all n values → O(n) extra space. Run the C++ or Python snippet live.

**Checkpoint (at 19 min)** — cold-call:
> *"After the brute-force reversal finishes, has a single `next` pointer in the list changed?"*
> **Answer:** No. The nodes are the same objects, in the same positions, in the same order — only each node's `data` field was overwritten from the stack.

---

## ⚡ ALS Activity 1 — Predict the Output: Stack Dry Run (19–24 min)

**ALS format:** Predict-the-Output — exposes whether students actually track which value comes back out of a LIFO stack, using the deck's own dry-run list (`1, 2, 3, 4, 5` pushed in that order).

**Setup line:**
> *"I'm pushing 1, 2, 3, 4, 5 onto a stack, in that order. Before I pop anything — on your fingers, show me: what's the very first value that comes back out?"*

Hold up fingers / call out an answer. Then pop one at a time on the board (5, then 4, 3, 2, 1), checking against the deck's own dry run.

**How to handle wrong answers:** If someone answers "1" (a FIFO/queue instinct), stop and physically demonstrate with 5 stacked books or hands: *"The last one down comes off first."* Re-ask before revealing the real order.

**Debrief line:**
> *"A stack always hands you back the last thing you gave it. That's the entire trick behind the brute-force reversal — push everything, then let the stack do the reversing for you, one pop at a time."*

**Cut rule:** Skip the books demo, go straight to a show-of-hands vote, then reveal. Keep the debrief line verbatim.

---

## Slide Block B — Optimal Approach: In-Place Reversal (24–33 min) — DELIVER SLIDES AS-IS

Covers: Optimal approach steps (three pointers: `cur`, `prev`, `front`) → dry run reversing `1→2→3→4→5` → pseudocode / C++ / Python code → complexity.

**Beats to emphasise**

- Three pointers, one job each: `prev` trails behind (starts at `nullptr`), `cur` is the node currently being flipped, `front` is a temporary bookmark so the rest of the list isn't lost the instant `cur->next` gets overwritten.
- The one line that does all the work is `cur->next = prev`. Say it, then show it flip on screen for node 1, node 2, node 3 — across the whole dry run.
- At the end of the loop, `cur` is `nullptr` and `prev` is sitting on the old last node (5) — that's why the function **returns `prev`**, not `head` and not `cur`.
- Zero extra data structures were allocated — this is the entire reason it's O(1) space against the brute force's O(n) stack. Say the contrast out loud; don't just point at the table.

**Checkpoint (at 33 min)** — show hands:
> *"At the moment the loop ends, `cur` is `nullptr`. What have we been returning as the new head, and why not `cur`?"*
> **Answer:** `prev` — it's sitting on the former last node, now the reversed list's first node. `cur` walked itself off the end and is `nullptr`.

---

## ⚡ ALS Activity 2 — Live Coding / Dry-Run Relay: Three-Pointer Reversal (33–40 min)

**ALS format:** Live Coding / Dry-Run Relay (groups of 3 at the board) — exposes whether students can hold three moving pointers in their heads through a full pass, using the deck's own list `1 → 2 → 3 → 4 → 5 → NULL`. Chosen as the closing activity because pointer-flipping only sticks once students have moved the arrows with their own hands.

**Setup line:**
> *"Groups of three. Draw 1 → 2 → 3 → 4 → 5 → NULL on your sheet. One of you IS `prev`, one is `cur`, one is `front` — point at your node. On my go, move through exactly one iteration together, out loud, then freeze so I can check."*

Iteration by iteration — (1) `front = cur->next`; (2) re-point the arrow: `cur->next = prev`; (3) `prev = cur`; (4) `cur = front`. Repeat until `cur` runs off the end. Spot-check 2–3 groups per iteration as you walk the room.

**How it surfaces:** Two errors show up reliably. Most common: groups move `prev` and `cur` forward *before* re-pointing `cur->next`, which loses the arrow they were supposed to flip — say *"re-point first, then move — in that order, every time."* Second: groups forget to save `front` before overwriting `cur->next`, "losing" the rest of the list — ask them what's downstream of node 3 if they skip that step.

**Debrief line:**
> *"Five nodes, five flips, one pointer move each time — and nothing you didn't already have. That's the whole reason this is O(1) space: three pointers, no matter how long the list is."*

**Cut rule:** Run it once as a whole-class relay with three volunteers at the board instead of small groups. Keep the debrief line verbatim.

---

## Classroom Quiz (40–45 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering both approaches' complexities and the three-pointer mechanics. -->

---

## Exit Ticket + Homework (45–48 min)

**Exit ticket** (~1 min) — on paper before anyone leaves:

> For the list `1 → 2 → 3 → NULL`, write the value of `prev`, `cur`, and `front` right after the **first** iteration of the optimal algorithm's loop body completes.
> **Answer:** `prev = 1` (now pointing to NULL as its `next`), `cur = 2`, `front = 3`.

**Homework:** Re-attempt today's dry run from memory, on the same `1→2→3→4→5` list.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Brute-force reversal rewires the pointers | "Reversal" sounds like it must flip links | Slide Block A's checkpoint — only `data` fields changed, confirmed by tracing it |
| The optimal algorithm returns `head` | Every function students have written so far returns the same variable it started with | Slide Block B's checkpoint — trace that `head` still points at the old first node; `prev` is the real new head |
| You can skip storing `front` and just write `cur = cur->next` after the flip | Looks equivalent, reads shorter | ALS Activity 2 — have a group try it and watch the rest of the list disappear |
| The stack-based approach is "more correct" because it explicitly touches every value | Two loops feels more thorough than one | Slide Block B's complexity contrast — O(n) space for nothing the in-place version doesn't already achieve in O(1) |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). This session's original 45-min version already had exactly 2 ALS activities and a single problem with two approaches — minimal restructuring needed beyond adding settling/buffer and moving the Classroom Quiz to the end.
- **Two ALS activities this session, both carried over directly:** Activity 1 is Predict the Output (the stack dry run), Activity 2 is the Live Coding / Dry-Run Relay (three-pointer reversal).
- **The Classroom Quiz now runs last, right before the Exit Ticket** — moved from its original mid-session position to match the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank.
- **This is a single-problem session** — the deck's own dry run (`1→2→3→4→5`) is deliberately the only example used throughout, including both activities. Do not introduce a second worked example.
- **This is session 14 of the Sem-3 sequence** (see `sem-3-sequence.md`).
- **ALS Activity 2 is the centrepiece** — protect its 7 minutes even if Slide Block B's checkpoint runs long. Pointer-flipping only sticks once students have moved the arrows with their own hands.
- **Keep the brute-force stack values (`1,2,3,4,5` pushed / `5,4,3,2,1` popped) visible on a side board through Slide Block B** — students will want to sanity-check the optimal result against it.
