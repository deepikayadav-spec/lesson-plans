# Session 3 — Leveraging Gen AI for Accelerated Learning

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Introduction to Python · **Prerequisite** Sessions 1–2
**Session type** Support session. No classroom quiz, no reading material, no MCQ pool. · **Format** 50-min recalibrated, 2 ALS activities

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

## Classroom Settling (0–3 min) · Buffer — not instructional

Live AI tool tested and open on the projector, fallback screenshot ready in case the network fails, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** project or state the MCQ Practice completion number since Session 1. No shaming, just visibility: *"X% completion, target is 80%. Anyone still not done finishes it in the room today."*

5 questions on **Sessions 1–2**, the ones today's session leans on. ~45 s each, project the distribution, never name individuals.

**Q1.** What are the four steps for attacking a coding problem?
`A` Read, Restate, Write, Run · `B` Think, Type, Test, Submit · `C` Copy, Paste, Run, Fix · `D` Plan, Code, Debug, Deploy
→ **A.** *Targets:* Session 2's method. *Misconception:* C is a real answer some will pick honestly — it's your opening for today.

**Q2.** What does `print("6 * 7")` output?
`A` `42` · `B` `6 * 7` · `C` `42.0` · `D` Error
→ **B.** *Targets:* Quotes vs arithmetic. *If >40% wrong:* this is the third session it's appeared. Stop and fix it now — two lines, live.

**Q3.** Python hits an error on line 4 of a 6-line program. What happens to lines 5 and 6?
`A` They run normally · `B` They never run · `C` They run with a warning · `D` Only line 6 runs
→ **B.** *Targets:* Top-to-bottom execution, from Session 2's Human Compiler. Ties directly into today's hook.

**Q4.** Which produces a `NameError`? *(MSQ — select all)*
`A` `Print("Hi")` · `B` `prnt("Hi")` · `C` `print("Hi")` · `D` `print("Hi"`
→ **A and B.** *Targets:* Error-type discrimination. D is a SyntaxError, not a NameError — that distinction is the point. *Misconception:* selecting D means they still treat all errors as one category.

**Q5.** Have you used ChatGPT or similar for coursework? *(No wrong answer)*
`A` Never · `B` Once or twice · `C` Regularly · `D` Every day
→ *Read:* This calibrates the whole session. A room at C/D needs the guardrails emphasis; a room at A/B needs the capability demo first.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

**Explain-the-answer beat (~20 s):** *"Q3 is why today matters — if you can't trace what a line does, you can't tell when AI-written code is about to break on line 5."*

---

## Hook (7–10 min)

Put a coding problem on screen. Ask the AI tool to solve it, live, in front of everyone. Paste the answer in, run it. It works.

Let the room sit with that for a second. Then:

> *"So that's it, right? Course over. Except — I want one person to tell me what line three does."*

Take a volunteer. Most rooms cannot answer.

> *"That's the trap. The code works and nobody in this room understands it. In eight weeks you'll be in an interview with no AI, and this exact gap is what shows up. Today isn't about whether you use these tools — you will. It's about using them so you get smarter instead of more dependent."*

---

## Slide Block A (10–20 min) — DELIVER SLIDES AS-IS

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

- **Slide 4 is a recap from Session 1.** Ten seconds, no more — the room has seen it.
- **Slides 6 and 9 carry the whole session.** "Shouldn't replace your understanding" and "use it as a tutor, not a vending machine" are the two sentences students should leave with. Everything else is mechanism.
- **Slide 9's Think / Reason / Explore** is the frame for ALS Activity 1 — name it there and refer back.

**Checkpoint (at 20 min)** — 10 s silent think, then cold-call:
> *"Give me one question you could ask an AI that would make you smarter, and one that would make you weaker."*
> **Model answer:** Smarter — *"explain why this line uses quotes."* Weaker — *"write the answer to problem 3."*

---

## ⚡ ALS Activity 1 — Think-Pair-Share (20–26 min)

**ALS format:** Think-Pair-Share. Chosen because the question has no single right answer — it's a judgment call about prompt quality, and judgment calls sharpen through comparing reasoning with a peer before committing.

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

## Slide Block B (26–37 min) — DELIVER SLIDES AS-IS

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

**Verification reality-check (90 s, before the checkpoint):** the deck never mentions AI being confidently wrong — this beat is the counterweight, kept short instead of a full activity.
> *"Quick one — shout out a time an AI tool gave you something confidently wrong. Any subject, not just code."* Take 3 callouts, list on the board. Push once: *"How did you find out it was wrong?"* Answer is almost always *"I checked."*
> *"That's the whole point. In this course your verification is the run button. If you didn't run it, you don't know it works — no matter how confident it sounded."*

**Checkpoint (at 37 min)** — show hands:
> *"AI gives you five lines of code and it runs correctly. Are you done?"*
> **Answer:** No. Not until you can say what each line does.

---

## ⚡ ALS Activity 2 — Student-Generated Prompt Design: Write the Question (37–44 min)

