# Session 13a — Lowest Common Ancestor of a Binary Tree (Part 1 of 2)

**Duration** 36 min · **Topic** Binary Tree — LCA: Definition & Bruteforce · **Prerequisite** Right view of Binary Tree (Session 12) · **Session type** Concept lecture

<!-- Split note: original session-13 ran 60 min. Split right after the Classroom Quiz — the same naive/optimal boundary used in Sessions 08 and 09. Part 1 covers the LCA definition (including the self-ancestor edge case) and the bruteforce path-comparison approach. Part 2 (session-13b) covers the optimal recursive approach, its two dry runs, and the closing Spot-the-Bug activity. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Lowest Common Ancestor of a Binary Tree | https://docs.google.com/presentation/d/1PfK6oST_X-plBPAQkknErZZXRYBwoNHF826rRmBc7b8/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define the Lowest Common Ancestor (LCA) of two nodes `p` and `q` as the deepest node that is an ancestor of both — and state the rule that a node counts as its own ancestor/descendant. *(REMEMBERING)*
2. Contrast the bruteforce root-to-node path-comparison approach with what an optimal approach would need to avoid. *(ANALYZING)* <!-- placement: inferred phrasing — both approaches are explicitly named and dry-run in the deck (slides 39–44 vs. 10–35, 45–121) -->

