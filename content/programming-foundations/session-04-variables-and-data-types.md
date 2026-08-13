# Session 4 — Variables and Data Types

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Introduction to Python · **Prerequisite** Session 1
**Session type** Concept lecture · **Format** 50-min recalibrated, 2 ALS activities, Classroom Quiz mandatory (never cut, runs last)

**Platform units**

| Resource | Unit ID |
|---|---|
| Video + deck — Variables and Data Types | `60a0f780-6133-4e84-9c62-32a99d1ec7a0` |
| RM — Variables and Data Types | `32aa5427-e439-4305-be93-7dc294eb495b` |
| Classroom Quiz A (19 q) | `a139338d-af05-4560-9128-9f45886e7234` |
| Classroom Quiz B (46 q) | `fb61164c-45db-47a0-a09e-52d04ed450e0` |
| MCQ Practice (17 q) | `68cb7e6d-fa68-4b53-8e52-057358d83f90` |
| Coding Practice (2 q) | `6fd19a96-5db6-42a1-8a6d-e53b8b96fce6` |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define a variable as a container that stores a value, and state that the value can change. *(REMEMBERING)*
2. Name the four data types — String, Integer, Float, Boolean — and give an example of each. *(REMEMBERING)*
3. Explain what the `=` assignment operator does. *(UNDERSTANDING)*
4. Assign values to variables and identify the data type of any given value. *(APPLYING)*
5. Determine why `"123"` is a string and `123` is an integer, and convert between the two forms in code. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Projector on, deck loaded, editor open for the live-typing segments, students seated before the clock starts on anything below. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Prior Knowledge Activation (3–7 min) · ALS: Polling

**Completion check-in (~15 s, before Q1):** project or state the MCQ Practice completion number since last session. No shaming, just visibility: *"X% completion, target is 80%."*

5 questions on **Session 1**. ~45 s each, project the distribution, never name individuals.

**Q1.** What does `print("Hello")` display?
`A` `"Hello"` with quotes · `B` `Hello` without quotes · `C` `Hello` on paper · `D` Error
→ **B.** *Targets:* Quotes delimit, they don't print. *Misconception:* A means they think quotes are part of the output.

**Q2.** What does `print(4 + 3)` output?
`A` `4 + 3` · `B` `7` · `C` `"7"` · `D` `7.0`
→ **B.** *Targets:* Arithmetic without quotes. Ties directly into today's ALS Activity 1.

**Q3.** What does `print(9 / 3)` output?
`A` `3` · `B` `3.0` · `C` `3.00` · `D` `27`
→ **B.** *Targets:* Division returns a decimal. *Misconception:* A is school maths. *If >40% wrong:* worth 30 seconds — it directly sets up Float today.

**Q4.** Which of these run without error? *(MSQ — select all)*
`A` `print("Python")` · `B` `Print("Python")` · `C` `print(Python)` · `D` `print(100)`
→ **A and D.** *Targets:* Case sensitivity + quotes. *Misconception:* selecting C means they haven't grasped that bare words are treated as code.

**Q5.** Which statement is true?
`A` Quotes are optional in Python · `B` Quotes turn something into a text message · `C` Quotes make numbers bigger · `D` Quotes are only for names
→ **B.** *Targets:* The quotes rule, stated abstractly. *This is the bridge into today* — String vs Integer is the same rule wearing a different hat. Note the number; you'll reference it in Slide Block A.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

> **Set up the deck's own device.** Slide 8 is a sports **Application Form**, and that form carries the entire session — every field becomes a variable, every answer becomes a data type. Prime it here rather than introducing a competing analogy.

Draw four blank lines on the board and say:

> *"You're signing up for a sports trial. Shout out what the form asks you."*

Take answers until you have roughly: **Sport**, **Age**, **Height**, and something yes/no like *have you played before*. Write each as a label with a blank beside it.

Then:

> *"Look at what you've built. Every line has two parts — a **name** on the left that never changes, and a **value** on the right that's different for every one of you. That is a variable. And notice the answers aren't all the same kind of thing: one's a word, one's a whole number, one's got a decimal, one's just yes or no. That's a data type. Both ideas, and you invented them before I opened a slide."*

Tie back to **Q5** — *"Most of you got the quotes question right. Hold on to it — today it decides which of those kinds you're actually holding."*

---

## Slide Block A (10–19 min) — DELIVER SLIDES AS-IS

**Verified against the deck.** Slides, in order:

