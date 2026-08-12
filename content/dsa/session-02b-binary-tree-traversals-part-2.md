# Session 02b — Binary Tree Traversals (Part 2 of 2)

**Duration** 38 min · **Topic** Binary Tree Traversals — In-order, Pre-order, Post-order & Level-order · **Prerequisite** Session 02a — Binary Tree Traversals, Part 1 (Node template, why traversal matters) · **Session type** Concept lecture

<!-- Split note: continues session-02 (original 60 min) from the Slide Block B boundary. Part 1 covered the Node template and motivation; this part covers the four traversal orders and their worked dry runs. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Binary Tree Traversals | https://docs.google.com/presentation/d/1Jd2OWb4FjwoWDe6efW1-Zl5ce2aEok950kLvW1FoAPY/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the visit-order rule for each of the four traversal types: In-order (Left, Root, Right), Pre-order (Root, Left, Right), Post-order (Left, Right, Root), and Level-order (level by level, left to right). *(REMEMBERING)*
2. Apply each of the four traversal rules to a given 7-node binary tree to produce its correct output sequence. *(APPLYING)*
3. Differentiate the three Depth-First orders (which all recurse into one subtree before the other) from Breadth-First/Level-order (which finishes an entire level before moving down). *(ANALYZING)* <!-- placement: inferred -->

---

## Warm-Up Poll — Retrieval Practice on Session 02a (0–6 min)

Say: *"Six questions on the Node template and why we traverse at all, before we put four different orders on top of it."*

**Q1.** A `Node` object in this course's tree implementation holds which fields?
`A` data, next · `B` data, left, right · `C` data, left, right, parent · `D` data only
→ *Read:* B. If `parent` or `next` shows up, that's carried over from linked-list thinking — correct it before today's traversals, which never touch a parent pointer.

**Q2.** What does a brand-new node's constructor set `left` and `right` to?
`A` 0 · `B` The node itself · `C` null / None · `D` Undefined, doesn't matter
→ *Read:* C — this was Activity 1's whole point (a missing `left = nullptr` line breaks this guarantee).

**Q3.** Which of these is a valid reason to traverse a tree?
`A` Only to print all values · `B` To check whether a value exists (Data Retrieval) · `C` Both A and B, plus locating a node to modify the tree · `D` Traversal has no practical use
→ *Read:* C.

**Q4.** True or false: traversal must visit every node in the tree, and each node exactly once.
`A` True · `B` False
→ *Read:* True — this is the Session 02a definition, word for word, and it's the rule every order below has to satisfy.

**Q5.** *(MSQ — pick all that apply)* Data Retrieval, as defined last session:
`A` Only reads values, never changes the tree · `B` Is the same operation as Tree Modification · `C` Can use any traversal order to check existence · `D` Requires deleting the found node
→ *Read:* A and C.

**Q6.** Session 02a's Spot-the-Bug activity broke a constructor by skipping one line. Which pointer was left uninitialized?
`A` data · `B` right · `C` left · `D` Both left and right
→ *Read:* C.

**Running it** — poll tool, ~40 s/question. Total 6 min including reads.

---

## Bridge (6–9 min)

Say: *"Part 1 gave you the Node — one value, two pointers. Today you visit that same node four different ways, and the ONLY thing that changes each time is when you print the node's own value relative to its two children."*

Redraw the 7-node tree (root 1; left child 2 with children 4, 5; right child 3 with children 6, 7) and ask: *"If I told you 'root first, then left, then right' — walk me through the first three values you'd print, out loud, right now, before I've defined anything else."* Take one attempt (correct answer: 1, 2, 4 — this previews Pre-order without naming it yet), then: *"That's one of today's four rules. Let's make all four precise."*

---

## Slide Block B (9–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide range — Slides 21-33: Types of Traversal (DFS vs. BFS), In-order, Pre-order, Post-order definitions with the DFS summary table, and the BFS/Level-order definition -->

**Beats to emphasise**

- **Two families: DFS and BFS** (Slide 21). DFS goes deep into one subtree before moving to the next, using recursion or an explicit stack. BFS visits level by level, left to right (Slide 22, Slide 33).
- **The three DFS orders, stated exactly as the deck's own summary table gives them** (Slide 32) — say all three back-to-back so the contrast is audible:
  - **In-order:** Left subtree → Root → Right subtree
  - **Pre-order:** Root → Left subtree → Right subtree
  - **Post-order:** Left subtree → Right subtree → Root
- The only difference between the three is **when the root gets visited relative to the two subtrees** — before both (pre), between them (in), or after both (post). Say this explicitly; it's the one-sentence version of the whole block.
- **Level-order / BFS** is fundamentally different in mechanism, not just order — it needs a queue (finish this level completely before starting the next), not simple root-left-right recursion (Slide 33).

**Checkpoint (at 19 min)** — show of hands:
> *"Two of the three DFS orders visit the left subtree before touching the root. Which one visits the root FIRST, before either subtree?"*
> **Answer:** Pre-order — Root, Left, Right.

---

## ⚡ Activity 2 — Predict-the-Output: In-order vs. Pre-order vs. Post-order (19–27 min)

**Format:** Predict-the-Output · **Exposes:** the tendency to default to level-order (reading the diagram left-to-right, top-to-bottom) regardless of which specific rule was asked for.

**Setup line (say this):**
> *"Same seven-node tree every time — root 1, left child 2 with children 4 and 5, right child 3 with children 6 and 7. I name the rule, you give me the full sequence, using only the definition — Left/Root/Right in whatever order that rule says. No calculators, no guessing from the picture."*

