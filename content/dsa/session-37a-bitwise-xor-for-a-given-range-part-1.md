# Session 37a — Bitwise XOR For a Given Range (Part 1 of 2)

**Duration** 38 min · **Topic** Bit Manipulation — XOR Over a Range: Brute Force & the n%4 Identity · **Prerequisite** Min Bit Flips for OR Operation (Session 36) · **Session type** Concept lecture

<!-- Split note: original session-37 ran 50 min. Split right after the Classroom Quiz. Part 1 covers the brute-force approach and the optimal `n%4` prefix-XOR identity, including its derivation. Part 2 (session-37b) is hands-on practice applying the pattern, plus the structural "why does it repeat every 4" discussion — and closes the entire Bit Manipulation block. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Bitwise XOR For a Given Range | https://docs.google.com/presentation/d/17bNkI-vHKfJlll-Rasw2uhWcPEQNGHYyrQH3tM889gI/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the problem: given `left` and `right`, compute the XOR of every integer in the inclusive range `[left, right]`. *(REMEMBERING)*
2. Explain the brute-force approach — iterate the range, XOR-accumulating as you go — and its `O(right - left)` cost. *(UNDERSTANDING)*
3. Explain the identity `XOR(left…right) = XOR(1…right) ^ XOR(1…left-1)`, and why prefix-XOR cancellation makes this valid. *(UNDERSTANDING)*
4. State and apply the `n % 4` pattern for computing `XOR(1…n)` in constant time (remainder 0 → `n`; 1 → `1`; 2 → `n+1`; 3 → `0`). *(APPLYING)*

