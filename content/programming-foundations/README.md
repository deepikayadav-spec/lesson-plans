# Programming Foundations — Lesson Plans, Sessions 1–15

Instructor-facing lesson plans for the first 15 sessions, built to raise engagement in 60-minute live classes.

Every plan is grounded in the platform export `../programming_foundations.json` — quiz questions are quoted verbatim with their real `question_id`s, and every unit ID resolves to a live platform unit.

---

## The sessions

| # | Session | Type | Deck | Quiz pools | Coding |
|---|---|---|---|---|---|
| [1](./session-01-programming-with-python.md) | Programming with Python | Concept | ✅ | A 21 · B 59 | 2 |
| [2](./session-02-coding-practice-walkthrough-part-1.md) | Coding Practice Walkthrough Part 1 | Support | ❌ none | — | — |
| [3](./session-03-leveraging-gen-ai.md) | Leveraging Gen AI | Support | ✅ | — | — |
| [4](./session-04-variables-and-data-types.md) | Variables and Data Types | Concept | ✅ | A 19 · B 46 | 2 |
| [5](./session-05-sequence-of-instructions.md) | Sequence of Instructions | Concept | ✅ | A 49 · C 34 | 2 |
| [6](./session-06-input-and-output-basics.md) | Input and Output Basics | Concept | ✅ | A 39 · B 75 | 15 |
| [7](./session-07-how-to-debug-your-code.md) | How to Debug Your Code | Support | ✅ | — | — |
| [8](./session-08-type-conversions.md) | Type Conversions | Concept | ✅ | A 34 · B 55 ⚠️ | 18 |
| [9](./session-09-relational-operators.md) | Relational Operators | Concept | ❌ none | A 52 · B 38 | 10 |
| [10](./session-10-logical-operators.md) | Logical Operators | Concept | ❌ none | A 31 · B 26 · C 29 | 15 |
| [11](./session-11-conditional-statements.md) | Conditional Statements | Concept | ❌ none | A 41 · B 33 | 13 |
| [12](./session-12-nested-conditional-statements.md) | Nested Conditional Statements | Concept | ✅ | A 30 · B 31 | 12 |
| [13](./session-13-loops.md) | Loops | Concept | ✅ | A 34 · B 27 | 11 |
| [14](./session-14-understanding-coding-question-formats.md) | Understanding Coding Question Formats | Support | ✅ | — MCQ only | — |
| [15](./session-15-for-loop.md) | For Loop | Concept | ✅ | A 56 only | 39 |

**Also here**