| # | Slide | Content |
|---|---|---|
| 1 | Welcome | Skip |
| 2 | **Recap — Hello World Program** | `print("Hello World!")` and its output |
| 3 | **Recap — Those Who Can't Understand** | "Focus more on Projects" |
| 4–7 | **Agenda** (build) | Variables *(Containers)* → Data Types *(int, float, string, boolean)* → Assignment Operator |
| 8 | **Announcement — Application Form** | Blank form: Sport, Age (yrs), Height (ft), *Did you participate anywhere before?* Yes/No |
| 9–10 | **Names and Values** | Same form filled in — Cricket, 10, 4.2, Yes — then the left column labelled **Variable Names** |
| 11 | **Variable** | "Values in the variables can be changed" — glass changing colour |
| 12 | **Data Type** | Sport: Cricket → **String** |
| 13 | **String** | Stream of characters: capitals, small letters, digits, special characters, **space** — with `"Hello World!"` and the space arrowed |
| 14 | **2 vs "2" — Mathematical Value vs Character** | `2` → Integer · `"2"` → String |
| 15–16 | **Data Type** | Yes → **Boolean**, then all four mapped at once: String · Integer · Float · Boolean |

**Beats to emphasise**

- **Slides 2–3 are a recap your warm-up poll already did.** Ten seconds total. Don't re-teach Hello World.
- **The Application Form is the spine of this session.** Every subsequent slide returns to it. If you built the form on the board in the hook, say *"this is the same form"* when slide 8 appears — the continuity does a lot of work.
- **Slide 14 is the session's central trap** and it's given its own slide. `2` versus `"2"`. Slow down, say it twice: quotes turn a number into text.
- **Slide 13:** note that a **space** counts as a character, and that digits inside quotes are still string characters. That's what makes `"423"` a string.
- **Boolean:** the deck shows it as a Yes/No tick box. Add verbally that in Python it's written `True` / `False` — **capital letter, no quotes.** The deck never shows the Python spelling, and students write `true` constantly.

**Checkpoint + Quick Match (at 19 min, ~2 min)** — 10 s silent think, then cold-call two students for the checkpoint, then run the match as a fast individual-then-reveal (compressed from a full activity — folded in here to protect the schedule):
> *Checkpoint:* **"Give me the data type of `"42"` and of `42`."* Answer: `"42"` is a String — it's in quotes. `42` is an Integer.
> *Quick match (30 s silent, then reveal):* `age = 10` → stores the number 10 · `age = "10"` → stores the text `10`, not the number · `age = ten` → NameError, `ten` isn't defined. Run the third one live so the room sees the real error — same error family as Sessions 1–2, now in a new place.

---

## ⚡ ALS Activity 1 — Silent Commit, Then Reveal: Predict the Output (19–25 min)

**ALS format:** Individual Predict → Reveal. Chosen because the whole point is catching a *confident wrong* prediction before it's corrected — group discussion would let the room average out to the right answer without anyone individually confronting being wrong.

**Setup line:**
> *"Commit to an answer before I hit run. Say it out loud or show fingers. Being wrong out loud is the fastest way to remember this."*

Take a prediction before running each:

```python
a = 10
b = 3
print(a + b)          # 1
```

```python
a = "10"
b = "3"
print(a + b)          # 2
```

```python
a = 10
b = "3"
print(a + b)          # 3
```

| # | Output | Why |
|---|---|---|
| 1 | `13` | Two integers — Python adds them |
| 2 | `103` | Two strings — Python joins them end to end |
| 3 | **TypeError** | Can't add a number to a text value |

**Snippet 2 is the moment of the session.** Most students confidently predict `13`. Let the wrong prediction happen before you run it.

**Debrief line:**
> *"Same `+` sign, three completely different behaviours — decided entirely by the type. That's why data types matter. Python isn't being difficult; it genuinely doesn't know whether you meant maths or text."*

**Cut rule:** Snippets 1 and 2 only. Snippet 2 is non-negotiable.

---

## Slide Block B (25–31 min) — DELIVER SLIDES AS-IS

**Verified against the deck.** Only two slides — this block is short, so there is room to run examples live.

| # | Slide | Content |
|---|---|---|
| 17 | **Python Syntax — Assigning Value to a Variable** | `age = 10`, with all three parts arrowed and labelled: **Variable Name** · **Assignment Operator** · **Value** |
| 18 | **Summary** | Table — Data type · Definition · Additional Examples (String = stream of characters, `"Book"`, `"423"`; Integer = …-3, -2, -1, 0, +1…) |
| 19 | Thank You | Closing |

**Beats to emphasise**

- **Use slide 17's three labels as your vocabulary** — Variable Name, Assignment Operator, Value. The deck names all three explicitly; matching its words keeps you consistent with the reading material and the quiz.
- **`=` means "put this in that box."** It is not the equals sign from maths. The deck doesn't say this — add it. It prevents a misconception that becomes expensive at conditionals.
- **Reading direction:** right side first, then into the left. `age = 10` is *"take 10, put it in age."*
- **Slide 18's summary table lists `"423"` as a string example** — point at it. It's slide 14's lesson restated.

