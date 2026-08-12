# Session 07b — Height of a Binary Tree (Part 2 of 2)

**Duration** 26 min · **Topic** Binary Tree — Properties · **Prerequisite** Session 07a — Height of a Binary Tree, Part 1 (definition, recursive formula, bottom-up dry run) · **Session type** Concept lecture

<!-- Split note: continues session-07 (original 50 min) from the Slide Block B boundary. Part 1 covered the definition and dry run; this part covers pseudocode/complexity, the nodes-vs-edges convention, and the closing activities. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Height of a Binary Tree | https://docs.google.com/presentation/d/1hyM0duOwFw78I_a7majxxe6ZGF_9icnJtlwgQNvfujs/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Distinguish the "number of nodes" convention for height from the "number of edges" convention, and adjust the algorithm's base case (`0` vs. `-1`) accordingly. *(ANALYZING)* <!-- placement: inferred phrasing, grounded in Slides 34-35, which state this distinction directly -->
2. State and justify the time and space complexity of the recursive height algorithm — O(N) time; O(H) space, worst case O(N) for a skewed tree. *(ANALYZING)* <!-- placement: inferred phrasing, grounded in Slides 30-31, 38, 115-120 -->

---

## Warm-Up Poll — Retrieval Practice on Session 07a (0–4 min)

Say: *"Three quick ones on the height formula before we look at what changes if a textbook defines it differently."*

**Q1.** State the recursive height formula.
`A` `leftHeight + rightHeight` · `B` `1 + max(leftHeight, rightHeight)` · `C` `max(leftHeight, rightHeight)` · `D` `1 + leftHeight + rightHeight`
→ *Read:* B.

**Q2.** What does a `null` node return in the height computation?
`A` 1 · `B` -1 · `C` 0 · `D` It errors out
→ *Read:* C — this is the node-counting convention's base case. Hold this number; it's about to become the whole topic.

**Q3.** In Part 1's dry run, does the recursion compute the root's height before or after its children's heights?
`A` Before · `B` After
→ *Read:* B — recursion resolves bottom-up; the root is always last.

**Running it** — poll tool, ~35 s/question. Total 4 min including reads.

---

## Bridge (4–6 min)

Say: *"Part 1's formula and base case are correct for one specific convention — counting nodes. Some judges and textbooks count edges instead, and that changes exactly one line. Today: what line, and why it matters."*

---

## Slide Block B (6–18 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 29-38, 41-51: pseudocode, complexity, C++/Python code, the nodes-vs-edges convention note, and the "three methods" recap -->
Covers: Pseudocode (`height(root){ if(root==null) return 0; leftHeight=height(root->left); rightHeight=height(root->right); return 1+max(leftHeight,rightHeight) }`) → Time Complexity O(N), each node visited once → Space Complexity O(H), the call stack's depth, worst case O(N) for a skewed tree → C++ and Python code → an explicit alternate convention: some textbooks/judges define height as the number of *edges* on the longest path instead of the number of nodes, which only changes the base case, from `return 0` to `return -1` → a "three methods" recap: counting levels, counting nodes on the longest path, and the recursive formula — all three producing the same number.

**Beats to emphasise**

- **The base case is the only thing that changes between the two height conventions.** Node convention: `if root == null, return 0`. Edge convention: `if root == null, return -1`. Everything else in the function is identical. This is stated directly in the deck (Slides 34-35) and is the single most practically useful thing in this session — students will meet both conventions on different judges and in different textbooks.
- **Space complexity is about the call stack, not a data structure you built.** Contrast directly with session 06's queue: nothing here is explicitly created by the programmer — the recursion itself consumes stack space proportional to how deep it goes, which is the height, `H`.
- The **"three methods" slides** (level counting, longest-path counting, and the recursive formula) are not three different algorithms — they're three ways of arriving at the same number. Say this outright; the deck itself demonstrates the formula method on a subtree that is literally node 3's own subtree from the main dry run (left height 2, right height 1, height `1+max(2,1)=3`), reusing the same worked example rather than introducing a new tree.

**Checkpoint (at 18 min)** — show hands:
> *"Using the edge convention instead of the node convention, what would this same tree's height come out to?"*
> **Answer:** 3, not 4 — the edge convention is always exactly one less than the node convention, because every leaf now returns 0 instead of 1.

---

## ⚡ Activity 2 — Spot the Bug: Nodes vs. Edges (18–22 min)

**Format:** Spot the Bug · **Exposes:** the assumption that "height" is a single fixed definition, when in fact the only thing distinguishing the two accepted conventions is one base-case value.

