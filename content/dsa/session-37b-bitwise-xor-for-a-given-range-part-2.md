# Session 37b — Bitwise XOR For a Given Range (Part 2 of 2)

**Duration** 22 min · **Topic** Bit Manipulation — Applying the n%4 Pattern & Why It Works · **Prerequisite** Session 37a — Bitwise XOR For a Given Range, Part 1 (brute force, the n%4 identity) · **Session type** Concept lecture

<!-- Split note: continues session-37 (original 50 min) right after the Classroom Quiz. This part is hands-on: applying the pattern to fresh numbers, then a structural discussion of why the pattern repeats every 4. This closes the entire Bit Manipulation block (Sessions 29–37). -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Bitwise XOR For a Given Range | https://docs.google.com/presentation/d/17bNkI-vHKfJlll-Rasw2uhWcPEQNGHYyrQH3tM889gI/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Trace the optimal approach end-to-end on a given `left, right` pair, unaided. *(APPLYING)*
2. Explain, structurally, why `XOR(1…n)` cycles with period 4 — as a consequence of binary counting, not an arbitrary rule. *(ANALYZING)*
3. State the optimal approach's complexity: `O(1)` time, `O(1)` space, versus the brute force's `O(right - left)`. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 37a (0–4 min)

Say: *"Three quick ones on the n%4 table before you apply it yourself."*

**Q1.** If `n % 4 == 0`, `xorOnetoN(n)` returns:
`A` `0` · `B` `1` · `C` `n` · `D` `n+1`
→ *Read:* C.

**Q2.** If `n % 4 == 3`, `xorOnetoN(n)` returns:
`A` `0` · `B` `1` · `C` `n` · `D` `n+1`
→ *Read:* A.

**Q3.** `XOR(left…right)` equals:
`A` `xorOnetoN(right) - xorOnetoN(left-1)` · `B` `xorOnetoN(right) ^ xorOnetoN(left-1)` · `C` `xorOnetoN(right) + xorOnetoN(left-1)` · `D` `xorOnetoN(right - left)`
→ *Read:* B — XOR, not subtraction.

**Running it** — poll tool, ~30 s/question. Total 4 min including reads.

---

## Bridge (4–5 min)

Say: *"You know the table. Now apply it cold — and then we'll find out why the number 4 shows up at all."*

---

## ⚡ Activity 1 — Live Trace: "Two Lookups, One XOR" (5–11 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can apply the `n%4` pattern correctly on fresh numbers, rather than only having watched the deck's `n=10` and `n=4` examples.

**Setup line (say this):**
> *"`left = 8, right = 15`. First, compute `xorOnetoN(15)` and `xorOnetoN(7)` using the `n%4` pattern — tell me the remainder and the result for each, before I confirm. Then combine them."*

Run **step by step**:

```
xorOnetoN(15): 15 % 4 = 3  → pattern says remainder 3 → return 0
xorOnetoN(7):   7 % 4 = 3  → pattern says remainder 3 → return 0
XOR(8...15) = xorOnetoN(15) ^ xorOnetoN(7) = 0 ^ 0 = 0
```

**How it surfaces:** Before revealing the combination, ask: *"Both helper calls returned 0 — does that mean something went wrong, or is a zero answer possible here?"* Correct: a zero answer is entirely possible and not a sign of error — it simply means the range `8` through `15` (8 consecutive integers) happens to XOR to zero.

**Debrief line:**
> *"Two constant-time lookups, one XOR — done, regardless of whether the range was 8 numbers wide or 8 million. That's the entire point of moving from brute force to this identity."*

**Cut rule:** If running short, do only `xorOnetoN(15)` live and state `xorOnetoN(7)` and the final combination directly — one correctly-applied remainder case is enough to confirm the pattern.

---

## ⚡ Activity 2 — Predict & Discuss: "Why Does the Pattern Repeat Every 4?" (11–17 min)

