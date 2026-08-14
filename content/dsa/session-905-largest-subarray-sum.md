# Session 5 — Largest Subarray Sum

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Largest Subarray Sum — Kadane's Algorithm · **Prerequisite** Session 4 — Longest Subarray with Sum K (same array family, a different question)
**Session type** Concept lecture. New topic added to the Sem-3 sequence — ⚠️ **no video and no slide deck exist for this session** — see Instructor Notes. · **Format** 50-min recalibrated, 2 ALS activities

**Resources**

| Resource | Status |
|---|---|
| Source deck | None — new topic, no deck exists yet |
| Classroom Quiz | not yet available — 5-min slot reserved at end of session, add once question bank exists for this topic |
| Coding Practice | not yet available — add once problem set exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the problem precisely: find the contiguous subarray with the maximum possible sum. *(REMEMBERING)*
2. Explain Kadane's core decision at each position — extend the running subarray, or abandon it and start fresh here. *(UNDERSTANDING)*
3. Implement Kadane's algorithm in O(n) time and O(1) space. *(APPLYING)*
4. Correctly handle an all-negative array, where the answer is the single largest (least negative) element, not zero. *(ANALYZING)*
5. Trace Kadane's algorithm by hand on an array with a mix of positive and negative numbers. *(APPLYING)*
6. Contrast Kadane's O(n) against the O(n²) brute force of checking every subarray. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 4 (3–7 min) · ALS: Polling

5 questions on **Session 4 (Longest Subarray with Sum K)**. ~45 s each, project the distribution, never name individuals.

**Q1.** What identity connects a subarray's sum to two prefix sums?
`A` `prefix[j] + prefix[i] = k` · `B` `prefix[j] - prefix[i] = k` · `C` `prefix[i] - prefix[j] = k` · `D` `prefix[j] × prefix[i] = k`
→ **B.**

**Q2.** Why must the hash map keep the *earliest* index for each prefix sum, not the latest?
`A` Earliest is easier to compute · `B` Overwriting can only shrink the found length, never grow it · `C` It doesn't actually matter · `D` Python dicts require it
→ **B.**

**Q3.** What does `prefix_index = {0: -1}` account for?
`A` A typo · `B` A subarray starting at index 0 · `C` The empty array · `D` A subarray of length -1
→ **B.**

**Q4.** Why does Session 3's sliding-window shrink technique fail on arrays with negative numbers?
`A` It doesn't — it always works · `B` The window sum no longer only grows as you expand · `C` Negative numbers cause a crash · `D` It's slower, but still correct
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about Session 4's algorithm?
`A` O(n) time · `B` O(n) space · `C` Works correctly with negative numbers · `D` Finds how many subarrays sum to k
→ **A, B, C.** *(D is false — that's Session 2's counting preview, a different question.)*

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–9 min)

Put this on the board:

```python
arr = [-2, 1, -3, 4, -1, 2, 1, -5, 4]

# Find the contiguous subarray with the LARGEST sum. No target. Just: biggest possible.
```

Ask: *"No `k` this time — just find the best possible contiguous stretch. Anyone want to guess, just by eyeballing it?"*

Let a few guesses land — most will squint at `4, -1, 2, 1` and get close.

> *"That instinct — 'ignore the bad start, focus on the good middle' — is the entire algorithm today, made precise. The actual answer is `[4, -1, 2, 1]`, summing to 6. Here's the question that makes it computable: at every single position, you only ever need to decide one thing — keep extending what you've built, or throw it away and start over right here. That's it. That's the whole algorithm."*

---

## Teaching Block A (9–17 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from standard Kadane's-algorithm fundamentals -->

**1. The one decision, formalised — Kadane's algorithm.**

```python
def max_subarray_sum(arr):
    current_max = arr[0]
    global_max = arr[0]

    for i in range(1, len(arr)):
        current_max = max(arr[i], current_max + arr[i])
        global_max = max(global_max, current_max)

    return global_max
```

> *"`current_max` answers: 'the best sum of a subarray that ends exactly here.' At each step, that's either just this element alone, or this element added to whatever the best-ending-just-before-here subarray was — whichever is bigger. `global_max` just remembers the best `current_max` seen anywhere."*

