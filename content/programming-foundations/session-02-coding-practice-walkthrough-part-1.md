# Session 2 — Coding Practice Walkthrough | Part 1

**Duration** 60 min · **Topic** Introduction to Python · **Prerequisite** Session 1
**Session type** Support session — walkthrough. No classroom quiz, no reading material, **no slide deck.**

**Platform units**

| Resource | Unit ID |
|---|---|
| Video — Coding Practice Walkthrough Part 1 | `f2a6cdec-7135-4db4-9466-d80aa26999fd` |
| *(Problems walked through belong to Session 1)* | `81959e79-ceeb-448c-af0e-7e0e7f5447f0` |

> ⚠️ **No deck exists for this session.** You are the content. Everything below is a live-typing session — laptop on the projector from minute 10 to minute 57. Have the editor open and the font size at 18pt+ before students arrive.

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the four steps of attacking any coding problem — read, restate, write, run. *(REMEMBERING)*
2. Restate a problem statement in their own words before writing any code. *(UNDERSTANDING)*
3. Write and submit a solution on the platform without assistance. *(APPLYING)*
4. Read a Python error message and identify which line to fix. *(ANALYZING)*

---

## Warm-Up Poll — Prior Knowledge Activation (0–7 min)

7 questions on **Session 1**. Newly authored. ~45 s each, project the distribution, never name individuals.

**Q1.** What is *syntax* in a programming language?
`A` The instructions you write · `B` The rules those instructions must follow · `C` The output of a program · `D` A Python library
→ **B.** *Targets:* Syntax definition. *Misconception:* picking A means they've merged code and syntax into one idea. *If >40% wrong:* one sentence — *"Code is what you write. Syntax is the rulebook it has to obey."*

**Q2.** What does `print(2 + 5)` output?
`A` `2 + 5` · `B` `7` · `C` `"7"` · `D` Error
→ **B.** *Targets:* Printing without quotes. *Misconception:* A means quotes-vs-no-quotes hasn't landed.

**Q3.** What does `print("2 + 5")` output?
`A` `7` · `B` `2 + 5` · `C` `"2 + 5"` · `D` Error
→ **B.** *Targets:* Printing with quotes. *Misconception:* A is the core Session 1 misconception. *If >40% wrong:* type both lines live right now, before the hook. This must be solid before they attempt problems.

**Q4.** Which of these will **fail**? *(MSQ — select all)*
`A` `print("Hi")` · `B` `Print("Hi")` · `C` `prnt("Hi")` · `D` `print(Hi)`
→ **B, C and D.** *Targets:* Possible Mistakes. *Misconception:* missing B means case-sensitivity is still not internalised.

**Q5.** `Print("Hello")` produces which error?
`A` SyntaxError · `B` NameError · `C` No error · `D` IndentationError
→ **B.** *Targets:* Error-message recognition. *Misconception:* students guess "SyntaxError" for everything. *If >40% wrong:* they aren't reading error text at all — call it out, it's the whole point of today.

**Q6.** What does `print(10 / 5)` output?
`A` `2` · `B` `2.0` · `C` `5` · `D` `2.5`
→ **B.** *Targets:* Division always returns a decimal. *Misconception:* A is school-maths carryover.

**Q7.** You get an error you don't understand. First move?
`A` Delete the line and retry · `B` Read the error message and find the line number · `C` Ask a friend · `D` Restart the laptop
→ **B.** *Targets:* Debugging habit. No wrong-answer shaming here — this one sets up the session.

---

## Hook (7–10 min)

Ask for a show of hands, honestly:

> *"Who attempted the two coding problems last night?"*

Whatever the number, don't react to it. Then:

> *"Here's what I know happens. You open the problem, you read it, and your brain says 'I don't know how to start.' So you close it. That feeling is not a sign you can't code. It's a sign nobody has shown you the first move. That's the entire hour."*

Write the four steps on the board and leave them there all session:

```
1. READ      the whole statement, out loud if needed
2. RESTATE   say what it wants in your own words
3. WRITE     the simplest thing that could work
4. RUN       read the output or read the error
```

---

## Walkthrough Block A (10–22 min) — *Hello World*

You type. Projector on. Narrate every keystroke including the boring parts.

**Run all four steps explicitly, naming them as you go:**

1. **Read** — put the problem statement on screen. Read it aloud, whole. *"Write a program that prints `Hello World` as output."*
2. **Restate** — *"In my words: show those two words on the screen. That's it. Nothing else."*
3. **Write** — type `print("Hello World")`. Say why quotes: *"It's a message, not a calculation."*
4. **Run** — show the output. Then **submit on the platform** and show the pass state.

**Show the submission flow deliberately.** Many students have never submitted and don't know what "accepted" looks like. Show them where the button is, what green means, what happens on failure.

**Then break it on purpose:**

```python
print("Hello World)
```

Submit that. Let the failure appear. Read the error aloud, calmly, and fix it.

> *"That's the loop. Write, run, read, fix. You're not supposed to get it right first time — nobody does."*

**Checkpoint (at 22 min):**
> *"What's step 2, and why does it exist?"*
> **Answer:** Restate it in your own words — because if you can't say what the program should do, you can't write it.

---

## ⚡ Activity 1 — Fill the Blank Live (22–28 min)

**Format:** Fill the Blank Live · **Exposes:** that students can recognise correct code but can't yet produce it.

**Setup line:**
> *"I'm typing exactly what you say. Not what you mean — what you say. Character for character."*

Put this on screen:

```python
_____("Three Hashes")
```

Take the answer. Type **literally** what the student says. If they say "print", type `print`. If someone says "Print", type `Print` and run it — let the `NameError` land.

Then escalate, one blank at a time:

```python
print(_____)          →  "###"
_____(_____)          →  print("###")
```

