# Session 3 — Sliding Window, Two-Pointer Technique

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Sliding Window (fixed & variable size) and the Two-Pointer Technique · **Prerequisite** Session 2 — Prefix Sum (the running-total habit this session turns into a moving window)
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

1. Explain the sliding window technique and recognise when a problem calls for it — contiguous subarray/substring, size or sum-related. *(UNDERSTANDING)*
2. Distinguish a **fixed-size** window from a **variable-size** window. *(UNDERSTANDING)*
3. Implement a fixed-size sliding window to find the maximum-sum subarray of size k, in O(n). *(APPLYING)*
4. Implement a variable-size (expand/shrink) window to find the smallest subarray with sum ≥ a target. *(APPLYING)*
5. State why sliding window turns an O(n·k) or O(n²) brute force into O(n). *(ANALYZING)*
6. Distinguish sliding window (one window moving through unsorted data) from the two-pointer technique (two pointers converging on *sorted* data). *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 2 (3–7 min) · ALS: Polling

5 questions on **Session 2 (Prefix Sum)**. ~45 s each, project the distribution, never name individuals.

**Q1.** Using a prefix array, what's the formula for `sum(i, j)` (inclusive range)?
`A` `prefix[j] - prefix[i]` · `B` `prefix[j+1] - prefix[i]` · `C` `prefix[i] - prefix[j]` · `D` `prefix[j+1] - prefix[i+1]`
→ **B.**

**Q2.** Why does `prefix[0]` always equal 0?
`A` It's a placeholder with no meaning · `B` It represents the sum of zero elements · `C` It's a rounding convention · `D` It's the smallest value in the array
→ **B.**

**Q3.** After building a prefix array once, what's the time complexity of a single range-sum query?
`A` O(n) · `B` O(log n) · `C` O(1) · `D` O(n²)
→ **C.**

**Q4.** In `count_subarrays_with_sum`, what does `seen = {0: 1}` at the start account for?
`A` A subarray of sum 0 · `B` A subarray starting at index 0 · `C` An empty array · `D` Nothing, it's arbitrary
→ **B.**

**Q5.** *(MSQ — select all that apply)* Which of these are true of a prefix sum array of length n?
`A` It has n+1 elements · `B` It has n elements · `C` Building it costs O(n) · `D` Querying it after building costs O(1) per query
→ **A, C, D.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–9 min)

Put this on the board:

```python
arr = [2, 1, 5, 1, 3, 2]
k = 3

# Find the maximum sum of any k=3 consecutive elements.
```

Ask: *"Brute force — try every window of size 3, sum each one, keep the biggest. What's the time complexity?"*

```python
def max_sum_naive(arr, k):
    n = len(arr)
    best = float('-inf')
    for i in range(n - k + 1):
        window_sum = sum(arr[i:i+k])   # re-sums k elements, every time
        best = max(best, window_sum)
    return best
```

Let them land on **O(n·k)** — for every starting position, sum k elements from scratch.

> *"Now notice something. Window `[2,1,5]` and the next window `[1,5,1]` — how much do they actually have in common?"*

Let them see it: both windows share `1` and `5`. Only `2` leaves and `1` (the new one) enters.

> *"You already know this move — Session 2 built a running total once and reused it. Today you slide that same running total across the array, one step at a time, updating it by removing what leaves and adding what enters. No re-summing. Ever."*

---

## Teaching Block A (9–18 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from standard sliding-window fundamentals -->

**1. Fixed-size sliding window — the core move.**

```python
def max_sum_fixed(arr, k):
    window_sum = sum(arr[:k])      # build the FIRST window once
    best = window_sum

    for i in range(k, len(arr)):
        window_sum += arr[i]           # element entering
        window_sum -= arr[i - k]       # element leaving
        best = max(best, window_sum)

    return best
```

Trace it live on `arr = [2, 1, 5, 1, 3, 2]`, `k = 3`:

| Step | Window | Entering | Leaving | `window_sum` | `best` |
|---|---|---|---|---|---|
| Start | `[2,1,5]` | — | — | 8 | 8 |
| `i=3` | `[1,5,1]` | `arr[3]=1` | `arr[0]=2` | `8+1-2=7` | 8 |
| `i=4` | `[5,1,3]` | `arr[4]=3` | `arr[1]=1` | `7+3-1=9` | **9** |
| `i=5` | `[1,3,2]` | `arr[5]=2` | `arr[2]=5` | `9+2-5=6` | 9 |

