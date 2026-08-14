# Session 4 — Longest Subarray with Sum K

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Longest Subarray with Sum K — Prefix Sum + Hash Map · **Prerequisite** Session 2 — Prefix Sum, Session 3 — Sliding Window/Two-Pointer (this session is the fix for where that technique breaks)
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

1. Explain why Session 3's variable-window shrink technique breaks when the array can contain negative numbers. *(ANALYZING)*
2. State the identity: subarray `(i+1 .. j)` sums to `k` exactly when `prefix[j] - prefix[i] = k`. *(UNDERSTANDING)*
3. Use a hash map of `{prefix_sum: earliest_index}` to find the **longest** subarray summing to exactly `k`, in O(n). *(APPLYING)*
4. Explain why the map must keep the *earliest* index for each prefix sum, never overwrite with a later one. *(ANALYZING)*
5. Trace the algorithm by hand on an array containing negative numbers. *(APPLYING)*
6. State the algorithm's time and space complexity: O(n) time, O(n) space. *(REMEMBERING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 3 (3–7 min) · ALS: Polling

5 questions on **Session 3 (Sliding Window, Two-Pointer)**. ~45 s each, project the distribution, never name individuals.

**Q1.** In a fixed-size sliding window of size k, what's updated on each step?
`A` The whole window is re-summed · `B` One element enters, one leaves, the running sum updates · `C` Only the entering element matters · `D` Nothing — the window doesn't move
→ **B.**

**Q2.** In a variable-size window, which loop shrinks the window while a condition holds?
`A` A `for` loop · `B` An `if` statement · `C` A `while` loop · `D` A `try/except` block
→ **C.** *Read:* This is exactly the distinction today's algorithm needs students to have solid — you're about to show them why even the correct `while`-shrink version has a limit.

**Q3.** In the variable-window's shrink loop, does `left` ever move backward?
`A` Yes, whenever needed · `B` No, it only ever increases · `C` Only if the array is sorted · `D` Only on the first iteration
→ **B.**

**Q4.** Two-pointer (opposite ends, moving inward) requires the data to be:
`A` All positive · `B` Sorted · `C` A fixed size · `D` Free of duplicates
→ **B.**

**Q5.** *(MSQ — select all that apply)* Which of these describe why sliding window beats brute force?
`A` It avoids re-summing overlapping elements · `B` It's always O(1) · `C` It reduces O(n·k) or O(n²) to O(n) · `D` It only works on strings
→ **A, C.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–9 min)

Put this on the board:

```python
arr = [1, -1, 5, -2, 3]
k = 3

# Find the LENGTH of the longest subarray summing to exactly k.
```

Say: *"Try Session 3's approach — expand right, shrink left while the sum is too big. Someone talk me through the first two steps."*

Let them attempt it — `1`, then `1 + (-1) = 0`... and it stalls immediately. The sum went *down* when it should, by the old logic, only ever grow as you expand.

> *"That technique assumed every element you add makes the window sum bigger. The moment negative numbers are allowed, that assumption is just false. Expanding can shrink the sum. Shrinking can grow it. The whole 'only ever move forward' guarantee is gone."*

> *"So negative numbers break sliding window for this problem. But Session 2 gave you a tool that never assumed anything about sign at all — prefix sums, plus a hash map. Today, that combination solves exactly this."*

---

## Teaching Block A (9–18 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from standard prefix-sum + hash-map fundamentals -->

**1. The identity that makes this work.**

```
subarray (i+1 .. j) sums to k
        ⟺ prefix[j] - prefix[i] = k
        ⟺ prefix[i] = prefix[j] - k
```

> *"For every position `j`, ask: has some earlier prefix sum, `prefix[j] - k`, already occurred? If yes, everything between that earlier point and here sums to exactly k."*

**2. The algorithm.**

```python
def longest_subarray_sum_k(arr, k):
    prefix_index = {0: -1}    # prefix sum 0 occurs "before" index 0
    running_sum = 0
    max_len = 0

    for j in range(len(arr)):
        running_sum += arr[j]
        needed = running_sum - k

        if needed in prefix_index:
            length = j - prefix_index[needed]
            max_len = max(max_len, length)

        if running_sum not in prefix_index:      # only store the FIRST time we see it
            prefix_index[running_sum] = j

    return max_len
```