**Format:** Predict-the-Output / Discussion · **Exposes:** whether students have genuine intuition for *why* the `n%4` cycle exists, rather than just memorizing the four-case table.

**Setup line (say this):**
> *"Look at the last two bits of any four consecutive integers — say, 4, 5, 6, 7 in binary: `100, 101, 110, 111`. What happens if you XOR all four together, and why might that explain why the pattern resets every 4 numbers?"*

**What students do:** Discuss for a minute, then share out — computing `4^5^6^7` in binary and noticing the lowest two bits cycle through all four combinations (`00, 01, 10, 11`) exactly once every four consecutive integers, while higher bits stay constant across the group of four.

**Answer:** Every group of 4 consecutive integers has lowest two bits that are a permutation of `00, 01, 10, 11` — XOR-ing all four combinations of two bits together always cancels to `00` for those two bits, while the higher, unchanging bits combine predictably. This is *why* `f(n)` cycles with period 4 — it's a direct consequence of how binary counting rolls over every 4 values, not an arbitrary rule to memorize.

**How it surfaces:** Ask a follow-up: *"So is `n%4` special because of anything about XOR specifically, or because of how binary counting works in general?"* Push toward: it's about binary counting — the lowest 2 bits of any 4 consecutive integers always cycle through all 4 possible 2-bit combinations, and that's a property of counting in binary, independent of XOR itself.

**Debrief line:**
> *"A pattern that looks like 'a rule to memorize' usually has a structural reason underneath it. Here, it's just binary counting's own rollover behavior — XOR is just the operation that happens to expose it cleanly."*

**Cut rule:** If running short, state the structural reason directly and skip the open discussion.

---

## Exit Ticket (17–20 min)

> `left = 11, right = 20`. Using the optimal approach, compute `xorOnetoN(20)`, `xorOnetoN(10)`, and the final answer.
> **Answer:** `xorOnetoN(20)`: `20 % 4 = 0` → return `20`. `xorOnetoN(10)`: `10 % 4 = 2` → return `11`. `XOR(11…20) = 20 ^ 11 = 10111 (in binary: 10100 ^ 01011 = 11111 = 31)`. Final answer: `31`. <!-- placement: inferred exit-ticket range, built to exercise both a remainder-0 and a remainder-2 case in the same computation -->

**Homework:** compute `XOR(23, 40)` using the `n%4` pattern, showing both helper-function calls and the final combination. <!-- placement: inferred — no homework/practice units exist for this course per deviation #2 -->

**This closes the Bit Manipulation block (Sessions 29–37).** If time allows, briefly recap the block's throughline: Sessions 29–33 built the core toolkit (binary conversion, bitwise operators, set-bit techniques); Sessions 34–37 applied that toolkit to four distinct problem shapes (bit-flip counting, XOR-cancellation, bit-by-bit rule tables, and prefix-XOR range identities) — the tools stayed the same, only what they were pointed at changed.

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The `n%4` pattern is an arbitrary rule to be memorized | It's introduced as a four-case lookup table without derivation | Activity 2 — deriving the pattern from how the lowest two bits of any four consecutive integers cycle through all combinations |
| A result of `0` from `xorOnetoN` or from the final range XOR indicates an error | Zero often reads as "nothing happened" or "a bug," especially after a multi-step calculation | Activity 1 — showing a genuine, correct zero result and confirming it's a valid answer rather than a sign of failure |
| This problem's optimal solution is unrelated to Session 35's XOR-cancellation trick | Different-sounding problem framing ("range" vs "array") | Explicitly connect: both rely on the identical algebraic fact, `a^a=0` — Session 35 canceled paired array elements; this problem cancels a shared numeric prefix |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split right after the Classroom Quiz, and the last session of the Bit Manipulation block.**
- **Activity 2's structural derivation is this session's highest-value five minutes** — resist the urge to skip it under time pressure. A student who can explain *why* the pattern has period 4 has understood something durable; a student who only memorized the four-case table will forget it by next week.
