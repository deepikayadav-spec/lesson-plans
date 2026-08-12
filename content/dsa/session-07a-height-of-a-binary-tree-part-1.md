# Session 07a — Height of a Binary Tree (Part 1 of 2)

**Duration** 34 min · **Topic** Binary Tree — Properties · **Prerequisite** Level Order Traversal (Session 06) · **Session type** Concept lecture

<!-- Split note: original session-07 ran 50 min. Split at the Classroom Quiz boundary. Part 1 covers the height definition, the recursive formula, and the bottom-up dry-run relay. Part 2 (session-07b) covers pseudocode/complexity, the nodes-vs-edges convention, and the closing activities. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Height of a Binary Tree | https://docs.google.com/presentation/d/1hyM0duOwFw78I_a7majxxe6ZGF_9icnJtlwgQNvfujs/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define the height of a binary tree as the number of nodes along the longest path from the root to a leaf, and state the two base cases: an empty tree has height 0, a single-node tree has height 1. *(REMEMBERING)* <!-- placement: inferred phrasing, grounded in Slides 4, 8 -->
2. Explain why height is computed recursively as `1 + max(leftHeight, rightHeight)`, and why the recursion bottoms out at a null node returning 0. *(UNDERSTANDING)* <!-- placement: inferred phrasing, grounded in Slides 9, 37 -->
3. Trace the recursive height computation bottom-up on a given binary tree, computing each node's height only once both of its children's heights are known. *(APPLYING)* <!-- placement: inferred phrasing, grounded in the dry run, Slides 10-28 -->

