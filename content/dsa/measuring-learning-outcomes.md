# Measuring Learning Outcomes — Metrics Guide

**For instructors and course leads.** What to measure across a DSA session, why, and what's missing before any of it can actually run.

---

## 1. Per-session metrics

Each session plan already has four natural measurement points — no new structure needed, just capture at these points:

| Point | What it measures | Metric |
|---|---|---|
| Warm-Up Poll | Readiness, not mastery — diagnostic only | % of class at each response tier (ungraded) |
| Classroom Quiz | Mid-session check on the objective just taught | % correct per question |
| Activities | Applied understanding under time pressure | Completion rate + which misconceptions surface |
| Exit Ticket | End-of-session mastery bar | % of class clearing the bar |

**Exit Ticket pass rate is the headline number per session** — everything else explains *why* it landed where it did.

---

## 2. Per-objective metrics (Bloom-level mastery)

Every Learning Objective in a session is already tagged with a cognitive level — *REMEMBERING*, *UNDERSTANDING*, *ANALYZING*, etc.

Metric: % of students demonstrating that level, using the quiz/exit-ticket item that maps to it.

Why it matters: a session can show a fine overall pass rate while every "ANALYZING" item is failing — raw score hides that. Reporting by objective/level catches it.

---

## 3. Retention metric (cross-session)

Next session's Warm-Up Poll re-probes the prior session's core objective.

**Retention rate = recall at Day+N ÷ exit-ticket score at Day 0.**

Flags sessions that "passed" on the day but didn't stick.

---

## 4. Topic rollup (cohort level)

Roll up exit-ticket pass rate + misconception recurrence rate across all sessions in a topic (Binary Tree, BST, Heaps, Bit Manipulation, Linked List, Stack & Queue).

Low rollup on a topic → re-teach candidate, independent of any single session's number.

---

## 5. What's needed before any of this runs

None of the above is capturable yet. Three gaps:

1. **Answer keys / rubrics** — quiz and exit-ticket items are prompts only right now, no scoring key attached.
2. **Objective → item mapping** — objectives are numbered in each session, but quiz/exit-ticket items don't reference which objective they test.
3. **Capture layer** — the site is static (markdown → HTML), no backend. Need a form/LMS (e.g. Google Form + Sheet per session) to actually record responses.

---

## One-line summary

Exit Ticket pass rate = headline. Quiz + Bloom-level breakdown = the "why." Next-session poll = retention. Topic rollup = where to re-teach. None of it works until answer keys, objective tags, and a capture form exist.
