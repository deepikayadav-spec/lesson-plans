# Session 22 — Infix, Prefix, and Postfix Notations

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Stack — Expression Notations, Precedence, Infix-to-Postfix Conversion · **Prerequisite** Session 21 — Next Greater Element
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Infix, Prefix, and Postfix | https://docs.google.com/presentation/d/1f58-Pm4m_3hWMLcdPlCaZW8_zwLXOMh4HGyf3m-VNE0/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define operator, operand, and expression, and state the precedence/associativity of `()`, `^`, `*`/`/`/`%`, and `+`/`-`. *(REMEMBERING)*
2. Distinguish infix, prefix (Polish Notation), and postfix (Reverse Polish Notation) by where the operator sits relative to its operands, and explain why prefix/postfix never need parentheses. *(UNDERSTANDING)*
3. Convert an infix expression containing parentheses and mixed-precedence operators to postfix, using the stack-based algorithm. *(APPLYING)*
4. Trace the algorithm's stack and output contents symbol by symbol for a multi-operator expression, including the one case where associativity (not just precedence) decides whether to pop. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 21 (3–7 min) · ALS: Polling

5 questions on **Session 21 (Next Greater Element)**. ~45 s each, project the distribution, never name individuals.

**Q1.** The optimal Next Greater Element approach scans:
`A` Left to right · `B` Right to left · `C` From the middle outward · `D` It doesn't matter
→ **B.**

**Q2.** Which type of monotonic stack does NGE use?
`A` Increasing · `B` Decreasing · `C` Either · `D` Neither
→ **B.**

**Q3.** What's the time complexity of the brute-force NGE approach?
`A` O(n) · `B` O(n²) · `C` O(log n) · `D` O(1)
→ **B.**

**Q4.** What does the stack hold in the optimal NGE approach?
`A` The final answers · `B` Candidates that might still be someone's next-greater element · `C` A sorted copy of the array · `D` Nothing — it's unused
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about NGE?
`A` The last element's answer is always `-1` · `B` A strictly decreasing array gives `-1` for every position · `C` Both approaches can give different final answers · `D` Each element is pushed once, popped at most once in the optimal approach
→ **A, B, D.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Write on the board: `8 / 4 + 2`. Ask: *"What does this evaluate to?"* Someone will say 4 (÷ first, giving 2, plus 2 = 4) — correct, and it only works because *you* know division happens before addition.

> *"Now imagine you're a very literal calculator with no built-in sense of precedence, reading left to right. How do I write this expression so you can evaluate it correctly *without ever needing to know a precedence rule, and without a single parenthesis*?"*

Let a couple of guesses land or fail.

> *"That's not a trick question — it's a solved problem, and it's exactly what postfix and prefix notation are for. By the end of today you'll convert any expression into a form a dumb, literal machine can evaluate with zero ambiguity."*

---

## Slide Block A (10–17 min) — DELIVER SLIDES AS-IS

Covers: Operator vs Operand → Expression → Parentheses (grouping, not operators/operands themselves) → Precedence & Associativity table.

**Beats to emphasise**

- **Operators** (`+ - * / ^`) act on **operands** (`a, b, 1, 2, A, B...`). The whole conversion algorithm is built on classifying every symbol as one or the other, plus parentheses as a third, special case.
- **Precedence table, top to bottom:** `()` highest, `^` (right-to-left associativity), `*`/`/`/`%` (left-to-right), `+`/`-` (left-to-right, lowest).
- **Associativity is the tie-breaker when precedence is equal.** Flag `^` as the odd one out — the only right-to-left operator in this table, and it matters later in the worked example.

**Checkpoint (at 17 min)** — cold-call:
> *"`a + b * c` — which operator executes first, and why?"*
> **Answer:** `*` executes first — multiplication has higher precedence than addition, regardless of left-to-right reading order.

---

## ⚡ ALS Activity 1 — Predict the Output: Write It Without Parentheses (17–22 min)

**ALS format:** Predict-the-Output — exposes whether students can apply precedence intuitively to produce postfix *before* seeing the formal stack algorithm, priming them for why the algorithm's precedence-popping rule exists. Chosen right after Slide Block A because it's the bridge between "precedence as a rule" and "precedence as something baked into symbol order."

**Setup line:**
> *"No algorithm yet — just your own reasoning. `8 / 4 + 2`. Operators must come *after* their operands, no parentheses allowed. Write the postfix form. Ninety seconds, then hands up."*

Attempt it individually, then share answers. **Correct answer:** `8 4 / 2 +`

