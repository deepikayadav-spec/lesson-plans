# Session 54b — Min Stack (Part 2 of 2)

**Duration** 28 min · **Topic** Stack & Queue — Min Stack: Encoded Single-Stack Approach · **Prerequisite** Session 54a — Min Stack, Part 1 (problem spec, pair-stack approach) · **Session type** Concept lecture

<!-- Split note: continues session-54 (original 50 min) right after the Classroom Quiz. This part covers Approach 2 — the space-optimised single-stack encoded-value trick — which is the hardest single idea in the Stack & Queue block. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Implement Min Stack | https://docs.google.com/presentation/d/1zvk5bu2qxqDY8Ccnd6i09yAhnaLxxM04Ge0MYChq9pw/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Trace the single-stack encoded-value approach on a given input sequence. *(APPLYING)*
2. Analyse why the encoded-value approach still achieves O(1) per operation while cutting space from O(2n) to O(n), and decode an encoded sentinel value by hand. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 54a (0–5 min)

Say: *"Four quick ones on the pair-stack approach before we try to do it with half the memory."*

**Q1.** In Approach 1, what does the second value of each pushed pair represent?
`A` The element's own value, duplicated · `B` The minimum of the whole stack including this element · `C` The index of this element · `D` The previous element's value
→ *Read:* B.

**Q2.** What is Approach 1's space complexity?
`A` O(1) · `B` O(n) · `C` O(2n) · `D` O(n²)
→ *Read:* C — two integers per element.

**Q3.** On `pop()` in Approach 1, how does the previous minimum get restored?
`A` It's recomputed by scanning · `B` It was already sitting in the pair one level down, exposed automatically · `C` It's looked up in a separate array · `D` It can't be restored
→ *Read:* B.

**Q4.** In Part 1's Predict-and-Defend, what was your guess — can this be done with one integer per element?
→ *Read:* Open response — reconnects to the trade-off question before Part 2 answers it.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"Time to test your prediction. One stack, one variable, and a value that sometimes isn't what it looks like."*

---

## Slide Block B2 (7–21 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 37–66: Approach 2 (single-stack encoding), Dry Run, Pseudocode, Complexity, Code -->
Covers: Approach 2 — one stack, one `mini` variable. When pushing a value smaller than `mini`, push an **encoded** value (`2×x − oldMini`) instead of `x`, and update `mini = x`. On pop, if the popped value is *less than* `mini`, it was an encoding — decode the old minimum as `2×mini − poppedValue` before restoring.

**Beats to emphasise**

- This is the harder half of the session — go slower here than the pacing looks like it allows.
- Walk the deck's own dry run: `push(-5)` → stack empty → push `-5` directly, `mini = -5`. `push(1)` → `1 > -5` → push `1` directly, `mini` unchanged. `push(-10)` → `-10 < -5` → push the **encoded** value `2×(-10) − (-5) = -15`, update `mini = -10`.
- **Say this explicitly, it's the crux:** "`-15` sitting on the stack is not a real element of this Min Stack. It's a flag that means 'the real minimum just changed, and the old one was `-5`.'"
- On `pop()` of that `-15`: since `-15 < mini (-10)`, it's an encoding. Decode: `mini = 2×(-10) − (-15) = -5`. The old minimum is restored, and the encoded value itself is discarded — it was never a real stack element.

**Checkpoint (at 21 min)** — cold-call:
> *"How does `pop()` know whether the value it just removed was a real element or an encoded sentinel?"*
> **Answer:** Compare it to the current `mini` — if the popped value is *less than* `mini`, it was an encoding (a real element can never be smaller than the tracked minimum); otherwise it's a genuine value.

---

## ⚡ Activity 2 — Spot the Bug: "Decode It Yourself" (21–26 min)

**Format:** Spot the Bug / Predict-the-Output · **Exposes:** whether students actually understand the decode formula, versus having just watched it happen once — this is the single most error-prone step in the whole session.

**Setup line (say this):**
> *"Stack currently holds an encoded value of `-21` on top, and `mini` is currently `-8`. I'm about to `pop()`. Before I show you the arithmetic: is `-21` a real element or an encoding? And if it's an encoding, what does `mini` become after the pop?"*

**What students do:** 30 seconds silent, then hands up.

**Answer:** `-21 < mini (-8)` → it's an encoding. Decode: `mini_new = 2 × mini_old − poppedValue = 2×(-8) − (-21) = -16 + 21 = 5`. Wait — deliberately let a student catch that this looks like an unreasonably large jump, then re-anchor: the formula is mechanical and always correct *provided* the encoding was written correctly at push time; the "reasonableness" check is not part of the algorithm, just a sanity habit.

**How it surfaces:** The most common wrong move is applying the *push* formula (`2×x − mini`) instead of the *pop/decode* formula (`2×mini − encodedValue`) — same two numbers, opposite arrangement. Write both formulas side by side on the board and have students say out loud which one is "going in" (push) and which is "coming out" (pop).

**Debrief line:**
> *"Two formulas, mirror images of each other. Push encodes: `2x − mini`. Pop decodes: `2·mini − encoded`. Mix them up and you get a number that looks plausible and is completely wrong — which is exactly why this bug is dangerous."*

**Cut rule:** If running short, skip having students compute the decode by hand and instead just verify the answer already worked out above, spending the saved time re-stating the two-formula distinction once more.

---

## Exit Ticket (26–28 min)

> In one sentence: why does the encoded-value approach (Approach 2) use less space than the pair-stack approach (Approach 1)?
> **Answer:** Approach 1 stores two integers per element always (O(2n) space); Approach 2 stores exactly one integer per element — a real value most of the time, an encoded sentinel only when a new minimum is set — so it stays O(n).

**Homework:** trace Approach 2 by hand on `push(4), push(4), push(1), push(3), pop(), getMin()`. <!-- placement: inferred — no homework/RM/practice units exist for this course per deviation #2 -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| An encoded value on the stack is a real, usable element | It sits in the same stack, looks like just another number | Activity 2's decode exercise — explicitly naming `-21` as a sentinel, not data, before showing the arithmetic |
| The push-encode formula and the pop-decode formula are interchangeable | Both involve `2 × mini` and one other value, so they look structurally identical | Writing both formulas side by side on the board in Activity 2 and naming which direction each runs |
| Approach 2 saves space by not tracking history at all | The single `mini` variable looks like the *only* thing being tracked | Point out the encoded values *are* the hidden history — they're just stored inline instead of in a second array |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split right after the Classroom Quiz.**
- **Pacing risk:** this part's push/pop encode-decode logic is genuinely the hardest single idea in the Stack & Queue block so far. If you're behind, do not compress Slide Block B2 — cut Activity 2 down to its stated cut rule instead.
- **Do the two formulas on the board, not just the slide.** `push`: `2x − mini`. `pop` (when encoded): `2·mini − encoded`. Leave both up for the rest of the session — students will refer back to them during Activity 2.