**ALS format:** Student-Generated Task Design. Chosen instead of a repeat of Think-Pair-Share because the skill here is production, not discussion — students have to construct and own a real artifact (a working prompt) rather than compare opinions on one.

> **Use the deck's own templates.** Slides 13, 17 and 18 hand students working prompts. Adapting a real template beats inventing one from scratch — and it means what they write today is something they'll actually reuse.

**Setup line:**
> *"Slide eighteen is on screen. That's a professional-grade prompt with two blanks in it. Your job: fill both blanks for **where you actually are** — you finished Session 1 and 2, you know `print`, quotes and arithmetic. Write the version you'd send tonight. Three minutes."*

Leave slide 18 projected the whole time.

**What students do:** Fill in `[current concept/topic]` and `[List of previous concepts/topics]` on paper or in chat.

**How it surfaces:** Collect three. Read them out anonymously. For each ask: *"Would the problem this generates be solvable with what we know today?"*

That question is the whole activity. Students routinely write *"loops"* or *"functions"* into the blank because it sounds impressive, then get a problem they cannot attempt — which is exactly how they end up pasting an AI answer they don't understand.

Then **run the best one live** and read the generated problem together. Ask: *can we actually solve this right now?*

**Debrief line:**
> *"The template did the hard part. The skill is being honest about what you've actually learned. Overstate it and the AI hands you something you can only copy."*

**Cut rule:** Collect two instead of three; skip the live run.

---

## Exit Ticket + Quiz Push (44–48 min)

**Exit ticket** (~30 s):

> Write one prompt you will actually use this week, and the rule you're going to follow about pasting code.
> **Expected rule:** don't paste anything you can't explain line by line.

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Anyone not yet at 100% on MCQ Practice — open it now. At least 3 more questions before you leave your seat. Try asking the AI to explain a question you get wrong, not just give you the answer — that's today's whole lesson, applied immediately."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 4's warm-up."*

**Remaining homework**

> *"Same two problems from Session 1, if you still haven't submitted them. And this week, every time you use an AI tool for this course, ask it to explain — not to solve. You'll know within a week whether it's working."*

| Task | Unit |
|---|---|
| Coding Practice — Session 1 set | `81959e79-ceeb-448c-af0e-7e0e7f5447f0` |
| MCQ Practice — Session 1 set, 56 questions *(started in class above — finish the rest)* | `3c0cf49d-4c57-4468-83ca-63cb7c63b1dd` |

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Working code means understood code | Output looks the same either way | The hook — nobody can explain line three |
| AI answers are reliable | They're fluent and confident | The verification reality-check beat in Slide Block B |
| Using AI is cheating, full stop | Framed that way elsewhere | Reframing entirely as self-interest, not honesty |
| Prompting is just asking | No exposure to a better version | ALS Activity 1 — comparing prompts side by side |
| I'll understand it later | Deferred effort feels free | Naming the interview scenario, concretely |

---

## Instructor Notes

- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair** — closes last session's loop, opens this one's. Target is 80% platform MCQ attempt rate, currently ~33%. Don't skip either half even under time pressure.
- **You need a live AI tool on the projector.** Test it before class. Have a fallback screenshot ready if the network fails — the hook does not work without a live demo.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). No classroom quiz, no reading material, no MCQ pool for this session — it's a support session by design.
- **Two ALS activities this session, both different from Sessions 1 and 2:** Activity 1 is Think-Pair-Share, Activity 2 is Student-Generated Task Design (students produce a real artifact, not a discussed opinion). The original third activity (Real-World Callout, on AI's confident wrong answers) is folded into a 90-second beat inside Slide Block B instead of running as its own block — the content survives, it just isn't a scheduled activity anymore.
- **Tone is everything in this session.** Moralising loses the room in the first two minutes. Every argument here is self-interest: *this is how you avoid looking stupid in an interview.* That lands; "don't cheat" does not.
- **Warm-up Q5 changes your emphasis.** A room that already uses these tools daily needs the guardrails and the wrong-answer demo. A room that's barely used them needs the capability side first, or the warnings are abstract.
- ✅ **Verified against the real deck** (*"Copy of Session 1 — Leveraging Gen AI for Accelerated learning"*, 40 animation steps, ~19 slides). Slide Blocks A and B list the actual slides in order.
- **The deck's real value is three prompt templates** (slides 13, 17, 18). Tell students to copy them. Most of this session's long-term benefit is those templates being reused across the next fourteen sessions.
- ⚠️ **Deck gap: nothing about AI being wrong.** There is no slide on hallucination, verification, or checking output. The deck is entirely about what these tools are good for. The verification reality-check beat in Slide Block B is the only counterweight — don't cut it. **Worth raising with the content team.**
- ⚠️ **Deck gap: slide 13's code example is three sessions ahead** (`while`, `int(input())`, counter). Show the prompt, not the code. Flagged in Slide Block B.
- **Pacing risk:** Activity 2's live run can rabbit-hole. Cap it at 2 minutes and move — the window is 7 minutes, not 8, in this format.
- **Data note:** no reading material, no classroom quiz, no MCQ pool exists for this session on the platform. Homework points back to Session 1.