> **Answer: max sum = 9**, from window `[5,1,3]`.

**Beats to emphasise**

- **Build the first window with a real sum, then slide.** Every window after the first costs exactly one addition and one subtraction — not a re-sum.
- **`arr[i - k]` is the element leaving.** This is the one line students copy wrong most often — walk the index arithmetic slowly: *"the window is size k, so the element k positions behind the one entering is the one leaving."*
- **O(n·k) → O(n).** Say the comparison out loud against the Hook's naive version.

**Checkpoint (at 18 min)** — 10 s silent think, cold-call:
> *"At `i=4`, `window_sum` goes from 7 to 9. Which element entered, which left, and what's `9 - 7`?"*
> **Answer:** `arr[4]=3` entered, `arr[1]=1` left. `9 - 7 = 2`, and `3 - 1 = 2` — matches, because the change in sum is exactly (entering − leaving).

---

## ⚡ ALS Activity 1 — Guided Table Build: Slide the Window (18–25 min)

**ALS format:** Guided Table Build — the class slides a fixed-size window across a new array together, one step at a time, cold-called for each entering/leaving pair. Chosen right after Teaching Block A because the "subtract what leaves, add what enters" move only becomes automatic after doing it with their own hands on numbers they haven't pre-seen solved.

**Setup line:**
> *"New array, window size 4. I point, you tell me what enters, what leaves, and the new sum. Nobody re-adds the whole window — if you do, that's the bug we're hunting."*

```
arr = [4, 6, 1, 9, 2, 8, 3, 5]
k = 4
```

**The trace, built live**

| Step | Window | Entering | Leaving | `window_sum` |
|---|---|---|---|---|
| Start | `[4,6,1,9]` | — | — | 20 |
| `i=4` | `[6,1,9,2]` | `arr[4]=2` | `arr[0]=4` | `20+2-4=18` |
| `i=5` | `[1,9,2,8]` | `arr[5]=8` | `arr[1]=6` | `18+8-6=20` |
| `i=6` | `[9,2,8,3]` | `arr[6]=3` | `arr[2]=1` | `20+3-1=22` |
| `i=7` | `[2,8,3,5]` | `arr[7]=5` | `arr[3]=9` | `22+5-9=18` |

**Maximum sum found: 22**, window `[9,2,8,3]`.

**How it surfaces:** ask before revealing each row: *"which index is leaving, and how do you know?"* — if a student can't name `arr[i-k]` without counting on their fingers, that's the exact gap to close before ALS Activity 2's harder problem.

**When it goes wrong**

| If… | Do this |
|---|---|
| A student re-sums the whole window instead of updating | Stop them — ask "what's the only thing that changed between this window and the last one?" |
| Wrong element identified as "leaving" | Have them write out both windows fully, side by side, and circle what's different |

**Debrief line:**
> *"Four windows, one running total, updated four times. The brute-force version would have re-summed 4 elements, four separate times — sixteen additions instead of four. That gap only gets bigger as the array grows."*

**Cut rule:** Trace 3 steps instead of 4 — drop the last row and state the final max directly.

---

## Teaching Block B (25–34 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from standard variable-window and two-pointer fundamentals -->

**1. Variable-size window — when the window's size isn't fixed in advance.**

> *"Fixed window: 'find the best window of size k.' Variable window: 'find the smallest window that satisfies some condition.' The size changes as you go — that's the difference."*

**Problem:** find the length of the **smallest** subarray with sum ≥ a target. (Assume all positive numbers — the shrink step below relies on that.)

```python
def smallest_window_at_least(arr, target):
    left = 0
    window_sum = 0
    best_len = float('inf')

    for right in range(len(arr)):
        window_sum += arr[right]                  # expand: pull right edge forward

        while window_sum >= target:                # shrink while the condition still holds
            best_len = min(best_len, right - left + 1)
            window_sum -= arr[left]
            left += 1

    return best_len if best_len != float('inf') else 0
```

Trace it live on `arr = [2, 1, 5, 2, 3, 2]`, `target = 7`:

