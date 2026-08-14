# Session 6 — Two Sum Problem

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Two Sum — One-Pass Hash Map · **Prerequisite** Session 1 — Hashing (this session finishes what `has_pair_with_sum` started)
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

1. State the Two Sum problem precisely: return the *indices* of two numbers summing to a target, not just whether a pair exists. *(REMEMBERING)*
2. Implement the one-pass hash map solution in O(n) time. *(APPLYING)*
3. Explain why the map stores `value → index`, not `index → value`. *(UNDERSTANDING)*
4. Correctly handle duplicate values without reusing the same index twice. *(ANALYZING)*
5. Contrast the one-pass approach against a two-pass version (build the map first, then scan) and state why one-pass is strictly better or equal. *(ANALYZING)*
6. Recognise Two Sum as the named, index-returning version of Session 1's `has_pair_with_sum`. *(UNDERSTANDING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Sessions 1–5 (3–7 min) · ALS: Polling

5 questions spanning the whole block so far. ~45 s each, project the distribution, never name individuals.

**Q1.** *(Session 1)* What did `has_pair_with_sum` use a hash set for?
`A` To sort the array first · `B` To check, in O(1), whether the complement of the current number had already been seen · `C` To count duplicates · `D` To reverse the array
→ **B.**

**Q2.** *(Session 4)* Why does the longest-subarray-sum-k hash map need to keep the *earliest* index for each prefix sum?
`A` It doesn't matter which index is kept · `B` A later index can only shrink the computed length, never grow it · `C` Python requires it · `D` Earliest indices are always 0
→ **B.**

**Q3.** *(Session 5)* On an all-negative array, what should Kadane's algorithm return?
`A` 0 · `B` The single largest (least negative) element · `C` An error · `D` The smallest element
→ **B.**

**Q4.** *(Session 3)* What requirement does the two-pointer (opposite-ends) technique have that sliding window doesn't?
`A` No negative numbers · `B` The data must be sorted · `C` A fixed window size · `D` No duplicates allowed
→ **B.**

**Q5.** *(MSQ — select all that apply, Session 1)* True about `first_duplicate`'s hash-set version?
`A` O(n) time · `B` O(n²) time · `C` Turns a nested loop into a single pass · `D` Requires the array to be sorted first
→ **A, C.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–9 min)

Put Session 1's `has_pair_with_sum` back on the board, exactly as it was:

```python
def has_pair_with_sum(nums, target):
    seen = set()
    for num in nums:
        if (target - num) in seen:
            return True
        seen.add(num)
    return False
```

Ask: *"This tells you yes or no. In an actual interview, or an actual program, when would 'yes, a pair exists' ever be a satisfying final answer on its own?"*

Let the room land on: *"Never — you need to know **which** two numbers. Or more precisely, in this exact problem, which two *positions*."*

> *"That's Two Sum. Same core idea as Session 1 — you're not changing the technique, you're changing what you hand back at the end. `True` becomes two indices. That one change is almost the entire session — and the one place it gets subtle is exactly where today's activities live."*

---

## Teaching Block A (9–17 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from standard hashing fundamentals -->

**1. The problem, stated precisely.**

> *"Given an array `nums` and a `target`, return the indices of the two numbers that add up to `target`. Assume exactly one valid answer exists, and you may not use the same index twice."*

**2. The naive version — the starting point students already half-know.**

```python
def two_sum_naive(nums, target):
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] + nums[j] == target:
                return [i, j]
```

> *"What's the time complexity?"* — **O(n²)**. Now the one-pass fix:

```python
def two_sum(nums, target):
    seen = {}                     # value -> index
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i
    return []
```

**3. Trace it live.** `nums = [2, 7, 11, 15]`, `target = 9`.

| `i` | `num` | `complement = target - num` | `complement in seen`? | `seen` after |
|---|---|---|---|---|
| 0 | 2 | 7 | no | `{2: 0}` |
| 1 | 7 | 2 | **yes, at index 0** | return `[0, 1]` |

