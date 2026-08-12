# Session 35b — Single Element 1 (Part 2 of 2)

**Duration** 25 min · **Topic** Bit Manipulation — Single Element: Hands-On Practice · **Prerequisite** Session 35a — Single Element 1, Part 1 (three approaches, full dry runs) · **Session type** Concept lecture

<!-- Split note: continues session-35 (original 50 min) right after the Classroom Quiz. This part is entirely hands-on — a live trace on fresh numbers, then the precondition-breaking "what if two elements are unique" check, then the exit ticket. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Single Element 1 | https://docs.google.com/presentation/d/1ClShR7M2swFtCqCOCAR8gAMrJ-Nxs1Up6CMblULaRwo/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Independently execute the running-XOR accumulation on a fresh array, without instructor narration. *(APPLYING)*
2. State the XOR trick's precondition (exactly one unpaired element) and explain what happens when it's violated. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 35a (0–4 min)

Say: *"Three quick ones on the XOR trick before you run it yourself."*

**Q1.** The optimal approach's complexity is:
`A` O(n) time, O(n) space · `B` O(n) time, O(1) space · `C` O(n²) time, O(1) space · `D` O(log n) time, O(1) space
→ *Read:* B.

**Q2.** Why does XOR-ing the whole array work regardless of order?
`A` It doesn't — order matters · `B` XOR is commutative and associative, so pairs cancel no matter how they're grouped · `C` The array gets sorted first · `D` Only the first and last elements matter
→ *Read:* B.

**Q3.** What does `a ^ 0` equal, for any `a`?
`A` 0 · `B` `a` · `C` `-a` · `D` Undefined
→ *Read:* B — this is why the leftover, unpaired element survives the running XOR untouched.

**Running it** — poll tool, ~30 s/question. Total 4 min including reads.

---

## Bridge (4–5 min)

Say: *"You've watched three approaches. Now you run the winner yourself — and then we break its one assumption on purpose."*

---

## ⚡ Activity 1 — Live Trace: "XOR Them All" (5–11 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can execute the running-XOR accumulation themselves on a fresh array, rather than having only watched the deck's regrouped example.

**Setup line (say this):**
> *"Fresh array: `[12, 5, 12, 9, 5]`. Running XOR, left to right — after each element, tell me the accumulator's value before I confirm."*

Run **one element at a time**:

```
result = 0
result = 0 ^ 12  = 12
result = 12 ^ 5  = 9
result = 9 ^ 12  = 5
result = 5 ^ 9   = 12
result = 12 ^ 5  = 9
```

**How it surfaces:** After the final step, ask before revealing: *"Is `9` the unique element, or did something go wrong?"* Confirm `9` is correct — `12` appears at positions 0 and 2, `5` appears at positions 1 and 4, both cancel, leaving `9` (position 3) as the answer.

**Debrief line:**
> *"Notice the running total doesn't 'know' which numbers are paired as it goes — it doesn't need to. Every pair cancels itself out eventually, purely from XOR's own algebra, with zero bookkeeping required."*

**Cut rule:** If running short, do the array in one silent pass and reveal only the final answer — the mechanism is confirmed either way; the step-by-step reveal is for reinforcement, not new information.

---

## ⚡ Activity 2 — Spot the Bug: "What If Two Elements Are Unique?" (11–17 min)

**Format:** Spot the Bug / Predict-the-Output · **Exposes:** whether students understand the XOR trick's precondition — exactly one unpaired element — rather than assuming it works for any array shape.

**Setup line (say this):**
> *"A classmate says: 'XOR-ing the whole array always finds the elements that don't have a pair, no matter how many there are.' Test it: `arr = [3, 3, 5, 7]` — both `5` and `7` appear only once. XOR the whole array and tell me what you get."*

**What students do:** Compute `3^3^5^7 = 0^5^7 = 5^7 = 2`. Note that `2` is not `5`, not `7`, and not any element in the array at all — it's a meaningless leftover value.

**How it surfaces:** Ask: *"So does the trick still work here?"* Push toward: no — the XOR trick's entire correctness depends on there being *exactly one* unpaired element; with two unpaired elements, their XOR partially cancels into a value that isn't either original number, and the technique produces garbage.

**Debrief line:**
> *"Every clever trick has a precondition it depends on — here, it's 'exactly one element without a partner.' Always ask what a technique assumes before applying it to a differently-shaped problem; two unique elements is a genuinely different problem requiring a different technique."*

**Cut rule:** If running short, state the two-unique-elements failure case directly rather than having students compute it live.

---

## Exit Ticket (17–20 min)

> `arr = [15, 20, 15, 33, 20]`. Using the XOR approach, what's the running total after each element, and what's the final answer?
> **Answer:** `0^15=15` → `15^20=27` → `27^15=20` → `20^33=53` → `53^20=33`. Final answer: `33` (the unpaired element; `15` and `20` each appeared twice and canceled). <!-- placement: inferred exit-ticket array, built to exercise the full cancel-and-survive pattern with pairs spaced apart -->

**Homework:** trace the XOR approach on `arr = [42, 17, 42, 8, 17]` by hand, showing the running total after each element. <!-- placement: inferred — no homework/practice units exist for this course per deviation #2 -->

**Bridge to Session 36 at the close:** "Today, XOR found the one element with no partner. Next session, a different bit-manipulation puzzle — minimum flips to satisfy an OR equation, not an equality — so don't expect the exact same trick to reappear."

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The XOR trick works no matter how many elements are unpaired | The trick "feels general" once it's seen working on one example | Activity 2 — showing `[3,3,5,7]` XORs to a meaningless value, since the precondition is exactly one unpaired element |
| XOR-ing the array requires processing elements in a specific order | Nested-loop and hashmap approaches both iterate in a fixed, meaningful order | Activity 1 — deliberately using an array where paired elements are far apart, showing the running XOR still lands correctly regardless of position |
| `a ^ 0 = a` only applies at the very start of the accumulation | The identity is usually introduced as an initialization rule | Point out it applies identically any time a running total happens to hit zero mid-array, not just at initialization |

---

## Instructor Notes

- **This is Part 2 of a 50-minute original session, split right after the Classroom Quiz. Entirely hands-on** — no new slide content.
- **The two-unique-elements failure case in Activity 2 is the single most valuable moment in this session** — it's the natural follow-up question ("what if there were two?") that students will ask anyway, and better to surface it deliberately than have it undermine confidence in the trick later.
