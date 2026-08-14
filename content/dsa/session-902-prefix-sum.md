# Session 2 — Prefix Sum

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Prefix Sum — Range Sum Queries, Precomputation · **Prerequisite** Session 1 — Hashing (the "precompute once, answer fast" habit this session extends)
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

1. Explain what a prefix sum array is and why it's built once, upfront. *(UNDERSTANDING)*
2. Build a prefix sum array from a given array. *(APPLYING)*
3. Answer any range-sum query in O(1) using a prefix sum array, after O(n) preprocessing. *(APPLYING)*
4. State the total complexity trade: O(n) build + O(1) per query, versus O(n) per query with no preprocessing. *(ANALYZING)*
5. Apply the identity `sum(i, j) = prefix[j] − prefix[i−1]` correctly, including the boundary case `i = 0`. *(APPLYING)*
6. Use a running prefix sum together with a hash map to count subarrays whose sum equals a target — a first look at the technique Session 4 builds in full. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 1 (3–7 min) · ALS: Polling

5 questions on **Session 1 (Hashing)**. ~45 s each, project the distribution, never name individuals.

**Q1.** What's the average-case time complexity of a lookup (`x in some_set`) on a Python `set`?
`A` O(n) · `B` O(1) · `C` O(log n) · `D` O(n²)
→ **B.**

**Q2.** What do we call it when two different keys hash to the same bucket?
`A` A crash · `B` A collision · `C` An overflow · `D` A duplicate
→ **B.**

**Q3.** In the `has_pair_with_sum` rewrite from Session 1, what did the hash set replace?
`A` The outer loop · `B` The inner loop · `C` The return statement · `D` The function definition
→ **B.** *Read:* Removing the inner loop is what turned O(n²) into O(n).

**Q4.** What's `counts.get("cherry", 0)` for, if `"cherry"` was never added to `counts`?
`A` Raises a KeyError · `B` Returns `None` · `C` Returns `0` · `D` Adds `"cherry"` with value 0
→ **C.** *Read:* Safe lookup with a default — comes up again today.

**Q5.** *(MSQ — select all that apply)* Which of these are true about hash maps?
`A` Average-case insert is O(1) · `B` Worst-case insert is always O(1) too · `C` A hash map trades memory for speed · `D` Python's `dict` is a hash map
→ **A, C, D.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–9 min)

Put this on the board:

```python
arr = [4, 2, 7, 1, 9, 3, 8, 5, 6, 0]   # imagine this has 100,000 elements

# Query: what's the sum of elements from index 2 to index 6?
```

Ask: *"Naive way — sum a slice, `sum(arr[2:7])`. What's the time complexity of one query?"* — **O(n)**.

> *"Fine for one query. Now imagine 100,000 queries come in, back to back, on the same array. What's the total cost?"*

Let them multiply it out — **O(n × q)**, potentially billions of operations.

> *"The array never changes between queries. We're re-adding the same numbers, over and over, every single time. Session 1 was 'compute the location once, don't search again.' Today is the same instinct applied to sums: **compute every possible running total once, then every query becomes one subtraction.**"*

---

## Teaching Block A (9–17 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from standard prefix-sum fundamentals -->

**1. Build a prefix sum array, live, on a small example.**

```python
arr    = [4, 2, 7, 1, 9]
prefix = [0, 4, 6, 13, 14, 23]
#         ^   ^  ^   ^   ^   ^
#         |   |  |   |   |   sum of first 5 elements
#         |   |  |   |   sum of first 4 elements
#         |   |  |   sum of first 3 elements
#         |   |  sum of first 2 elements
#         |   sum of first 1 element
#         sum of first 0 elements (always 0)
```

Build it on the board one cell at a time, cold-calling: *"`prefix[1]` is the sum of the first 1 element — what is it? `prefix[2]` — first 2 elements?"* Land the formula:

```
prefix[0] = 0
prefix[i] = prefix[i-1] + arr[i-1]
```

