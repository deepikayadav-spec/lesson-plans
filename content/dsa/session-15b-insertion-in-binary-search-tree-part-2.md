# Session 15b — Insertion in Binary Search Tree (Part 2 of 2)

**Duration** 20 min · **Topic** Binary Search Tree — Insertion Complexity & Deletion Preview · **Prerequisite** Session 15a — Insertion in Binary Search Tree, Part 1 (insertion rule, worked dry runs) · **Session type** Concept lecture

<!-- Split note: continues session-15 (original 50 min) from the Slide Block B boundary. This part is intentionally short — complexity analysis plus a conceptual-only preview of Session 16's three deletion cases. Can be run back-to-back with Part 1 or as a standalone short session before Session 16. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Insertion in Binary Search Tree | https://docs.google.com/presentation/d/18K-En87Al628DLlClc7jwzOqCFOhA7mSaxpbETki944/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Compare the space complexity of iterative insertion (O(1)) against recursive insertion (O(h)), and justify the difference in terms of the call stack. *(ANALYZING)*
2. Describe, at a conceptual level, the three deletion cases previewed in this session — leaf, one child, two children — ahead of next session's full treatment. *(UNDERSTANDING)* <!-- placement: inferred from the deck's own deletion-preview section, slides 38–57 -->

---

## Warm-Up Poll — Retrieval Practice on Session 15a (0–5 min)

Say: *"Four quick ones on the insertion rule before we look at its cost and peek ahead to deletion."*

**Q1.** BST insertion rule: go left if the new value is ___, go right if it's ___.
`A` smaller / greater · `B` greater / smaller · `C` equal / unequal · `D` odd / even
→ *Read:* A.

**Q2.** Where does a new value get inserted?
`A` Anywhere there's an empty spot · `B` At the first empty spot the comparison walk leads to · `C` Always as the root's child · `D` It replaces the closest existing value
→ *Read:* B — this was Part 1's Spot-the-Bug takeaway.

**Q3.** Does insertion ever change the value stored in an existing node?
`A` Yes, it updates the closest match · `B` No, it always creates a new node
→ *Read:* B.

**Q4.** What is the time complexity of BST insertion, iterative or recursive, in terms of height `h`?
`A` O(1) · `B` O(log n) always · `C` O(h) · `D` O(n)
→ *Read:* C.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"You can insert correctly now. Two things left: what it costs, and what its mirror-image operation — deletion — is going to look like next session."*

---

## Slide Block B (7–14 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide-block boundary -->
Covers: Iterative and recursive insertion pseudocode/code → complexity analysis (both O(h) time; O(1) space iterative vs. O(h) space recursive) → a conceptual **preview** of Deletion's three cases: deleting a leaf (delete 7), deleting a node with one child (delete 5, replaced by its child 4), deleting a node with two children (delete 11, replaced by successor 14).

**Beats to emphasise**

- Complexity pairing: **iterative insertion is O(h) time, O(1) space; recursive insertion is O(h) time, O(h) space.** Identical time, different space — same contrast as search from the previous session. Say it the same way both times so students hear the pattern repeating.
- **Frame the deletion section explicitly as a preview:** *"We are not building this algorithm today. I'm showing you the three shapes a deletion can take, so next session's pseudocode isn't the first time you've seen them."* Walk the three cases at a conceptual level only — no pseudocode, no code, just "what changes in the tree":
  - **Leaf (delete 7):** node has no children → just remove it, nothing to reattach.
  - **One child (delete 5, whose only remaining child is 4):** node is removed and its single child takes its place.
  - **Two children (delete 11, whose children are 10 and 14):** node is removed and replaced by a value that preserves order — the deck uses `14`, the in-order successor (smallest value in 11's right subtree).
- Do **not** derive the successor/predecessor rule in depth here — that reasoning belongs to Session 16. Today's job is just: "two children means you can't simply delete or promote a child — you need a value that keeps everything sorted."

**Checkpoint (at 14 min)** — show hands:
> *"Node 11 has two children — 10 and 14. The deck replaces it with 14. Who thinks 10 would also have worked?"*
> **Answer:** Yes — either the in-order predecessor (largest value in the left subtree, here 10) or the in-order successor (smallest value in the right subtree, here 14) preserves the ordering. The deck picked the successor; both are valid strategies, and Session 16 covers exactly how to pick and splice one in.

---

## Exit Ticket (14–17 min)

> On paper or in chat: *"(1) Using the tree from Part 1 (root 9, with 2/11 as its children), where does the value 6 get inserted? (2) Name the three deletion cases previewed today."*
> **Answers:** (1) `9`→left(6<9)→`2`→right(6>2)→`5`→right(6>5)→`7`→left(6<7)→**left child of 7.** (2) Leaf, one child, two children.

Homework: re-run Part 1's insert-8 dry run from memory, then predict where 6, 3, and 20 would each land in the same tree. <!-- placement: inferred -->

---

## ⚡ Wrap — Active Learning Strategy: Fist-to-Five Confidence Check (17–20 min)

**Why this strategy here:** deletion hasn't been taught yet — only previewed. A confidence check tells you, before Session 16 starts, whether the three-case framing landed or needs a 2-minute re-anchor at the top of next session.

**Run it (3 minutes):**
> *"Fist to five, right now: fist means 'I couldn't name the three deletion cases if you asked,' five means 'I could explain all three to a partner.' Show me."*

Scan the room. If the average is below 3, note it — open Session 16 with a 2-minute re-walk of the three cases before touching new pseudocode, rather than assuming the preview stuck.

> *"Hold that number. Next session turns these three previews into a real algorithm you can trace end to end."*

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Recursive insertion uses O(1) space, "like iterative does the same job" | Both produce identical trees, so students assume identical cost | The complexity pairing in Slide Block B — same time, different space, tied to the call stack |
| Deleting a two-children node just removes it and reattaches its children arbitrarily | Leaf and one-child deletion are simple removals, so two-children "should be" too | The deletion preview — naming successor/predecessor explicitly as the fix, even before the algorithm is built |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split at the Slide Block B boundary. Deliberately short** — pair it with Part 1 in the same slot, or run it as a quick standalone opener right before Session 16.
- **Known deck artifact — do not teach from it:** the recursive insertion C++/Python code slides in this deck are visually preceded by a leftover LCA code block (`Node* lca(Node* root, Node* p, Node* q) {...}`) that appears to be a copy-paste remnant from an earlier session's slide template, sitting above the actual `insertBST` code on the same slide. It is not part of this session's content — skip past it silently rather than explaining it. <!-- placement: inferred from raw slide-text extraction; flagging so the instructor isn't caught off guard live -->
- **Cap the deletion preview at 5 minutes of talk time.** If you find yourself explaining *why* the successor works, you've drifted into Session 16's territory; stop and say "more on that next time."
