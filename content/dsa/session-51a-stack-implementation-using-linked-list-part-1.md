# Session 51a — Stack Implementation Using Linked List (Part 1 of 2)

**Duration** 33 min · **Topic** Stack & Queue — Linked-List Stack: Push & the Three-Step Order · **Prerequisite** Session 50 — Stack Implementation Using Array · **Session type** Concept lecture

<!-- Split note: original session-51 ran 60 min. Split right after the Classroom Quiz. Part 1 covers node structure, initialization, and the push dry run, drilling the three-step ordering. Part 2 (session-51b) covers top(), pop's two-step order, advantages, pseudocode/code, and the "can this overflow" discussion. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Stack Implementation Using Linked List | https://docs.google.com/presentation/d/19LsdepePTa52TM4UqbL4G4ZMhJM1MigMvtSx_ozv9mo/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State that a linked-list stack's `top` pointer corresponds to the head of the list, initialised to `null`. *(REMEMBERING)*
2. Trace `push` (create node → link it to the current top → update top) in the correct order. *(APPLYING)*

*(pop's two-step order, top(), advantages/disadvantages, and the pseudocode/code walkthrough are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 50 (Array Stack) (0–6 min)

Say: *"Eight questions on the array stack before we rebuild the same idea a completely different way."*

**Q1.** In the array implementation, `top` starts at what value on an empty stack?
`A` 0 · `B` -1 · `C` capacity · `D` null

**Q2.** The correct order of operations for `push` in the array implementation is:
`A` Insert the value, then increment `top` · `B` Increment `top`, then insert the value · `C` Order doesn't matter · `D` Decrement `top`, then insert
→ *Read:* If this isn't unanimous B, the whole session's contrast with linked-list push order won't land — recap it before moving on.

**Q3.** Overflow in the array stack occurs when:
`A` `top == -1` and you call push · `B` `top == capacity - 1` and you call push · `C` The array is empty · `D` `top == capacity`

**Q4.** Underflow occurs when:
`A` `top == -1` and you call pop · `B` `top == capacity - 1` and you call pop · `C` The array is full · `D` `top == 0`

**Q5.** What is the time complexity of push, pop, top, empty, and size in the array implementation?
`A` O(n) for all · `B` O(1) for all · `C` O(log n) for all · `D` Varies by operation

**Q6 (MSQ — pick all correct).** Which of these are genuine disadvantages of an array-backed stack?
`A` Fixed capacity risks overflow · `B` Resizing the array is expensive (allocate + copy everything) · `C` Reading the top element is slow · `D` Memory can be wasted if the array is much bigger than what's actually stored
→ *Read:* Correct answers: A, B, D. If anyone picks C, that's the misconception to squash right now — direct indexing is precisely what an array stack is *good* at.

**Q7.** True or False: `pop()` on the array stack clears/zeroes the array slot it just removed.
`A` True · `B` False

**Q8.** `isFull()` in the array implementation is the single comparison:
`A` `top == 0` · `B` `top == -1` · `C` `top == capacity - 1` · `D` `top == capacity`

**Running it** — poll tool, ~30 s per question. Total 6 min including reads.

---

## Hook (6–9 min)

Say: *"Last session ended with a complaint: the array stack has a hard ceiling — capacity. Today's question: what if there's no array at all?"*

Draw a single box on the board: `[data | next]`. Ask:

> *"If this is all I have — one value, and a pointer to the next one — where would 'top' even live?"*

Take a guess or two, then reveal: *"Top isn't an index anymore. Top **is** a pointer, and it always points at the most recently added node — the head of the list. No capacity, no array, no `top = top + 1`. Instead: build a new node, hand it the old top as its `next`, and make it the new top. Three steps, every time."*

---

## Slide Block A (9–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 4–19: Introduction, Node Structure, Initialize the Stack, Empty() Operation, Push dry run (10, 20, 30) -->
Covers: Introduction (top = head of the list) → Node structure (`data`, `next`) → Stack initialised with `top = null` → `empty()` operation (`top == null`) → Push dry run: `push(10)`, `push(20)`, `push(30)`.

**Beats to emphasise**

- **Top is a pointer now, not a number.** Say this contrast explicitly against Session 50 — it's the single biggest mental shift of the day.
- **Push is always three steps, in this fixed order:** (1) create a new node holding the value, (2) set the new node's `next` to whatever `top` currently is, (3) update `top` to point at the new node. Narrate all three steps, in order, for every push in this block — the order is non-negotiable, because step 2 has to happen *before* step 3 overwrites `top`.
- Walk `push(10)` (top: null → node(10)), `push(20)` (node(20)→node(10), top moves to node(20)), `push(30)` (node(30)→node(20)→node(10), top moves to node(30)). By the third push, students should be able to predict the chain themselves.
- **`empty()`** is one check: is `top` `null`?

**Checkpoint (at 19 min)** — cold-call:
> *"After push(10), push(20), push(30) — what does `top` point to, and what does `top->next->next` point to?"*
> **Answer:** `top` points to the node holding 30. `top->next->next` is the node holding 10 (30 → 20 → 10 → null).

---

## ⚡ Activity 1 — Live Trace: "Three Steps, Every Push" (19–25 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can hold the *order* of push's three steps in their head — this is the exact ordering Part 2's Activity 2 will later show breaking on the pop side.

**Setup line (say this):**
> *"Same idea as last session's relay, pointers instead of indices. I call an operation, you tell me what `top` points to *and* what `top->next` is, before I confirm."*

Run these **one at a time** (continuing the deck's own numeric example):

```
push(10)   → top → 10 → null
push(20)   → top → 20 → 10 → null
push(30)   → top → 30 → 20 → 10 → null
top()      → returns 30, chain unchanged
pop()      → Step 1: top = top->next (top now → 20)
           → Step 2: discard the old node holding 30
           → chain: top → 20 → 10 → null
push(40)   → top → 40 → 20 → 10 → null
push(50)   → top → 50 → 40 → 20 → 10 → null
```

**How it surfaces:** Before revealing the `pop()`, ask: *"Which happens first — moving `top`, or discarding the old node?"* The correct answer is always "move top first." Make students say the two pop steps in order out loud before you confirm the new chain.

**Common wrong answer:** students say pop "just removes the top node" without articulating that `top` must be reassigned *before* the old node can safely be discarded — this is exactly the bug Part 2's Activity 2 exposes.

**Debrief line:**
> *"Every push is three moves — new node, link it to the old top, then take over as top. Every pop is the same three moves backwards — move top off the old node first, *then* clean it up. Get that order wrong and you either lose the list or point at deleted memory."*

**Cut rule:** If running short, drop the final two pushes (40, 50) — the ordering lesson is already fully demonstrated by push(10)/(20)/(30) and the one pop.

---

## Classroom Quiz (25–30 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Human Chain Push/Pop (30–33 min)

**Why this strategy here:** the three-step push order is the whole session's foundation, and a physical chain makes "step 2 before step 3" impossible to fudge — you can't reassign `top` before the new node has somewhere to point.

**Run it (3 minutes):**
> *"Three volunteers. Empty stack — nobody's `top` yet. New volunteer joins: first they point at whoever is currently `top` (or at nothing, if empty), THEN the class declares them the new top. Do this for all three, one at a time, out loud, in that order."*

Run it for 3 volunteers joining in sequence, then reverse it for one "pop" — the class must say "point away from the old top first" before that volunteer sits down.

> *"That's the whole session. Part 2 does the reverse operation — and shows you exactly what breaks when someone gets impatient and sits down before pointing away."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Push order is create → update top → link next | Students port over the array stack's "increment first" instinct without realising the object being updated is different here | Slide Block A's explicit 3-step narration, repeated for all three pushes in the dry run |
| `top->next` after several pushes points to the *oldest* element | "Next" sounds forward-moving, like it should lead deeper into the list in insertion order | Tracing the full chain in the checkpoint at minute 19 — showing `top->next->next` reaches backward through push history |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz.**
- **This session is a structural mirror of Session 50** — same beats (init → push dry run → pop dry run → failure conditions → pseudocode → code → key takeaways), deliberately, so students can map the two implementations onto each other operation-by-operation.
- **The three-step push ordering is the whole point of this part.** If you only have time to drill one thing, drill this.
