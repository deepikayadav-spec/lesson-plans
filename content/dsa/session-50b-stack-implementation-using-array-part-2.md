# Session 50b — Stack Implementation Using Array (Part 2 of 2)

**Duration** 37 min · **Topic** Stack & Queue — Array Stack: Overflow, Underflow & Code · **Prerequisite** Session 50a — Stack Implementation Using Array, Part 1 (init, push, increment rule) · **Session type** Concept lecture

<!-- Split note: continues session-50 (original 60 min) right after the Classroom Quiz. This part covers top(), the overflow/underflow failure conditions, isFull/isEmpty, the full pseudocode/code walkthrough, and advantages/disadvantages. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Stack Implementation Using Array | https://docs.google.com/presentation/d/1yXTQK1E67BYC8PsZRrCkNhzsfsYxdd47Qa4-4N9_pG8/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Identify the overflow condition (`top == capacity - 1` on push) and the underflow condition (`top == -1` on pop) from code or a described scenario. *(ANALYZING)*
2. Implement `push`, `pop`, `top`, `empty`, `full`, and `size` as O(1) array-index operations. *(APPLYING)*
3. Weigh the advantages (direct O(1) access, simple to implement) against the disadvantages (fixed capacity, wasted memory, expensive resize) of an array-backed stack. *(EVALUATING)*

---

## Warm-Up Poll — Retrieval Practice on Session 50a (0–5 min)

Say: *"Four quick ones on push before we look at where it can fail."*

**Q1.** On an empty array stack, `top` starts at:
`A` 0 · `B` -1 · `C` capacity · `D` null
→ *Read:* B.

**Q2.** The correct order for `push` is:
`A` Insert, then increment `top` · `B` Increment `top`, then insert · `C` Order doesn't matter · `D` Decrement, then insert
→ *Read:* B — Part 1's whole focus.

**Q3.** After `pop()`, what happens to the value that was at the old `top` index?
`A` It's zeroed out · `B` It's still physically in the array, just unreachable · `C` It moves to index 0 · `D` It's copied to a backup array
→ *Read:* B.

**Q4.** In Part 1's Whiteboard Race, what was the one reflex you were drilling?
→ *Read:* Open response — reconnects to increment-first before overflow guards depend on it.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"You can push safely into space that exists. Now: what happens at the edges — a full array, or an empty one — and how the code has to check before it acts."*

---

## Slide Block B (7–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 16–55: Top Operation, continued Push dry run (40, 50, 60, 70), Overflow Condition, isFull, Pop dry run to empty, isEmpty, Underflow Condition -->
Covers: `top()` operation (read-only) → continued push dry run up to capacity → **Overflow condition** (`push(80)` on a full capacity-5 stack) → `isFull` → full pop dry run down to `top = -1` → **Underflow condition** → `isEmpty`.

**Beats to emphasise**

- **`top()` never touches `top`.** It only reads `arr[top]`. Contrast this explicitly against `pop()`, which both reads *and* decrements — this pairs directly with Part 1's Activity 1 debrief.
- **Overflow, precisely:** the deck pushes 10, 20, 40, 60, 70 into a capacity-5 stack (already at `top = 4`), then attempts `push(80)`. Narrate: "top is already at index 4, the last valid index — there is nowhere to increment to." This is the exact scenario Activity 2 will hand back to students.
- **`isFull`** is one comparison: `top == capacity - 1`. Say it as a sentence, not just a formula: "full means the top pointer has reached the last valid index."
- **Underflow, precisely:** popping when `top == -1` — there's nothing to decrement from. Narrate the full pop-down sequence from the deck (five pops in a row until the stack is empty) without skipping steps — the rhythm of "check, decrement, done" repeating five times is what makes the rule automatic.
- **`isEmpty`** is `top == -1` — the mirror image of `isFull`. Put both conditions on the board side by side.

**Checkpoint (at 19 min)** — show of hands:
> *"Capacity-5 stack, top = 4 (full). I call `isFull()` then immediately `push(100)`. What does each call return/do?"*
> **Answer:** `isFull()` returns `true`. `push(100)` fails — overflow, `top` does not change, `100` is never written into the array.

---

## ⚡ Activity 2 — Predict-the-Output: "Will It Overflow?" (19–25 min)

**Format:** Predict-the-Output · **Exposes:** whether students can tell overflow apart from a normal push using nothing but the current value of `top` and the capacity — taken directly from the deck's own overflow example.

**Setup line (say this):**
> *"Capacity-5 stack. I'm going to describe its current state, then propose an operation. Before I tell you what happens, thumbs up for 'succeeds,' thumbs down for 'overflow.'"*

