# Session 19 — Stack Implementation Using Linked List

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Stack — Linked-List-Backed Implementation, Push/Pop Ordering, No-Fixed-Overflow · **Prerequisite** Session 18 — Introduction of Stack, Array Implementation
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Stack Implementation Using Linked List | https://docs.google.com/presentation/d/19LsdepePTa52TM4UqbL4G4ZMhJM1MigMvtSx_ozv9mo/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State that a linked-list stack's `top` is a pointer to the head of the list, initialised to `null`. *(REMEMBERING)*
2. Trace `push` (create node → link it to the current top → update top) in the correct three-step order. *(APPLYING)*
3. Trace `pop` (save the old top → advance top → discard the old node) in the correct order, and explain why reversing it causes undefined behaviour. *(APPLYING)*
4. Explain why a linked-list stack has no fixed-capacity overflow, and why "no overflow" doesn't mean "cannot fail." *(UNDERSTANDING)*
5. Weigh a linked-list stack's dynamic sizing against its per-node pointer overhead, compared to Session 18's array-based stack. *(EVALUATING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 18 (3–7 min) · ALS: Polling

5 questions on **Session 18 (Introduction of Stack, Array Implementation)**. ~45 s each, project the distribution, never name individuals.

**Q1.** In the array implementation, `top` starts at what value on an empty stack?
`A` 0 · `B` -1 · `C` capacity · `D` null
→ **B.**

**Q2.** The correct order of operations for `push` in the array implementation is:
`A` Insert the value, then increment `top` · `B` Increment `top`, then insert the value · `C` Order doesn't matter · `D` Decrement `top`, then insert
→ **B.** *Read:* Today's linked-list push has its own fixed order too — different mechanics, same discipline.

**Q3.** Overflow in the array stack occurs when:
`A` `top == -1` and you call push · `B` `top == capacity - 1` and you call push · `C` The array is empty · `D` `top == capacity`
→ **B.**

**Q4.** What's the time complexity of push, pop, top, empty, and size in the array implementation?
`A` O(n) for all · `B` O(1) for all · `C` O(log n) for all · `D` Varies by operation
→ **B.**

**Q5.** *(MSQ — select all that apply)* True disadvantages of an array-backed stack?
`A` Fixed capacity risks overflow · `B` Resizing is expensive (allocate + copy everything) · `C` Reading the top element is slow · `D` Memory can be wasted if the array is bigger than what's stored
→ **A, B, D.** *(C is false — direct indexing is exactly what an array stack is good at.)*

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Say: *"Last session ended with a complaint: the array stack has a hard ceiling — capacity. Today's question: what if there's no array at all?"*

Draw a single box on the board: `[data | next]`.

> *"If this is all I have — one value, and a pointer to the next one — where would 'top' even live?"*

Take a guess or two, then reveal:

> *"Top isn't an index anymore. Top **is** a pointer, and it always points at the most recently added node — the head of the list. No capacity, no array, no `top = top + 1`. Instead: build a new node, hand it the old top as its `next`, and make it the new top. Three steps, every time."*

---

## Slide Block A (10–18 min) — DELIVER SLIDES AS-IS

Covers: Introduction (top = head of the list) → Node structure (`data`, `next`) → Stack initialised with `top = null` → `empty()` operation (`top == null`) → Push dry run: `push(10)`, `push(20)`, `push(30)`.

**Beats to emphasise**

- **Top is a pointer now, not a number.** Say this contrast explicitly against Session 18 — it's the single biggest mental shift of the day.
- **Push is always three steps, in this fixed order:** (1) create a new node holding the value, (2) set the new node's `next` to whatever `top` currently is, (3) update `top` to point at the new node. Narrate all three steps, in order, for every push — the order is non-negotiable, because step 2 has to happen *before* step 3 overwrites `top`.
- Walk `push(10)` (top: null → node(10)), `push(20)` (node(20)→node(10), top moves to node(20)), `push(30)` (node(30)→node(20)→node(10), top moves to node(30)). By the third push, students should predict the chain themselves.
- **`empty()`** is one check: is `top` `null`?

**Checkpoint (at 18 min)** — cold-call:
> *"After push(10), push(20), push(30) — what does `top` point to, and what does `top->next->next` point to?"*
> **Answer:** `top` points to the node holding 30. `top->next->next` is the node holding 10 (30 → 20 → 10 → null).

---

## ⚡ ALS Activity 1 — Live Coding / Dry-Run Relay: Three Steps, Every Push (18–25 min)

**ALS format:** Live Coding / Dry-Run Relay — exposes whether students can hold the *order* of push's three steps in their head. Chosen right after Slide Block A because this ordering is exactly what ALS Activity 2 will later show breaking on the pop side, in reverse.

**Setup line:**
> *"Pointers instead of indices this time. I call an operation, you tell me what `top` points to *and* what `top->next` is, before I confirm."*

Run these **one at a time**:

```
push(10)   → top → 10 → null
push(20)   → top → 20 → 10 → null
push(30)   → top → 30 → 20 → 10 → null
top()      → returns 30, chain unchanged
pop()      → Step 1: top = top->next (top now → 20)
           → Step 2: discard the old node holding 30
           → chain: top → 20 → 10 → null
push(40)   → top → 40 → 20 → 10 → null
```

**How it surfaces:** Before revealing the `pop()`, ask: *"Which happens first — moving `top`, or discarding the old node?"* The correct answer is always "move top first." Make students say the two pop steps in order out loud before you confirm the new chain. Watch for students who say pop "just removes the top node" without articulating the order — that's exactly the bug ALS Activity 2 exposes.

**Debrief line:**
> *"Every push is three moves — new node, link it to the old top, then take over as top. Every pop is the same three moves backwards — move top off the old node first, *then* clean it up. Get that order wrong and you either lose the list or point at deleted memory."*

**Cut rule:** Drop the final `push(40)` — the ordering lesson is already fully demonstrated by push(10)/(20)/(30) and the one pop.

---

## Slide Block B (25–34 min) — DELIVER SLIDES AS-IS

Covers: `top()` (read-only) → full pop sequence back down to an empty stack → `empty()` revisited → Advantages (dynamic size, efficient memory, no overflow, simple pointer rewrites) → Pseudocode/Complexity/Code.

**Beats to emphasise**

- **`top()` never touches the pointer chain**, exactly like the array version never touched `top` on a read — same principle, different mechanism.
- **Popping all the way to empty:** narrate the pop pseudocode mapped onto ALS Activity 1's fix — `Node* temp = top` (save first), `top = top->next` (move), `delete temp` (then clean up). *"Notice there was never a moment where a push could fail. There was no capacity to run out of."*
- **Advantages, read as a list students should recite:** dynamic size, efficient memory use (only allocate what you use), no fixed-capacity overflow, simple pointer rewrites with no shifting of other elements.
- **"No overflow" doesn't mean "cannot fail."** There's no `capacity - 1` check anywhere in this implementation — but `new Node(x)` still asks the operating system for memory. If the system is genuinely out of memory, that allocation fails. **This is not the same claim as "infinite."**
- **Complexity table:** push, pop, top, empty all O(1) — same headline result as Session 18's array version, achieved by completely different plumbing. **The real tradeoff, not mentioned in the deck's Advantages slide:** per-node pointer memory overhead (each node stores a pointer in addition to the data) and worse cache locality than a contiguous array — say this explicitly, since the deck presents advantages without a matched disadvantages slide.

**Checkpoint (at 34 min)** — show of hands:
> *"True or false: a linked-list stack can never fail to push, under any circumstances."*
> **Answer:** False — it can't overflow the way an array does, but a push can still fail if the system is out of memory to allocate a new node. "No overflow" means no *fixed-capacity* overflow, not "infinite."

---

## ⚡ ALS Activity 2 — Spot the Bug: Delete Before You Move (34–41 min)

**ALS format:** Spot the Bug — exposes the exact ordering bug ALS Activity 1's debrief warned about: deleting the old top node before reassigning `top` away from it. Chosen as the closing activity because this is the linked-list stack's single most dangerous silent failure mode.

**Setup line:**
> *"Here's a `pop()` with its two steps swapped. Tell me exactly what breaks, and why."*

```cpp
void pop() {
    if (empty()) return;
    delete top;          // BUG: top is deleted first
    top = top->next;     // top is now a dangling pointer — reading top->next is undefined behavior
}
```

30 seconds silent, then hands up.

**Answer:** `delete top` frees the memory the node occupied. The very next line then tries to read `top->next` — but `top` no longer points to valid memory. This is **undefined behaviour**: it might crash, might silently return garbage, might appear to "work" during testing and fail later. The fix is to save `top->next` (or a temp pointer to the old node) *before* deleting.

**How it surfaces:** Ask: *"Why might this bug pass your test cases and still be wrong?"* Expect: undefined behaviour sometimes happens to produce the "right" answer by luck, which is worse than an obvious crash because it hides the bug.

**Debrief line:**
> *"This is the pointer version of Session 18's missing overflow guard — a one-line reordering that turns working code into a landmine. Always capture what you need from a node before you free it, never after."*

**Cut rule:** Skip the "why might it pass tests" discussion and move straight from the bug identification to the debrief line.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering the push/pop ordering rules and the "no fixed-capacity overflow" distinction. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> An empty linked-list stack (`top = null`). Draw or write out the chain after: `push(4)`, `push(9)`, `pop()`, `push(2)`.
> **Answer:** `push(4)` → `top → 4`. `push(9)` → `top → 9 → 4`. `pop()` → `top → 4` (9 is discarded). `push(2)` → `top → 2 → 4`.

**Homework:** Re-draw the exit-ticket chain from memory, then extend it with two more operations of your choice and trace `top` by hand.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Push order is create → update top → link next | Students port over the array stack's "increment first" instinct without realising the object being updated is different here | Slide Block A's explicit 3-step narration, repeated for every push in the dry run |
| `top->next` after several pushes points to the *oldest* element | "Next" sounds forward-moving, like it should lead deeper into the list in insertion order | The checkpoint at minute 18 — showing `top->next->next` reaches backward through push history |
| A linked-list stack can never fail under any circumstances | The Advantages slide literally says "No Overflow" | Slide Block B's checkpoint — distinguishing "no fixed-capacity overflow" from "infinite memory" |
| `pop()` just "removes the top node," order doesn't matter | Push/pop feel like single atomic actions in everyday language | ALS Activity 2's Spot the Bug — showing the exact crash/undefined-behaviour caused by deleting before reassigning `top` |
| A linked-list stack is strictly better than an array stack because it "never overflows" | The session frames overflow as a weakness of arrays without weighing the tradeoff | Slide Block B's explicit reminder of per-node pointer memory overhead and cache locality |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Merged from two original sessions ("Stack Implementation Using Linked List" Parts 1 and 2, 33 + 37 min = 70 min) into one 50-min session — see `sem-3-sequence.md`.
- **Two ALS activities this session, both carried over directly:** Activity 1 is the Live Coding / Dry-Run Relay (three-step push order), Activity 2 is Spot the Bug (delete-before-move on pop). Both were already the load-bearing activities in the original two-part session.
- **Dropped:** Part 1's "Human Chain Push/Pop" closing wrap (redundant with Activity 1, which already covers the same ordering physically via trace) and Part 2's "Predict & Discuss: Can This Ever Overflow?" (its content is folded directly into Slide Block B's checkpoint instead of running as a separate activity).
- **The Classroom Quiz now runs last, right before the Exit Ticket** — moved from its original mid-session position(s) to match the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank.
- **This is session 19 of the Sem-3 sequence** (see `sem-3-sequence.md`) — this session is structurally a mirror of Session 18, deliberately, so students can map the array and linked-list implementations onto each other operation-by-operation.
- **Resist the urge to declare a "winner" between array and linked-list stacks.** State the tradeoff explicitly in Slide Block B: per-node pointer overhead and worse cache locality versus no hard capacity ceiling — both are real costs and benefits, not a strict improvement.
- **The three-step push ordering (Slide Block A / ALS Activity 1) and the pop-ordering bug (ALS Activity 2) are this session's two highest-value ideas.** If time is short, protect both over the pop-to-empty dry run narration in Slide Block B — narrate the first 2-3 pops fully, then accelerate through the rest.