> **Answer: `[0, 1]`** — `nums[0] + nums[1] = 2 + 7 = 9`.

**Beats to emphasise**

- **The map stores `value → index`, not `index → value`.** Say why explicitly: you're always searching *by value* (the complement), so the value has to be the key.
- **Check the complement *before* adding the current number.** This single ordering decision is what prevents using the same index twice — it gets its own full treatment in Teaching Block B.
- **This is the exact shape of `has_pair_with_sum`, with one difference: the map stores indices, not just membership.** A `set` answers "have I seen this value." A `dict` answers "have I seen this value, and if so, where."

**Checkpoint (at 17 min)** — 10 s silent think, cold-call:
> *"Why does `seen` map `value → index` and not `index → value`?"*
> **Answer:** Every lookup is "have I already seen the number `target - num`" — a search *by value*. If the map were `index → value`, finding a given value would mean scanning every entry, defeating the O(1) lookup.

---

## ⚡ ALS Activity 1 — Guided Table Build: Trace Two Sum (17–24 min)

**ALS format:** Guided Table Build — the class traces the one-pass algorithm together on an array where the answer isn't at the very start, cold-called column by column. Chosen right after Teaching Block A because the Hook's example resolves in one step — this activity needs the algorithm to actually run for a few iterations before finding anything, so "check complement, then store" becomes a real habit, not a one-shot lucky pattern.

**Setup line:**
> *"New array, new target. I point at a column, you compute it. Say the complement out loud before you check whether it's in the map — don't skip straight to the answer."*

```
nums = [3, 5, -4, 8, 11, 1, -1, 6]
target = 10
```

**The completed trace**

| `i` | `num` | `complement` | in `seen`? | `seen` after |
|---|---|---|---|---|
| 0 | 3 | 7 | no | `{3:0}` |
| 1 | 5 | 5 | no | `{3:0, 5:1}` |
| 2 | -4 | 14 | no | `{3:0, 5:1, -4:2}` |
| 3 | 8 | 2 | no | `{3:0, 5:1, -4:2, 8:3}` |
| 4 | 11 | -1 | no | `{..., 11:4}` |
| 5 | 1 | 9 | no | `{..., 1:5}` |
| 6 | -1 | 11 | **yes, at index 4** | return `[4, 6]` |

**Answer: `[4, 6]`** — `nums[4] + nums[6] = 11 + (-1) = 10`.

**How it surfaces:** the answer isn't found until the 7th element — good, it forces every row to actually be worked through rather than the room recognising the pair by eye and skipping ahead.

**When it goes wrong**

| If… | Do this |
|---|---|
| A student jumps to `[4, 6]` without tracing the rows in between | Make them state the complement for every skipped row anyway — the habit is the point, not just the final answer |
| Someone computes the complement wrong on a negative number (row 2 or 4) | Redo the subtraction out loud: `target - num`, e.g. `10 - (-4) = 14` |

**Debrief line:**
> *"Six misses before the hit. That's normal — most real inputs don't resolve on the first try. The map just has to be right every single step, hit or miss."*

**Cut rule:** Trace through row 4, then state the final answer directly.

---

## Teaching Block B (24–32 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from standard hashing fundamentals -->

**1. Duplicate values — the case that breaks a careless implementation.**

```python
nums = [3, 3]
target = 6
```

> *"Two 3s. `3 + 3 = 6`. The answer should be `[0, 1]`. Trace it — does the correct algorithm still work?"*

| `i` | `num` | `complement` | in `seen`? | `seen` after |
|---|---|---|---|---|
| 0 | 3 | 3 | no *(seen is empty)* | `{3: 0}` |
| 1 | 3 | 3 | **yes, at index 0** | return `[0, 1]` |

> *"It works — because at `i=0`, `seen` is still empty. The complement check happens before `3` gets added, so index 0 can never accidentally match itself."*