> *"`prefix` is always one element longer than `arr`. That leading 0 is not decoration — it's what makes the range formula work for queries starting at index 0. Watch."*

**2. The range-sum formula.**

```
sum(i, j) = prefix[j+1] - prefix[i]      # sum of arr[i..j], inclusive
```

Work the Hook's query live: *"Sum of `arr[2..6]`, using `prefix`?"*

```python
arr    = [4, 2, 7, 1, 9, 3, 8, 5, 6, 0]
prefix = [0, 4, 6, 13, 14, 23, 26, 34, 39, 45, 45]

sum(2, 6) = prefix[7] - prefix[2] = 34 - 6 = 28
# check: arr[2]+arr[3]+arr[4]+arr[5]+arr[6] = 7+1+9+3+8 = 28 ✔
```

**Beats to emphasise**

- **Build once, query forever.** O(n) to build `prefix`, then every single query after that is O(1) — a fixed subtraction, no matter how big the range.
- **`prefix[j+1] - prefix[i]`, not `prefix[j] - prefix[i]`.** The `+1` is the single most common bug in this topic — flag it now, it comes back in ALS Activity 2.
- **Total cost for q queries: O(n + q)**, not O(n × q). Say the comparison out loud against the Hook's naive total.

**Checkpoint (at 17 min)** — 10 s silent think, cold-call:
> *"Using the `prefix` array above, what's `sum(4, 8)` — and which two `prefix` values do you subtract?"*
> **Answer:** `prefix[9] - prefix[4] = 45 - 14 = 31`. Check: `arr[4..8] = 9+3+8+5+6 = 31` ✔

---

## ⚡ ALS Activity 1 — Guided Table Build: Build the Prefix Array (17–24 min)

**ALS format:** Guided Table Build — the class constructs a prefix sum array together, cell by cell, then answers three range queries using only the finished table. Chosen right after Teaching Block A because the `+1` offset in the range formula only becomes automatic once students have built the array themselves and immediately used it, not just watched it built.

**Setup line:**
> *"New array, blank prefix row underneath. I point at a cell, you give me the running total. Nobody skips ahead — every cell depends on the one before it."*

```
arr:     6   1   4   9   2   8   3
prefix:  0   _   _   _   _   _   _   _
```

**The completed table**

| Index | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|---|---|
| `arr` | — | 6 | 1 | 4 | 9 | 2 | 8 | 3 |
| `prefix` | 0 | 6 | 7 | 11 | 20 | 22 | 30 | 33 |

**Now answer, using only the table, no re-summing:**

1. `sum(1, 3)` (i.e. `arr[1]+arr[2]+arr[3]`) → `prefix[4] - prefix[1] = 20 - 6 = 14`
2. `sum(0, 6)` (the whole array) → `prefix[7] - prefix[0] = 33 - 0 = 33`
3. `sum(3, 3)` (just one element) → `prefix[4] - prefix[3] = 20 - 11 = 9`

**How it surfaces:** Query 3 is the trap — a single-element range. If a student computes `prefix[3] - prefix[3] = 0`, that's the off-by-one bug from Teaching Block A, live and real.

**When it goes wrong**

| If… | Do this |
|---|---|
| Someone uses `prefix[j] - prefix[i]` instead of `prefix[j+1] - prefix[i]` | Point at query 3 specifically — it exposes the bug immediately, a wrong answer of 0 for a range that clearly isn't empty. |
| Cell-building stalls | Say the running total out loud: "previous prefix value, plus this array element." |

**Debrief line:**
> *"That `+1` isn't a formula to memorise separately — it falls straight out of `prefix[0] = 0` meaning 'sum of nothing.' If you ever forget which index to use, ask what range gives you the whole array, and check your formula against that."*

**Cut rule:** Build the table together but run only queries 1 and 3 — query 3 is the one that must not be cut, it's the off-by-one exposure.

---

## Teaching Block B (24–33 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from standard prefix-sum fundamentals -->

**1. In Python — you rarely hand-build the array with a loop like the board version; this is the idiomatic form:**

