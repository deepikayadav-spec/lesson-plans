# Session 17 — Adding Two Numbers

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Linked List — Add Two Numbers (Digit by Digit, With Carry) · **Prerequisite** Session 16 — Length of Cycle
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Add Two Numbers | https://docs.google.com/presentation/d/1UFNX3HAh8y-V1tSh-HQdEB3rCHgKYFUIwOjv0ugKvzg/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the "Add Two Numbers" problem: two non-negative numbers stored as linked lists with digits in reverse order, summed into a resulting list. *(REMEMBERING)*
2. Explain why storing digits least-significant-first lets the algorithm add head-to-head instead of needing to reverse anything, and why a dummy head simplifies building the result. *(UNDERSTANDING)*
3. Dry-run the digit-by-digit addition with carry propagation, including the case where a final carry creates an extra node. *(APPLYING)*
4. Justify why the algorithm's time and space complexity is O(max(M, N)), not O(M + N). *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 16 (3–7 min) · ALS: Polling

5 questions on **Session 16 (Length of Cycle)**. ~45 s each, project the distribution, never name individuals.

**Q1.** In the brute-force "length of cycle" approach, what does the map store alongside each node?
`A` Its value doubled · `B` Its index/position in the traversal · `C` Its `next` pointer's address twice · `D` Nothing — just the node
→ **B.**

**Q2.** When a node is found already in the map, how is cycle length computed?
`A` `currentIndex + storedIndex` · `B` `currentIndex − storedIndex` · `C` `storedIndex − currentIndex` · `D` `storedIndex ÷ currentIndex`
→ **B.**

**Q3.** What's the time complexity of that brute-force approach, and why is it different from Session 15's cycle-*detection* brute force?
`A` O(N), same as before · `B` O(N log N), because it uses an ordered `map` instead of a hash-based `set` · `C` O(log N) · `D` O(1)
→ **B.**

