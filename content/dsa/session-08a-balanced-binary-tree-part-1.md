# Session 08a — Balanced Binary Tree (Part 1 of 2)

**Duration** 30 min · **Topic** Balanced Binary Tree — Definition & Brute Force · **Prerequisite** Height of a Binary Tree (Session 07) · **Session type** Concept lecture

<!-- Split note: original session-08 ran 50 min. Split right after the Classroom Quiz, which falls right after the brute-force definition/complexity block — a clean "naive approach" vs. "optimal approach" boundary, same pattern as Sessions 09 and 13. Part 1 covers the definition and brute-force approach. Part 2 (session-08b) covers the O(N²) redundancy reveal and the optimal single-pass solution. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Balanced Binary Tree | https://docs.google.com/presentation/d/1MscAVuewwMhNE52LB11SF5Rp6zEcccmvaXrZa08GS2I/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define a balanced binary tree: for every node, the heights of its left and right subtrees differ by at most 1, **and** both subtrees are themselves balanced. *(REMEMBERING)*
2. Explain why the brute-force approach recomputes `height()` from scratch at every node, producing O(N²) time. *(UNDERSTANDING)*
3. Apply the brute-force algorithm by hand — compute the height difference at a node, decide pass/fail, recurse — to determine whether a given tree is balanced. *(APPLYING)*

*(The optimal single-pass algorithm is covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 07 (0–8 min)

**Prerequisite: Height of a Binary Tree (Session 07)**

Say: *"Eight quick ones on last session. Today's whole topic is built directly on top of `height()` — if that function is shaky, say so now, not halfway through today."*

**Q1.** What does the "height" of a binary tree measure?
`A` Number of nodes in the tree · `B` Number of levels in the tree / number of nodes along the longest root-to-leaf path · `C` Number of leaf nodes · `D` Number of edges only
→ *Read:* If most pick A, they're confusing height with total node count (size) — clear this up in one sentence before Slide Block A, which assumes it's solid.

**Q2.** What is the height of an empty tree?
`A` 0 · `B` 1 · `C` -1 · `D` Undefined
→ *Read:* Answer is A. Also restate: a tree with a single node has height 1 — that's the other base fact from Session 07 today's pseudocode inherits unchanged.

**Q3.** The recursive formula from last session: `height(root) = ?`
`A` `max(leftHeight, rightHeight)` · `B` `1 + max(leftHeight, rightHeight)` · `C` `leftHeight + rightHeight` · `D` `1 + leftHeight + rightHeight`
→ *Read:* Answer B. Today's `balanced()` calls this exact formula — verbatim, no changes.

**Q4.** *(MSQ — pick all that apply)* Which are true about `height()`'s base case?
`A` Returns 0 when root is null · `B` Returns -1 in the edges-based definition some textbooks use · `C` Returns 1 always · `D` Is checked before recursing into children
→ *Read:* A, B, D. This MSQ is the setup for today's pseudocode, which reuses this exact base case.

**Q5.** In Session 07's worked tree (root 1; children 2, 3; node 2's child 4; node 3's children 5, 6; node 5's child 7), height(4) = 1. What is height(node 2)?
`A` 1 · `B` 2 · `C` 3 · `D` 0
→ *Read:* height(2) = 1 + max(0, 1) = 2. Answer B. If they say 1, they forgot the `+1` for node 2 itself.

**Q6.** In the same tree, what is the final height of the whole tree (at the root)?
`A` 3 · `B` 4 · `C` 5 · `D` 2
→ *Read:* Answer B (h(1) = 1 + max(h(2)=2, h(3)=3) = 4). If they say 3, walk the `+1` at the root again out loud.

**Q7.** What is the time complexity of computing height recursively?
`A` O(log N) · `B` O(N) · `C` O(N²) · `D` O(H)
→ *Read:* Answer B — every node visited exactly once. Hold this number; today you'll see what happens when a function calls `height()` *repeatedly*.

**Q8.** What is the worst-case space complexity of `height()`, and when does it occur?
`A` O(H), worst case O(N) for a skewed tree · `B` O(N), always · `C` O(1) · `D` O(H), worst case O(log N)
→ *Read:* Answer A. This O(H)-via-recursion-stack idea carries over unchanged into today's functions — flag it now so it isn't "new" later.

**Running it** — poll tool, ~40 s per question, project the distribution. Total 8 min including reads.

---

## Hook (8–11 min)

Draw two trees on the board, same rough size, unlabeled as to which is which — one is today's deck's Example 1 (root with a node two levels down whose subtrees differ by 2), one is Example 2 (root with a node two levels down whose subtrees differ by 1). Don't say which is which.