```python
def build_prefix(arr):
    prefix = [0] * (len(arr) + 1)
    for i in range(len(arr)):
        prefix[i + 1] = prefix[i] + arr[i]
    return prefix

def range_sum(prefix, i, j):
    return prefix[j + 1] - prefix[i]
```

**2. A first look at prefix sums + hashing together — counting subarrays with a target sum.**

> *"Here's a harder question: not 'what's the sum of this range,' but 'how many ranges sum to exactly k?' Session 4 builds this technique in full — today, just the core idea."*

```python
def count_subarrays_with_sum(nums, k):
    count = 0
    running_sum = 0
    seen = {0: 1}          # empty prefix (sum 0) has occurred once, before we start

    for num in nums:
        running_sum += num
        # if (running_sum - k) has occurred before, a subarray summing to k ends here
        count += seen.get(running_sum - k, 0)
        seen[running_sum] = seen.get(running_sum, 0) + 1

    return count
```

Trace it live on `nums = [1, 2, 3]`, `k = 3`:

| Step | `num` | `running_sum` | `running_sum - k` | `seen.get(...)` | `count` | `seen` after |
|---|---|---|---|---|---|---|
| 1 | 1 | 1 | -2 | 0 | 0 | `{0:1, 1:1}` |
| 2 | 2 | 3 | 0 | **1** | **1** | `{0:1, 1:1, 3:1}` |
| 3 | 3 | 6 | 3 | **1** | **2** | `{0:1, 1:1, 3:1, 6:1}` |

> **Answer: 2 subarrays** — `[1, 2]` and `[3]`, both sum to 3.

**Beats to emphasise**

- **This is a running prefix sum, not a precomputed array.** No separate `prefix[]` list — just one running total, updated as you go. Same identity (`sum = k` becomes `running_sum - k` appearing before), applied on the fly.
- **`seen = {0: 1}` is the trick that catches subarrays starting at index 0.** Without it, a subarray from the very start that sums to exactly `k` would never register. Flag this explicitly — it's this session's version of the `+1` offset bug.
- **This is a preview, not the full technique.** Session 4 (Longest Subarray with Sum K) is where this gets its real depth — today's job is just planting the "running sum + hash map" combination so it isn't brand new later.

**Checkpoint (at 33 min)** — cold-call:
> *"In `count_subarrays_with_sum`, why does `seen` start as `{0: 1}` instead of an empty dict?"*
> **Answer:** So a subarray that starts at index 0 and happens to sum to exactly `k` is still counted — its "running sum before it started" is 0, which needs to already be in `seen`.

---

## ⚡ ALS Activity 2 — Rapid Fire Board Race: Query the Prefix Array (33–40 min)

**ALS format:** Board Race — teams race to answer range-sum queries using a shared prefix array already on the board, first team with the right number *and* the right subtraction shown wins the round. Chosen as the closing activity because speed under a finished prefix array is exactly the skill being tested — not building it, using it fast and correctly.

**Setup line:**
> *"Prefix array's already built, up on the board. I call a range, you race to write the subtraction and the answer. Right number with the wrong subtraction doesn't count — I want to see `prefix[?] - prefix[?]`."*

```
arr:     5   3   8   2   7   4   1   6
prefix:  0   5   8   16  18  25  29  30  36
```

**The queries**

| # | Range (inclusive) | Subtraction | Answer |
|---|---|---|---|
| 1 | `sum(0, 2)` | `prefix[3] - prefix[0]` | `16` |
| 2 | `sum(3, 5)` | `prefix[6] - prefix[3]` | `13` |
| 3 | `sum(5, 5)` | `prefix[6] - prefix[5]` | `4` |
| 4 | `sum(0, 7)` | `prefix[8] - prefix[0]` | `36` |

**How it surfaces:** Query 3 (single element) and query 4 (whole array) are the two edge cases most likely to expose an off-by-one slip — watch those two rounds closely.

**When it goes wrong**

