# Session 1 — Hashing

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Hashing — Hash Maps, Hash Sets, Collision Handling · **Prerequisite** Arrays, and basic time complexity / Big-O (assumed from earlier semesters)
**Session type** Concept lecture. New topic added to the Sem-3 sequence — ⚠️ **no video and no slide deck exist for this session** — see Instructor Notes. · **Format** 50-min recalibrated, 2 ALS activities

**Resources**

| Resource | Status |
|---|---|
| Source deck | None — new topic, no deck exists yet |
| Classroom Quiz | not yet available — 5-min slot reserved at end of session, add once question bank exists for this topic |
| Coding Practice | not yet available — add once problem set exists for this topic |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Explain what a hash function does and why it makes lookup close to constant-time. *(UNDERSTANDING)*
2. State the average-case and worst-case time complexity of hash map insert, search, and delete. *(REMEMBERING)*
3. Distinguish a hash map (key → value) from a hash set (keys only, no value). *(UNDERSTANDING)*
4. Use Python's `dict` / `set` to turn an O(n²) "does this exist" check into an O(n) one. *(APPLYING)*
5. Explain what a hash collision is and name chaining as one way to handle it. *(UNDERSTANDING)*
6. Trace, by hand, how a small set of keys lands in a hash table's buckets, given a simple hash function. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Diagnostic (3–7 min) · ALS: Polling

**This session is the exception.** It's the first session of a new block — Hashing through Two Sum — so the poll checks prior-semester fundamentals (arrays, linear search, Big-O), not last session's content. No wrong answers, just calibration.

Say: *"Five quick ones before we start today's topic. Nobody is graded, nobody is named. I need to know what's still solid."*

**Q1.** You have an unsorted array of 1,000,000 numbers. What's the time complexity of checking whether a specific value exists in it, using a plain loop?
`A` O(1) · `B` O(log n) · `C` O(n) · `D` O(n²)
→ **C.** *Read:* If this isn't automatic, slow down through Teaching Block A's motivation — the whole session is "can we beat this."

**Q2.** What does "O(1)" mean, in your own words?
`A` It takes exactly 1 millisecond · `B` The time doesn't grow as the input grows · `C` It only works on 1 item · `D` It's the fastest possible algorithm, always
→ **B.** *Read:* Constant time — independent of input size. This is the property today's whole topic is chasing.

**Q3.** In Python, what does `arr[3]` cost, time-wise, for a list `arr`?
`A` O(1) · `B` O(n) · `C` O(log n) · `D` Depends on what's stored
→ **A.** *Read:* Index access is O(1) — array indexing already gives constant time by *position*. Today's question is whether we can get that speed by *value* instead.

**Q4.** What's a Python `dict` used for, at a basic level — even if you haven't formally studied how it works?
`A` Storing values in order, like a list · `B` Storing key-value pairs · `C` Storing only unique numbers · `D` Not sure
→ *Read:* If most of the room picks B or has used one before, good — today formalizes and extends what they already touch. If D dominates, slow down on the very first `dict` example.

**Q5.** *(MSQ — select all that apply)* Which of these have you already used in code, even without knowing the formal name?
`A` A Python `dict` (`{}`)· `B` A Python `set` · `C` Checking `if x in some_list`· `D` None of these
→ *Read:* Tells you how much of today is "new vocabulary for something familiar" versus genuinely new.

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Put this on the board, nothing else:

```python
numbers = [ ... ]   # 1,000,000 random integers
target = 728491

if target in numbers:      # how long does this take?
    print("found it")
```

Ask: *"This list has a million numbers. To find out if 728491 is in there, in the worst case, how many numbers does Python have to check?"*

Let the answer land — up to a million, one at a time.

> *"Now imagine I told you: I can answer that same question — is it in here? — in roughly the same amount of time whether the list has ten numbers or ten million. Not by being clever about searching. By never searching at all."*

Pause.

> *"That's not a trick. It's an entire data structure built around one idea: **decide where something belongs before you ever go looking for it.** That's hashing. By the end of today you'll know exactly how, and you'll have used it to solve a real problem."*

---

## Teaching Block A (10–19 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from standard hashing fundamentals -->