**Checkpoint (at 31 min)** — show hands:
> *"`score = 100`. Name the three parts, using the slide's words."*
> **Answer:** `score` is the Variable Name, `=` is the Assignment Operator, `100` is the Value.

---

## ⚡ ALS Activity 2 — Silent Bug Hunt → Pair Fix: Name the Box (31–38 min)

**ALS format:** Silent Bug Hunt → Pair Fix — students watch a live-typed program run *without error* and have to individually notice something's wrong before conferring with a neighbour on the fix. Different from Activity 1's predict-before-run: here nothing is predicted in advance, the danger is that broken code looks fine until you check the output.

**Setup line:**
> *"I'm at the keyboard, you give the instructions. We're solving tonight's homework problem together — the first one only."*

Build up to the Coding Practice problem *Sum of 2495 and 789358*, but make them name things:

```python
first = 2495
second = 789358
print(first + second)
```

Ask at each step: *"What do I call this box? What goes in it? What do I print?"*

**Then the deliberate bug** — type this and run it:

```python
first = "2495"
second = "789358"
print(first + second)
```

Output: `2495789358`

> *"It ran. No error. It's completely wrong. 15 seconds, silent — look at the output and decide if it's right. Then 15 seconds with your neighbour — agree on why."*

Take the fix from a pair — remove the quotes.

**Debrief line:**
> *"That's the dangerous kind of bug. It didn't crash, it just quietly gave you nonsense. Quotes turned your maths into text-joining. Check your types."*

**Cut rule:** Skip the naming discussion, go straight to the buggy version and the fix.

---

## Classroom Quiz (38–45 min) · ALS: Individual Answer → Reveal

> 🔒 **Mandatory block — do not cut, do not shorten, do not skip under time pressure.** Runs last, right before the Exit Ticket — a cumulative check across everything taught today. If you're running behind by the time you reach it, that's what the cut rules on the Hook, both Slide Blocks, and both ALS activities are for — protect these 7 minutes first.

Every question below is run ALS-style: **individual silent answer first (poll or show of fingers), then explanation.**

5 MCQs from the platform pools. ~85 s each including the individual-answer beat.

**Q1** — `c3998e73-4e5f-4f66-9a47-aeff68b06d3e` *(Quiz A · REMEMBERING)*
In Python, what is a variable?
- A fixed value that cannot change
- A type of Python function
- ✅ **A container for storing data values**
- A Python library

> *Explanation (platform):* Variables are like containers for storing values. In Python, we use variables to hold information or data that can be used and changed throughout our program.
> **If they pick "a fixed value":** they've got it backwards — the whole point is that it changes. Worth correcting firmly; Session 5 depends on it.

**Q2** — `055d668a-2835-4f79-9294-2a3954484d14` *(Quiz B · REMEMBERING)*
What defines a float in programming?
- A whole number with no decimal places
- ✅ **A number with a decimal point**
- A textual representation of a number
- A number representing true or false

> *Explanation:* **[authored — the platform record for this question has an empty explanation field]** A float is any number written with a decimal point, such as `24.3` or `-321.86`. Whole numbers without a decimal point are integers.

**Q3** — `f823f682-4654-4851-b570-be439fe1eb73` *(Quiz B · UNDERSTANDING)*
What does the `=` operator do in `age = 30`?
- Checks if age is equal to 30
- Creates a variable named 30 and assigns it the value of age
- ✅ **Assigns the value 30 to the variable age**
- Adds 30 to the existing value of age

> *Explanation (platform):* In Python, the `=` operator is used to assign a value to a variable. In the code `age = 30`, the variable `age` acts as a container that stores the value `30`.
> **If they pick "checks if equal":** they're importing `=` from maths. Flag now that comparison uses `==` and they'll meet it in a few sessions — don't teach it today.

**Q4** — `5b57cc5a-7f51-42e8-adb1-5c9298c636d5` *(Quiz B · APPLYING)*
Is `number = "123"` assigning an integer value to `number`?
- ✅ **False**
- True

> *Explanation (platform):* The code `number = "123"` assigns a string value to the variable `number`, not an integer. The value `"123"` is enclosed in quotes, which means it is a string data type. To assign an integer value, the quotes would need to be removed: `number = 123`.
> **This is the session's core question.** If >40% say True, that's a signal to reopen Slide 14 and ALS Activity 1 at the start of Session 5.

**Q5** — `3213cc7a-3a73-468f-bdc1-cb124833c77f` *(Quiz B · ANALYZING)*
`is_completed = "True"` — which change makes it a Boolean?
- Replace `"True"` with `1`
- ✅ **Remove the quotes around `"True"`**
- Replace `"True"` with `'True'`
- No change needed