- **[Practice Session Playbook](./practice-session-playbook.md)** — the 60-minute script for dedicated MCQ + coding practice blocks. Instructor-facing, run it identically every time.
- **[Progress board visual reference](https://claude.ai/code/artifact/8faafc7f-0d8c-45ee-b679-0833076656cd)** — what to draw on the whiteboard and how to read the tallies.
- `_ops-practice-protocol-brief.md` — reasoning, rollout expectations and troubleshooting behind the playbook. **Not for instructors.**

---

## Session structure (60 minutes)

Every concept session follows the same shape. Timings always total 60.

| Time | Block |
|---|---|
| 0–7 | **Warm-Up Poll** — 6–8 newly authored MCQ/MSQ on the previous session |
| 7–10 | **Hook** |
| 10–22 | **Slide Block A** — deck delivered as-is |
| 22–27 | **⚡ Activity 1** |
| 27–34 | **Classroom Quiz** — 5 real questions from the platform pools |
| 34–44 | **Slide Block B** — deck delivered as-is |
| 44–50 | **⚡ Activity 2** |
| 50–57 | **⚡ Activity 3** |
| 57–60 | **Exit Ticket + Homework** |

Then: **Common Misconceptions** and **Instructor Notes**.

**Slide content is never modified.** Plans specify only which range to deliver, which beats to emphasise, and where activities sit between blocks. Longest stretch of passive listening is 12 minutes.

**Support sessions** (2, 3, 7, 14) have no classroom quiz pool on the platform, so that block becomes a third activity or a live walkthrough of MCQ practice questions.

**Sessions without a deck** (2, 9, 10, 11) replace Slide Blocks with **Teaching Blocks** — full board content, the exact code to type, and tables to build with the class, all written out from the reading material. They are deliverable as written.

---

## Activities

Each session runs 2–3, never repeating a format within a session, and no format appears in three consecutive sessions.

Every activity block is **self-contained** — written for an instructor who has never run that format. Each includes: what the activity is, why it's in this session, before-class prep, a minute-by-minute run table, the exact words to say, the answers, a **when it goes wrong** table, the most common instructor mistake, and a cut rule for when time runs short.

**The bank:** Predict the Output · Spot the Bug · Think–Pair–Share · Human Compiler · Fill the Blank Live · Rapid Fire Board Race · Error Message Match · Real-World Callout · Trace the Table · Write the Question · Live Coding

---

## Warm-up polls

All newly authored — not lifted from the practice pools. 6–8 questions on the previous session, mixed MCQ and MSQ, ~45 seconds each.

Every question states the correct answer, the concept it targets, the misconception a wrong pick reveals, and — where it matters — the 30-second reteach if more than 40% get it wrong.

Difficulty ramps: first two recall, next three or four application, last one or two analysis. At least two per session target a documented mistake from the previous session's reading material.

**Session 1 is the exception** — no prior session exists, so its poll is a diagnostic used to calibrate pace.

---

## Known data gaps

Carried from the platform export. None of these are errors in the plans; each is worked around and flagged in the relevant Instructor Notes.

| Gap | Sessions | Handling |
|---|---|---|
| **No video and no slide deck** | 2, 9, 10, 11 | Teaching Blocks written from the reading material |
| **Deck exists but was unreadable** | 3, 7, 14 | Block contents inferred; marked `<!-- placement: inferred -->` |
| **Quiz pool doesn't match session topic** | 8 | Quiz A is slicing, Quiz B is Session 5 reassignment. Conversion questions exist only in MCQ Practice, so the quiz draws 2 + 3 |
| **Only one quiz pool** | 15 | All five questions from Quiz A |
| **No classroom quiz pool at all** | 2, 3, 7, 14 | Replaced with a third activity or a live MCQ walkthrough |
| **Transcripts expired** | all | S3 presigned URLs lapsed 2026-08-05. Reading material and question tags used instead |

### Content issues worth fixing on the platform

1. **15 questions have an empty `answer_explanation`.** Explanations are authored in the plans and labelled as such, but this is a systematic gap rather than a handful of oversights. Worth an audit.
2. **Session 5, question `9ae028e4`** has a wrong answer key — it marks `3` where Python returns `3.0`. Avoided in the plans and flagged.
3. **Session 11, question `b6cc2147`** has two defensible options; one describes the error, the other describes the fix, and only the first is marked correct. Students will argue. Handled in the plan.
4. **Session 8's quiz pools** don't cover the session's title topic. An instructor picking five questions at random would assess the wrong thing entirely.
5. **`REARRANGE` and `CODE_ANALYSIS_TEXTUAL` questions have no correct option marked** — 549 across these sessions. Correct for their interaction type, but it means they cannot be used in a live vote. Quiz selection draws only from `MULTIPLE_CHOICE`, `CODE_ANALYSIS_MULTIPLE_CHOICE` and `MORE_THAN_ONE_MULTIPLE_CHOICE`.

---

## Verification

All 15 plans are checked by script against the source JSON, not by eye:

1. Every `unit_id` and `question_id` cited exists in the export.
2. Every quoted quiz answer matches the `is_correct` option in the data.
3. Every timeline covers 0–60 with no gaps or overlaps.
4. Required sections present; no placeholder text.
5. No activity format repeats within a session, and none appears in three consecutive sessions.

---

## Not in this pass

- **DSA lesson plans** — blocked on a content export in the same shape as `programming_foundations.json`. The DSA folder currently holds only a sequence skeleton: session names, unit IDs and platform URLs, with no question bank, reading material or slide content.
- **Sessions 16+** — the course continues with *Comparing Strings & Naming Variables*, then nested loops, lists, functions, and OOP.
- **A frontend for browsing these plans** — planned separately; markdown is the interim format.
