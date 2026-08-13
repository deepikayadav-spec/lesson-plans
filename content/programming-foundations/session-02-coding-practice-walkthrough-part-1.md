# Session 2 — Coding Practice Walkthrough | Part 1

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Introduction to Python · **Prerequisite** Session 1
**Session type** Support session — walkthrough. No classroom quiz, no reading material, **no slide deck.** · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Unit ID |
|---|---|
| Video — Coding Practice Walkthrough Part 1 | `f2a6cdec-7135-4db4-9466-d80aa26999fd` |
| *(Problems walked through belong to Session 1)* | `81959e79-ceeb-448c-af0e-7e0e7f5447f0` |

> ⚠️ **No deck exists for this session.** You are the content. Everything below is a live-typing session — laptop on the projector for almost the whole hour. Have the editor open and the font size at 18pt+ before students arrive.

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the four steps of attacking any coding problem — read, restate, write, run. *(REMEMBERING)*
2. Restate a problem statement in their own words before writing any code. *(UNDERSTANDING)*
3. Write and submit a solution on the platform without assistance. *(APPLYING)*
4. Read a Python error message and identify which line to fix. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Projector on, editor open at 18pt+, platform logged in, students seated before the clock starts on anything below. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** project or state the MCQ Practice completion number from Session 1. No shaming, just visibility: *"X% of you finished the MCQ Practice — target is 80%. If you didn't, you're doing it in the room today before you leave."*

5 questions on **Session 1**, the ones that matter for today's walkthrough. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `print(2 + 5)` output?
`A` `2 + 5` · `B` `7` · `C` `"7"` · `D` Error
→ **B.** *Targets:* Printing without quotes. *Misconception:* A means quotes-vs-no-quotes hasn't landed.

**Q2.** What does `print("2 + 5")` output?
`A` `7` · `B` `2 + 5` · `C` `"2 + 5"` · `D` Error
→ **B.** *Targets:* Printing with quotes. *Misconception:* A is the core Session 1 misconception. *If >40% wrong:* type both lines live right now, before the hook. This must be solid before they attempt problems.

**Q3.** Which of these will **fail**? *(MSQ — select all)*
`A` `print("Hi")` · `B` `Print("Hi")` · `C` `prnt("Hi")` · `D` `print(Hi)`
→ **B, C and D.** *Targets:* Possible Mistakes. *Misconception:* missing B means case-sensitivity is still not internalised.

**Q4.** `Print("Hello")` produces which error?
`A` SyntaxError · `B` NameError · `C` No error · `D` IndentationError
→ **B.** *Targets:* Error-message recognition. *Misconception:* students guess "SyntaxError" for everything. *If >40% wrong:* they aren't reading error text at all — call it out, it's the whole point of today.

**Q5.** You get an error you don't understand. First move?
`A` Delete the line and retry · `B` Read the error message and find the line number · `C` Ask a friend · `D` Restart the laptop
→ **B.** *Targets:* Debugging habit. No wrong-answer shaming here — this one sets up the session.

**Running it** — poll tool, ~45 s per question. Total ~3.5 min for the 5 questions.

**Explain-the-answer beat (~20 s):** *"A couple of those had you split — that's exactly why today is a full hour of hands-on practice, not more slides."*

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

## Walkthrough Block A (10–19 min) — *Hello World*

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

**Checkpoint (at 19 min)** — 10 s silent think, then cold-call:
> *"What's step 2, and why does it exist?"*
> **Answer:** Restate it in your own words — because if you can't say what the program should do, you can't write it.

---

## ⚡ ALS Activity 1 — Guided Construction: Fill the Blank Live (19–25 min)

**ALS format:** Cold-Call Construction — the instructor is a literal typist, students supply every token out loud one at a time. Chosen over a pair activity because the entire point is the gap between recognising code and producing it, which only shows up when one voice has to commit to an exact answer with nobody to lean on.

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

## Walkthrough Block B (25–36 min) — *Three Hashes*, students driving

**You are at the keyboard. Students give the instructions.** You type nothing they don't say.

Run the same four steps, but ask instead of tell:

1. **Read** — *"Someone read the problem out loud."*
2. **Restate** — *"In your own words, what does it want?"* Take two answers.
3. **Write** — *"What do I type first?"* Type exactly what's said.
4. **Run** — *"What do we expect? Say it before I hit run."*

**Expect these wrong turns.** They're useful — run each one rather than blocking it. Cap it at two wrong turns, then land the answer:

| What they say | What happens | Your one-line nudge |
|---|---|---|
| `print(###)` | Prints nothing — `#` starts a comment | *"Run it. What printed? Why nothing?"* |
| `print("#")` three times | Correct output, three lines | *"That works. Can you do it in one line?"* |
| `print(#)` | Same comment problem | *"Same thing as before. What's `#` doing?"* |

The `#`-is-a-comment collision is worth 90 seconds — it's the first time they meet a character that means something to Python.

