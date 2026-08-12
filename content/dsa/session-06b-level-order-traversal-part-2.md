# Session 06b — Level Order Traversal (Part 2 of 2)

**Duration** 29 min · **Topic** Binary Tree — Traversals · **Prerequisite** Session 06a — Level Order Traversal, Part 1 (BFS definition, queue mechanism) · **Session type** Concept lecture

<!-- Split note: continues session-06 (original 50 min) from the Slide Block B boundary. Part 1 covered the BFS/queue concept; this part covers the full dry run, pseudocode, complexity, and the two closing activities. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Level Order Traversal | https://docs.google.com/presentation/d/1gmTJbXzHlwaLUWTz0aqXqAMAFF37GbM8VSAT7EUXCSg/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Trace the level-order algorithm on a given binary tree, correctly maintaining both the queue and the result list at each step. *(APPLYING)* <!-- placement: inferred phrasing, grounded in the dry run, Slides 11-20 -->
2. Implement level order traversal using the enqueue-root / dequeue-record-enqueue-children pattern, in pseudocode, C++, or Python. *(APPLYING)* <!-- placement: inferred phrasing, grounded in Slides 21-22, 26-28 -->
3. State and justify the time and space complexity of level order traversal — O(N) time, O(N) worst-case space (at most ~N/2 nodes at the widest level of a full tree). *(ANALYZING)* <!-- placement: inferred phrasing, grounded in Slides 23-25, 95-99 -->

---

## Warm-Up Poll — Retrieval Practice on Session 06a (0–5 min)

Say: *"Four quick ones on the queue mechanism before we turn it into an algorithm."*

**Q1.** Level order traversal is another name for:
`A` Depth-First Search · `B` Breadth-First Search · `C` Binary Search · `D` Post-order traversal
→ *Read:* B.

**Q2.** What data structure enforces level-order's visiting order?
`A` Stack · `B` Queue · `C` Array · `D` Recursive call stack
→ *Read:* B.

**Q3.** In the cinema-line analogy from Part 1, who gets served first?
`A` Whoever is at the back of the line · `B` Whoever is at the front of the line · `C` Whoever arrived most recently · `D` It's random
→ *Read:* B — FIFO, first in first out.

**Q4.** If level order traversal used a stack instead of a queue, what would happen to the output order?
`A` Nothing would change · `B` It would break the level-by-level, left-to-right guarantee · `C` It would run faster · `D` It would only visit leaf nodes
→ *Read:* B — this was Part 1's Activity 1 "what if it were a stack" push.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–6 min)

Say: *"You can explain the queue mechanism now. Today you drive it — pop, record, push children, repeat — on the exact same tree, until every node's been through the queue once."*

---

## Slide Block B (6–16 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 11-28: full dry run, pseudocode, complexity, C++/Python code -->
Covers: Dry run of the queue-based BFS on the tree (root 1; children 2, 3; 2's children 4, 5; 3's children 6, 7), tracking Queue and Result at every step → Pseudocode (`levelOrder(root)`: push root; while queue not empty, for each node at this level — pop the front, push its left/right children if they exist, append its data to `ans`) → Time Complexity O(N) → Space Complexity O(N), worst case ~N/2 nodes at the widest level of a full tree → C++ and Python code.

**Beats to emphasise**

- **Walk the dry run at the deck's own pace, node by node.** The Queue column and the Result column are two separate lists on screen at once — point at each explicitly on every step so students don't conflate "what's still in the queue" with "what's already been recorded."
- **The removal always happens before the enqueue.** Per the deck's own pseudocode order: pop the front → check/push its left child → check/push its right child → append its data to the result. Say the order out loud, in that order, every single time through the dry run.
- On **Space Complexity**, contrast explicitly with session 05's post-order O(h): today's worst case is O(N) — a full tree's last level alone can hold roughly N/2 nodes in the queue simultaneously. This is a deliberate, stated contrast in the deck (Slide 25).

**Checkpoint (at 16 min)** — show hands:
> *"For our tree (root 1, children 2/3, grandchildren 4/5/6/7), when node 2 is popped from the front of the queue, what exactly happens, in order?"*
> **Answer:** Node 2 is removed from the front, its value 2 is appended to the result, then its left child 4 and right child 5 are pushed onto the back of the queue.

---

## ⚡ Activity 2 — Live Dry-Run Relay (16–22 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can independently drive the queue-and-result mechanics end to end, without the instructor doing the bookkeeping for them.

**Setup line (say this):**
> *"Same tree as the slides: root 1, children 2 and 3, and 2/3's children are 4, 5, 6, 7. Queue starts with just [1]. I will not touch the queue or the result list unless one of you tells me exactly what to remove, what to add to the result, and what to push — in that order."*