**2. The order that makes this safe — check, then store, never the reverse.**

> *"Watch what happens if you flip the order — store first, check second."*

```python
def two_sum_broken(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        seen[num] = i                    # bug: stores BEFORE checking
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
    return []
```

Trace on `nums = [3, 3]`, `target = 6`:

| `i` | `num` | `seen` after storing | `complement` | in `seen`? |
|---|---|---|---|---|
| 0 | 3 | `{3: 0}` *(stored before checking!)* | 3 | **yes, at index 0** — but that's `nums[0]` matching itself |

> **Broken result: `[0, 0]`** — the same index used twice, which the problem explicitly forbids. The correct version never produces this, because it never lets a number see itself in the map.

**3. One-pass vs. two-pass.**

> *"A two-pass version builds the whole map first, then scans again looking up complements. Does that ever find something one-pass misses?"*

Let the room reason it out: **no** — anything findable in two passes is findable in one, because by the time you'd look up a complement, everything before it is already in the map either way. One-pass does the identical job with half the iteration.

**Beats to emphasise**

- **"Check complement, then store" is not a stylistic choice — it's the one line that prevents self-matching.** Flag this explicitly; it's this session's single highest-value line of code.
- **Two Sum guarantees exactly one valid answer** (per the problem statement) — that's *why* returning on the first hit is safe. A version of the problem allowing multiple valid pairs would need different handling, not covered today.
- **This is O(n) time, O(n) space** — same trade Session 1 and Session 4 both made. Naming the pattern again reinforces that it's a family, not three separate tricks.

**Checkpoint (at 32 min)** — show hands:
> *"In the broken version, `seen[num] = i` runs before the complement check. On `nums = [3, 3]`, `target = 6`, what wrong answer does that produce, and why?"*
> **Answer:** `[0, 0]` — because index 0's own value `3` gets stored into `seen` before the check happens, so `3`'s complement (`3`) immediately matches against itself.

---

## ⚡ ALS Activity 2 — Rapid Fire Board Race: Two Sum Speed Round (32–39 min)

**ALS format:** Board Race — teams race to find the correct index pair for each array/target combo, first team with both the right indices *and* the correct complement shown for the winning step takes the round. Chosen as the closing activity because, by this point in the block, speed and accuracy under the correct check-then-store discipline is exactly the transferable skill — not learning something new.

**Setup line:**
> *"Four rounds. I show an array and a target, you race to the board with the two indices — and the complement check that found them. Right indices, no shown reasoning, doesn't win the round."*

**The rounds**

| # | `nums` | `target` | Answer | Found because |
|---|---|---|---|---|
| 1 | `[1, 2, 3, 4]` | `7` | `[2, 3]` | at `i=3`, `num=4`, complement `3` already seen at index 2 |
| 2 | `[10, 15, 3, 7]` | `17` | `[0, 3]` | at `i=3`, `num=7`, complement `10` already seen at index 0 |
| 3 | `[-1, -2, -3, -4, -5]` | `-8` | `[2, 4]` | at `i=4`, `num=-5`, complement `-3` already seen at index 2 |
| 4 | `[5, 5, 5]` | `10` | `[0, 1]` | at `i=1`, `num=5`, complement `5` already seen at index 0 *(not index 1 or 2 — earliest occurrence wins by construction, since the check happens before storing)* |

**How it surfaces:** round 4 (three identical values) is the trap — a team that isn't tracing carefully might grab the wrong index pair, or hesitate because "which 5?" feels ambiguous. It isn't: the algorithm resolves it deterministically.

**When it goes wrong**

| If… | Do this |
|---|---|
| A team gets round 3 wrong (negative numbers) | Redo the complement subtraction live: `target - num`, e.g. `-8 - (-5) = -3` |
| Round 4 causes hesitation | Ask: "at `i=1`, is index 0's value already in the map or not?" — walk it back to the same check-before-store rule from Teaching Block B |

