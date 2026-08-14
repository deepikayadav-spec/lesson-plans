# Session 16 — Length of Cycle In Linked List

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Linked List — Length of Cycle · **Prerequisite** Session 15 — Cycle Detection
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Length of Cycle | https://docs.google.com/presentation/d/1WZCBJX5XX5Cheq0vAV4cG5_HrRiU-Kq_KeXk26opBuI/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the "length of cycle" problem and explain how it differs from Session 15's yes/no cycle-detection problem. *(REMEMBERING)*
2. Explain how the brute-force map approach recovers cycle length from `currentIndex − storedIndex`. *(UNDERSTANDING)*
3. Dry-run the Floyd's-based optimal approach, including the second phase where `slow` counts its way back to the meeting point. *(APPLYING)*
4. Compare the time/space complexity of the brute-force map approach (O(N log N) / O(N)) against the optimal approach (O(N + cycle length) / O(1)), and explain why the brute-force cost changed from Session 15's O(N). *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 15 (3–7 min) · ALS: Polling

5 questions on **Session 15 (Cycle Detection)**. ~45 s each, project the distribution, never name individuals.

**Q1.** In Session 15's brute-force approach, what data structure tracked visited nodes?
`A` Array · `B` A set (hash-based) · `C` Stack · `D` Queue
→ **B.** *Read:* Today's session swaps this set for a map — that swap is the whole point of Slide Block A.

**Q2.** What was the time complexity of Session 15's brute-force approach?
`A` O(1) · `B` O(log n) · `C` O(n) · `D` O(n²)
→ **C.**

**Q3.** In Floyd's approach, how many steps do `slow` and `fast` take per move, respectively?
`A` 1 and 2 · `B` 2 and 1 · `C` 1 and 3 · `D` Equal steps
→ **A.**

**Q4.** What's the space complexity of the optimal (Floyd's) cycle detection approach?
`A` O(n) · `B` O(1) · `C` O(log n) · `D` O(n²)
→ **B.** *Read:* This is the number that matters most today — the optimal approach for cycle *length* keeps this exact O(1), while the brute force does not.

**Q5.** *(MSQ — select all that apply)* True about Floyd's cycle detection?
`A` The gap between slow and fast shrinks by exactly 1 per iteration inside the cycle · `B` It needs to know where the cycle starts in advance · `C` `fast != null && fast->next != null` guards against a crash · `D` It's O(1) space
→ **A, C, D.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Put yesterday's cycle example back on screen: the list `5 → 7 → 4 → 9 → 2 → 3 → 1 → 9` looping back, cycle answer = `True`.

> *"Yesterday you answered one question about this list: does it loop? Today I'm asking a harder one: if it loops, exactly how many nodes are in the loop?"*

