# Session 21 — Next Greater Element

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Stack — Next Greater Element (Brute Force vs. Monotonic Stack) · **Prerequisite** Session 20 — Introduction to Monotonic Stacks
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Next Greater Element | https://docs.google.com/presentation/d/1fYEqvg63eWARWKlNAGWz-tp1N6zvDi7VPJMo8DmVoAQ/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the Next Greater Element (NGE) problem: for each element, find the closest element to its *right* that's larger, or `-1` if none exists. *(REMEMBERING)*
2. Explain the brute-force approach (nested scan) and why it costs O(n²). *(UNDERSTANDING)*
3. Trace the optimal right-to-left monotonic-stack approach on a given array, including the pop loop at each step. *(APPLYING)*
4. Connect this problem back to Session 20's increasing/decreasing pairing rule — explain *why* NGE uses a decreasing-style scan direction and comparison. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 20 (3–7 min) · ALS: Polling

5 questions on **Session 20 (Introduction to Monotonic Stacks)**. ~45 s each, project the distribution, never name individuals.

**Q1.** Which type of monotonic stack finds the next/previous *greater* element?
`A` Increasing · `B` Decreasing · `C` Either works · `D` Neither
→ **B.** *Read:* Today's whole session depends on this pairing.

**Q2.** In a monotonic stack's pop rule, is the condition checked once per incoming element, or looped?
`A` Once (`if`) · `B` Looped (`while`), as many times as the condition holds · `C` Never — pop is unconditional · `D` Twice, always
→ **B.**

**Q3.** Across a full run, how many times, at most, is any single element pushed or popped?
`A` Pushed once, popped unlimited times · `B` Pushed once, popped at most once · `C` No limit either way · `D` Popped once, pushed unlimited times
→ **B.**

**Q4.** Why does that "pushed once, popped at most once" bound matter?
`A` It doesn't · `B` It's the proof the total work is O(n), not O(n²) · `C` It only applies to increasing stacks · `D` It only applies to small arrays
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about monotonic stacks?
`A` They maintain elements in strictly increasing or decreasing order · `B` They're still stacks — push/pop only at the top · `C` They immediately produce a final answer array by themselves · `D` The pop condition compares the top to the incoming element
→ **A, B, D.** *(C is false — Session 20 built the mechanism; today is the first real payoff.)*

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Write this array on the board: `[73, 74, 75, 71, 69, 72, 76, 73]` (a week of daily temperatures).

Ask: *"For each day, I want to know: how many days until a warmer day? Day 1 is 73° — the very next day, 74°, is warmer, so the answer for day 1 is 1. What about day 6, 72°?"*

Let students reason it out (day 7 is 76° — warmer — so 1 day).

> *"You're doing 'next greater element' right now, just phrased as temperatures instead of numbers. It's one of the most common interview problems that exists, precisely because the naive way to solve it — check every day against every future day — is slow, and the clever way uses exactly the monotonic stack you built last session. Today, that stack finally answers something."*

---

## Slide Block A (10–19 min) — DELIVER SLIDES AS-IS

Covers: Problem Statement (for each element, find the closest larger element to its right; `-1` if none — the last element is always `-1`) → worked example `arr = [7, 3, 1, 5, 8, 4]` → output `[8, 5, 5, 8, -1, -1]` → Brute Force Approach: for each element, scan right until a larger one is found.

**Beats to emphasise**

- Read the output aligned under the input so the pattern is visible: `7→8`, `3→5`, `1→5`, `5→8`, `8→-1`, `4→-1`.
- **Say explicitly why the last element is always `-1`:** there's nothing to its right at all, so the search space is empty by definition — not a special case, just the natural consequence of the rule.
- Brute force, stated as one sentence: "for every position, walk right one step at a time until something bigger shows up, or you run out of array."

**Checkpoint (at 19 min)** — cold-call:
> *"For `arr = [7, 3, 1, 5, 8, 4]`, why is the answer for `8` equal to `-1`, but the answer for `4` is also `-1` — same answer, different reason?"*
> **Answer:** `8` is `-1` because nothing to its right (`4`) is bigger than it. `4` is `-1` because it's the *last* element — nothing is to its right at all.