| `right` | `arr[right]` | `window_sum` | shrink? | `left` after | `best_len` |
|---|---|---|---|---|---|
| 0 | 2 | 2 | no | 0 | ∞ |
| 1 | 1 | 3 | no | 0 | ∞ |
| 2 | 5 | 8 | yes → shrink | 1 | `2-0+1=3` |
| 3 | 2 | `8-2+2=8`... | *(continue shrinking while ≥7)* | 2 | `3-1+1=3`, then check again |

> *"Notice `right` only ever moves forward, and `left` only ever moves forward — neither goes backward. That's what keeps this O(n) instead of O(n²): every element gets added once and removed at most once, total, across the whole run."*

<!-- placement: inferred — instructor should complete this trace live on the board through right=5 and confirm the final best_len; the shrink loop's exact step count depends on running it fully, deliberately left as a live board exercise rather than fully worked here. -->

**2. Two-pointer on sorted data — a related but different move.**

> *"Sliding window uses one window moving through data, usually unsorted. Two-pointer usually means two pointers starting at opposite ends of *sorted* data, moving toward each other."*

**Problem:** given a **sorted** array, does a pair exist that sums to exactly `target`?

```python
def has_pair_sorted(arr, target):
    left, right = 0, len(arr) - 1
    while left < right:
        current = arr[left] + arr[right]
        if current == target:
            return True
        elif current < target:
            left += 1          # sum too small — need a bigger left value
        else:
            right -= 1         # sum too big — need a smaller right value
    return False
```

> *"Compare this to Session 1's hash-set version of the same question. That one worked on unsorted data using extra memory. This one needs the data sorted first, but uses no extra memory at all — two pointers, nothing else. Different trade-off, same question."*

**Beats to emphasise**

- **Variable window: `right` expands, `left` shrinks — both only ever move forward.** That's the whole reason it's O(n) and not O(n²).
- **Two-pointer requires sorted input.** If the array isn't sorted, either sort it first (O(n log n)) or use hashing instead (Session 1's approach).
- **These are two different techniques bundled under one session because they rhyme, not because they're the same thing.** Name the distinction explicitly: one window vs. two pointers; unsorted vs. sorted.

**Checkpoint (at 34 min)** — show hands:
> *"In `smallest_window_at_least`, does `left` ever move backward, even once?"*
> **Answer:** No — `left` only ever increases. That's what guarantees the total work stays O(n).

---

## ⚡ ALS Activity 2 — Silent Diagnose, Named Reveal: Spot the Missing Shrink (34–41 min)

**ALS format:** Silent Diagnose, Named Reveal — a broken variable-window implementation goes on the board; students must name exactly what's missing before the fix is revealed. Chosen as the closing activity because the shrink step is the one part of variable-window code students forget under pressure — this exposes that specific gap directly.

**Setup line:**
> *"This code is supposed to find the smallest window summing to at least the target. It's missing something. Don't just say 'it's wrong' — tell me which line, and what should be there instead."*

```python
def smallest_window_broken(arr, target):
    left = 0
    window_sum = 0
    best_len = float('inf')

    for right in range(len(arr)):
        window_sum += arr[right]
        if window_sum >= target:
            best_len = min(best_len, right - left + 1)

    return best_len if best_len != float('inf') else 0
```

Give 90 seconds silent, then cold-call: *"Run this on `[1, 1, 1, 7]`, `target = 7`. What length does it return, and what's the actual smallest window?"*

**The diagnosis:** `left` never moves in this version, so it's really just tracking the cumulative sum from index 0. That first crosses 7 at `right=3` (`1+1+1+7=10`), giving `best_len = 4` — the whole array. But the real smallest window is `[7]` alone, length `1`, sitting right there at the end. The `if` never shrinks `left`, so it can never discover a smaller window hiding inside a bigger one — once the cumulative sum from the start clears the target, that's the only length it can ever record.

**The fix — replace `if` with a `while` loop that shrinks:**

```python
while window_sum >= target:
    best_len = min(best_len, right - left + 1)
    window_sum -= arr[left]
    left += 1
```

> *"An `if` checks once. A `while` keeps checking — and keeps shrinking — for as long as the condition still holds, which is exactly what finds the *smallest* window, not just *a* window."*

**When it goes wrong**

