# Session 29a — Binary Operations (Part 1 of 2)

**Duration** 38 min · **Topic** Bit Manipulation — Number Conversion · **Prerequisite** Session 28 (Top K Frequent Elements — Heaps) · **Session type** Concept lecture

<!-- Split note: original session-29 ran 75 min across three slide blocks. Split right after the Classroom Quiz. Part 1 covers bit fundamentals and both conversion directions (decimal↔binary). Part 2 (session-29b) covers binary arithmetic (addition, both subtraction methods) and complements/2's-complement subtraction — the densest material in the topic. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Binary Operations | https://docs.google.com/presentation/d/153LZGni1xef_OfEY2p7qdybI5EgPvjxf5IPRvr8konE/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define bit, LSB, and MSB, and state the place values they represent. *(REMEMBERING)*
2. Convert a decimal number to binary using the division-by-2 method, and a binary string back to decimal using positional (place) values. *(APPLYING)*

*(Binary arithmetic and complements are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 28 (0–7 min)

> Retrieval practice on **Top K Frequent Elements** (the last Heaps session). No new content — this is recall.

Say: *"Eight quick ones on last session's heap problem. Answer solo, no discussion yet."*

**Q1.** In the brute-force approach for Top K Frequent Elements, what do you build first?
`A` A min-heap of size k · `B` A frequency map (dictionary) of element→count · `C` A sorted array of the input · `D` A max-heap of all elements
→ *Read:* Answer B. If many pick A, they've mentally skipped straight to the optimal approach — fine instinct, but they need to be able to describe brute force too.

**Q2.** After building the frequency map in the brute-force approach, what's the very next step?
`A` Return the top k keys in insertion order · `B` Convert to (frequency, element) pairs and sort descending · `C` Push all pairs into a min-heap · `D` Binary search for k
→ *Read:* Answer B.

**Q3.** Worst-case time complexity of the brute-force approach (u = n unique elements)?
`A` O(n) · `B` O(n log k) · `C` O(n log n) · `D` O(n²)
→ *Read:* Answer C — sorting the frequency list dominates.

**Q4.** In the optimal approach, what data structure holds the "top k so far" while scanning the frequency map?
`A` A max-heap of size n · `B` A min-heap of size k · `C` A stack · `D` A sorted list rebuilt every step
→ *Read:* Answer B. If this doesn't stick, restate the one-liner live: min-heap because you want to evict the *smallest* to protect the largest.

**Q5.** When does an element get popped from the heap in the optimal approach?
`A` Every time a new element is pushed, regardless of size · `B` Only when the heap size exceeds k · `C` Only when the new element is larger than everything already in the heap · `D` Never — the heap only grows
→ *Read:* Answer B.

**Q6.** *(MSQ — pick 2)* Which are true about the optimal approach's complexity?
`A` Time is O(n log k) · `B` Time is O(n log n) always · `C` Space is O(n + k) · `D` Space is O(1)
→ *Read:* A and C.

**Q7.** Why is O(n log k) better than O(n log n) when k is much smaller than the number of unique elements?
`A` They're the same thing written differently · `B` log k grows far slower than log n when k << n, so each heap operation does less work · `C` Heaps are always faster than sorting, period · `D` It isn't actually better — common misconception
→ *Read:* Answer B. If C gets picked, correct it now — heaps aren't unconditionally faster, the *k* is doing the work here.

**Q8.** In the dry run, after processing element 3 (frequency 1) with k=2, why did the heap immediately pop (1,3)?
`A` 3 is a prime number · `B` The heap size (3) exceeded k (2), so the smallest pair was evicted · `C` 3 was already in the heap · `D` The algorithm made an error
→ *Read:* Answer B.

**Running it** — poll tool, ~40 s per question. Total 7 min.

---

## Hook (7–11 min)

Write **25** on the board. Ask: *"That's how you and I see this number. A computer has never seen a '2' or a '5' — it only has switches that are on or off. How does it actually store 25?"*

Take two or three guesses out loud, then reveal the deck's own framing: everything a computer stores — this number, an image, this sentence — is ultimately a sequence of two symbols, 0 and 1. Say: *"By the end of Part 2 you'll convert between what you see and what the machine sees, in both directions, and you'll know how it stores negative numbers too — which is the part that surprises everyone."*

---

## Slide Block A (11–24 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — grouped as "bit fundamentals + both conversion directions", slides 4–23 -->
Covers: What is a bit / LSB / MSB → Decimal-to-Binary conversion (division-by-2 method, pseudocode, code) → Binary-to-Decimal conversion (positional-value method, pseudocode, code).

**Beats to emphasise**

- **LSB is rightmost, MSB is leftmost** — say it out loud with the word "significant" attached each time; this pairing is the single most reversed fact in this topic.
- On decimal→binary: the algorithm collects remainders **from LSB to MSB**, so the string must be **reversed** at the end. This is the exact bug source for Activity 1 — flag it now, don't wait.
- On binary→decimal: walk the deck's own example (`11001` → 25) bit by bit, reading right to left, and say the power of 2 out loud each time (2⁰, 2¹, 2², …).

**Checkpoint (at 24 min)** — cold-call two students:
> *"One sentence each: how do you go from decimal to binary, and how do you go back?"*
> **Answer:** Decimal→binary: repeatedly divide by 2, record remainders, reverse them. Binary→decimal: multiply each bit by 2 raised to its position (from the right, starting at 0), and sum.

---

## ⚡ Activity 1 — Live Coding / Dry-Run Relay: Convert 37 Both Ways (24–30 min)

**Format:** Dry-Run Relay · **Exposes:** the reverse-the-remainders step being skipped, and position-index errors (starting at 1 instead of 0) in the binary-to-decimal direction.

**Setup line (say this):**
> *"New number, not from the slides — 37. Row by row, out loud, you tell me what to write. I only write what you say."*

**What students do:** One student at a time calls out the next division step (`37 / 2 = 18 remainder 1`, `18 / 2 = 9 remainder 0`, …) until the quotient hits 0. Once the remainder column is done, ask the class: *"Read it off top to bottom — is that the answer?"* Let someone catch that it must be reversed. Then flip to binary→decimal: put `100101` on the board and relay the positional-value sum back to 37.

**How to handle wrong answers:** If a student reads the remainders top-to-bottom as the final answer (skipping the reverse), don't correct immediately — write it exactly as they say, then ask the class to verify by converting it back. The mismatch is the correction.

**Debrief line:**
> *"Two mirror-image algorithms. One walks right-to-left collecting remainders and has to flip the string at the end. The other walks right-to-left multiplying by powers of 2 and never needs to flip anything. If you mix up which one needs the reverse, you'll get a backwards number that looks plausible — always sanity-check by converting back."*

**Cut rule:** If running short, do only the decimal→binary direction (37) and skip the binary→decimal relay — the reverse-step bug is the higher-value catch of the two.

---

## Classroom Quiz (30–35 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Call-and-Response Chant Drill (35–38 min)

**Why this strategy here:** Part 2 introduces its own chant ("flip every bit, add one") for complements — a technique that works because it's short and rehearsed aloud. Part 1's own rule ("collect LSB-first, then reverse") deserves the same treatment before it competes for memory space with Part 2's chant.

**Run it (3 minutes):**
> *"Call and response. I say 'decimal to binary' — you say 'divide by two, collect remainders, reverse.' I say 'binary to decimal' — you say 'multiply by powers of two, starting at zero, sum.' Loud enough that the back row hears it."*

Run each direction twice. Then cold-call one student to say both chants back to back, unprompted.

> *"Lock those two chants in — Part 2 hands you a third one, and having two already automatic makes room for it."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The remainder string from decimal→binary conversion doesn't need reversing | The division steps run top-to-bottom, and reading top-to-bottom "feels" like the natural order | Activity 1 — have them verify by converting their un-reversed answer back to decimal and watching it fail |

---

## Instructor Notes

- **This is Part 1 of a 75-minute original session, split right after the Classroom Quiz.**
- **This is the first Bit Manipulation session** after a full Heaps unit — the warm-up poll is intentionally the only backward-looking content; everything after the Hook is new. Don't assume familiarity with binary beyond what Slide Block A itself delivers.
- **Reuse fresh numbers, not the deck's own.** The deck reuses 5, 3, 6, 9, 10 across almost every sub-topic. Students can pattern-match the *answer* without doing the *method*. This part's activity deliberately uses a number the deck never shows (37) — keep doing this if you improvise more examples in Part 2.
