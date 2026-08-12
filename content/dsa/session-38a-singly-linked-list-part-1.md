# Session 38a — Singly Linked List (Part 1 of 2)

**Duration** 32 min · **Topic** Linked List — Why It Exists & Node Structure · **Prerequisite** Arrays (fixed size, contiguous storage, indexing) · **Session type** Concept lecture

<!-- Split note: original session-38 ran 60 min. Split right after the Classroom Quiz. Part 1 covers why linked lists exist, node structure, the three list types (named, not built), and the real-world playlist framing. Part 2 (session-38b) covers the four practice-problem algorithms: construct-from-array, print, length, and search. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Singly Linked List | https://docs.google.com/presentation/d/1MFFp2bxzh6l6-4LyxaEP2mdk3HiEy2fnB5rPU40ioRg/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. State the two drawbacks of arrays — fixed size and the contiguous-memory requirement — that motivate linked lists. *(REMEMBERING)*
2. Explain what a node is and how `data` + `next` together form a singly linked list. *(UNDERSTANDING)*
3. Differentiate singly, doubly, and circular linked lists by how their `next`/`prev` pointers are wired. *(ANALYZING)* <!-- placement: inferred from Key Takeaways slide 60 -->

*(Constructing a list from an array, and the print/length/search algorithms, are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval on Session 37: Bitwise XOR For a Given Range (0–7 min)

Say: *"Eight quick ones on last session's XOR problem before we move to something completely different. No penalty, just show me what stuck."*

**Q1.** What did `XOR(5, 6, 7, 8, 9, 10)` evaluate to in last session's dry run?
`A` 0 · `B` 11 · `C` 15 · `D` 6

**Q2.** What was the time complexity of the brute-force approach (loop, XOR-ing every number from `left` to `right`)?
`A` O(1) · `B` O(log n) · `C` O(right − left) · `D` O(right × left)

**Q3.** What was the space complexity of BOTH the brute-force and the optimal approach?
`A` O(n) · `B` O(1) · `C` O(log n) · `D` O(right − left)
→ *Read:* If a chunk of the class flips this to O(n), they're confusing "the loop runs n times" with "the loop uses n space." Point out: only the accumulator `ans` and the loop counter exist — nothing grows with the range.

**Q4.** In the optimal approach's helper, if `n % 4 == 2`, what does `xorOnetoN(n)` return?
`A` 0 · `B` 1 · `C` n · `D` n + 1

**Q5.** *(MSQ — select all that are TRUE about `xorOnetoN(n)`)*
`A` returns `n` when `n % 4 == 0` · `B` returns `1` when `n % 4 == 1` · `C` returns `0` when `n % 4 == 2` · `D` returns `0` when `n % 4 == 3`

**Q6.** The full optimal solution was `xorRange(left, right) = ?`
`A` `xorOnetoN(left) ^ xorOnetoN(right)` · `B` `xorOnetoN(right) ^ xorOnetoN(left - 1)` · `C` `xorOnetoN(right - left)` · `D` `xorOnetoN(right) + xorOnetoN(left)`
→ *Read:* If fewer than ~70% get this, that's the whole optimal approach not landing — it's the "compute cumulative-from-1, then cancel out the part you don't want" trick, which recurs constantly in DSA. Worth 30 seconds re-deriving on the board before you start today's new topic.

**Q7.** What was the time complexity of the OPTIMAL approach?
`A` O(right − left) · `B` O(log n) · `C` O(1) · `D` O(n)

**Q8.** True or False: the optimal approach avoids looping over the range entirely.
`A` True · `B` False

**Running it** — poll tool, ~50 s per question, project the distribution after each. Total 7 min including your reads.

---

## Hook (7–11 min)

Draw a 5-slot array on the board, boxes touching edge to edge, labelled `arr[0]` through `arr[4]`, with memory addresses underneath (`1024, 1028, 1032...` — same numbers as the deck).

Ask: *"I want to add a 6th element. Show of hands — does it just slide in next door?"*

Erase the "next door" space to show it's already someone else's memory. Then: *"This is the array's whole problem: fixed size, and it needs one unbroken block of memory. Today's data structure fixes both — by giving up the one thing arrays had for free: neighbours who are actually next to each other."*

---

## Slide Block A (11–20 min) — DELIVER SLIDES AS-IS

Covers: Drawbacks of Arrays (fixed size, contiguous memory) → Introduction to Linked List → Node structure (data + pointer) → Non-Contiguous Memory Allocation → Types of Linked List (singly, doubly, circular) → Head & Tail → Practical Example (Music Playlist) → Node class in C++ and Python.

**Beats to emphasise**

- **Fixed size vs. dynamic size** is the entire motivation — don't rush past the two array-drawback slides, they're the "why" for everything that follows.
- **Non-contiguous memory** (slide 11): nodes can live anywhere in memory; only the pointers wire them together. Point at the diagram's scattered addresses — this is the direct fix for the array's second drawback from the Hook.
- On **Types of Linked List**: the one differentiator that matters for exam-style questions is what the `next` (and `prev`, for doubly) pointers do at the two ends. Singly = last node's `next` is null. Doubly = both ends null, two-way pointers. Circular = last node points back to the first, no null anywhere.
- **Head and Tail** are structural terms, not data terms — head is "the node you start from," tail is "the node with nothing after it." Reinforce with the Music Playlist example (first song to play = head, last song = tail).
- Show both the **C++ Node class** (with its multiple constructors) and the **Python Node class** side by side — Python's `self.next = address` is the same idea with less ceremony.

**Checkpoint (at 20 min)** — cold-call one student:
> *"Give me one sentence on why a linked list doesn't need contiguous memory the way an array does."*
> **Answer:** Because each node only needs to know the *address* of the next node — the nodes themselves can live anywhere in memory, wired together by pointers instead of by sitting side by side.

---

## ⚡ Activity 1 — Real-World Callout (20–24 min)

**Format:** Real-World Callout · **Exposes:** that "dynamic size" and "non-contiguous memory" feel abstract until tied to something students already use — the deck's own Music Playlist example.

**Setup line (say this):**
> *"Think of the last playlist you added a song to, or removed a song from, on your phone. Shout out: roughly how many songs was it, and did you ever have to tell the app in advance how many songs you'd add?"*

**What students do:** Call out playlist sizes and app names (Spotify, YouTube Music, etc.). Quick tally on the board.

**How to handle it:** If someone insists "the app probably just uses an array, it's fine" — push once: *"Every single time you add one song, does the app rebuild the entire array from scratch?"* Let them land on why that doesn't scale — that's the Drawbacks-of-Arrays slide, now with a face on it.

**Debrief line:**
> *"That's exactly the linked-list use case from the slides — the playlist's head is the first song, the tail is the last, and adding a song is just wiring one more node. No resizing, no shifting, no wasted contiguous block sitting empty just in case."*

**Cut rule:** If running short, skip the tally, take 2 shout-outs, and go straight to the debrief line.

---

## Classroom Quiz (24–29 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Physical Pointer Recap (29–32 min)

**Why this strategy here:** the entire session hinges on students seeing pointers as physical wiring, not abstract syntax. A quick physical recap — arms as pointers — locks in "head is fixed, next is the only connection" before Part 2 asks them to trace three algorithms built on that exact mental model.

**Run it (3 minutes):**
> *"Three volunteers, arm's-length apart. Volunteer 1, point at Volunteer 2 — that's your `next`. Volunteer 2, point at Volunteer 3. Volunteer 3, point at nothing — that's `null`. Rest of class: who is `head`? Who is `tail`? What's the ONE thing that would change if I asked Volunteer 1 to insert a new person before themselves?"*

Let the class answer (head changes; nobody else moves).

> *"That's the whole picture. Part 2 turns this into four real algorithms — building this chain from an array, then walking it three different ways."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| A linked list's nodes sit next to each other in memory, like an array | The diagrams draw nodes left-to-right in a row | Slide 11's scattered-address diagram, reinforced in the Hook by erasing the array's "next door" slot |
| Traversal in a singly linked list can go backward if needed | Students haven't yet seen a doubly linked list to contrast against | Pointing out there is no `prev` field in the C++/Python Node class shown this session — only `next` exists |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split right after the Classroom Quiz.**
- **Pacing risk:** Slide Block A has six sub-topics (drawbacks, intro, types, head/tail, real-world, node class) in 9 minutes — don't let "Types of Linked List" balloon; doubly and circular get one sentence each, they're previewed here and taught properly in later sessions.
- **Have the head/cur/temp vocabulary ready before Part 2's Activity 2** — Part 2 assumes today's node/pointer mental model is already solid.
