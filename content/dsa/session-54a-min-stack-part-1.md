# Session 54a — Min Stack (Part 1 of 2)

**Duration** 32 min · **Topic** Stack & Queue — Min Stack: Pair-Stack Approach · **Prerequisite** Session 53 — Monotonic Stack · **Session type** Concept lecture

<!-- Split note: original session-54 ran 50 min. Split right after the Classroom Quiz — the deck's own natural seam, since it sits right after Approach 1 (pair-stack) is fully covered and before Approach 2 (encoded single-stack) begins. Part 1 covers the problem spec and the pair-stack approach with its full dry run. Part 2 (session-54b) covers the harder, space-optimised encoded-value approach. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Implement Min Stack | https://docs.google.com/presentation/d/1zvk5bu2qxqDY8Ccnd6i09yAhnaLxxM04Ge0MYChq9pw/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the Min Stack requirement: `push`, `pop`, `top`, and `getMin` must all run in O(1) time. *(REMEMBERING)*
2. Explain the pair-stack approach — storing `(value, currentMinAtThatPoint)` at every level — and why popping it automatically restores the previous minimum. *(UNDERSTANDING)*
3. Trace the pair-stack approach on a given input sequence. *(APPLYING)*

*(The space-optimised single-stack encoded-value approach is covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 53 (Monotonic Stack) (0–6 min)

Say: *"Eight quick ones on last session's monotonic stack before we bolt a new trick onto plain stacks."*

**Q1.** A monotonically increasing stack is useful for finding:
`A` The next/previous smaller element · `B` The next/previous greater element · `C` The maximum subarray · `D` A balanced bracket sequence

**Q2.** A monotonically decreasing stack is useful for finding:
`A` The next/previous smaller element · `B` The next/previous greater element · `C` A cycle in a list · `D` A palindrome

**Q3.** For `arr = [5, 2, 8, 6, 3]`, building a monotonically increasing stack left to right, what is the final stack (bottom → top)?
`A` `[5, 2, 8, 6, 3]` · `B` `[2, 3]` · `C` `[8, 6, 3]` · `D` `[5]`
→ *Read:* B. If this misses, re-run the previous session's dry run in one sentence before moving on — today's Min Stack dry run assumes this trace is fluent.

**Q4.** The pop rule for a monotonically increasing stack is: while the top is ___ the incoming element, pop.
`A` less than · `B` greater than · `C` equal to · `D` not equal to

**Q5.** Across a full monotonic-stack build over n elements, each element is pushed and popped at most how many times?
`A` n times each · `B` Once each · `C` log n times each · `D` It depends on the array

**Q6.** What makes a monotonic stack O(n) instead of O(n²)?
`A` It uses recursion · `B` Each element is touched a bounded number of times, not compared against every other element · `C` It sorts the array first · `D` It only works on small arrays

**Q7 (MSQ — pick all correct).** Which of these are still true of a monotonic stack, same as any other stack?
`A` You only ever push/pop from the top · `B` It never stores more than one copy of an element · `C` You can peek the top without removing it · `D` It requires extra memory proportional to the array size, same as a regular stack

**Q8.** True or false: a monotonic stack changes *what* you can store in a stack, not *how* a stack works mechanically.
`A` True · `B` False
→ *Read:* True. That's the bridge into today — Min Stack is another case of "same stack mechanics, smarter idea about what you store at each level."

**Running it** — poll tool, ~25 s per question. Total 6 min including reads.

---

## Hook (6–9 min)

Put this on the board:

> *"You're tracking stock prices as they come in, one at a time, and pushing each new one. At any moment, someone can ask you: 'what's the lowest price we've seen so far?' You need to answer instantly — not by scanning the whole list of prices every time."*

Ask: *"If I just kept a plain stack of prices, how would you answer 'what's the minimum' right now?"*

Let a student say "scan the whole stack." Then:

> *"That's O(n) every single time someone asks. Today and next part we build a stack that answers 'what's the minimum right now' in O(1) — constant time, no matter how many prices are in it — without breaking `push`, `pop`, or `top`. Two different ways to do it, same result."*

---

## Slide Block A (9–18 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 4–13: Problem Statement, Examples 1 & 2, Approach 1 (pair-stack) -->
Covers: Problem Statement (`MinStack()`, `push(x)`, `pop()`, `top()`, `getMin()`, all O(1)) → two worked examples showing expected output sequences → Approach 1: store `(value, minSoFar)` pairs.

**Beats to emphasise**

- Read the operation list slowly: `push`, `pop`, `top`, `getMin` — all four, O(1), no exceptions. This is the whole spec.
- **Approach 1's core idea, said as one sentence:** "Every time you push, you also push what the minimum would be *including* this new element — so the minimum is always sitting right at the top, no digging required."
- Point at Example 1's output list (`[-5, -10, 1, -5]`) and note it's just the answers to the `getMin`/`top` calls in the order they were asked — the dry run in the next block builds exactly this.

**Checkpoint (at 18 min)** — cold-call:
> *"If I push a pair `(x, m)`, what does that second value `m` actually represent?"*
> **Answer:** The minimum of the entire stack *including* `x`, at the moment `x` was pushed — not just `x` itself.

---

## Slide Block B1 (18–24 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 14–36: Dry Run of Approach 1, Pseudocode, Complexity Analysis, Code -->
Covers: Full dry run of `str = ["push -5", "push 1", "getMin", "push -10", "getMin", "pop", "top", "getMin"]` using pairs, then pseudocode, complexity (all O(1) time; O(2n) space), and C++ code.

**Beats to emphasise**

- Narrate every push as a pair decision: push `-5` → stack empty → pair `(-5, -5)`. Push `1` → compare `1` vs current min `-5` → `1 > -5` so min stays `-5` → pair `(1, -5)`. Push `-10` → compare vs `-5` → `-10 < -5` → new min `-10` → pair `(-10, -10)`.
- On `pop()`: remove the top pair entirely. Say explicitly — *"the previous minimum comes back for free, because it was sitting one level down the whole time."*
- Flag the space cost directly from the deck: O(2n), because every single element carries a second integer alongside it.

**Checkpoint (at 24 min)** — show hands:
> *"After popping the pair `(-10, -10)`, what does `getMin()` return? Who says `-10`? Who says `-5`?"*
> **Answer:** `-5` — the pair `(1, -5)` is now on top, and its stored minimum is `-5`.

---

## Classroom Quiz (24–29 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Predict-and-Defend Pairs (29–32 min)

**Why this strategy here:** Part 2's encoded-value approach is genuinely the hardest idea in the block. Before introducing it, students should commit to a prediction about the trade-off — space vs. simplicity — so the reveal in Part 2 either confirms or corrects a stance they've publicly taken.

**Run it (3 minutes):**
> *"With your partner: Approach 1 stores two integers per element. Do you think there's a way to solve this with only ONE integer per element and still keep every operation O(1)? Agree on a yes/no and a one-sentence reason before I call on pairs."*

Take 2-3 pairs' guesses, don't confirm or deny yet.

> *"Hold onto your reasoning. Part 2 does exactly that — one stack, one extra variable, and a trick where a stored value sometimes lies about what it is."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A new pair is only needed when the minimum actually changes | Feels wasteful to "do work" when nothing changed | Point out the invariant: *every* push gets a pair, even when the minimum doesn't change — that's what keeps `getMin()` O(1) at every single level, not just some |
| `getMin()` after several pops requires re-scanning what's left | Natural instinct when "the top changed" is to assume a re-check is needed | The dry run — `getMin()` is always a direct read (the pair's second value), never a scan |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split right after the Classroom Quiz** — the deck's own natural seam between the two approaches.
- **Approach 1 is not a "wrong" answer to be discarded** — frame it as the natural first idea (more space, simpler to reason about), with Part 2's approach as the space-optimised refinement. Both are legitimate; interviewers accept either unless O(n) space is explicitly required.
- **Have the dry-run sequence ready before class** (the deck's `[-5, 1, -10, ...]`) so you're not improvising numbers live.
