# Session 15a — Insertion in Binary Search Tree (Part 1 of 2)

**Duration** 38 min · **Topic** Binary Search Tree — Insertion · **Prerequisite** Introduction to Binary Search Tree · **Session type** Concept lecture

<!-- Split note: original session-15 ran 50 min. Split at the Classroom Quiz boundary. Part 1 covers the insertion rule, both worked dry runs, and the two activities that make insertion concrete (the relay, and the deck's own broken-insertion counter-example). Part 2 (session-15b) covers complexity and the conceptual preview of Session 16's deletion cases. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Insertion in Binary Search Tree | https://docs.google.com/presentation/d/18K-En87Al628DLlClc7jwzOqCFOhA7mSaxpbETki944/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the BST insertion rule: compare with the current node, go left if the new value is smaller, right if it's greater, and insert at the first empty spot found. *(REMEMBERING)*
2. Trace the insertion algorithm to insert a new value into a given BST. *(APPLYING)*
3. Explain why inserting a value at an arbitrary position (rather than at the position the comparison rule dictates) breaks the BST property. *(ANALYZING)*

*(Iterative-vs-recursive complexity and the deletion preview are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Introduction to BST (0–6 min)

Say: *"Six on yesterday's BST basics before we touch insertion."*

**Q1.** In a BST, the right subtree of a node contains values that are…
`A` smaller than the node · `B` greater than the node · `C` equal to the node · `D` unrelated to the node
→ *Read:* B. If this misses, the rest of today collapses — insertion IS this rule, applied once.

**Q2. (True/False)** Both the left and right subtrees of a BST node must themselves be BSTs.
→ *Read:* True. This is the recursive part of the definition, not just the top-level comparison.

**Q3.** What does an in-order traversal of a BST return?
`A` Reverse sorted order · `B` Random order · `C` Strictly increasing order · `D` Level order
→ *Read:* C.

**Q4. (MSQ)** Which of these are BST properties, per yesterday's session? *(pick all that apply)*
`A` Ordering invariant holds at every node · `B` No duplicate values, by default · `C` In-order traversal gives increasing order · `D` Search is always O(1)
→ *Read:* A, B, C are correct. D is the trap — search is O(h), never O(1).

**Q5.** What is the time complexity of iterative BST search?
`A` O(1) · `B` O(log n) always · `C` O(h) · `D` O(n²)
→ *Read:* C — and only equals O(log n) when the tree happens to be balanced.

**Q6.** What is the SPACE complexity of iterative search, specifically?
`A` O(h) · `B` O(1) · `C` O(n) · `D` O(log h)
→ *Read:* B — no recursion, no call stack, just a couple of pointers.

**Q7.** For a skewed BST with `n` nodes, the height `h` is approximately…
`A` log n · `B` n · `C` 1 · `D` n/2
→ *Read:* B — every node has exactly one child, so height degenerates to the node count.

**Running it** — poll tool, ~30–40 s per question. Total 6 min.

---

## Hook (6–9 min)

Say: *"Insertion is going to feel suspiciously familiar. Here's why: inserting a value into a BST is a search for that value that's allowed to fail — except when it fails, instead of shrugging and returning 'not found,' you plant a new node exactly where the search fell off the tree."*

Draw the comparison rule again on the board: `smaller → left, larger → right`. *"Same rule as yesterday. Today it just gets one more line: 'and if there's nothing there, put it there.'"*

---

## Slide Block A (9–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide-block boundary -->
Covers: Insertion introduction and approach → Example 1 (insert 13) full dry run → Example 2 (insert 8) full dry run.

**Beats to emphasise**

- Walk **both** dry runs live, matching the deck's own comparisons exactly.
  - **Insert 13** into `{9, 4, 11, 1, 10, 14, 2, 5, 7}`: `9`→(13>9)→right to `11`→(13>11)→right to `14`→(13<14)→left child of `14` is empty→**insert 13 as left child of 14.**
  - **Insert 8** into the same tree: `9`→(8<9)→left to `2`→(8>2)→right to `5`→(8>5)→right to `7`→(8>7)→right child of `7` is empty→**insert 8 as right child of 7.**
- Say explicitly: *"Notice neither dry run ever needed to look at more than one side per step. That's the entire payoff of yesterday's property."*
- The **"return the root"** line in the approach (both iterative and recursive insertion return the tree's root at the end) is easy to skate past — flag it, because it's the detail students forget when they write insertion code and end up returning the wrong node.

**Checkpoint (at 19 min)** — cold-call:
> *"If I insert the value 6 into this same tree, which existing node does it end up under, and on which side?"*
> **Answer:** `9`→(6<9)→left to `2`→(6>2)→right to `5`→(6>5)→right to `7`→(6<7)→left child of `7` is empty → 6 becomes the **left child of 7**.

---

## ⚡ Activity 1 — Live Coding / Dry-Run Relay: Insert 8 (19–25 min)

**Format:** Dry-Run Relay · **Exposes:** whether students can run the comparison rule end-to-end without narration, and whether they remember to stop the moment they hit an empty spot rather than continuing to compare.

**Setup line (say this):**
> *"Same tree, same value the deck just used — 8. I'm covering the answer this time. Each of you gets one comparison. Say the comparison, say the direction, pass it to the next person, and tell me when to stop."*

Draw the tree: root `9`; left child `2` (children `1` and `5`, where `5`'s children are `4` and `7`); right child `11` (children `10` and `14`).

**Expected relay:** `9`→(8<9)→left to `2` →(8>2)→right to `5` →(8>5)→right to `7` →(8>7)→right child of `7` is empty → **insert 8 here, as the right child of 7.**

**How it surfaces:** If a student keeps comparing after reaching the empty spot (e.g., tries to compare 8 against "nothing"), stop: *"There's no node there. What do you do when the rule points you at empty space?"*

**Debrief line:**
> *"You just ran the identical rule from yesterday's search, with one new ending: when the walk runs out of tree, that's not failure — that's your insertion point."*

**Cut rule:** If running short, skip re-drawing the tree and reuse the one already on the board from Slide Block A.

---

## ⚡ Activity 2 — Spot the Bug: The Deck's Own Broken Insertion (25–30 min)

**Format:** Spot the Bug · **Exposes:** the belief that insertion just needs "a spot," not "the correct spot the rule dictates" — this activity is lifted directly from the deck's own worked counter-example.

**Setup line (say this):**
> *"The deck tried inserting the value 13 as the LEFT child of node 1. Before I tell you whether that's allowed — is it still a BST afterward? Defend your answer with the rule, not a gut feeling."*

**What students do:** 45 seconds, then hands up.

**Answer:** No. `13 < 1` is false — 13 is **greater** than 1, but it was placed as 1's **left** child, where the rule requires every value to be **less than** 1. The left child of a node must be smaller than that node; putting a larger value there breaks the ordering invariant on the spot, regardless of where in the tree it happens.

**Debrief line:**
> *"'Find an empty spot' was never the rule. 'Find the ONE empty spot the comparison walk leads you to' is the rule. Every other empty spot in the tree is the wrong answer, even if it's unoccupied."*

**Cut rule:** This is a 3-sentence activity if you're tight on time — state the broken insertion, take one hand, give the answer, move on. Do not cut it entirely; it is the only place this session names the failure mode directly.

---

## Classroom Quiz (30–35 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Numbered Heads Together (35–38 min)

**Why this strategy here:** Part 1's payload is one comparison rule, applied correctly. Numbered Heads forces every group to arrive at a shared answer through discussion before any one student speaks for the group — good insurance against the "confident student answers, quiet ones coast" pattern that a straight cold-call misses.

**Run it (3 minutes):**
> *"Groups of four, number yourselves 1 to 4. Question: insert the value 3 into today's tree. Discuss as a group — nobody writes until everyone agrees. When I call a number, that numbered student from a random group gives the full walk, comparison by comparison."*

Call one or two numbers, confirm the walk (`9→2→1→(3>1)→right child of 1 is empty→insert 3 as right child of 1`) against the group's answer.

> *"Everyone in that group could have given that answer — that's the point. Part 2 is shorter: complexity, then a look at what happens when we remove a value instead of adding one."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Insertion just needs "an" empty spot | "Empty" feels like the only requirement once they stop thinking about ordering | Activity 2 — the deck's own 13-under-1 counter-example |
| Insertion can change an existing node's value instead of adding a new node | "Insert" sounds similar to "update" in everyday language | Point at the pseudocode's `new Node(target)` line — insertion always creates a node, never mutates an existing one |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split at the Classroom Quiz boundary.**
- **Have the tree `{9, 4, 11, 1, 10, 14, 2, 5, 7}` already drawn** before class starts; it's reused across the Hook, Slide Block A, and both activities. Redrawing it from scratch each time is where short sessions quietly run long.
- Part 2 (session-15b) reuses this exact tree for the complexity discussion and the deletion preview — keep it on the board or photograph it if sessions span different days.
