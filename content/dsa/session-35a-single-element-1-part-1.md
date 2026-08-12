# Session 35a — Single Element 1 (Part 1 of 2)

**Duration** 35 min · **Topic** Bit Manipulation — Single Element: Brute Force, Hashmap & Optimal Approach · **Prerequisite** Minimum Bit Flips to Convert a Number (Session 34) · **Session type** Concept lecture

<!-- Split note: original session-35 ran 50 min. Split right after the Classroom Quiz. Part 1 covers all three approaches — brute force, hashmap, and the optimal XOR trick — with full dry runs. Part 2 (session-35b) is entirely hands-on: a live trace on fresh numbers and the "what if two elements are unique" precondition check. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Single Element 1 | https://docs.google.com/presentation/d/1ClShR7M2swFtCqCOCAR8gAMrJ-Nxs1Up6CMblULaRwo/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the problem: given an array where every element appears exactly twice except one, find the element that appears only once. *(REMEMBERING)*
2. Explain the brute-force approach — count every element's frequency by nested iteration — and its `O(n²)` cost. *(UNDERSTANDING)*
3. Explain the hashmap approach — count frequencies in one pass, then scan the map for the count-1 entry — and its `O(n)` time / `O(n)` space cost. *(UNDERSTANDING)*
4. Trace the optimal XOR approach: XOR every element together, relying on `a ^ a = 0` and `a ^ 0 = a` so all paired elements cancel out, leaving only the unique one. *(APPLYING)*
5. Explain why XOR-ing an entire array is order-independent — pairs cancel regardless of where they sit — and state the final complexity: `O(n)` time, `O(1)` space. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 34 (Minimum Bit Flips to Convert a Number) (0–6 min)

Say: *"Six on yesterday's XOR-to-find-differences trick, then we use that exact same XOR property for something new — finding one element instead of comparing two numbers."*

**Q1.** To find the minimum bit flips between `source` and `target`, the first step is:
`A` Add the two numbers · `B` XOR the two numbers · `C` Sort their bits · `D` Subtract the smaller from the larger
→ **Answer:** B.

**Q2.** After computing `source ^ target`, the flip count equals:
`A` The XOR result's decimal value · `B` The number of set bits in the XOR result · `C` The number of zero bits in the XOR result · `D` Always 1
→ **Answer:** B.

**Q3.** Why can't you estimate the flip count from the decimal difference between `source` and `target`?
`A` You can — they're the same thing · `B` Decimal difference has no reliable relationship to how many individual bit positions differ · `C` Decimal numbers don't have bits · `D` It only fails for negative numbers
→ **Answer:** B.

**Q4.** `N & (N-1)` is used in that session to:
`A` Set every bit to 1 · `B` Clear the rightmost set bit, for counting set bits one at a time · `C` Reverse all bits · `D` Multiply N by 2

**Q5.** Time complexity of the min-bit-flips algorithm?
`A` `O(log N)` always · `B` `O(number of set bits in the XOR result)` · `C` `O(N)` · `D` `O(N²)`
→ **Answer:** B.

**Q6 (MSQ — pick all correct).** Which XOR properties were used in that session?
`A` `a ^ a = 0` · `B` `a ^ 0 = a` · `C` `a ^ b` is 1 exactly where `a` and `b` disagree · `D` XOR is only defined for single bits, not full numbers

**Running it** — poll tool, ~30 s per question. Total 6 min including reads.

---

## Hook (6–9 min)

Ask: *"An array has a thousand numbers. Every single one shows up exactly twice — except one number, which shows up only once. Can you find that one number without counting anything?"*

Let students think. Then:

> *"You can — using the exact same XOR properties from yesterday, pushed one step further. Yesterday, XOR told us where two numbers *differed*. Today, XOR makes every *pair* in the array cancel itself out completely, leaving only the one number that had no partner. No counting, no hashmap, just one pass with XOR."*

---

## Slide Block A (9–19 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 4–37: Problem Statement, Examples, Brute Force Approach, Dry Run, Pseudocode, Complexity, Code, Better (hashmap) Approach, Dry Run, Pseudocode, Complexity, Code -->
Covers: problem statement (every element appears twice except one; return the unique one) → Example 1 (`arr=[7,7,9,8,8]` → `9`) → Example 2 (`arr=[25,26,27,25,26,28,27,29,29]` → `28`) → brute force: for each element, count its frequency across the whole array by nested iteration, return the one with frequency 1 → dry run on `[7,7,9,8,8]` → pseudocode → complexity (`O(n²)` time — nested loop; `O(1)` space) → code → better approach: build a frequency hashmap in one pass, then scan the map for the entry with count 1 → dry run building `{7:2, 9:1, 8:2}` and returning `9` → pseudocode → complexity (`O(n)` time — one pass to build, one pass to scan; `O(n)` space for the map, worst case `n/2 + 1` unique entries) → code.

