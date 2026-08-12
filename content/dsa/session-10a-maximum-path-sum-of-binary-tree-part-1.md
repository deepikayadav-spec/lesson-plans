# Session 10a — Maximum Path Sum of Binary Tree (Part 1 of 2)

**Duration** 42 min · **Topic** Binary Tree — Maximum Path Sum: Definition & First Pass · **Prerequisite** Diameter Of Binary Tree (Session 09) · **Session type** Concept lecture

<!-- Split note: original session-10 ran 60 min across three slide blocks (the deck teaches the algorithm twice — once directly, once via "deflection point" intuition). Split right after the Classroom Quiz, which falls right after the first full pass of the algorithm (path vocabulary, approach, dry run, pseudocode, complexity). Part 1 is that complete first pass. Part 2 (session-10b) is the deck's second, intuition-building pass plus the closing activities. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Maximum Path Sum of Binary Tree | https://docs.google.com/presentation/d/1GfVjTl50KdOAQMpefbNJ8GRcX4GXOln4qnkuWlOgckw/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define a path in a binary tree, distinguishing path length (number of edges) from path sum (sum of node values), and state that a path may start and end at any node — including the same node twice. *(REMEMBERING)*
2. Explain the approach: at each node, combine the node's own value with the maximum path sums contributed by its left and right subtrees, ignoring any subtree whose contribution is negative. *(UNDERSTANDING)*
3. Apply the `maxDownPath` / `maxPathSum` recursion by hand to compute the maximum path sum of a given binary tree. *(APPLYING)*