**Answer:** `print("###")`

**Checkpoint (at 36 min)** — 10 s silent think, then cold-call:
> *"Why did `print(###)` print nothing instead of erroring?"*
> **Answer:** `#` starts a comment, so Python ignored everything after it — there was nothing left to print.

---

## ⚡ ALS Activity 2 — Round-Robin Trace: Human Compiler (36–44 min)

**ALS format:** Round-Robin Structured Cold-Call — a different student takes each line, in order, no pairing or discussion. Chosen instead of a repeat of Activity 1's format because the skill here is different: reading code top-to-bottom as a sequence, not constructing it token by token. A chain of individual answers, where one wrong line visibly breaks the next student's line, makes that sequencing tangible in a way pair discussion wouldn't.

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

## Exit Ticket + Quiz Push (44–48 min)

**Exit ticket** (~30 s) — before anyone leaves:

> Write the four steps from the board, from memory.
> **Answer:** Read · Restate · Write · Run.

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Whoever hasn't finished MCQ Practice — open it now, this room. Attempt at least 3 more questions before you leave your seat."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33% — starting it in the room is what closes that gap, a homework reminder alone hasn't.
> *"I'll show completion numbers at the start of Session 3's warm-up."*

**Remaining homework**

> *"Both Session 1 problems, submitted on the platform tonight — even if you already did them. Do them again using the four steps. And read Session 1's material if you haven't."*

| Task | Unit |
|---|---|
| Coding Practice — *Hello World*, *Three Hashes* | `81959e79-ceeb-448c-af0e-7e0e7f5447f0` |
| MCQ Practice — 56 questions *(started in class above — finish the rest)* | `3c0cf49d-4c57-4468-83ca-63cb7c63b1dd` |

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early. If you land here with 3+ minutes still going, and only then, run the optional Rapid Fire Board Race closer below — it's a bonus, never a scheduled block, and skipping it costs nothing.

**Optional closer — Rapid Fire Board Race** (not one of the two ALS activities; use only if the buffer allows):
Two volunteers at the board, prompts read one at a time, both write simultaneously, class calls the winner per prompt.
1. Print the result of 6 times 7 → `print(6 * 7)`
2. Print the characters `6 * 7` → `print("6 * 7")`
3. Fix this: `Print("done")` → `print("done")`
> *Debrief if you run it:* *"Prompts one and two are the same characters and completely different programs. Quotes are the difference. That's the one thing from this week you cannot afford to forget."*

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| "I should know how to start without thinking" | Nobody has shown them a method, so they assume competent people just *know* | Naming the four steps and running them visibly, twice |
| Errors mean you failed | School conditioning | Deliberately breaking your own code in Block A and fixing it calmly |
| Python reads the whole program at once | Reading habits from prose | ALS Activity 2 — the `Print` on line 4 stops line 5 from ever running |
| `#` is just a symbol | No reason to know otherwise yet | Running `print(###)` and asking why nothing printed |
| Recognising correct code = being able to write it | Recognition feels like knowledge | ALS Activity 1 — typing literally what's said exposes the gap |

---

## Instructor Notes

- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair** — one closes last session's loop, the other opens this session's. Target is 80% platform MCQ attempt rate, currently ~33%. Don't skip either half even under time pressure.
- **No deck for this session, and no classroom quiz** — this is a walkthrough/support session by design, not a concept lecture. Don't try to add a quiz block here; there's no question pool attached to it on the platform.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Screen share is the entire delivery. Editor open, font ≥18pt, platform logged in, before the room fills.
- **Two ALS activities this session, deliberately different from each other and from Session 1's:** Activity 1 is Cold-Call Construction (one voice builds the code token by token), Activity 2 is Round-Robin Structured Cold-Call (a chain of individual line-reads). Neither is Think-Pair-Share or a poll — pick the format the content actually needs.
- **This session's job is behavioural, not conceptual.** Nothing new is taught. The goal is that students leave with a repeatable first move so they stop closing the tab. Judge it by whether attempt rates rise, not by whether anyone learned a new function.
- **Do not react to the show of hands in the hook.** If three people attempted, that's information, not a discipline problem. Reacting badly guarantees an honest answer never comes again.
- **You will be tempted to type ahead in Block B.** Don't. The whole point is that students supply every instruction. Silence while waiting is productive.
- **Pacing risk:** Block B can overrun badly if you take every wrong turn. Cap it at two wrong turns, then land the answer — the window is 11 minutes, not 14, in this format.
- **The original plan had a third activity (Rapid Fire Board Race).** It's kept as an optional buffer-only closer at the very end, not a scheduled block — the 50-min budget only has room for two ALS activities, and Fill-the-Blank/Human Compiler carry more unique diagnostic value than the board race does.
- **Data note:** this session has no reading material, no classroom quiz, and no MCQ pool of its own on the platform. Nothing to assign from it directly — homework points back at Session 1.
