# Session 15 — Cycle Detection In Linked List

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Linked List — Cycle Detection (Floyd's Tortoise and Hare) · **Prerequisite** Session 14 — Reversing a Linked List
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Cycle Detection | https://docs.google.com/presentation/d/1OWc0tSGS1Viiq3SMKUQ6Wy01O2hWn_-W-RMFtmCJ0d0/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the problem: given a singly linked list, determine whether it contains a cycle. *(REMEMBERING)*
2. Explain the brute-force approach — traverse the list, tracking every visited node's address in a set, and detect a cycle the moment a node repeats. *(UNDERSTANDING)*
3. Trace Floyd's Tortoise-and-Hare approach: `slow` moves one step, `fast` moves two steps, meeting if and only if a cycle exists. *(APPLYING)*
4. Explain *why* `slow` and `fast` are guaranteed to meet inside a cycle — the gap between them shrinks by exactly one node per iteration. *(ANALYZING)*
5. Contrast the brute force's O(n) time / O(n) space against Floyd's O(n) time / O(1) space. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 14 (3–7 min) · ALS: Polling

5 questions on **Session 14 (Reversing a Linked List)**. ~45 s each, project the distribution, never name individuals.

**Q1.** Reversing a singly linked list in place requires tracking how many pointers per node, at minimum?
`A` One · `B` Three (`prev`, `cur`, `front`) · `C` Zero — no extra pointers needed · `D` Four
→ **B.**

**Q2.** What's the time and space complexity of the optimal (three-pointer) reversal?
`A` O(n) time, O(n) space · `B` O(n) time, O(1) space · `C` O(1) time, O(n) space · `D` O(n²) time, O(1) space
→ **B.**

**Q3.** At the end of the optimal reversal's loop, which variable is returned as the new head?
`A` `head` · `B` `cur` · `C` `prev` · `D` `front`
→ **C.**

**Q4.** Why does the brute-force stack-based reversal need O(n) extra space?
`A` It doesn't — it's O(1) · `B` It pushes every node's data onto a stack before rewriting `data` fields · `C` It creates new nodes · `D` It sorts the list first
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about the three-pointer in-place reversal?
`A` The key line is `cur->next = prev` · `B` `front` must be saved before overwriting `cur->next` · `C` It allocates new nodes · `D` It's O(1) space
→ **A, B, D.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Ask: *"If I hand you the head of a linked list and just say 'traverse it and print every value until you hit null' — is there any way that could go wrong, even though the instruction sounds completely safe?"*

Let students think — most won't immediately see it.

> *"What if the list never actually reaches `null`, because some node further down points back to an earlier node, looping forever? Your traversal would run infinitely, and you'd have no way to know it, from the inside, without a way to detect that repetition. That's today's entire problem: before you trust *any* traversal, how do you know it will actually end?"*

---

## Slide Block A (10–20 min) — DELIVER SLIDES AS-IS

Covers: problem statement (detect whether a singly linked list contains a cycle) → Example 1 (list with a loop → `True`) → Example 2 (list ending in `null` → `False`) → brute force: traverse the list, tracking every visited node's address in a set → full dry run on an 8-node list → pseudocode → complexity → C++/Python code.

**Beats to emphasise**

- State the brute force in one line: *"walk the list, and remember every node's address you've seen — the moment you're asked to visit an address you've already recorded, you've found the loop."*
- **Say explicitly why this uses node *addresses*, not node *values*:** two different nodes can hold the same value, so comparing values could produce a false cycle detection. The set must track node identity, not what number sits inside it.
- Complexity: **O(n) time** (each real node visited exactly once before either a cycle is found or the list legitimately ends), **O(n) space** (the set can grow to hold every node visited).

**Checkpoint (at 20 min)** — cold-call:
> *"Why does the brute-force approach check node *addresses* in the set, rather than the *values* stored in each node?"*
> **Answer:** Different nodes can legitimately hold identical values without any cycle existing. Only comparing addresses correctly distinguishes "I've revisited this exact node" from "I've seen this same number before at a different node."

---

## Slide Block B (20–29 min) — DELIVER SLIDES AS-IS

Covers: optimal approach — Floyd's Cycle Detection Algorithm (Tortoise and Hare): initialize `slow` and `fast` both at `head`; move `slow` one step and `fast` two steps per iteration; if they ever point to the same node, a cycle exists; if `fast` (or `fast->next`) reaches `null`, no cycle exists → full dry run → pseudocode → complexity → C++/Python code.

**Beats to emphasise**

- **The mechanism in one sentence:** *"one pointer moves at normal speed, a second pointer moves twice as fast — if there's a loop, the fast pointer will eventually lap the slow one and land on the exact same node; if there's no loop, the fast pointer simply falls off the end first."*
- **Say explicitly why they're guaranteed to meet, not just likely to:** once both pointers are inside the cycle, the *gap* between them shrinks by exactly one every iteration, because `fast` gains one extra step on `slow` each time. A shrinking integer gap that starts positive must eventually hit zero — it can't skip over zero, since the maximum step-size difference per iteration is exactly one.
- Contrast directly against Slide Block A: **zero extra data structures** — no set, no map, just two pointer variables — which is exactly why space drops from O(n) to O(1).

**Checkpoint (at 29 min)** — cold-call:
> *"Why can't the fast pointer 'jump over' the slow pointer and miss it entirely, once both are inside the cycle?"*
> **Answer:** The gap between them shrinks by exactly one node per iteration. A gap that decreases by exactly one each step, starting from some positive integer, must pass through every smaller value on its way down — including zero — so it can never skip past the meeting point.

---

## ⚡ ALS Activity 1 — Live Coding / Dry-Run Relay: Slow and Fast, Step by Step (29–36 min)

**ALS format:** Live Coding / Dry-Run Relay — exposes whether students can track two independently-moving pointers themselves, rather than only having watched the deck's single worked example. Chosen right after Slide Block B because the "gap shrinks by one" argument only becomes concrete once students trace it on a list with a wraparound step.

**Setup line:**
> *"Six-node list: `A → B → C → D → E → F`, and `F` points back to `C`. Starting both `slow` and `fast` at `A`. After each iteration, tell me where each pointer is — before I confirm."*

Run **one iteration at a time**:

```
Start:        slow=A, fast=A
Iteration 1:  slow=B, fast=C
Iteration 2:  slow=C, fast=E
Iteration 3:  slow=D, fast=C   (fast wrapped: E → F → C)
Iteration 4:  slow=E, fast=E   → MEET — cycle detected
```

**How it surfaces:** At Iteration 3, ask before revealing: *"Fast was at `E` — where does it go after two more steps, given `F` loops back to `C`?"* Correct: `E → F`, then `F → C` (following the loop-back), landing at `C` — not falling off the list, since `F`'s `next` is `C`, not `null`.

**Debrief line:**
> *"They meet at `E` on iteration 4 — inside the cycle, exactly as guaranteed. Notice fast doesn't need to 'know' where the cycle is; it just keeps moving twice as fast as slow, and the meeting happens naturally once both are looping."*

**Cut rule:** Do only iterations 1–2, then state the final meeting point directly — the mechanism is demonstrated either way.

---

## ⚡ ALS Activity 2 — Predict and Discuss: What If There's No Cycle? (36–41 min)

**ALS format:** Predict-the-Output / Discussion — exposes whether students understand the algorithm's *other* branch, correctly recognising termination, not just the cycle-found case. Chosen as the closing activity because the loop's exit condition is the most common place students introduce a crash when implementing this from scratch.

**Setup line:**
> *"Five-node list, no cycle: `A → B → C → D → E → null`. Trace `slow` and `fast` together. What happens, and how does the algorithm know to return `false`?"*

Discuss for a minute, then trace together: `slow=A,fast=A` → `slow=B,fast=C` → `slow=C,fast=E` → next step, `fast` needs to move from `E`, but `E->next` is `null` — the loop condition `fast != null && fast->next != null` fails, so the loop exits and the algorithm returns `false`.

**How it surfaces:** Ask a follow-up: *"Why does the loop check both `fast != null` AND `fast->next != null`, instead of just one of them?"* Push toward: `fast` moves two steps per iteration, so before advancing it, the algorithm must confirm *both* the current node and the very next node exist — otherwise `fast->next->next` could dereference a `null` pointer and crash.

**Debrief line:**
> *"A two-pointer trick that moves at different speeds has to be equally careful about *both* ways it can end — meeting (cycle found) and running off the end (no cycle) — and the loop condition has to protect against crashing while checking for the second case."*

**Cut rule:** State the termination condition and its reasoning directly, skipping the open trace.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering both approaches' complexities and the meeting-guarantee argument. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — on paper before anyone leaves:

> Four-node list: `W → X → Y → Z`, and `Z` points back to `X`. Trace `slow` and `fast` from `W` and state which node they meet at.
> **Answer:** `slow=W,fast=W` → iter 1: `slow=X, fast=Y` → iter 2: `slow=Y, fast=X` (fast moves `Y→Z`, then `Z→X` via the loop-back) → iter 3: `slow=Z, fast=Z` (slow moves `Y→Z`; fast moves `X→Y→Z`) → **meet at `Z`.**

**Homework:** Trace Floyd's algorithm on a 7-node list `P→Q→R→S→T→U→V` where `V` points back to `R`, reporting the meeting node.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The brute-force set should track node *values*, not addresses | Values are what students usually compare when checking "have I seen this before" | Slide Block A's checkpoint — two distinct nodes can share a value with no cycle present; only address identity is safe |
| The fast pointer might "jump over" the slow pointer and miss meeting it | Feels intuitively possible since fast moves twice as far each step | Slide Block B — the gap-shrinks-by-exactly-one argument, showing the gap can't skip past zero |
| Floyd's algorithm needs to know where the cycle starts before it can detect one | The two-pointer trick feels like it should require some upfront cycle information | State plainly: the algorithm needs no advance knowledge of the cycle at all — it discovers the meeting purely from the relative speed difference |
| The loop condition only needs to check `fast != null` | `slow` never risks going out of bounds, so it's natural to assume the same laxity applies to `fast` | ALS Activity 2 — showing `fast->next` must also be checked, since `fast` looks two nodes ahead each iteration |
| This problem is solved the same way as searching for a duplicate value in an array | Both involve "have I seen this before" | Contrast explicitly: the two-pointer speed-difference mechanism is unique to sequential, directional linked-list traversal |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). This session's original 45-min version already had exactly 2 ALS activities — minimal restructuring needed beyond adding settling/buffer and moving the Classroom Quiz to the end (originally sat between Slide Block B and the activities).
- **Two ALS activities this session, both carried over directly:** Activity 1 is the Live Coding / Dry-Run Relay (tracking slow/fast step by step, including the wraparound), Activity 2 is Predict and Discuss (the no-cycle termination branch).
- **The Classroom Quiz now runs last, right before the Exit Ticket** — matching the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank.
- **This is session 15 of the Sem-3 sequence** (see `sem-3-sequence.md`).
- **The gap-shrinks-by-one argument in Slide Block B is the session's real payoff — protect it even under time pressure.** Students who can explain *why* the pointers must meet (not just that they do) have understood Floyd's algorithm; students who only memorise "slow moves 1, fast moves 2" have not.
- **Watch for the `fast->next != null` omission specifically** — it's the most common subtle bug students will write when asked to implement this from scratch, and ALS Activity 2 exists to pre-empt it.
- **Bridge to Session 16 explicitly at the close:** "Today answered yes-or-no: does a cycle exist? Next session asks a harder follow-up — if it does, exactly how long is the loop? Same two pointers, one more phase added on."