Ask: *"By eye — which of these two looks more 'balanced' to you?"*

Let disagreement happen; both look like reasonably full trees at a glance. Then: *"Here's the problem — 'balanced' isn't a look. It's a number, checked at every single node, and the check is done by a function you already know."* Hold up last session's `height()` pseudocode. *"Today, `height()` gets called twice per node, and what it returns decides whether that node passes or fails. One of these two trees fails — and not at the root."*

---

## Slide Block A (11–22 min) — DELIVER SLIDES AS-IS

Covers: Introduction/Definition → Problem Statement → Example 1 (False) & Example 2 (True) → Brute Force Approach → brief Dry-Run glimpse → Pseudocode/Code → Complexity Analysis.

**Beats to emphasise**

- **The definition is recursive, not a one-time check.** "Heights differ by at most 1" must hold at *every* node, and both subtrees must *themselves* be balanced — say this twice, it's the single most missed idea of the session.
- **Example 1 (False):** the deck's own explanation: *"At node 2, left subtree height = 2, right subtree height = 0. Difference = 2 → exceeds 1. Hence the tree is not balanced."* Note out loud that this is a 7-node tree carried over from Session 07's own height example — same shape, new question.
- **The Dry Run for Example 1 only checks two nodes before it stops:** node 1 (its own children's heights differ by 1 → passes) then node 2 (its own children's heights differ by 2 → **fails, and the walk stops there**). <!-- placement: inferred — deck's dry run for this tree only shows checks at node 1 and node 2 before concluding "not balanced"; it does not walk node 3's side, illustrating that one failing node anywhere is enough to short-circuit the whole result. Exact left/right child assignment for this tree is not fully recoverable from the extracted deck text — the height/diff numbers themselves are given directly and are what this beat relies on. -->
- **Brute Force Approach:** for each node, `height()` is called fresh on both children — and that `height()` call walks the *entire* subtree underneath, every time. This is the seed for Part 2's Activity 1.
- Quick teaser only — don't do the full brute-force dry run here (that's Part 2's job): show the pseudocode's two functions (`height()`, `balanced()`) side by side and point out `balanced()` calls `height()` twice, then calls *itself* twice more, each of which will call `height()` twice again.
- **Complexity:** O(N²) time (`height()` recomputed at every node), O(H) space (recursion stack).

**Checkpoint (at 22 min)** — cold-call:
> *"In one sentence — what's the difference between what today's `height()`-based check does, and what plain `height()` did last session?"*
> **Answer:** Last session, `height()` just returned a number. Today, `balanced()` calls `height()` on both children and checks whether the *difference* between those two numbers is more than 1 — same helper function, new arithmetic on top.

---

## Classroom Quiz (22–27 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Predict-and-Defend Pairs (27–30 min)

**Why this strategy here:** Part 2 opens by proving the brute-force approach is O(N²) through a redundancy count. Before showing that proof, this wrap makes students commit to a prediction and a reason — so the reveal in Part 2 either confirms or corrects a stance they've publicly taken, which sticks better than a fresh unmotivated demonstration.

**Run it (3 minutes):**
> *"With your partner: `balanced()` calls `height()` on both children of every node. For an 8-node tree, roughly how many total `height()` calls do you think fire before the whole check finishes — close to 8, or a lot more than 8? Agree on a number and a one-sentence reason before I call on pairs."*

Take 2-3 pairs' guesses and reasons out loud, don't confirm or deny yet.

> *"Hold onto your number. First thing next session, we count it for real on this exact tree — and if you guessed 'close to 8,' you're about to see why that's wrong."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A tree is balanced if the root's two subtrees look roughly equal in height | Natural to stop checking once the top level looks fine | Slide Block A's Example 1 walk — root passes (diff 1), node 2 fails |
| "Balanced" means visually symmetric — same shape on both sides | Informal, everyday use of the word "balanced" | Point at the definition: the *only* test is the ≤1 height-difference rule, not shape |
| If the root passes, every node passes | Inverse of the row above — assuming the check is "monotonic" from the top down | Same Example 1 walk: root passes, node 2 (two levels down) fails anyway |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split right after the Classroom Quiz** — a naive-approach / optimal-approach boundary, same shape as Sessions 09 and 13.
- **Example 1's exact left/right structure is not fully recoverable from the source deck text** — only the height/diff numbers at node 1 and node 2 are given directly. This lesson plan relies only on those numbers, not a specific left/right diagram, for that tree.
- Have the 8-node balanced tree (root 1; children 2, 3; node 2's children 4, 5; node 4's left child 8; node 3's children 6, 7) ready to draw at the start of Part 2 — it's used throughout that session.
