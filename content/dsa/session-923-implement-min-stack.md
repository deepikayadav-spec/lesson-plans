# Session 23 — Implement Min Stack

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Stack — Min Stack (Pair-Stack Approach & Space-Optimised Encoding) · **Prerequisite** Session 22 — Infix, Prefix, and Postfix Notations
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Implement Min Stack | https://docs.google.com/presentation/d/1zvk5bu2qxqDY8Ccnd6i09yAhnaLxxM04Ge0MYChq9pw/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the Min Stack requirement: `push`, `pop`, `top`, and `getMin` must all run in O(1) time. *(REMEMBERING)*
2. Explain the pair-stack approach — storing `(value, currentMinAtThatPoint)` at every level — and why popping it automatically restores the previous minimum. *(UNDERSTANDING)*
3. Trace the pair-stack approach on a given input sequence. *(APPLYING)*
4. Trace the space-optimised single-stack encoded-value approach, including decoding a sentinel value on pop. *(APPLYING)*
5. Analyse why the encoded-value approach still achieves O(1) per operation while cutting space from O(2n) to O(n). *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 22 (3–7 min) · ALS: Polling

5 questions on **Session 22 (Infix, Prefix, Postfix)**. ~45 s each, project the distribution, never name individuals.

**Q1.** In the infix-to-postfix algorithm, when does a `(` on the stack get popped to the output?
`A` Never — it's discarded when matched, not popped to output · `B` At the very end · `C` Immediately after being pushed · `D` Whenever an operand appears
→ **A.**

**Q2.** The rule for popping operators during conversion is: pop while the stack top has ___ precedence than the incoming operator.
`A` Lower · `B` Higher or equal · `C` Equal only · `D` Any
→ **B.**

**Q3.** Which operator in the precedence table is right-to-left associative?
`A` `+` · `B` `-` · `C` `*` · `D` `^`
→ **D.**

**Q4.** Why does `/` NOT get popped when `^` arrives, in the worked example?
`A` `/` has higher precedence · `B` `^` has higher precedence than `/`, so nothing pops · `C` They're never compared · `D` `/` was already removed
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about postfix notation?
`A` Never needs parentheses · `B` The operator comes after its operands · `C` It's the same as prefix, just reversed · `D` It can be evaluated left to right, firing an operator the moment both operands are ready
→ **A, B, D.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Put this on the board:

> *"You're tracking stock prices as they come in, one at a time, and pushing each new one. At any moment, someone can ask you: 'what's the lowest price we've seen so far?' You need to answer instantly — not by scanning the whole list of prices every time."*

Ask: *"If I just kept a plain stack of prices, how would you answer 'what's the minimum' right now?"*

Let a student say "scan the whole stack."

> *"That's O(n) every single time someone asks. Today we build a stack that answers 'what's the minimum right now' in O(1) — constant time, no matter how many prices are in it — without breaking `push`, `pop`, or `top`. Two different ways to do it, same result."*

---

## Slide Block A (10–15 min) — DELIVER SLIDES AS-IS

Covers: Problem Statement (`MinStack()`, `push(x)`, `pop()`, `top()`, `getMin()`, all O(1)) → two worked examples showing expected output sequences → Approach 1: store `(value, minSoFar)` pairs.

**Beats to emphasise**

- Read the operation list: `push`, `pop`, `top`, `getMin` — all four, O(1), no exceptions. This is the whole spec.
- **Approach 1's core idea, in one sentence:** "Every time you push, you also push what the minimum would be *including* this new element — so the minimum is always sitting right at the top, no digging required."

**Checkpoint (at 15 min)** — cold-call:
> *"If I push a pair `(x, m)`, what does that second value `m` actually represent?"*
> **Answer:** The minimum of the entire stack *including* `x`, at the moment `x` was pushed — not just `x` itself.

---

## Slide Block B1 (15–21 min) — DELIVER SLIDES AS-IS

Covers: Full dry run of `["push -5", "push 1", "getMin", "push -10", "getMin", "pop", "top", "getMin"]` using pairs, then pseudocode, complexity (all O(1) time; O(2n) space), and code.

**Beats to emphasise**

