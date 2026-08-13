# Session 62b — Queue Using Stack (Two Stacks) (Part 2 of 2)

**Duration** 28 min · **Topic** Stack & Queue — Queue Using Two Stacks: Approach 2 (Lazy Transfer) & Trade-offs · **Prerequisite** Session 62a — Queue Using Stack, Part 1 (problem framing, Approach 1) · **Session type** Concept lecture

<!-- Split note: continues session-62 (original 50 min) right after the Classroom Quiz. This part covers Approach 2 (lazy transfer, only when needed) and the workload-dependent trade-off between the two approaches. This closes the entire Stack & Queue block. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Queue using two stacks | https://docs.google.com/presentation/d/1uYLbuFpzop3rCEcTbGBz38-ebPHFkdv9UhXjyTyXXBo/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Explain Approach 2: transfer lazily, only when needed for `pop`/`front`. *(UNDERSTANDING)*
2. Trace Approach 2 on a given operation sequence and confirm it produces results identical to Approach 1. *(APPLYING)*
3. Analyse the complexity trade-off in each approach, and decide which one suits a push-heavy workload versus a pop/front-heavy workload. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 62a (0–5 min)

Say: *"Four quick ones on Approach 1 before we build a version that skips most of that work."*

**Q1.** In Approach 1, when does the double-transfer happen?
`A` Only on the first push · `B` On every single push · `C` Only on pop · `D` Never
→ *Read:* B.

**Q2.** After Approach 1's `push` finishes, what sits on top of `stk1`?
`A` The newest element · `B` The oldest element · `C` `stk2`'s contents · `D` Nothing, it's empty
→ *Read:* B.

**Q3.** What is `push`'s time complexity in Approach 1?
`A` O(1) · `B` O(N) · `C` O(log N) · `D` O(N²)
→ *Read:* B — proportional to however many elements are already there.

**Q4.** In Part 1's Turn-and-Teach, what was the one thing your explanation had to cover?
→ *Read:* Open response — reconnects to "why the double-move" before Part 2 shows a version that mostly avoids it.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"Approach 1 pays a cost on every push, guaranteed. Watch a version that pays a bigger cost, but only sometimes — and figure out with me when that trade is actually worth it."*

---

## Slide Block B2 (7–17 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 35–63: Approach 2 (lazy transfer), Dry Run, Pseudocode, Complexity, Code, Note comparing both approaches -->
Covers: Approach 2 — `push` always goes straight onto `stk1`, no shuffling. `pop`/`front` check `stk2` first; if `stk2` is empty, transfer *everything* from `stk1` into `stk2` (reversing order), then operate on `stk2`'s top. If `stk2` already has elements, use it directly — no transfer needed.

**Beats to emphasise**

- Contrast directly with Approach 1: "Approach 1 pays the shuffle cost on every push, always. Approach 2 pays a *bigger* shuffle, but only sometimes — the moment `stk2` runs dry."
- Walk the deck's dry run: `push(1), push(2), push(3)` all go straight onto `stk1` — no work at all. Then `front()`: `stk2` is empty, so transfer everything from `stk1` (`3, 2, 1` pop order) into `stk2`, which reverses it to `[1, 2, 3]` bottom to top with `1` on top. `front()` then reads `1` directly.
- **Point at the deck's own explicit trade-off note:** "if you expect more `push` operations, favour Approach 2 (pushes stay cheap, individually). If you expect more `pop`/`front` operations, favour Approach 1 (those stay cheap, individually)." Neither approach is universally better — it depends on the workload.

**Checkpoint (at 17 min)** — cold-call:
> *"In Approach 2, once `stk2` has elements in it, does a second `front()` call right after the first one need to transfer anything again?"*
> **Answer:** No — as long as `stk2` still has elements, `front()`/`pop()` just read directly from it; the expensive transfer only happens again once `stk2` has been fully drained.

---

## ⚡ Activity 2 — Predict & Discuss: "Push-Heavy or Pop-Heavy?" (17–22 min)