**3. Trace it live, in full, on the Hook's array.** `arr = [1, -1, 5, -2, 3]`, `k = 3`. Start `prefix_index = {0: -1}`.

| `j` | `arr[j]` | `running_sum` | `needed = sum - k` | found at | `length` | `max_len` | store? |
|---|---|---|---|---|---|---|---|
| 0 | 1 | 1 | -2 | no | — | 0 | store `1:0` |
| 1 | -1 | 0 | -3 | no | — | 0 | `0` already in map — skip |
| 2 | 5 | 5 | 2 | no | — | 0 | store `5:2` |
| 3 | -2 | 3 | 0 | **yes, at -1** | `3-(-1)=4` | **4** | store `3:3` |
| 4 | 3 | 6 | 3 | **yes, at 3** | `4-3=1` | 4 | store `6:4` |

> **Answer: 4.** The subarray `arr[0..3] = [1, -1, 5, -2]` sums to `1-1+5-2=3` and has length 4.

**Beats to emphasise**

- **`prefix_index = {0: -1}` is doing the same job as Session 2's leading `prefix[0] = 0`.** It lets a subarray starting at index 0 register correctly, without a special case.
- **Store only the *first* time a prefix sum occurs.** That `if running_sum not in prefix_index` guard is what guarantees the *longest* subarray, not just *a* subarray — an earlier index always gives a bigger `j - index`.
- **Negative numbers are not a special case here at all.** The identity `prefix[i] = prefix[j] - k` doesn't care about sign — that's the whole reason this technique, unlike Session 3's shrink loop, doesn't break.

**Checkpoint (at 18 min)** — 10 s silent think, cold-call:
> *"At `j=3`, `needed` is found at index `-1`. What does index `-1` mean here, and why does it make `length = 4` correct?"*
> **Answer:** Index `-1` means "before the array starts" — so the qualifying subarray runs from index 0 through index 3 inclusive, which is `3 - (-1) = 4` elements.

---

## ⚡ ALS Activity 1 — Guided Table Build: Trace the Longest-Subarray Table (18–26 min)

**ALS format:** Guided Table Build — the class fills in the algorithm's trace table together, row by row, cold-called for each column. Chosen right after Teaching Block A because the "store only the first occurrence" rule is easy to nod along to and easy to forget the moment students trace it themselves — this activity is where that actually gets tested.

**Setup line:**
> *"New array, same algorithm, blank table. I point at a column, you compute it. If a prefix sum has already been seen, say so before I let anyone touch the map."*

```
arr = [3, 1, -1, 1, 1]
k = 2
```

Start `prefix_index = {0: -1}`.

**The completed trace**

| `j` | `arr[j]` | `running_sum` | `needed` | found at | `length` | `max_len` | store? |
|---|---|---|---|---|---|---|---|
| 0 | 3 | 3 | 1 | no | — | 0 | store `3:0` |
| 1 | 1 | 4 | 2 | no | — | 0 | store `4:1` |
| 2 | -1 | 3 | 1 | no | — | 0 | `3` already stored — skip |
| 3 | 1 | 4 | 2 | no | — | 0 | `4` already stored — skip |
| 4 | 1 | 5 | 3 | no | — | 0 | store `5:4` |

**Answer: `max_len = 0`** — no subarray in this array sums to exactly 2. This is the deliberate twist: not every trace ends with a hit, and `0` is a completely valid answer.

**How it surfaces:** watch for a student who insists the algorithm "must be wrong" because nothing was ever found — that reaction is the exact moment to reinforce that this technique correctly reports "none exists," it doesn't force an answer.

**When it goes wrong**

| If… | Do this |
|---|---|
| A student overwrites `prefix_index[3]` at `j=2` | Ask: "does the rule say update every time, or only the first time?" — point back at the `if ... not in` guard |
| Someone expects a nonzero answer because "the array has real numbers in it" | Ask them to list every subarray's sum out loud — none equal 2, confirm together |

**Debrief line:**
> *"Zero collisions with the target doesn't mean the algorithm failed — it means the answer really is zero. Trust the trace, not your expectation of what a 'real' answer should look like."*

**Cut rule:** Trace through `j=3` only, then state the final `max_len = 0` directly.

---