*(The optimal recursive algorithm and its full dry run are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Right view of Binary Tree (Session 12) (0–6 min)

> Retrieval practice on the session immediately before this one. No new content — this is recall.

Say: *"Seven quick ones on yesterday's Right View problem before we move to today's topic."*

**Q1.** In Right View, do we keep the FIRST node dequeued at each level, or the LAST?
`A` First · `B` Last
→ *Read:* B — the last node dequeued at a level is the rightmost, and therefore visible.

**Q2.** True or False: the Right View algorithm uses a map keyed by column, the same way Top View does.
`A` True · `B` False
→ *Read:* False. No map, no horizontal distance — just a queue and level-by-level tracking.

**Q3.** What do we snapshot as `len = q.size()` BEFORE entering the inner loop, and why?
`A` The total number of nodes in the tree · `B` The number of nodes at the current level, so children pushed during this level don't blur the boundary · `C` A random buffer size · `D` The tree's height
→ *Read:* B — that snapshot is what lets the loop process exactly one level at a time.

**Q4.** For the tree root `8`; left `2`, right `6`; `2`'s left `3`; `6`'s left `1`, right `5`; `1`'s left `0` — what is the right view?
`A` 8, 2, 6 · `B` 8, 6, 5, 0 · `C` 8, 6, 1, 0 · `D` 8, 3, 5, 0
→ *Read:* B (`8, 6, 5, 0`) — straight from the deck's own dry-run tree.

**Q5. (MSQ)** Which of these are true about Right View's complexity? *(pick all that apply)*
`A` Time is O(N) — each node visited once · `B` Space is O(N) — the queue can hold up to N/2 nodes at the widest level · `C` Time is O(N log N) like Top View · `D` Space depends on tree height only
→ *Read:* A and B. C is the trap — that log factor belongs to Top View's map, not Right View.

**Q6.** A student claims: "Right View is just root → right → right → right... until null." Is this always correct?
`A` Yes, always · `B` No — it can miss a node whose rightmost position at some level hangs off a left branch deeper in the tree
→ *Read:* B — this was Session 12's Activity 3, and it comes back today in a different disguise.

**Q7.** Inside the level's loop, what happens to `temp` on every iteration, and when does it get pushed into `ans`?
`A` It accumulates a growing list; pushed every iteration · `B` It's overwritten by the current node's data each iteration; pushed to `ans` once, after the loop for that level ends
→ *Read:* B — `temp` is disposable, `ans` only wants the survivor.

**Running it** — poll tool, ~30–40 s per question. Total 6 min.

---

## Hook (6–9 min)

Put the deck's definition tree on the board: some tree with two nodes marked `p` and `q`.

Say: *"Point at the lowest common ancestor of these two marked nodes. Just point — you have eyes, a brain, and three seconds."*

Let a few students point correctly at a glance. Then: *"Every one of you just did that instantly, by eye. Now the actual assignment: write a rule a computer can follow, that gets the same answer, on a tree with a thousand nodes you can't glance at."*

Tie forward: *"Today you'll see two such rules — one that's obvious but wasteful, and one that's clever and does it in a single pass. Part 1 is the obvious one."*

---

## Slide Block A (9–16 min) — DELIVER SLIDES AS-IS

Covers: Definition of LCA ("the node located deepest in the tree that serves as an ancestor to two nodes p and q; a node is considered its own descendant") → Problem Statement → Example 1 (same tree, `p=4, q=14` → LCA `8`) → Example 2 (root `20/10/30/5/15/25/35/3/7/null/null/22`, `p=3, q=10` → LCA `10`).

**Beats to emphasise**

- **"A node is considered its own descendant" is not a footnote — it's the edge case that trips up almost every first attempt.** Example 2's query (`p=3, q=10`) is deliberately chosen so that `q=10` is itself an ancestor of `p=3` — the correct answer is `10` itself, not some node further up.
- Example 1's tree structure (same tree reused throughout the deck) has `p=4, q=14` landing in different subtrees of the root, giving LCA `8` — contrast this immediately against Example 2, where one target sits *above* the other. <!-- placement: inferred — Example 1's exact node layout in the raw slide text is reconstructed by cross-checking against the "Bruteforce Approach" tree (slide 39) that reuses the same structure; confident but worth a second look against the live deck before class -->
- Don't over-explain yet — the "why" for both examples is what Part 2 builds toward.

**Checkpoint (at 16 min)** — cold-call two students:
> *"If q is already an ancestor of p, what's the LCA?"*
> **Answer:** `q` itself — a node counts as its own ancestor/descendant, so there's no need to look any further up the tree.

---

## ⚡ Activity 1 — Predict-the-Output: The Self-Ancestor Case (16–21 min)

**Format:** Predict-the-Output · **Exposes:** whether the "a node is its own descendant" rule actually landed, before students see the mechanical algorithm that enforces it. This is the deck's own Example 2 (`p=3, q=10` → LCA `10`) — stated in the deck but never dry-run step by step, which makes it ideal for prediction rather than replaying an animation.

**Setup line (say this):**
> *"Tree on the board: root 20; left 10, right 30; 10's children are 5 and 15; 30's children are 25 and 35; 5's children are 3 and 7; 25's left child is 22. Find node 3 and node 10. Before I say anything else — what's their LCA? Write it down."*

**What students do:** Write a single answer silently (10 seconds), then show hands for their answer.

**How it surfaces:** If students propose a deeper node — e.g. `5` (the parent of `3`) — because they're hunting for "the first place the two paths overlap" without noticing `10` is already an ancestor of `3`: walk the ancestor chain out loud — `3`'s ancestors are `5, 10, 20`; `10`'s ancestors are `20` (and itself). The deepest node common to both lists is `10` itself, precisely because `10` is allowed to be its own ancestor.

**Debrief line:**
> *"The moment one of your two target nodes sits on the path to the other, that target node IS the answer. Don't go hunting past it — you'd only be climbing further from the deepest common point, not closer."*

**Cut rule:** If running late, skip the written prediction and jump straight to the show-of-hands, then move directly into the debrief line.

---

## Slide Block B (21–28 min) — DELIVER SLIDES AS-IS

Covers: Bruteforce Approach — tree root `8`; left `3`, right `10`; `3`'s children `1, 6`; `10`'s children `null, 14`; `6`'s children `4, 7`; `14`'s left `13`; query `p=1, q=7` → path to `p`: `8 → 3 → 1`; path to `q`: `8 → 3 → 6 → 7`; common nodes: `8, 3`; lowest common = `3`.

**Beats to emphasise**

- This approach is deliberately simple to build trust: find the full root-to-node path for `p`, find the full root-to-node path for `q`, walk both paths together and take the last node they still agree on.
- Say explicitly what it costs: two full traversals to build both paths, plus the paths themselves stored in memory — O(N) time, O(Height) extra space for the stored paths, same as the optimal approach's space bound, but with more up-front work and two arrays to maintain instead of one pass.
- This tree and this exact query (`p=1, q=7` → LCA `3`) is the same one Part 2's optimal recursive approach dry-runs next — flag that connection so students recognise it's the same problem, solved two ways.

**Checkpoint (at 28 min)** — show hands:
> *"What are the two costs of the bruteforce approach that Part 2's optimal approach is about to avoid?"*
> **Answer:** It needs two separate searches (one for `p`, one for `q`) instead of one combined pass, and it needs to explicitly store both root-to-node paths to compare them.

---

## Classroom Quiz (28–33 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Whip-Around (33–36 min)

**Why this strategy here:** Part 1 ends on a cost list (two searches, two stored paths) that Part 2's optimal approach is about to demolish. A fast whip-around — one word or phrase each, no pass allowed — makes every student publicly commit to a piece of that cost list, so Part 2's reveal lands as "watch this get eliminated," not fresh information.

**Run it (3 minutes):**
> *"Going around the room, one word or short phrase each, no repeats: name ONE thing the bruteforce LCA approach has to do that you suspect a smarter approach wouldn't need. Go fast — if you can't think of a new one, say 'pass' and we'll circle back."*

Expected answers to listen for: "two searches," "storing both paths," "comparing paths afterward," "extra memory." Write them in a running list on the board.

> *"Keep that list up. Next session, watch how many of these the optimal approach just... doesn't do."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The LCA must be a node distinct from both `p` and `q` | Feels wrong for one target to "be" the ancestor of the other | Activity 1 — Example 2's `p=3, q=10` case, where the correct answer is `10` itself |
| Bruteforce is "basically the same" as whatever the optimal approach turns out to be | Both eventually produce the same LCA node | The Part 1 Wrap's cost list — bruteforce's costs are concrete and countable, which makes the optimal approach's savings concrete too |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz** — the same naive/optimal boundary as Sessions 08 and 09.
- **Example 1's exact tree layout (slides 5–7, `p=4, q=14` → LCA `8`) is reconstructed by inference** — the raw slide text for this specific tree is more garbled than Example 2's clean `root = ...` list. It's cross-checked and consistent with the tree reused later in the "Bruteforce Approach" section (slide 39), so confidence is reasonably high, but glance at the live deck before presenting it as fact.
- **Keep the bruteforce tree (root 8; left 3, right 10; 3's children 1, 6; 10's children null, 14; 6's children 4, 7; 14's left 13) drawn on the board** — Part 2 dry-runs the optimal approach on this exact tree and query first, before moving to a second tree.