Run these **one at a time** (all lifted from the deck's own dry run):

1. Stack holds `[10, 20, 40, 60]`, `top = 3`. Propose: `push(70)`. → **Succeeds** (`top` becomes 4, the last valid index).
2. Stack holds `[10, 20, 40, 60, 70]`, `top = 4`. Propose: `push(80)`. → **Overflow.** `top` is already at `capacity - 1 = 4`; there's no room.
3. Stack holds `[10, 20, 40, 60, 70]`, `top = 4`. Propose: `pop()`. → **Succeeds** (`top` becomes 3, `70` is discarded).
4. Stack holds `[]`, `top = -1`. Propose: `pop()`. → **Underflow.** Nothing to remove.

**How it surfaces:** For case 2, ask someone to state *why* in one sentence before you confirm — "top is at the last index, capacity 5 means valid indices are 0 to 4, there's no index 5." Case 4 gets the same treatment for underflow.

**Common wrong answer:** students confuse `top = capacity - 1` (full) with `top = capacity` (which would be an actual out-of-bounds index and never legitimately occurs if the guard works). Clarify: the guard's entire job is to make sure `top` never reaches `capacity`.

**Debrief line:**
> *"Overflow and underflow are just the same guard, mirrored: one checks you're not past the top of the array, the other checks you're not past the bottom of the stack's contents. Both are a single `if` statement — you'll see that in the pseudocode in a minute."*

**Cut rule:** If running short, run cases 2 and 4 only — those are the two failure modes; cases 1 and 3 are the "normal" cases already covered in Part 1.

---

## Slide Block C (25–32 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 58–77: Pseudocode (push/pop/top/empty/full/size), Complexity Analysis, C++ Code, Python Code, Advantages, Disadvantages, Key Takeaways -->
Covers: Pseudocode for `push`, `pop`, `topElement`, `empty`, `full`, `size` → Complexity table (all O(1) time and space) → C++ implementation → Python implementation → Advantages / Disadvantages → Key Takeaways.

**Beats to emphasise**

- Read the guard clauses in the pseudocode aloud exactly as written: `push` opens with `if (top == capacity - 1) { return }` — **the guard comes first**, before any increment. Same for `pop`: `if (top == -1) { return }` before any decrement. This ordering is the difference between a safe implementation and the corrupted one in Activity 3.
- The C++ and Python code (slides 64–75) are the same logic in two syntaxes — don't re-teach the algorithm, just point out the direct line-for-line correspondence to the pseudocode already covered.
- **Advantages:** O(1) direct access via indexing, genuinely simple to implement.
- **Disadvantages:** fixed capacity risks overflow; resizing an array (when you eventually need to) means allocating a new array and copying everything over — expensive; and a stack that never fills up wastes the unused capacity the whole time.

**Checkpoint (at 32 min)** — cold-call:
> *"Name one advantage and one disadvantage of implementing a stack with an array, in your own words."*
> **Answer (any reasonable phrasing):** Advantage — O(1) direct access, simple. Disadvantage — fixed capacity causes overflow, or resizing is costly.

---

## ⚡ Activity 3 — Spot the Bug: "The Missing Guard" (32–35 min)

**Format:** Spot the Bug · **Exposes:** whether students understand *why* the overflow/underflow guards exist, by seeing what breaks without them — grounded directly in the deck's own `push`/`pop` pseudocode with the guard clause deleted.

**Setup line (say this):**
> *"Here's `push`, with one line deleted. Tell me what goes wrong, and give me a concrete case where it breaks."*

Put this on screen:

```python
def push(self, num):
    self.top += 1
    self.arr[self.top] = num
    # (the capacity check that used to be here is gone)
```

**What students do:** 30 seconds silent, then hands up.

**Answer:** With a capacity-5 array (valid indices 0–4) already full (`top = 4`), calling `push(6th value)` increments `top` to `5` and then attempts `self.arr[5] = num` — an out-of-bounds write. In Python this raises an `IndexError`; in a language like C++ without bounds checking, it can silently corrupt adjacent memory instead of failing loudly.

**How it surfaces:** Ask, "Which is worse — Python's crash, or C++'s silent corruption?" Most will correctly say silent corruption is worse — you don't even get an error to tell you something went wrong.

**Debrief line:**
> *"The guard clause isn't decoration — without it, overflow doesn't just fail politely, it can write past the end of your array and corrupt whatever's sitting in memory next to it. Always check capacity before you touch the array, never after."*

**Cut rule:** If running short, skip the "which is worse" discussion and go straight from the bug identification to the debrief line.

---

## Exit Ticket (35–37 min)

> Capacity-3 stack, empty (`top = -1`). Write out `top`'s value after each of these calls, in order: `push(5)`, `push(9)`, `push(2)`, `push(7)`.
> **Answer:** `0, 1, 2, ` — the fourth `push(7)` **overflows** and `top` stays at 2 (capacity is 3, valid indices 0–2, already full).

Scan responses on the way out. If several students write `top = 3` for the last call, that's the overflow guard not sticking — reopen Session 51 with a 60-second recap of the guard-before-increment rule.

**Homework:** re-attempt the exit-ticket sequence from memory, then extend it with two more pushes and a pop, and trace `top` by hand. <!-- placement: inferred — no homework/RM/practice units exist for this course per deviation #2 -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Overflow means the array itself is out of memory | "Overflow" sounds like a memory-level failure | Precisely defining it as `top == capacity - 1` — a logical full stack, not a hardware limit |
| `isFull()`/`isEmpty()` change the stack's state | Function calls with "is" in the name still feel like actions to new programmers | Point out they only read `top` and return a boolean — nothing is written |
| A missing overflow guard just "does nothing" safely | Students assume unchecked code degrades gracefully | Activity 3 — showing the concrete out-of-bounds write and its two very different failure behaviours across languages |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz.**
- **Don't let the C++/Python code slides turn into a syntax lesson.** They're there to show the pseudocode translates directly into working code in two languages — a 90-second walkthrough, not a re-teach.
- **If you're behind by the time you reach Activity 3, cut it entirely per its cut rule** and move straight to the Exit Ticket — Slide Blocks B and C already cover the load-bearing concepts (overflow/underflow recognition, complexity, tradeoffs).
- **Set up next session's contrast now.** Closing line for this part, if time allows: "Everything that made this fast — direct indexing — is also what makes it inflexible. Next session, same data structure, opposite tradeoffs: a linked list."
