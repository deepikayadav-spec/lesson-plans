# Session 52b — Infix, Prefix, and Postfix (Part 2 of 2)

**Duration** 31 min · **Topic** Stack & Queue — Infix-to-Postfix Conversion Algorithm · **Prerequisite** Session 52a — Infix, Prefix, and Postfix, Part 1 (notations, precedence, associativity) · **Session type** Concept lecture

<!-- Split note: continues session-52 (original 60 min) right after the Classroom Quiz. This part is the algorithmic core of the topic — the stack-based conversion rules and the full multi-operator, parenthesised worked dry run. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Infix, Prefix, and Postfix | https://docs.google.com/presentation/d/1f58-Pm4m_3hWMLcdPlCaZW8_zwLXOMh4HGyf3m-VNE0/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Convert an infix expression containing parentheses and mixed-precedence operators to postfix, using the stack-based algorithm. *(APPLYING)*
2. Trace the algorithm's stack and output contents symbol by symbol for a multi-operator expression. *(ANALYZING)*

---

## Warm-Up Poll — Retrieval Practice on Session 52a (0–5 min)

Say: *"Four quick ones on notation before we build the algorithm that does the conversion for us."*

**Q1.** In postfix, where does the operator sit relative to its operands?
`A` Before both · `B` Between them · `C` After both · `D` Anywhere
→ *Read:* C.

**Q2.** Which operator is right-to-left associative?
`A` `+` · `B` `-` · `C` `*` · `D` `^`
→ *Read:* D — the one exception in the table.

**Q3.** `a + b * c` in postfix is:
`A` `+ a * b c` · `B` `a b c * +` · `C` `a b + c *` · `D` `a * b + c`
→ *Read:* B.

**Q4.** In Part 1's reflection, what made `^` "the odd one out"?
→ *Read:* Open response — reconnects to right-to-left associativity before it matters in today's dry run.

**Running it** — poll tool, ~30 s/question. Total 5 min including reads.

---

## Bridge (5–7 min)

Say: *"You can produce postfix by reasoning it out by hand on a short expression. Today: the mechanical rule that does it reliably even when the expression is too long to eyeball — and one exception, right at the end, that only makes sense because of that `^` you flagged."*

---

## Slide Block C (7–21 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 14–38: Steps to Convert Infix to Postfix, worked example on "a + b * c / (d - e) ^ f" -->
Covers: The stack-based conversion algorithm, then the deck's full worked dry run on `a + b * c / (d - e) ^ f`.

**Beats to emphasise**

- **The four rules, stated as a checklist before the dry run starts:**
  1. Operand → straight to output.
  2. `(` → push onto the stack.
  3. `)` → pop to output until a `(` is found, then **discard** that `(` (it never goes to output or stays on the stack).
  4. Operator → pop from the stack to output while the stack's top has **higher or equal precedence** (respecting associativity), *then* push the current operator.
  5. After the scan finishes: pop everything remaining on the stack to the output.
- Narrate the full dry run on `a + b * c / (d - e) ^ f` symbol by symbol, matching the deck exactly:
  - `a` → output. `+` → stack empty, push. `b` → output. `*` → top of stack is `+` (lower precedence), so don't pop, push `*`. `c` → output. `/` → top is `*` (equal precedence, left-to-right), pop `*` to output, then push `/`. `(` → push. `d` → output. `-` → top is `(`, don't pop across it, push `-`. `e` → output. `)` → pop `-` to output, discard the `(`. `^` → top is now `/` (lower precedence than `^`), don't pop, push `^`. `f` → output. End of string → pop remaining stack (`^`, then `/`, then `+`) to output.
  - **Final postfix:** `a b c * d e - f ^ / +`
- **Call out the one subtlety that trips students up:** when comparing `/` (already on stack) against the incoming `^`, `^` is higher precedence, so nothing gets popped — `^` is simply pushed on top. This is the associativity/precedence rule doing real work, not just parentheses.

**Checkpoint (at 21 min)** — cold-call, mid-recap:
> *"Right after processing the `)` that closes `(d - e)`, what does the stack contain, and what has the output produced so far?"*
> **Answer:** Stack: `+`, `/` (from before the parenthesis). Output so far: `a b c * d e -`.

---

## ⚡ Activity 2 — Live Coding / Dry-Run Relay: "Finish the Conversion" (21–27 min)

**Format:** Live Coding / Dry-Run Relay · **Exposes:** whether students can apply the precedence-popping rule themselves on the trailing, trickiest part of the expression (the `^`, which is right-associative and interacts with `/` sitting on the stack) — rather than just having watched it happen.

