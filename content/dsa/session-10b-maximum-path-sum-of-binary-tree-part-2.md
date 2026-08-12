# Session 10b — Maximum Path Sum of Binary Tree (Part 2 of 2)

**Duration** 29 min · **Topic** Binary Tree — Maximum Path Sum: Deflection Points & the Negative-Sum Clamp · **Prerequisite** Session 10a — Maximum Path Sum of Binary Tree, Part 1 (definition, return-vs-update split, full dry run) · **Session type** Concept lecture

<!-- Split note: continues session-10 (original 60 min) right after the Classroom Quiz. This part is the deck's second, intuition-building pass — the "deflection point" framing — plus a relay drill and the Spot-the-Bug activity showing why the negative-sum clamp exists. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Maximum Path Sum of Binary Tree | https://docs.google.com/presentation/d/1GfVjTl50KdOAQMpefbNJ8GRcX4GXOln4qnkuWlOgckw/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Analyze, for a given node, the difference between the value it can *return* to its parent (its single best branch) and the value it *contributes* to the global answer (both branches combined) — the deck's own "deflection point" idea. *(ANALYZING)*
2. State and justify the O(N) time / O(H) space complexity of the optimal approach, and explain what breaks if the negative-sum clamp is removed. *(UNDERSTANDING)*

<!-- placement: inferred — phrased from the deck's own Approach/Complexity recap slides (15, 19, 42–43, 48–49, 82) -->

---

## Warm-Up Poll — Retrieval Practice on Session 10a (0–5 min)

Say: *"Four quick ones on the return-vs-update split before we give it a name."*

**Q1.** What does `maxDownPath` *return* to a node's parent?
`A` `data + L + R` · `B` `data + max(L, R)` · `C` Just `data` · `D` `max(L, R)` without adding data
→ *Read:* B — only the better single branch, because a path can't fork twice on its way up.

**Q2.** What does `maxDownPath` *feed into* the global `ans`?
`A` `data + max(L, R)` · `B` `data + L + R` · `C` `L + R` without data · `D` Just `data`
→ *Read:* B — both branches combined, since this node might be the actual bend point of the best path.

**Q3.** In Part 1's dry run, `ans` starts at:
`A` -1 · `B` 0 · `C` -1e9 / -infinity · `D` The root's value
→ *Read:* C.

**Q4.** At node 10 in Part 1's dry run (left contribution 17, right contribution 11), what value did node 10 hand up to node 1?
`A` 38 · `B` 27 · `C` 17 · `D` 11
→ *Read:* B — 27, its single better branch. 38 went into `ans` directly, it never traveled upward.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"Part 1 gave you the mechanics. Now the deck gives the same idea a name — 'deflection point' — and proves it with a list you'll read out loud in about ninety seconds."*

---

## Slide Block C (7–17 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide-block boundary, slides 50–121 -->
Covers: a second pass over path vocabulary (any-node path, path sum, "maximum path sum" defined again with the -20/25/10 tree) → the "deflection point" framing, worked across the same 1/2/10-rooted tree — for each candidate deflection node (1, 2, 3, 4, 8, 9, 10, 5, 6), the deck computes the max path sum "deflecting" at that node, landing on node 10's 38 as the overall winner → a line-by-line walkthrough of the `maxDownPath`/`maxPathSum` pseudocode.

**Beats to emphasise**

- **"Deflection point" is just a name for "the node where the path stops going up and starts going down the other side."** Every node in the tree is a *candidate* deflection point; the algorithm's job is to find the deflection point with the highest combined sum. Node 10 (sum 38) wins over node 1 the root (sum 34) — deliberately picked by the deck to prove the answer does **not** have to live at the root.
- The deck recomputes the same 1/2/10 tree's deflection sums explicitly: node 1 → 34, node 4 → 4, node 2 → 9, node 3 → 3, node 10 → **38**, node 9 → 17, node 8 → 8, node 5 → 11, node 6 → 6. Reading this list aloud in order is the fastest way to make "the answer can be anywhere" concrete.
- The pseudocode walkthrough (line-by-line: base case → recurse left, clamp to 0 if negative → recurse right, clamp to 0 if negative → compute `x = data + L + R` → update `ans` → return `data + max(L, R)`) is a direct, slower repeat of Part 1's Slide Block B — deliver it at a brisk pace as reinforcement, not as new material.

**Checkpoint (at 17 min)** — cold-call:
> *"Is the maximum path sum guaranteed to pass through the root? Why or why not?"*
> **Answer:** No — exactly like yesterday's diameter, the answer is the best value across *every* node's deflection sum, and in today's own worked example the winning deflection point is node 10, not the root (node 1).

