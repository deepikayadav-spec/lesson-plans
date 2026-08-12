# Session 21a — Introduction to Heaps (Part 1 of 2)

**Duration** 35 min · **Topic** Heaps — Definition & Properties · **Prerequisite** Binary Search Trees (previous session: Merge Two BSTs) · **Session type** Concept lecture

<!-- Split note: original session-21 ran 60 min across three slide blocks. Split right after the Classroom Quiz. Part 1 covers the heap definition, min/max distinction, structural properties, and the real-world-callout activity. Part 2 (session-21b) covers insertion, extraction, getMax, other heap families, and applications — the operational core of the topic. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Introduction to Heaps | https://docs.google.com/presentation/d/17X8ri-v3OXVq0DdZrz0oPcu3hWfNY5EsdYNf1uMqhVU/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define a heap as a complete binary tree that satisfies the heap property. *(REMEMBERING)*
2. Distinguish a Min Heap from a Max Heap by the parent–child ordering rule and by what sits at the root. *(UNDERSTANDING)*
3. Explain why a heap's height is `log(n)` and why that bounds every heap operation. *(UNDERSTANDING)* <!-- placement: inferred from Key Takeaways slide 53 -->

*(Insertion, extraction, and applications are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 20: Merge Two BSTs (0–7 min)

Say: *"Seven questions on yesterday's problem — merging two BSTs. No names, no grades, just tell me what stuck."*

**Q1.** What must the final output of "Merge Two BSTs" look like?
`A` Two separate sorted arrays · `B` One sorted array containing every element from both trees · `C` The two trees merged into one BST · `D` Doesn't matter, any order works
→ *Read:* B is the whole problem statement. If this misses, the rest of the poll is noise — restate the problem before Q2.

**Q2.** What is the first concrete step of the taught approach?
`A` Do a full inorder traversal of each tree and concatenate the two lists · `B` Push every left-descendant node from each root onto two separate stacks · `C` Convert both trees to arrays and merge-sort them · `D` Convert both trees into heaps
→ *Read:* If most of the class picks A, they're recalling *what inorder traversal produces*, not the *stack-based mechanism* that was actually taught. That gap is fine for today but flag it.

**Q3.** *(MSQ — pick 2)* Which are true of the merge step once both stacks are primed?
`A` Compare the tops of both stacks and pop the smaller one · `B` Always pop from stack 1 first if there's a tie · `C` If the popped node has a right child, push that child's left-descendant chain onto the *same* stack it came from · `D` Recursively call the merge function on each subtree
→ **Answer:** A and C.

**Q4.** Time complexity of Merge Two BSTs, with `N1`, `N2` nodes in the two trees?
`A` `O(N1 · N2)` · `B` `O(N1 + N2)` · `C` `O(log N1 + log N2)` · `D` `O(N1 log N2)`
→ **Answer:** B — every node in both trees is visited exactly once.

**Q5.** Space complexity, with `H1`, `H2` the heights of the two trees?
`A` `O(1)` · `B` `O(N1 + N2)` · `C` `O(H1 + H2)` · `D` `O(H1 · H2)`
→ *Read:* C. If the class answers B here, they're substituting time complexity for space complexity — a mix-up worth naming out loud before moving on: the stacks only ever hold one root-to-leaf path per tree, not every node.

**Q6.** In the dry run, once one stack goes empty but the other still has elements, what happens?
`A` The algorithm throws an error · `B` Keep popping from whichever stack still has elements · `C` The algorithm stops early · `D` Swap the two stacks
→ **Answer:** B — this is exactly the `s1.empty() || ...` branch in the pseudocode.

**Q7.** True or False: the algorithm never sorts the combined result directly — the sorted order falls out of the stack mechanics alone.
`A` True · `B` False
→ **Answer:** A True. *Read:* Worth 20 seconds — this is the same "the order comes from the algorithm's structure, not a separate sort step" idea that will reappear today in how a heap keeps its max accessible without ever sorting itself.

**Running it** — poll tool, ~40 s/question, project the distribution after each. Total 7 min including reads.

---

## Hook (7–11 min)

Say: *"Yesterday's BST problem got you a fully sorted array. That took visiting every node, and every stack push and pop. But most of the time, you don't need the full sorted order — you need one thing, fast, over and over: the maximum. Or the minimum. Right now."*

Ask: *"Emergency room, right now — who gets seen next? Not the person who arrived first. The person who's most critical. Every time someone new walks in, the answer to 'who's next' can change instantly. Would you re-sort the entire waiting room every time someone new arrives?"*

Let a few answers land — someone will say "no, that's wasteful." Then: *"Exactly. You want a structure that always knows who's most urgent, without needing everyone else in order. That's a heap."*

---

## Slide Block A (11–22 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — slides 4–9: Definition, Types of Heaps, Heap Properties -->
Covers: Heap definition → Min Heap vs Max Heap → Heap Properties (Complete Binary Tree shape, unsorted siblings, height = `log(n)`).

**Beats to emphasise**

- **Heap property ≠ full sort.** Slide 8 is the single most important slide in this block: left and right children are *not* ordered relative to each other, only relative to their parent. Say this out loud even though the slide already says it — it directly contradicts the BST instinct they walked in with from the previous topic.
- **Root tells you everything you need.** Min heap → smallest at root. Max heap → largest at root. That's the whole payoff of the structure.
- **Height = `log(n)` because the heap is always a complete binary tree** — no skew is possible, unlike the BSTs from the last several sessions. This is *why* every heap operation you'll see in Part 2 is bounded by `log(n)`.

**Checkpoint (at 22 min)** — cold-call two students:
> *"Give me the two things every heap must satisfy, in one sentence."*
> **Answer:** It must be a complete binary tree (all levels full except possibly the last, filled left to right), and every parent must be ≥ (max heap) or ≤ (min heap) its children.

---

## ⚡ Activity 1 — Real-World Callout (22–27 min)

**Format:** Real-World Callout · **Exposes:** the sense that "heap" is an abstract data-structure exercise disconnected from anything students already reason about daily.

**Setup line (say this):**
> *"Thirty seconds. Name one real system where you always need 'the most urgent one' or 'the biggest one' right now, and you genuinely don't care what order everything else is in."*

**What students do:** Shout out systems. Write up to 8 on the board — expect things like hospital triage, an OS process scheduler, a flight standby list, a food-delivery app's next-driver assignment, a leaderboard's "current top score."

**How it surfaces:** For 2–3 of the callouts, push once: *"In that system, what's the 'parent' and what decides who's on top?"* Accept plain English — e.g., triage → "the most critical patient is always the one at the front, and a new critical patient can jump straight to the front without re-sorting the whole line."

**Debrief line:**
> *"Every one of those systems needs the extreme value, fast, again and again, and can't afford to re-sort everything each time someone new shows up. That's exactly the problem a heap solves — and that's why it's not a sorted array underneath."*

**Cut rule:** If running late, take 3 callouts instead of 8 and skip the push-for-mechanism step. Do not cut the debrief line.

---

## Classroom Quiz (27–32 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Concept Card Sort (32–35 min)

**Why this strategy here:** Part 1 hands students two labels (Min Heap, Max Heap) and one shared shape rule (complete binary tree). A sort forces them to file facts under the right label instead of blurring the two — exactly the discrimination Part 2's insert/extract dry runs assume is already automatic.

**Run it (3 minutes):**
> *"I'll call out a fact. You tell me: Min Heap, Max Heap, or Both. Go fast."* Call out: *"Smallest value at the root"* (Min) · *"Largest value at the root"* (Max) · *"Complete binary tree shape"* (Both) · *"Height is log(n)"* (Both) · *"Left child always smaller than right child"* (Neither — trick, call this out explicitly if picked) · *"Every parent ≥ both children"* (Max) · *"Every parent ≤ both children"* (Min).

Linger on the "Neither" trick — it's the single most load-bearing fact from Slide Block A (siblings are never guaranteed ordered against each other).

> *"You now know what a heap IS. Part 2 is entirely about HOW you get a value in and out while keeping all of this true."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A heap keeps everything in sorted order, like a BST's inorder traversal | The immediately preceding topic (BSTs) trained "traverse it and you get sorted order" | Slide 8 — point at a valid max heap where the left child is smaller than the right child, or vice versa; only the parent–child relationship is guaranteed |
| Heap height can be `O(n)`, like a skewed BST | Same BST habit from the immediately preceding topic, where skewed/unbalanced trees are common | Slide 9 — a heap is *always* a complete binary tree, so height is always `log(n)`, no exceptions |
| Min heap means "less important" and max heap means "more important" | The words "min" and "max" get read as value judgments instead of ordering direction | State plainly: min heap = smallest value at root, max heap = largest value at root — nothing about importance, only about ordering |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz.**
- **BST carryover is the dominant risk in this part.** Because this is the first Heaps session immediately after the BST unit, expect the class to keep reaching for "sorted order" instincts. Name the contrast explicitly at least twice (checkpoint and Part 1 Wrap).
- **This is a foundation session.** Part 2 and Sessions 22–28 all build on the definitions taught here.