**Debrief line:**
> *"Every round was the same six lines of code. What changed was just the numbers — that's exactly what 'the technique transfers' is supposed to feel like."*

**Cut rule:** Run rounds 1 and 4 only — one straightforward case, one edge case with duplicates.

---

## Classroom Quiz (39–44 min) · Reserved — not yet available

No quiz bank exists yet for this topic (new to the Sem-3 sequence — see Resources table). This slot is reserved here, at the end of the session and right before the Exit Ticket, so the plan doesn't need restructuring once a bank exists. Until then, use it for an instructor-led review of today's toughest moment — re-run the duplicate-values trace (`[3, 3]`, `target=6`) one more time, cold-calling a different student for each step — or fold the slot into Buffer and end early.

---

## Exit Ticket + Homework (44–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> Write the one-pass Two Sum function from memory, and state in one sentence why checking the complement must happen *before* storing the current number.
> **Answer:** Checking first prevents a number from matching against itself when the array contains duplicate or repeated values — storing first would let index `i` find itself as its own "earlier" occurrence.

**Homework**

| Task | Note |
|---|---|
| Trace `two_sum([8, 2, 5, -1, 9, 3], target=4)` by hand, full table | State the final index pair |
| Look up "Three Sum" — read only the problem statement, don't attempt to solve it | One sentence: how does it relate to today's technique? *(No need to solve it — this is a look-ahead, not homework to complete.)* |

Tell them: *"Six sessions, one throughline: turn a nested loop into a single pass using a hash map, a prefix sum, or a running decision. That's the entire block. Linked Lists start next session — genuinely new territory, not a variation on today."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The map should store `index → value` | Feels like the "natural" direction, matching array order | Teaching Block A's checkpoint — lookups are always by value |
| Storing before checking is a harmless reordering | Both lines run either way, order feels cosmetic | Teaching Block B's `[3,3]` trace — order is the entire difference between correct and using an index twice |
| Two Sum and `has_pair_with_sum` are unrelated problems | Different names, different-sounding requirements | The Hook's explicit callback — same technique, different return value |
| A two-pass version (build map, then scan) finds pairs one-pass misses | Feels more "thorough" | Teaching Block B's reasoning — nothing is findable in two passes that isn't findable in one |
| Duplicate values make Two Sum ambiguous or broken | "Which 5 do I use?" feels unresolved | ALS Activity 2 round 4 — the check-before-store order resolves it deterministically |

---

## Instructor Notes

- **⚠️ No video and no slide deck exist for this session.** It's newly added to the Sem-3 sequence (see `sem-3-sequence.md`) — both teaching blocks above are written as board-and-live-typing sessions built from standard hashing fundamentals, not from any platform export.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Guided Table Build (a multi-step trace that doesn't resolve immediately), Activity 2 is Rapid Fire Board Race (speed + accuracy drilling across four varied cases, including a duplicate-values trap).
- **This is session 6, the last of the new 6-session block** opening the Sem-3 sequence (Hashing → Prefix Sum → Sliding Window/Two-Pointer → Longest Subarray Sum K → Largest Subarray Sum → Two Sum). Session 7 onward moves into Linked Lists, genuinely new material — say this explicitly at the close, per the Exit Ticket homework note.
- **The check-before-store ordering (Teaching Block B) is this session's single highest-value idea** — it's the one line separating a correct one-pass solution from a subtly broken one, and it's exercised twice (Teaching Block B's worked trace, ALS Activity 2 round 4). Protect both over anything else if the session runs behind.
- **All numeric traces in this file have been hand-verified**, including the negative-number round in ALS Activity 2 and the duplicate-value edge cases in Teaching Block B. If you swap in different numbers, re-verify the trace before class.
- **Don't let "Three Sum" homework turn into a solve-it assignment.** It's a look-ahead only — flagged explicitly as "read the problem statement, don't attempt it" to prevent students from spending real time on a K-Sum generalisation this course hasn't taught the tools for yet.