**2. Trace it live, in full, on the Hook's array.**

```
arr = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
```

| `i` | `arr[i]` | `current_max = max(arr[i], current_max+arr[i])` | `global_max` |
|---|---|---|---|
| 0 (start) | -2 | — | -2 |
| 1 | 1 | `max(1, -2+1=-1) = 1` | 1 |
| 2 | -3 | `max(-3, 1-3=-2) = -2` | 1 |
| 3 | 4 | `max(4, -2+4=2) = 4` | 4 |
| 4 | -1 | `max(-1, 4-1=3) = 3` | 4 |
| 5 | 2 | `max(2, 3+2=5) = 5` | 5 |
| 6 | 1 | `max(1, 5+1=6) = 6` | **6** |
| 7 | -5 | `max(-5, 6-5=1) = 1` | 6 |
| 8 | 4 | `max(4, 1+4=5) = 5` | 6 |

> **Answer: 6**, matching the Hook's `[4, -1, 2, 1]`. Notice `current_max` never has to "know" where the subarray started — it only carries the running best.

**Beats to emphasise**

- **`current_max` is a *local* decision, `global_max` is a *memory*.** Keep them visually separate on the board — conflating them is the most common implementation slip.
- **"Start fresh here" happens exactly when `arr[i] > current_max + arr[i]`** — which is exactly when `current_max` was negative. A negative running total can only drag down anything added to it.
- **This is O(n) time, O(1) space.** One pass, two variables, no hash map, no extra array — the leanest technique in this entire block.

**Checkpoint (at 17 min)** — 10 s silent think, cold-call:
> *"At `i=2` (`arr[2]=-3`), `current_max` resets from 1 down to -2 instead of continuing to add. What decided that, exactly?"*
> **Answer:** `max(-3, 1 + (-3)) = max(-3, -2) = -2` — continuing (`-2`) still beat starting fresh (`-3`), so it kept extending, it didn't actually reset. *(Flag this explicitly — it's a common misreading of the trace: the value went down, but the subarray didn't restart.)*

---

## ⚡ ALS Activity 1 — Guided Table Build: Trace Kadane's (17–25 min)

**ALS format:** Guided Table Build — the class fills in Kadane's trace table together, column by column, cold-called student by student. Chosen right after Teaching Block A because "extend or restart" is easy to state and easy to apply wrong under time pressure — this is where it gets tested on numbers nobody has pre-seen solved.

**Setup line:**
> *"New array. I point at a cell, you compute `current_max` and tell me: did it extend, or start fresh? Say which, every time — not just the number."*

```
arr = [5, -4, 3, -2, 6, -1]
```

**The completed trace**

| `i` | `arr[i]` | `current_max` | extend or fresh? | `global_max` |
|---|---|---|---|---|
| 0 | 5 | 5 | (start) | 5 |
| 1 | -4 | `max(-4, 5-4=1)=1` | extend | 5 |
| 2 | 3 | `max(3, 1+3=4)=4` | extend | 5 |
| 3 | -2 | `max(-2, 4-2=2)=2` | extend | 5 |
| 4 | 6 | `max(6, 2+6=8)=8` | extend | **8** |
| 5 | -1 | `max(-1, 8-1=7)=7` | extend | 8 |

**Answer: `global_max = 8`**, from the subarray `[5, -4, 3, -2, 6]` (the whole array except the last element).

**How it surfaces:** every single row here happens to extend — no fresh starts at all. That's deliberate: it forces the room to actually check the comparison each time rather than pattern-matching "negative number means restart."

**When it goes wrong**

| If… | Do this |
|---|---|
| A student resets `current_max` to `arr[i]` just because `arr[i]` is negative | Make them compute both sides of the `max()` explicitly — negative doesn't automatically mean "restart," only mean *possibly* restart |
| Someone loses track of `global_max` vs `current_max` | Point at the board's two separate rows — ask which one just changed and which one is only updated when a new best appears |

**Debrief line:**
> *"Every row here extended, and the biggest sum still came from almost the whole array. Don't assume — compute the comparison every single time, exactly like you just did."*

**Cut rule:** Trace through `i=4` only, state the final `global_max` and the last row directly.

---

## Teaching Block B (25–33 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from standard Kadane's-algorithm fundamentals -->

