# Session 20b — Merge Two BSTs (Part 2 of 2)

**Duration** 20 min · **Topic** Binary Search Tree — Merge: Pseudocode & Complexity · **Prerequisite** Session 20a — Merge Two BSTs, Part 1 (approach, full dry run) · **Session type** Concept lecture

<!-- Split note: continues session-20 (original 50 min) from the Slide Block B boundary. This part covers pseudocode, the O(N1+N2) time / O(H1+H2) space complexity, and the closing real-world callout. This is also the last of the seven BST sessions in this block. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Merge Two BSTs | https://docs.google.com/presentation/d/1cHTFivGiZX_ws3OimObzkzH5v_rUK3yctx0xxamYLwI/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Compare this technique to the merge step of merge sort — combining two already-sorted sequences by repeatedly comparing their fronts. *(ANALYZING)* <!-- placement: inferred analogy, not stated explicitly in the deck -->
2. State the time complexity O(N1 + N2) and space complexity O(H1 + H2), and explain why space depends on height, not node count. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 20a (0–5 min)

Say: *"Four quick ones on the two-stack approach before we look at what it costs."*

**Q1.** What goes onto each stack first, before any comparisons start?
`A` Every node in the tree · `B` Just the root · `C` The root's entire left spine · `D` Only the leaf nodes
→ *Read:* C.

**Q2.** When you pop a node during the merge, what (if anything) do you push next?
`A` Nothing, ever · `B` Its right child only · `C` Its right child's entire left spine, if it has a right child · `D` Its left child
→ *Read:* C — this was Part 1's most-skipped step.

**Q3.** True or false: you alternate popping from stack 1 and stack 2 in a fixed order.
`A` True · `B` False
→ *Read:* False — always compare both tops, pop the smaller.

**Q4.** In Part 1's Human Stacks activity, what did a "push" look like?
→ *Read:* Open response — reconnects to the physical model before formalizing it as pseudocode.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"You've run the algorithm by hand and acted it out standing up. Now: six lines of pseudocode, and the proof that the space cost is much smaller than you'd expect."*

---

## Slide Block B (7–14 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide-block boundary -->
Covers: Pseudocode (`pushLeft` helper + `mergeBSTs` main loop) → code (C++/Python) → complexity analysis (O(N1 + N2) time, O(H1 + H2) space).

**Beats to emphasise**

- Walk the pseudocode's two pieces separately: `pushLeft(root, s)` just walks left, pushing every node it passes, until it hits `null` — this is the "load a stack with a left spine" operation used both at the very start AND every time a right child needs to be added mid-merge.
- The main loop's condition — `if s1 is empty OR (s2 is not empty AND s2's top < s1's top)` — is just a careful way of saying "always compare both tops, UNLESS one stack has already run out." Walk this condition slowly; it's denser to read than to execute.
- Complexity: **time is O(N1 + N2)** because every node from both trees is pushed and popped exactly once. **Space is O(H1 + H2)**, NOT O(N1 + N2) — each stack only ever holds one root-to-current path (a left spine) at any moment, bounded by that tree's height, never the whole tree.

**Checkpoint (at 14 min)** — show hands:
> *"Why is the space complexity O(H1 + H2) and not O(N1 + N2), when every node does eventually get pushed at some point during the algorithm?"*
> **Answer:** Nodes get pushed and popped continuously throughout the run — the stack's *maximum simultaneous size* at any instant is just one left-spine's worth of nodes (bounded by height), not every node the algorithm will ever touch across the whole run.

---

## ⚡ Activity 2 — Real-World Callout: Two Sorted Leaderboards (14–18 min)

**Format:** Real-World Callout · **Exposes:** whether the two-stack technique feels like an arbitrary trick or a recognisable general strategy once it's re-stated outside tree vocabulary.

**Setup line (say this):**
> *"Two class leaderboards, both already sorted by score, and you need one combined leaderboard. No re-sorting allowed — you're too lazy for that. What's the laziest CORRECT way to build the merged list, given both lists are already sorted?"*

**What students do:** 30 seconds, pairs, then a few call-outs.

**How it surfaces:** Push toward the answer if students suggest "just concatenate and sort again": *"That works, but it throws away the fact that both lists were already sorted. Use that fact instead."* Land on: "look at both fronts, take the smaller, repeat."

**Debrief line:**
> *"That's the merge step from merge sort, and it's exactly what today's two stacks are doing on BSTs. Each stack isn't 'a leftover pile of tree nodes' — it's standing in for 'the next smallest value not yet used from this tree,' updated on demand, one pop at a time."*

**Cut rule:** Skip entirely if short on time — it's reinforcement of an idea already delivered, not new content.

---

## Exit Ticket (18–20 min)

> On paper or in chat: *"In one sentence: why does pushing a popped node's right child's LEFT SPINE (rather than just the right child itself) keep the stack correctly ordered for merging?"*
> **Answer:** Because the smallest not-yet-used value in that right subtree is its leftmost node, not the subtree's root — so the stack's new top has to be that leftmost node for the next comparison to stay correct.

**This is the last of the seven BST sessions in this block.** A 2-minute verbal recap tying together Search → Insert → Delete → Kth Smallest → Validate → Predecessor/Successor → Merge as "seven ways of exploiting the same one-line ordering rule from the first BST session" is a strong close.

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Time complexity is O(N1 × N2) | "Merging two things" sounds like it should involve comparing every pair | The complexity breakdown — every node is pushed and popped exactly once, so costs add (O(N1+N2)), they don't multiply |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split at the Slide Block B boundary, and the last session of the BST block.**
- **This topic has no separate "brute force" section in the deck**, unlike Sessions 17, 18, and 19 — the two-stack technique is presented as the only approach. If a student asks "what's the naive way," the honest answer is "build both sorted arrays via in-order traversal, then do a standard two-pointer array merge" — mention it as the obvious O(N1+N2) time / O(N1+N2) space baseline the taught technique improves on for space, but don't build it out as a full section since the deck doesn't. <!-- placement: inferred — flagging the asymmetry with the rest of the topic's session structure -->
