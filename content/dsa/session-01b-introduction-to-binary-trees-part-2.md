# Session 01b — Introduction to Binary Trees (Part 2 of 2)

**Duration** 44 min · **Topic** Introduction to Binary Trees — Tree Types & Real-World Hierarchies · **Prerequisite** Session 01a — Introduction to Binary Trees, Part 1 (terminology, height conventions, parent/ancestor) · **Session type** Concept lecture

<!-- Split note: continues session-01 (original 75 min) from the Slide Block B boundary. Part 1 covered terminology + properties; this part covers the six binary tree types, real-life examples, and the original Exit Ticket. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Introduction to Binary Trees | https://docs.google.com/presentation/d/1IlPlKtEUeak8Yx-68B1NBz1kIWT2bUFXVQyEW18wqGI/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the structural rule that distinguishes each of the six binary tree types: Full, Balanced, Complete, Perfect, Degenerate, Skewed. *(UNDERSTANDING)*
2. Classify a given binary tree diagram as one of the six types (or none of them) by applying the definitions and, for Balanced trees, by computing left/right subtree height differences node by node. *(ANALYZING)*
3. Connect the hierarchical-data-structure model to real-world hierarchies (file systems, family trees) and recognise when such a hierarchy is *not* a strict binary tree. *(UNDERSTANDING)* <!-- placement: inferred from Slide 45-46 summary + Slides 41-44 -->

---

## Warm-Up Poll — Retrieval Practice on Session 01a (0–6 min)

Say: *"Six questions on last session's terminology before we build the six tree types on top of it."*

**Q1.** A node with no children is called a ___.
`A` Root · `B` Parent · `C` Leaf node · `D` Ancestor
→ *Read:* C. Every tree-type definition today assumes you already know this one cold.