**1. The all-negative edge case — the classic gotcha.**

```python
arr = [-8, -3, -6, -2, -5, -4]
```

> *"Run Kadane's on this by the exact same rule — no special-casing negatives."*

| `i` | `arr[i]` | `current_max` | `global_max` |
|---|---|---|---|
| 0 | -8 | -8 | -8 |
| 1 | -3 | `max(-3, -8-3=-11)=-3` | -3 |
| 2 | -6 | `max(-6, -3-6=-9)=-6` | -3 |
| 3 | -2 | `max(-2, -6-2=-8)=-2` | -2 |
| 4 | -5 | `max(-5, -2-5=-7)=-5` | -2 |
| 5 | -4 | `max(-4, -5-4=-9)=-4` | -2 |

> **Answer: -2** — the single least-bad element. **Not 0.** The problem asks for the sum of a non-empty contiguous subarray; if you're not allowed to pick zero elements, the best you can do here is pick the one element that hurts least.

> *"This is exactly why `current_max` and `global_max` both start at `arr[0]`, not at `0`. Starting either one at 0 would silently let 'pick nothing' compete as an option — and on an all-negative array, 'pick nothing' would win, giving you the wrong answer of 0."*

**2. Contrast with brute force.**

```python
def max_subarray_naive(arr):
    n = len(arr)
    best = float('-inf')
    for i in range(n):
        total = 0
        for j in range(i, n):
            total += arr[j]
            best = max(best, total)
    return best
```

> *"O(n²) — every start, every extension, re-summed. Kadane's does the identical job in one pass. Same answer, radically less work."*

**Beats to emphasise**

- **Initialising at `arr[0]`, not `0`, is the single most important line in the whole implementation.** State this explicitly and connect it directly to the all-negative trace.
- **Kadane's is a specific case of "extend-or-restart" dynamic programming** — students will meet this decision shape again; naming it now makes the pattern recognisable later.
- **This session's technique is unrelated to Session 4's hash map.** No prefix sums, no map, no target `k` — say this explicitly so the two don't blur together as "the same subarray-sum thing."

**Checkpoint (at 33 min)** — show hands:
> *"If `current_max` were initialised to `0` instead of `arr[0]`, what would `max_subarray_sum` return on an array of all negative numbers?"*
> **Answer:** `0` — incorrectly, since picking zero elements isn't a valid subarray. The correct answer is the largest (least negative) single element.

---

## ⚡ ALS Activity 2 — Silent Diagnose, Named Reveal: Spot the Zero-Init Bug (33–40 min)

**ALS format:** Silent Diagnose, Named Reveal — a version of Kadane's that initialises at `0` instead of `arr[0]` goes on the board; students trace it against an all-negative array and name exactly where it goes wrong. Chosen as the closing activity because this specific bug is the single most common real-world mistake with this algorithm, and it's silent — it never crashes, it just returns a plausible-looking wrong answer.

**Setup line:**
> *"One line changed — both variables start at 0 instead of `arr[0]`. Looks harmless. Trace it with me on an all-negative array and watch what happens."*

```python
def max_subarray_broken(arr):
    current_max = 0
    global_max = 0

    for num in arr:
        current_max = max(num, current_max + num)
        global_max = max(global_max, current_max)

    return global_max
```

Give 90 seconds silent to predict the output on `arr = [-3, -1, -7, -2]`, then trace live:

| `num` | `current_max = max(num, current_max+num)` | `global_max` |
|---|---|---|
| -3 | `max(-3, 0-3=-3)=-3` | `max(0,-3)=0` |
| -1 | `max(-1, -3-1=-4)=-1` | `max(0,-1)=0` |
| -7 | `max(-7, -1-7=-8)=-7` | `max(0,-7)=0` |
| -2 | `max(-2, -7-2=-9)=-2` | `max(0,-2)=0` |

**The broken version returns `0`.** The correct version (initialised at `arr[0]=-3`) would return `-1` (the least-bad single element). `0` isn't just wrong — it isn't even achievable, since the array has no way to sum to `0` from any real subarray.

**When it goes wrong**