**1. The core idea — a hash function turns a key into a location.**

Write on the board:

```
key  →  hash function  →  index (bucket number)
```

> *"A hash function takes anything — a number, a string, whatever — and turns it into a number. That number tells you exactly which 'bucket' to look in. No searching. You compute where it should be, and you go straight there."*

**2. A toy hash function, worked by hand.** Say: *"Real hash functions are more complex, but the idea is identical to this."*

```
hash(key) = key % 5      # 5 buckets: 0, 1, 2, 3, 4
```

Insert `12`, `7`, `23` live, one at a time, drawing 5 empty buckets on the board:

- `hash(12) = 12 % 5 = 2` → bucket 2
- `hash(7) = 7 % 5 = 2` → bucket 2 **(collision — flag it, don't resolve it yet)**
- `hash(23) = 23 % 5 = 3` → bucket 3

**3. Name the two structures.**

- **Hash set** — stores just keys. *"Is this value present, yes or no?"* Python: `set()`.
- **Hash map** — stores key → value pairs. *"What value is attached to this key?"* Python: `dict()`.

**4. The complexity table — write it and leave it up all session.**

| Operation | Average case | Worst case |
|---|---|---|
| Insert | O(1) | O(n) |
| Search | O(1) | O(n) |
| Delete | O(1) | O(n) |

> *"Average case is what you get almost always. Worst case happens when the hash function does a bad job spreading keys out — everything piles into one bucket. You don't need to engineer around that today; you need to know it exists."*

**Beats to emphasise**

- **The magic isn't searching faster — it's not searching at all.** Say this explicitly; it's the one-sentence version of the whole topic.
- **A hash set/map trades memory for speed.** You're storing extra structure (the buckets) to avoid scanning. That trade is almost always worth it.
- **`key % 5` is a real, if weak, hash function.** Don't present hashing as some unreachable black box — it's arithmetic, and a bad hash function is just one that causes too many collisions.

**Checkpoint (at 19 min)** — 10 s silent think, cold-call:
> *"Using `hash(key) = key % 5`, which bucket does 18 land in — and does it collide with anything we've already inserted?"*
> **Answer:** `18 % 5 = 3` → bucket 3, which collides with `23` (also bucket 3).

---

## ⚡ ALS Activity 1 — Guided Table Build: Trace the Hash Table (19–27 min)

**ALS format:** Guided Table Build — the class fills in a hash table by hand, one insertion at a time, cold-called student by student. Chosen right after Teaching Block A because "decide where it belongs, then go straight there" only really lands once students have physically placed a few keys themselves — watching it once on the board isn't enough.

**Setup line:**
> *"Six numbers, hash function `key % 5`, five buckets. I point, you tell me the bucket. If it collides with something already there, say so before I write it down."*

Draw 5 empty buckets (0–4) on the board.

**The keys, in insertion order:** `14, 9, 22, 4, 19, 11`

**The trace**

| Key | `key % 5` | Bucket | Collision? |
|---|---|---|---|
| 14 | 4 | 4 | No |
| 9 | 4 | 4 | **Yes — collides with 14** |
| 22 | 2 | 2 | No |
| 4 | 4 | 4 | **Yes — collides with 14, 9** |
| 19 | 4 | 4 | **Yes — collides with 14, 9, 4** |
| 11 | 1 | 1 | No |

**How it surfaces:** by the third collision in bucket 4, someone will ask "why do we keep using this hash function if it's this bad?" — that's the exact question that sets up chaining in Teaching Block B. Let the question hang, don't answer it yet.

**When it goes wrong**

| If… | Do this |
|---|---|
| A student computes the mod wrong | Have them say the division out loud: "19 divided by 5 is 3 remainder 4" |
| Nobody notices a collision | Ask directly: "is that bucket already occupied?" before moving to the next key |

**Debrief line:**
> *"Bucket 4 just took four keys. A real hash function spreads keys out far better than `% 5` — but collisions are never fully avoidable, no matter how good the function is. The question is what you do when one happens. That's next."*

**Cut rule:** Trace keys 14, 9, 22, 4 only — that's enough to show one clean insert and the first collision.

---

## Teaching Block B (27–34 min) — BOARD + LIVE TYPING

<!-- no deck exists; content built from standard hashing fundamentals -->

**1. Collision handling — chaining.** Resolve the question ALS Activity 1 left open.

> *"When two keys land in the same bucket, the simplest fix is: don't overwrite, just keep a small list at that bucket."*

Draw bucket 4 from the trace as a chain: `14 → 9 → 4 → 19`.

> *"Looking something up in that bucket now costs a little more than one step — but only among the handful of keys that collided, never the whole table. That's why average case stays close to O(1) even with collisions."*

Mention, briefly, without deriving: *"There's another approach — open addressing, where a colliding key hops to the next open bucket instead of chaining. You'll meet the name; chaining is the one to know cold."*

**2. Python's `dict` and `set` — this is hashing, already built for you.**

```python
seen = set()
seen.add(5)
seen.add(12)
print(7 in seen)      # False — O(1) lookup
print(5 in seen)      # True  — O(1) lookup
```

```python
counts = {}
counts["apple"] = 3
counts["banana"] = 1
print(counts["apple"])          # 3
print(counts.get("cherry", 0))  # 0 — safe lookup, no KeyError
```

> *"Every `in` check on a `set`, every `dict[key]` lookup — that's the bucket-and-hash-function machinery from today, running underneath, already written for you. You will almost never write your own hash function in this course. You will constantly use `dict` and `set` to get its speed."*

**3. A real problem, solved with hashing — find the first duplicate.**

> *"Given a list, find the first number that appears twice. Naive way?"*

```python
def first_duplicate_naive(nums):
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] == nums[j]:
                return nums[i]
    return None
```

> *"What's the time complexity of that?"* — **O(n²)**, nested loop. Now the hashing version:

```python
def first_duplicate(nums):
    seen = set()
    for num in nums:
        if num in seen:
            return num
        seen.add(num)
    return None
```

> *"One loop. Every check is O(1). That's O(n) total — and it's the exact same shape you'll reuse for Two Sum in a few sessions."*

**Beats to emphasise**

- **Chaining doesn't break O(1) average case** — it just means "average case" is doing real work, not a guarantee.
- **`dict.get(key, default)` avoids `KeyError`.** Flag this now; it comes up constantly.
- **The naive-vs-hashed rewrite is the pattern for the entire rest of this block.** Sliding Window, Two Sum, and the subarray-sum sessions are all some version of "turn a nested loop into one pass using a hash set or map."

**Checkpoint (at 34 min)** — show hands:
> *"`first_duplicate` uses one loop and a set. What's its time complexity, and why isn't it O(n²) like the naive version?"*
> **Answer:** O(n). Each `in` check and each `add` on the set is O(1) average case, so one pass through n elements is O(n) total — no nested loop.

---

## ⚡ ALS Activity 2 — Silent Diagnose, Named Reveal: Spot the Missing Hash (34–41 min)

**ALS format:** Silent Diagnose, Named Reveal — a naive, working-but-slow solution goes on the board; students must name *why* it's slow and *which* hash-based fix removes the nested loop, before the fix is revealed. Chosen as the closing activity because recognising "this is an O(n²) pattern that a hash set/map would fix" is the actual transferable skill — more than any single problem solved today.

**Setup line:**
> *"This code works. It's also slower than it needs to be. Don't fix it yet — first tell me exactly which line is the problem, and why."*

```python
def has_pair_with_sum(nums, target):
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] + nums[j] == target:
                return True
    return False
```

Give 90 seconds silent, then cold-call: *"What's the time complexity, and what's the one line doing the damage?"*

**The diagnosis:** O(n²) — the inner `for j in range(...)` loop. Every element is compared against every other element.

**The reveal — hash-based rewrite:**

```python
def has_pair_with_sum(nums, target):
    seen = set()
    for num in nums:
        if (target - num) in seen:
            return True
        seen.add(num)
    return False
```

> *"For each number, ask one question: have I already seen the number that would complete the pair? That's a single O(1) lookup, not a second loop."*

**When it goes wrong**

| If… | Do this |
|---|---|
| Students fix it by sorting the array first | Valid alternative (O(n log n)), but ask: "can we do better than sorting?" — steer back to O(n) with a hash set |
| Nobody spots `target - num` as the key move | Ask: "if 10 is the target and you're looking at 3, what number would complete the pair?" |
| A student says "this is basically Two Sum" | Yes — name it explicitly. This is the shape, without yet returning indices. That refinement is a future session. |

**Debrief line:**
> *"Every time you see a nested loop whose only job is 'does some other element satisfy a condition with this one,' ask first: could a hash set answer that in one pass instead?"*

**Cut rule:** Skip the silent diagnose phase and go straight to a class discussion of the naive code, then the reveal.

---

## Classroom Quiz (41–46 min) · Reserved — not yet available

No quiz bank exists yet for this topic (it's new to the Sem-3 sequence — see Resources table). This slot is reserved here, at the end of the session and right before the Exit Ticket, so the plan doesn't need restructuring once a bank exists. Until then, use it for an instructor-led review of today's toughest moment — re-run the `has_pair_with_sum` rewrite one more time, cold-calling a different student for each line — or fold the slot into Buffer and end early.

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> In one sentence: why does checking `x in some_set` cost roughly the same time whether the set has 10 items or 10 million? And what do we call it when two different keys land in the same bucket?
> **Answers:** Because a hash function computes the bucket directly from the key instead of searching for it — the lookup goes straight to the right place regardless of how much else is stored. That event is called a **collision**.

**Homework**

| Task | Note |
|---|---|
| Rewrite `first_duplicate_naive` and `has_pair_with_sum` from memory, without looking at today's board | Time yourself — both should take under 3 minutes each once the pattern is internalised |
| Given the hash function `key % 7`, hand-trace where these land: `10, 17, 3, 24, 31` | Note every collision |

Tell them: *"Every session for the next five sessions builds directly on today. If 'nested loop → hash set' isn't automatic yet, that's tonight's job."*

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Hashing means "searching, but faster" | The word "search" gets used loosely | The Hook's framing — hashing computes location, it never searches |
| A hash table never has collisions if the hash function is "good enough" | Feels like a solvable engineering problem | ALS Activity 1 — even a real trace with 6 keys collides more than once |
| `dict` and `set` are just fancy lists | Both look like containers on the surface | Teaching Block B's O(1) vs O(n²) rewrite — the speed difference is the whole point |
| Worst-case O(n) means hash maps aren't actually useful | Worst case sounds disqualifying | The complexity table — worst case is rare in practice, average case is what you design around |
| This is basically the same as Two Sum, so why have a separate session later | Both use "have I seen this before" | Teaching Block B names the connection explicitly, then defers the index-returning refinement |

---

## Instructor Notes

- **⚠️ No video and no slide deck exist for this session.** It's newly added to the Sem-3 sequence (see `sem-3-sequence.md`) — both teaching blocks above are written as board-and-live-typing sessions built from standard hashing fundamentals, not from any platform export.
- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex).
- **Two ALS activities this session:** Activity 1 is Guided Table Build (hands-on hash-table tracing), Activity 2 is Silent Diagnose → Named Reveal (recognising the O(n²)-to-hash-set pattern). Deliberately different registers — one is mechanical tracing, one is code-reading and diagnosis.
- **This is session 1 of a new 6-session block** (Hashing → Prefix Sum → Sliding Window/Two-Pointer → Longest Subarray Sum K → Largest Subarray Sum → Two Sum) that opens the Sem-3 sequence. None of these six have source decks; all six are written from general DSA knowledge.
- **The `first_duplicate` and `has_pair_with_sum` examples are deliberately not "Two Sum."** Two Sum gets its own dedicated session (#6) with index-returning and the classic interview framing. Today's examples exist to teach the *pattern* (nested loop → hash set) without pre-empting that session's content.
- **If a student already knows Two Sum by name, let them say so** — Teaching Block B explicitly acknowledges the connection rather than pretending it isn't there.
- **Protect the ALS Activity 1 trace over the checkpoint drills** if the session runs behind — physically placing keys in buckets is the one thing a lecture can't substitute for.
