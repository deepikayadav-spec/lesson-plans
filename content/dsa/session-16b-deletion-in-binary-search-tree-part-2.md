# Session 16b — Deletion in Binary Search Tree (Part 2 of 2)

**Duration** 21 min · **Topic** Binary Search Tree — Deletion: Implementation & Complexity · **Prerequisite** Session 16a — Deletion in Binary Search Tree, Part 1 (three deletion cases, dry runs) · **Session type** Concept lecture

<!-- Split note: continues session-16 (original 50 min) from the Slide Block B boundary. This part covers the recursive and iterative implementations, the complexity decomposition (why two O(h) searches don't multiply), and the successor-loop activity. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Deletion in Binary Search Tree | https://docs.google.com/presentation/d/1eIV4xw5ICsy5DwJWymzGtJw-VSEk4bb6Rg400LDMBG0/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Justify why deletion's overall time complexity remains O(h) even in the two-children case, by decomposing it into a search phase and an adjustment phase. *(ANALYZING)*
2. Compare the recursive (call-stack-based) and iterative (parent-pointer-based) deletion implementations. *(UNDERSTANDING)* <!-- placement: inferred — phrasing built from the deck's two full implementations, slides 36–41 and 47–60 -->

---

## Warm-Up Poll — Retrieval Practice on Session 16a (0–5 min)

Say: *"Four quick ones on the three cases before we look at how they're actually coded."*

**Q1.** In a leaf deletion, what replaces the removed node?
`A` Its parent · `B` Nothing — it's just removed · `C` A borrowed successor value · `D` Its sibling
→ *Read:* B.

**Q2.** In a one-child deletion, what replaces the removed node?
`A` Nothing · `B` Its single remaining child, promoted into its place · `C` A borrowed successor value · `D` The root
→ *Read:* B.

**Q3.** In a two-children deletion, what replaces the removed node's value?
`A` Its parent's value · `B` A borrowed value from elsewhere in the tree (successor or predecessor) · `C` The average of its two children · `D` Nothing — you can't delete such a node
→ *Read:* B.

**Q4.** In Part 1's ranking exercise, which case did most pairs call hardest, and why?
→ *Read:* Open response — reconnects to the reason ("needs a value from somewhere else") that Part 2 is about to formalize into a loop.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"You can identify and reason through all three cases. Now: the actual loop that finds the successor, and the proof that a second search doesn't double your complexity class."*

---

## Slide Block B (7–16 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide-block boundary -->
Covers: Recursive pseudocode/code for deletion → complexity analysis (search phase O(h) + adjustment phase O(1) for 0/1-child or O(h) for 2-children, overall O(h)) → the iterative approach with explicit parent-pointer tracking.

**Beats to emphasise**

- Walk the recursive pseudocode's two-children branch specifically: `cur = root->right; while (cur->left) cur = cur->left;` — this loop IS "find the in-order successor," expressed as "go right once, then keep going left." Connect it back to Part 1's delete-11 example: 11's right child is 14, which has no left child, so the loop stops immediately and returns 14.
- On complexity, walk the decomposition explicitly: *"Total time = search to find the node (O(h)) + cleanup. For 0 or 1 child, cleanup is O(1) pointer surgery, so total is O(h) + O(1) = O(h). For 2 children, cleanup means ANOTHER search — for the successor — which costs O(h) in the worst case, so total is O(h) + O(h), which is still just O(h)."* The "two O(h)'s add up to O(h), not O(h²)" point is the one that trips students.
- The iterative approach (parent-pointer tracking) is denser — it maintains `parent` and `current` explicitly because, without recursion, there's no call stack remembering "how did I get here." Frame it as: *"Recursion gets the parent reference for free, on the stack. Iteration has to track it by hand."*

**Checkpoint (at 16 min)** — show hands:
> *"Two O(h) searches happen during a two-children deletion — finding the node, then finding its successor. Who thinks that makes the total O(h²)? Who thinks it's still O(h)?"*
> **Answer:** Still O(h). The successor search only ever walks down 11's *right subtree*, which is itself bounded by the tree's height — the two searches are sequential, not nested, so their costs **add**, not multiply: O(h) + O(h) = O(h).

---

## ⚡ Activity 2 — Predict the Output: The Successor-Finding Loop (16–19 min)

**Format:** Predict-the-Output · **Exposes:** whether students actually trust the `while (cur->left) cur = cur->left` loop to find the successor, or are still trying to compute it by inspecting the whole subtree.

**Setup line (say this):**
> *"One loop: start at the deleted node's right child, keep going left until you can't. Whatever you land on is the successor. I'll give you two versions of the same tree — predict what the loop returns before I confirm."*

- **Version 1 (from the deck):** node 11's right child is `14`, and `14` has no left child. → **Predicted successor: 14** (loop stops immediately).
- **Version 2 (a one-step extension of the same rule):** suppose `14` *did* have a left child, `12`. → **Predicted successor: 12** (loop now takes one more step left before stopping). <!-- placement: inferred — a minimal hypothetical extension of the deck's own tree, used only to test the loop's general behaviour, not new algorithm content -->

**How it surfaces:** If students predict `14` for Version 2 as well, push: *"The loop says keep going left WHILE there's a left child. Does 14 have one now?"*

**Debrief line:**
> *"The rule was never 'the right child.' It's 'go right once, then hug the left wall until you can't anymore.' That's the smallest value in the right subtree, which is exactly the next value up from the one you deleted."*

**Cut rule:** Run Version 1 only, verbally, without drawing Version 2 — state the extension as a rhetorical question instead of a full dry run.

---

## Exit Ticket (19–21 min)

> On paper or in chat: *"In one sentence, why is deletion's overall time complexity O(h) even in the two-children case, when it requires two separate searches?"*
> **Answer:** Both searches are bounded by the tree's height and happen one after the other (not nested), so their costs add rather than multiply: O(h) + O(h) = O(h).

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Two O(h) searches (node + successor) make deletion O(h²) | "Two loops" reads as "multiply the costs" by analogy with nested loops | The checkpoint after Slide Block B — sequential vs. nested cost |
| The successor-finding loop looks at the whole right subtree to pick the smallest value | Without tracing the loop, "smallest in a subtree" sounds like it needs a full scan | Activity 2 — showing the loop is just "right once, then all-the-way left" |
| Recursive and iterative deletion are fundamentally different algorithms | The iterative version's explicit `parent`/`current` bookkeeping looks unfamiliar next to the compact recursive version | Naming the parity directly: both do the same search + one of the same three cleanup moves; iteration just tracks `parent` by hand instead of getting it free from the call stack |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split at the Slide Block B boundary.**
- **Pacing risk:** the iterative parent-pointer implementation is the densest material in the session (it's also the densest in the whole deck's raw slide text — many short slides, one code fragment growing across them). Deliver it at a brisk, high-level pace ("this does the same three cases, just without recursion") rather than tracing every pointer update live; Activity 2 already covers the one piece of iterative-style reasoning (the successor loop) worth slowing down for.
- **Callback opportunity:** the "local check isn't enough, you need the full picture" idea from Session 14's Spot-the-Bug activity resurfaces here in a new form — the successor value has to be correct relative to the ENTIRE subtree it's leaving, not just the node it's replacing. Worth a 10-second verbal callback if time allows, not worth building a slide for.