| If… | Do this |
|---|---|
| Students say "0 seems like a reasonable fallback" | Push back directly: the problem requires a non-empty subarray — 0 represents *not picking anything*, which isn't a valid answer here |
| Nobody notices `global_max` never moves off 0 | Point at every row — `max(0, negative number)` is always 0, so `global_max` is mathematically stuck the instant every element is negative |

**Debrief line:**
> *"This bug never crashes. It never looks wrong on an array with any positive numbers in it — it only surfaces on all-negative input, which is exactly the input most people forget to test. That's what makes it dangerous, not that it's hard to understand once you see it."*

**Cut rule:** Trace only the first two elements, then state the final broken/correct outputs directly.

---

## Classroom Quiz (40–45 min) · Reserved — not yet available

No quiz bank exists yet for this topic (new to the Sem-3 sequence — see Resources table). This slot is reserved here, at the end of the session and right before the Exit Ticket, so the plan doesn't need restructuring once a bank exists. Until then, use it for an instructor-led review of today's toughest moment — re-run the all-negative trace on a fresh 4-5 element array, cold-calling a different student for each row — or fold the slot into Buffer and end early.

---

## Exit Ticket + Homework (45–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> Write Kadane's core recurrence for `current_max`, and explain in one sentence why both variables are initialised to `arr[0]`, not `0`.
> **Answers:** `current_max = max(arr[i], current_max + arr[i])`. Initialising at `arr[0]` guarantees a real, non-empty subarray is always the answer — initialising at `0` would incorrectly let "pick nothing" compete and win on an all-negative array.

**Homework**

| Task | Note |
|---|---|
| Trace `max_subarray_sum([-1, -2, 3, 5, -3, 2])` by hand, full table | State the final `global_max` and which subarray achieves it |
| In one paragraph, explain why Kadane's doesn't need a hash map, while Session 4's technique does | This is a "convince yourself" exercise about what each problem is actually asking |

Tell them: *"Next session is Two Sum — the problem Session 1 already previewed with `has_pair_with_sum`. You'll finally return the actual indices, not just true or false."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A negative `arr[i]` always means "start fresh" | Sounds intuitive, "negative is bad" | Teaching Block A's checkpoint — `i=2` extends despite a negative value |
| The answer on an all-negative array is 0 | 0 "feels like" a safe minimum | Teaching Block B's full trace — the real answer is the least-bad single element |
| `current_max` and `global_max` are the same variable | Both track "a max" | The two-column trace table, kept visually distinct throughout |
| Kadane's needs a hash map, like Session 4 | Recency — the previous session used one | Teaching Block B's explicit contrast — O(1) space, no map at all |
| This algorithm returns *which* subarray, automatically | The trace shows the subarray informally | State explicitly: as written, it returns only the *sum* — recovering the actual start/end indices needs tracking two more variables, not shown here |

---

## Instructor Notes

- **⚠️ No video and no slide deck exist for this session.** It's newly added to the Sem-3 sequence (see `sem-3-sequence.md`) — both teaching blocks above are written as board-and-live-typing sessions built from standard Kadane's-algorithm fundamentals, not from any platform export.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Guided Table Build (a trace where every row happens to extend, deliberately resisting pattern-matching), Activity 2 is Silent Diagnose → Named Reveal (the zero-initialisation bug on an all-negative array).
- **This is session 5 of the new 6-session block** opening the Sem-3 sequence (Hashing → Prefix Sum → Sliding Window/Two-Pointer → Longest Subarray Sum K → Largest Subarray Sum → Two Sum).
- **The all-negative edge case is this session's single highest-value moment** — it's covered twice (Teaching Block B's worked trace, ALS Activity 2's bug hunt) by design. If the session runs behind, protect both of those over the guided-trace activity's later rows.
- **This session does not return the actual subarray, only its sum** — flagged explicitly in Common Misconceptions. If asked how to recover the indices, the answer is: track a `start` variable that resets whenever `current_max` restarts fresh, and a `best_start`/`best_end` pair updated alongside `global_max`. Not required content for this session, but be ready for the question.
- **All numeric traces in this file have been hand-verified** (Hook/Teaching Block A's 9-element trace, ALS Activity 1's 6-element trace, Teaching Block B's all-negative trace, ALS Activity 2's broken-vs-correct trace). If you swap in different numbers, re-verify before class.