*(The nodes-vs-edges convention, pseudocode, and complexity are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 06: Level Order Traversal (0–6 min)

Say: *"Eight quick ones on yesterday's level order traversal. No names, no grades — just tell me what's still there."*

**Q1.** What data structure does level order traversal use to process nodes in order?
`A` Stack · `B` Queue · `C` Array · `D` Linked list
→ *Read:* B. If this misses, the whole session was about the wrong data structure — worth a 20-second re-anchor before Q2.

**Q2.** Level order traversal visits nodes:
`A` Root, then left subtree, then right subtree, recursively · `B` All nodes at one depth before moving to the next depth, left to right · `C` Left, then right, then root · `D` Alternating left and right, one node at a time

**Q3.** For the tree used in session 06's dry run (root 1; children 2, 3; 2's children 4, 5; 3's children 6, 7), what is the level-order output?
`A` 1 2 4 5 3 6 7 · `B` 1 2 3 4 5 6 7 · `C` 4 5 6 7 2 3 1 · `D` 1 3 2 7 6 5 4
→ *Read:* B — direct recall of yesterday's worked dry run.

**Q4.** *(MSQ — pick all that apply)* Which of these are true of the queue as used in level order traversal?
`A` First In, First Out · `B` Last In, First Out · `C` Nodes are removed from the front and children are added at the back · `D` It's the same structure the call stack uses in recursive traversals
→ **Answer:** A and C.

**Q5.** What is the time complexity of level order traversal?
`A` O(log N) · `B` O(N) · `C` O(N²) · `D` O(H)

**Q6.** What is the worst-case space complexity of the queue in level order traversal, and when does it occur?
`A` O(1), always · `B` O(N), only when the tree is skewed · `C` O(N), at the widest level of a full/complete tree · `D` O(H), always
→ *Read:* C. This is the one students most often mix up with recursive traversals' O(H) — worth re-stating before moving on.

**Q7.** In the deck's cinema-ticket-line analogy for how a queue behaves, who gets served first?
`A` Whoever is at the back of the line · `B` Whoever is at the front of the line · `C` Whoever shouts loudest · `D` It's random
→ *Read:* B. Hold onto this — today has no queue and no line at all. We're back to pure recursion.

**Q8.** Level order traversal is an example of which traversal strategy?
`A` Depth-First Search · `B` Breadth-First Search · `C` Binary Search · `D` In-order traversal
→ *Read:* B. Today's topic sits back on the Depth-First side of that split — recursion, call stack, no queue.

**Running it** — poll tool, ~40 s/question, project the distribution after each. Total 6 min including reads.

---

## Hook (6–9 min)

Say: *"Yesterday we needed an explicit queue sitting outside the tree to get the order right. Today, no queue at all — we're back to plain recursion, and the question is almost embarrassingly simple: how tall is this tree?"*

Draw a tree with at least three different root-to-leaf paths of different lengths (mirror the deck's own opening image, Slides 4-6, which labels three candidate paths A, B, and C on the same tree). Ask: *"Three different paths from root to a leaf, three different lengths. Which one is 'the height' of this tree — the shortest, the longest, or do we average them?"*

Let guesses land, then confirm: *"The longest one. Height is always about the worst case — the deepest a search could possibly have to go."* <!-- placement: inferred hook, built directly from the deck's own three-paths framing on Slides 4-6 -->

---

## Slide Block A (9–20 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 1-9: Welcome/title/agenda, height definition (two equivalent framings), problem statement with base cases, recursive approach -->
Covers: Height defined two equivalent ways — "number of levels in the tree" and "number of nodes along the longest root-to-leaf path" → Problem Statement, with the explicit base-case notes: height of an empty tree is 0, height of a single-node tree is 1 → Approach: if the tree is empty, height is 0; recursively find the left subtree's height and the right subtree's height; the current node's height is `1 + max(leftHeight, rightHeight)`.

**Beats to emphasise**

- **The two definitions are the same number, seen two ways.** "Number of levels" and "number of nodes in the longest root-to-leaf path" always agree — say this explicitly, because the deck presents them as two separate framings without stating outright that they're equivalent. <!-- placement: inferred connective statement; the deck shows both framings (Slides 4-5, and again as "Method 1"/"Method 2" later) but does not explicitly say they always produce the same number -->
- **Read the two base cases as a pair, not separately:** empty tree → 0, single node → 1. Students will try to reason about one without the other; make them recite both together.
- **The formula has exactly three moving parts:** left subtree's height, right subtree's height, and `1 +`. Nothing else. Say it as one sentence: *"Ask both children how tall they are, take the taller answer, add one for yourself."*

**Checkpoint (at 20 min)** — cold-call two students:
> *"State the recursive formula for a node's height in one sentence, and tell me what a `null` node returns."*
> **Answer:** A node's height is 1 plus the larger of its left and right subtree heights; a `null` node returns 0.

---

## ⚡ Activity 1 — Live Dry-Run Relay: Bottom-Up Height (20–26 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** the assumption that recursion evaluates top-down (root's answer known first); in reality the deepest calls return first, and every parent is stuck waiting on both children.

**Setup line (say this):**
> *"Here's the tree from the dry run: root 1; 1's left child is 2, right child is 3; 2 has no left child but its right child is 4; 3's left child is 5 and right child is 6; 5's left child is 7 and has no right child. I am not going to write a single height value on the board unless one of you gives it to me — and I will only accept a node's height once you've already told me both of its children's heights."*

**What students do:** Called on in the order the recursion actually resolves (matching the deck's own dry run, Slides 10-28):
- Node 4 (leaf): height 1
- Node 2: `1 + max(0, 1) = 2` (left height 0 — no left child)
- Node 7 (leaf): height 1
- Node 5: `1 + max(1, 0) = 2` (right height 0 — no right child)
- Node 6 (leaf): height 1
- Node 3: `1 + max(2, 1) = 3`
- Node 1 (root): `1 + max(2, 3) = 4`

**How it surfaces:** If a student tries to answer for node 2 (or node 1) before its children's heights are on the board, stop and ask: *"Which subtree don't we know yet?"* Refuse to write anything until they name it and go compute that one first.

**Debrief line:**
> *"Every recursive call sits there, stuck, waiting for its children to answer before it can answer itself. That's not a queue this time — that's the call stack, and it always resolves bottom-up, leaves first, root last."*

**Cut rule:** If running short, state the left half (nodes 2 and 4) yourself and only run the relay on the right half (5, 7, 6, then 3), then combine at node 1 together as a class.

---

## Classroom Quiz (26–31 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: One-Sentence-Summary Chain (31–34 min)

**Why this strategy here:** the entire height formula fits in one sentence, and Activity 1 just proved students can execute it — but execution under guidance isn't the same as being able to state the rule cold. A chained summary forces each student to reproduce a fragment of the formula in front of peers, with nowhere to hide.

**Run it (3 minutes):**
> *"We're building one sentence for the height formula, one clause at a time, around the room. First person: start it. Next person: continue it. If you repeat what's already been said instead of adding the next real clause, I'll stop the chain and we restart from you."*

Target sentence shape: *"A node's height is one, plus the larger of, its left subtree's height, and its right subtree's height, and a null node returns zero."* Six clauses — six students minimum. If the chain breaks, restart at that student rather than rescuing them.

> *"That sentence is the entire algorithm. Part 2 turns it into code, and shows you the one thing that changes if a different textbook counts height in edges instead of nodes."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Recursion computes the root's height first, since the root is "first" | Reading order (top of the tree, top of the code) suggests top-down evaluation | Activity 1's bottom-up relay — refusing to accept a parent's height until both children's heights are already known |
| Height of a single-node tree is 0 | Confusing "height" with "number of edges" or with zero-indexed level counting | Explicitly stating the deck's own base-case note: empty tree → 0, single node → 1 |
| `height = leftHeight + rightHeight + 1` (sum instead of max) | Pattern-matching against other formulas (e.g., counting total nodes) rather than height specifically | Walking the formula chain in the Part 1 Wrap: it is `max`, not `+`, between the two subtree heights |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split at the Classroom Quiz boundary.**
- **This deck is internally consistent** — the worked example tree (root 1; left 2 with only a right child 4; right 3 with children 5 and 6, where 5 has only a left child 7) is used identically across the intro framing and the guided dry run. No conflicting tree or output was found here.
- Part 2 (session-07b) reuses this exact tree for the nodes-vs-edges contrast — no need to redraw it if your board still has it up.
