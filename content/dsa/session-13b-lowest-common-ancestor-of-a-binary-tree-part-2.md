# Session 13b — Lowest Common Ancestor of a Binary Tree (Part 2 of 2)

**Duration** 34 min · **Topic** Binary Tree — LCA: Optimal Recursive Approach · **Prerequisite** Session 13a — Lowest Common Ancestor of a Binary Tree, Part 1 (definition, bruteforce approach) · **Session type** Concept lecture

<!-- Split note: continues session-13 (original 60 min) right after the Classroom Quiz. This part covers the optimal recursive approach, its two full dry runs, and the closing Spot-the-Bug activity. This is also the last session of the Binary Tree block. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Lowest Common Ancestor of a Binary Tree | https://docs.google.com/presentation/d/1PfK6oST_X-plBPAQkknErZZXRYBwoNHF826rRmBc7b8/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Explain why, in the recursive approach, a node whose left AND right recursive calls both return non-null must itself be the LCA. *(UNDERSTANDING)*
2. Trace the recursive LCA algorithm on a given tree to determine the LCA of two specified nodes, including cases where one node is an ancestor of the other. *(APPLYING)*
3. State the time and space complexity of the optimal recursive solution — O(N) time, O(H) space — and identify the worst case (a skewed tree, where H = N). *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 13a (0–5 min)

Say: *"Four quick ones on the bruteforce approach before we replace it with one pass."*

**Q1.** The bruteforce LCA approach works by:
`A` Comparing the two nodes' values directly · `B` Building the full root-to-node path for both `p` and `q`, then finding where the paths last agree · `C` Using a queue and BFS · `D` Sorting the tree first
→ *Read:* B.

**Q2.** For the bruteforce tree (root 8; left 3, right 10; 3's children 1, 6; 6's children 4, 7) with query `p=1, q=7`, what is the LCA?
`A` 8 · `B` 3 · `C` 6 · `D` 1
→ *Read:* B — path to 1: `8→3→1`; path to 7: `8→3→6→7`; last common node is `3`.

**Q3.** What are the two costs of the bruteforce approach that an optimal approach should avoid?
`A` Two separate searches, plus explicitly storing both paths · `B` It's actually already optimal · `C` It uses too much time complexity (worse than O(N)) · `D` It can't handle the self-ancestor case
→ *Read:* A — bruteforce is still O(N) time, its cost is the *extra work*, not a worse complexity class.

**Q4.** True or false: a node is considered its own ancestor and its own descendant.
`A` True · `B` False
→ *Read:* True — this is the edge case from Part 1's Activity 1, and it resurfaces today in the recursive base case.

**Running it** — poll tool, ~35 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"One pass, no stored paths, no separate searches for p and q. Watch how much of Part 1's cost list just disappears."*

---

## Slide Block C (7–19 min) — DELIVER SLIDES AS-IS

Covers: Optimal recursive Approach (`if root is null or root == p or root == q: return root`; recurse left and right; `if !left: return right`; `if !right: return left`; `return root`) → Dry Run on the bruteforce tree (`p=1, q=7`) → Pseudocode → Time Complexity O(N) → Space Complexity O(H) → C++/Python code.

**Beats to emphasise**

