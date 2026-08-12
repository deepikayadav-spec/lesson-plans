# Session 01a — Introduction to Binary Trees (Part 1 of 2)

**Duration** 40 min · **Topic** Introduction to Binary Trees — Terminology & Properties · **Prerequisite** Arrays & recursion basics (assumed, not verified against this deck) <!-- placement: inferred --> · **Session type** Concept lecture

<!-- Split note: original session-01 ran 75 min (2 slide blocks, 3 activities). Split at the Classroom Quiz boundary — the natural pause the deck itself already treats as a checkpoint. Part 1 covers terminology + properties (Slide Block A) through the diagnostic Activity 1. Part 2 (session-01b) covers the six tree types + real-life examples (Slide Block B) through Activities 2-3 and the original Exit Ticket. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Introduction to Binary Trees | https://docs.google.com/presentation/d/1IlPlKtEUeak8Yx-68B1NBz1kIWT2bUFXVQyEW18wqGI/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define a binary tree and its core terminology — node, parent, root, child, leaf node, internal node, subtree, height, ancestor. *(REMEMBERING)*
2. Explain the two conventions for measuring height (counting nodes on the longest root-to-leaf path vs. counting edges) and state which one a given problem is using. *(UNDERSTANDING)*
3. Correctly distinguish "parent" (one level up) from "ancestor" (every node on the path to the root, self included) on a labelled tree. *(ANALYZING)*

*(Objectives 3–5 of the original session — classifying tree types and connecting to real-world hierarchies — are covered in Part 2.)*

---

## Warm-Up Poll — Diagnostic (0–7 min)

> **This is the true first session of the entire DSA course.** There is no previous session to recall, so the poll is a *diagnostic*, not retrieval practice. No wrong answers. Purpose is to calibrate pace and to establish, on minute one, that this classroom expects everyone to answer.

Say: *"Seven quick questions before we touch a single tree diagram. Nobody is graded, nobody is named. I need to know who I'm teaching."*

**Q1.** Have you studied any data structure before (arrays, linked lists, stacks, queues)?
`A` Never heard the term · `B` Heard of arrays only · `C` A few, in theory · `D` Yes, comfortably, including some coding
→ *Read:* If A+B > 60%, slow down on "hierarchical data structure" in Slide Block A — don't assume they have a mental model of "structure" beyond arrays.

**Q2.** Are you comfortable with recursion (a function that calls itself)?
`A` Never heard of it · `B` Heard of it, don't fully get it · `C` Can trace through simple examples · `D` Yes, comfortably
→ *Read:* This isn't tested today, but it's the backbone of every traversal in Session 02. If C+D < 40%, flag it now — you may need a 2-minute recursion refresher before Session 02's warm-up.

**Q3.** When you hear the word "tree" in a computing context, what comes to mind first?
`A` A plant / nature · `B` A family tree · `C` A folder/file structure on my computer · `D` No idea
→ *Read:* B and C are both good instincts — the Real-Life Examples block in Part 2 validates whichever one they picked. Don't correct A yet; let the Hook do it.

**Q4.** Guess: in a "binary" tree, how many children can one node have, at most?
`A` 1 · `B` 2 · `C` Unlimited · `D` Not sure
→ *Read:* B is where the whole session lands. If most pick C, that's your hook — the file-system example is about to look very "unlimited," and today's whole point is the strict 2-child rule.

**Q5.** True or false (guess): every hierarchy you can draw as a tree is automatically a "binary" tree.
`A` True · `B` False · `C` Not sure
→ *Read:* Note the split. You'll revisit this exact question in the Hook and again in Part 2's real-life-examples beat.

**Q6.** Which of these do you most want out of this course? *(MSQ — pick up to 2)*
`A` A job / placement · `B` Build my own projects · `C` Clear college coursework · `D` Curiosity

