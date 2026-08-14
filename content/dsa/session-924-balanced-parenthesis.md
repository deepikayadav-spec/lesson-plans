# Session 24 — Balanced Parenthesis

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Stack — Balanced Parenthesis Validation · **Prerequisite** Session 23 — Implement Min Stack
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Balanced Parenthesis | https://docs.google.com/presentation/d/1NzWVMwN6CqCKR--ORa0Gy6uVLGrY2vXjM304aOBOeDg/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the three conditions for a bracket sequence to be valid: matching type, correct nesting order, and every closing bracket having a corresponding opening one. *(REMEMBERING)*
2. Explain why a stack — not a counter — is the right tool: order and type both matter, not just counts. *(UNDERSTANDING)*
3. Trace the push-on-open, match-and-pop-on-close algorithm on a given string, including both valid and invalid cases. *(APPLYING)*
4. Identify the three distinct failure modes — closing bracket with an empty stack, closing bracket that doesn't match the stack's top, and leftover unclosed brackets at the end — and explain why the string is invalid in each. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 23 (3–7 min) · ALS: Polling

5 questions on **Session 23 (Implement Min Stack)**. ~45 s each, project the distribution, never name individuals.

**Q1.** Min Stack's four required operations, all O(1), are:
`A` push, pop, top, getMin · `B` push, pop, sort, getMin · `C` insert, delete, search, getMin · `D` push, remove, peek, getMax
→ **A.**

**Q2.** In the pair-stack approach, each stack entry stores:
`A` Just the value · `B` The value and the minimum-so-far at that point · `C` The value and its index · `D` The value twice
→ **B.**

**Q3.** In the encoded-value approach, an encoded sentinel is pushed only when:
`A` Every single push · `B` The incoming value is a new minimum · `C` The stack is empty · `D` The incoming value equals the current minimum
→ **B.**

**Q4.** On `pop()`, how do you know the value you just removed was an encoded sentinel, not a real element?
`A` It's negative · `B` It's less than the current `mini` · `C` It's greater than the current `mini` · `D` You can't tell
→ **B.**