---

## Slide Block B1 (19–27 min) — DELIVER SLIDES AS-IS

Covers: Full dry-run walk of the brute force approach on `[7, 3, 1, 5, 8, 4]`, checking each element against everything to its right → pseudocode (nested loop) → complexity: O(n²) time, O(n) space.

**Beats to emphasise**

- Narrate the dry run exactly as the deck does: for `7`, scan right `[3, 1, 5, 8, 4]` — first value bigger than `7` is `8`. For `3`, scan right `[1, 5, 8, 4]` — first bigger is `5`. Continue through `1 → 5`, `5 → 8`, `8 → (nothing bigger, -1)`, `4 → (last element, -1)`.
- State the cost plainly: worst case, every element scans almost the entire rest of the array — that's the outer loop times the inner loop, O(n²).
- This is the same shape of inefficiency as Session 20's opening hook — call that back explicitly.

**Checkpoint (at 27 min)** — cold-call:
> *"What's the absolute worst input for brute force here — the array that makes it do the most work?"*
> **Answer:** A strictly decreasing array (e.g. `[9, 8, 7, 6, 5]`) — every element has to scan almost the entire remaining array before concluding there's no greater element, hitting close to n² comparisons total.

---

## ⚡ ALS Activity 1 — Predict the Output: Brute Force by Hand (27–33 min)

**ALS format:** Predict-the-Output — exposes whether students can execute the brute-force scan themselves, necessary groundwork before the optimal approach replaces it with something less intuitive-looking. Chosen right after Slide Block B1 to lock in the brute-force baseline before flipping to the optimal approach.

**Setup line:**
> *"New array: `[4, 8, 2, 9, 3]`. For each position, tell me the next greater element before I confirm — scan right, same as the dry run."*

Call out each answer in turn, one position at a time.

**Answers**

```
4 → scan [8, 2, 9, 3] → 8 is first bigger → 8
8 → scan [2, 9, 3]    → 9 is first bigger → 9
2 → scan [9, 3]       → 9 is first bigger → 9
9 → scan [3]          → nothing bigger → -1
3 → last element      → -1
```

**How it surfaces:** At `2`, ask before revealing: *"Is the answer `9` or `3`?"* Push students to confirm they're finding the *first bigger* one, not just any nearby number, and that they stop scanning the moment they find it.

**Debrief line:**
> *"Every one of those scans stops the instant it finds something bigger — you never need to look further right than that. The only question left is: can we avoid re-scanning from scratch for every single position? That's next."*

**Cut rule:** Do just `4` and `2` — one straightforward case, one where "first bigger, not first different" needs reinforcing.

---

## Slide Block B2 (33–37 min) — DELIVER SLIDES AS-IS

Covers: Optimal Approach — traverse the array **right to left**, maintain a stack of "candidates that might be the next greater element" for positions still to come. At each position, pop everything smaller-or-equal, then the new top (if any) is the answer; push the current element.

**Beats to emphasise**

- **Connect directly to Session 20:** this is a monotonically *decreasing* stack (bottom → top decreasing), scanning right to left — exactly the pairing rule from last session (decreasing stack ↔ next/previous greater).
- Say the rule as one sentence: *"Walking backwards, the stack only ever holds numbers that could still be someone's answer. Anything smaller than what's currently arriving can never be anyone's next-greater from this point on, so it gets thrown away."*
- This flips the brute-force intuition (scan forward from each element) into a single backward pass that reuses work instead of repeating it.

**Checkpoint (at 37 min)** — cold-call:
> *"Why do we scan right to left here, instead of left to right like the brute force did?"*
> **Answer:** Scanning right to left lets the stack accumulate "candidates to the right" as we go, so by the time we reach any position, the stack already holds exactly the information needed to answer it in O(1) amortised — no re-scanning.

---

## ⚡ ALS Activity 2 — Live Coding / Dry-Run Relay: Run the Optimal Stack (37–41 min)

**ALS format:** Live Coding / Dry-Run Relay — exposes whether students can execute the right-to-left monotonic-stack algorithm themselves, tying the mechanical trace back to the pairing rule just restated. Chosen as the closing activity because it uses the exact same array as ALS Activity 1, so the two answers can be checked against each other directly.