*(Applying the pattern hands-on, and the structural reason it repeats every 4, are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 36 (Min Bit Flips for OR Operation) (0–6 min)

Say: *"Six on yesterday's bit-by-bit OR rule table, then we shift from checking single bit positions to XOR-ing an entire numeric range."*

**Q1.** In the Min Bit Flips for OR problem, if `z`'s bit is `1` and both `x`,`y`'s bits are `0`, the flip cost at that position is:
`A` 0 · `B` 1 · `C` 2 · `D` Undefined
→ **Answer:** B.

**Q2.** If `z`'s bit is `0`, the flip cost at that position equals:
`A` Always 0 · `B` Always 1 · `C` The sum of `x`'s bit and `y`'s bit at that position · `D` Always 2
→ **Answer:** C.

**Q3.** What is the maximum possible flip cost for a single bit position?
`A` 1 · `B` 2 · `C` 3 · `D` Unbounded

**Q4.** The loop in that algorithm terminates when:
`A` It has run exactly 32 times · `B` `x`, `y`, and `z` have all become 0 · `C` `z` alone becomes 0 · `D` It never terminates
→ **Answer:** B.

**Q5.** Time complexity of the Min Bit Flips for OR algorithm?
`A` `O(max_bits)`, effectively `O(1)` for fixed-width integers · `B` `O(n log n)` · `C` `O(n²)` · `D` `O(log n)`
→ **Answer:** A.

**Q6 (MSQ — pick all correct).** Which are true of that session's rule table?
`A` A `z`-bit of 1 never costs more than 1 flip · `B` A `z`-bit of 0 can cost up to 2 flips · `C` The same rule applies regardless of `z`'s bit value · `D` The rule depends entirely on what `z`'s bit is at that position

**Running it** — poll tool, ~30 s per question. Total 6 min including reads.

---

## Hook (6–9 min)

Ask: *"XOR every integer from 5 to 10, one by one — that's not hard for six numbers. Now do it for every integer from 5 to 10 million. Same six-number pattern, or is there a shortcut?"*

Let students react. Then:

> *"There's a genuine shortcut — and it depends on an idea you haven't used yet: XOR-ing from 1 up to some number `n` follows a repeating pattern based on `n`'s remainder when divided by 4. Once you know that pattern, XOR over *any* range collapses to two lookups and one XOR — regardless of how wide the range is."*

---

## Slide Block A (9–18 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 4–22: Problem Statement, Examples, Brute Force Approach, Dry Run, Pseudocode, Complexity, Code -->
Covers: problem statement (XOR every integer in `[left, right]` inclusive) → Example 1 (`left=5, right=10` → `15`) → Example 2 (`left=7, right=13` → `6`) → brute force: initialize `ans=0`, iterate `i` from `left` to `right`, `ans = ans ^ i` → dry run on `[5,10]`: `0^5=5 → 5^6=3 → 3^7=4 → 4^8=12 → 12^9=5 → 5^10=15` → pseudocode → complexity (`O(right - left)` time — one iteration per number in range; `O(1)` space) → C++/Python code.

**Beats to emphasise**

- State the brute force in one line: *"start at 0, XOR in every number from `left` to `right` in order — nothing clever, just a running accumulator, exactly like Session 35's XOR-cancellation loop but over a contiguous range instead of an array."*
- **Say explicitly what's expensive about it:** for a range like `[5, 10,000,000]`, this approach genuinely performs ten million XOR operations — the range's *width*, not its content, drives the cost.
- Complexity is entirely proportional to the range's width, `right - left + 1` — not to the size of the numbers themselves.

**Checkpoint (at 18 min)** — cold-call:
> *"What does the brute-force approach's cost actually scale with — the size of `left` and `right` as numbers, or something else?"*
> **Answer:** The *width* of the range, `right - left + 1` — not the numeric magnitude of `left` or `right` individually. A range from 1 to 10 costs the same as a range from 999,991 to 1,000,000.

---

## Slide Block B (18–30 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 23–41: Optimal Approach, full Dry Run, Pseudocode, Complexity, Code, Logical Approach derivation (slides 69–93 mirror this with the n%4 pattern's algebraic derivation) -->
Covers: optimal approach — use the identity `XOR(left…right) = XOR(1…right) ^ XOR(1…left-1)`, computed via a helper `xorOnetoN(n)` that returns `n` if `n%4==0`, `1` if `n%4==1`, `n+1` if `n%4==2`, `0` if `n%4==3` → full dry run on `left=5, right=10`: `xorOnetoN(10)`: `10%4=2` → return `11`; `xorOnetoN(4)`: `4%4=0` → return `4`; combine `11 ^ 4 = 15` → algebraic derivation of the `n%4` pattern itself, built up recursively as `f(i) = f(i-1) ^ i` for `f(1)` through `f(10)`, observing the pattern repeats every four consecutive values of `n` → pseudocode → complexity (`O(1)` time — two constant-time helper calls plus one XOR; `O(1)` space) → C++/Python code.

**Beats to emphasise**

- **Say the identity as one sentence, this is the whole session:** *"XOR-ing 1 through `left-1` and then XOR-ing that same prefix again as part of `1` through `right` makes the shared prefix cancel out completely — via `a^a=0` — leaving exactly the XOR of `left` through `right`."* This is a direct reuse of Session 35's pairwise-cancellation idea, just applied to a prefix range instead of individual array pairs.
- **Walk the `n%4` pattern derivation carefully, using the deck's own recursive buildup** (`f(1)=1, f(2)=3, f(3)=0, f(4)=4, f(5)=1, f(6)=7, f(7)=0, f(8)=8, ...`) — the pattern of `{n, 1, n+1, 0}` repeating every four values is something students should see emerge from the recursion, not just memorize as a rule.
- Contrast complexity directly: brute force is `O(right-left)`; the optimal approach is `O(1)` regardless of range width, because `xorOnetoN` never loops — it only checks a remainder and returns a constant-time result.

**Checkpoint (at 30 min)** — cold-call:
> *"Why does XOR-ing `1` through `right` and `1` through `left-1` together correctly cancel down to just `left` through `right`?"*
> **Answer:** Both prefixes share the identical sub-range `1` through `left-1`. XOR-ing something with itself cancels to `0` (`a^a=0`), so that shared portion disappears entirely, leaving only the part that `1…right` had but `1…left-1` didn't — which is exactly `left` through `right`.

---

## Classroom Quiz (30–35 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Silent Board Race (35–38 min)

**Why this strategy here:** the `n%4` pattern is a four-case lookup table — exactly the kind of fact that benefits from fast, repeated, low-stakes retrieval before students apply it unaided in Part 2.

**Run it (3 minutes):**
> *"Two teams, two board halves. I call a number, first team to write its remainder mod 4 AND the correct `xorOnetoN` return rule (not the numeric answer, just which of the four cases applies) scores a point."*

Call 4-5 numbers fast (e.g., 9, 14, 21, 28). Keep score loosely.

> *"That's the lookup half of the formula, fast. Part 2 is where you put both halves together — the lookup and the combine — on ranges you haven't seen."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `XOR(left…right)` can be computed as `xorOnetoN(right) - xorOnetoN(left)` (subtraction instead of XOR) | The identity superficially resembles a prefix-sum-style range formula, where subtraction is standard | State plainly, and show with a worked example: prefix cancellation for XOR requires XOR-ing the two prefixes together (since `a^a=0`), not subtracting — subtraction doesn't have the matching cancellation property |
| The optimal approach only works for ranges that start at 1 | The helper function is explicitly named `xorOnetoN`, which can read as "only for ranges from 1" | Slide Block B — pointing out `xorOnetoN` is always called on `right` and `left-1` as an internal step, but the *range itself* can start anywhere; the two-call combination is what generalizes it to arbitrary `left` |

---

## Instructor Notes

- **This is Part 1 of a 50-minute original session, split right after the Classroom Quiz.**
- **The subtraction-vs-XOR misconception is worth actively watching for**, since it's the most natural-looking wrong answer a student familiar with prefix-sum techniques (from arrays or ranges elsewhere) would produce.
- Part 2 (session-37b) reuses this part's `n%4` table directly — no need to re-derive it there.