**Beats to emphasise**

- State the brute force in one line: *"for every element, re-scan the whole array counting how many times it shows up — the one with count 1 is the answer."* Note explicitly this is `O(n²)` because every element triggers its own full scan.
- **The hashmap approach removes the nested loop** by counting once and looking up counts instead of recounting: *"one pass to build the map, one pass to find the count-1 entry — both `O(n)`, so the whole thing is `O(n)` instead of `O(n²)`."*
- Flag the hashmap's real cost honestly: *"we traded time for space — `O(n)` extra memory to hold the frequency map, worst case nearly one entry per pair."*

**Checkpoint (at 19 min)** — cold-call:
> *"What's the actual difference between the brute-force and hashmap approaches — do they count frequency differently, or the same way?"*
> **Answer:** They count frequency the same conceptual way — the difference is *how many times* the array gets scanned to get there. Brute force re-scans the whole array once per element (nested loop, `O(n²)`); the hashmap approach scans the array exactly once to build counts, then scans the map once to find the answer (`O(n)` total).

---

## Slide Block B (19–27 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 38–71: Optimal Approach (XOR), XOR Properties, full Dry Run, Pseudocode, Complexity, Code -->
Covers: optimal approach — XOR every element in the array together; result is the unique element → XOR properties (`a ^ a = 0`, `a ^ 0 = a`) → full dry run on `[7,9,8,7,8]`: `7^9^8^7^8` regrouped as `(7^7)^(8^8)^9 = 0^0^9 = 9` → pseudocode → complexity (`O(n)` time — single pass; `O(1)` space — one accumulator variable) → code.

**Beats to emphasise**

- **Say the mechanism as one sentence, this is the whole session:** *"XOR every element together — every number that has a partner cancels itself to zero via `a ^ a = 0`, and XOR-ing anything with the leftover zero via `a ^ 0 = a` just hands you the one number that never found a partner."*
- **Say explicitly why order doesn't matter:** XOR is commutative and associative, so `7^9^8^7^8` can be freely regrouped as `(7^7)^(8^8)^9` regardless of the original array order — the pairs find each other no matter where they sit in the array.
- Contrast the space cost directly against the previous two approaches: *"same `O(n)` time as the hashmap version, but `O(1)` space — no map, no nested loop, just one running XOR."*

**Checkpoint (at 27 min)** — cold-call:
> *"Why does XOR-ing the entire array in any order still produce the correct answer?"*
> **Answer:** XOR is commutative and associative — `a^b = b^a` and grouping doesn't matter — so every pair of identical elements will cancel to `0` regardless of the order they appear in, leaving only the unpaired element once all cancellations are done.

---

## Classroom Quiz (27–32 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Predict-and-Defend Pairs (32–35 min)

**Why this strategy here:** three approaches were just delivered back to back. Before Part 2's live trace, students should be able to predict which approach they'd reach for and defend the trade-off — not just recall that XOR is "the optimal one."

**Run it (3 minutes):**
> *"With your partner: if memory were tight but time wasn't, which approach would you pick — hashmap or XOR? What if both were tight? Agree on an answer and a one-sentence reason before I call on pairs."*

Take 2 pairs' answers. The honest answer for "both tight" is XOR — same time as hashmap, but O(1) space, no real trade-off left to make.

> *"Hold that answer. Part 2 has you run the XOR approach yourself, cold, on numbers you haven't seen."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The hashmap approach is "wrong" now that a better approach exists | Once the optimal solution is shown, earlier approaches can feel invalidated | State plainly: the hashmap approach is fully correct, just costs `O(n)` extra space the XOR approach avoids — there's no correctness difference, only a resource trade-off |
| Counting frequency (brute force or hashmap) and XOR-cancellation are two names for the same idea | Both approaches solve the identical problem and reach the identical answer | Contrast explicitly: counting approaches ask "how many times does this appear," while XOR asks nothing about counts at all — it relies purely on algebraic cancellation |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split right after the Classroom Quiz.**
- **This session directly reuses Session 34's XOR properties (`a^a=0`, `a^0=a`)** — say so explicitly; the only new idea is applying those properties across an entire array via one running accumulator, not to a single pair.
- Part 2 (session-35b) is entirely hands-on — no new slide content, just live practice and the two-unique-elements edge case.
