# Session 20 — Introduction to Monotonic Stacks

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Stack — Monotonic Stack (Increasing & Decreasing) · **Prerequisite** Session 19 — Stack Implementation Using Linked List
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Monotonic Stack | https://docs.google.com/presentation/d/13WDE1ZfHsX0jqvbNcpwrp9SJi8etqsdYNhRL4-6-YwE/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define a monotonic stack: a stack that maintains its elements in strictly increasing or strictly decreasing order, rather than plain LIFO. *(REMEMBERING)*
2. Distinguish a monotonically **increasing** stack (useful for next/previous *smaller*) from a monotonically **decreasing** stack (useful for next/previous *greater*). *(UNDERSTANDING)*
3. Trace the conditional push/pop rule that builds an increasing or decreasing stack for a given input array. *(APPLYING)*
4. Explain why each element is pushed and popped at most once across a full run, and connect that to the O(n) efficiency this buys over a nested-loop approach. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 19 (3–7 min) · ALS: Polling

5 questions on **Session 19 (Stack Implementation Using Linked List)**. ~45 s each, project the distribution, never name individuals.

**Q1.** In a linked-list stack, what does `top` become on an empty stack?
`A` -1 · `B` 0 · `C` `null` · `D` `capacity`
→ **C.**

**Q2.** Push's three steps, in order:
`A` Update top → create node → link next · `B` Create node → link its next to old top → update top · `C` Link next → create node → update top · `D` Order doesn't matter
→ **B.**

**Q3.** In the correct `pop`, what must happen before the old top node is deleted?
`A` Nothing, delete first · `B` `top` must be reassigned first, using a saved pointer to the old node · `C` The stack must be resized · `D` A new node must be created
→ **B.**

**Q4.** True or false: "no fixed-capacity overflow" means a linked-list stack's push can never fail.
`A` True · `B` False — it can still fail if the system runs out of memory to allocate
→ **B.**

**Q5.** *(MSQ — select all that apply)* True tradeoffs of a linked-list stack vs. an array stack?
`A` Per-node pointer overhead · `B` Worse cache locality · `C` No hard capacity ceiling · `D` Slower push/pop, asymptotically
→ **A, B, C.** *(D is false — both are O(1).)*

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Write the array on the board: `[5, 2, 8, 6, 3]`. Ask:

> *"For each number, I want the closest number to its *right* that's smaller than it. Just eyeball it — shout out answers."*

Let students call out (5→2, 2→none, 8→6, 6→3, 3→none).

> *"You just did that by scanning ahead every time — for a 5-element array that's manageable. For a 100,000-element array, scanning ahead from every position is brutally slow. Today's tool solves this with a stack that only ever moves forward, and touches each element at most twice, total, for the *entire* array. That's the monotonic stack, and it's the engine behind almost every session left in this block."*

---

## Slide Block A (10–19 min) — DELIVER SLIDES AS-IS

Covers: What is a Monotonic Stack (maintains elements in increasing or decreasing order by value, not just insertion order) → conditional push/pop → the two types: Monotonically Increasing (bottom→top increasing; finds next/previous **smaller**) and Monotonically Decreasing (bottom→top decreasing; finds next/previous **greater**).

**Beats to emphasise**

- **A monotonic stack is still a stack** — you only ever push and pop at the top, same as every stack so far. What's different is the *rule* for when you pop: not "whenever the caller asks," but "whenever the incoming element would break the order you're maintaining."
- **Say the pairing explicitly, twice:** increasing stack ↔ next/previous *smaller*. Decreasing stack ↔ next/previous *greater*. This pairing is the single fact students most often invert under pressure in later sessions.
- This is a **building block**, not a problem with its own final answer — flag that explicitly: "today we practice maintaining the invariant; the next few sessions are where this invariant solves an actual problem."

**Checkpoint (at 19 min)** — cold-call:
> *"If I need the next *greater* element for every position in an array, which type of monotonic stack do I reach for — increasing or decreasing?"*
> **Answer:** Decreasing.

---

## Slide Block B1 (19–27 min) — DELIVER SLIDES AS-IS

Covers: The full push/pop dry run building a monotonically **increasing** stack on `arr = [5, 2, 8, 6, 3]`.

**Beats to emphasise**

