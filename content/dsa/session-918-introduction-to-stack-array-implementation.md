# Session 18 — Introduction of Stack, Stack Implementation Using Array

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Stack — LIFO Concept, Array-Backed Implementation, Overflow/Underflow · **Prerequisite** Session 17 — Adding Two Numbers (this session opens the Stack block)
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Intro of Stack | https://docs.google.com/presentation/d/1NzAoqpub2ZvP_kjvtJT7GZGt_UL6g7oyh9ET3haxAQg/edit |
| Video + deck — Stack Implementation Using Array | https://docs.google.com/presentation/d/1yXTQK1E67BYC8PsZRrCkNhzsfsYxdd47Qa4-4N9_pG8/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the LIFO principle and explain why insertion/deletion happen only at `top`. *(REMEMBERING)*
2. Distinguish fixed-size from dynamic-size stacks and name their respective failure conditions (overflow, underflow). *(ANALYZING)*
3. Trace `push` on an array-backed stack, correctly updating `top` *before* inserting (increment-then-insert). *(APPLYING)*
4. Identify the overflow condition (`top == capacity - 1` on push) and underflow condition (`top == -1` on pop). *(ANALYZING)*
5. State that push, pop, top, empty, and size are all O(1) on an array-backed stack, and explain why. *(APPLYING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 17 (3–7 min) · ALS: Polling

5 questions on **Session 17 (Adding Two Numbers)** — the last session of the Linked List block, before this session moves to Stack. ~45 s each, project the distribution, never name individuals.

**Q1.** Why are digits stored least-significant-first in the Add Two Numbers problem?
`A` It's arbitrary · `B` It lets the algorithm add head-to-head without reversing anything · `C` It saves memory · `D` It's required by the language
→ **B.**

**Q2.** What's the correct loop condition for the digit-by-digit addition?
`A` `temp1 != null && temp2 != null` · `B` `temp1 != null || temp2 != null` · `C` `temp1 == temp2` · `D` `temp1->data == temp2->data`
→ **B.**

**Q3.** Why is the time complexity O(max(M, N)) and not O(M + N)?
`A` It's actually O(M+N) · `B` The loop runs once per position, up to the longer list's length · `C` Because of the carry · `D` Because of the dummy head
→ **B.**

**Q4.** If a leftover carry exists after both lists are exhausted, what happens?
`A` It's discarded · `B` One more node is appended with that carry value · `C` The program crashes · `D` The first node is overwritten
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about the Add Two Numbers algorithm?
`A` Carry is recomputed fresh each iteration via `sum / 10`, never manually reset · `B` A dummy head avoids a special case for the first node · `C` It requires both lists to be the same length · `D` The new node's value is `sum % 10`
→ **A, B, D.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Say: *"For the last several sessions you've been chasing pointers through nested structures — up, down, next, merge, repeat. Today's data structure has exactly one legal move."*

Physically pick up a stack of 3-4 notebooks/books from your desk. Ask: *"I want to remove the notebook second from the bottom without touching anything else. Go."*

Let them tell you it's impossible without a mess.

> *"Right. There's exactly one item you're allowed to touch — whatever's on top. That's the entire rule of a stack. No pointers to chase, no cases to handle — one end, one move. Today you learn the rule, and then you learn exactly how a plain array can be made to obey it."*

---

## Slide Block A (10–18 min) — DELIVER SLIDES AS-IS

Covers: What is a Stack (LIFO) → Stack Structure (insertion/deletion only at `top`) → Real-Life Example (stack of plates) → Operations of Stack recap table → Types of Stack (Fixed-Size vs Dynamic-Size).

**Beats to emphasise**

- **LIFO, said plainly:** "Last one in is the first one out." Use the deck's own push/pop illustration (element 1, 2, 3 going in, then 3 coming out first).
- **One end, one name.** Insertion and deletion both happen at `top` — there is no "front" and "back" the way there will be for Queue later. Students fresh off the Linked List block will want to reach for `head`/`tail` vocabulary; stop that here.
- **Plates, not abstractions.** "To get the plate at the bottom, you must remove every plate above it first." This is the sentence students should be able to repeat back.
- **Operations table** — `push`, `pop`, `top`, `empty`, `size`, all O(1). Say explicitly: "Every single operation on a stack is instant, no matter how many elements are in it."
- **Fixed vs. dynamic, in one line each:** fixed capacity → **overflow** on push-when-full. Dynamic → grows/shrinks, but not free — something resizes behind the scenes. Both terms return in a few minutes.

**Quick tie-in beat (~1 min):** *"Name one everyday thing — tech or otherwise — where the last thing you did is the first thing that gets undone."* One or two shout-outs (browser back button, Ctrl+Z, a stack of trays). *"Every 'undo' button you've ever clicked is a stack."*

**Checkpoint (at 18 min)** — cold-call two students:
> *"In one sentence: why can't I pull the second-from-top plate out of a stack of plates?"*
> **Answer:** Because a stack only exposes the top element — everything below it is inaccessible until the elements above are removed first (LIFO).

---

## ⚡ ALS Activity 1 — Live Coding / Dry-Run Relay: Call the Operations, on the Array (18–25 min)

**ALS format:** Live Coding / Dry-Run Relay — traces a sequence of stack operations while explicitly narrating the array/`top` mechanics underneath each one. Chosen right after Slide Block A because this is the bridge activity: it tests general stack-operation sequencing (push/pop/top) *and* introduces the array-specific rule — `top` starts at `-1`, and every push is **increment `top`, then insert** — in the same breath, before Slide Block B formalises it.

**Setup line:**
> *"Capacity-5 array, empty, `top = -1`. I call an operation, you tell me the new value of `top` *before* you tell me what's stored where — say it in that order every time."*

Call these out **one at a time**, taking an answer before confirming:

```
push(10)   → top: -1 → 0,  arr[0] = 10
push(20)   → top: 0 → 1,   arr[1] = 20
push(30)   → top: 1 → 2,   arr[2] = 30
top()      → returns arr[2] = 30, top unchanged (still 2)
pop()      → top: 2 → 1,   (30 is discarded — arr[2] is now stale, ignore it)
pop()      → top: 1 → 0,   (20 is discarded)
push(40)   → top: 0 → 1,   arr[1] = 40
```

**How it surfaces:** After the two `pop()` calls, ask: *"Is the old value still physically sitting in the array at index 2 and index 1?"* Correct answer: yes, but it's irrelevant — `top` says it doesn't exist anymore. Also watch for students who say `top()` "removes" the top element — immediately follow any `top()` call with "so what's the stack now — did anything change?"

**Debrief line:**
> *"The array never gets cleaned up. `top` is the only source of truth for what's 'really' in the stack. And notice the order every single time: increment `top` first, *then* insert. Get that backwards, and you either overwrite good data or read garbage."*

**Cut rule:** Drop the last `push(40)` — the increment/decrement rule is already demonstrated by the first six operations.

---

## Slide Block B (25–34 min) — DELIVER SLIDES AS-IS

Covers: Array initialisation (size 5, empty), `top = -1` → Overflow condition → `isFull` → Underflow condition → `isEmpty` → Complexity (all O(1)) → brief code walkthrough → Advantages/Disadvantages.

**Beats to emphasise**

- **Overflow, precisely:** a capacity-5 stack already at `top = 4` (full) attempts `push(80)`. Narrate: "top is already at index 4, the last valid index — there is nowhere to increment to." **`isFull` is one comparison: `top == capacity - 1`.**
- **Underflow, precisely:** popping when `top == -1` — there's nothing to decrement from. **`isEmpty` is `top == -1`** — the mirror image of `isFull`. Put both conditions on the board side by side.
- **The guard comes first, always.** `push`'s pseudocode opens with `if (top == capacity - 1) { return }` — checked *before* any increment. Same shape for `pop`: check `top == -1` before any decrement. Say this explicitly; it's the difference between a safe implementation and a corrupted one.
- **Code (C++/Python) is the same logic in two syntaxes** — point at the line-for-line correspondence to the pseudocode, don't re-teach it.
- **Advantages:** O(1) direct access via indexing, simple to implement. **Disadvantages:** fixed capacity risks overflow; resizing means allocating a new array and copying everything over — expensive.

**Checkpoint (at 34 min)** — show of hands:
> *"Capacity-5 stack, top = 4 (full). I call `isFull()` then immediately `push(100)`. What does each call return/do?"*
> **Answer:** `isFull()` returns `true`. `push(100)` fails — overflow, `top` does not change, `100` is never written into the array.

---

## ⚡ ALS Activity 2 — Predict the Output: Will It Overflow? (34–41 min)

**ALS format:** Predict-the-Output — exposes whether students can tell overflow apart from a normal push using nothing but the current value of `top` and the capacity. Chosen as the closing activity because overflow/underflow recognition is the single load-bearing skill this session builds toward, and it needs a fast, repeated drill to become reflexive.

**Setup line:**
> *"Capacity-5 stack. I'm going to describe its current state, then propose an operation. Before I tell you what happens, thumbs up for 'succeeds,' thumbs down for 'overflow' or 'underflow.'"*

Run these **one at a time**:

1. Stack holds `[10, 20, 40, 60]`, `top = 3`. Propose: `push(70)`. → **Succeeds** (`top` becomes 4, the last valid index).
2. Stack holds `[10, 20, 40, 60, 70]`, `top = 4`. Propose: `push(80)`. → **Overflow.** `top` is already at `capacity - 1 = 4`; there's no room.
3. Stack holds `[10, 20, 40, 60, 70]`, `top = 4`. Propose: `pop()`. → **Succeeds** (`top` becomes 3, `70` is discarded).
4. Stack holds `[]`, `top = -1`. Propose: `pop()`. → **Underflow.** Nothing to remove.

**How it surfaces:** For case 2, ask someone to state *why* in one sentence before confirming — "top is at the last index, capacity 5 means valid indices are 0 to 4, there's no index 5." Case 4 gets the same treatment for underflow. Common wrong answer: confusing `top = capacity - 1` (full) with `top = capacity` (which would be out-of-bounds and never legitimately occurs if the guard works).

**Debrief line:**
> *"Overflow and underflow are the same guard, mirrored: one checks you're not past the top of the array, the other checks you're not past the bottom of the stack's contents. Both are a single `if` statement, checked *before* the pointer moves — never after."*

**Cut rule:** Run cases 2 and 4 only — those are the two failure modes.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering LIFO/top-only access, the increment-then-insert rule, and overflow/underflow conditions. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> Capacity-3 stack, empty (`top = -1`). Write out `top`'s value after each of these calls, in order: `push(5)`, `push(9)`, `push(2)`, `push(7)`.
> **Answer:** `0, 1, 2, ` — the fourth `push(7)` **overflows** and `top` stays at 2 (capacity is 3, valid indices 0–2, already full).

**Homework:** Re-attempt today's live-trace and predict-the-output sequences from memory, on paper.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A stack has a "front" and "back" like the linked lists just studied | Fresh off the Linked List block, where head/tail vocabulary dominated | Slide Block A — a stack has exactly one active end: `top` |
| `pop()` clears/zeroes the array slot it removed | "Removing" sounds like it should erase data | ALS Activity 1's debrief — the old value is still physically there, just unreachable |
| Push inserts first, then increments `top` | "Push adds an element" sounds like the add happens before any bookkeeping | Narrating every push as "increment, *then* insert," in that fixed order, every time |
| Overflow means the array itself is out of memory | "Overflow" sounds like a memory-level failure | Precisely defining it as `top == capacity - 1` — a logical full stack, not a hardware limit |
| A missing overflow guard just "does nothing" safely | Assuming unchecked code degrades gracefully | State plainly: an unguarded `push` on a full array writes out of bounds — a crash in some languages, silent memory corruption in others |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Merged from three original sessions — "Intro of Stack" (45 min) plus "Stack Implementation Using Array" Parts 1 and 2 (33 + 37 min = 70 min) — roughly 115 minutes of original content compressed into one 50-min session. This is the heaviest single compression in the Sem-3 sequence so far; see `sem-3-sequence.md`.
- **Two ALS activities this session:** Activity 1 merges the original "Call the Operations" trace (general stack ops) with "Increment, Then Insert" (array-specific mechanics) into one combined trace — they tested closely related skills, so merging them saves real time without losing either lesson. Activity 2 is Predict the Output (Will It Overflow?), kept close to its original form since overflow/underflow recognition is this session's highest-value idea.
- **Dropped entirely, not folded:** the original "Stacks Around You" real-world callout is reduced to a 1-minute tie-in inside Slide Block A. The original "Spot the Bug: The Missing Guard" activity (an unguarded `push` writing out of bounds) is **not run as its own activity** — its core insight ("guard checked before the pointer moves, never after") is stated directly in Slide Block B instead. If the session is running ahead of pace, this is the first thing to add back in, using the Buffer.
- **The Classroom Quiz now runs last, right before the Exit Ticket** — moved from its original mid-session position(s) to match the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank.
- **This is session 18 of the Sem-3 sequence** (see `sem-3-sequence.md`) — the first of the Stack block, following the completed Linked List block (Sessions 7-17).
- **Do not let the code slides (C++/Python) turn into a syntax lesson.** They exist to show the pseudocode translates directly into working code — a brief pointing-out, not a re-teach. Given how compressed this session already is, this is one of the easiest places to lose time without noticing.
- **Set up next session's contrast at the close, if time allows:** "Everything that made this fast — direct indexing — is also what makes it inflexible. Next session, same data structure, opposite tradeoffs: a linked list."
