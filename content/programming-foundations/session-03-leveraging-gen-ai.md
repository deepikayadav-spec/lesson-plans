# Session 3 — Leveraging Gen AI for Accelerated Learning

**Duration** 60 min · **Topic** Introduction to Python · **Prerequisite** Sessions 1–2
**Session type** Support session. No classroom quiz, no reading material, no MCQ pool.

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Leveraging Gen AI for Accelerated Learning | `e89439e9-5e5e-4d4e-8f63-c55e4f81fd01` |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the difference between using AI to *get* an answer and using it to *understand* one. *(REMEMBERING)*
2. Write a prompt that asks for an explanation rather than a solution. *(APPLYING)*
3. Judge whether AI-produced code is correct by running it, not by trusting it. *(ANALYZING)*
4. Name the situations where using AI will damage their learning. *(UNDERSTANDING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Sessions 1–2**. Newly authored. Session 2 introduced no new syntax, so this poll recalls Session 1's concepts plus Session 2's four-step method.

**Q1.** What are the four steps for attacking a coding problem?
`A` Read, Restate, Write, Run · `B` Think, Type, Test, Submit · `C` Copy, Paste, Run, Fix · `D` Plan, Code, Debug, Deploy
→ **A.** *Targets:* Session 2's method. *Misconception:* C is a real answer some will pick honestly — it's your opening for today.

**Q2.** What does `print(6 * 7)` output?
`A` `6 * 7` · `B` `42` · `C` `"42"` · `D` Error
→ **B.** *Targets:* Arithmetic without quotes.

**Q3.** What does `print("6 * 7")` output?
`A` `42` · `B` `6 * 7` · `C` `42.0` · `D` Error
→ **B.** *Targets:* Quotes vs arithmetic. *If >40% wrong:* this is the third session it's appeared. Stop and fix it now — two lines, live.

**Q4.** `print(###)` prints nothing. Why?
`A` `#` isn't a valid character · `B` `#` starts a comment, so Python ignores the rest of the line · `C` Hashes must be in quotes to exist · `D` It's a silent error
→ **B.** *Targets:* Comments, from Session 2's walkthrough.

**Q5.** Python hits an error on line 4 of a 6-line program. What happens to lines 5 and 6?
`A` They run normally · `B` They never run · `C` They run with a warning · `D` Only line 6 runs
→ **B.** *Targets:* Top-to-bottom execution, from Session 2's Human Compiler.

**Q6.** Which produces a `NameError`? *(MSQ — select all)*
`A` `Print("Hi")` · `B` `prnt("Hi")` · `C` `print("Hi")` · `D` `print("Hi"`
→ **A and B.** *Targets:* Error-type discrimination. D is a SyntaxError, not a NameError — that distinction is the point. *Misconception:* selecting D means they still treat all errors as one category.

**Q7.** Have you used ChatGPT or similar for coursework? *(No wrong answer)*
`A` Never · `B` Once or twice · `C` Regularly · `D` Every day
→ *Read:* This calibrates the whole session. A room at C/D needs the guardrails emphasis; a room at A/B needs the capability demo first.

---

## Hook (7–10 min)

Put a coding problem on screen. Ask the AI tool to solve it, live, in front of everyone. Paste the answer in, run it. It works.

Let the room sit with that for a second. Then:

> *"So that's it, right? Course over. Except — I want one person to tell me what line three does."*

Take a volunteer. Most rooms cannot answer.

> *"That's the trap. The code works and nobody in this room understands it. In eight weeks you'll be in an interview with no AI, and this exact gap is what shows up. Today isn't about whether you use these tools — you will. It's about using them so you get smarter instead of more dependent."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred, no deck available to confirm — see Instructor Notes -->
Covers: what Gen AI tools can do for a learner, where they help, where they hurt, how to prompt.

**Beats to emphasise**

- **The distinction that matters:** asking for an *answer* versus asking for an *explanation*. Everything else in the session hangs off this.
- **Verification is not optional.** AI produces confident, wrong code routinely. Running it is the only test.
- Keep the tone practical, not moralising. Students will use these tools regardless; a lecture about honesty loses the room. Frame it entirely as self-interest — *"this is how you avoid being the person who can't answer in an interview."*

**Checkpoint (at 22 min)** — cold-call:
> *"Give me one question you could ask an AI that would make you smarter, and one that would make you weaker."*
> **Model answer:** Smarter — *"explain why this line uses quotes."* Weaker — *"write the answer to problem 3."*

---

## ⚡ Activity 1 — Think–Pair–Share (22–28 min)

**Format:** Think–Pair–Share · **Exposes:** that students haven't distinguished between using a tool and outsourcing to it.

**Setup line:**
> *"One minute alone, two minutes with the person next to you, then I take answers. Question: you're stuck on a coding problem for ten minutes. What is the best thing to type into an AI tool — and what's the worst?"*

**Timing:** 1 min silent · 2 min pairs · 3 min report-out from three pairs.

**What good answers look like**

| Better prompt | Worse prompt |
|---|---|
| *"I wrote this and got this error. What is the error telling me?"* | *"Solve this problem."* |
| *"Explain what this line does, one word at a time."* | *"Give me the code."* |
| *"Give me a similar, simpler problem to practise."* | *"Is this right?"* (without reading it yourself) |

**Debrief line:**
> *"Notice the pattern. The good ones all keep you at the keyboard. The bad ones move you off it."*

**Cut rule:** 30 s think, 90 s pair, two reports.

---

## Slide Block B (28–42 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred, no deck available to confirm -->
Covers: prompting technique, verification, and the limits of these tools.

**Beats to emphasise**

- **Show a wrong answer.** Ask the AI something slightly ambiguous and let it produce confidently incorrect code. Run it. This single demo does more than any warning.
- **Prompting is a skill, not a trick.** Specific context in, useful answer out.
- **Never paste code you can't explain.** Make this the session's one hard rule.

**Checkpoint (at 42 min)** — show hands:
> *"AI gives you five lines of code and it runs correctly. Are you done?"*
> **Answer:** No. Not until you can say what each line does.

---

## ⚡ Activity 2 — Write the Question (42–50 min)

**Format:** Write the Question · **Exposes:** whether students can construct a prompt that teaches them something, rather than one that hands them an answer.

**Setup line:**
> *"Everyone writes one prompt. The rule: it must be a prompt that would help you learn, and it must be about something we've actually covered — printing, quotes, arithmetic, errors. You have three minutes."*

**What students do:** Write one prompt on paper or in chat.

**How it surfaces:** Collect four. Read them out anonymously. For each, ask the room: *"Does this make the person smarter or weaker?"*

Then **run the best one live** against a real tool and evaluate the answer together — is it correct? Is it clear? Would you have learned from it?

**Debrief line:**
> *"You just wrote the difference between a student who uses AI and a student who's used by it. Same tool, different question."*

**Cut rule:** Collect two prompts instead of four; skip the live run.

---

## ⚡ Activity 3 — Real-World Callout (50–57 min)

**Format:** Real-World Callout · **Exposes:** the assumption that AI is a general-purpose oracle rather than a tool with specific failure modes.

**Setup line:**
> *"Shout out one time an AI tool gave you something confidently wrong. Any subject, not just code."*

**What students do:** Call out examples. You list them on the board — cap at six.

**How it surfaces:** For two of them, push: *"How did you find out it was wrong?"* The answer is almost always *"I checked"* or *"someone told me."*

**Debrief line:**
> *"Every one of those was caught by verification. In this course your verification is the run button. If you didn't run it, you don't know it works — no matter how confident the answer looked."*

**Cut rule:** Three callouts, one push, keep the debrief.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket:**

> Write one prompt you will actually use this week, and the rule you're going to follow about pasting code.
> **Expected rule:** don't paste anything you can't explain line by line.

**Homework**

> *"Same two problems from Session 1, if you still haven't submitted them. And this week, every time you use an AI tool for this course, ask it to explain — not to solve. You'll know within a week whether it's working."*

| Task | Unit |
|---|---|
| Coding Practice — Session 1 set | `81959e79-ceeb-448c-af0e-7e0e7f5447f0` |
| MCQ Practice — Session 1 set, 56 questions | `3c0cf49d-4c57-4468-83ca-63cb7c63b1dd` |

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Working code means understood code | Output looks the same either way | The hook — nobody can explain line three |
| AI answers are reliable | They're fluent and confident | Demoing a confidently wrong answer in Slide Block B |
| Using AI is cheating, full stop | Framed that way elsewhere | Reframing entirely as self-interest, not honesty |
| Prompting is just asking | No exposure to a better version | Activity 2 — comparing prompts side by side |
| I'll understand it later | Deferred effort feels free | Naming the interview scenario, concretely |

---

## Instructor Notes

- **You need a live AI tool on the projector.** Test it before class. Have a fallback screenshot ready if the network fails — the hook does not work without a live demo.
- **Tone is everything in this session.** Moralising loses the room in the first two minutes. Every argument here is self-interest: *this is how you avoid looking stupid in an interview.* That lands; "don't cheat" does not.
- **Warm-up Q7 changes your emphasis.** A room that already uses these tools daily needs the guardrails and the wrong-answer demo. A room that's barely used them needs the capability side first, or the warnings are abstract.
- **Slide placement is unverified.** The deck exists on the platform but was not readable when this plan was written, so Block A/B contents are inferred from the session title and objectives. Confirm the split against the real deck and adjust the two blocks — the activities can slot anywhere between them.
- **Pacing risk:** Activity 2's live run can rabbit-hole. Cap it at 3 minutes and move.
- **Data note:** no reading material, no classroom quiz, no MCQ pool exists for this session on the platform. Homework points back to Session 1.