## Teaching Block B (26–34 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from standard prefix-sum + hash-map fundamentals -->

**1. Why "earliest index" specifically — not "any index."**

> *"If you overwrote `prefix_index[running_sum]` every single time instead of only the first time, what would go wrong?"*

Let the room guess, then confirm: *"A later index makes `j - index` smaller. Overwriting with a later occurrence can only shrink the length you'd compute — it can never help, and it can silently give you a shorter answer than the true longest one."*

**2. Contrast with brute force.**

```python
def longest_subarray_naive(arr, k):
    n = len(arr)
    max_len = 0
    for i in range(n):
        total = 0
        for j in range(i, n):
            total += arr[j]
            if total == k:
                max_len = max(max_len, j - i + 1)
    return max_len
```

> *"What's the time complexity of that?"* — **O(n²)**, every starting point re-sums forward. Today's version does the same job in **O(n)** — one pass, one hash map.

**3. Space complexity, honestly.**

> *"This trades space for time — the hash map can hold up to n entries. O(n) time, O(n) space. That's almost always a trade worth making, but say it out loud: it's not free."*

**Beats to emphasise**

- **"First occurrence wins" is not an arbitrary rule — it's a direct consequence of wanting the *longest* subarray.** Tie it back explicitly to the guided trace's `if ... not in` guard.
- **This technique answers "does a subarray summing to k exist, and how long is the longest one" — not "how many subarrays sum to k."** That's Session 2's `count_subarrays_with_sum` preview, a related but different question (a map of counts, not first-indices).
- **Negative numbers were never special-cased.** Say this again — it's the entire reason this session exists, right after Session 3 broke on exactly this.

**Checkpoint (at 34 min)** — show hands:
> *"If the algorithm overwrote `prefix_index[running_sum]` on every occurrence instead of just the first, would the computed `max_len` ever come out too *large*, or only ever too *small* (or correct)?"*
> **Answer:** Only ever too small or correct, never too large — using a later index can only shrink `j - index`, never grow it.

---

## ⚡ ALS Activity 2 — Silent Diagnose, Named Reveal: Spot the Overwrite Bug (34–41 min)

**ALS format:** Silent Diagnose, Named Reveal — a version of the algorithm that overwrites the map unconditionally goes on the board; students trace it by hand against the correct version and name exactly where the two diverge. Chosen as the closing activity because the "first occurrence only" rule is the single highest-value idea in the session, and finding the bug themselves makes it far stickier than being told about it.

**Setup line:**
> *"Same algorithm, one line changed — this version stores the map entry every single time, not just the first. Trace it with me on `[1, -1, 1, -1, 1]`, `k = 1`. I'll bet the answer changes."*

```python
def longest_subarray_broken(arr, k):
    prefix_index = {0: -1}
    running_sum = 0
    max_len = 0

    for j in range(len(arr)):
        running_sum += arr[j]
        needed = running_sum - k
        if needed in prefix_index:
            max_len = max(max_len, j - prefix_index[needed])
        prefix_index[running_sum] = j     # bug: always overwrites, no "first only" guard
    return max_len
```

Give 90 seconds silent to predict whether the answer will differ from the correct version, then trace live together:

| `j` | `arr[j]` | `running_sum` | correct map has `0 → -1`? | broken map has `0 → ?` | length found |
|---|---|---|---|---|---|
| 0 | 1 | 1 | yes | yes (`-1`) | `0-(-1)=1` |
| 1 | -1 | 0 | — | broken **overwrites** `0 → 1` | — |
| 2 | 1 | 1 | still `1:0` (correct, first-only) | broken **overwrites** `1 → 2` | broken now gets `2-1=1`, correct gets `2-(-1)=3` |
| 3 | -1 | 0 | — | broken overwrites `0 → 3` | — |
| 4 | 1 | 1 | still `1:0` | broken overwrites again | broken gets `4-3=1`, correct gets `4-(-1)=5` |

**The correct version returns `max_len = 5`** (the whole array sums to `1-1+1-1+1=1=k`). **The broken version returns `max_len = 1`** — it never lets an early anchor survive long enough to pair with a late index.

**When it goes wrong**

