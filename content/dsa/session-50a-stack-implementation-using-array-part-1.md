# Session 50a — Stack Implementation Using Array (Part 1 of 2)

**Duration** 33 min · **Topic** Stack & Queue — Array Stack: Push & the Increment Rule · **Prerequisite** Session 49 — Intro of Stack · **Session type** Concept lecture

<!-- Split note: original session-50 ran 60 min. Split right after the Classroom Quiz. Part 1 covers array/top initialization and the push dry run, drilling the increment-then-insert order. Part 2 (session-50b) covers top(), overflow/underflow, isFull/isEmpty, pseudocode/code, and advantages/disadvantages. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Stack Implementation Using Array | https://docs.google.com/presentation/d/1yXTQK1E67BYC8PsZRrCkNhzsfsYxdd47Qa4-4N9_pG8/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State that an array-based stack needs a fixed-size array plus a `top` index initialised to `-1`. *(REMEMBERING)*
2. Trace `push` on an array stack, correctly updating `top` *before* inserting. *(APPLYING)*

*(pop, overflow/underflow, isFull/isEmpty, and the pseudocode/code walkthrough are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 49 (Intro of Stack) (0–6 min)

Say: *"Seven questions on stacks before we build one for real."*

**Q1.** What ordering principle does a stack follow?
`A` FIFO · `B` LIFO · `C` Random · `D` Priority-based

**Q2.** Insertion and deletion in a stack both happen at:
`A` The front · `B` The back · `C` The top · `D` Anywhere you like
→ *Read:* If anyone says "the back," they're blending Session 49's stack with the queue they haven't met yet. Flag it and move on — Queue arrives at Session 59.

**Q3.** Which real-world example did we use to explain LIFO?
`A` A queue at a ticket counter · `B` A stack of plates · `C` A deck of shuffled cards · `D` A phone book

**Q4.** A **dynamic-size** stack, compared to a fixed-size one:
`A` Has a set capacity that never changes · `B` Automatically grows when full and can shrink when elements are removed · `C` Is always slower · `D` Cannot underflow

**Q5.** Pushing onto a fixed-size stack that is already full causes:
`A` Underflow · `B` Overflow · `C` A silent no-op, no error · `D` The stack to auto-resize

**Q6.** Popping from an empty stack causes:
`A` Underflow · `B` Overflow · `C` A silent no-op, no error · `D` The stack to auto-resize
→ *Read:* Q5 and Q6 are the two terms today's session leans on hardest — if the split isn't near-unanimous, put both words on the board before moving on.

**Q7 (MSQ — pick all correct).** Which stack operations run in O(1) time?
`A` push · `B` pop · `C` top · `D` size
→ *Read:* Correct answer is all four. This is the whole promise of today's implementation — if the array design breaks this, we've done something wrong.

**Running it** — poll tool, ~30 s per question. Total 6 min including reads.

---

## Hook (6–9 min)

Put a plain array on the board: 5 boxes, indices 0–4, all empty. Ask:

> *"An array has no built-in idea of 'top.' If all I give you is this array, how do *you* know which box holds the top of the stack?"*

Take 2-3 guesses (someone will say "the last box that isn't empty," someone else may say "check every box"). Then:

> *"Both of those work, but both are wasteful — you'd be scanning the array every single time. Today's entire implementation is one clever trick: keep a single extra number, called `top`, that always tells you exactly where the top is. Update that one number correctly, and every operation becomes instant. Get it wrong by one, and you'll either overwrite good data or read garbage. That's the whole session."*

---

## Slide Block A (9–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 4–15: Stack Introduction, Array Initialization, Top Pointer Initialization, Push Operation dry run (10, 20, 30) -->
Covers: Array-backed stack introduction → Array initialisation (size 5, empty) → `top` initialised to `-1` → Push dry run: `push(10)`, `push(20)`, `push(30)`.

**Beats to emphasise**

- **`top = -1` means empty, not "index -1 has something."** Say this explicitly — it's a sentinel value, not a real index.
- **The push sequence is always increment-then-insert, in that order.** `top = top + 1`, *then* `arr[top] = x`. Say the order out loud every single time you narrate a push in this block — this is the exact rule Activity 1 will test.
- Narrate `push(10)`: top goes from `-1` to `0`, `arr[0] = 10`. Then `push(20)`: top `0 → 1`, `arr[1] = 20`. Then `push(30)`: top `1 → 2`, `arr[2] = 30`. Three reps is enough for the rule to land before you ask students to do it themselves.

**Checkpoint (at 19 min)** — cold-call:
> *"Capacity-5 array, currently holds [10, 20, 30] with top = 2. I call push(99). What are the two things that happen, in order?"*
> **Answer:** `top` becomes 3 first, *then* `arr[3] = 99`.

---

## ⚡ Activity 1 — Live Trace: "Increment, Then Insert" (19–25 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students have internalised increment-before-insert on push, and decrement-after-inspect on pop — the exact off-by-one gap that produces real bugs in the code slides in Part 2.

**Setup line (say this):**
> *"Same capacity-5 array, starting empty, top = -1. I call an operation, you tell me the new value of `top` *before* you tell me what's stored where — say it in that order every time."*

Call these out **one at a time**, taking an answer before confirming (this continues the deck's own numeric example):

```
push(10)   → top: -1 → 0,  arr[0] = 10
push(20)   → top: 0 → 1,   arr[1] = 20
push(30)   → top: 1 → 2,   arr[2] = 30
top()      → returns arr[2] = 30, top unchanged (still 2)
pop()      → top: 2 → 1,   (30 is discarded — arr[2] is now stale, ignore it)
pop()      → top: 1 → 0,   (20 is discarded)
push(40)   → top: 0 → 1,   arr[1] = 40
push(50)   → top: 1 → 2,   arr[2] = 50
```

**How it surfaces:** After the two `pop()` calls, ask: *"Is the old value still physically sitting in the array at index 2 and index 1?"* Correct answer: yes, but it's irrelevant — `top` says it doesn't exist anymore. This is the detail students miss and it matters for the overflow discussion coming up in Part 2.

**Common wrong answer:** students say `pop()` "clears" or "deletes" the array slot. Correct it by pointing out the pseudocode never zeroes anything out — only `top` moves.

**Debrief line:**
> *"The array never gets cleaned up. `top` is the only source of truth for what's 'really' in the stack. Everything below and including `top` is live; everything above it is garbage nobody reads."*

**Cut rule:** If running short, drop the two `push` calls at the end (40, 50) — the increment/decrement rule is already demonstrated by the first six operations.

---

## Classroom Quiz (25–30 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Whiteboard Race (30–33 min)

**Why this strategy here:** increment-then-insert has to become reflexive before Part 2 introduces the failure conditions (overflow/underflow) that depend on it. A timed drill under mild pressure is the fastest way to check that reflex.

**Run it (3 minutes):**
> *"Two teams, two board halves. Capacity-4 array, empty. I call a sequence of pushes — first team to correctly write the final `top` value AND the array contents scores a point."*

Call 2-3 short sequences fast (e.g., `push(3), push(7)` → top=1, `[3,7]`). Keep score loosely.

> *"That reflex — increment first, always — is what Part 2's overflow guard depends on. Miss the order once, and the guard checks the wrong thing."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `pop()` clears/zeroes the array slot it removed | "Removing" sounds like it should erase data | Activity 1's debrief — pointing out the old value is still physically there, just unreachable because `top` moved past it |
| Push inserts first, then increments `top` | The English sentence "push adds an element" sounds like the add happens before any bookkeeping | Narrating every push in Slide Block A as "increment, *then* insert," in that fixed order, every single time |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz.**
- **Increment-before-insert is the one rule that matters most in this part.** Part 2's overflow/underflow guards, isFull/isEmpty, and the Spot-the-Bug activity are all restatements of this rule from a different angle.
- **Set up Part 2's contrast now if time allows.** Closing line for this part: "You've seen push work perfectly five times. Part 2 shows you the one time it can't — and why the code has to check before it acts, not after."