**Format:** Predict-the-Output / Discussion · **Exposes:** whether students can reason about which approach fits a given workload, rather than treating "Approach 2" as a strictly better upgrade over "Approach 1."

**Setup line (say this):**
> *"Two scenarios. For each, which approach — 1 or 2 — would you pick, and why? One: a logging system that pushes thousands of events per second but only occasionally reads the oldest one. Two: a task scheduler that pushes one task, then immediately processes (`pop`s) it, over and over."*

**What students do:** Discuss in pairs for a minute, then share out.

**Answer:** Scenario 1 (push-heavy) → **Approach 2**: pushes stay O(1) individually; the expensive transfer only happens on the occasional read, and it's amortised across however many pushes preceded it. Scenario 2 (tightly interleaved push/pop) → Approach 1's guaranteed O(1) `pop`/`front` is more predictable, because Approach 2's advantage evaporates when `stk2` empties almost every time anyway.

**How it surfaces:** Push students past "just pick Approach 2, it sounds more efficient" — ask directly: *"If every single push is immediately followed by a pop, does Approach 2 still avoid doing the expensive transfer often?"* Walk through it: no — if `stk2` empties every time (because you `pop` right after each `push`), the transfer happens almost every time too, so Approach 2 loses its advantage in that specific pattern.

**Debrief line:**
> *"Neither approach is 'the right one' in general — they're two honest answers to two different questions about what your workload actually looks like. That's true of nearly every data-structure trade-off you'll meet from here on."*

**Cut rule:** If running short, cover only Scenario 1 and skip the interleaved-push-pop follow-up — the core lesson (workload shape determines the right approach) still lands from one scenario.

---

## Exit Ticket (22–25 min)

> In one sentence each: which operation is expensive in Approach 1, and which is expensive in Approach 2?
> **Answer:** Approach 1: `push` is expensive (O(N), double-transfer every time). Approach 2: `pop`/`front` are expensive *only when `stk2` is empty* (O(N) then, O(1) otherwise).

**Also confirm out loud, as a naming check:** *"Quick gut check — Session 61 built a ___ using a ___. Today we built a ___ using ___."* (Answers: a Stack, using a Queue; a Queue, using two Stacks.)

**Homework:** trace Approach 2 on `push(A), push(B), pop(), push(C), front(), pop(), pop()` by hand, tracking both stacks throughout. <!-- placement: inferred — no homework/RM/practice units exist for this course per deviation #2 -->

---

## Closing — This Closes the Stack & Queue Block (25–28 min)

Say, as a one-line retrospective: *"Two sessions ago, four different problems all reduced to 'maintain one invariant with a stack' — Monotonic Stack → Next Greater Element → Asteroid Collision → Largest Rectangle. The last two sessions were the reverse move — using one structure to *simulate* the other entirely, and paying for it somewhere specific each time."*

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Approach 2 is strictly better than Approach 1 since it "delays" the expensive work | "Delaying" sounds like avoiding, not just postponing | Activity 2 — the interleaved push/pop scenario, where Approach 2's delay buys nothing if `stk2` empties every time anyway |
| In Approach 2, the transfer from `stk1` to `stk2` happens on every `pop`/`front` call | Natural to assume "the expensive step" runs every time an expensive-sounding operation is called | Slide Block B2's checkpoint — the transfer only happens when `stk2` is empty; repeated calls afterward are O(1) |
| Choosing between Approach 1 and Approach 2 is arbitrary since both are "O(N) somewhere" | Surface-level reading stops once both are confirmed to have an O(N) operation somewhere | Activity 2 — the workload-shape reasoning is the actual decision criterion, not just spotting that an O(N) exists |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split right after the Classroom Quiz, and the final session of the Stack & Queue block.**
- **Activity 2 is the load-bearing activity of this part, more than the mechanical trace.** The workload-dependent trade-off is the actual point of covering two approaches at all; don't let it get cut if time is short — cut nothing else first.
