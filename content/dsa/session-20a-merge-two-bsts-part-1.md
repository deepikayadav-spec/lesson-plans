# Session 20a — Merge Two BSTs (Part 1 of 2)

**Duration** 40 min · **Topic** Binary Search Tree — Merge: Approach & Dry Run · **Prerequisite** Predecessor and Successor in BST · **Session type** Concept lecture

<!-- Split note: original session-20 ran 50 min. Split at the Classroom Quiz boundary. Part 1 covers the problem statement, the two-stack approach, and the full dry run — the longest, most step-dense walkthrough in the BST topic. Part 2 (session-20b) covers pseudocode, complexity, and the closing real-world callout. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Merge Two BSTs | https://docs.google.com/presentation/d/1cHTFivGiZX_ws3OimObzkzH5v_rUK3yctx0xxamYLwI/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the problem: given two BSTs, return a single array containing every element from both, in sorted order. *(REMEMBERING)*
2. Explain why the merge technique pushes each root's left spine onto a stack first, and why that mirrors the first steps of an iterative in-order traversal. *(UNDERSTANDING)*
3. Trace the merge dry run: repeatedly comparing the two stacks' top values, popping the smaller, and — if the popped node has a right child — pushing that child's own left spine onto the same stack. *(APPLYING)*

*(Pseudocode, complexity, and the merge-sort analogy are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Predecessor and Successor in BST (0–6 min)

Say: *"Six on yesterday's predecessor/successor before today's problem, which reuses the same pointer-walk instinct on two trees at once."*

**Q1.** The predecessor of a node is defined as…
`A` Its parent · `B` The node immediately before it in an in-order traversal · `C` Its left child · `D` The smallest value in the tree
→ *Read:* B.

**Q2.** In the optimal predecessor walk, what happens when `current->data < target`?
`A` Record it as a candidate and move right · `B` Record it as a candidate and move left · `C` Discard it and move right · `D` Stop immediately
→ *Read:* A.

**Q3. (True/False)** The successor walk's rule is the exact mirror of the predecessor walk's rule.
→ *Read:* True — move left/record on `current > target` instead of right/record on `current < target`.

**Q4.** What is the space complexity of the optimal predecessor/successor approach?
`A` O(N) · `B` O(H) · `C` O(1) · `D` O(N log N)
→ *Read:* C — just a couple of pointers, no array, no recursion stack (it's an iterative walk).

**Q5.** In the brute-force predecessor/successor approach, what is the sorted array built from?
`A` A pre-order traversal · `B` An in-order traversal · `C` A post-order traversal · `D` The tree's raw node order
→ *Read:* B.

**Q6.** If a target is the FIRST value in the in-order sequence, its predecessor is…
`A` The root · `B` NULL · `C` Itself · `D` The largest value in the tree
→ *Read:* B.

**Running it** — poll tool, ~30–40 s per question. Total 6 min.

---

## Hook (6–9 min)

Say: *"Two sorted piles of cards, and you need one sorted pile. You don't shuffle everything together and re-sort from scratch — you look at the two top cards, take the smaller one, and repeat. That's the merge step from merge sort. Today's problem is exactly that, except your 'top card' isn't the front of an array. It's whatever a stack of tree pointers says is the smallest value not yet used, from each of two BSTs."*

---

## Slide Block A (9–24 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide-block boundary -->
Covers: Problem statement + both worked examples → Approach (push each root's left spine onto its own stack; repeatedly compare tops, pop the smaller, push the popped node's right child's left spine onto that same stack) → full dry run of Example 1.

**Beats to emphasise**

- State the approach in the deck's own three steps: *"(1) Push every root's left descendants onto its own stack. (2) Compare the two stacks' top values; pop whichever is smaller into the result. (3) If what you popped has a right child, push THAT child's left descendants onto the same stack, then repeat from step 2 until both stacks are empty."*
- Connect step (1) explicitly to prior sessions: *"Pushing a node then all its left children, one at a time, is literally how you'd START an iterative in-order traversal. Each stack, on its own, is just doing an in-order traversal of its own tree — one step at a time, on demand."*
- Walk the dry run at a **representative pace**, not every single slide: show the initial stacks being loaded (stack 1 from BST 1's root, stack 2 from BST 2's root, each following its left spine down), then walk 6–8 compare-pop-push cycles live exactly as the deck sequences them, then jump to the final merged result and confirm it matches the deck's stated output.
- Flag the one detail that's easy to skip: **you push the popped node's RIGHT child's left spine — not just the right child itself.** This is the exact rule Activity 1 tests.

**Checkpoint (at 24 min)** — cold-call:
> *"If the value you just popped has NO right child, what happens to that stack on the next comparison?"*
> **Answer:** Nothing gets pushed — the stack's next top is simply whatever was already sitting underneath the popped value (an ancestor from earlier in that same left-spine push).

---

## ⚡ Activity 1 — Live Coding / Dry-Run Relay: Compare, Pop, Push (24–32 min)

**Format:** Dry-Run Relay · **Exposes:** whether students remember to push the popped node's right-subtree left-spine (not just note the right child and move on), which is the step almost everyone forgets on a first pass.

**Setup line (say this):**
> *"I'm going to read out comparisons exactly the way the deck's dry run does them, one at a time. Before I tell you which stack wins, YOU tell me: which value pops, and — this is the part people skip — does anything new get pushed as a result?"*

Reuse the deck's own sequence from Example 1 (BST 1 rooted at 10 with left-spine values including 5, 2, 1; BST 2 rooted at 12 with left-spine values including 6, 4). Read out the comparisons in the deck's own order: *"1 vs. 4 → 1 is smaller, pop 1. 2 vs. 4 → 2 is smaller, pop 2, and 2 has a right child (3), so push 3's left spine. 3 vs. 4 → 3 is smaller, pop 3. 5 vs. 4 → 4 is smaller, pop 4. 5 vs. 6 → 5 is smaller, pop 5, and 5 has a right child (7), so push 7's left spine."* Continue through as many comparisons as time allows, tracking the growing result array `1, 2, 3, 4, 5, 6, 7, 8, 9, 10, ...` against the deck's own running list.

**How it surfaces:** If a student pops a value but doesn't mention pushing its right subtree's left spine (when it has one), stop: *"You can't just walk away from that pop. If what you popped had a right child, that child's whole left spine has to go on the stack now, or you'll silently skip every value in between."*

**Debrief line:**
> *"Every single pop is one step of an in-order traversal on ONE of the two trees. The merge never builds two separate sorted lists first — it runs both in-order traversals AND the sorted merge in the exact same pass."*

**Cut rule:** Stop after 6–8 comparisons instead of tracing the full ~18-step dry run; state the deck's final merged array directly rather than tracing every remaining step.

---

## Classroom Quiz (32–37 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Human Stacks (37–40 min)

**Why this strategy here:** the two-stack mechanic is genuinely physical — two piles, compare-the-tops, pop-the-smaller. Acting it out with bodies rather than a board diagram gives students a kinesthetic anchor for "push the popped node's right-subtree left spine," the exact detail Activity 1 showed is easy to skip.

**Run it (3 minutes):**
> *"Two lines of four volunteers, standing front-to-back — that's your two stacks, front of the line is the top. Line 1 holds cards 1, 2, 3, 5 (front to back). Line 2 holds cards 4, 6, 7, 9. Rest of the class calls out: which front card is smaller? That person steps out and sits — that's the pop. If I say their card had a right child, one more volunteer joins the FRONT of that same line — that's the push."*

Run 3-4 rounds fast. Don't aim to finish the full sequence — the point is the physical pop/compare/push rhythm, not completeness.

> *"That's the entire algorithm, standing up. Part 2 turns it into six lines of pseudocode and proves the space cost is nowhere near as big as the number of cards on the field."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| You need to build both trees' full sorted arrays first, then merge them | Feels like the "obvious" two-step version of the problem | Naming that each stack only ever holds one root-to-current path — the whole point is avoiding two full sorted arrays |
| Popping a node and pushing just its right CHILD (not the right child's left spine) is enough | "Push the right child" sounds complete on first read of the approach | Activity 1 — the exact moment most relay attempts silently skip values |
| You alternate popping from stack 1 and stack 2 in a fixed order | Feels natural to "take turns" between the two trees | Re-reading the comparison rule — you always compare BOTH tops and pop the smaller, regardless of which stack it came from |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split at the Classroom Quiz boundary.**
- **Pacing risk:** the full dry run is the longest in the whole BST topic — resist the urge to trace every single comparison live. Six to eight comparisons, done carefully with the class following along, teaches the pattern; the remaining dozen are repetition of the same rule.
- **Exact stack contents at each step are reconstructed from the dry-run narration text**, not from directly legible stack diagrams in the raw slide extraction — cross-check against the live deck before presenting specific intermediate stack states as fact. The final merged output and the overall comparison SEQUENCE (which value pops when) are stated unambiguously in the deck and can be presented with full confidence. <!-- placement: inferred -->