Follow immediately with a harder one: `a + (b * c) - d` → expect `a b c * + d -`.

**How it surfaces:** The most common wrong answer for the second one is `a b + c * d -` (evaluating strictly left to right, ignoring that `*` inside the parentheses must resolve *before* the `+`). Ask: *"If a machine read your version left to right, what would it compute first — and is that what the original expression means?"*

**Debrief line:**
> *"Even with no parentheses, postfix isn't 'operators wherever' — precedence is still baked into the *order* operators appear in. The mechanical algorithm coming up is really just a disciplined way of getting this right every single time, even when you can't eyeball it."*

**Cut rule:** Do only `8 / 4 + 2` and skip the harder parenthesised example.

---

## Slide Block B (22–28 min) — DELIVER SLIDES AS-IS

Covers: Infix (operator between operands — what humans read) → Prefix / Polish Notation (operator *before* operands) → Postfix / Reverse Polish Notation, RPN (operator *after* operands) → side-by-side examples table.

**Beats to emphasise**

- **Infix is for humans; prefix and postfix are for machines.** Say this framing explicitly — it's the "why do we even need this" answer.
- Walk the examples table: `8 / 4 + 2` → prefix `+ / 8 4 2`, postfix `8 4 / 2 +`. `a + (b*c) - d` → prefix `- + a * b c d`, postfix `a b c * + d -`. These match exactly what ALS Activity 1 just had students derive by hand.
- **Neither prefix nor postfix ever needs a parenthesis** — the position of the operator itself fully encodes the grouping. This is the direct payoff of the Hook's challenge.

**Checkpoint (at 28 min)** — show of hands:
> *"In postfix `a b c * +`, which operation happens first when this is evaluated?"*
> **Answer:** `b * c` — you scan left to right and evaluate an operator the moment you have its two operands ready.

---

## Slide Block C (28–36 min) — DELIVER SLIDES AS-IS

Covers: The stack-based infix-to-postfix conversion algorithm, then the deck's full worked dry run on `a + b * c / (d - e) ^ f`.

**Beats to emphasise**

