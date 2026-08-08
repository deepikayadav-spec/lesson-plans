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

**Verified against the deck.** Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1 | Welcome | Skip |
| 2–3 | **Agenda** | AI-Powered Learning → Code Explanation → Generation, with callouts *Maximize your learning with AI* and *Code / Quiz / Coding-problem generation* |
| 4 | **Why Python?** | AI · Data Science · Machine Learning · Supportive Community |
| 5 | Section card | *AI-Powered Learning* |
| 6 | **AI-Powered Learning** | "AI tools can help you write code faster, but they **shouldn't replace your understanding**" |
| 7 | **AI-Powered Learning** | "To truly master Python you need core concepts, logic, and creativity behind problem-solving" |
| 8 | **Three steps** | 1 Use AI tools like ChatGPT/Gemini → 2 Implement structured prompting → 3 Enhance your learning |
| 9 | **Think · Reason · Explore** | "Instead of relying on AI to hand you code, use it as a **tutor**" |
| 10 | **Better prompts** | "Learning to write better prompts is a skill that amplifies your growth with AI" |

**Beats to emphasise**

- **Slide 4 is a recap from Session 1.** Twenty seconds, no more — the room has seen it.
- **Slides 6 and 9 carry the whole session.** "Shouldn't replace your understanding" and "use it as a tutor, not a vending machine" are the two sentences students should leave with. Everything else is mechanism.
- **Slide 9's Think / Reason / Explore** is the frame for Activity 1 — name it there and refer back.

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

**Verified against the deck.** This is the practical half — it hands students **three reusable prompt templates.**

| # | Slide | Content |
|---|---|---|
| 11 | **Your First Python Program using AI** | "Let's start by using AI to help you write and understand your very first Python program" |
| 12 | Section card | *Coding Explanation* |
| 13 | **Coding Explanation** | ⭐ **Prompt template:** *"Explain what the given code does and then simplify/break down the given code in python into steps, and explain each step in simple terms to a school kid in India who has just learned Python"* — shown with a worked code example |
| 14 | **Generating Code** | "AI can help to generate code from scratch" |
| 15 | Section card | *Quiz Generation* |
| 16 | **Quiz Generation** | "Gen AI can create personalized quizzes based on what you've just learned" |
| 17 | **Quiz follow-up** | ⭐ **Prompt:** *"Now, increase the difficulty of the questions on [concept], and ask questions that are hard and tricky. If I couldn't answer the questions, provide explanations for the questions."* |
| 18 | **Coding Problem Generation** | ⭐ **Full prompt template** with `[current concept/topic]` and `[List of previous concepts/topics]` placeholders — asks the AI to specify task, input format, output format, sample test cases, edge cases, and to review the student's solution afterwards |
| 19 | Next Session | Closing |

**Beats to emphasise**

- **The three starred slides are the takeaway.** Tell students explicitly to screenshot or copy slides 13, 17 and 18 — they are reusable for the whole course, not just today.
- **Slide 18 is the most valuable single slide in this session.** It generates practice problems calibrated to exactly what they've learned so far. Spend real time on the two placeholders and how to fill them.
- **Slide 17's follow-up move** — asking the AI to make it harder — is the difference between passive quizzing and deliberate practice.

> ⚠️ **Slide 13's code example is far beyond this session.** It uses a `while` loop, `int(input())` and a counter — content from Sessions 8 and 13. At Session 3 students have only seen `print()`. **Do not walk the class through that code.** Show the *prompt*, say the code is a preview of week three, and move on. If you trace it line by line you will lose the room for ten minutes.

**Checkpoint (at 42 min)** — show hands:
> *"AI gives you five lines of code and it runs correctly. Are you done?"*
> **Answer:** No. Not until you can say what each line does.

---

## ⚡ Activity 2 — Write the Question (42–50 min)

**Format:** Write the Question · **Exposes:** whether students can construct a prompt that teaches them something, rather than one that hands them an answer.

> **Use the deck's own templates.** Slides 13, 17 and 18 hand students working prompts. Adapting a real template beats inventing one from scratch — and it means what they write today is something they'll actually reuse.

**Setup line:**
> *"Slide eighteen is on screen. That's a professional-grade prompt with two blanks in it. Your job: fill both blanks for **where you actually are** — you finished Session 1 and 2, you know `print`, quotes and arithmetic. Write the version you'd send tonight. Three minutes."*

Leave slide 18 projected the whole time.

**What students do:** Fill in `[current concept/topic]` and `[List of previous concepts/topics]` on paper or in chat.

**How it surfaces:** Collect four. Read them out anonymously. For each ask: *"Would the problem this generates be solvable with what we know today?"*

That question is the whole activity. Students routinely write *"loops"* or *"functions"* into the blank because it sounds impressive, then get a problem they cannot attempt — which is exactly how they end up pasting an AI answer they don't understand.

Then **run the best one live** and read the generated problem together. Ask: *can we actually solve this right now?*

**Debrief line:**
> *"The template did the hard part. The skill is being honest about what you've actually learned. Overstate it and the AI hands you something you can only copy."*

**Cut rule:** Collect two instead of four; skip the live run.

---

## ⚡ Activity 3 — Real-World Callout (50–57 min)

**Format:** Real-World Callout · **Exposes:** the assumption that AI is a general-purpose oracle rather than a tool with specific failure modes.

> ⚠️ **This activity is instructor-added, not deck-supported.** The deck covers what AI is *good* for and never mentions that it produces confident wrong answers. That's a real gap — students will meet hallucinated code within a week. Keep this activity; it is the only verification content in the session.

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
- ✅ **Verified against the real deck** (*"Copy of Session 1 — Leveraging Gen AI for Accelerated learning"*, 40 animation steps, ~19 slides). Slide Blocks A and B list the actual slides in order.
- **The deck's real value is three prompt templates** (slides 13, 17, 18). Tell students to copy them. Most of this session's long-term benefit is those templates being reused across the next fourteen sessions.
- ⚠️ **Deck gap: nothing about AI being wrong.** There is no slide on hallucination, verification, or checking output. The deck is entirely about what these tools are good for. Activity 3 is the only counterweight — don't cut it. **Worth raising with the content team.**
- ⚠️ **Deck gap: slide 13's code example is three sessions ahead** (`while`, `int(input())`, counter). Show the prompt, not the code. Flagged in Slide Block B.
- **Pacing risk:** Activity 2's live run can rabbit-hole. Cap it at 3 minutes and move.
- **Data note:** no reading material, no classroom quiz, no MCQ pool exists for this session on the platform. Homework points back to Session 1.