**Setup line:**
> *"Same array as Activity 1: `[4, 8, 2, 9, 3]`. Right to left this time. I'll call the position, you tell me what gets popped, what the answer is, and what gets pushed — before I confirm."*

Run **right to left, one element at a time**:

```
3  → stack empty → answer -1 → push 3.                Stack: [3]
9  → top 3 ≤ 9 → pop 3. Stack empty → answer -1 → push 9.   Stack: [9]
2  → top 9 > 2 → no pop → answer 9 → push 2.          Stack: [9, 2]
8  → top 2 ≤ 8 → pop 2. top 9 > 8 → stop → answer 9 → push 8.  Stack: [9, 8]
4  → top 8 > 4 → no pop → answer 8 → push 4.          Stack: [9, 8, 4]
```

Final answers, read left to right: `4→8, 8→9, 2→9, 9→-1, 3→-1` — matching ALS Activity 1 exactly.

**How it surfaces:** At `8`, ask before revealing: *"How many pops happen, and why does popping stop at `9`?"* Correct: one pop (`2`), then stop, because `9 > 8` means `9` is a valid answer for `8` and also still a valid future candidate — it doesn't get thrown away.

**Debrief line:**
> *"Same final answers as the brute force, same problem — but every element was pushed once and popped at most once across the whole array. That's O(n), not O(n²), and it's the exact same discipline you practiced last session."*

**Cut rule:** Do only the `9` and `8` steps — `9` shows a pop-to-empty, `8` shows a pop-then-stop, which together cover the whole mechanism.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering the O(n²) vs O(n) contrast and the right-to-left decreasing-stack mechanics. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> For `arr = [5, 4, 3, 2, 1]` (strictly decreasing), what is the Next Greater Element for every position, and why?
> **Answer:** `[-1, -1, -1, -1, -1]` for all — since the array is strictly decreasing, nothing to the right of any element is ever larger.

**Homework:** Trace the optimal right-to-left approach by hand on `[2, 7, 3, 5, 4]`.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The brute force and optimal approaches can give different answers | Feels like "different algorithm" should mean "different logic entirely" | ALS Activity 1 and 2 use the *same* array and land on identical output — only the work done differs |
| The optimal approach should scan left to right, matching how humans read | Reading direction bias | Slide Block B2's explicit right-to-left framing, reinforced by the checkpoint question naming *why* |
| Popping stops after exactly one pop | Carried over from underestimating monotonic-stack loops generally | ALS Activity 2's `8` step — one pop, but only because the next top happens to be bigger; a different array could pop several |
| A strictly decreasing array is an edge case that needs special handling | Every answer being `-1` looks like something must have gone wrong | Exit ticket — confirming this is just the ordinary algorithm producing an ordinary (if uniform) result |
| The stack in the optimal approach stores answers | It's easy to conflate "the stack" with "the answer array" since both update together | State explicitly: the stack stores *candidates*, a completely separate `ans` array stores the actual answers |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). This session's original 45-min version already had exactly 2 ALS activities — minimal restructuring needed beyond adding settling/buffer and moving the Classroom Quiz to the end (originally sat between Slide Block B1 and Activity 1).
- **Two ALS activities this session, both carried over directly:** Activity 1 is Predict the Output (brute force by hand), Activity 2 is the Live Coding / Dry-Run Relay (the optimal right-to-left stack).
- **The Classroom Quiz now runs last, right before the Exit Ticket** — matching the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank.
- **This is session 21 of the Sem-3 sequence** (see `sem-3-sequence.md`) — this is where Session 20's investment pays off. If students struggled with the increasing/decreasing pairing last session, this is the natural moment to re-anchor it, since NGE is the pairing's first real payoff.
- **Keep both activities on the exact same array (`[4, 8, 2, 9, 3]`).** Running brute force and optimal on identical input lets students see directly that the answers match — more convincing than two different examples ever would be.
- **The next few Stack sessions (Asteroid Collision, Largest Rectangle in Histogram) reuse this same right-to-left-adjacent stack discipline in physically different framings** — flag that connection at the close if time allows.