| If… | Do this |
|---|---|
| A team writes `prefix[5] - prefix[5]` for query 3 | That's the missing `+1` bug again — ask what range that subtraction actually represents (an empty one). |
| A team re-sums from `arr` instead of using `prefix` | Stop the round — the whole point is not touching `arr` again. |

**Debrief line:**
> *"Every one of those was one subtraction. That's the entire payoff of building the array first — the hard work already happened, all today did was spend it."*

**Cut rule:** Run queries 1 and 3 only — one straightforward range, one edge case.

---

## Classroom Quiz (40–45 min) · Reserved — not yet available

No quiz bank exists yet for this topic (new to the Sem-3 sequence — see Resources table). This slot is reserved here, at the end of the session and right before the Exit Ticket, so the plan doesn't need restructuring once a bank exists. Until then, use it for an instructor-led review of today's toughest moment — re-run the `count_subarrays_with_sum` trace on a fresh small example, cold-calling a different student for each row — or fold the slot into Buffer and end early.

---

## Exit Ticket + Homework (45–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> Write the range-sum formula using a prefix array, and explain in one sentence why `prefix` is built with a leading 0.
> **Answers:** `sum(i, j) = prefix[j+1] - prefix[i]`. The leading 0 represents "sum of zero elements," which is what makes ranges starting at index 0 work correctly with the same formula.

**Homework**

| Task | Note |
|---|---|
| Build `build_prefix` and `range_sum` from memory, test on a 6-element array of your choice | Verify at least 3 different ranges by hand |
| Re-trace `count_subarrays_with_sum([1, -1, 1, 1], 1)` by hand, row by row | This one includes a negative number — prefix sums work identically, don't special-case it |

Tell them: *"Session 4 turns today's preview — running sum plus a hash map — into the full technique for the longest such subarray. If the `count_subarrays_with_sum` trace didn't fully land tonight, that's the one to redo before then."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `sum(i, j) = prefix[j] - prefix[i]` | Feels symmetric, no reason to expect a `+1` | ALS Activity 1 query 3 and the Board Race's edge-case rounds |
| Prefix sums need to be rebuilt for every query | Conflating "build" with "query" | Teaching Block A's O(n) build / O(1) query framing |
| The leading `prefix[0] = 0` is just padding | Doesn't look like it does anything | The range-formula derivation — it's what makes index-0 ranges work |
| `seen = {0: 1}` in the counting version is an arbitrary trick | No obvious reason without deriving it | Teaching Block B's checkpoint — subarrays starting at index 0 |
| Prefix sums only work for range totals, nothing else | Only range-sum is shown first | Teaching Block B's counting example — same idea, different question |

---

## Instructor Notes

- **⚠️ No video and no slide deck exist for this session.** It's newly added to the Sem-3 sequence (see `sem-3-sequence.md`) — both teaching blocks above are written as board-and-live-typing sessions built from standard prefix-sum fundamentals, not from any platform export.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Guided Table Build (constructing the array, then querying it), Activity 2 is Rapid Fire Board Race (speed drilling the query formula). Deliberately sequenced slow-then-fast — build understanding first, then drill it.
- **This is session 2 of the new 6-session block** opening the Sem-3 sequence (Hashing → Prefix Sum → Sliding Window/Two-Pointer → Longest Subarray Sum K → Largest Subarray Sum → Two Sum).
- **Teaching Block B's `count_subarrays_with_sum` is a deliberate preview, not a full teach.** Session 4 owns this technique properly. Don't let this session's version run long or go deeper than the trace shown — that's next session's job, and over-teaching it here steals its thunder.
- **The `+1` offset is this session's single highest-value repeated exposure.** It appears in the worked example, ALS Activity 1's query 3, and the Board Race's query 3 and 4 — that's by design, not redundancy. If time is short, protect all three exposures before protecting anything else.
- **The verify-live flag in the Teaching Block A checkpoint (`sum(4,8)`) needs a quick arithmetic check before class** — recompute against the board's own prefix array and adjust the numbers if anything doesn't land exactly on 25/31.