**Debrief line:**
> *"Notice what happened when I typed exactly what was said. The computer is doing the same thing to you. It has no idea what you meant."*

**Cut rule:** Do the first blank only. The literal-typing moment is the lesson; the escalation is a bonus.

---

## Walkthrough Block B (28–42 min) — *Three Hashes*, students driving

**You are at the keyboard. Students give the instructions.** You type nothing they don't say.

Run the same four steps, but ask instead of tell:

1. **Read** — *"Someone read the problem out loud."*
2. **Restate** — *"In your own words, what does it want?"* Take two answers.
3. **Write** — *"What do I type first?"* Type exactly what's said.
4. **Run** — *"What do we expect? Say it before I hit run."*

**Expect these wrong turns.** They're useful — run each one rather than blocking it:

| What they say | What happens | Your one-line nudge |
|---|---|---|
| `print(###)` | Prints nothing — `#` starts a comment | *"Run it. What printed? Why nothing?"* |
| `print("#")` three times | Correct output, three lines | *"That works. Can you do it in one line?"* |
| `print(#)` | Same comment problem | *"Same thing as before. What's `#` doing?"* |

The `#`-is-a-comment collision is worth 90 seconds — it's the first time they meet a character that means something to Python.

**Answer:** `print("###")`

**Checkpoint (at 42 min):**
> *"Why did `print(###)` print nothing instead of erroring?"*
> **Answer:** `#` starts a comment, so Python ignored everything after it — there was nothing left to print.

---

## ⚡ Activity 2 — Human Compiler (42–50 min)

**Format:** Human Compiler · **Exposes:** that students read code as a whole instead of line by line, top to bottom.

**Setup line:**
> *"You are Python now. I point at a line, you tell me exactly what the machine does. Not what the program means — what that one line does."*

Put this on screen and point at each line in turn, taking a different student each time:

```python
print("Hello")
print(2 + 5)
print("2 + 5")
Print("Bye")
print(10 / 5)
```

| Line | Expected answer |
|---|---|
| 1 | Shows `Hello` |
| 2 | Works out 7, shows `7` |
| 3 | Shows the characters `2 + 5` |
| 4 | **Stops with a NameError** — `Print` doesn't exist |
| 5 | Shows `2.0` |

**The trap is line 4.** Most rooms will read past it. When someone catches it, press: *"So what happens to line 5?"*
**Answer:** it never runs. Python stops at the error.

**Debrief line:**
> *"Python reads top to bottom and stops at the first thing it can't do. That's why the error message gives you a line number — it's telling you exactly where it gave up."*

**Cut rule:** Use lines 1, 3 and 4 only. Line 4 is non-negotiable.

---

## ⚡ Activity 3 — Rapid Fire Board Race (50–57 min)

**Format:** Rapid Fire Board Race · **Exposes:** nothing new — this is a deliberate energy reset before the hour ends, and it rehearses the four-step method under mild pressure.

**Setup line:**
> *"Two volunteers at the board. Five prompts. Class judges. No laptops."*

Prompts — read one at a time, both write simultaneously:

1. Print the word `Python` → `print("Python")`
2. Print the number 12 → `print(12)`
3. Print the result of 6 times 7 → `print(6 * 7)`
4. Print the characters `6 * 7` → `print("6 * 7")`
5. Fix this: `Print("done")` → `print("done")`

Class calls the winner per prompt. Keep it fast and light.

**Debrief line:**
> *"Prompts three and four are the same characters and completely different programs. Quotes are the difference. That's the one thing from this week you cannot afford to forget."*

**Cut rule:** Prompts 3, 4 and 5 only.

---

## Exit Ticket + Homework (57–60 min)

**Exit ticket** — before anyone leaves:

> Write the four steps from the board, from memory.
> **Answer:** Read · Restate · Write · Run.

**Homework**

> *"Both Session 1 problems, submitted on the platform tonight — even if you already did them. Do them again using the four steps. And read Session 1's material if you haven't."*

| Task | Unit |
|---|---|
| Coding Practice — *Hello World*, *Three Hashes* | `81959e79-ceeb-448c-af0e-7e0e7f5447f0` |
| MCQ Practice — 56 questions | `3c0cf49d-4c57-4468-83ca-63cb7c63b1dd` |

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| "I should know how to start without thinking" | Nobody has shown them a method, so they assume competent people just *know* | Naming the four steps and running them visibly, twice |
| Errors mean you failed | School conditioning | Deliberately breaking your own code in Block A and fixing it calmly |
| Python reads the whole program at once | Reading habits from prose | Activity 2 — the `Print` on line 4 stops line 5 from ever running |
| `#` is just a symbol | No reason to know otherwise yet | Running `print(###)` and asking why nothing printed |
| Recognising correct code = being able to write it | Recognition feels like knowledge | Activity 1 — typing literally what's said exposes the gap |

---

## Instructor Notes

- **No deck for this session.** Screen share is the entire delivery. Editor open, font ≥18pt, platform logged in, before the room fills.
- **This session's job is behavioural, not conceptual.** Nothing new is taught. The goal is that students leave with a repeatable first move so they stop closing the tab. Judge it by whether attempt rates rise, not by whether anyone learned a new function.
- **Do not react to the show of hands in the hook.** If three people attempted, that's information, not a discipline problem. Reacting badly guarantees an honest answer never comes again.
- **You will be tempted to type ahead in Block B.** Don't. The whole point is that students supply every instruction. Silence while waiting is productive.
- **Pacing risk:** Block B can overrun badly if you take every wrong turn. Cap it — take at most two wrong turns, then land the answer.
- **Data note:** this session has no reading material, no classroom quiz, and no MCQ pool on the platform. Nothing to assign from it directly — homework points back at Session 1.