- Narrate every push as a pair decision: push `-5` → stack empty → pair `(-5, -5)`. Push `1` → compare `1` vs current min `-5` → `1 > -5` so min stays `-5` → pair `(1, -5)`. Push `-10` → compare vs `-5` → `-10 < -5` → new min `-10` → pair `(-10, -10)`.
- On `pop()`: remove the top pair entirely. *"The previous minimum comes back for free, because it was sitting one level down the whole time."*
- Space cost: **O(2n)**, because every single element carries a second integer alongside it.

**Checkpoint (at 21 min)** — show hands:
> *"After popping the pair `(-10, -10)`, what does `getMin()` return?"*
> **Answer:** `-5` — the pair `(1, -5)` is now on top, and its stored minimum is `-5`.

---

## ⚡ ALS Activity 1 — Guided Table Build: Trace the Pair Stack (21–27 min)

**ALS format:** Guided Table Build — the class builds a pair-stack trace on a fresh sequence, column by column, cold-called for each pair. Chosen right after Slide Block B1 because Approach 1 needs to be genuinely fluent in students' hands before Approach 2 asks them to abandon the safety of storing two full values per element.

**Setup line:**
> *"New sequence: `push(3), push(1), push(4), pop(), getMin()`. I point at a step, you give me the pair — both numbers — before I confirm."*

**The completed trace**

| Step | Operation | Stack (bottom → top) | `getMin()` if called |
|---|---|---|---|
| 1 | `push(3)` | `(3,3)` | 3 |
| 2 | `push(1)` | `(3,3), (1,1)` | 1 |
| 3 | `push(4)` | `(3,3), (1,1), (4,1)` | 1 |
| 4 | `pop()` | `(3,3), (1,1)` | — |
| 5 | `getMin()` | `(3,3), (1,1)` | **1** |

**How it surfaces:** At step 3, ask before revealing: *"Is `4`'s stored minimum `4` or `1`?"* — the trap is treating the second value as "this element's own value" instead of "the running minimum including it." At step 5, confirm the popped `4` never affected the minimum at all, since `1` was always smaller.

**Debrief line:**
> *"Every single pair carries the full answer for that level. That redundancy is exactly what Approach 2 is about to try to remove — hold onto how *safe* this feels, because the next approach trades some of that safety for space."*

**Cut rule:** Skip step 3's full pair reveal and state it directly; keep steps 1, 2, 4, 5.

---

## Slide Block B2 (27–36 min) — DELIVER SLIDES AS-IS

Covers: Approach 2 — one stack, one `mini` variable. When pushing a value smaller than `mini`, push an **encoded** value (`2×x − oldMini`) instead of `x`, and update `mini = x`. On pop, if the popped value is *less than* `mini`, it was an encoding — decode the old minimum as `2×mini − poppedValue` before restoring.

**Beats to emphasise**

- **This is the harder half of the session — go slower here than the pacing looks like it allows.**
- Walk the deck's own dry run: `push(-5)` → stack empty → push `-5` directly, `mini = -5`. `push(1)` → `1 > -5` → push `1` directly, `mini` unchanged. `push(-10)` → `-10 < -5` → push the **encoded** value `2×(-10) − (-5) = -15`, update `mini = -10`.
- **Say this explicitly, it's the crux:** "`-15` sitting on the stack is not a real element of this Min Stack. It's a flag that means 'the real minimum just changed, and the old one was `-5`.'"
- On `pop()` of that `-15`: since `-15 < mini (-10)`, it's an encoding. Decode: `mini = 2×(-10) − (-15) = -5`. The old minimum is restored, and the encoded value itself is discarded — it was never a real stack element.
- **Write both formulas on the board and leave them up:** push-encode `2x − mini`; pop-decode `2·mini − encoded`. Mirror images, opposite directions.

**Checkpoint (at 36 min)** — cold-call:
> *"How does `pop()` know whether the value it just removed was a real element or an encoded sentinel?"*
> **Answer:** Compare it to the current `mini` — if the popped value is *less than* `mini`, it was an encoding (a real element can never be smaller than the tracked minimum); otherwise it's a genuine value.

---

## ⚡ ALS Activity 2 — Spot the Bug: Decode It Yourself (36–41 min)