- Walk the dry run exactly as the deck stages it: descend to node `1` (matches `p`, return `1` up to its parent `3`); descend the other side to node `7` (matches `q`, return `7` up through `6`, since `6`'s left returned null); at node `3`, left result = `1`, right result = `7` — **both non-null** — so node `3` returns *itself* up to the root as the LCA.
- State the combine rule as a single sentence and put it on the board: *"If both sides find something, you're standing at the split point — that's the LCA. If only one side finds something, hand it straight up unchanged."*
- Space complexity is O(H), the recursion call stack — **not** automatically O(N)/O(log N). It only becomes O(N) in the worst case, a fully skewed tree where height equals the number of nodes.

**Checkpoint (at 19 min)** — cold-call:
> *"At node 3 in the dry run, left result is node 1, right result is node 7. Both non-null. What does node 3 return, and why?"*
> **Answer:** Node `3` returns *itself*. Both subtrees reported back a non-null find, meaning `p` and `q` are in different branches below node `3` — so node `3` is the point where their paths to the root diverge, which makes it the LCA.

---

## ⚡ Activity 2 — Dry-Run Relay: Be the Call Stack (19–27 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can execute the recursive "descend, then combine on the way back up" logic themselves, using the deck's own second worked example — root `20`; left `10`, right `30`; `10`'s children `5, 15`; `30`'s children `25, 35`; `5`'s children `3, 7`; `25`'s left child `22`; query `p=22, q=35`.

**Setup line (say this):**
> *"Ten volunteers, one per node: 20, 10, 30, 5, 15, 25, 35, 3, 7, 22. I'll call a node's name — that student says what THEY see (is it null? is it p=22? is it q=35? or neither?), calls their children if neither, and waits to hear back BEFORE announcing what they return to their own parent. No one gets to answer for their parent."*

**What students do:** Follow the deck's own Optimal Solution 2 sequence:
- `20` isn't `p` or `q` → calls left (`10`) and right (`30`).
- `10`'s branch (`10 → 5 → 3`, `5 → 7`) finds neither `22` nor `35` anywhere → `10` eventually returns `null` up to `20`.
- `30` isn't `p`/`q` → calls left (`25`).
- `25` isn't `p`/`q` → calls left (`22`) — `22` matches `p` → returns `22` up to `25`. `25`'s right is null → `25` returns `22` up to `30`.
- `30` calls right (`35`) — `35` matches `q` → returns `35` up to `30`.
- `30`: left result = `22`, right result = `35` — **both non-null** → `30` returns *itself* to `20`.
- `20`: left result = `null` (from `10`), right result = `30` → hand `30` straight up unchanged.
- Final LCA = `30`.

**How it surfaces:** If the student playing `30` announces the wrong return value (e.g. propagates `22` or `35` instead of declaring itself the LCA), stop and re-point at the combine rule from Slide Block C: both sides non-null means *this* node is the answer, not either child's value.

**Debrief line:**
> *"Every node in that relay did exactly one of three things: found a target, found nothing, or discovered it was sitting between the two targets. Only the last case is the LCA — and notice nobody needed to see the whole tree to know it, just their own two children's answers."*

**Cut rule:** If running short, skip relaying node `10`'s entire null-returning branch — state that it returns null and start the live relay from node `30` downward, since that's where the interesting logic lives.

---

## ⚡ Activity 3 — Spot the Bug: Broken Combine Logic (27–32 min)

**Format:** Spot the Bug · **Exposes:** reading recursive code for its general shape ("it recurses left and right, then does something") instead of tracing the exact base case and combine conditions. Every variant below is a one- or two-line change from the deck's own pseudocode (slide 28/119).

**Setup line (say this):**
> *"Three versions of the LCA function on screen. Only one is what's actually in the deck. For the other two, find the missing or wrong line, and tell me what tree/query would expose the bug — you don't need to run it, just point at the line."*

Put all three on screen:

```
// Version A
lca(root, p, q) {
  if (root == null) return root
  lf = lca(root.left, p, q)
  rt = lca(root.right, p, q)
  if (!lf) return rt
  if (!rt) return lf
  return root
}

// Version B
lca(root, p, q) {
  if (root == null || root == p || root == q) return root
  lf = lca(root.left, p, q)
  rt = lca(root.right, p, q)
  if (!lf) return lf
  if (!rt) return lf
  return root
}

// Version C — the deck's actual version
lca(root, p, q) {
  if (root == null || root == p || root == q) return root
  lf = lca(root.left, p, q)
  rt = lca(root.right, p, q)
  if (!lf) return rt
  if (!rt) return lf
  return root
}
```

**What students do:** 90 seconds, then hands up per version.

**Answers**

| Version | Bug | What breaks |
|---|---|---|
| A | Base case drops `root == p \|\| root == q` | The recursion never recognises it has actually found `p` or `q` — it just keeps descending past them looking for `null`, so it can never correctly report "found `p` here" up to a parent. |
| B | `if (!lf) return lf` should be `return rt` | When the left side comes back empty, this returns the empty left result instead of handing up whatever the right side found — so a real match on the right side gets silently thrown away. |
| C | None — this is the deck's real algorithm | Matches the dry run from Slide Block C exactly. |

**How it surfaces:** If students accept Version A because "it still checks `root == null`," push: *"Walk it on our Part 1 bruteforce tree — root 8, target p=1. When does this version ever return node 1 itself?"* (Answer: never — it only returns non-null when a subtree is entirely empty, so a genuine match is never signalled upward.)

**Debrief line:**
> *"Both bugs are one wrong or missing line, and both are invisible unless you trace them against a query where they actually matter. That's exactly why we dry-run recursive code line by line instead of eyeballing it."*

**Cut rule:** If running late, drop Version A and only compare B against the real version C — B's bug is subtler and more instructive, and A vs C is a smaller, faster contrast to state verbally if needed.

---

## Exit Ticket (32–34 min)

> On paper or in chat: *"Using today's Optimal Solution 2 tree — root 20; left 10, right 30; 10's children 5, 15; 30's children 25, 35; 5's children 3, 7; 25's left child 22 — what is the LCA of p=5 and q=22?"*
> **Answer:** `20`. Path to `5`: `20 → 10 → 5`. Path to `22`: `20 → 30 → 25 → 22`. The only node common to both paths is the root, `20` — so that's the LCA.

Scan responses on the way out — this query has neither node as an ancestor of the other and the split happens at the root, so it's a clean check of whether students can apply the combine rule to a tree they've now seen twice, on a query that wasn't dry-run for them in class.

**This closes the Binary Tree topic (Sessions 1–13).** A short recap before dismissing is worth the 60 seconds: Top View (Session 11) read the tree by column with a map, Right View (Session 12) read it by level with a queue, and LCA (Session 13) read it by recursive descent-and-combine — three different lenses on the same tree structure.

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The base case `root == p \|\| root == q` means "we found the final answer" | It looks like a success condition | Slide Block C — the real decision happens at the ancestor where BOTH sides return non-null, not at the match itself |
| Bruteforce and optimal give different answers on the same input | They look like unrelated methods | Slide Block C dry-runs the identical tree and query (`p=1, q=7` → LCA `3`) that Part 1's bruteforce approach used |
| Space complexity is always O(N) for the recursive approach | "Recursion = expensive" is a common blanket rule | State O(H) explicitly, then contrast a balanced tree (`H ≈ log N`) against the worst-case skewed tree (`H = N`) |
| If `lf` is non-null, that's automatically the LCA | Feels like "found something, done" | Activity 3, Version B — you must also check whether `rt` is non-null; only when exactly one side is null do you propagate the other, and both non-null means the *current* node is the LCA |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz, and the last session of the Binary Tree batch.** Close with the one-line recap in the Exit Ticket section rather than pointing to a next session — there isn't one in this batch.
- **The deck's "Optimal Solution" (slides 45–77) and the earlier recursive "Approach" + "Dry Run" (slides 10–27) are the same algorithm on the same tree and the same query (`p=1, q=7`)** — just re-animated in two different visual styles (a pre-order-traversal narrative vs. a recursive-call narrative). Don't present them as two different algorithms; pick one animation pass to actually click through live in Slide Block C, and mention the other exists in the deck as reinforcement for students to revisit later.
- **Slides 123–124 (Summary + "Optimal solution Steps")** give the deck's own compressed recap ("check for node p, check for node q, perform pre-order traversal") — useful as a closing slide, but this phrasing simplifies the real combine logic into something that sounds sequential. Don't let students walk away thinking the algorithm checks for `p`, then separately checks for `q`, in two passes — it's one pass that checks for either at every node.
