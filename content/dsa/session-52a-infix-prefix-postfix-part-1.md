# Session 52a — Infix, Prefix, and Postfix (Part 1 of 2)

**Duration** 39 min · **Topic** Stack & Queue — Expression Notations & Precedence · **Prerequisite** Session 51 — Stack Implementation Using Linked List · **Session type** Concept lecture

<!-- Split note: original session-52 ran 60 min. Split right after the Classroom Quiz. Part 1 covers operator/operand vocabulary, precedence/associativity, and the three notations (infix/prefix/postfix) with side-by-side examples. Part 2 (session-52b) covers the stack-based conversion algorithm and its full worked dry run — the algorithmic core of the topic. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Infix, Prefix, and Postfix | https://docs.google.com/presentation/d/1f58-Pm4m_3hWMLcdPlCaZW8_zwLXOMh4HGyf3m-VNE0/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define operator, operand, and expression, and state the precedence/associativity of `()`, `^`, `*`/`/`/`%`, and `+`/`-`. *(REMEMBERING)*
2. Distinguish infix, prefix (Polish Notation), and postfix (Reverse Polish Notation) by where the operator sits relative to its operands. *(UNDERSTANDING)*
3. Explain why prefix and postfix notation never need parentheses to fix evaluation order. *(UNDERSTANDING)*