Run the deck's own fully-worked dry run, one order at a time, taking a full-sequence prediction before each reveal:

- **In-order** (Left, Root, Right) → **4, 2, 5, 1, 6, 3, 7** (Slides 63-67)
- **Pre-order** (Root, Left, Right) → **1, 2, 4, 5, 3, 6, 7** (Slides 68-72)
- **Post-order** (Left, Right, Root) → **4, 5, 2, 6, 7, 3, 1** (Slides 73-78) <!-- placement: inferred — the deck-text extraction shows the final value as "10" (Slide 78: "4, 5, 2, 6, 7, 3, 10"), which cannot be correct since the tree's root value is 1, not 10, and post-order always ends on the root. Treat this as a transcription artifact and use 1; verify against the live slide before presenting. -->

**What students do:** Predict the full 7-value sequence out loud (or write it down) before each reveal; compare against the deck's worked build-up node by node.

**How to handle wrong answers:** The single most common miss is defaulting to **1, 2, 3, 4, 5, 6, 7** (level-order) no matter which rule was asked — call this out by name the first time it happens: *"That's level-order. Nobody asked for level-order yet. Re-check: does Left, Root, Right actually visit node 3 second?"* For In-order vs. Pre-order confusion specifically (both visit left first), the giveaway is WHEN the root appears — Pre-order prints it immediately, In-order only after the entire left subtree is done.

**Debrief line:**
> *"Same seven numbers, three completely different sequences, from the exact same tree. The order you visit left, root, and right isn't a detail — it IS the algorithm. Get it backwards and you don't get a wrong answer to the same traversal, you get a different traversal entirely."*

**Cut rule:** If running short, drop Post-order and run In-order vs. Pre-order only — those two are the most commonly confused pair (both start by going left) and carry the most diagnostic value.

---

## ⚡ Activity 3 — Level-Order Dry-Run Relay (27–33 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** treating BFS as "just another DFS order" instead of a fundamentally different, queue-based mechanism.

**Setup line (say this):**
> *"Same tree, one more time — but now I'm going row by row, not branch by branch. When I point at a level, that row calls out its values left to right, together, fast — like a queue, not like the recursive digging we just did."*

Run the deck's own level-by-level build-up (Slides 79-81) as a relay: root first, then the whole of level 1, then the whole of level 2.

- Level 0: **1**
- Level 1: **2, 3**
- Level 2: **4, 5, 6, 7**
- Full sequence: **1, 2, 3, 4, 5, 6, 7**

**What students do:** Assign rows of the room to levels if the class is large enough; each "level" calls out its values together, in order, when pointed at.

**How to handle wrong answers:** If a group jumps ahead depth-first (e.g. calls out "1, 2, 4" instead of waiting for the full level), stop and contrast directly with Activity 2: *"That's the DFS instinct again. BFS finishes the ENTIRE current level before dropping down one — nobody visits a grandchild before every child has been visited first."*

**Debrief line:**
> *"Level-order is the only one of the four traversals that needs a queue instead of straightforward recursion — and it's the one that matches how you'd naturally scan an org chart or a file browser's tree view, one row at a time."*

**Cut rule:** If running short, skip the row-by-row relay entirely and have the whole class chorus the full sequence once (1, 2, 3, 4, 5, 6, 7) against the slide — the queue-vs-recursion contrast can be stated verbally instead.

---

## Exit Ticket (33–38 min)

**Exit ticket** — on paper or in chat before anyone leaves:

> For the tree used all session (root 1; left child 2 with children 4, 5; right child 3 with children 6, 7), write the Pre-order traversal sequence. Then, in one sentence, say which traversal you'd reach for if you just wanted to check whether the value 60 exists somewhere in a tree — and why any order would actually work for that particular task.
> **Answers:** Pre-order = `1, 2, 4, 5, 3, 6, 7`. Any traversal order works for a pure existence check, because Data Retrieval (Part 1) only needs every node visited at least once — the specific order only matters when the output's sequence itself is meaningful, or the tree has an ordering property (as future sessions on Binary Search Trees will introduce).

Scan responses on the way out. If many students can't articulate the second half, open the next session with a 2-minute recap distinguishing "traversal order matters for the output" from "traversal order doesn't matter for a plain existence check."

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Every traversal question's answer is "read the diagram left to right, top to bottom" (i.e., level-order) | Level-order matches how people naturally scan a picture | Activity 2 — naming the level-order default out loud the first time it appears, for a rule that wasn't asked for |
| In-order and Pre-order are basically the same because both "go left first" | Both orders do visit the left subtree before the right | Activity 2's explicit contrast on WHEN the root prints — immediately (Pre) vs. after the whole left subtree (In) |
| BFS/Level-order can be written with the same simple root-left-right recursion as DFS | All four traversals are taught back-to-back and look structurally similar on slides | Activity 3's row-by-row relay, which physically cannot be done branch-by-branch |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split at the Slide Block B boundary.**
- **Verify Slide 78's final post-order value live before Activity 2.** The text extraction shows "...,3,10" where the mathematically correct value is "...,3,1" (post-order always ends on the root, and the root's value is 1, not 10). This is very likely a transcription artifact, not a deck error — but confirm against the actual slide before presenting it as fact.
- **Pacing risk:** the four-traversal dry run (Activities 2-3) is where this session's real value sits — if Slide Block B's talk-through runs long, protect Activities 2-3 by cutting per their stated cut rules rather than compressing the dry run itself.
- **This closes session 02.** Session 03 (Pre-Order Traversal) goes deeper into implementing pre-order specifically — students should leave today able to state all four rules from memory, even if they can't yet write the recursive code unaided.