> *Explanation (platform):* In the given code, `is_completed = "True"` stores a string value because "True" is enclosed in quotes. To convert it to a boolean data type, we need to remove the quotes so it becomes `is_completed = True`.
> **If they pick `'True'`:** they think single quotes are different from double. Say it plainly — both are strings, Python treats them identically.

---

## Exit Ticket + Quiz Push (45–48 min)

**Exit ticket** (~30 s) — before anyone leaves:

> Write the data type of each: `"hello"` · `42` · `3.14` · `True` · `"42"`
> **Answers:** String · Integer · Float · Boolean · String

The last one is the one that matters. Scan for it on the way out.

**Quiz Push — start it now, not tonight (2 min):** phones/laptops out, right now, still in the room.
> *"Open MCQ Practice. Everyone, this room, right now — attempt the first 3 questions before you leave your seat. Only 17 questions this time, it's a short one."*

Circulate while they do it. Target is 80% platform attempt rate, currently ~33%.
> *"I'll show completion numbers at the start of Session 5's warm-up."*

**Remaining homework**

| Task | Unit |
|---|---|
| Coding Practice — *Sum of 2495 and 789358*, *Subtract 596 from 193856* | `6fd19a96-5db6-42a1-8a6d-e53b8b96fce6` |
| MCQ Practice — 17 questions *(started in class above — finish the rest)* | `68cb7e6d-fa68-4b53-8e52-057358d83f90` |
| RM — Variables and Data Types | `32aa5427-e439-4305-be93-7dc294eb495b` |

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| `"123"` is a number | It looks like one | ALS Activity 1 snippet 2 — `"10" + "3"` gives `103` |
| `=` means "is equal to" | Ten years of maths | Slide Block B — *"put this in that box"*, right side first |
| Single and double quotes differ | Two forms suggests two meanings | Quiz Q5 — state plainly that Python treats them identically |
| `true` works as a Boolean | Lowercase in most other contexts | Slide Block A — say the capital out loud, write it on the board |
| A variable holds one value forever | The word "assign" sounds permanent | Quiz Q1 debrief — the value changing is the entire point |
| No error means correct | Errors are the only feedback they know | ALS Activity 2's deliberate bug — runs fine, answer is nonsense |

---

## Instructor Notes

- ✅ **Verified against the real deck** (*"Copy of 1.2 Variables and Datatypes"*, ~19 slides). Slide Blocks A and B list the actual slides in order.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Every window is tighter than the original 60-min plan — use the cut rules first, the buffer last.
- **The whole session rests on one idea:** quotes decide the type. Warm-up Q5 measures it, **deck slide 14 states it**, the Slide A quick-match contrasts it, ALS Activity 1 makes it bite, ALS Activity 2 shows it failing silently, Quiz Q4 tests it. If you cut anything, keep that chain intact.
- **Two ALS activities this session, both new formats not used in Sessions 1–3:** Activity 1 is Individual Predict → Reveal (Silent Commit variant), Activity 2 is Silent Bug Hunt → Pair Fix. The original third activity (Error Message Match) is folded into a 2-minute quick-match at the end of Slide Block A's checkpoint instead of running as its own block.
- **The Classroom Quiz runs last, right before the Exit Ticket** — cumulative check, never cut, never shortened.
- **Quiz Push (in Exit Ticket block) + the warm-up completion check-in are a pair.** Target is 80% platform MCQ attempt rate, currently ~33%. Don't skip either half even under time pressure.
- **The deck's Application Form is its spine** — slides 8–16 all return to it. The hook now builds that form on the board first, so the slides land as confirmation rather than a new idea.
- **Block A is nine content slides, Block B is two.** The deck is heavily front-loaded. Expect to be ahead of schedule after slide 18 and use spare minutes on live typing, not on stretching the summary.
- ⚠️ **The deck never shows Python's `True` / `False` spelling** — Boolean appears only as a Yes/No tick box. Add it verbally, or students will write `true` all week. Quiz Q5 depends on it.
- **Don't teach `==` today.** It will come up when someone reads `=` as comparison. Acknowledge it exists, name the session it arrives in, move on.
- **Don't teach type conversion today either.** `int()` and `str()` are Session 8. Students will ask after ALS Activity 1's TypeError — tell them it's coming.
- **Quiz Q2 (`055d668a`) has an empty `answer_explanation` on the platform.** The explanation above is authored — review before use and consider filing a content fix.
- **Only 17 MCQ practice questions here** — the smallest pool in the first 15 sessions. If the practice block runs long, pull extra questions from Session 1's 56-question pool as revision.
