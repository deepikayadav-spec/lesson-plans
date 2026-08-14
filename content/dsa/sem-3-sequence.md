# DSA Semester 3 — Session Sequence & Slot Design

**For planners.** Source: [Aptitude Team Docs — DSA / Sem 3](https://aptitude-team.gitbook.io/session-plans/dsa/sem-3). This is the topic order and slot allocation for Semester 3, fit to the real slot budget:

| Type | Slots | Percentage |
|---|---|---|
| Learning Sessions | 61 | 52.1% |
| Practice Sessions | 56 | 47.9% |
| **Total** | **117** | **100%** |

Every Learning Session is **50 min max** (45 min instruction + 5 min buffer), same format as Programming Foundations and Aptitude. Practice Sessions are not individually authored here — they follow the existing topic-agnostic ritual in `dsa-practice-session-playbook.md`, one practice block per 1–2 learning sessions, question set swapped to match whatever topic just landed.

---

## Why 61, not 65

The GitBook sequence has **65 leaf-level sessions** across 63 numbered topics — two topics (*Introduction to Linked List*, *Deletion in Linked List*) are each split into a Part 1 / Part 2 sub-page. 65 leaf sessions against a 61-slot budget means **4 sessions have to merge**. Merge choices, in order of how natural the pairing is:

1. **Introduction to Linked List** — Intro-1 + Intro-2 → one 50-min session.
2. **Deletion in Linked List** — Deletion-1 + Deletion-2 → one 50-min session.
3. **Implement Queue Using Stack** — the GitBook sequence already lists this as two flat topics (Part 1, Part 2) back to back → merged into one 50-min session.
4. **Pre-Order + Post-Order Traversal** — merged into one session. Chosen over merging In-Order or Level-Order because Pre- and Post-Order are the two simplest, most symmetric traversals (root-first vs. root-last, same recursion shape); In-Order gets its own slot because it's the one that matters for BST work later in the sequence, and Level-Order needs its own slot because it's the only iterative/BFS traversal in the set.

No other merges — every other GitBook topic keeps its own 50-min slot, including `Kth Largest Element in an Array` Part 1 / Part 2, which GitBook lists as two separate topics for a reason (two genuinely different techniques — partial sort vs. heap-based) and stays split.

## The two content gaps

- **Sessions 1–6 (Hashing → Two Sum)** have no source deck anywhere on disk. These will be written from scratch, no-deck / teaching-block format — same pattern already used for no-deck sessions elsewhere on this site (badge + teaching blocks instead of `DELIVER SLIDES AS-IS`). All six are standard, well-established DSA topics with no ambiguity in content.
- **Bit Manipulation** (9 sessions already built in `content/dsa`: Binary Operations through Bitwise XOR For a Given Range) is **not part of this GitBook sequence** and is left out of the 61-slot numbering below. Those files stay as-is in `content/dsa`, unrenumbered, as separate/bonus content outside Semester 3's official sequence.

---

## The 61-session sequence

| # | Topic | Duration | Source |
|---|---|---|---|
| 1 | Hashing | 50 min | No deck — write from scratch |
| 2 | Prefix Sum | 50 min | No deck — write from scratch |
| 3 | Sliding Window, Two-Pointer Technique | 50 min | No deck — write from scratch |
| 4 | Longest Subarray with Sum K | 50 min | No deck — write from scratch |
| 5 | Largest Subarray Sum | 50 min | No deck — write from scratch |
| 6 | Two Sum Problem | 50 min | No deck — write from scratch |
| 7 | Introduction to Linked List | 50 min | Existing: `session-38-singly-linked-list.md` (already covers construct/print/length/search — matches GitBook's Intro-1+Intro-2 scope directly) |
| 8 | Insertion in Linked List | 50 min | Existing: `session-39-insertion-deletion.md` (insertion half) |
| 9 | Deletion in Linked List | 50 min | Merged (Deletion-1 + Deletion-2) — existing: `session-39-insertion-deletion.md` (deletion half) |
| 10 | Introduction to Doubly Linked List | 50 min | Existing: `session-40-doubly-linked-list-traversal-insertion-deletion.md` (intro/traversal part) |
| 11 | Insertion in Doubly Linked List | 50 min | Existing: `session-40-...` (insertion part) |
| 12 | Deletion in Doubly Linked List | 50 min | Existing: `session-40-...` (deletion part) |
| 13 | Circular Linked List | 50 min | Existing: `session-41-circular-linked-list.md` |
| 14 | Reversing a Linked List | 50 min | Existing: `session-42-reversals.md` |
| 15 | Cycle Detection In Linked List | 50 min | Existing: `session-43-cycle-detection.md` |
| 16 | Length of Cycle In Linked List | 50 min | Existing: `session-44-cycle-length.md` |
| 17 | Adding Two Numbers | 50 min | Existing: `session-45-adding-two-numbers.md` |
| 18 | Merge Two Sorted Linked List | 50 min | Existing: `session-46-merge-two-lists.md` |
| 19 | Intersection Of Two Linked Lists | 50 min | Existing: `session-47-intersection-of-linked-lists.md` |
| 20 | Flatten a Linked List | 50 min | Existing: `session-48-flatten-list.md` |
| 21 | Introduction of Stack, Stack Implementation Using Array | 50 min | Existing: `session-49-intro-of-stack.md` + `session-50a/50b-stack-implementation-using-array-*.md` (merge to one 50-min session) |
| 22 | Stack Implementation Using Linked List | 50 min | Existing: `session-51a/51b-stack-implementation-using-linked-list-*.md` (merge to one 50-min session) |
| 23 | Introduction to Monotonic Stacks | 50 min | Existing: `session-53-monotonic-stack.md` |
| 24 | Next Greater Element | 50 min | Existing: `session-56-next-greater-element.md` |
| 25 | Infix, Prefix, and Postfix Notations | 50 min | Existing: `session-52a/52b-infix-prefix-postfix-*.md` (merge to one 50-min session) |
| 26 | Implement Min Stack | 50 min | Existing: `session-54a/54b-min-stack-*.md` (merge to one 50-min session) |
| 27 | Balanced Parenthesis | 50 min | Existing: `session-55-balanced-parenthesis.md` |
| 28 | Asteroid Collision | 50 min | Existing: `session-57a/57b-asteroid-collision-*.md` (merge to one 50-min session) |
| 29 | Largest Rectangle In Histogram | 50 min | Existing: `session-58a/58b-largest-rectangle-in-histogram-*.md` (merge to one 50-min session) |
| 30 | Queue - Introduction & Implementation Using Arrays | 50 min | Existing: `session-59-queue-intro-and-implementation-using-arrays.md` |
| 31 | Queue Implementation Using Linked List | 50 min | Existing: `session-60-queue-implementation-using-linked-list.md` |
| 32 | Implement Stack Using Queue | 50 min | Existing: `session-61-stack-using-queue.md` |
| 33 | Implement Queue Using Stack | 50 min | Merged (Part 1 + Part 2) — existing: `session-62a/62b-queue-using-stack-*.md` |
| 34 | Introduction to Binary Trees | 50 min | Existing: `session-01-introduction-to-binary-trees.md` |
| 35 | Binary Tree Traversals | 50 min | Existing: `session-02-binary-tree-traversals.md` |
| 36 | Pre-Order + Post-Order Traversal | 50 min | Merged — existing: `session-03-pre-order-traversal.md` + `session-05-post-order-traversal.md` |
| 37 | In-Order Traversal | 50 min | Existing: `session-04-in-order-traversal.md` |
| 38 | Level Order Traversal | 50 min | Existing: `session-06-level-order-traversal.md` |
| 39 | Height of a Binary Tree | 50 min | Existing: `session-07-height-of-a-binary-tree.md` |
| 40 | Balanced Binary Tree | 50 min | Existing: `session-08-balanced-binary-tree.md` |
| 41 | Diameter Of Binary Tree | 50 min | Existing: `session-09-diameter-of-binary-tree.md` |
| 42 | Maximum Path Sum of Binary Tree | 50 min | Existing: `session-10-maximum-path-sum-of-binary-tree.md` |
| 43 | Top view of Binary Tree | 50 min | Existing: `session-11-top-view-of-binary-tree.md` |
| 44 | Right view of Binary Tree | 50 min | Existing: `session-12-right-view-of-binary-tree.md` |
| 45 | Lowest Common Ancestor of a Binary Tree | 50 min | Existing: `session-13-lowest-common-ancestor-of-a-binary-tree.md` |
| 46 | Introduction to Binary Search Tree | 50 min | Existing: `session-14-introduction-to-binary-search-tree.md` |
| 47 | Insertion in Binary Search Tree | 50 min | Existing: `session-15-insertion-in-binary-search-tree.md` |
| 48 | Deletion in Binary Search Tree | 50 min | Existing: `session-16-deletion-in-binary-search-tree.md` |
| 49 | Kth Smallest Element in BST | 50 min | Existing: `session-17-kth-smallest-element-in-bst.md` |
| 50 | Validate a Binary Search Tree | 50 min | Existing: `session-18-validate-a-binary-search-tree.md` |
| 51 | Predecessor and Successor in BST | 50 min | Existing: `session-19-predecessor-and-successor-in-bst.md` |
| 52 | Merge Two BSTs | 50 min | Existing: `session-20-merge-two-bsts.md` |
| 53 | Heaps | 50 min | Existing: `session-21-introduction-to-heaps.md` |
| 54 | Implementation of Binary Heap | 50 min | Existing: `session-22-implementation-of-binary-heap.md` |
| 55 | Heapsort Algorithm | 50 min | Existing: `session-23-heapsort-algorithm.md` |
| 56 | Max Heap Validation | 50 min | Existing: `session-24-max-heap-validation.md` |
| 57 | Convert Min Heap to Max Heap | 50 min | Existing: `session-25-convert-min-heap-to-max-heap.md` |
| 58 | Kth Largest Element in an Array — Part 1 | 50 min | Existing: `session-26-kth-largest-element-in-an-array.md` (split into Part 1/2 content) |
| 59 | Kth Largest Element in an Array — Part 2 | 50 min | Existing: `session-26-...` (split into Part 1/2 content) |
| 60 | Merge K Sorted Arrays | 50 min | Existing: `session-27-merge-k-sorted-arrays.md` |
| 61 | Top K Frequent Elements | 50 min | Existing: `session-28-top-k-frequent-elements.md` |

---

## What this doesn't cover yet

- None of the 61 sessions above are in the 50-min/2-ALS format yet — the existing "Existing" files are still in their original longer format from the DSA content migration, and the "No deck" and "Merged" rows don't have files written at all.
- Actually building this — writing the 6 new no-deck sessions, merging the paired files down to single 50-min sessions each, and renumbering/reordering the rest of `content/dsa` to match this sequence — is separate follow-up work, not done by this doc.
- Practice Session placement (which of the 56 slots follows which Learning Session) isn't mapped topic-by-topic here — the existing playbook format doesn't need a fixed 1:1 mapping to work.
