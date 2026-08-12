# Session 31a — Bitwise Operators (Part 1 of 2)

**Duration** 33 min · **Topic** Bit Manipulation — AND & OR · **Prerequisite** Session 30 (Code for Binary Conversion) · **Session type** Concept lecture

<!-- Split note: original session-31 ran 55 min. Split right after the Classroom Quiz. Part 1 covers why bit manipulation matters, real-life use cases, and the AND/OR operators. Part 2 (session-31b) covers XOR, NOT, shifts, applications, and INT_MAX/INT_MIN — including the session's hardest idea, why `~5` prints `-6`. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Bitwise Operators | https://docs.google.com/presentation/d/1r3lgW5W1n5JPdDWsRypWIFRPhCqCphmAq205XQhIeVU/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State what AND and OR each do to a pair of bits, using their truth tables. *(REMEMBERING)*
2. Compute the result of AND and OR on two given binary numbers by hand. *(APPLYING)*
3. Identify at least two real-world uses of bitwise operations and state why bitwise operations are faster than arithmetic ones. *(UNDERSTANDING)*

*(XOR, NOT, shifts, and the `~5 = -6` puzzle are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 30 (0–6 min)

> Retrieval practice on **Code for Binary Conversion**. Solo answers, no discussion yet.

**Q1.** Time complexity of `decimal_to_binary`?
`A` O(1) · `B` O(n) · `C` O(log₂ n) · `D` O(n log n)
→ *Read:* Answer C.

**Q2.** Time complexity of `binary_to_decimal`, where n is the length of the input string?
`A` O(1) · `B` O(n) · `C` O(log₂ n) · `D` O(n²)
→ *Read:* Answer B.

**Q3.** Space complexity of `binary_to_decimal`?
`A` O(n) · `B` O(log₂ n) · `C` O(1) · `D` O(n²)
→ *Read:* Answer C — only fixed variables, regardless of string length.

**Q4.** According to the deck's own pseudocode (no zero-guard), what does `decimal_to_binary(0)` actually return?
`A` `"0"` · `B` `""` (empty string) · `C` An error · `D` `"00"`
→ *Read:* Answer B. If this trips people up, that's expected — it's the whole point of yesterday's Spot-the-Bug activity, revisit it in 30 seconds if the miss rate is high.

**Q5.** Why does `decimal_to_binary`'s output string need to be reversed at the end, but `binary_to_decimal`'s loop doesn't need any reversing?
`A` Pure convention, no real reason · `B` Decimal-to-binary collects digits LSB-first; binary-to-decimal reads the string directly from its last character (already LSB) toward the first · `C` Because Python strings are backwards · `D` They both actually need reversing
→ *Read:* Answer B.

**Q6.** *(MSQ — pick 2)* For `n = 100`, which loop counts are correct?
`A` `decimal_to_binary`'s while-loop runs about 7 times · `B` `decimal_to_binary`'s while-loop runs 100 times · `C` `binary_to_decimal`'s for-loop on `"1100100"` runs 7 times · `D` `binary_to_decimal`'s for-loop runs once
→ *Read:* A and C.

**Running it** — poll tool, ~40 s per question. Total 6 min.

---

## Hook (6–9 min)

Write on the board: `n * 2` and `n << 1`. Ask: *"Same result, for any positive integer n. So why would anyone write the second one instead of the first?"*

Let a few guesses land, then say: *"Bitwise operations run directly on the CPU's circuitry — no multiplication logic involved, just a wire shift. They're the fastest operations a processor has. That speed is why they show up everywhere from image compression to encryption to how your phone stores a Boolean flag in a single bit instead of a whole byte. Today and next part you learn the six operators that make all of that possible."*

---

## Slide Block A (9–20 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred — slides 4-23: intro, why bit manipulation, real-life use cases, bit & byte, AND, OR -->
Covers: Introduction to bit manipulation → Why Bit Manipulation (efficiency, memory optimization, fine-grained control) → Real Life Use Cases (image compression, cryptography) → Bit & Byte → Bitwise AND (`&`) with truth table and worked example (`0101 & 0011 = 0001`) → Bitwise OR (`|`) with truth table and worked example (`0101 | 0011 = 0111`).

**Beats to emphasise**

- Land the three reasons for bit manipulation as a memorable trio: **efficiency, memory, control.** These come back verbatim in Part 2's Key Takeaways slide.
- On the truth tables: read AND as "both must be 1" and OR as "at least one must be 1" — say those two phrases explicitly, they're the cleanest possible distinction and it's the one students blur most.
- Walk the deck's own worked examples (`0101 & 0011`, `0101 | 0011`) bit by bit, column by column, exactly as the slides animate them.

**Checkpoint (at 20 min)** — show of hands:
> *"`1010 & 0110` — what's bit position 1 (second from the right) in the result?"*
> **Answer:** Both operands have `1` there, so AND gives `1`. (Full result: `0010`.)

---

## ⚡ Activity 1 — Real-World Callout: Where Have You Already Seen This? (20–25 min)

**Format:** Real-World Callout · **Exposes:** the belief that bitwise operators are an abstract classroom-only tool with no connection to software students actually use.

**Setup line (say this):**
> *"Thirty seconds. Anywhere you've seen a system store several yes/no flags packed into one number, or combine settings, or mask something out — shout it out. I'll write down what you say."*

**What students do:** Call out examples. Push toward concrete ones if the room stalls: file permissions (`rwx` in Unix, e.g. `chmod 755`), RGB color values packed into a single 24/32-bit integer, checkbox settings stored as a bitmask, network subnet masks. Write up to 6 on the board.

**How it surfaces:** For 2 of the examples, push once: *"Which operator would you use — AND, OR, or XOR — and why?"* e.g., checking if a permission bit is set → AND; combining two sets of flags → OR.

**Debrief line:**
> *"Every one of those systems is doing exactly what you just learned — packing multiple true/false answers into the bits of a single number, and using AND/OR to read or combine them. This isn't a toy topic, it's how real systems save memory and stay fast."*

**Cut rule:** If running late, take 3 callouts instead of 6 and skip the "which operator" push — keep the debrief line, it's the payoff.

---

## Classroom Quiz (25–30 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Human Truth Table (30–33 min)

**Why this strategy here:** AND and OR are easy to state but easy to blur under time pressure. Acting out a truth table with bodies — standing for 1, sitting for 0 — gives a physical anchor for "both" (AND) versus "at least one" (OR) that a verbal recap doesn't, and sets up Part 2's XOR ("exactly one") as a clean third contrast.

**Run it (3 minutes):**
> *"Two volunteers, each is one bit — standing is 1, sitting is 0. Rest of the class calls out a combination (stand-stand, stand-sit, sit-stand, sit-sit) and asks 'AND says?' then 'OR says?' Volunteers don't answer — the class does, based on what they see."*

Run all four combinations for both AND and OR. Keep it fast — this is a physical mnemonic, not a new lesson.

> *"Hold that image — two people standing means both AND and OR say yes. Part 2 adds a third operator that disagrees with both of them in exactly that one situation."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Bitwise operators are just an alternate syntax for the equivalent arithmetic (`<<` is "the same as" `*`) | The results often match for small, positive numbers, so the two seem interchangeable | Session's own framing: bitwise ops work per-bit on the CPU directly, which is *why* they're fast — Part 2 shows a case (NOT) where the "similar" arithmetic intuition actively misleads |

---

## Instructor Notes

- **This is Part 1 of a 55-minute original session, split right after the Classroom Quiz.**
- **This session is a hard prerequisite for everything from Session 32 onward** — every Bit Manipulation Technique (check/set/clear/toggle a bit) is built directly out of AND, OR, XOR, and shifts. If the class is shaky on AND/OR here, flag it before Part 2 introduces XOR and NOT on top.
- **Keep the "efficiency, memory, control" trio and the "AND=both, OR=at least one" phrasing on the board** for the whole session — both get reused as checkpoints in Part 2 and in its exit ticket.
