# Session 1a — Programming with Python (Part 1 of 2)

**Duration** 37 min · **Topic** Introduction to Python — What Software Is & Why Python · **Prerequisite** None — this is day one · **Session type** Concept lecture

<!-- Split note: original session-01 ran 60 min. Split right after the Classroom Quiz. Part 1 covers the diagnostic warm-up, the Java-vs-Python hook, the software/programming/syntax vocabulary block, and the real-world callout activity. Part 2 (session-01b) covers the actual `print()` mechanics, common mistakes, and the two hands-on coding activities — where students first touch the editor. -->

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Programming with Python | `837f23cb-d3be-4f96-877f-b76f7defe3e2` |
| RM — Programming with Python | `e57497b0-cccd-4ec6-bd44-5c791468d4f0` |
| RM — Python Setup & Coding in VS Code | `292ce498-2b51-44b2-bc2c-65666c09090c` |
| RM — Algorithms, Flowcharts, and Pseudocode | `7516496f-23c2-4460-9691-b70219d4dc8b` |
| Classroom Quiz A (21 q) | `9567f314-fd85-4ef2-a445-6d9907337545` |
| Classroom Quiz B (59 q) | `d303e3b9-9b7a-457b-8357-a74987ba0dcb` |
| MCQ Practice (56 q) | `3c0cf49d-4c57-4468-83ca-63cb7c63b1dd` |
| Coding Practice (2 q) | `81959e79-ceeb-448c-af0e-7e0e7f5447f0` |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define software, programming, code, and syntax, and state how they relate. *(REMEMBERING)*
2. Explain why Python is chosen for this course by comparing it against Java for the same task. *(UNDERSTANDING)*

*(Writing and running `print()`, arithmetic inside `print()`, and the four common `print()` errors are covered in Part 2 — where students first open the editor.)*

---

## Warm-Up Poll — Diagnostic (0–7 min)

> **This session is the exception.** There is no previous session to recall, so the poll is a *diagnostic*, not retrieval practice. No wrong answers. Purpose is to calibrate pace and to establish, on minute one, that this classroom expects everyone to answer.

Say: *"Seven quick questions. Nobody is graded, nobody is named. I need to know who I'm teaching."*

**Q1.** Have you written a computer program before — any language?
`A` Never · `B` Tried once or twice · `C` A few small programs · `D` Yes, comfortably
→ *Read:* If A+B > 60%, keep every code example at RM pace and do not skip the VS Code walkthrough.

**Q2.** Have you used Python specifically?
`A` No · `B` Heard of it, never used it · `C` Some · `D` Regularly

**Q3.** Do you have Python installed on the laptop you'll use for this course?
`A` No · `B` Not sure · `C` Yes · `D` Yes, plus VS Code
→ *Read:* Anything below 70% at C/D means you assign the Python Setup RM as compulsory homework tonight, not optional.

**Q4.** When you hear "software", what comes to mind first?
`A` Apps on my phone · `B` Windows / operating system · `C` Instructions a computer follows · `D` Not sure
→ *Read:* C is where the session lands. If almost nobody picks C, that's your hook — don't correct it now, let Slide Block A do it.

**Q5.** In your own guess — what does `print("Hello")` do?
`A` Prints on paper · `B` Shows `Hello` on screen · `C` Shows `"Hello"` with quotes · `D` No idea
→ *Read:* C is the quotes misconception showing up early. Note the number; Part 2's Activity 3 revisits it.

**Q6.** Which of these do you most want out of this course? *(MSQ — pick up to 2)*
`A` A job / placement · `B` Build my own projects · `C` Clear college coursework · `D` Curiosity

**Q7.** How do you prefer to learn code?
`A` Watch first, then try · `B` Try first, ask later · `C` Read the material · `D` Work with a partner
→ *Read:* If B+D is high, lean harder on Part 2's activities and shorten your talk-through.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Never name individuals. Total 7 min including your reads.

---

## Hook (7–10 min)

Put both of these on the board side by side, nothing else:

```java
class Main {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

```python
print("Hello World")
```

Ask: *"Both do exactly the same thing. Show of hands — who wants to learn the top one?"*

Let the laugh happen. Then: *"That's the whole reason this course is in Python. Same result, one line. By the end of Part 2 you'll write that line yourself and make a computer obey you."*

Tie back to **Q4** of the poll — *"Most of you said software is the apps on your phone. By the end of this block you'll have a sharper answer than that."*

---

## Slide Block A (10–22 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred from RM structure, confirm against deck -->
Covers: Software → Programming → Code → Syntax → Why Python → Applications → Career Opportunities.

**Beats to emphasise**

- **Syntax = grammar.** Use the students' own languages: a sentence with scrambled grammar is still understandable to a human, but a computer rejects it outright. This single analogy prevents most of the frustration in weeks 1–2.
- **Code is instructions, nothing more.** Deflate the mystique early.
- Spend real time on **Career Opportunities** — it is the motivation anchor for the entire course and costs you 90 seconds.

**Checkpoint (at 22 min)** — cold-call two students:
> *"Give me the difference between code and syntax in one sentence each."*
> **Answer:** Code is the instructions you write. Syntax is the set of rules those instructions must follow.

---

## ⚡ Activity 1 — Real-World Callout (22–27 min)

**Format:** Real-World Callout · **Exposes:** the belief that programming is abstract and disconnected from the software students actually use.

**Setup line (say this):**
> *"Thirty seconds. Think of one app or website you used in the last 24 hours. I want you to shout out the app, and then guess out loud what a programmer had to *tell* the computer to make that one feature work."*

**What students do:** Call out app names. You write them on the board in a fast list — no more than 8.

**How it surfaces:** For 3 of the apps, push once: *"What instruction? Say it like a command."* Accept plain English. e.g. Instagram → *"when the user double-taps, add a like."*

**Debrief line:**
> *"Every one of those is a set of instructions. That's all software is. You've been surrounded by it — Part 2 is where you start writing it."*

**Cut rule:** If running late, take 3 callouts instead of 8 and skip the push-for-instruction step. Do not cut the debrief line.

---

## Classroom Quiz (27–34 min)

5 MCQs from the platform pools. Run at ~80 s each including discussion.

**Q1** — `7918cf2f-e55d-411b-b16e-501709630ca2` *(Quiz A · REMEMBERING)*
Which of the following is referred as software in computer programming?
- ✅ **A set of instructions to the hardware**
- A physical component of a computer system
- A user interface design
- A type of computer virus

> *Explanation (platform):* In computer programming, software refers to a set of instructions that the hardware executes to perform tasks, not a physical component, a design element, or a virus.
> **If they pick "physical component":** they're conflating hardware with software. Point at the laptop, then at the code on screen.

**Q2** — `31ad6935-bb8a-4e34-a34c-17249e2c06c6` *(Quiz A · REMEMBERING)*
Which of the following best describes 'syntax' in programming languages?
- The instructions for installing software
- ✅ **The rules for writing code.**
- The process of compiling a program
- The user interface of a development environment

> *Explanation (platform):* Syntax in programming languages is the set of the rules for writing the code, ensuring that it is correctly formatted and can be understood by the computer.
> **If they pick "process of compiling":** the grammar analogy didn't land. Re-run it in one sentence before moving on.

**Q3** — `2bb88302-3225-4cf9-86bb-6b49fd71e4fe` *(Quiz A · UNDERSTANDING)*
Select the code that correctly prints "Hello World" in Python.
- ✅ **`print("Hello World")`**
- `echo "Hello World"`
- `Console.WriteLine("Hello World");`
- `System.out.println("Hello World");`

> *Explanation (platform):* In Python, the `print` statement is used to display text.
> **If they pick the Java option:** they were pattern-matching on the hook rather than reading. Harmless — say so and move on.

**Q4** — `3dcc4930-83e1-4f21-87d1-6184c5d5a652` *(Quiz B · APPLYING)*
Which of the following will fix the error in `Print("Hello World!")`?
- ✅ **The 'print' function should start with a lowercase 'p'.**
- The message should not be in quotes.
- The 'print' function should not have parentheses.
- There is no error in the code.

> *Explanation (platform):* In Python, the syntax rules require that the `print()` function name be written in lowercase. Using an uppercase 'P' as in `Print()` violates Python's syntax rules and will cause an error.
> **If >40% miss this:** stop. Python is case-sensitive and they haven't internalised it. State it as a rule, write it on the board, leave it there for the rest of the session.

**Q5** — `a51ca9ea-ee77-443b-bb3a-17672eebd42f` *(Quiz B · APPLYING)*
What will be the output of `print("2 + 5")`?
- `2`
- ✅ **`2 + 5`**
- `"7"`
- `7`

> *Explanation:* **[authored — the platform record for this question has an empty explanation field]** The quotes make `2 + 5` a text message, not a calculation. Python prints the characters exactly as written. Remove the quotes and Python does the arithmetic instead, giving `7`.
> **If they pick `7`:** the single most common misconception of this session. Do not fix it here — Part 2's Activity 3 runs exactly this comparison live.

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Whip-Around (34–37 min)

**Why this strategy here:** Part 1 has been entirely vocabulary and framing — no code has been typed yet. A fast round-robin locks in the software/code/syntax distinction and keeps energy up right before Part 2's first real hands-on moment.

**Run it (3 minutes):**
> *"Going around the room, one word or short phrase each: name ONE instruction a computer needs to do something you use daily — a login button, a like, a search bar. No repeats, go fast."*

Write nothing down — this is a warm-up for engagement, not a content check.

> *"Every one of those instructions, you're about to learn to write yourself. Part 2 — editor open, first real line of Python."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Software = the apps on my phone | Only consumer-facing software is visible | Slide Block A, reinforced by Activity 1's callouts |
| `Print` and `print` are the same | Every other written language they know is case-forgiving | Quiz Q4 — stated as a rule, written on the board, left up for the rest of the session |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz.**
- **Pacing risk:** Slide Block A's *Applications* and *Career Opportunities* lists are easy to over-talk. Cap the block at 12 minutes — the energy of this session lives in Part 2's activities, not the lists.
- **Day-one dynamic:** students will not volunteer yet. Activity 1 is deliberately the lowest-risk format in the bank (shout out an app name) to break that seal before Part 2's activities ask them to reason in front of peers.
- **Data note:** the poll here is diagnostic because there's no prior session anywhere in the course. Every other split session in this course opens Part 2 with retrieval practice on Part 1 instead — Part 2 of this session follows that same pattern.
- **Quiz Q5 (`a51ca9ea`) has an empty `answer_explanation` on the platform.** The explanation above is authored — review it before use, and consider filing a content fix.