*(The "deflection point" intuition and the negative-sum clamp bug are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 09 (Diameter Of Binary Tree) (0–7 min)

Say: *"Eight quick ones on yesterday's Diameter of a Binary Tree before we build on top of it today."*

**Q1.** What is the diameter of a binary tree measured in?
`A` Number of nodes · `B` Number of edges · `C` Number of levels · `D` Sum of node values
→ *Read:* B. The deck is explicit: "the length of a path is measured by the number of edges." If a chunk of the room says A (nodes), correct it now — today's session reuses the same tree-walking pattern but sums *values* instead of counting edges, and that distinction needs to be crisp going in.

**Q2.** Must the diameter's longest path pass through the root?
`A` Always · `B` Never · `C` It may or may not · `D` Only in a skewed tree
→ *Read:* C.

**Q3.** In the brute-force diameter approach, what makes it O(N²)?
`A` Recomputing the height of a node's subtrees from scratch, for every single node in the tree · `B` Using two arrays instead of one · `C` Sorting the nodes first · `D` Recursion depth exceeding N
→ *Read:* A. If C or D come up, the "height gets recalculated over and over" mental model hasn't landed — restate it before Q4, since today's optimal approach is a direct answer to this exact inefficiency.

**Q4.** What did the optimal `height(root, &ans)` function do that the brute-force `height()` didn't?
`A` It also updated a global `ans` with the current node's diameter candidate, as a side effect of computing height · `B` It returned the diameter directly instead of the height · `C` It used a queue instead of recursion · `D` It ignored negative subtree heights
→ *Read:* A. This "do the useful side-effect update while you're already there computing something else" pattern is exactly what today's `maxDownPath` also does.

**Q5. (MSQ)** Select ALL that are true about the diameter formula used at each node.
`A` diameter-at-node = height(left subtree) + height(right subtree) · `B` height-at-node = 1 + max(height(left), height(right)) · `C` `ans` is updated with `max(ans, lh + rh)` · `D` diameter-at-node = max(height(left), height(right))
→ *Read:* A, B, C are correct.

**Q6.** For the 15-node dry-run tree (root = node 3), what final diameter value did the class compute?
`A` 7 · `B` 8 · `C` 9 · `D` 6
→ *Read:* B. If most say 7, they stopped tracking `ans` at node 3's own local diameter and never noticed node 6 overtake it with 8 — that's exactly why you keep a running max instead of trusting the root's own number.

**Q7.** In the optimal approach, the extra space used comes from:
`A` An explicit array of size N · `B` The recursion call stack · `C` A hash map storing all N heights · `D` Sorting overhead
→ *Read:* B.

**Q8. (MSQ)** Which of these are true about the O(H) space complexity? *(pick all that apply)*
`A` In a skewed tree, H = N, so space is O(N) · `B` In a balanced tree, H = log N, so space is O(log N) · `C` The brute-force and optimal approaches have different space complexities · `D` H is always equal to N
→ *Read:* A, B are correct. C is the trap — both approaches are O(H); only the *time* complexity improved from O(N²) to O(N).

**Running it** — poll tool, ~40–50 s per question. Total 7 min.

---

## Hook (7–11 min)

Say: *"Yesterday, every question was about edges — how many hops between two nodes. Today the tree has numbers on it, and some of those numbers are negative."*

Draw a tiny 3-node tree on the board: root `15`, left child `-20`, right child `25`. Ask: *"Diameter of this tree — trivial, it's 2 edges, root to either leaf. But what's the biggest total you can make by adding up values along some path through this tree?"*

Let a few guesses land (some will include `-20`). Then: *"By the end of Part 1 you won't want to touch that `-20` at all — and you'll know exactly why the algorithm agrees with you."*

---

## Slide Block A (11–20 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide-block boundary, slides 1–15 -->
Covers: title/agenda → what a "path" is in a binary tree (path length = edges, path sum = sum of node values) → the worked path-length/path-sum example (tree with root 42, path `12 → 9 → 17 → 28`, length 3 edges, sum 66) → Problem Statement → Example 1 (root 15, children -20/25, output 50 via `15 → 25 → 10`) → Example 2 (output 27 via `12 → 1 → 10 → -4 → 8`).

**Beats to emphasise**

- **Path length ≠ path sum.** The deck deliberately shows both on the same example tree — 3 edges, but a sum of 66 — precisely so students stop conflating "how far" with "how much." Say both numbers out loud for that one example.
- **A path can start and end anywhere, including the same node.** This is a hard break from Session 09, where every dry run was framed leaf-to-leaf. Flag it as a deliberate contrast, not a footnote.
- Walk Example 1 and Example 2 exactly as the deck states the winning path — don't just show the output number, say the node sequence out loud both times.

**Checkpoint (at 20 min)** — cold-call two students:
> *"In one sentence — what's the difference between a path's length and a path's sum?"*
> **Answer:** Length is the number of edges on the path; sum is the total of the node *values* along that same path. A path can have a small length and a huge sum, or the reverse.

---

## ⚡ Activity 1 — Predict-the-Output (20–25 min)

**Format:** Predict-the-Output · **Exposes:** the instinct to route the answer through every "big-looking" node on the tree regardless of sign, instead of treating a negative branch as something to walk away from.

**Setup line (say this):**
> *"Here's the tree from Example 1 — root 15, with -20 and 25 as its two children, 5 hanging off -20, and 10 hanging off 25. Before I reveal the answer: write down the maximum path sum you can make in this tree, and which nodes it passes through."*

**What students do:** 30–45 seconds writing individually, then a show of hands between two or three candidate answers you write on the board (e.g., "35? 50? 0?").

**How it surfaces:** If someone lands on 35 or lower, ask them to say their path out loud, node by node — most wrong guesses either route through `-20` or add up every node in the tree instead of following one connected path.

**Debrief line:**
> *"The winning path is 15 → 25 → 10, sum 50. Node -20 and its child 5 never show up anywhere in the answer — the moment a branch's contribution goes negative, the algorithm treats it as worth zero rather than letting it drag the total down. That's the 'ignoring any negative sums' line from the approach slide, and it's the entire reason 50 beats every path that touches -20."*

**Cut rule:** If running short, skip the individual write-and-guess step — go straight to "35 or 50, hands up" and then the debrief.

---

## Slide Block B (25–34 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide-block boundary, slides 15–49 -->
Covers: Approach (traverse every node top-to-bottom; at each node, use the left and right child's contribution, ignoring negative sums; keep a running max) → Dry Run on the tree rooted at node 1 (children 2 and 10; leaves 4, 3, 8; deeper nodes 9, 5, 6) → Pseudocode (`maxDownPath` / `maxPathSum`) → Complexity Analysis → C++/Python code.

**Beats to emphasise**

- Two variables, two jobs: `maxDownPath` **returns** `root.data + max(L, R)` — the best single branch a parent can extend — while it **updates** the global `ans` with `root.data + L + R` — both branches, because that's the biggest sum *through* this node as a bend point. This return-vs-update split is the crux of the whole algorithm; say it twice.
- Run the dry run exactly as the deck sequences it: leaves first (4, 3, then 8), up through 9, then 6, then 5, then 10, then finally node 1. Track `ans` out loud at every single update — it moves `-∞ → 4 → 9 → 8 → 17 → 6 → 11 → 38` and then stops changing at node 1 (34 doesn't beat 38).
- `ans` starts at `-1e9` / `-infinity`, **not** `-1` like yesterday's diameter — flag this contrast explicitly, since students will pattern-match on Session 09's `ans = -1`.
- Complexity: O(N) time (every node visited once), O(H) space (recursion stack) — same shape as yesterday's optimal diameter approach.

**Checkpoint (at 34 min)** — show hands:
> *"At node 10 in the dry run, the left branch contributed 17 and the right branch contributed 11. What did node 10 return to its parent (node 1), and what did it feed into `ans`?"*
> **Answer:** It returned `10 + max(17, 11) = 27` to node 1 — only its better branch. It fed `10 + 17 + 11 = 38` into `ans` — both branches. 38 turns out to be the final answer; 27 is just what got passed upward.

---

## Classroom Quiz (34–39 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Two-Column Concept Sort (39–42 min)

**Why this strategy here:** the single hardest idea today is that one node produces *two different numbers* for two different purposes. A physical sort — literally two columns — makes students commit each fact to one column or the other, which a passive recap wouldn't.

**Run it (3 minutes):**
> *"Two columns on the board: 'RETURNED to parent' and 'FED into ans.' I'll call out a fact from today's dry run — you tell me which column it belongs in."* Call out, one at a time: *"data + max(L,R)"* (returned) · *"data + L + R"* (fed into ans) · *"only the better branch"* (returned) · *"both branches combined"* (fed into ans) · *"what node 10 gave to node 1 (27)"* (returned) · *"what made ans hit 38"* (fed into ans).

Write each in its column as students call it. End by pointing at the two columns: *"Every single node in this tree does both of these, every time. Part 2 gives that pair of columns a name — 'deflection point' — and a bug to go find."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A path must start at the root or end at a leaf | Session 09's diameter dry runs were always framed leaf-to-leaf | Slide Block A's explicit "any-node path" definition, reinforced in Activity 1 |
| A negative-valued node should still be included if the path "looks" high-value overall | Intuition says "more nodes = more chances at a big number" | Activity 1's predict-then-reveal |
| The value returned to a node's parent is the same value used to update the global `ans` | Both use the same L/R inputs, so they look identical | The Slide Block B checkpoint and the Part 1 Wrap's two-column sort, distinguishing `data + max(L,R)` (return) from `data + L + R` (ans update) |
| `ans` should start at `-1` like yesterday's diameter | Direct pattern-matching from the immediately preceding session | Point out node values can be as low as -1000 (per the deck's stated constraints), so `-1` is not "negative enough" — `-1e9`/`-infinity` is required |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz.** Part 1 alone delivers a complete, working algorithm — a student who only attends Part 1 can solve the problem correctly, just without the deeper "why" intuition Part 2 builds.
- **`ans = -1e9` vs `ans = -1`:** call this out by name at least twice (Slide Block B and again in the misconceptions table) — it is the single most likely copy-paste error students will carry into practice problems from yesterday's diameter code.
- **Keep the 1/2/10-rooted tree drawn on the board (or a slide) through the end of this part** — Part 2 reuses it immediately, no need to redraw.