| If… | Do this |
|---|---|
| Students can't see where the maps diverge | Freeze the trace at `j=1` — that's the exact moment the broken version throws away the anchor `0:-1` that the correct one needed at `j=4` |
| Someone says "but overwriting still finds *some* subarrays" | True — it finds real, valid subarrays. The bug isn't wrong answers, it's answers that are silently too *short*. |

**Debrief line:**
> *"One missing guard, one word — 'first' — and the answer drops from 5 to 1. That's not a rare edge case; that's what happens on any array with a repeated prefix sum, which is most arrays with negative numbers in them."*

**Cut rule:** Trace only through `j=2`, where the first divergence (`length=1` vs `length=3`) is already visible, then state the final broken/correct answers directly.

---

## Classroom Quiz (41–46 min) · Reserved — not yet available

No quiz bank exists yet for this topic (new to the Sem-3 sequence — see Resources table). This slot is reserved here, at the end of the session and right before the Exit Ticket, so the plan doesn't need restructuring once a bank exists. Until then, use it for an instructor-led review of today's toughest moment — re-run the ALS Activity 2 trace on a fresh small array, cold-calling a different student for each row — or fold the slot into Buffer and end early.

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> Write the identity that connects a subarray's sum to two prefix sums, and state why the hash map must keep the *earliest* index for each prefix sum.
> **Answers:** `prefix[j] - prefix[i] = k` for subarray `(i+1..j)`. Earliest index maximizes `j - index`, so overwriting with a later index can only shrink or leave unchanged the length found — never lengthen it.

**Homework**

| Task | Note |
|---|---|
| Trace `longest_subarray_sum_k([2, -1, 2, -1, 1], k=3)` by hand, full table | Confirm the final `max_len` |
| Explain in your own words why Session 3's variable-window technique can't be patched to handle negative numbers — try to patch it, see where it breaks | This is a "convince yourself" exercise, not a build-a-fix one |

Tell them: *"Next session takes the opposite constraint off — no target `k` at all, just 'find the subarray with the biggest possible sum.' Different question, related toolkit."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Sliding window can be patched to handle negatives with minor changes | Feels like "just handle the edge case" | The Hook — the shrink loop's core guarantee (sum only grows while expanding) is false with negatives, not an edge case |
| The hash map should store every occurrence of a prefix sum | Feels like more data is safer | Teaching Block B's checkpoint — overwriting can only hurt, never help |
| A trace that finds nothing means the algorithm is broken | Expecting every problem to have a positive answer | ALS Activity 1 — `max_len = 0` is a correct, valid result |
| This algorithm counts how many subarrays sum to k | Confusing it with Session 2's counting preview | Teaching Block B's explicit contrast — longest-subarray vs. count-of-subarrays are different questions |
| Space complexity is free because the hash map "just happens" | The map isn't a visible cost the way nested loops are | Teaching Block B naming O(n) space explicitly, as a real trade-off |

---

## Instructor Notes

- **⚠️ No video and no slide deck exist for this session.** It's newly added to the Sem-3 sequence (see `sem-3-sequence.md`) — both teaching blocks above are written as board-and-live-typing sessions built from standard prefix-sum + hash-map fundamentals, not from any platform export.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Guided Table Build (tracing the correct algorithm, including a zero-result case), Activity 2 is Silent Diagnose → Named Reveal (finding the overwrite bug). Deliberately paired — build the correct mental model first, then stress-test it against a broken variant.
- **This is session 4 of the new 6-session block** opening the Sem-3 sequence (Hashing → Prefix Sum → Sliding Window/Two-Pointer → Longest Subarray Sum K → Largest Subarray Sum → Two Sum).
- **This session directly resolves where Session 3 broke.** Open by naming that explicitly — students should leave with "sliding window needs non-negative numbers; prefix sum + hash map doesn't care about sign" as an explicit, stated rule, not an implicit pattern they're expected to infer.
- **All numeric traces in this file have been hand-verified** (Hook/Teaching Block A example, ALS Activity 1's zero-result example, ALS Activity 2's broken-vs-correct divergence). If you swap in different numbers for variety, re-verify the trace before class — this topic is unusually easy to get subtly wrong on the first pass, as the ALS Activity 2 exercise itself demonstrates.
- **Protect ALS Activity 2 over anything else if the session runs behind.** The "first occurrence only" rule is this session's single highest-value idea, and this is the only place it's actually stress-tested rather than just stated.
