# Session 47a — Intersection of Linked Lists (Part 1 of 2)

**Duration** 32 min · **Topic** Intersection of Two Singly Linked Lists — Brute Force · **Prerequisite** Linked list traversal & two-pointer basics (Session 46 — Merge Two Sorted Linked Lists) <!-- placement: inferred --> · **Session type** Concept lecture

<!-- Split note: original session-47 ran 60 min. Split right after the Classroom Quiz. Part 1 covers the problem's exact contract (node identity, not value equality) and the brute-force map approach. Part 2 (session-47b) covers the length-difference approach and the optimal two-pointer switching trick. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Intersection of Linked Lists | https://docs.google.com/presentation/d/1ZUJxVBoauXcUtxsWNqsSvgrgJE-oeeb_sAFOGYW1J10/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the intersection-of-two-linked-lists problem precisely: return the first shared node of two singly linked lists, or `null` if none exists. *(REMEMBERING)*
2. Explain why two nodes holding the **same value** are not necessarily the intersection point — only a shared **node (memory address)** counts. *(UNDERSTANDING)*
3. Trace and implement the brute-force approach: store list 1's node pointers in a map, then scan list 2 against that map. *(APPLYING)*

*(The length-difference approach and the optimal two-pointer approach are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 46 (Merge Two Sorted Lists) (0–5 min)

Say: *"Quick recall check on last session's merge before we build on it. Answer solo, no discussion yet."*

**Q1.** In the merge-two-sorted-lists algorithm, why do we create a dummy node before merging begins?
`A` To store the final answer permanently · `B` To avoid special-casing the very first node inserted into the merged list · `C` It's required syntax · `D` To count the combined length

**Q2.** `temp1` and `temp2` point at the current nodes of List 1 and List 2. When `temp1->data <= temp2->data`, what happens?
`A` `cur->next = temp2`, move `temp2` · `B` `cur->next = temp1`, move `temp1` forward, then move `cur` forward · `C` Both pointers move forward together · `D` The two lists are swapped

**Q3.** Once `temp1` becomes `null` (list 1 is exhausted), what do we do with the rest of list 2?
`A` Discard it · `B` Attach it directly as `cur->next` — it's already sorted, no more comparisons needed · `C` Reverse it first · `D` Merge it node-by-node against nothing

**Q4.** *(MSQ — pick 2)* Which are true of the merge algorithm's complexity?
`A` Time complexity is O(M + N) · `B` Time complexity is O(M × N) · `C` Space complexity is O(1) extra (a handful of pointers) · `D` Space complexity is O(M + N) because a brand-new list is built
→ *Read:* If many pick D, that's the misconception to kill fast: no new nodes are ever created — only re-linked.

**Q5.** What does `mergeTwoLists` finally `return`?
`A` `temp1` · `B` `cur` · `C` `dummy` · `D` `dummy->next`
→ *Read:* If several pick "dummy," clarify on the spot: `dummy` is scaffolding, never part of the answer — the real list starts one node after it.

**Q6.** In Example 2 of that session, both lists contained the values `3` and `8`. In the merged output, what happened to those duplicate values?
`A` Only one copy of each survives · `B` Both copies survive, appearing back-to-back in the merged sequence · `C` The merge errors out on duplicates · `D` They get combined into a single node

**Q7.** Do we ever allocate a brand-new node to hold a data value while merging?
`A` Yes, one new node per value · `B` No — existing nodes from list 1 and list 2 are re-linked by pointer; only the dummy is newly created

**Running it** — poll tool, ~30 s per question, project results after each. Total 5 min including reads.

---

## Hook (5–7 min)

<!-- placement: inferred — no hook slide in deck; built directly from the two worked examples -->

Draw this on the board, no explanation yet:

```
List 1:  3 → 2 → 6 → 7 → 4 → NULL
List 2:  5 → 9 → 3 → 1 → 6 → 7 → 4 → NULL
```

Ask: *"Somewhere, these two lists become the same list. Not the same values — the same actual nodes, sharing memory from that point on. Where does that happen, and how would you get a computer to find it without just eyeballing the diagram?"*

Let a few guesses land — someone will say "look for node 6." Then: *"You're right that it's 6. But notice list 2 also has a `3` in it — same digit as list 1's `3`. Is that the intersection? No. That's the trap this entire session is built around: same value, different node. By the end you'll have three different ways to tell them apart, from the brute-force way to the one-line-of-genius way."*

---

## Slide Block A (7–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide range from deck: Problem Statement, Examples 1 & 2, Brute Force approach, dry run, pseudocode, complexity, code -->

Covers: Problem Statement → Example 1 → Example 2 → Brute Force Approach → Dry Run → Pseudocode → Complexity Analysis → C++ Code.

**Beats to emphasise**

- Nail the exact contract from the Problem Statement: *"return the first intersection node if there is one; otherwise, return null."* Not the value at that node — the node itself.
- Example 1: `3→2→6→7→4` and `5→9→3→1→6→7→4`, merging at node 6. Example 2: `0→1→2→20→40` and `3→5→20→40`, merging at node 20. Both examples share a tail after the intersection — point that out explicitly, it's the whole geometry of the problem.
- The brute-force approach stores list 1's nodes in `map<Node*, int>` — **the key is the node pointer (its address), not the data value.** Say this out loud, twice. It is the single most important sentence in the block.
- Walk the dry run once at full narration speed (nodes 5, 9, 3, 1 miss the map; node 6 hits), then don't re-narrate every repeated slide — the mechanic is simple once shown.
- On the node with value `3` in list 2 during the dry run: the deck's own annotation says it plainly — *"3 is not in the map (same value, different nodes)."* Point at it.

**Checkpoint (at 19 min)** — cold-call:
> *"Why do we store list 1's nodes in a map instead of just comparing values as we scan both lists side by side?"*
> **Answer:** Because two different nodes on two different lists can hold the same value without being the intersection point. We need to detect the exact same node — same memory location — not just equal data. That's why the map is keyed on the pointer.

---

## ⚡ Activity 1 — Spot the Bug: Same Value, Different Node (19–24 min)

**Format:** Spot the Bug · **Exposes:** the value-equality-vs-node-identity confusion the deck itself flags mid-dry-run.

**Setup line (say this):**
> *"Map `m` now holds every node from list 1. I'm walking `temp2` through list 2 one node at a time. Every time I land on a node, you tell me: found or not found — and defend it using what's actually stored in the map, not the number on the node."*

**What students do:** Call the nodes of list 2 in order — `5, 9, 3, 1, 6` — before each one, take a quick show-of-hands vote (found / not found), then reveal.

**How to handle wrong answers:** The trap node is `3`. If several vote "found" when `temp2` lands on it, stop and ask: *"Found means the map contains this exact node object. Is list 2's node-with-value-3 the same object as list 1's node-with-value-3, or two separate nodes that happen to store the same integer?"* Walk to the board and point at the two separate boxes.

**Debrief line:**
> *"The map's key is a memory address, not a number. `3 == 3` tells you nothing here — it's `same_node == same_node` that matters. That's the whole reason brute force needs a map at all instead of just comparing values."*

**Cut rule:** If running short, skip straight to the `3` node and the `6` node — those are the two that matter (the trap and the answer) — and drop the earlier misses (`5`, `9`, `1`).

---

## Classroom Quiz (24–29 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Node vs. Value Sort (29–32 min)

**Why this strategy here:** the entire session's throughline is "node identity, not value equality," solved three different ways. A quick sort of statements into the two buckets locks in the distinction before Part 2 solves the same problem twice more, without a map either time.

**Run it (3 minutes):**
> *"I'll read a statement. You tell me: is this about NODE IDENTITY or VALUE EQUALITY?"* Read: *"Two lists both contain the number 3"* (value equality) · *"The map's key is a pointer"* (node identity) · *"`temp1 == temp2`"* (node identity) · *"The intersection point is defined by shared memory, not shared data"* (node identity).

> *"Every wrong answer in this problem comes from sliding back into value equality. Part 2 solves the identical problem twice more — once by aligning lengths, once by a pointer-switching trick — and neither one uses a map. Watch how they both still respect node identity without it."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Two nodes with the same value are the intersection | Value-based thinking is the default from every prior list algorithm | Activity 1 — walking the node-with-value-3 trap and pointing at two distinct memory locations |
| The map stores data values, not node addresses | `map<Node*, int>` reads unfamiliar; students assume the int is the payload | Stating explicitly in Slide Block A that the key is the pointer, the `0` is just a placeholder value |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz.**
- **Do not let Slide Block A's dry run (16+ slides of node-by-node map checks) run long** — narrate the mechanic once in full, then move briskly through the repeated frames.
- **Keep the "same value, different node" framing alive** — it's introduced here and resolved two more ways in Part 2. Naming it each time is what turns three separate algorithms into one coherent story about node identity.
