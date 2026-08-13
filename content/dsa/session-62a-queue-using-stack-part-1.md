# Session 62a — Queue Using Stack (Two Stacks) (Part 1 of 2)

**Duration** 32 min · **Topic** Stack & Queue — Queue Using Two Stacks: Approach 1 (Eager Transfer) · **Prerequisite** Session 61 — Stack Using Queue · **Session type** Concept lecture

<!-- Split note: original session-62 ran 50 min. Split right after the Classroom Quiz. Part 1 covers the problem framing (and its mirror-image relationship to Session 61), and Approach 1 — transfer on every push — with its full dry run. Part 2 (session-62b) covers Approach 2 (lazy transfer) and the workload-dependent trade-off discussion, and closes the Stack & Queue block. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Queue using two stacks | https://docs.google.com/presentation/d/1uYLbuFpzop3rCEcTbGBz38-ebPHFkdv9UhXjyTyXXBo/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the constraint of this problem — build a queue's FIFO behaviour using only two stacks — and explicitly distinguish it from Session 61's mirror-image problem. *(REMEMBERING)*
2. Explain Approach 1: transfer between stacks on every `push`, so the oldest element is always ready at the top. *(UNDERSTANDING)*
3. Trace Approach 1 on a given operation sequence. *(APPLYING)*