**Setup line (say this):**
> *"Same function, one number changed. `return 0` becomes `return -1` in the base case. Before I tell you why anyone would do that — guess: for our tree from the dry run, height 4 by nodes, what does this new version return?"*

Show both, side by side:
```
height(root):                         height(root):
    if root == null: return 0             if root == null: return -1
    ...                                    ...
```

**What students do:** Predict the new number (3), then justify it using just a single leaf node: in the node convention, `height(leaf) = 1 + max(0, 0) = 1`; in the edge convention, `height(leaf) = 1 + max(-1, -1) = 0`.

**How it surfaces:** If students say "still 4," make them compute a single leaf's height under the edge-convention base case live — show that the leaf's own height changes from 1 to 0 first, and that the off-by-one then rides all the way up to the root untouched.

**Debrief line:**
> *"Every textbook and every judge picks one of these two conventions. The formula never changes — only the base case does. Read the problem statement's worked example before you trust your gut on which one you're being asked for."*

**Cut rule:** If short on time, skip the full leaf-to-root propagation and just state the rule directly — *"edge-convention height is always node-convention height minus one"* — then move on.

---

## ⚡ Activity 3 — Predict-the-Output: Apply the Formula Cold (22–24 min)

**Format:** Predict-the-Output · **Exposes:** whether students can apply the recursive height formula independently, without the instructor guiding them node by node the way Activity 1 did.

**Setup line (say this):**
> *"Forget the whole tree. Here's just one subtree, isolated: its left child's height is 2, its right child's height is 1. Five seconds, on your own — what's this node's height?"*

**What students do:** Write or say the number silently, then reveal together. Correct answer: 3, since `1 + max(2, 1) = 3`. <!-- placement: inferred activity, but the exact numbers (left height 2, right height 1) are not invented — they are node 3's own subtree from the deck's main dry run, reused here deliberately as an unguided check -->

**How it surfaces:** If someone answers 2 (dropped the `+1`) or 4 (added instead of taking the max), make them say the formula out loud, word by word, before recomputing.

**Debrief line:**
> *"That's the entire algorithm, done. Every node in a tree of any size answers this exact same one-line question about its two children — nothing more."*

**Cut rule:** If short on time, cut this activity entirely and ask it instead as the Slide Block B checkpoint question — it is short enough to serve as either.

---

## Exit Ticket (24–26 min)

> On paper or in chat: *"A single-node tree just has a root, no children. What's its height using the node convention, and what's its height using the edge convention?"*
> **Answer:** Node convention: 1 (the deck's own stated base case for a single-node tree). Edge convention: 0 (no edges exist on a path that never leaves the root). <!-- placement: inferred exit-ticket scenario; both numbers follow directly from the base cases stated in Slides 8 and 34-35, not from an invented example -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Height = number of edges, always | Some online judges and resources default to the edge convention, and students may have seen it before this course | Slides 34-35's explicit dual-convention note, plus Activity 2's side-by-side base-case comparison |
| `height = leftHeight + rightHeight + 1` (sum instead of max) | Pattern-matching against other formulas (e.g., counting total nodes) rather than height specifically | Walking the pseudocode line by line: it is `max`, not `+`, between the two subtree heights |
| Space complexity is always O(log N) | The balanced-tree case is the one usually taught first as the "typical" case in complexity discussions | Explicit statement in Slide Block B: a skewed tree pushes the space complexity to O(N), same as its height |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split at the Slide Block B boundary.**
- **Pacing risk:** Slides 52-114 retrace the *exact same* dry-run tree a third time, now annotated with `h(x)` notation for each recursive call. This is reinforcement of Part 1's Activity 1 relay, not new content — narrate it briskly ("we already did this, here it is written as h(x) instead") rather than re-deriving every value from scratch.
- **The "Example" subtree in the Method 3 slides (Slides 50-51, values giving height 3) is not a new example** — it is node 3's own subtree, lifted directly out of the main dry-run tree from Part 1. Presenting it as a fresh, independent example (as the deck's slide order might suggest) risks implying there's a second worked tree in this session; there isn't. <!-- placement: inferred observation about deck structure, not a content error, but worth naming so the instructor doesn't accidentally introduce a tree that doesn't exist -->
- **Two slides near the very end (122-123) are duplicate recap images** of the same dry-run tree and values already covered — no new information to narrate; treat them as a visual summary to flash past.
- The Classroom Quiz placeholder note from Part 1 applies to this session too — no quiz bank is embedded in Part 2.