---

## ⚡ Activity 2 — Live Coding / Dry-Run Relay (17–22 min)

**Format:** Dry-Run Relay · **Exposes:** whether students can independently keep the return-value and the `ans`-update separate at each node, without you narrating it for them.

**Setup line (say this):**
> *"Same tree as the deck's walkthrough — root 1, left child 2 (with leaf children 4 and 3), right child 10 (with subtree 9→8 on one side and 5→6 on the other). I'll call a node, you give me two numbers: what it returns to its parent, and what it feeds into the running max."*

**What students do:** Call on a different student per node, working bottom-up: node 4, node 3, node 2, node 8, node 9, node 6, node 5, node 10, node 1. Each answers with (return value, ans-candidate).

**How it surfaces:** The most common slip is feeding `max(L, R)` into `ans` instead of `L + R` (or vice versa for the return value). When it happens, write both formulas on the board side by side and re-ask just that one node.

**Debrief line:**
> *"Node 10 is where the real answer lives — 10 + 17 + 11 = 38, using BOTH its branches. But node 10 could only ever hand 27 up to node 1, because a path can't fork twice. That gap — 38 stays exactly where it is, 27 is all that travels upward — is the entire trick of this algorithm."*

**Cut rule:** If running short, skip the leaf nodes (4, 3, 8) — state their values aloud yourself (a leaf always returns its own value) and start the relay at node 9.

---

## ⚡ Activity 3 — Spot the Bug (22–27 min)

**Format:** Spot the Bug · **Exposes:** what breaks when the "if L < 0, set L = 0" / "if R < 0, set R = 0" clamp is deleted from `maxDownPath` — i.e., why "ignoring negative sums" has to be an explicit step, not an assumption.

**Setup line (say this):**
> *"I've deleted two lines from the pseudocode — the ones that reset L and R to 0 when they come back negative. Same tree as Part 1's Activity 1: root 15, -20 and 25 as children, 5 under -20, 10 under 25. Trace it by hand without the clamp — what wrong answer does this buggy version produce, and at which node does it go wrong?"*

**What students do:** In pairs, retrace node `-20` → node `15` on paper, without clamping negative values to zero.

**How it surfaces (the answer):** Without the clamp, node `-20` returns `-20 + max(5, 0) = -15` up to the root instead of being blocked. At node `15`: unclamped `L = -15`, `R = 35` (from the 25/10 branch), so `x = 15 + (-15) + 35 = 35`, and `ans` never climbs past 35. **The buggy version reports 35, not 50.**

**Debrief line:**
> *"Without the clamp, a strongly negative branch reaches all the way up and drags the root's own path sum down with it. Those two 'if it's negative, treat it as zero' lines are the only thing standing between this algorithm and a wrong answer on any tree that has a bad branch sitting above a good one."*

**Cut rule:** If running late, skip the pair-tracing — ask the class only "will the buggy answer be higher or lower than 50?" (lower), reveal 35, and go straight to the debrief.

---

## Exit Ticket (27–29 min)

> On paper or in chat: *"Draw any 3-node tree with at least one negative value. Write the maximum path sum, and underline the node(s) your path does NOT use."*
> **Answer shape:** Any correct trace is acceptable — the point is that the underlined, excluded node(s) should be exactly the ones whose branch contribution is negative.

Scan responses on the way out. If several students route their path *through* a negative node anyway, that's the signal to reopen Activity 3's clamp explanation before Session 11 begins.

This closes the two-part Session 10.

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The maximum path sum must pass through the root | Carried over from thinking of trees as always rooted at the "main" computation | Slide Block C's deflection-point list, where node 10 (not the root) wins |
| The negative-sum clamp is a minor optimization, not a correctness requirement | It's presented as a small "if negative, set to 0" line, easy to skim past | Activity 3's Spot-the-Bug — deleting it produces a wrong final answer (35 instead of 50), not just a slower one |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz.**
- **Pacing risk:** Slide Block C's pseudocode line-by-line walkthrough repeats Part 1's Slide Block B almost verbatim — if running long, compress that walkthrough rather than cutting Activity 3, which is the only place students see concretely *why* the negative-sum clamp exists rather than just being told it exists.
- **Keep the 1/2/10-rooted tree drawn on the board (or a slide) through Slide Block C and Activity 2** — both reuse it, and redrawing it wastes minutes you don't have.