*(Approach 2 — lazy transfer — and the workload trade-off discussion are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 61 (Stack Using Queue) (0–6 min)

Say: *"Six on Stack Using Queue — and pay close attention to the names today, because this session is its mirror image."*

**Q1.** In Session 61's Stack-using-Queue, what happens on every `push`?
`A` Nothing extra — direct enqueue · `B` The queue rotates so the new element reaches the front · `C` The queue is sorted · `D` Two queues are merged

**Q2.** In that implementation, `pop()` and `top()` run in:
`A` O(1) · `B` O(N) · `C` O(N²) · `D` O(log N)
→ *Read:* A. If this misses, restate it in one line — today's problem does the *same kind* of trade-off analysis, just with the costly and cheap operations swapped.

**Q3.** In that implementation, `push()` runs in:
`A` O(1) · `B` O(N) · `C` O(N²) · `D` O(log N)

**Q4.** The number of rotations on a given `push` equals:
`A` A fixed constant · `B` The number of elements already in the queue before this push · `C` The total capacity · `D` Always zero

**Q5.** The core lesson of Session 61 was:
`A` Queues are strictly better than stacks · `B` Simulating one structure with another moves the cost somewhere, it doesn't remove it · `C` Rotation is always free · `D` Stacks can't be simulated at all

**Q6 (MSQ — pick all correct).** Which are true of Session 61's approach?
`A` It uses exactly one queue · `B` The most recently pushed element ends up at the front of the queue · `C` It requires two separate queues · `D` `pop` and `top` never need to rotate

**Running it** — poll tool, ~25 s per question. Total 6 min including reads.

---

## Hook (6–9 min)

Say: *"Last session, one queue pretending to be a stack. Today, exactly the reverse: two stacks pretending to be a queue. Same spirit, opposite direction — and I want you to notice, by the end, that the exact same trade-off shows up again, just pointed the other way."*

Ask: *"With only `push` and `pop` available on a stack — LIFO — how would you ever get FIFO order out of it, using just stacks?"*

Let a guess or two land (often: "reverse it somehow"). Then:

> *"'Reverse it' is exactly right, and that's literally what a second stack does — popping everything off one stack and pushing it onto another flips the order. The only real decision left is *when* you do that flip: every single push, or only when you actually need to read the front? That single decision is the whole session — today's Part 1 does it eagerly, Part 2 does it lazily."*

---

## Slide Block A (9–17 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 3–8: Introduction, Basic Operations, Approach 1 -->
Covers: Introduction (simulate FIFO queue behaviour using two LIFO stacks) → Basic Operations (`push`, `pop`, `front`, `back`, `size`, `empty`) → Approach 1: on every `push`, transfer all of `stk1` into `stk2`, push the new element onto `stk1`, then transfer everything back from `stk2` into `stk1`.

**Beats to emphasise**

- Say the two-stack roles plainly: "one stack briefly becomes a scratch space during the shuffle — neither stack is permanently 'the queue,' the roles swap temporarily on every operation in this approach."
- **State the mechanism as one sentence:** "moving everything to `stk2` and back, around the new element, re-sorts `stk1` so the oldest element ends up on top every single time — ready for an O(1) `pop` or `front`."
- Preview honestly: "this makes every `push` expensive — proportional to however many elements are already there — precisely so that `pop` and `front` stay cheap. Sound familiar?" (Bridge explicitly to Session 61's mirrored trade-off.)

**Checkpoint (at 17 min)** — cold-call:
> *"In Approach 1, after a `push` finishes, which element sits on top of `stk1` — the newest or the oldest?"*
> **Answer:** The oldest — the double-transfer specifically re-sorts the stack so the front of the queue is always immediately accessible.

---

## Slide Block B1 (17–24 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 9–34: Dry Run of push(1), push(2), push(3), front(), pop(), push(4); Pseudocode, Complexity, Code -->
Covers: Full dry run of `push(1), push(2), push(3), front(), pop(), push(4)` using Approach 1, showing the transfer-shuffle on every push → pseudocode → complexity (`push`: O(N); `pop`, `front`: O(1); `size`, `empty`: O(1)) → code.

**Beats to emphasise**

- Narrate `push(2)` exactly as the deck does: `stk1 = [1]`. Move `1` to `stk2` → `stk2 = [1]`. Push `2` onto `stk1` → `stk1 = [2]`. Move everything back from `stk2` to `stk1` → `stk1 = [2, 1]`, with `1` now on top.
- Continue to `push(3)`: move `2, 1` to `stk2` (in that pop order) → walk the actual order carefully on the board, since this is where students lose track fastest. End state: `stk1 = [3, 2, 1]` top-to-bottom order such that `1` (the oldest) is on top.
- `front()` and `pop()` are then trivial: just read or remove `stk1`'s top, which the shuffling guaranteed is always the oldest element.

**Checkpoint (at 24 min)** — cold-call:
> *"Why does `front()` never need to touch `stk2` at all in this approach?"*
> **Answer:** Because `push`'s double-transfer already re-sorted `stk1` so the oldest (front) element is always sitting right on top — `front()` and `pop()` just read it directly, with no shuffling of their own.

---

## Classroom Quiz (24–29 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Turn-and-Teach (29–32 min)

**Why this strategy here:** the double-transfer is genuinely the most fiddly mechanical step in this session, and explaining it out loud to a partner — without the board — is a stronger test than one more silent trace.

**Run it (3 minutes):**
> *"Turn to your partner. Explain, without drawing anything, why `push` in Approach 1 moves elements to `stk2` and then ALL THE WAY BACK, instead of just leaving them on `stk2`. Partner checks: did you say why the oldest element ends up on top?"*

Cold-call one pair to report their explanation.

> *"That double-move is the whole cost of Approach 1. Part 2 shows you a version that skips it most of the time — and asks you to figure out exactly when that trade pays off."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Session 61 (Stack Using Queue) and Session 62 (Queue Using Stack) are the same problem with different names | Both involve simulating one structure with the opposite structure, and the names are easy to skim past | Restating both problems' directions clearly in the Hook, and again at the Part 1 Wrap |
| Both stacks in Approach 1 permanently hold "half the queue" | The shuffle moves things back and forth, which can look like a stable split | Point out `stk2` is always empty again by the end of every `push` — it's scratch space, not a permanent second half |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split right after the Classroom Quiz.**
- **The single biggest risk across both parts is students conflating this with Session 61.** Say the distinction out loud at least three times across the two parts: in the Hook, at this Part 1 Wrap, and again in Part 2's Exit Ticket.
- **Walk Approach 1's dry run carefully, on the board, not just narrated.** The double-transfer (there and back) is genuinely easy to lose track of verbally; write out `stk1` and `stk2`'s contents at every single sub-step during Slide Block B1.