Ask: *"You already have working code from yesterday that finds the loop. Shout out — how would you change it to also count the loop's length?"* Take 2–3 guesses (expect "count from where it repeats" or "keep going until you're back where you started" — both are the seeds of today's two approaches). Don't confirm or correct: *"Hold that thought — we're about to build exactly that."*

---

## Slide Block A (10–20 min) — DELIVER SLIDES AS-IS

Covers: Problem Statement → Brute-Force Approach → Dry Run (map of node→index) → Pseudocode → Complexity Analysis → C++ Code.

**Beats to emphasise**

- **Reframe yesterday's set as today's map.** Yesterday you only needed a yes/no answer ("have I seen this node?") so a *set* was enough. Today you need *when* you saw it, so the set becomes a **map from node to its index** in the traversal.
- **The entire insight is one subtraction.** When a node is found already in the map, `cycleLength = currentIndex − storedIndex`. Walk the dry run's final slide (`8 − 2 = 6`) slowly — this is the one line students must be able to reproduce from memory.
- **Complexity changed, and that's deliberate.** The deck states time complexity as `O(N log N)`, not `O(N)` — because this approach uses an (ordered) `map`, where insert/find cost `O(log N)` each, unlike Session 15's `unordered_set` at `O(1)` average. Say this contrast out loud; it is the most commonly missed distinction in the whole session.

**Quick contrast beat (~1 min):** *"Both approaches say 'store what you've seen, check before adding.' So why is today's O(N log N) and yesterday's O(N)?"* Take one answer: *"Same pattern, different container — `map` is tree-based (O(log N) per operation), `unordered_set`/`unordered_map` is hash-based (O(1) average). Check the container name, not just what it's used for — `map` and `unordered_map` are not interchangeable in complexity, even though they read almost the same."*

**Checkpoint (at 20 min)** — cold-call two students:
> *"Why is cycle length `currentIndex − storedIndex`, and not just `currentIndex`?"*
> **Answer:** `currentIndex` counts every node visited from the head, including the straight-line part before the loop starts. `storedIndex` marks exactly where the loop begins. Subtracting the two removes that straight-line prefix and leaves only the loop itself.

---

## ⚡ ALS Activity 1 — Live Coding / Dry-Run Relay: Be the Map (20–27 min)

**ALS format:** Live Coding / Dry-Run Relay — exposes confusing "index" (a position count) with "node identity," and forgetting that the map is checked *before* it is updated, not after. Chosen right after Slide Block A because the subtraction insight only becomes concrete once students have physically tracked their own indices.

**Setup line:**
> *"Eight of you, up front, in a line. You are nodes 5, 7, 4, 9, 2, 3, 6, 8 — in that order. Node 8 secretly points back to whichever of you is holding 4. I'll tap each of you in turn. When tapped, say three things out loud: your value, your index, and whether you're already 'in the map.'"*

Line up in order (index 0–7, node `8` pointing back to the student holding `4`, index 2). Tap student 1 through student 8 in order. Each says: *"I'm [value], index [i], not in the map → add me."* When you reach a 9th tap — routed back to the student holding `4` — that student says: *"I'm 4, and I'm already in the map at index 2!"*

**How it surfaces:** Two common slips — (1) a student announces the wrong index because they start counting from 1, not 0; (2) when you tap back to node `4`, the class jumps straight to "cycle length is 8" instead of subtracting. Let the class sit with the wrong answer for a beat, then ask: *"8 nodes have been visited total — is the loop 8 nodes long?"* and point back at the physical line — there are clearly only 6 people between the two "4" taps.

**Debrief line:**
> *"The map never told you the length directly — it only ever told you 'have I been here, and when.' The subtraction is where the real answer lives."*

**Cut rule:** Skip standing everyone up — do it as call-and-response from seats using the slide's own numbers, and jump straight to the final subtraction (`8 − 2 = 6`).

---

## Slide Block B (27–35 min) — DELIVER SLIDES AS-IS

Covers: Optimal Approach (Floyd's, two phases) → Dry Run → Pseudocode → Complexity Analysis → C++ Code.

**Beats to emphasise**

- **Phase 1 is exactly Session 15's algorithm.** Slow moves 1 step, fast moves 2; if they meet, a cycle exists. Don't re-teach this from scratch — name it as "the part you already know."
- **Phase 2 is new: counting back to the meeting point.** Once `slow == fast`, move `slow` one more step, set `count = 1`, then keep moving `slow` alone until it meets `fast` again — that count is the cycle length. Genuinely different from the brute force: no map, just pointers.
- **No extra data structure at all.** Zero sets, zero maps — hence **O(1) space**, a sharp contrast with the brute force's O(N). Time is **O(N + cycle length)**: one pass to find the meeting point, plus at most one more lap around the cycle to count it.

**Checkpoint (at 35 min)** — show hands:
> *"In the pseudocode, right after `slow == fast` is detected, we set `count = 1` — not `count = 0`. Who thinks `count` should start at `0` instead?"*
> **Answer:** `count = 1`, because the very next line already moves `slow` forward once *before* the counting loop starts. That first move already used up one step, so `count` must reflect it — starting at `0` would undercount by exactly one.

---

## ⚡ ALS Activity 2 — Spot the Bug: The Missing First Step (35–41 min)

**ALS format:** Spot the Bug — exposes the off-by-one error of skipping the "move slow once, set count = 1" step before the counting loop begins. Chosen as the closing activity because it's the exact bug the checkpoint just flagged, now stress-tested against real code.

**Setup line:**
> *"Here's the real pseudocode next to a version I wrote that looks almost identical. One of them is broken. Find it, and tell me exactly what number the broken one returns for our example — not just 'it's wrong.'"*

```
// Correct (from the deck)
if (slow == fast) {
    slow = slow->next
    count = 1
    while (slow != fast) {
        slow = slow->next
        count++
    }
    return count
}
```

```
// Buggy version
if (slow == fast) {
    count = 0
    while (slow != fast) {
        slow = slow->next
        count++
    }
    return count
}
```

60 seconds silent, then hands up. Someone identifies the missing `slow = slow->next` before the loop; push for the actual returned value.

**How it surfaces:** Most students correctly spot "something's missing" but guess the buggy version returns a slightly-wrong number like 5. Walk it through: at the moment `slow == fast` is true, the `while (slow != fast)` condition is immediately false — the loop body never runs, and the function returns `0` on the spot, for every single cycle, regardless of its real length.

**Debrief line:**
> *"Any loop that says 'count until you're back where you started' needs one deliberate step taken before counting begins — otherwise you're already 'back where you started' and the loop never runs. Zero steps counted, zero returned. Same shape of bug you'll meet in for-loops all course."*

**Cut rule:** Skip the silent-think time and just ask the question aloud, taking the first raised hand.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering the subtraction insight, the map-vs-set complexity contrast, and the count-starts-at-1 off-by-one. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — before anyone leaves:

> In your own words: what does `currentIndex − storedIndex` actually measure? And separately — in the optimal approach, why does `count` start at `1` rather than `0`?
> **Answers:** The subtraction measures the number of nodes between the first time you saw a repeated node and the second time — i.e., the length of the loop. `count` starts at `1` because the first step away from the meeting point has already been taken before the counting loop begins.

Scan responses on the way out — if the subtraction answer is weak across the room, open Session 17 with a 60-second recap before moving on.

**Homework:** Re-attempt both dry runs (brute-force map, and Floyd's meet-then-count) from memory.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Cycle length = `currentIndex` alone | The index feels like "the answer" since it's the last number computed | ALS Activity 1's physical relay — pointing out only 6 people separate the two "node 4" taps, not 8 |
| Map-based tracking is the same speed as set-based tracking | Both "sound like" hash lookups | Slide Block A's quick contrast beat, naming O(log N) vs O(1) explicitly |
| The counting loop can start at `count = 0` | It's the default they reach for when initialising any counter | ALS Activity 2's Spot the Bug — showing the buggy version returns `0` for every cycle, not just this one |
| Cycle detection (Session 15) and cycle length (this session) are "basically the same algorithm" | Both use slow/fast pointers and both involve a meeting point | Slide Block B's explicit two-phase framing: Phase 1 is identical to Session 15, Phase 2 is new |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Converted from the original 45-min/3-activity version — see below for what changed.
- **Two ALS activities this session:** Activity 1 is the Live Coding / Dry-Run Relay ("Be the Map"), Activity 2 is Spot the Bug (the missing first step). The original third activity (Predict the Output: Map vs. Set) is folded into a 1-minute quick beat inside Slide Block A instead of running as its own block.
- **The Classroom Quiz now runs last, right before the Exit Ticket** — moved from its original mid-session position (after Activity 1) to match the site-wide convention. No fixed question set exists in the source material; pull 5-6 from the platform bank.
- **This is session 16 of the Sem-3 sequence** (see `sem-3-sequence.md`).
- **Draw the 8-node list with its loop-back before class starts.** Both the brute-force and optimal dry runs reuse the same shape (`5,7,4,9,2,3,6,8` with `8 → 4`) — having it on the board already saves real time in ALS Activity 1.
- **Do not re-derive Floyd's from scratch in Slide Block B.** Session 15 already built the "why do slow and fast eventually meet" intuition — spend that time on Phase 2 (the counting step) instead, since it's genuinely new material.
- **The map-vs-set complexity contrast (Slide Block A's quick beat) is easy to rush past because it feels like a footnote — it isn't.** It's the source of Session 15/16's whole "check the container name" lesson.