**Q4.** In the optimal (Floyd's) approach for cycle length, what happens immediately after slow and fast first meet?
`A` Return 0 immediately · `B` Move slow one more step and start counting from 1 · `C` Reset both pointers to head · `D` Swap slow and fast
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about the optimal cycle-length approach?
`A` O(1) space · `B` Uses only a few pointers, no map · `C` Time is O(N + cycle length) · `D` Returns `-1` if no cycle exists
→ **A, B, C.** *(D is false — it returns `0` if no cycle exists, worth a mental note since today's problem also has a "what if nothing's there" edge case.)*

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Say: *"Last two sessions were entirely about loops in linked lists — does one exist, how long is it. Today, forget cycles completely. New skill: doing arithmetic ON a linked list."*

Put this on the board:

```
List a:  0 → 2 → 4 → NULL
List b:  1 → 3 → 5 → NULL
```

Ask: *"If I told you each of these lists is a number written backwards, what two numbers am I holding, and what's their sum?"* Let the room work it out: `420 + 531 = 951`. Then reveal the actual output list: `1 → 5 → 9 → NULL` — also backwards, also `951`.

> *"You just did the algorithm in your head. Today we make a computer do it one digit at a time, without ever assembling the whole number."*

---

## Slide Block A (10–19 min) — DELIVER SLIDES AS-IS

Covers: Problem Statement → Example 1 (no carry) → Example 2 (with carry) → Approach.

**Beats to emphasise**

- **Reverse order is a feature, not an inconvenience.** Addition works right-to-left in real life (ones, then tens, then hundreds). Storing the least-significant digit first means the algorithm can add head-to-head, in order, without ever needing to know how long either number is in advance.
- **The dummy head removes a special case.** `ans` starts as a throwaway node valued `-1`; `cur` points to it. Every real digit gets appended after `cur`, and at the very end the function returns `ans->next`, silently dropping the dummy.
- **Example 2 is why carry matters.** List `a = 6,8,9` (reverse order) is the number `986`; list `b = 8,3` is `38`; `986 + 38 = 1024`, and the output list `4,2,0,1` (reverse order) reads as `1024`. The output has **one more digit** than either input — that extra digit only exists because of a leftover carry.

**Checkpoint (at 19 min)** — cold-call one student:
> *"In Example 2, the result has 4 digits even though both inputs have at most 3. Where does that extra digit come from?"*
> **Answer:** After both input lists are fully consumed, there's still a carry left over. That leftover carry becomes one more node, appended at the very end of the result.

---

## ⚡ ALS Activity 1 — Live Coding / Dry-Run Relay: Carry the Digit (19–26 min)

**ALS format:** Live Coding / Dry-Run Relay — exposes conflating *when* carry is computed with *when* it's used, and the instinct to "reset" carry to 0 each round instead of overwriting it. Chosen right after Slide Block A because carry only becomes intuitive once students have narrated computing it themselves, iteration by iteration.

**Setup line:**
> *"Four roles, four volunteers: temp1, temp2, carry-keeper, and cur. I'll call out each iteration of Example 1 — 0,2,4 plus 1,3,5 — and each of you announces your role's new value, in order: sum, then new node, then carry, then move pointers."*

Walk iteration 1 live: `temp1 = 0`, `temp2 = 1`, `carry = 0` → sum = `0 + 1 + 0 = 1` → new node value = `1` (`sum % 10`) → carry-keeper announces `carry = 0` (`sum / 10`) → temp1/temp2 move to `2` and `3`. Repeat for iteration 2 (`2 + 3 = 5`, carry stays `0`) and iteration 3 (`4 + 5 = 9`, carry stays `0`). End: both temps are null, carry is `0`, so nothing extra is appended; result reads `1 → 5 → 9`.

**How it surfaces:** Two common slips — (1) the carry-keeper says "reset carry to 0" at the start of each round, as if it needs manual resetting; correct them: it isn't reset, it's *recomputed fresh* from `sum / 10` every iteration, and this example just happens to keep landing on 0. (2) Students compute the new node's value using the *carry* instead of `sum % 10` — make them say the formula out loud each time.

**Debrief line:**
> *"Carry is never 'reset.' It's overwritten every single iteration by `sum / 10`, whatever that turns out to be. If you find yourself writing `carry = 0` inside the loop, you've broken the algorithm."*

**Cut rule:** Run only iterations 1 and 3 live, and narrate iteration 2 verbally without the relay.

---

## Slide Block B (26–35 min) — DELIVER SLIDES AS-IS

Covers: Pseudocode (including the final `if (carry == 1)` step) → Complexity Analysis → C++ Code → Key Takeaways.

**Beats to emphasise**

- **The loop condition is `temp1 != null || temp2 != null`** — OR, not AND. As long as *either* list still has digits, the loop keeps going; the exhausted side simply contributes nothing (`if (temp1 != null) sum += temp1->data`, guarded individually for each side).
- **The final `if (carry == 1) { cur->next = new Node(1) }` line is the "carry the 1" from long addition**, applied exactly once, after both lists are done. It's a one-line edge case, not a separate algorithm.
- Complexity is **O(max(M, N))**, not O(M + N) — the loop runs once per *position*, up to the length of the longer list, because the shorter list just stops contributing after it ends.

**Quick predict beat (~1 min):** *"List a is just the digit 5. List b is also just the digit 5. Predict the full output list before I show you."* Reveal: `5+5=10` → node value `0`, carry `1`. Both lists exhausted, but carry is `1`, not `0` → append one more node. **Output: `0 → 1 → NULL`** (representing `10`). *"Carry doesn't get flushed away just because the loop ended — check it one more time, after the loop, or you'll silently drop the most significant digit of your answer."*

**Checkpoint (at 35 min)** — show hands:
> *"Why is the time complexity O(max(M, N)), and not O(M + N)?"*
> **Answer:** The loop advances one position at a time, and it keeps running as long as *either* list has a node left — so the number of iterations equals the length of the longer list, not the combined length of both.

---

## ⚡ ALS Activity 2 — Spot the Bug: The Wrong Loop Condition (35–41 min)

**ALS format:** Spot the Bug — exposes the assumption that `&&` and `||` are interchangeable in a "keep going while there's more to do" loop. Chosen as the closing activity because it's the single most dangerous silent bug in this algorithm — no crash, no error, just a truncated answer.

**Setup line:**
> *"Real code on the left, my version on the right. I changed exactly one character. Tell me what breaks, and use Example 1 to prove it — list a has 3 digits, list b has 3 digits, so first try it there, then tell me what happens if list b only had 2."*

```
// Correct (from the deck)
while (temp1 != null || temp2 != null) { ... }
```

```
// Buggy version
while (temp1 != null && temp2 != null) { ... }
```

45 seconds to test it mentally against Example 1 (same length — bug doesn't show), then against a shortened list `b` of only 2 digits. Someone identifies that the buggy `&&` version stops the instant *either* list runs out — even if the other list still has digits left.

**How it surfaces:** Students often say "no difference" because they only test the equal-length example, where both conditions behave identically. Push them: *"Now make list b one digit shorter. Does anything change?"* — that's when the AND-version silently drops the remaining digits and any leftover carry.

**Debrief line:**
> *"`&&` means both must still have something. `||` means either is enough. Any 'process until everything's done' loop over two things of possibly different lengths needs `||` — get this backwards and you silently truncate your answer with no error message at all."*

**Cut rule:** Skip the mental test and just state the two scenarios (equal-length vs. unequal-length) directly.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering the carry mechanics, the OR loop condition, and the complexity justification. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> Two linked lists, `a = 9 → NULL` and `b = 9 → NULL` (representing the single digits 9 and 9). Write out the resulting linked list, digit by digit, and say in one sentence why it has two nodes instead of one.
> **Answer:** `9 + 9 = 18` → new node value `8` (`sum % 10`), carry `1` (`sum / 10`). Loop ends (both lists exhausted), but carry is `1`, so one more node is appended with value `1`. Result: `8 → 1 → NULL` (representing `18`). It has two nodes because the leftover carry after the loop becomes its own node.

**Homework:** Re-attempt the dry run of Example 2 (the one with the carry) from memory.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Carry needs to be manually reset to `0` each iteration | It "feels like" a running total that should clear | ALS Activity 1's relay — carry-keeper states it's overwritten by `sum / 10`, never reset |
| `&&` and `||` are interchangeable in a "keep going" loop over two lists | Both "look like" the natural way to say "while there's more" | ALS Activity 2's Spot the Bug — showing the AND-version silently drops digits from the longer list |
| Carry left over after the loop ends can be safely ignored | Attention naturally drops once the main loop is "done" | Slide Block B's quick predict beat — walking `5 + 5` to its two-node result |
| Time complexity is O(M + N) because "both lists get processed" | Sounds intuitive if you're thinking about total nodes touched, not loop iterations | Slide Block B's checkpoint — reasoning from iteration count, not node count |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Converted from the original 45-min/3-activity version — see below for what changed.
- **Two ALS activities this session:** Activity 1 is the Live Coding / Dry-Run Relay (Carry the Digit), Activity 2 is Spot the Bug (the `&&`/`||` loop-condition trap). The original third activity (Predict the Output: The Leftover Carry) is folded into a 1-minute quick beat inside Slide Block B instead of running as its own block.
- **The Classroom Quiz now runs last, right before the Exit Ticket** — moved from its original mid-session position (after Activity 1) to match the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank.
- **Have Example 1's dry run pre-drawn** (four roles: `temp1`, `temp2`, `carry`, `cur`/`ans`) before class — ALS Activity 1 depends on it and setting it up live costs minutes you don't have.
- **This is session 17 of the Sem-3 sequence** (see `sem-3-sequence.md`) — the last of the "cycles and arithmetic" trio (Sessions 15-17) before the block moves to Stack.
- **The deck repeats its own Key Takeaways and pseudocode slides several times** in the source — this is a source artefact, not intentional pacing. Deliver each concept once at the pace of Slide Block B above; don't re-teach every repeated slide.
- **ALS Activity 2 only "clicks" once students test it against an *unequal-length* pair** — if the room jumps straight to "no difference," don't move on until someone tries the shortened list b.