- Narrate the rule before every step: *"While the top of the stack is greater than the incoming element, pop. Then push the incoming element."*
- Walk it exactly as the deck does: push `5` → stack `[5]`. Incoming `2`: `5 > 2` is true, pop `5`, push `2` → stack `[2]`. Incoming `8`: `2 > 8` is false, no pop, push `8` → stack `[2, 8]`. Incoming `6`: `8 > 6` is true, pop `8`, push `6` → stack `[2, 6]`. Incoming `3`: `6 > 3` is true, pop `6`, push `3` → stack `[2, 3]`.
- Say out loud after each pop: *"That element just got popped because something smaller showed up after it — which is exactly the information 'next smaller element' needs."*

**Checkpoint (at 27 min)** — cold-call:
> *"Walking through that dry run, why did `8` get popped when `6` arrived, but `2` never got popped at all?"*
> **Answer:** `8 > 6` triggers a pop (order would break), but `2` is never greater than anything that comes after it in this array, so it's never violated and stays at the bottom for the whole run.

---

## ⚡ ALS Activity 1 — Live Coding / Dry-Run Relay: You Build the Decreasing Stack (27–33 min)

**ALS format:** Live Coding / Dry-Run Relay — exposes whether students can flip the comparison direction themselves (increasing's rule uses `top > incoming`; decreasing's rule uses `top < incoming`) rather than just having watched one direction demonstrated. Chosen right after Slide Block B1 because it uses the exact same array, so predictions can be checked slide-for-slide against Slide Block B2.

**Setup line:**
> *"Same array, `[5, 2, 8, 6, 3]`. This time we're building a monotonically *decreasing* stack — bottom to top, decreasing. The rule flips: while the top of the stack is *less than* the incoming element, pop. I'll call out each number, you tell me the stack *before* I reveal it."*

Run **one number at a time**, taking a predicted stack state before confirming:

```
5   → stack empty → push 5.                         Stack: [5]
2   → top (5) < 2? No (5 is not less than 2) → push 2.   Stack: [5, 2]
8   → top (2) < 8? Yes → pop 2.
      top (5) < 8? Yes → pop 5.
      → push 8.                                      Stack: [8]
6   → top (8) < 6? No → push 6.                       Stack: [8, 6]
3   → top (6) < 3? No → push 3.                       Stack: [8, 6, 3]
```

**How it surfaces:** At the `8` step, ask before revealing: *"How many pops happen here, and why more than one?"* Correct answer: two pops (`2`, then `5`) — both violate the decreasing order relative to `8`, and the rule says keep popping *while* the condition holds, not just once. Common wrong answer: students pop only `2` (the immediate top) and stop, treating monotonic-stack popping like a single conditional check rather than a `while` loop.

**Debrief line:**
> *"Same mechanism, mirrored comparison. Increasing pops on `top > incoming`; decreasing pops on `top < incoming`. Everything else — push after popping, one element in and out at most once — is identical."*

**Cut rule:** Do only the `8` step (the one with two pops) and the debrief — that's the step carrying the whole lesson.

---

## Slide Block B2 (33–37 min) — DELIVER SLIDES AS-IS

Covers: Reveal of the decreasing-stack dry run (confirming ALS Activity 1's predictions) → side-by-side comparison of both final stacks on the same input → Key Takeaways.

**Beats to emphasise**

- Confirm the final decreasing stack matches what students just predicted: `[8, 6, 3]` bottom to top.
- Put both final stacks side by side (increasing: `[2, 3]`; decreasing: `[8, 6, 3]`) and note they're built from the *same* five numbers with only the comparison direction flipped.
- **Key Takeaways, read as a two-line summary:** increasing stack → next/previous smaller problems. Decreasing stack → next/previous greater problems.

---

## ⚡ ALS Activity 2 — Predict and Discuss: Why Not Just Check Every Pair? (37–41 min)

**ALS format:** Predict-the-Output / Discussion — exposes whether students understand *why* the monotonic stack pattern is efficient, which is the entire motivation for using it in every session that follows. Chosen as the closing activity because it's the last chance this session gets to make the O(n) claim concrete rather than asserted.

**Setup line:**
> *"For `[5, 2, 8, 6, 3]`, if I found the next smaller element for every position by checking every element to its right with a nested loop, how many comparisons, worst case? Now count: across the whole increasing-stack dry run we just did, how many times, total, was any single element pushed or popped?"*

Estimate both numbers. Nested loop: roughly n²/2 comparisons in the worst case (5 elements → up to ~10). Stack version: every element is pushed exactly once, and popped at most once — so at most `2n` stack operations total.

**How it surfaces:** If students can't see why "pushed once, popped at most once" bounds the *total* work, point back at the dry run: `8` was pushed once and popped once; `2` and `5` were each pushed once and popped once; `6` and `3` were pushed once and never popped (they're still on the stack at the end). No element is ever touched a third time.