**Q7.** How do you prefer to learn a new structure like this?
`A` Watch a diagram first, then try · `B` Try labelling it myself first, ask later · `C` Read the definition first · `D` Work with a partner
→ *Read:* If B+D is high, lean harder on the activities and shorten your talk-through of definitions.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Never name individuals. Total 7 min including your reads.

---

## Hook (7–12 min)

Put both of these on the board side by side, nothing else:

**Diagram A** — a file system tree (from the deck): `Root directory of C Drive` branching into `Documents and Settings`, `Program files`, `Desktop`, `Favorites`, `Adobe`, `Microsoft office` — six children hanging off one root.

**Diagram B** — the deck's own binary tree definition diagram (Slide 4): every node has *at most two* children, left and right.

Ask: *"Both of these are 'trees' — hierarchies with a root and branches. Which one is a valid Binary Tree, by definition?"*

Let the disagreement happen (tie back to **Q5** of the poll — some said "false," some said "true"). Then: *"Diagram A is a tree. It is not a binary tree — that root has six children, and a binary tree allows at most two. Every rule in the next 40 minutes comes from that one restriction: at most two children, called left and right. That's the whole deal today."*

---

## Slide Block A (12–27 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide range — Slides 4-17: Introduction, the 9 Key Terminologies (Node, Parent, Root, Child, Leaf Node, Internal Node, Subtree, Height, Ancestors), and Properties of Binary Trees -->

**Beats to emphasise**

- **Node = value + two pointers.** Say it exactly like that, every time a new term is introduced — it's the one sentence that makes every later term (parent, child, leaf) fall out logically instead of needing separate memorisation.
- **Root has no parent — it's a position, not a shape guarantee.** Students will later try to assume the root always has two children; kill that assumption now (Slide 9).
- **Parent vs. Ancestor is the sharpest distinction in this block.** Parent = one level up, direct. Ancestor = *every* node on the path from root down to this one, excluding the node itself (Slide 15). Say both definitions back-to-back, on the same diagram, so the contrast is visible in one glance.
- **Height has two competing conventions and the deck flags this itself** (Slide 14 NOTE): count *nodes* along the longest root-to-leaf path, or count *edges*. Don't gloss over this — pick one convention explicitly for this classroom's exams/coding practice and say which one out loud, because it changes every height-based answer by exactly 1.
- **Properties/formulas** (Slides 16-17): at most 2 children per node; at most 2^i nodes at level *i* (root = level 0); a tree of height *h* has at most 2^(h+1) − 1 nodes <!-- placement: inferred — the exponent characters were lost in the deck-text extraction on Slide 17; verify the exact exponent against the live slide before writing it on the board -->; minimum possible height for *n* nodes is ⌈log₂(n+1)⌉. Don't derive these — state them, show one worked plug-in each, move on.

**Checkpoint (at 27 min)** — cold-call two students:
> *"Node 8 in a tree is the parent of node 15, and node 2 is the parent of node 8. Is node 2 a parent of node 15, an ancestor of node 15, or both?"*
> **Answer:** Ancestor, not parent — node 2 is two levels above node 15, and "parent" only ever means the one node directly above.

---

## ⚡ Activity 1 — Predict-the-Label (27–34 min)

**Format:** Predict-the-Output (adapted: students predict a terminology *label*, not a numeric output) · **Exposes:** Parent-vs-Ancestor confusion, Leaf-vs-Internal confusion, and the "root has no parent" special case — the three traps set up in Slide Block A.

**Setup line (say this):**
> *"Fresh tree, nodes numbered 1 through 8, same as the recap diagrams later in this deck. I'll ask one term at a time. Everyone commits an answer — thumbs to the term's letter — before I reveal."*

Use the deck's own recap facts, which are stated outright rather than requiring you to reverse-engineer the diagram's exact edges <!-- placement: inferred — the recap tree's full edge layout is not recoverable from the text extraction alone; run the questions below only, in the order shown on the live slides, rather than inventing extra node relationships -->:

1. *"Node 8 is the child of node 7. True or false — is node 8 also an ancestor of node 7?"* → **False.** It's the reverse: node 7 is an ancestor of node 8. (Slide 63)
2. *"The root of this tree — does it have a parent? Yes or no?"* → **No, never.** (Slides 64-65)
3. *"The ancestors of node 4 are which nodes?"* → **Nodes 1 and 2** — every node on the path from root to node 4, excluding node 4 itself. (Slide 72)
4. *"This tree has 4 levels. Using the 'count nodes on the path' convention, what's its height? Using the 'count edges' convention?"* → **4** (nodes) or **3** (edges) — both are "correct," which is exactly the point. (Slides 70-71 give both values for the same tree.)

**What students do:** Thumbs-vote per question, then one cold-call to justify the answer in a full sentence before you confirm.

**How to handle wrong answers:** If students flip parent/ancestor on Q1, redraw the one-sentence rule from the checkpoint ("ancestor = everyone above, parent = one step above") right on top of this tree. If Q4 produces only one answer confidently, that's a red flag — it means the ambiguity didn't land in Slide Block A; restate which convention *this classroom* uses and move on.

**Debrief line:**
> *"Every one of these came straight from a definition you just heard — no trick questions. If you hesitated, it's because two of these terms sound alike. They aren't the same. Parent is one step. Ancestor is every step."*

**Cut rule:** If running short, drop Q1 and Q4, keep Q2 and Q3 — they carry the two ideas (root has no parent; ancestor ≠ node itself) most likely to resurface in Session 02+.

---

## Classroom Quiz (34–39 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Think-Pair-Share (39–40 min)

**Why this strategy here:** the whole of Part 1 is definitions and a genuinely confusable pair (parent/ancestor). Think-Pair-Share forces every student to *produce* the definitions in their own words before Part 2 builds tree-type classification on top of them — silent listening doesn't surface who's still shaky.

**Run it (60 seconds):**
> *"Turn to the person next to you. One of you says the definition of 'ancestor' out loud, in your own words, no notes. The other checks it against 'every node on the path to the root, excluding this node.' Swap: now do 'height,' both conventions. Go."*

Walk the room for 30 seconds while pairs talk. Cold-call one pair to report back what they disagreed on, if anything — public disagreement here is useful, not embarrassing, because it previews exactly the kind of ambiguity Part 2 will lean on (Complete vs. Perfect).

> *"Hold onto that discomfort. Next session it comes back — six tree types, and most of the confusion is the same shape: two definitions that sound alike but aren't."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| "Height" has one fixed numeric value for any given tree | Most other measurements in maths are unambiguous | Showing Slides 70-71's own two different height values (4 vs. 3) for the identical tree, and stating which convention this classroom uses |
| Ancestor and Parent mean the same thing | Both describe "someone above me in the hierarchy" | Running Activity 1's Q1/Q3 back-to-back on the same diagram, then Think-Pair-Share |
| Any hierarchy diagram (file systems, org charts) is automatically a "binary" tree | Both are commonly drawn as branching diagrams and casually called "trees" | The Hook's file-system vs. binary-tree-definition side-by-side |

---

## Instructor Notes

- **This is Part 1 of a 75-minute original session, split at the Classroom Quiz boundary.** Part 2 (session-01b) picks up with the six binary tree types and real-life examples — don't preview tree-type content here, it dilutes today's terminology focus.
- **Resolve the height convention (nodes vs. edges) explicitly and write it on the board for the rest of the course.** This is a real, deck-acknowledged ambiguity (Slide 14's own NOTE), not an instructor error — but if you don't pick one, students will carry two silently-conflicting definitions into every future height/depth problem.
- **Verify the exact exponent in the "2^(h+1) − 1 nodes" formula** (Slide 17) against the live slide before writing it on the board — the superscript character did not survive the text extraction cleanly.
- **Have the two Hook diagrams already drawn or printed before the session starts.** Building the file-system tree live on the board burns time you don't have.
