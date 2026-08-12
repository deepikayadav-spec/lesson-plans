# Session 08b — Balanced Binary Tree (Part 2 of 2)

**Duration** 31 min · **Topic** Balanced Binary Tree — Why Brute Force Is Slow & the Optimal Approach · **Prerequisite** Session 08a — Balanced Binary Tree, Part 1 (definition, brute-force approach) · **Session type** Concept lecture

<!-- Split note: continues session-08 (original 50 min) right after the Classroom Quiz. This part covers the O(N²) redundancy reveal (Activity 1) and the optimal single-pass solution. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Balanced Binary Tree | https://docs.google.com/presentation/d/1MscAVuewwMhNE52LB11SF5Rp6zEcccmvaXrZa08GS2I/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Apply the optimal single-traversal algorithm (a shared `ans`/flag updated inside the same `height()` call) to check balance in one pass. *(APPLYING)*
2. Analyze why folding the balance check into the height computation eliminates the brute force's redundant work, cutting time complexity from O(N²) to O(N). *(ANALYZING)* <!-- placement: inferred phrasing, content drawn from deck's own Brute Force vs Optimal complexity summary slides -->

---

## Warm-Up Poll — Retrieval Practice on Session 08a (0–5 min)

Say: *"Four questions on the brute-force approach before we find out exactly how wasteful it is."*

**Q1.** A tree is balanced if, at every node:
`A` Left and right subtree heights are exactly equal · `B` Left and right subtree heights differ by at most 1, and both subtrees are themselves balanced · `C` The node has exactly 2 children · `D` The tree has an even number of nodes
→ *Read:* B.

**Q2.** In the brute-force approach, how is `height()` called at each node?
`A` Once, cached for reuse · `B` Fresh, from scratch, on both children, every single time · `C` Never — brute force skips height entirely · `D` Only at the root
→ *Read:* B — this is exactly what Part 2 is about to prove is expensive.

**Q3.** What is the time complexity of the brute-force check?
`A` O(N) · `B` O(N log N) · `C` O(N²) · `D` O(H)
→ *Read:* C.

**Q4.** In Part 1's Predict-and-Defend, what did you and your partner guess for total `height()` calls on an 8-node tree — close to 8, or a lot more?
→ *Read:* No right/wrong here — just reconnect them to their own prediction before revealing the real count.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–8 min)

Say: *"Time to check your prediction. We're counting, for real, how many separate `height()` calls pass through one single node in an 8-node tree."*

---

## ⚡ Activity 1 — Spot the Bug: Why Brute Force Is O(N²) (8–14 min)

**Format:** Spot the Bug · **Exposes:** students accept "O(N²)" as a label without seeing *why* — they don't realize `height()` re-walks the same subtree from scratch every time a different ancestor asks for it.

**Setup line (say this):**
> *"Here's the balanced tree from the deck — 8 nodes: root 1; children 2 and 3; node 2's children 4 and 5; node 4's left child 8; node 3's children 6 and 7. I'm going to call `height(node 4)` to check node 2's balance. That call walks down into node 8. Now — when `balanced()` recurses into node 4 itself a moment later, does it call `height()` on node 8 *again*?"*

**What students do:** Trace, out loud, how many separate `height()` calls — fired from different ancestor nodes on their way down — end up passing through node 8 before the whole check finishes. (Answer: at least twice — once when node 2 needs its left height, once when node 4 needs its own left height, potentially more depending on how the recursion is structured.)

**How it surfaces:** If a student says "no redundancy, each node is visited once" — point at node 8 specifically and ask them to count every distinct call stack that reaches it. Do the count on the board.

**Debrief line (say this):**
> *"Every node underneath gets walked past by one `height()` call for every ancestor above it that needed a height. That repeated walking, multiplied across every node in the tree, is the entire O(N²) — not a mysterious formula, just the same subtree being re-measured over and over. The optimal approach fixes exactly this: one function does the height *and* the balance check, in the same single walk."*

**Cut rule:** If running short, skip the full count and just state the redundancy verbally using node 8 as the example — but do not cut the debrief line, it's the entire bridge into Slide Block B.

---

## Slide Block B (14–24 min) — DELIVER SLIDES AS-IS

Covers: Optimal Approach → Dry Run (Example 2 tree, ans-tracking) → Pseudocode → Code → Complexity Analysis.

**Beats to emphasise**

