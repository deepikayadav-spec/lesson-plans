# Session 06a — Level Order Traversal (Part 1 of 2)

**Duration** 32 min · **Topic** Binary Tree — Traversals · **Prerequisite** Post-Order Traversal (Session 05) · **Session type** Concept lecture

<!-- Split note: original session-06 ran 50 min. Split at the Classroom Quiz boundary. Part 1 covers the BFS definition, the queue-as-mechanism idea, and the cinema-queue real-world callout. Part 2 (session-06b) covers the full dry run, pseudocode/complexity, and the two closing activities. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Level Order Traversal | https://docs.google.com/presentation/d/1gmTJbXzHlwaLUWTz0aqXqAMAFF37GbM8VSAT7EUXCSg/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define level order traversal as visiting nodes level by level, top to bottom, left to right within each level, and name it as Breadth-First Search (BFS). *(REMEMBERING)* <!-- placement: inferred phrasing, grounded in Slide 5 -->
2. Explain why a queue (First In First Out) is the data structure that produces this visiting order, in contrast to the call stack used by the recursive traversals taught in prior sessions. *(UNDERSTANDING)* <!-- placement: inferred; the deck states the FIFO/queue rationale directly (Slides 9-10, 45-51) but the explicit DFS-contrast framing is mine -->

*(Tracing the full algorithm, the pseudocode, and complexity analysis are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 05: Post-Order Traversal (0–6 min)

Say: *"Six questions on yesterday's post-order traversal. No names, no grades — I just need to know what's still there before we build on top of it."*

**Q1.** What is the visiting order in a post-order traversal?
`A` Root, Left, Right · `B` Left, Root, Right · `C` Left, Right, Root · `D` Right, Left, Root
→ *Read:* C. If this misses, stop — nothing else in the poll will make sense.

**Q2.** In the session 05 dry run (root 1; 1's children 2, 3; 2's children 4, 5; 3's children 6, 7; 4's left child 8; 6's right child 9), which node is visited *first*?
`A` Node 1 · `B` Node 2 · `C` Node 8 · `D` Node 9
→ *Read:* C. Post-order always bottoms out at the deepest-left leaf before it visits anything.

**Q3.** *(MSQ — pick all that apply)* In the pseudocode `postorder(root){ if(root==null) return; postorder(root->left); postorder(root->right); print(root->data) }`, which lines execute *before* a node's own value is printed?
`A` The null check · `B` The recursive call on the left child · `C` The recursive call on the right child · `D` Nothing — the value prints first
→ **Answer:** A, B, and C — the whole point of post-order is that both subtree calls finish before the print line runs.

**Q4.** What is the time complexity of post-order traversal?
`A` O(log n) · `B` O(n) · `C` O(n²) · `D` O(h)
→ *Read:* B — every node is visited exactly once.

**Q5.** What does the O(h) space complexity of post-order traversal actually measure, and what causes it?
`A` The size of an explicit queue · `B` The depth of the recursive call stack · `C` The number of leaf nodes · `D` The number of print statements
→ *Read:* B. Hold onto this answer — today's traversal will *not* use the call stack the same way.

**Q6.** For the session 05 dry-run tree (root 1; children 2, 3; 2's children 4, 5; 3's children 6, 7; 4's left child 8; 6's right child 9), what is the correct post-order output?
`A` 1 2 4 8 5 3 6 9 7 · `B` 8 4 5 2 9 6 7 3 1 · `C` 8 9 4 5 6 7 2 3 1 · `D` 1 3 7 9 6 2 5 8 4
→ **Answer:** B — direct recall of the session 05 worked dry run.

**Running it** — poll tool, ~40 s/question, project the distribution after each. Total 6 min including reads.

---

## Hook (6–9 min)

Draw (or project) the same tree from session 05's dry run: root 1; children 2 and 3; 2's children 4 and 5; 3's children 6 and 7.

Say: *"Post-order gave you 8 4 5 2 9 6 7 3 1 — root last, and you had to go all the way down to a leaf before printing anything. Today I want the same tree to give me 1 2 3 4 5 6 7 — top row first, then the next row, left to right. Same tree. Completely different order. What has to change?"*

Let a few guesses land. Then: *"Recursion alone won't do this — recursion naturally drills down one branch at a time. To go row by row, you need to remember every node you haven't visited yet, in the exact order you found them. That's not a stack. That's a queue."* <!-- placement: inferred hook, built directly from the contrast between session 05's tree/output and session 06's own Slide 7 example output -->

---

## Slide Block A (9–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 1-10: Welcome/title/agenda, BFS definition, problem statement, worked example output, approach (queue-based BFS) -->
Covers: Level order traversal definition (visit level by level, top to bottom, left to right) → Problem Statement → Example (tree 1 / 2,3 / 4,5,6,7 → output `1 2 3 4 5 6 7`) → Approach: use a queue to perform Breadth-First Search; when a node is processed, visit its value, then enqueue its left and right children.

**Beats to emphasise**

- **Name it BFS, out loud, more than once.** The deck itself labels this "Breadth First Search (Level Order)" on Slide 5 — say the two names together every time so students build the association: level order = BFS.
- **The queue is not optional bookkeeping — it *is* the algorithm.** The deck's own line: *"A queue ensures that nodes are processed in the exact order they appear at each level."* Land on this before moving to the dry run.
- **Per-node action is always the same three steps:** visit/collect its value, then enqueue its left child (if it exists), then enqueue its right child (if it exists). This three-step pattern repeats for every single node and is the thing students must be able to say without looking at the slide.

**Checkpoint (at 19 min)** — cold-call two students:
> *"In one sentence each: what does level order traversal visit, in what order, and what data structure makes that order happen?"*
> **Answer:** It visits every node level by level, top to bottom and left to right within a level, and a queue (FIFO) is what enforces that order.

---

## ⚡ Activity 1 — Real-World Callout: The Cinema Queue (19–24 min)

**Format:** Real-World Callout · **Exposes:** whether students actually understand *why* FIFO produces left-to-right, level-by-level order, or whether "queue" is just a vocabulary word they're repeating back.

**Setup line (say this):**
> *"You're in line at a cinema ticket counter. First person in line gets served first, gets their ticket, and leaves. Nobody cuts. Is that a stack or a queue — and what would break about level order traversal if it were the other one?"* <!-- placement: inferred setup line; the cinema/FIFO analogy itself is verbatim from the deck, Slides 45-47 -->

**What students do:** Call out "queue" and "FIFO." Push once more: *"If it were a stack instead — last person in line served first — what would our tree's output look like?"* Take 2-3 verbal guesses.

**How it surfaces:** If someone answers "stack" or hesitates, walk them back to the cinema line itself: point out that the *last* person to arrive getting served first would mean nodes discovered late (deeper, or further right) jump ahead of nodes discovered earlier — which destroys the level-by-level guarantee entirely.

**Debrief line:**
> *"Queue in, queue out, no cutting. That single rule — first in, first out — is the entire reason level order traversal visits top to bottom, left to right. Change the rule, and you change the traversal."*

**Cut rule:** If running late, skip the "what if it were a stack" push and just take the cinema-line answer (queue/FIFO) before moving on. Do not cut the debrief line.

---

## Classroom Quiz (24–29 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Peer Teach-Back (29–32 min)

**Why this strategy here:** Part 1's entire payload is one mechanism — "queue in, queue out, no cutting, that's why the order comes out level by level." Having a student *explain it to a partner, using the cinema analogy*, is a stronger check than a quiz question, because it forces them to reproduce the causal chain (FIFO → level order), not just recognise a label.

**Run it (3 minutes):**
> *"Turn to your partner. One of you explains, using the cinema line, why a queue produces level-by-level order — the other one has to stop you if you say 'queue' without saying WHY. Then swap: explain what would go wrong if we used a stack instead."*

Cold-call one student to repeat their partner's explanation, not their own — this checks whether the explanation actually transferred.

> *"Hold onto the cinema line. Part 2 turns this exact mechanism into a step-by-step algorithm — pop, record, push children — on this same tree."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Level order is just another flavour of the recursive traversals from previous sessions | Sessions 04-05 were all recursive, DFS-style, using the call stack | Naming it explicitly as Breadth-First Search from the first slide, and contrasting the queue mechanism against the call stack in the Hook |
| Left-to-right visiting order is automatic, inherent to "using a queue" | Students haven't had to think about *why* an order emerges, only that a queue is FIFO | Activity 1 and the Peer Teach-Back — forcing the causal chain (FIFO → order), not just the label |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split at the Classroom Quiz boundary.**
- **This is the class's first BFS/queue-based traversal after three recursive sessions.** Expect an instinctive reach for recursion; the Hook and Activity 1 are both built to interrupt that instinct early.
- Part 2 (session-06b) opens with a short retrieval poll on today's FIFO/queue mechanism before diving into the full node-by-node dry run — no need to re-teach the cinema analogy there, just reference it.