**Debrief line:**
> *"That 'each element in, each element out, at most once' argument is the proof that this pattern is O(n) instead of O(n²) — you don't need to trust it, you can count it, and you just did."*

**Cut rule:** Skip the nested-loop comparison count and go straight to counting the stack operations, then deliver the debrief line.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering the increasing/decreasing pairing and the O(n) push/pop-once argument. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> For `arr = [4, 1, 5, 2]`, would building a monotonically **increasing** stack pop the `4` at any point? If so, when?
> **Answer:** Yes — when `1` arrives, `4 > 1` triggers a pop of `4` before `1` is pushed. (Full trace: push `4` → `[4]`; `1` arrives, pop `4`, push `1` → `[1]`; `5` arrives, `1 > 5` false, push `5` → `[1, 5]`; `2` arrives, `5 > 2` true, pop `5`, push `2` → `[1, 2]`.)

**Homework:** Trace both a monotonically increasing and a monotonically decreasing stack build on `[6, 3, 9, 2, 8]` by hand.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Popping happens once per incoming element, at most | Most everyday "if this then that" reasoning is single-shot, not looped | ALS Activity 1's `8` step — showing two pops triggered by one incoming element, driven by a `while`, not an `if` |
| Increasing stack ↔ next greater; decreasing stack ↔ next smaller (the pairing flipped) | The names "increasing"/"decreasing" describe the stack's own order, which feels intuitively backwards from what it's used to *find* | Slide Block A's explicit, twice-repeated pairing statement, plus the minute-19 checkpoint testing it directly |
| A monotonic stack finds an actual answer (like "the next smaller element for index 3") by itself | The dry run's visual focus is on stack contents, not a per-index answer array | Explicitly flagging that today builds the *mechanism* — the payoff (an actual answer array) arrives in the next few sessions |
| Building a monotonic stack costs more than a plain nested-loop scan, since there's "extra bookkeeping" | Maintaining an order feels like it should add overhead compared to "just checking everything" | ALS Activity 2 — counting total push/pop operations directly against nested-loop comparisons on the same small example |
| Elements popped off a monotonic stack are simply discarded and irrelevant | The dry run doesn't show where popped elements "go" | Note explicitly: in real problems, the moment an element is popped is exactly when you learn its answer (e.g., "next smaller/greater found") — covered concretely from the next session onward |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). This session's original 45-min version already had exactly 2 ALS activities — minimal restructuring needed beyond adding settling/buffer and moving the Classroom Quiz to the end (originally sat between Slide Block B1 and Activity 1).
- **Two ALS activities this session, both carried over directly:** Activity 1 is the Live Coding / Dry-Run Relay (building the decreasing stack), Activity 2 is Predict and Discuss (why the pattern beats a nested loop).
- **The Classroom Quiz now runs last, right before the Exit Ticket** — matching the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank.
- **This is session 20 of the Sem-3 sequence** (see `sem-3-sequence.md`) — the shortest deck in the Stack block, and the lightest session. Resist the urge to pad it with content from later sessions (Next Greater Element, Largest Rectangle) — those build directly on this one and will feel repetitive if the payoff is spoiled here.
- **The one thing worth over-teaching today is the increasing↔smaller / decreasing↔greater pairing.** Every session for the next two weeks assumes students can retrieve this instantly. If time is short anywhere else, protect the two moments that drill it: the minute-19 checkpoint and Slide Block B2's side-by-side comparison.
- **ALS Activity 1 is load-bearing** — it's the only place students actively apply the rule themselves rather than watching it applied. Do not cut it if behind; cut ALS Activity 2 first per its own cut rule.
- **Set up the next few sessions explicitly at the close:** "Next Greater Element, Asteroid Collision, Largest Rectangle in Histogram — all of the next sessions are this exact pattern wearing a different problem's clothes. If today's rule is solid, the hard part of all of them is already done."