- **The one-line insight:** fold the balance check *into* `height()` itself. A shared flag (`ans`, starting `true`) gets flipped to `false` the moment any node's height difference exceeds 1 — `height()` still returns the height as before, but now also updates `ans` on the way.
- **Full Dry Run on the 8-node tree** (root 1; children 2, 3; node 2's children 4, 5; node 4's left child 8; node 3's children 6, 7 — same tree as Activity 1), walked leaf-up exactly as the deck does it:
  - Node 8 (leaf): left=0, right=0 → diff=0, `ans` stays `true`. height(8) = 1.
  - Node 4: left=1 (from 8), right=0 (no right child) → diff=1, `ans` stays `true`. height(4) = 1 + max(1,0) = 2.
  - Node 5 (leaf): left=0, right=0 → diff=0, `ans` stays `true`. height(5) = 1.
  - Node 2: left=2 (from 4), right=1 (from 5) → diff=1, `ans` stays `true`. height(2) = 1 + max(2,1) = 3.
  - Node 6 (leaf) and Node 7 (leaf): both diff=0, both height=1.
  - Node 3: left=1, right=1 → diff=0, `ans` stays `true`. height(3) = 1 + max(1,1) = 2.
  - Node 1 (root): left=3 (from 2), right=2 (from 3) → diff=1, `ans` stays `true`. height(1) = 4.
  - **`ans` was never flipped — the tree is balanced.**
- **Contrast explicitly with Example 1's tree:** same two ingredients (left height, right height) at every node, but there `ans`/the check would flip to `false` the moment node 2's diff of 2 is found — and once flipped, no later node can undo it.
- **Complexity:** Time O(N) — `height()` now does double duty but is still called exactly once per node. Space: the deck states this as O(N) on its complexity slide, but its own explanation describes it as depending on the recursion stack depth (the tree's height, H) — i.e. **O(H), worst case O(N) for a skewed tree**, same shape as the brute-force approach's space complexity. <!-- placement: inferred — flagging a wording inconsistency in the deck's own slide (headline says "O(N)", explanation describes O(H)); teach it as O(H) worst-case O(N) so students aren't confused later when they see O(H) written elsewhere for the same idea. -->

**Checkpoint (at 24 min)** — show hands:
> *"At node 2 in the tree we just walked, height difference was 1 — a pass. If that had been a difference of 2 instead, does the tree still get checked past node 2, the way brute force does?"*
> **Answer:** No — the moment `ans` flips to `false`, it can never flip back. The rest of the traversal still runs (to compute remaining heights correctly) but the final answer is already decided.

---

## ⚡ Activity 2 — Dry-Run Relay: Track lh, rh, and ans (24–29 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can now do the height/diff/`ans` bookkeeping themselves without watching it happen on a slide.

**Setup line (say this):**
> *"Same 8-node tree. I'll point at a node — you give me left height, right height, the difference, and whether `ans` changes. Get all four before I confirm. If your height is right but your `ans` call is wrong, that's the interesting mistake — that's the whole point of today."*

**What students do:** Relay through nodes 8, 4, 5, 2 (or however far time allows) in the same leaf-up order as Slide Block B — one student per node, cold-called, stating the four numbers before the instructor confirms against the deck.

**How it surfaces:** The most common error is reporting the *height* correctly but skipping the diff/`ans` step, or reporting `ans` as if it resets per node. When this happens, point at the pseudocode line `if (diff > 1) ans = false` and have the student re-read it aloud, then re-answer.

**Debrief line (say this):**
> *"Height climbs by one every step up the tree, automatically. `ans` only ever moves in one direction — true to false — and only when a node actually fails. Two different jobs, same function call, same single pass."*

**Cut rule:** If running short, relay only nodes 4 and 2 — the two nodes where a diff of exactly 1 makes the "still balanced" point — and state the leaf nodes' results directly rather than relaying them.

---

## Exit Ticket (29–31 min)

> **Part 1:** In Part 1's Example 1 tree, the root's own height difference was 1 (a pass). If you had *only* checked the root and stopped, what would you have wrongly concluded — and why is that wrong?
> **Answer:** You'd wrongly conclude "balanced," because the root's own children's heights differ by only 1. The tree actually fails two levels down, at node 2 (difference of 2) — checking only the root misses it entirely.
>
> **Part 2:** In one sentence — what does the optimal approach do that brute force does *not* do?
> **Answer:** It does not recompute `height()` separately, from scratch, for every node — it computes height and checks balance in the same single pass, using a shared flag.

Scan responses on the way out. If Part 1 answers show "the root already told us it's fine," that's the misconception to open Session 09 against — Session 09's diameter problem has the exact same trap (the answer often isn't decided at the root).

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Brute force and optimal check different things | Same arithmetic (`diff = abs(left - right)`, `if diff > 1`) appears in both sets of pseudocode | Side-by-side pseudocode comparison in Slide Block B — the *check* is identical; only *how many times `height()` runs* differs |
| `ans` updates every time `height()` is called anywhere in the tree | Both live inside the same function call | Activity 2's debrief — height changes at every call; `ans` only changes when a node's own diff exceeds 1 |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split right after the Classroom Quiz.**
- **Deck repeats itself heavily for animation, not new content.** Slides 89–133 re-run the *exact same two example trees* (Example 1 unbalanced, Example 2 balanced) a third time via the raw abs-diff method, purely as visual reinforcement. Click through these briskly — they need no new instructor commentary, the numbers are already familiar by then.
- **Space-complexity wording:** the deck's Optimal Approach complexity slide headlines "O(N)" for space but its own explanation describes recursion-stack depth (O(H), worst case O(N)) — teach the O(H) framing consistently with Session 07 and Part 1's Brute Force approach in this same session, and don't let the "O(N)" headline imply the optimal approach changed something about space usage. It didn't.
- **`height()` is now doing double duty.** Remind students it's the *exact* function from Session 07, unchanged — only the *caller* (`balanced()`) is new.