*(The stack-based conversion algorithm and its full worked dry run are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 51 (Stack Using Linked List) (0–6 min)

Say: *"Eight on the linked-list stack, then we leave stack mechanics behind for a bit and talk about expressions."*

**Q1.** In a linked-list stack, `top` corresponds to:
`A` The tail of the list · `B` The head of the list · `C` The middle node · `D` A separate index variable

**Q2.** The correct order for `push` is:
`A` Update top → link new node → create node · `B` Create node → link its `next` to the old top → update top · `C` Link next → create node → update top · `D` Order doesn't matter

**Q3.** The correct order for `pop` is:
`A` Delete the top node → then move `top` to `top->next` · `B` Move `top` to `top->next` → then delete the old node · `C` Delete and move simultaneously · `D` Order doesn't matter
→ *Read:* If Q2/Q3 aren't both near-unanimous, that's last session's core rule not sticking — a 20-second recap is worth it before moving to today's very different topic.

**Q4.** What happens if you delete the old top node *before* reassigning `top`?
`A` Nothing, it's equivalent · `B` `top` becomes a dangling pointer — reading `top->next` next is undefined behaviour · `C` The stack silently becomes empty · `D` A compile error

**Q5 (MSQ — pick all correct).** Which are genuine advantages of a linked-list stack over an array-based one?
`A` Dynamic size · `B` No fixed-capacity overflow · `C` Faster direct-index access · `D` No shifting of other elements needed for push/pop
→ *Read:* Correct: A, B, D. C is the array stack's advantage, not the linked list's — if anyone picks it, that's the two implementations blending together in memory.

**Q6.** True or False: a linked-list stack can never fail to push under any circumstances.
`A` True · `B` False

**Q7.** `empty()` on a linked-list stack checks:
`A` `top == -1` · `B` `top == null` · `C` `size == capacity` · `D` `top->next == null`

**Q8.** What is the time complexity of push, pop, and top on a linked-list stack?
`A` O(n) · `B` O(1) · `C` O(log n) · `D` Depends on stack size

**Running it** — poll tool, ~30 s per question. Total 6 min including reads.

---

## Hook (6–9 min)

Write on the board: `8 / 4 + 2`. Ask: *"What does this evaluate to?"* Someone will say 4 (÷ first, giving 2, plus 2 = 4). Good — that's correct, and it only works because *you* know division happens before addition.

Then say: *"Now imagine you're a very literal calculator with no built-in sense of precedence, reading left to right. How do I write this expression so you can evaluate it correctly *without ever needing to know a precedence rule, and without a single parenthesis*?"*

Let a couple of guesses land or fail. Then: *"That's not a trick question — it's a solved problem, and it's exactly what postfix and prefix notation are for. By the end of Part 2 you'll convert any expression into a form a dumb, literal machine can evaluate with zero ambiguity."*

---

## Slide Block A (9–17 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 5–8: Operator & Operand, Expression, Parentheses, Precedence & Associativity -->
Covers: Operator vs Operand → Expression → Parentheses (grouping, not operators/operands themselves) → Precedence & Associativity table.

**Beats to emphasise**

- **Operators** (`+ - * / ^`) act on **operands** (`a, b, 1, 2, A, B...`). Simple, but say it explicitly — the whole conversion algorithm is built on classifying every symbol as one or the other (plus parentheses as a third, special case).
- **Precedence table, read top to bottom exactly as ranked:** `()` highest, `^` (right-to-left associativity), `*`/`/`/`%` (left-to-right), `+`/`-` (left-to-right, lowest).
- **Associativity is the tie-breaker when precedence is equal.** Flag `^` as the odd one out — it's the only right-to-left operator in this table, and it will matter later in the worked example (`... ^ f` at the very end of the expression).

**Checkpoint (at 17 min)** — cold-call:
> *"`a + b * c` — which operator executes first, and why?"*
> **Answer:** `*` executes first — multiplication has higher precedence than addition, regardless of left-to-right reading order.

---

## ⚡ Activity 1 — Predict-the-Output: "Write It Without Parentheses" (17–23 min)

**Format:** Predict-the-Output · **Exposes:** whether students can apply precedence intuitively to produce postfix *before* seeing the formal stack algorithm — priming them for why the algorithm's precedence-popping rule exists.

**Setup line (say this):**
> *"No algorithm yet — just your own reasoning. `8 / 4 + 2`. Operators must come *after* their operands, no parentheses allowed. Write the postfix form. Ninety seconds, then I want hands up."*

**What students do:** Attempt it individually, then share answers.

**Correct answer (from the deck's own example):** `8 4 / 2 +`

Follow immediately with a harder one: `a + (b * c) - d` → expect `a b c * + d -`.

**How it surfaces:** The most common wrong answer for the second one is `a b + c * d -` (evaluating strictly left to right, ignoring that `*` inside the parentheses must resolve *before* the `+`). When this comes up, ask: *"If a machine read your version left to right, what would it compute first — and is that what the original expression means?"* Let them catch the mismatch themselves.

**Debrief line:**
> *"Even with no parentheses, postfix isn't 'operators wherever' — precedence is still baked into the *order* operators appear in. Part 2's mechanical algorithm is really just a disciplined way of getting this right every single time, even when you can't eyeball it."*

**Cut rule:** If running short, do only `8 / 4 + 2` and skip the harder parenthesised example — the core insight (precedence still matters) is demonstrated either way.

---

## Slide Block B (23–31 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide grouping — Slides 9–13: Infix, Prefix (Polish Notation), Postfix (Reverse Polish Notation), Examples table -->
Covers: Infix (operator between operands — what humans read) → Prefix / Polish Notation (operator *before* operands) → Postfix / Reverse Polish Notation, RPN (operator *after* operands) → side-by-side examples table for all three expressions.

**Beats to emphasise**

- **Infix is for humans; prefix and postfix are for machines.** Say this framing explicitly — it's the "why do we even need this" answer.
- Walk the examples table row by row: `8 / 4 + 2` → prefix `+ / 8 4 2`, postfix `8 4 / 2 +`. `a + (b*c) - d` → prefix `- + a * b c d`, postfix `a b c * + d -`. Point out these match exactly what Activity 1 just had students derive by hand.
- **Neither prefix nor postfix ever needs a parenthesis** — the position of the operator itself fully encodes the grouping. This is the direct payoff of the Hook's challenge.

**Checkpoint (at 31 min)** — show of hands:
> *"In postfix `a b c * +`, which operation happens first when this is evaluated?"*
> **Answer:** `b * c` — you scan left to right and evaluate an operator the moment you have its two operands ready.

---

## Classroom Quiz (31–36 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: 3-2-1 Reflection (36–39 min)

**Why this strategy here:** Part 1 delivered three notations plus a full precedence/associativity table. Before Part 2's dense algorithmic dry run, a structured reflection consolidates the vocabulary and flags which piece (precedence vs. associativity vs. notation itself) is still shaky.

**Run it (3 minutes):**
> *"On paper, thirty seconds each: THREE things you now know cold — pick from operator/operand, the three notations, or the precedence table. TWO things still fuzzy. ONE guess at why `^` got flagged as 'the odd one out' in the precedence table."*

Skim a few "2 fuzzy things" answers out loud. If associativity comes up repeatedly, that's expected — it's the subtlest idea — but flag it for a 20-second callback before Part 2's dry run reaches the `^` step.

> *"Hold onto that `^` guess. Part 2's entire worked example hinges on exactly that one exception."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Postfix conversion ignores precedence since there are no parentheses | "No parentheses" sounds like "no rules" | Activity 1 — showing that a naive left-to-right postfix guess produces the wrong evaluation order |
| Prefix and postfix are just infix "with the operator moved," evaluated the same way | The three notations share the same operators and operands, so they look like cosmetic reorderings | Slide Block B's checkpoint — evaluating `a b c * +` left to right and showing operators fire the moment both operands are ready, a genuinely different evaluation mechanism |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz** — a natural seam, since the deck's Classroom Quiz slot already sits right before the conversion algorithm begins.
- **This session has no code implementation slides** — the deck stays entirely at the level of manual conversion (rules + one fully worked dry run in Part 2). Don't introduce code; match the deck's own scope.
