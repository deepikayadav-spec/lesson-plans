# Session 16a — Deletion in Binary Search Tree (Part 1 of 2)

**Duration** 39 min · **Topic** Binary Search Tree — Deletion: The Three Cases · **Prerequisite** Insertion in Binary Search Tree · **Session type** Concept lecture

<!-- Split note: original session-16 ran 50 min. Split at the Classroom Quiz boundary. Part 1 covers all three deletion cases (leaf, one child, two children) with full dry runs and the case-identification relay. Part 2 (session-16b) covers the recursive/iterative implementations, the complexity decomposition, and the successor-loop activity. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Deletion in Binary Search Tree | https://docs.google.com/presentation/d/1eIV4xw5ICsy5DwJWymzGtJw-VSEk4bb6Rg400LDMBG0/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the three deletion cases in a BST — leaf, one child, two children — and the replacement rule for each. *(REMEMBERING)*
2. Trace deletion of a leaf node, a one-child node, and a two-children node on a given BST. *(APPLYING)*
3. Explain why a two-children deletion replaces the node's value with its in-order successor (or predecessor) rather than simply relinking its children. *(UNDERSTANDING)*

*(The recursive/iterative implementations and the full complexity decomposition are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Insertion in BST (0–6 min)

Say: *"Six on yesterday's insertion before we do the opposite operation."*

**Q1.** BST insertion rule: go left if the value is ___, go right if it's ___.
`A` smaller / greater · `B` greater / smaller · `C` equal / unequal · `D` odd / even
→ *Read:* A.

**Q2. (True/False)** Iterative and recursive insertion use the same amount of auxiliary space.
→ *Read:* False. Iterative is O(1); recursive is O(h) because of the call stack. This was last session's #1 mix-up — if it's still shaky, restate it now before deletion adds a second layer of recursion reasoning.

**Q3.** In yesterday's "broken insertion" example, the deck placed value 13 as the left child of node 1. Why was that wrong?
`A` 13 is too large to exist in the tree · `B` 13 > 1, but a left child must be smaller than its parent · `C` Node 1 already had a left child · `D` Nothing was wrong
→ *Read:* B.

**Q4. (MSQ)** Which deletion cases were previewed at the end of last session? *(pick all that apply)*
`A` Leaf node · `B` Node with one child · `C` Node with two children · `D` Deleting the entire tree
→ *Read:* A, B, C.

**Q5.** In the two-children preview example, node 11 (children 10 and 14) was replaced by which value?
`A` 10 · `B` 14 · `C` 9 · `D` The node was removed with nothing put in its place
→ *Read:* B — the deck used the in-order successor.

**Q6.** What is the time complexity of BST insertion, iterative or recursive, in terms of height `h`?
`A` O(1) · `B` O(log n) always · `C` O(h) · `D` O(n)
→ *Read:* C.

**Q7.** For a skewed BST, `h` is approximately…
`A` log n · `B` n · `C` constant · `D` n/2
→ *Read:* B.

**Running it** — poll tool, ~30–40 s per question. Total 6 min.

---

## Hook (6–9 min)

Say: *"Yesterday's whole session was: find the empty spot, plant a node. Today is the opposite problem — you have to remove a node WITHOUT leaving a hole in the tree's shape. The entire session is really just one question, asked three different ways depending on how many children the node you're deleting has: what do you put in the hole?"*

---

## Slide Block A (9–24 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide-block boundary -->
Covers: Deletion approach overview → Case 1: deleting a leaf (delete 7, full dry run) → Case 2: deleting a node with one child (delete 5, full dry run) → Case 3: deleting a node with two children (delete 11, full dry run).

**Beats to emphasise**

- Open with the three-case decision tree from the approach slide: *"Find the node the same way you'd search for it. Then look at how many children it has — that decides everything that happens next."*
- Walk **all three dry runs live**, on the shared tree `{9, 4, 11, 1, 10, 14, 2, 5, 7}` (root 9; left child 2 with children 1 and 5; 5's children 4 and 7; right child 11 with children 10 and 14):
  - **Delete 7 (leaf):** search `9→2→5→7` (comparing 7 against each), found, no children → **remove it outright, nothing to reattach.**
  - **Delete 5 (one child):** search `9→2→5`, found, only child remaining is `4` → **5 is removed and 4 takes its place** as the child of node 2.
  - **Delete 11 (two children):** search `9→11`, found, children are `10` and `14` → **11's value is replaced by 14** (its in-order successor — the smallest value in 11's right subtree), and the old node holding 14 is removed instead.
- Land the general rule explicitly after all three: *"Every deletion is a search, followed by exactly one of three cleanup moves. The first two moves are just pointer surgery. The third move is the only one that needs a NEW value from somewhere else in the tree."*

**Checkpoint (at 24 min)** — cold-call two students:
> *"Why can't you just delete node 11 and reattach both 10 and 14 as children of node 9 directly?"*
> **Answer:** Node 9 can only have one right child. You'd also lose the ordering between 10 and 14 relative to whatever else sits under them — replacing 11's *value* with a value that's already correctly ordered (the successor) is the only way to keep the rest of the subtree intact without re-inserting everything.

---

## ⚡ Activity 1 — Live Coding / Dry-Run Relay: Three Deletions, Three Students (24–31 min)

**Format:** Dry-Run Relay · **Exposes:** whether students can identify which of the three cases applies BEFORE they try to fix anything, and whether they instinctively reach for "just remove it" without asking what has to be reattached.

**Setup line (say this):**
> *"Same tree as the slides. I'm assigning each of you one of the three deletions — leaf, one child, two children. Walk me through it exactly like a search: compare, move, and when you find the target, tell me what happens to the pointers around it."*

Reuse the tree from Slide Block A. Assign:
- **Student A:** delete 7 (leaf)
- **Student B:** delete 5 (one child, only child remaining is 4)
- **Student C:** delete 11 (two children, 10 and 14)

**How it surfaces:** If a student says "just remove it" without stating what replaces it, push: *"Remove it, and then what's sitting in the hole? Nothing? A child? A borrowed value?"* For Student C specifically, if they try to promote both 10 and 14 at once, stop: *"A node can't have two right children. Pick ONE value that keeps everything sorted — where does it come from?"*

**Debrief line:**
> *"Every deletion is secretly still a search, then one of exactly three cleanup moves. Leaf: nothing to reattach. One child: promote it. Two children: borrow the successor's value, then go delete THAT node instead — which is now guaranteed to be a leaf or one-child case."*

**Cut rule:** If running short, run Student A and Student C only — the leaf case and the two-children case bracket the whole idea; the one-child case is the easiest to describe verbally without a full relay.

---

## Classroom Quiz (31–36 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Rank the Difficulty (36–39 min)

**Why this strategy here:** all three cases have now been demonstrated once (Slide Block A) and executed once (Activity 1). Ranking them by difficulty, with a justification, forces students to articulate *why* the two-children case is different — which is exactly what Part 2's complexity discussion (two sequential searches, not one) depends on them already sensing.

**Run it (3 minutes):**
> *"With your neighbor: rank the three deletion cases, easiest to hardest, and agree on ONE sentence for why the hardest one earns that spot. I'll take two pairs' rankings, out loud."*

Take 2 pairs. Almost every group will rank two-children hardest — press the reason: *"hardest because...?"* Listen for "it needs a value from somewhere else" as the target answer.

> *"Hold that reason. Part 2 shows you the exact one-line loop that finds that borrowed value, and proves that even though it's a second search, the whole operation stays O(h), not O(h²)."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Deleting a two-children node just removes it and reattaches both children arbitrarily | Leaf and one-child deletion feel like "just disconnect it" | Activity 1, Student C — forcing the "a node can only have one right child" contradiction |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split at the Classroom Quiz boundary.**
- **The exact resulting tree shape after the two-children deletion (delete 11) is drawn on the original slides but not fully recoverable from extracted text** — teach the *values* (11 replaced by 14) with confidence, since that's stated explicitly, but don't over-commit to describing the exact final left/right child arrangement beyond what's given here. <!-- placement: inferred — source slide diagrams for the post-deletion tree shape are ambiguous in text extraction -->
- Part 2 (session-16b) reuses this exact tree and these exact three deletions for the pseudocode walkthrough — keep the board drawing if possible.
