# Session 09b — Diameter Of Binary Tree (Part 2 of 2)

**Duration** 36 min · **Topic** Diameter of a Binary Tree — Optimal Approach & Full Dry Run · **Prerequisite** Session 09a — Diameter Of Binary Tree, Part 1 (definition, brute-force approach) · **Session type** Concept lecture

<!-- Split note: continues session-09 (original 55 min) right after the Classroom Quiz. This part is the core of the topic — the O(N²) redundancy reveal and the full 13-node optimal-approach dry run. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Diameter Of Binary Tree | https://docs.google.com/presentation/d/1uGpBJp47qrMbWN1Gd_GFTn_bKJ8B2k736frID7ONmn8/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Apply the optimal single-traversal algorithm (one `height()` call that also updates a running max diameter) to a given tree, producing both the height and the diameter in one pass. *(APPLYING)*
2. Analyze why combining height computation and diameter tracking into a single function eliminates the brute force's redundant work, reducing complexity from O(N²) to O(N). *(ANALYZING)* <!-- placement: inferred phrasing, content drawn from deck's own closing Brute Force / Optimal Solution summary slides -->

---

## Warm-Up Poll — Retrieval Practice on Session 09a (0–5 min)

Say: *"Four quick ones on diameter's definition before we walk the full tree."*

**Q1.** Diameter is measured in:
`A` Nodes · `B` Edges · `C` Levels · `D` Subtrees
→ *Read:* B.

**Q2.** Must the diameter's longest path pass through the root?
`A` Always · `B` Never · `C` It may or may not
→ *Read:* C.

**Q3.** What makes the brute-force diameter check O(N²)?
`A` Recomputing height from scratch at every node · `B` Using two arrays · `C` Sorting the nodes · `D` Recursion depth exceeding N
→ *Read:* A.

**Q4.** In Part 1's teaser, node 6 produced a diameter-here of 8, beating the root's 7. What does that already tell you about where the final answer can live?
→ *Read:* Open response — reconnects to "the answer isn't always at the root," which today's full dry run proves conclusively.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–8 min)

Say: *"Time to make your Part 1 prediction rigorous. We're counting exactly how many `height()` calls pass through one deep node — and then we're going to fix it."*

---

## ⚡ Activity 1 — Spot the Bug: Counting the Redundant Walks (8–14 min)

**Format:** Spot the Bug · **Exposes:** students accept "O(N²)" as a label without seeing *why* — they don't realize a deep leaf gets walked past by a fresh `height()` call from every single ancestor that needs a height above it.

**Setup line (say this):**
> *"Same 13-node tree from Part 1's teaser — node 14 is buried four levels down, under node 12, under node 10, under node 8, under node 6. When `diameter()` walks the tree top-down, calling `height()` on both children at every node it visits, how many separate `height()` calls end up passing through node 14 before the whole thing finishes?"*

**What students do:** Trace, on the board, every ancestor of node 14 that fires a `height()` call reaching down through it — node 12 (when computing its own left height), node 10 (same, one level up), node 8 (same), node 6 (same) — count them out loud.

**How it surfaces:** If a student says "just once, it's a leaf," redirect: *"Once for the `height()` call fired directly at it — but how many *different* `height()` calls, started at *different* nodes, pass through it on their way down?"* Walk the count together.

**Debrief line (say this):**
> *"Every node on the way to a deep leaf gets re-measured once for every ancestor above it that needed a height — and this happens for every node in the tree, not just node 14. That repeated re-walking, multiplied across the whole tree, is the entire O(N²). The optimal approach fixes exactly this the same way last session's balanced-tree fix did: one function computes the height and updates the answer, in the same single pass."*

**Cut rule:** If running short, state the redundancy verbally using node 14 as the example instead of counting live on the board — but keep the debrief line, it's the bridge into Slide Block B.

---

## Slide Block B (14–29 min) — DELIVER SLIDES AS-IS

Covers: Optimal Approach → the full node-by-node Dry Run (13-node tree) → Pseudocode → Complexity Analysis.

**Beats to emphasise**

- **The one-line insight, same shape as last session's fix:** fold the diameter tracking *into* `height()` itself. `height(root, &ans)` still returns `1 + max(leftHeight, rightHeight)` exactly as before — but on the way, it also does `ans = max(ans, leftHeight + rightHeight)`.
- **The full Dry Run — this is the core of the session.** Tree: root 3; children 4 (leaf), 5; node 5's children 6, 7 (leaf); node 6's children 8, 9; node 8's left child 10 (no right); node 10's left child 12 (no right); node 12's left child 14 (leaf); node 9's right child 11 (no left); node 11's right child 13 (no left); node 13's right child 15 (leaf). Walk it leaf-up, exactly as the deck does:

  | Node | left height | right height | diameter here (lh+rh) | ans after | height returned |
  |---|---|---|---|---|---|
  | 4 (leaf) | 0 | 0 | 0 | -1 → 0 | 1 |
  | 14 (leaf) | 0 | 0 | 0 | stays | 1 |
  | 12 | 1 (from 14) | 0 | 1 | 0 → 1 | 2 |
  | 10 | 2 (from 12) | 0 | 2 | 1 → 2 | 3 |
  | 8 | 3 (from 10) | 0 | 3 | 2 → 3 | 4 |
  | 15 (leaf) | 0 | 0 | 0 | stays | 1 |
  | 13 | 0 | 1 (from 15) | 1 | stays (1 < 3) | 2 |
  | 11 | 0 | 2 (from 13) | 2 | stays (2 < 3) | 3 |
  | 9 | 0 | 3 (from 11) | 3 | stays (3 = 3) | 4 |
  | **6** | **4 (from 8)** | **4 (from 9)** | **8** | **3 → 8** | 5 |
  | 7 (leaf) | 0 | 0 | 0 | stays | 1 |
  | 5 | 5 (from 6) | 1 (from 7) | 6 | stays (6 < 8) | 6 |
  | 3 (root) | 1 (from 4) | 6 (from 5) | 7 | stays (7 < 8) | 7 |

  **Final diameter = 8.** Longest path: 14 → 12 → 10 → 8 → 6 → 9 → 11 → 13 → 15 (8 edges) — and it never touches the root.