**Q5.** *(MSQ — select all that apply)* True of both Min Stack approaches?
`A` `getMin()` is O(1) · `B` `push()` is O(1) · `C` They both use exactly one stack · `D` They both track a running minimum somehow
→ **A, B, D.** *(C is false — Approach 1 stores pairs, which some implementations model as two parallel stacks or one stack of pair objects; the encoded approach is the one that's genuinely a single stack.)*

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Write this on the board: `(){[{}])`

Ask: *"Your code editor underlines a bracket in red the instant you type something like this. How does it know, instantly, without running your program?"*

Let a few guesses land.

> *"Every compiler, every linter, every IDE runs some version of what you're building today. It's one of the oldest problems in computer science, and it's the cleanest possible demonstration of why a stack — specifically, last-in-first-out — is exactly the right shape for 'things that must close in the reverse order they opened.'"*

---

## Slide Block A (10–19 min) — DELIVER SLIDES AS-IS

Covers: Problem Statement (`(`, `)`, `{`, `}`, `[`, `]` — valid if every opening has a matching closing bracket of the same type, closed in the correct order) → Example 1 (`{}()[]` → valid) → Example 2 (`(){[{}])` → invalid, the `{` and `)` don't pair) → Approach: push openings, match closings against the top.

**Beats to emphasise**

- Read Example 2's failure out loud character by character until the mismatch: `(`, `)` — closes fine. `{`, `[`, `{` — all pushed. `}` — matches the most recent `{`, pops fine. `]` — the top is now the *outer* `{`, not `[`. Mismatch.
- **Say explicitly: "count of brackets is not enough."** `(){[{}])` has three of each type — perfectly balanced counts — and is still invalid. Order and type both matter; a stack is what enforces both at once.
- Preview the two ways this can fail mid-scan, without solving them yet: (1) a closing bracket shows up when the stack is empty, (2) a closing bracket's type doesn't match what's on top. Both get built into the dry run next, plus a third failure mode that only shows up *after* the scan ends.

**Checkpoint (at 19 min)** — cold-call:
> *"Why can't I just count opening and closing brackets and compare the totals?"*
> **Answer:** Equal counts don't guarantee correct order or matching types — `(){[{}])` proves it: 3 and 3, still invalid.

---

## Slide Block B (19–26 min) — DELIVER SLIDES AS-IS

Covers: Full dry run of `s = "(){[{}])"` character by character, ending in the mismatch at `]` → pseudocode → complexity (O(N) time, O(N) space) → code.

**Beats to emphasise**

- Narrate every step exactly as the deck does: `(` push. `)` matches top `(`, pop — stack empty. `{` push. `[` push. `{` push (stack: `{`, `[`, `{`). `}` matches top `{`, pop (stack: `{`, `[`). `]` matches top `[`, pop (stack: `{`). `)` — top is `{`, does **not** match `)` — invalid, stop.
- State the three failure modes explicitly: closing bracket arrives and the stack is **empty** → invalid. Closing bracket arrives and it **doesn't match the top** → invalid. After the whole string, the stack is **not empty** (unclosed openings remain) → also invalid.
- Complexity is refreshingly simple: one pass, one stack, O(N) time and O(N) space (worst case: every character is an opening bracket).

**Checkpoint (at 26 min)** — cold-call:
> *"Suppose the string is just `"(("` — two opening brackets, nothing else. Walk me through what happens, and is it valid?"*
> **Answer:** Push `(`, push `(` — stack has two elements, string ends. The stack is *not* empty, so it's invalid — every opening needs a matching close.

---

## ⚡ ALS Activity 1 — Spot the Bug: Valid or Not, and Why (26–34 min)

**ALS format:** Spot the Bug — exposes whether students can identify *which* of the three failure modes applies, not just guess valid/invalid from a glance. Chosen right after Slide Block B because naming the specific failure is the actual transferable skill here, not just voting.

**Setup line:**
> *"Four strings on the board. For each one: valid or invalid? If invalid, tell me exactly which character breaks it and which failure mode it is — empty-stack-on-close, mismatched-type-on-close, or leftover-stack-at-the-end."*

```
1.  "([])"
2.  "([)]"
3.  "((("
4.  ")("
```

45 seconds silent, then hands up. Take one student per string.

**Answers**

| # | Valid? | Reason |
|---|---|---|
| 1 | Valid | Properly nested: `(`, `[`, `]` matches `[`, `)` matches `(` |
| 2 | Invalid | At `)`: stack top is `[`, doesn't match — mismatched-type-on-close |
| 3 | Invalid | End of string, stack still has 3 unmatched `(` — leftover-stack-at-the-end |
| 4 | Invalid | At `)`: stack is empty (nothing pushed yet) — empty-stack-on-close |

**How it surfaces:** For string 2, push students to say specifically what's on top of the stack the instant `)` appears (`[`, not `(`) — this is the mismatched-type failure, distinct from string 4's empty-stack failure. Many students will say "invalid" correctly but conflate the two reasons.

**Debrief line:**
> *"Three ways this breaks: empty stack when you need to pop, wrong type on top when you pop, or leftover stack when you're done. Every invalid string in this problem is exactly one of those three — nothing else."*

**Cut rule:** Do strings 2 and 4 only — they're the two genuinely distinct mid-scan failure modes; 1 and 3 are confirmations, not new information.

---

## ⚡ ALS Activity 2 — Live Coding / Dry-Run Relay: You Run the Stack (34–41 min)

**ALS format:** Live Coding / Dry-Run Relay — exposes whether students can execute the full algorithm themselves end to end, on a string they haven't seen. Chosen as the closing activity because it's the first time students run the complete algorithm start to finish, on eight characters in a row, without the safety of a partial example.

**Setup line:**
> *"New string: `{[()()]}`. I want the stack state after every single character — call it out before I write it."*

Run **one character at a time**, taking a prediction before each:

```
{   → push                    Stack: [{]
[   → push                    Stack: [{, []
(   → push                    Stack: [{, [, (]
)   → matches top (           Stack: [{, []
(   → push                    Stack: [{, [, (]
)   → matches top (           Stack: [{, []
]   → matches top [           Stack: [{]
}   → matches top {           Stack: []
```

End of string, stack empty → **valid**.

**How it surfaces:** At each `)`, confirm out loud what's being matched against — students should say "top of stack" every time, not "the most recent `(` I can remember," which breaks down on longer strings.

**Debrief line:**
> *"Every close only ever looks at one thing: the top of the stack. Not the whole string, not memory — just the top. That's the entire algorithm, executed eight times in a row."*

**Cut rule:** Do the first four characters only (`{[()`) plus the final `}` — enough to show both a push run and a full unwind to empty.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering the three failure modes and the count-isn't-enough misconception. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> Is `"[(])"` valid? Name the exact character where it fails and which failure mode it is.
> **Answer:** Invalid. At `]` (third character): stack top is `(` (from the second character), which doesn't match `]` — mismatched-type-on-close.

**Homework:** Trace `"{[]}()"` and `"{(})"` by hand, stating valid/invalid and why.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Equal counts of each bracket type means the string is balanced | Feels like the natural, simpler check | Slide Block A's `(){[{}])` example — 3 and 3, still invalid |
| Any closing bracket that has *appeared before* is a valid match | Students track "have I seen this type opened" instead of "is it on top *right now*" | ALS Activity 1, string 2 (`([)]`) — `[` was opened, but it's not on top when `)` arrives |
| A string with only opening brackets and no closers is "vacuously valid" since nothing ever mismatched | Nothing throws an error mid-scan, so it feels fine | ALS Activity 1, string 3 (`(((`) — explicitly checking the stack is empty *after* the loop ends |
| The stack needs to be checked for emptiness only at the very end | Natural to think of "empty" as a final-state property | ALS Activity 1, string 4 (`)(`) — the empty-stack check has to happen the instant a closing bracket arrives, mid-scan |
| Matching is based on position/index bookkeeping rather than the stack itself | Some students want to track opening positions in a separate array out of habit | Point out the stack's *top* already encodes "most recent unmatched opening" — no extra bookkeeping needed |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). This session's original 40-min version already had exactly 2 ALS activities and was flagged as the "lightest session since Monotonic Stack" — the conversion here mostly adds breathing room (fuller checkpoint framing, a third named failure mode) rather than cutting anything.
- **Two ALS activities this session, both carried over directly:** Activity 1 is Spot the Bug (naming the specific failure mode across four strings), Activity 2 is the Live Coding / Dry-Run Relay (running the full algorithm on a fresh 8-character string).
- **The Classroom Quiz now runs last, right before the Exit Ticket** — moved from its original mid-session position to match the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank.
- **This is session 24 of the Sem-3 sequence** (see `sem-3-sequence.md`).
- **ALS Activity 1 is the load-bearing activity.** It's the only place students name a *specific* failure mode rather than just voting valid/invalid. Do not cut it; cut ALS Activity 2 to its stated cut rule first if behind.
- **Have all four ALS Activity 1 strings and the ALS Activity 2 string written on the board before class starts** — writing them live burns time you don't have.
- **This session is a template for everything that follows in interviews:** stack-based validation of nested/paired structures shows up constantly (HTML tag matching, expression parsing). Say this explicitly if time allows — it's a strong motivation hook for why this "toy" problem matters.