**ALS format:** Spot the Bug / Predict-the-Output — exposes whether students actually understand the decode formula, versus having just watched it happen once. Chosen as the closing activity because mixing up the push and pop formulas is the single most error-prone step in the whole session.

**Setup line:**
> *"Stack currently holds an encoded value of `-21` on top, and `mini` is currently `-8`. I'm about to `pop()`. Before I show you the arithmetic: is `-21` a real element or an encoding? And if it's an encoding, what does `mini` become after the pop?"*

30 seconds silent, then hands up.

**Answer:** `-21 < mini (-8)` → it's an encoding. Decode: `mini_new = 2 × mini_old − poppedValue = 2×(-8) − (-21) = -16 + 21 = 5`.

**How it surfaces:** The most common wrong move is applying the *push* formula (`2×x − mini`) instead of the *pop/decode* formula (`2×mini − encodedValue`) — same two numbers, opposite arrangement. Point at the two formulas already on the board and have students say out loud which one is "going in" (push) and which is "coming out" (pop).

**Debrief line:**
> *"Two formulas, mirror images of each other. Push encodes: `2x − mini`. Pop decodes: `2·mini − encoded`. Mix them up and you get a number that looks plausible and is completely wrong — which is exactly why this bug is dangerous."*

**Cut rule:** Skip having students compute the decode by hand and instead just verify the answer already worked out above, spending the saved time re-stating the two-formula distinction once more.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering both approaches, their space complexities, and the encode/decode formulas. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> In one sentence: why does the encoded-value approach (Approach 2) use less space than the pair-stack approach (Approach 1)?
> **Answer:** Approach 1 stores two integers per element always (O(2n) space); Approach 2 stores exactly one integer per element — a real value most of the time, an encoded sentinel only when a new minimum is set — so it stays O(n).

**Homework:** Trace Approach 2 by hand on `push(4), push(4), push(1), push(3), pop(), getMin()`.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A new pair is only needed when the minimum actually changes | Feels wasteful to "do work" when nothing changed | ALS Activity 1 — every push gets a pair, even when the minimum doesn't change, which is what keeps `getMin()` O(1) at every single level |
| An encoded value on the stack is a real, usable element | It sits in the same stack, looks like just another number | ALS Activity 2's decode exercise — explicitly naming `-21` as a sentinel, not data, before showing the arithmetic |
| The push-encode formula and the pop-decode formula are interchangeable | Both involve `2 × mini` and one other value, so they look structurally identical | The two formulas written side by side and left on the board throughout Slide Block B2 and ALS Activity 2 |
| Approach 2 saves space by not tracking history at all | The single `mini` variable looks like the *only* thing being tracked | Point out the encoded values *are* the hidden history — stored inline instead of in a second array |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Merged from two original sessions ("Min Stack" Parts 1 and 2, 32 + 28 min = 60 min) into one 50-min session — see `sem-3-sequence.md`.
- **Two ALS activities this session:** Activity 1 is a new Guided Table Build (tracing Approach 1 on a fresh sequence — the original Part 1 had no dedicated activity for the pair-stack approach itself, only lecture), Activity 2 is Spot the Bug (Decode It Yourself), carried over directly from the original since it's the load-bearing check for the hardest idea in the session. The original Part 1 "Predict-and-Defend Pairs" wrap is dropped in favor of the more substantive guided trace.
- **The Classroom Quiz now runs last, right before the Exit Ticket** — moved from its original mid-session position to match the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank.
- **This is session 23 of the Sem-3 sequence** (see `sem-3-sequence.md`).
- **Approach 1 is not a "wrong" answer to be discarded** — frame it as the natural first idea (more space, simpler to reason about), with Approach 2 as the space-optimised refinement. Both are legitimate; interviewers accept either unless O(n) space is explicitly required.
- **Slide Block B2's encode/decode logic is the hardest single idea in the Stack block so far.** If behind, do not compress it — cut ALS Activity 2 down to its stated cut rule instead, or trim ALS Activity 1's step 3 per its own cut rule.
- **Have both dry-run sequences ready before class** (`[-5, 1, -10, ...]` for the deck's own trace, `[3, 1, 4, ...]` for ALS Activity 1) so you're not improvising numbers live.
