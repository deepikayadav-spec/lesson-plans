# Session 51b — Stack Implementation Using Linked List (Part 2 of 2)

**Duration** 37 min · **Topic** Stack & Queue — Linked-List Stack: Pop Order, Advantages & Code · **Prerequisite** Session 51a — Stack Implementation Using Linked List, Part 1 (node structure, push order) · **Session type** Concept lecture

<!-- Split note: continues session-51 (original 60 min) right after the Classroom Quiz. This part covers top(), the correct two-step pop order (and the bug when it's reversed), advantages, the pseudocode/code walkthrough, and the "can this really never overflow" discussion. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Stack Implementation Using Linked List | https://docs.google.com/presentation/d/19LsdepePTa52TM4UqbL4G4ZMhJM1MigMvtSx_ozv9mo/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Trace `pop` (advance top → discard the old head) in the correct order. *(APPLYING)*
2. Explain why a linked-list stack has no fixed-capacity overflow condition, and what it means to say it can still fail when memory runs out. *(UNDERSTANDING)*
3. Implement `push`, `pop`, `top`, `empty`, and `size` as O(1) pointer operations. *(APPLYING)*
4. Weigh a linked-list stack's dynamic sizing and no-overflow behaviour against its per-node pointer overhead, compared to the array-based stack from Session 50. *(EVALUATING)*

---

## Warm-Up Poll — Retrieval Practice on Session 51a (0–5 min)

Say: *"Four quick ones on the push order before we look at pop's mirror image."*

**Q1.** Push's three steps, in order:
`A` Update top → create node → link next · `B` Create node → link its next to old top → update top · `C` Link next → create node → update top · `D` Order doesn't matter
→ *Read:* B.

**Q2.** After `push(10), push(20), push(30)`, what does `top->next->next` point to?
`A` null · `B` The node holding 10 · `C` The node holding 20 · `D` The node holding 30
→ *Read:* B.

**Q3.** `empty()` on a linked-list stack checks:
`A` `top == -1` · `B` `top == null` · `C` `size == capacity` · `D` `top->next == null`
→ *Read:* B.

**Q4.** In Part 1's Human Chain activity, what had to happen before a new volunteer became `top`?
→ *Read:* Open response — reconnects to "point away before you take over" before pop's mirror-image order arrives.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"Push had to link before it took over. Pop has the same discipline in reverse — and this time, getting the order wrong doesn't just misplace data, it can crash your program outright."*

---

## Slide Block B (7–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 20–56: Top() Operation, continued Push/Pop dry run (40, 50, 60), full pop-down to empty, Empty() revisited, Advantages -->
Covers: `top()` (read-only) → continued push/pop dry run (up to 60) → full pop sequence back down to an empty stack → `empty()` revisited → **Advantages**: dynamic size, efficient memory utilisation, no overflow, easy insertions/deletions.

**Beats to emphasise**

- **`top()` never touches the pointer chain**, exactly like the array version never touched `top` on a read — same principle, different mechanism. Draw the parallel explicitly.
- Narrate the deck's continuing dry run (push 40, pop, top, push 50, pop, push 60, pop, pop, pop, pop) at a brisk pace — by now students should be predicting each `top` chain themselves before you reveal it.
- **Popping all the way to empty:** walk the final few pops explicitly down to `top = null`. This is the moment to say: *"Notice there was never a moment where a push could fail. There was no capacity to run out of."*
- **Advantages, read as a list students should be able to recite:** dynamic size (grows/shrinks freely), efficient memory use (only allocate what you use), no overflow condition, and push/pop are simple pointer rewrites with no shifting of other elements.

**Checkpoint (at 19 min)** — show of hands:
> *"True or false: a linked-list stack can never fail to push, under any circumstances."*
> **Answer:** False — it can't overflow the way an array does, but a push can still fail if the system is out of memory to allocate a new node. "No overflow" means no *fixed-capacity* overflow, not "infinite."

---

## ⚡ Activity 2 — Spot the Bug: "Delete Before You Move" (19–24 min)

**Format:** Spot the Bug · **Exposes:** the exact ordering bug Part 1's Activity 1 debrief warned about — deleting the old top node before reassigning `top` away from it.

**Setup line (say this):**
> *"Here's a `pop()` with its two steps swapped. Tell me exactly what breaks, and why."*

Put this on screen:

```cpp
void pop() {
    if (empty()) return;
    delete top;          // BUG: top is deleted first
    top = top->next;     // top is now a dangling pointer — reading top->next is undefined behavior
}
```

**What students do:** 30 seconds silent, then hands up.

**Answer:** `delete top` frees the memory the node occupied. The very next line then tries to read `top->next` — but `top` no longer points to valid memory. This is **undefined behaviour**: it might crash, might silently return garbage, might appear to "work" during testing and fail later. The fix is to save `top->next` (or a temp pointer to the old node) *before* deleting.

**How it surfaces:** Ask: *"Why might this bug pass your test cases and still be wrong?"* Expect: undefined behaviour sometimes happens to produce the "right" answer by luck, which is worse than an obvious crash because it hides the bug.

**Debrief line:**
> *"This is the pointer version of Session 50's missing overflow guard — a one-line reordering that turns working code into a landmine. Always capture what you need from a node before you free it, never after."*

**Cut rule:** If running short, skip the "why might it pass tests" discussion and move straight from the bug identification to the debrief line.

---

## Slide Block C (24–31 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 57–79: Pseudocode (push/pop/top/empty/sizeOfStack), Complexity Analysis, C++ Code, Python Code, Key Takeaways -->
Covers: Pseudocode for `push`, `pop`, `top`, `empty`, `sizeOfStack` → Complexity table (all O(1)) → C++ implementation (`Node` + `Stack` classes) → Python implementation → Key Takeaways.

**Beats to emphasise**

- Read the `push` pseudocode aloud and map it directly onto Part 1's three steps: `Node* temp = new Node(x)` (step 1), `temp->next = top` (step 2), `top = temp` (step 3, plus `size++`).
- Read the `pop` pseudocode aloud and map it onto Activity 2's fix: `Node* temp = top` (save first), `top = top->next` (move), `delete temp` (then clean up) — this is the *correct* order the buggy version violated.
- C++ and Python code are the same logic in two syntaxes — a fast walkthrough, not a re-teach.
- **Complexity table:** push, pop, top, empty all O(1) time and O(1) space — same headline result as Session 50's array version, achieved by completely different plumbing.

**Checkpoint (at 31 min)** — cold-call:
> *"In the correct pop pseudocode, why does `Node* temp = top` have to come before `top = top->next`?"*
> **Answer:** Because once `top` is reassigned, the only way to reach the old node (to delete it) is through a pointer saved beforehand — otherwise it's lost or, worse, deleted while still needed.

---

## ⚡ Activity 3 — Predict & Discuss: "Can This Ever Overflow?" (31–34 min)

**Format:** Predict-the-Output / Discussion · **Exposes:** the lingering belief that "no overflow" in the Advantages slide means the structure is literally unbreakable.

**Setup line (say this):**
> *"The deck's Advantages slide says 'no overflow.' Thirty seconds — is that ever untrue? When would a push on this exact linked-list stack actually fail?"*

**What students do:** Discuss in pairs for 30 seconds, then two or three volunteers answer.

**Answer:** It's true there's no *fixed-capacity* overflow — there's no `capacity - 1` check anywhere in this implementation. But `new Node(x)` still asks the operating system for memory. If the system is genuinely out of memory, that allocation fails — which is a real-world "overflow" of a different kind (a system-level failure, not a logical one the stack code checks for).

**How it surfaces:** If students insist it truly cannot fail, ask: "What does `new` do if there's no memory left anywhere on the machine?" — steer them to the idea that "no overflow" is a claim about the *algorithm's* logic, not a guarantee about the *machine* it runs on.

**Debrief line:**
> *"'No overflow' is true at the level we're reasoning about — no arbitrary capacity limit baked into the code. It doesn't mean unlimited memory. That distinction matters every time a slide says a structure 'can't' fail."*

**Cut rule:** If running short, skip straight to the debrief line without the discussion — state the distinction directly.

---

## Exit Ticket (34–37 min)

> An empty linked-list stack (`top = null`). Draw or write out the chain after: `push(4)`, `push(9)`, `pop()`, `push(2)`.
> **Answer:** `push(4)` → `top → 4`. `push(9)` → `top → 9 → 4`. `pop()` → `top → 4` (9 is discarded). `push(2)` → `top → 2 → 4`.

Scan responses on the way out. If several students draw the chain in the wrong direction (oldest element on top), that's the "top is always the most recent" rule not sticking — reopen Session 52 with a 60-second recap.

**Homework:** re-draw the exit-ticket chain from memory, then extend it with two more operations of your choice and trace `top` by hand. <!-- placement: inferred — no homework/RM/practice units exist for this course per deviation #2 -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A linked-list stack can never fail under any circumstances | The Advantages slide literally says "No Overflow" | Activity 3 — distinguishing "no fixed-capacity overflow" from "infinite memory" |
| `pop()` just "removes the top node," order doesn't matter | Push/pop feel like single atomic actions in everyday language | Activity 2's Spot the Bug — showing the exact crash/undefined-behaviour caused by deleting before reassigning `top` |
| A linked-list stack is strictly better than an array stack because it "never overflows" | Session frames overflow as a weakness of arrays without weighing the tradeoff | Slide Block B's Advantages beat, paired with an explicit reminder of the per-node pointer memory overhead arrays don't have |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz.**
- **Resist the urge to declare a "winner" between array and linked-list stacks.** The deck presents linked-list advantages without a matched disadvantages slide (unlike Session 50, which had both) — say explicitly in Slide Block B that the tradeoff is per-node memory overhead (each node stores a pointer in addition to the data) and generally worse cache locality than a contiguous array, even though there's no hard capacity ceiling.
- **Pacing risk:** the pop-to-empty dry run in Slide Block B (roughly 25 slides in the deck) can drag if narrated at full detail. Narrate the first 2-3 pops fully, then accelerate through the rest — students have already seen the pattern from Part 1's Activity 1.
- **If you're behind by Activity 3, cut it per its cut rule** and move straight to the Exit Ticket — Activity 2 and Slide Block C already carry the load-bearing ideas (operation ordering, and what "no overflow" really means).
