# Session 09a — Diameter Of Binary Tree (Part 1 of 2)

**Duration** 30 min · **Topic** Diameter of a Binary Tree — Definition & Brute Force · **Prerequisite** Balanced Binary Tree (Session 08) · **Session type** Concept lecture

<!-- Split note: original session-09 ran 55 min. Split right after the Classroom Quiz — same naive/optimal boundary used in Sessions 08 and 13. Part 1 covers the definition (edges, not nodes; path may skip the root) and the brute-force approach. Part 2 (session-09b) covers the O(N²) redundancy reveal and the full optimal-approach dry run — the core of the session. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Diameter Of Binary Tree | https://docs.google.com/presentation/d/1uGpBJp47qrMbWN1Gd_GFTn_bKJ8B2k736frID7ONmn8/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define the diameter of a binary tree as the longest path, measured in **edges**, between any two nodes — noting the path may or may not pass through the root. *(REMEMBERING)*
2. Explain why the brute-force approach recomputes `height()` from scratch at every node, producing O(N²) time. *(UNDERSTANDING)*
3. Apply the brute-force algorithm by hand — at each node, sum left height + right height, track a running global maximum — to a given tree. *(APPLYING)*

*(The optimal single-traversal algorithm and its full dry run are covered in Part 2 — that's the core of this topic.)*

---

## Warm-Up Poll — Retrieval Practice on Session 08 (0–8 min)

**Prerequisite: Balanced Binary Tree (Session 08)**

Say: *"Seven on last session before we move on. Today's problem reuses the exact same `height()` helper again — third session in a row — so if the balance check isn't solid, tell me now."*

**Q1.** What must be true at **every** node for a binary tree to be called "balanced"?
`A` Left and right subtree heights are exactly equal · `B` Left and right subtree heights differ by at most 1, and both subtrees are themselves balanced · `C` The tree has the same number of nodes on both sides · `D` All leaves are at the same level
→ *Read:* Answer B. If they pick A, that's the "must be equal" misconception from last session — the ≤1 tolerance is the whole point.

**Q2.** Last session's unbalanced example tree failed at one specific node, even though the root itself passed. Which node?
`A` The root · `B` Two levels down, where one side's height was 2 more than the other · `C` A leaf node · `D` It never failed
→ *Read:* Answer B. This is the "root looked fine but a deeper node failed" trap — flags whether last session's key takeaway actually stuck.

**Q3.** What is the time complexity of the **brute-force** balanced-tree check, and why?
`A` O(N), each node visited once · `B` O(N²), because `height()` is recomputed from scratch at every node · `C` O(log N) · `D` O(H)
→ *Read:* Answer B.

**Q4.** What is the one change the optimal approach makes to fix that?
`A` It skips checking some nodes · `B` It combines height computation and the balance check into a single traversal using a shared flag · `C` It uses a different formula for height · `D` It only checks leaf nodes
→ *Read:* Answer B. Hold onto this idea — today's optimal diameter approach makes the *identical* move.

**Q5.** *(MSQ — pick all that apply)* Which are true of the shared `ans`/flag variable in the optimal balanced-tree check?
`A` It starts as `true` · `B` It can flip back to `true` after being set `false` · `C` It gets set `false` the moment any node's height difference exceeds 1 · `D` It's shared across recursive calls
→ *Read:* A, C, D. B is false and worth calling out explicitly — once it fails, it stays failed.

**Q6.** For the optimal balanced-tree check, what determines its space complexity?
`A` O(N), always, regardless of tree shape · `B` O(H) — the recursion stack depth, worst case O(N) for a skewed tree · `C` O(1) · `D` O(N²)
→ *Read:* Answer B. (The deck's own slide states this inconsistently in one spot — if a student answers "O(N)" don't mark it wrong outright; use it to reinforce that O(H) and worst-case-O(N) are the same idea, not competing ones.)

**Q7.** True or False: a tree can be balanced overall even if it isn't visually symmetric — the same shape on both sides.
→ **True.** *Read:* Ties back to last session's balanced 8-node example, which passed without being shape-symmetric.

**Running it** — poll tool, ~40 s per question. Total 8 min including reads.

---

## Hook (8–11 min)

Draw the deck's small 6-node tree on the board: root 1; children 2, 3 (node 3 is a leaf); node 2's children 4 (leaf) and 5; node 5's child 6 (leaf).

Ask: *"Longest path between any two nodes in this tree — not from the root, between *any two*. Go."*

Let a few guesses land — most will instinctively measure from the root, the way `height()` trained them to for two sessions straight. Then trace it on the board: node 6 → node 5 → node 2 → node 1 → node 3. *"Four edges. Notice this path uses the root — but it didn't have to. Today's whole session is about a path that, in the tree we'll spend the most time on, skips the root completely."*

---

## Slide Block A (11–22 min) — DELIVER SLIDES AS-IS

Covers: Introduction/Definition → Problem Statement → Example 1 (6-node tree) → Brute Force Approach → brief Dry-Run teaser → Pseudocode/Code → Complexity Analysis.

**Beats to emphasise**

- **Diameter is measured in edges, not nodes** — say this against Session 07/08's `height()`, which counts *nodes* along a path. Same tree, different unit, if students blur the two they'll be off by one on every answer from here on.
- **The path may or may not pass through the root.** This directly contradicts the pattern set by two sessions of root-anchored `height()` calls — call this out explicitly, it's today's single biggest habit to break.
- **Example 1** (the hook's tree): longest path is node 6 → 5 → 2 → 1 → 3, diameter = 4 edges.
- **Brute Force Approach:** for *every* node, sum `height(left) + height(right)`; keep a running global maximum across the whole tree. Contrast directly with last session: balanced-tree checks used the *difference* of left/right height; diameter uses the *sum* — same two ingredients, different arithmetic, different goal.
- **Brute-force teaser only** (full walk comes in Part 2) — using the 13-node tree that anchors the rest of the session (root 3; children 4, 5; node 5's children 6, 7; node 6's children 8, 9; node 8's left child 10; node 10's left child 12; node 12's left child 14; node 9's right child 11; node 11's right child 13; node 13's right child 15):
  - At node 3 (root): left height = 1, right height = 6 → diameter here = 7 → `ans` = 7.
  - Skip ahead to node 6: left height = 4, right height = 4 → diameter here = 8 → `ans` = max(7, 8) = **8**. *"Hold that number — we're walking every node properly next session."*
- **Complexity:** O(N²) time (height recomputed fresh at every node), O(H) space.

**Checkpoint (at 22 min)** — cold-call:
> *"One sentence — what's the arithmetic difference between what `balanced()` checked last session and what `diameter()` checks today, given both call the same `height()` underneath?"*
> **Answer:** `balanced()` checks the *absolute difference* between left and right height at each node (must be ≤ 1). `diameter()` checks the *sum* of left and right height at each node, and keeps the running maximum across the whole tree.

---

## Classroom Quiz (22–27 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Two-Minute Paper (27–30 min)

**Why this strategy here:** Part 2 opens by counting exactly how redundant the brute-force approach is, then walks a long 13-node dry run. A short private writing task consolidates today's two ingredients (edges-not-nodes; root-optional) before that heavier lift, and gives you, the instructor, a fast read on who's ready.

**Run it (3 minutes):**
> *"Two minutes, on paper, no discussion: in your own words, what is the diameter of a binary tree, and why can't you assume it passes through the root? Use today's 6-node hook tree in your answer if it helps."*

Collect or scan a few on the way past (don't grade). If several answers still say "from the root," that's your cue to re-open next session with the hook tree redrawn before touching the 13-node tree.

> *"Next session that 13-node tree gets walked node by node, and you'll see exactly where — not at the root — the real answer hides."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Diameter is measured in nodes, like height | Two straight sessions of `height()` counting nodes | Contrast the hook's path (6→5→2→1→3, 4 edges, 5 nodes) — say both numbers out loud |
| The diameter always passes through the root | Every worked example in Sessions 07-08 was root-anchored | The hook's own path uses the root by coincidence, but Slide Block A explicitly flags that it doesn't have to — Part 2's main dry run proves it |
| `diameter()` and `balanced()` check the same thing, since both call `height()` | Same helper function, same recursive shape | Slide Block A's checkpoint: difference (≤1 test) vs. sum (maximize) |

---

## Instructor Notes

- **This is Part 1 of a 55-minute original session, split right after the Classroom Quiz** — the same naive/optimal boundary as Sessions 08 and 13.
- **Reuse the board drawing.** The 13-node tree (root 3 → 4, 5; 5 → 6, 7; 6 → 8, 9; 8 → 10 → 12 → 14; 9 → 11 → 13 → 15) introduced in the teaser here is the one Part 2 builds its entire dry run around — draw it once, leave it up, or photograph it for Part 2 if sessions are on different days.
- **Protect Part 2's time above all else.** If this part runs long, trim the brute-force teaser further (state node 6's numbers directly instead of also showing node 3) rather than rushing the Hook or Slide Block A's core definition.