- **Stop on node 6 explicitly.** It's the one node whose *both* sides are tall (height 4 each) — it's the lowest common ancestor of the two farthest-apart leaves (14 and 15). Every other node on the eventual path only has one tall side, which is why `ans` only ever jumps at node 6.
- **Complexity:** Time O(N) — each node visited exactly once, constant work per node. Space O(H), recursion stack, worst case O(N) for a skewed tree.

**Checkpoint (at 29 min)** — cold-call:
> *"Why does `ans` jump from 3 to 8 at node 6, and not at the root, or anywhere else?"*
> **Answer:** Node 6 is the only node where both the left subtree (through 8→10→12→14) and the right subtree (through 9→11→13→15) are equally tall (height 4 each). Every node above node 6 — node 5, node 3 — only has one side that's tall; the other side is short, so their sums never come close to 8.

---

## ⚡ Activity 2 — Dry-Run Relay: Finish the Same Tree (29–34 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can now track `lh`, `rh`, and `ans` themselves — specifically whether they understand that height changes at *every* node while `ans` only changes *sometimes*.

**Setup line (say this):**
> *"Same tree, same table we just built. I'll point at a node from the right-hand branch — 9, 11, 13, or 15 — you give me left height, right height, diameter-here, and whether `ans` changes, before I confirm. If your height's right but your `ans` call is wrong, that's the mistake today is about."*

**What students do:** Relay through nodes 15, 13, 11, 9 in that order (leaf-up, right branch), one student per node, cold-called, stating all four numbers before the instructor confirms against the table above.

**How it surfaces:** The most common error is updating `ans` using the node's own *returned height* instead of `lh + rh` — e.g. saying "`ans` = 4" at node 9 instead of "diameter here = 0 + 3 = 3, no change, `ans` is already 3." When this happens, point at the pseudocode line `ans = max(ans, lh + rh)` and have the student re-read it aloud before re-answering.

**Debrief line (say this):**
> *"Height climbed by one at every single node on this branch. `ans` barely moved — it only jumps when a node has real length on *both* sides at once, and this branch never did until it joined up with the left branch at node 6. Two different numbers, tracked by the exact same function call — that's the whole trick of the optimal approach."*

**Cut rule:** If running short, relay only nodes 9 and 6 — the two nodes where `ans`'s final value is actually decided — and state the leaf/13/11 results directly instead of relaying them.

---

## Exit Ticket (34–36 min)

> Using today's 13-node tree: what is height(node 8), and what is the diameter contribution *at* node 8 (left height + right height)? Is node 8 responsible for the tree's final diameter of 8? Why or why not?
> **Answer:** height(8) = 4; diameter at node 8 = 3 + 0 = 3. Node 8 is **not** responsible — its own local sum never gets close to 8. The final diameter of 8 is decided entirely at node 6, where node 8's subtree height (4) and node 9's subtree height (4) combine as node 6's left and right heights.

Scan responses on the way out. If students answer "yes, node 8" or point at the root, that's the "diameter lives at the root" misconception resurfacing — worth a 30-second correction at the start of the next session.

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `ans` updates every time `height()` is called | Both live inside the same function call | Activity 2's debrief — height changes at every call; `ans` only changes when `lh + rh` beats the running max |
| Brute force "isn't really different," just written with two functions | The arithmetic (`lh + rh`, compare to max) looks identical in both approaches | Activity 1 — counting how many times a single deep leaf gets re-walked by separate `height()` calls |

---

## Instructor Notes

- **This is Part 2 of a 55-minute original session, split right after the Classroom Quiz.** This part carries the session's real weight — protect the full dry run's time above everything else in this part.
- **This deck is one dry run told three ways.** The 13-node tree's optimal-approach computation appears as a call-stack narrative (~slides 74-97) and again at extreme slide-by-slide granularity, one pseudocode line highlighted per slide (~slides 157-280) — well over 200 of the deck's 282 slides cover this single computation. This lesson plan follows the call-stack narrative pace; treat the ultra-granular slides as a self-study pointer for a student who wants to see every micro-step, not something to click through live.
- **Continuity note worth a spoken aside:** the deck's *other* optimal-approach dry run (an 8-node tree: root 1; children 2, 3; node 2's children 4, 5; node 4's left child 8; node 3's children 6, 7 — giving diameter 5) is the *identical* tree used for Session 08's balanced-tree optimal dry run. Worth telling students explicitly — "same tree, different question, same `height()` underneath" — as a continuity anchor, even though this lesson plan builds its main dry run and both activities around the 13-node tree instead.
- **Deck data-quality flag:** Example 2 in the edge-counting section (a separate, smaller reinforcement example, not the 13-node tree used above) has two different nodes both extracted as label "7" in the source text. <!-- placement: inferred — likely an artifact of overlapping diagram text boxes in the original slide; verify the actual node labels against the live slide before presenting that particular example, or skip it in favor of the 13-node tree, which is unambiguous. --> This lesson plan does not rely on that example anywhere.