**What students do:** Called on in turn, one student per step, each must state all three actions for that step:
- Pop 1 → result `[1]` → push 2, 3 (queue: `[2,3]`)
- Pop 2 → result `[1,2]` → push 4, 5 (queue: `[3,4,5]`)
- Pop 3 → result `[1,2,3]` → push 6, 7 (queue: `[4,5,6,7]`)
- Pop 4 → result `[...,4]` → no children (queue: `[5,6,7]`)
- Pop 5 → result `[...,5]` → no children (queue: `[6,7]`)
- Pop 6 → result `[...,6]` → no children (queue: `[7]`)
- Pop 7 → result `[...,7]` → no children (queue: `[]` → done)

**How it surfaces:** If a student jumps straight to "the children are 4 and 5" without first stating "pop 2, add 2 to result," stop them and make them restate all three actions in order — the point is the sequence, not just the final children.

**Debrief line:**
> *"Notice the result list came out 1 2 3 4 5 6 7 — in numeric order — purely because the queue processed things in the order they were discovered. Nobody sorted anything."*

**Cut rule:** If running short, run the relay live only through node 3 (levels 0-1), then state the remaining steps (4 through 7) yourself and just confirm the final result list together.

---

## ⚡ Activity 3 — Spot the Bug: Does Push Order Matter? (22–25 min)

**Format:** Spot the Bug · **Exposes:** the assumption that "left to right" is automatic, rather than a direct consequence of the order children are pushed onto the queue.

**Setup line (say this):**
> *"Same pseudocode as the slides, except I've swapped one pair of lines. Tell me only what changes in the *output* — not whether the code looks wrong."*

Show:
```
if (temp->right != null) { q.push(temp->right) }
if (temp->left  != null) { q.push(temp->left)  }
ans.push(temp->data)
```
(right pushed before left — swapped from the deck's own left-then-right order.)

**What students do:** Trace just the first level by hand: root 1 is popped, and now pushes 3 before 2, so the queue becomes `[3, 2]` instead of `[2, 3]`. Predict the full output from there.

**How it surfaces:** If students say the output is unaffected, make them finish the trace: with queue `[3,2]`, node 3 is processed next (not 2), so 3's children (6, 7) get enqueued before 2's children (4, 5) — final output becomes `1 3 2 6 7 4 5`, not `1 2 3 4 5 6 7`.

**Debrief line:**
> *"Left-to-right isn't a property of queues in general — it's a property of *this* code, because we push left before right. Swap the push order, and you silently get a mirror-image traversal that still runs without errors."*

**Cut rule:** If short on time, skip the full re-trace — just ask verbally, *"If I pushed right before left, would level 2 still read 4, 5, 6, 7?"* and take the one-word answer ("no").

---

## Exit Ticket (25–29 min)

> On paper or in chat: *"Here's a tree: root 10, left child 20, right child 30; 20's children are 40 and 50 (30 has no children). Write the queue's contents right after node 10 is popped, and write the final level-order output."*
> **Answer:** Queue after popping 10: `[20, 30]`. Final output: `10 20 30 40 50`. <!-- placement: inferred exit-ticket scenario, built from the same queue mechanics as the deck's worked example, using new node values so it isn't a copy of the in-class tree -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Once you see a node, you immediately enqueue its children — no removal step needed | Prior recursive traversals never required an explicit "remove from structure" step | Activity 2's dry-run relay, which forces pop-then-record-then-push in that exact order, every time |
| The Queue and the Result list are the same list | Both are lists of numbers shown side by side on the same slide throughout the dry run | Pointing at the two separate columns explicitly on every dry-run step in Slide Block B |
| Space complexity is O(h), like the recursive traversals just covered | Direct carryover from session 05's post-order O(h) space | Explicit contrast in Slide Block B: the queue's worst case is O(N), driven by the widest level, not the tree's height |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split at the Slide Block B boundary.**
- **Pacing risk:** the deck re-walks the *same* example tree three times — once as a guided dry run (Slides 11-20), once through the cinema/FIFO framing (Slides 45-64, covered conceptually in Part 1), and once again as a granular per-pseudocode-line trace (Slides 65-99). Treat the third pass as reinforcement, not new content — don't re-derive the mechanics from scratch or you will run out of session.
- **Two spots in the deck are worth a heads-up before you present them.** Slides 35 and 38 carry a leftover "Post-Order Traversal Example 1" title and an output of `[4, 8, 5, 2, 6, 7, 3, 1]` that does not match level order's left-to-right, top-to-bottom pattern for any tree consistent with the rest of the deck — this reads as an un-edited artifact from a copied template, not new content. This lesson plan does not build on those two slides; consider skipping past them quickly or flagging them as a content-fix candidate. <!-- placement: inferred — I could not reconcile this output with the rest of the deck's worked example -->
- The Classroom Quiz (Part 1) placeholder note applies here too — pull questions live from the platform's bank.