- **The rules, as a checklist:**
  1. Operand → straight to output.
  2. `(` → push onto the stack.
  3. `)` → pop to output until a `(` is found, then **discard** that `(` — it never goes to output or stays on the stack. *(The single most-missed detail: if a student's postfix ever contains a `(`, this is the bug.)*
  4. Operator → pop from the stack to output while the stack's top has **higher or equal precedence** (respecting associativity), *then* push the current operator.
  5. After the scan finishes: pop everything remaining on the stack to the output.
- **Narrate the full dry run on `a + b * c / (d - e) ^ f`, symbol by symbol:** `a`→output. `+`→stack empty, push. `b`→output. `*`→top is `+` (lower precedence), don't pop, push `*`. `c`→output. `/`→top is `*` (equal precedence, left-to-right), pop `*` to output, push `/`. `(`→push. `d`→output. `-`→top is `(`, don't pop across it, push `-`. `e`→output. `)`→pop `-` to output, discard the `(`.
- **Stop here — this is where ALS Activity 2 picks up.** So far: **Stack: `+, /`. Output: `a b c * d e -`.**
- **Call out the subtlety already visible:** the `)` step popped `-` but discarded `(` entirely — never emitted, never left on the stack.

**Checkpoint (at 36 min)** — cold-call, mid-recap:
> *"Right after processing the `)` that closes `(d - e)`, what does the stack contain, and what has the output produced so far?"*
> **Answer:** Stack: `+`, `/`. Output so far: `a b c * d e -`.

---

## ⚡ ALS Activity 2 — Live Coding / Dry-Run Relay: Finish the Conversion (36–41 min)

**ALS format:** Live Coding / Dry-Run Relay — exposes whether students can apply the precedence-popping rule themselves on the trailing, trickiest part of the expression (`^`, right-associative, interacting with `/` sitting on the stack). Chosen as the closing activity because this is the one step in the entire worked example where associativity — not just precedence — decides the outcome.

**Setup line:**
> *"We're picking up exactly where the last slide left off: stack has `+`, `/` on it, output is `a b c * d e -`. Remaining symbols: `^`, `f`, end-of-string. For each one, tell me the new stack and the new output *before* I confirm."*

Run **one symbol at a time**:

```
^     → Compare against stack top '/'. ^ has HIGHER precedence than /, so do NOT pop.
        Push ^.  Stack: [+, /, ^]   Output: a b c * d e -
f     → Operand, straight to output.
        Stack: [+, /, ^]   Output: a b c * d e - f
(end) → Pop everything left on the stack, in order: ^, then /, then +.
        Stack: []   Output: a b c * d e - f ^ / +
```

**How it surfaces:** Before revealing the `^` step, ask explicitly: *"Would we pop `/` here if `^` were left-to-right associative instead of right-to-left?"* Correct answer: yes — this is the one place in the whole example where associativity changes the outcome. Common wrong answer: students pop `/` before pushing `^`, treating "higher or equal precedence" as "any operator on the stack" — re-read rule 4 aloud: pop only while the stack top is higher-**or-equal**, and `/` is lower than `^`, so it stays.

**Debrief line:**
> *"You just did, symbol by symbol, exactly what the algorithm does mechanically. There's no cleverness beyond 'compare precedence, maybe pop, always push.' That's why a computer can do this reliably and a human parsing by eye can't, at scale."*

**Cut rule:** Skip the associativity discussion question and just confirm each step's stack/output directly.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering the four conversion rules, the discard-not-emit rule for `(`, and the associativity exception. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> Convert `a * b + c` to postfix by hand, one symbol at a time, showing the stack state after each step.
> **Answer:** `a` → output `a`. `*` → stack empty, push. `b` → output `a b`. `+` → top is `*` (higher/equal precedence), pop `*` to output, then push `+`. Output: `a b *`. `c` → output `a b * c`. End → pop `+`. **Final postfix: `a b * c +`.**

**Homework:** Convert `(a - b) / c * d` to postfix by hand, tracking stack and output at every symbol.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Postfix conversion ignores precedence since there are no parentheses | "No parentheses" sounds like "no rules" | ALS Activity 1 — showing a naive left-to-right postfix guess produces the wrong evaluation order |
| The matching `(` is popped to the output along with the operators inside it | Rule 3 is easy to skim as "pop until you see `(`" without registering "then discard it" | Slide Block C's explicit callout, isolating exactly this omission |
| "Pop while higher precedence" also means pop when precedence is lower or unrelated | The rule has two clauses (precedence *and* associativity) that are easy to compress into one | Slide Block C's narration of the `/` vs `^` comparison, where nothing is popped |
| Right-to-left associativity (`^`) behaves the same as left-to-right (`+ - * /`) | Every other operator in the table is left-to-right, so `^` looks like an outlier worth ignoring | ALS Activity 2's explicit "would we pop if `^` were left-associative?" question |
| Prefix and postfix are just infix "with the operator moved," evaluated the same way | The three notations share the same operators and operands, so they look like cosmetic reorderings | Slide Block B's checkpoint — evaluating `a b c * +` and showing operators fire the moment both operands are ready, a genuinely different evaluation mechanism |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Merged from two original sessions ("Infix, Prefix, and Postfix" Parts 1 and 2, 39 + 31 min = 70 min) into one 50-min session — see `sem-3-sequence.md`. This is a dense merge; content was tightened for pace, not cut in substance.
- **Two ALS activities this session:** Activity 1 is Predict the Output (write postfix by intuition, before the formal algorithm), Activity 2 is the Live Coding / Dry-Run Relay (finishing the worked conversion at its trickiest step). Both carried over from the originals. The original Part 1 "3-2-1 Reflection" wrap is dropped (lowest content value, easiest cut); the original Part 2 "Spot the Bug: The Missing Discard" is folded into a callout inside Slide Block C instead of running as its own activity.
- **The Classroom Quiz now runs last, right before the Exit Ticket** — moved from its original mid-session position(s) to match the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank.
- **This is session 22 of the Sem-3 sequence** (see `sem-3-sequence.md`).
- **The single worked example (`a + b * c / (d - e) ^ f`) is doing a lot of work** — it's the only concrete conversion run end-to-end, and it deliberately includes every rule (operand, low-precedence push, equal-precedence pop, parenthesis push/pop/discard, and the one associativity exception with `^`). Don't substitute a simpler example for pacing — if you must trim, cut narration speed, not coverage.
- **This session has no code implementation slides** in the source — the deck stays entirely at the level of manual conversion. Don't introduce code; match the deck's own scope.
- **The `^` vs `/` step (ALS Activity 2) is the one moment worth slowing down for.** Everything else in the dry run is "pop while higher-or-equal, then push" on repeat; this is the only step where the answer is "don't pop," and it's precisely because of associativity, not precedence alone.
- **Set up the next few sessions at the close, if time allows:** "Everything from here — monotonic stacks, next greater element, balanced parentheses — reuses this exact 'push while a condition holds, otherwise pop' pattern. Today's mechanical rule *is* the pattern."