**Q2.** True or false: the root of a binary tree always has exactly two children.
`A` True · `B` False
→ *Read:* False — root is a *position*, not a shape guarantee (Session 01a's Slide 9 point). This resurfaces immediately in today's Full/Complete/Perfect distinctions.

**Q3.** Which pair of terms means "one level up" vs. "every node on the path to the root"?
`A` Root / Leaf · `B` Parent / Ancestor · `C` Child / Sibling · `D` Internal / External
→ *Read:* B.

**Q4.** For the same tree, one person says height 4, another says height 3. Both can be right. Why?
`A` One of them made a mistake · `B` One counts nodes on the longest root-to-leaf path, the other counts edges · `C` Height depends on the tree's balance · `D` It's a trick question, only one is right
→ *Read:* B — this is the convention this classroom picked in Part 1; restate it once more before today's Balanced-tree work, which leans on height numbers directly.

**Q5.** At most, how many nodes can exist at level *i* of a binary tree (root = level 0)?
`A` i · `B` 2i · `C` 2^i · `D` Unlimited
→ *Read:* C.

**Q6.** True or false (recall from the Hook): a file system directory tree, where a folder can have any number of subfolders, is always a valid Binary Tree.
`A` True · `B` False
→ *Read:* False — ties directly into today's Real-Life Examples beat.

**Running it** — poll tool, ~40 s/question. Total 6 min including reads.

---

## Bridge (6–9 min)

Say: *"Last time, every question was 'what do we call this node.' Today every question is 'what do we call this whole tree' — and the honest answer is often more than one label at once, or none at all."*

Redraw (or re-project) the deck's own comparison pair for **Full** trees (Slides 20-22) without labelling which is which yet. Ask: *"Same rule you'd apply to any of today's six types — what's the ONE clause that makes Example 1 valid and Example 2 invalid?"* Take 2-3 guesses, don't confirm yet — this is the exact move Activity 2 will drill in a few minutes.

---

## Slide Block B (9–24 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide range — Slides 18-46: the six binary tree types (Full, Balanced, Complete, Perfect, Degenerate, Skewed), each with a "which one is X" comparison, plus Real-Life Examples (File Systems, Family Hierarchy) and the deck's own summary slides -->

**Beats to emphasise**

- Deliver each type as **rule, then the deck's own two-example comparison, then the deck's own stated reason the "wrong" example fails.** Don't paraphrase the reason — the deck states it precisely each time, e.g.:
  - **Full:** every node has 0 or 2 children. The non-example fails because "node 20 has 1 child" (Slide 22).
  - **Balanced:** left/right subtree heights differ by at most 1 at every node. The non-example fails because the root's subtree-depth difference is 2 (Slide 26).
  - **Complete:** every level filled except possibly the last, and the last level fills left-to-right with no gaps. The deck shows two distinct ways this fails: "the second-last level is not completely filled" (Slide 29) and "last-level nodes are not filled from left to right" (Slide 30) — these are two *different* failure modes, not the same one twice.
  - **Perfect:** every level completely filled, all leaves at the same level. Fails because "all leaf nodes are not at the same level" (Slide 34).
  - **Degenerate:** every node has exactly one child except the leaf — looks like a linked list. Fails when any node (including the root) has two children (Slide 37). <!-- placement: inferred — the deck text for which of "Example 1" / "Example 2" is the degenerate one is garbled in extraction (Slides 36-37 give conflicting order); verify against the live slide before stating which example is which. The discriminating rule itself is not in doubt. -->
  - **Skewed:** a special case of degenerate, split into left-skewed (only left children) and right-skewed (only right children) — this one isn't a "which is/isn't," both examples shown are valid, just different subtypes (Slide 39).
- On **Real-Life Examples** (Slides 41-44): call back to Part 1's Hook immediately. File systems and org-chart-style family hierarchies are trees, but only count as *binary* trees if every node is capped at two children — most real file systems aren't.
- The deck's own summary (Slides 45-46) is your closing line for this block, verbatim: *"Height of a Binary Tree is the longest path from root to leaf node. Full, Complete, Perfect, Balanced, Degenerate and Skewed trees exhibit different structural characteristics."*

**Checkpoint (at 24 min)** — show of hands:
> *"A tree has every level completely full, except the last, and the last level's nodes are pushed as far left as possible with no gaps. Complete, or Perfect?"*
> **Answer:** Complete. Perfect requires the LAST level to also be completely full — Complete only requires every level *except* the last to be full.

---

## ⚡ Activity 2 — "Which One Is It?" (24–31 min)

**Format:** Predict-the-Output (applied to classification instead of a numeric result) · **Exposes:** the Complete/Perfect/Full three-way confusion and the tendency to eyeball a tree shape instead of checking the specific rule.

**Setup line (say this):**
> *"I'm going to put up the deck's own 'which one' comparison for each of the six types, one at a time. Before I reveal the answer, vote: Example 1, Example 2, both, or neither. Then tell me the ONE-SENTENCE reason — not just the label."*

Run through, in this order, using the deck's own comparison slides: Full (Slides 20-22) → Balanced (Slides 23-26) → Complete (Slides 27-30) → Perfect (Slides 31-34) → Degenerate (Slides 35-37) → Skewed (Slide 39, both valid — the "gotcha" question).

**What students do:** Vote by show of hands per type, then one student gives the one-sentence rule before you reveal the deck's stated reason.

**How to handle wrong answers:** The single most common miss is Complete vs. Perfect — if a class calls a Complete tree "Perfect," don't just correct the label, make them re-check the specific clause that fails ("is the LAST level completely full, yes or no?"). For Skewed, the trap is expecting a "wrong" example — flag out loud that both are valid, just different subtypes, before voting so nobody wastes time hunting for a bug that isn't there.

**Debrief line:**
> *"Six types, six different single-clause rules. Every one of today's 'gotcha' answers came down to checking one specific clause, not eyeballing the overall shape. That's the skill — not memorising six pictures, memorising six one-line tests."*

**Cut rule:** If running short, do Full, Balanced, and Complete only (the three most likely to reappear in coding-round questions) and skip Perfect, Degenerate, and Skewed — state their one-line rules verbally instead of running the full vote.

---

## ⚡ Activity 3 — "Is This Balanced?" Dry-Run Relay (31–40 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** the misconception that "balanced" means "equal number of nodes on each side" rather than "height difference ≤ 1 at every node."

**Setup line (say this):**
> *"I'm giving you a tree, node by node. Starting from the leaves, going up — at every node, you tell me the height of its left subtree, the height of its right subtree, and the difference. We don't get a verdict on the whole tree until we've done this at every single node, including the root."*

Use the deck's own fully-worked example (Slides 51-57): a tree built from values 5, 15, 8, 12, 20, 10, 3, 4, 7. Go bottom-up exactly as the deck does, computing the height-difference at each node, ending at the root with left subtree height 3, right subtree height 2, difference |3−2| = 1 → **Balanced**.

Then contrast immediately with the deck's second worked tree (values 5, 15, 7, 10, 3, 4): left subtree height 3, right subtree height 0, difference |3−0| = 2 → **Not Balanced**.

**What students do:** Go around the room, one node per student, calling out that node's left-height/right-height/difference before you reveal the deck's own number for that node. Keep a running tally on the board exactly like the deck's slide build-up.

**How to handle wrong answers:** If a student answers based on counting total nodes on each side rather than height, stop and redo that one node together — this is the exact misconception the activity targets, don't let it slide past to preserve pace.

**Debrief line:**
> *"Balanced never means equal head-count on both sides. It means the taller side is never more than one level taller than the shorter side — and you only find that out by checking height at every single node, not just eyeballing the root."*

**Cut rule:** If running short, do only the first tree (the Balanced one, Slides 51-54) live as a full relay, then simply show the second tree's (Not Balanced) final numbers from Slide 57 as a fast contrast rather than re-running the relay.

---

## Exit Ticket (40–44 min)

**Exit ticket** — on paper or in chat before anyone leaves:

> Draw or describe a tree with exactly 3 nodes that is a Full Binary Tree AND a Perfect Binary Tree AND a Balanced Binary Tree, all at once. Then write one sentence: is it possible for a tree to be Complete but not Full? Why or why not?
> **Answers:** A root with exactly two children (0 or 2 children at every node = Full; both levels completely filled = Perfect; height difference 0 = Balanced) satisfies all three at 3 nodes. Yes, Complete-but-not-Full is possible — e.g. a root with a left child only and no right child is Complete (last level filled left-to-right with no gaps) but not Full (that node has exactly 1 child).

Scan responses on the way out. Confusion on the second half of the ticket is the signal to open Session 02 with a 2-minute recap of Complete vs. Full before moving into traversals.

This closes the two-part Session 01. Next session (02) builds directly on today's "at most two children, called left and right" rule to define traversal order.

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Complete, Perfect, and Full binary trees are basically the same thing | The names all describe "a tree that's nicely filled in" and the shapes look similar at a glance | Activity 2's one-sentence-rule requirement — forcing the specific clause, not the label, to be spoken aloud |
| "Balanced" means equal number of nodes on the left and right | The everyday meaning of "balanced" is about equal weight/count | Activity 3's node-by-node height relay, which never once counts total nodes |
| Any hierarchy diagram (file systems, org charts) is automatically a "binary" tree | Both are commonly drawn as branching diagrams and casually called "trees" | Slide Block B's Real-Life Examples beat, reinforced by the Part 1 Hook |

---

## Instructor Notes

- **This is Part 2 of a 75-minute original session, split at the Slide Block B boundary.** If a student missed Part 1, they're missing the height-convention and parent/ancestor foundation this whole session assumes — don't re-teach it here, point them to session-01a.
- **The deck has a second, denser pass of worked material starting around Slide 47** (an extra Perfect-tree comparison, the full Balanced-tree height-difference walkthroughs, and a full terminology recap on a fresh 1-8 tree). This lesson plan redistributes that material into Activities 2-3 rather than delivering it as additional slides verbatim — showing all of Slides 47-74 as more lecture content on top of Slides 18-46 would roughly double this part with substantial repetition. <!-- placement: inferred restructuring — confirm this matches how the deck is actually meant to be delivered before running it cold. -->
- **Verify the Degenerate-tree "which example is which" against the live slide** (Slides 36-37) before Activity 2 — the raw text extraction gives a genuinely ambiguous/conflicting order for Example 1 vs. Example 2, even though the discriminating rule itself (any node with two children breaks degeneracy) is unambiguous.
- **If your slot is hard-capped below 44 min, cut Activity 3 first** (move the Balanced-tree dry-run to a follow-up or homework walkthrough) before cutting any of the six type definitions in Slide Block B — the six-type distinction is the content most likely to reappear across the rest of the course and in coding-round questions.