**Setup line (say this):**
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

**How it surfaces:** Before revealing the `^` step, ask explicitly: *"Would we pop `/` here if `^` were left-to-right associative instead of right-to-left?"* Correct answer: yes — this is the one place in the whole example where associativity (not just precedence) changes the outcome, so make students state *why* `^` doesn't trigger a pop.

**Common wrong answer:** students pop `/` before pushing `^`, treating "higher or equal precedence" as "any operator on the stack." Correct by re-reading rule 4 aloud: pop only while the stack top is higher-**or-equal**, and `/` is lower than `^`, so it stays.

**Debrief line:**
> *"You just did, symbol by symbol, exactly what the algorithm does mechanically. There's no cleverness beyond 'compare precedence, maybe pop, always push.' That's why a computer can do this reliably and a human parsing by eye can't, at scale."*

**Cut rule:** If running short, skip the associativity discussion question and just confirm each step's stack/output directly.

---

## ⚡ Activity 3 — Spot the Bug: "The Missing Discard" (27–29 min)

**Format:** Spot the Bug · **Exposes:** the easy-to-miss detail in rule 3 — that the matching `(` must be *discarded*, not pushed to output or left on the stack.

**Setup line (say this):**
> *"Someone converts `(a + b) * c` and gets this buggy postfix. Ten seconds — what's wrong?"*

Put this on screen:

```
Buggy output:  a b + ( * c
```

**What students do:** Hands up with the error.

**Answer:** The `(` should never appear in the output at all — rule 3 says pop to output until you *hit* the `(`, then throw the `(` away. The correct postfix is `a b + c *`.

**Debrief line:**
> *"The open parenthesis's whole job is to be a wall on the stack that stops premature popping. Once a matching `)` arrives and does its job, the `(` has nothing left to do — it's discarded, never emitted."*

**Cut rule:** If running very short, cut this activity entirely and fold the rule restatement into the Slide Block C beats instead.

---

## Exit Ticket (29–31 min)

> Convert `a * b + c` to postfix by hand, one symbol at a time, showing the stack state after each step.
> **Answer:** `a` → output `a`. `*` → stack empty, push. `b` → output `a b`. `+` → top is `*` (higher/equal precedence), pop `*` to output, then push `+`. Output: `a b *`. `c` → output `a b * c`. End → pop `+`. **Final postfix: `a b * c +`.**

Scan responses on the way out. If several students stop popping too early (leaving an operator stranded on the stack at the end), that's rule 5 ("pop everything remaining after the scan") not landing — reopen Session 53 with a quick recap.

**Homework:** convert `(a - b) / c * d` to postfix by hand, tracking stack and output at every symbol. <!-- placement: inferred — no homework/RM/practice units exist for this course per deviation #2 -->

---

## Common Misconceptions (Part 2 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| The matching `(` is popped to the output along with the operators inside it | Rule 3 is easy to skim as "pop until you see `(`" without registering "then discard it" | Activity 3's Spot the Bug, isolating exactly this omission |
| "Pop while higher precedence" also means pop when precedence is lower or unrelated | The rule has two clauses (precedence *and* associativity) that are easy to compress into one | Slide Block C's explicit narration of the `/` vs `^` comparison, where nothing is popped |
| Right-to-left associativity (`^`) behaves the same as left-to-right (`+ - * /`) | Every other operator in the table is left-to-right, so `^` looks like an outlier worth ignoring | Activity 2's explicit "would we pop if `^` were left-associative?" question |

---

## Instructor Notes

- **This is Part 2 of a 60-minute original session, split right after the Classroom Quiz.**
- **The single worked example (`a + b * c / (d - e) ^ f`) is doing a lot of work** — it's the only concrete conversion the deck runs end-to-end, and it deliberately includes every rule (operand, low-precedence push, equal-precedence pop, parenthesis push/pop/discard, and the one associativity exception with `^`). Don't substitute a simpler example for pacing — if you must trim, cut narration speed, not coverage.
- **The `^` vs `/` step is the one moment worth slowing down for.** Everything else in the dry run is "pop while higher-or-equal, then push" on repeat; this is the only step where the answer is "don't pop," and it's precisely because of associativity, not precedence alone.
- **Set up the next few sessions.** Closing line, if time allows: "Everything from here — monotonic stacks, next greater element, balanced parentheses — reuses this exact 'push while a condition holds, otherwise pop' pattern. Today's mechanical rule *is* the pattern."