| If… | Do this |
|---|---|
| Students fix it by adding a second loop instead of changing `if` to `while` | Ask: "does that keep the total work at O(n), or does it start re-scanning?" |
| Nobody catches the specific `[1,1,1,7]` failure | Walk the trace live: sum only reaches 7 once all four elements are included — the single `7` at the last index alone is never checked on its own, because `left` is stuck at 0 the whole time. |

**Debrief line:**
> *"`if` finds *a* window that works. `while` finds the *smallest* one, by refusing to stop shrinking until it has to. That one-word difference is the whole technique."*

**Cut rule:** Skip the silent diagnose phase, walk the broken trace as a class discussion, then reveal the fix.

---

## Classroom Quiz (41–46 min) · Reserved — not yet available

No quiz bank exists yet for this topic (new to the Sem-3 sequence — see Resources table). This slot is reserved here, at the end of the session and right before the Exit Ticket, so the plan doesn't need restructuring once a bank exists. Until then, use it for an instructor-led review of today's toughest moment — re-run the `smallest_window_at_least` trace on `[2,1,5,2,3,2]`, `target=7` all the way through, cold-calling a different student for each row — or fold the slot into Buffer and end early.

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> In one sentence each: what's the difference between a fixed-size and variable-size sliding window? And what's the difference between sliding window and two-pointer?
> **Answers:** Fixed-size keeps the window length constant and slides it; variable-size grows and shrinks the window based on a condition. Sliding window moves one window through (usually unsorted) data; two-pointer moves two pointers toward each other through *sorted* data.

**Homework**

| Task | Note |
|---|---|
| Finish the `smallest_window_at_least([2,1,5,2,3,2], 7)` trace by hand through `right=5` | Confirm the final `best_len` |
| Rewrite `max_sum_fixed` and `has_pair_sorted` from memory | Time yourself — both should be automatic within a few minutes |

Tell them: *"Sessions 4 and 5 both build on today — one of them turns the variable-window idea toward negative numbers, where the shrink step you just fixed doesn't work the same way. Come back knowing exactly why `while window_sum >= target` shrinks — that's about to matter."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Sliding window always means fixed size | Most people meet the fixed version first | Teaching Block B's explicit fixed-vs-variable framing |
| The window-leaving index is `arr[i]` or `arr[i-1]` | Off-by-one instinct, same family as prefix sum's `+1` | Teaching Block A's checkpoint — `arr[i-k]` specifically |
| A variable window's `left` can move backward if needed | Feels safer to "double check" | Teaching Block B's checkpoint — `left` only ever increases |
| `if window_sum >= target` is equivalent to `while` | Both look like they "check the condition" | ALS Activity 2 — the `[1,4,4]` trace shows the concrete failure |
| Two-pointer and sliding window are the same technique | Both use pointers/indices moving through an array | Teaching Block B's explicit contrast — one window vs. two pointers, unsorted vs. sorted |
| Two-pointer works on any array | The word "pointer" doesn't imply "sorted" | `has_pair_sorted`'s name and its reliance on sorted order to decide which pointer moves |

---

## Instructor Notes

- **⚠️ No video and no slide deck exist for this session.** It's newly added to the Sem-3 sequence (see `sem-3-sequence.md`) — both teaching blocks above are written as board-and-live-typing sessions built from standard sliding-window and two-pointer fundamentals, not from any platform export.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Guided Table Build (fixed-window tracing), Activity 2 is Silent Diagnose → Named Reveal (finding the missing shrink step in variable-window code).
- **This is session 3 of the new 6-session block** opening the Sem-3 sequence (Hashing → Prefix Sum → Sliding Window/Two-Pointer → Longest Subarray Sum K → Largest Subarray Sum → Two Sum).
- **The `smallest_window_at_least` trace in Teaching Block B is deliberately left half-worked on the page** — finish it live on the board through `right=5` before class so you have the exact `best_len` ready; don't present it as fully solved without having run it yourself first.
- **Flag explicitly that variable-window's shrink trick (Teaching Block B) assumes non-negative numbers.** This matters directly for Session 4, which handles the harder case where the array can include negatives and the shrink step from today no longer applies cleanly — that's genuinely a different technique (prefix sum + hash map, from Session 2), not a variant of today's.
- **Protect ALS Activity 2's `[1,4,4]` trace over anything else if the session runs behind.** The `if`-vs-`while` distinction it exposes is the single highest-value moment in the session — most real bugs in variable-window code are exactly this mistake.
