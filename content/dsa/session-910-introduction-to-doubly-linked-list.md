# Session 10 — Introduction to Doubly Linked List

**Duration** 50 min total — **45 min instruction + 5 min buffer** (3 min settling at the start, 2 min flex at the end) · **Topic** Doubly Linked List — Node Structure, Construction, Traversal · **Prerequisite** Session 9 — Deletion in Linked List
**Session type** Concept lecture. · **Format** 50-min recalibrated, 2 ALS activities

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Doubly Linked List - Traversal, Insertion, Deletion (intro/construction half) | https://docs.google.com/presentation/d/1CtyEsYixyAXlaQ-wZUaqsxFZx4XQF1JPPIJ18LZ9YKg/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Describe how a doubly linked list node differs from a singly linked list node — it carries both `prev` and `next`. *(UNDERSTANDING)*
2. Construct a doubly linked list from an array, correctly linking both `prev` and `next` at every step. *(APPLYING)*
3. Explain why a DLL requires two pointer updates per link instead of one. *(UNDERSTANDING)*
4. State the time and space complexity of `arrayToDLL` and compare it to `arraytoLL` from Session 7. *(ANALYZING)*
5. Identify the specific failure mode of forgetting a `prev` link while building a DLL. *(ANALYZING)*

---

## Classroom Settling (0–3 min) · Buffer — not instructional

Board cleared, editor open, students seated. Don't reclaim this time for content if your room settles faster — hold it as extra flex at the end.

---

## Warm-Up Poll — Retrieval Practice on Session 9 (3–7 min) · ALS: Polling

5 questions on **Session 9 (Deletion in Linked List)**. ~45 s each, project the distribution, never name individuals.

**Q1.** What must you check BEFORE deleting the tail of a list that might have just one node?
`A` Whether `head->next` is null · `B` Whether `head->data` equals `x` · `C` Whether `k` equals 0 · `D` Nothing — the same code always works
→ **A.**

**Q2.** What's the time complexity of deleting the head of a singly linked list?
`A` O(n) · `B` O(1) · `C` O(log n) · `D` O(k)
→ **B.**

**Q3.** When a node is unlinked from a list but not yet explicitly freed, what's true about it?
`A` It's already gone from memory · `B` It's unreachable, but may still exist in memory momentarily · `C` It becomes the new head · `D` Nothing changes
→ **B.**

**Q4.** In a chained `insertAtHead` then `deleteTail`, which node does `deleteTail` remove?
`A` Whatever was last in the *original* list · `B` Whatever is last in the list *after* the insert · `C` Always the second node · `D` It depends on the value inserted
→ **B.**

**Q5.** *(MSQ — select all that apply)* True about deletion operations on a singly linked list?
`A` Delete-head is O(1) · `B` Delete-tail requires a full traversal · `C` Delete-Kth uses the same `count == k-1` pattern as insertion · `D` All deletions are O(n) space
→ **A, B, C.**

**Running it** — poll tool, ~45 s per question. Total ~3.75 min for the 5 questions.

---

## Hook (7–10 min)

Draw a 3-node singly linked list on the board: `10 → 20 → 30 → NULL`. Point at node `20`.

> *"I'm standing at node 20. Give me the value of the node before me."*

Let the silence land — there's no way to answer without re-traversing from `head`.

> *"In everything you've built for three sessions, going backward means starting over from the front. Today's data structure gives every node a second arrow, pointing back the way it came — at the cost of one extra pointer to keep correct, every single time you build, insert into, or delete from it."*

---

## Slide Block A (10–23 min) — DELIVER SLIDES AS-IS

Covers: Doubly Linked List introduction — node structure (`prev`, `data`, `next`) → Head and Tail → C++ Node class (three-argument constructor) → Convert an Array into a DLL (`arrayToDLL`): problem statement, approach, code, complexity.

**Beats to emphasise**

- The node picture is the whole idea: **`prev` ← `data` → `next`**. Every node except the head has a real `prev`; every node except the tail has a real `next`. Both ends are `NULL` on their outward side.
- Walk `arrayToDLL`'s approach exactly as staged: create `head` from `arr[0]`, then for each remaining element create `temp`, set `temp->prev = cur` **and** `cur->next = temp`, then move `cur = temp`. Two links per step, not one — say this out loud every time.
- Complexity: **O(n) time** (one pass, same shape as `arraytoLL` from Session 7) and **O(n) space** (one new node per element) — identical complexity to the singly-linked-list version; the only thing that changed is *how much wiring* happens per node, not how many times the loop runs.
- Reuse the deck's own **Music Playlist** framing if time allows — head = first song, tail = last song, same as Session 7, now with the ability to skip back to the previous track.

**Checkpoint (at 23 min)** — cold-call one student:
> *"When you build a doubly linked list from an array, why do you need `temp->prev = cur` in addition to `cur->next = temp`?"*
> **Answer:** A DLL node needs both directions wired. `cur->next` lets you walk forward from `cur` to `temp`, but without `temp->prev = cur` there's no way to walk backward from `temp` to `cur` — skip it, and you've quietly built a singly linked list with an unused second pointer.

---

## ⚡ ALS Activity 1 — Live Coding / Dry-Run Relay: Build the DLL, Both Pointers (23–32 min)

**ALS format:** Live Coding / Dry-Run Relay — four volunteers physically become nodes at the board. Chosen right after Slide Block A because the single new failure mode a DLL introduces — wiring `next` and forgetting `prev` — only really lands once students have physically had to draw the second arrow themselves, under a rule that enforces it.

**Setup line:**
> *"Same relay you know from linked lists, one new rule. `arr = [10, 20, 30, 40]`. Four volunteers, one box each. This time, every arrow needs a partner — for every `next` arrow you draw, the `prev` arrow going the other way gets drawn immediately after, before we move to the next node."*

Volunteer 1 is `head` (`prev = NULL`). Volunteer 2 draws the `next` arrow from node 1 to node 2, and must immediately draw the `prev` arrow from node 2 back to node 1 before the class moves to volunteer 3. Continue through node 4, whose `next` is `NULL`.

**How it surfaces:** If the class rushes ahead and draws all four `next` arrows first, stop everything: *"Count the `prev` arrows on the board right now."* Let them see the gap themselves before you let them fix it — that's the entire point of the activity.

**Debrief line:**
> *"Every insertion or deletion you do on a DLL from here on has this exact shape — one `next` fix, one `prev` fix. Forget the second one, and you've built a singly linked list wearing a doubly linked list's clothes."*

**Cut rule:** Drop to 3 nodes instead of 4, but do not skip the "count the `prev` arrows" trap — that's the whole teaching point.

---

## ⚡ ALS Activity 2 — Silent Diagnose, Named Reveal: The Missing Prev Link (32–41 min)

**ALS format:** Silent Diagnose, Named Reveal — a construction function with the `prev` link silently removed goes on the board; students must predict exactly what breaks and when. Chosen as the closing activity because it stress-tests Activity 1's lesson against real code, not just a physical relay — the bug is silent, which is what makes it dangerous.

**Setup line:**
> *"This is `arrayToDLL`, except one line is missing. Nothing will crash while it *builds*. Tell me exactly what breaks, and only when you try to do what."*

```cpp
Node* arrayToDLL(int arr[], int n){
    Node* head = new Node(arr[0]);
    Node* cur = head;
    for (int i = 1; i < n; i++){
        Node* temp = new Node(arr[i]);
        cur->next = temp;
        // missing: temp->prev = cur;
        cur = temp;
    }
    return head;
}
```

Give 60 seconds silent, then cold-call: *"Walk me through what happens if I call `printForward(head)` versus `printBackward(tail)`."*

**The diagnosis:** `printForward` works perfectly — every `next` pointer is correctly wired, and forward traversal never touches `prev` at all. `printBackward`, starting from the tail, prints exactly one value (the tail's own `data`) and then hits `nullptr`, because every node's `prev` is still its default null value — the list is, silently, only a singly linked list wearing DLL clothing.

**When it goes wrong**

| If… | Do this |
|---|---|
| Students expect a crash or a build-time error | This is C++/Python — nothing checks that `prev` was ever set. The bug is purely behavioral, and only shows up the first time backward traversal is attempted. |
| Nobody predicts `printForward` still works | Ask them to trace `printForward`'s loop condition — it only ever reads `->next`, never `->prev` |

**Debrief line:**
> *"This bug builds fine, prints forward fine, and only reveals itself the first time someone tries to go backward — which might be sessions from now. That's exactly why Activity 1's 'count the prev arrows' discipline matters: catch it at construction time, not debugging time."*

**Cut rule:** Skip the silent diagnose phase, walk the missing-line trace as a class discussion, then reveal.

---

## Classroom Quiz (41–46 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here, right before the Exit Ticket. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform before class, covering DLL node structure, construction, and the two-pointer-per-link pattern. -->

---

## Exit Ticket + Homework (46–48 min)

**Exit ticket** (~1 min) — on paper before anyone leaves:

> Write the two lines that link a new node `temp` after the current node `cur` in a doubly linked list — both directions.
> **Answer:** `cur->next = temp;` and `temp->prev = cur;`

**Homework:** Re-attempt today's `arrayToDLL` dry run from memory on `arr = [5, 10, 15, 20]`, drawing both the `prev` and `next` arrows at every single step.

---

## Buffer (48–50 min) · Flex — not instructional

Unscheduled on purpose. If you land here with time on the clock, let the session end early — don't stretch content to fill it.

---

## Common Misconceptions

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Updating `next` is enough; `prev` will "just follow along" | Several sessions of singly-linked-list muscle memory, where only `next` ever mattered | ALS Activity 1's "count the `prev` arrows" trap, and ALS Activity 2's silent bug |
| A DLL takes twice as long to build as a singly linked list | More wiring feels like more asymptotic cost | Slide Block A — still O(n) time, identical loop count; only the per-step constant work changed |
| A missing `prev` link would show up immediately, as an error | Most bugs in this course so far have surfaced fast, in the same session | ALS Activity 2 — this one is silent until someone specifically traverses backward |
| A DLL gives O(1) access to the tail because "you have two pointers now" | Confusing "bidirectional traversal" with "instant access to both ends" | Flag explicitly: without a stored tail reference, reaching the tail still requires a full traversal — that's next session's problem to solve carefully |

---

## Instructor Notes

- **50-min format: 45 min instruction + 5 min buffer** (3 min settling, 2 min flex). Split out from the original 60-min "Session 40 — Doubly Linked List - Traversal, Insertion, Deletion," which covered construction, insertion, and deletion all in one session — see `sem-3-sequence.md`. Insertion and Deletion now have their own sessions (11 and 12).
- **Two ALS activities this session:** Activity 1 is the Live Coding / Dry-Run Relay (hands-on construction, both pointers), Activity 2 is Silent Diagnose → Named Reveal (a new activity, not in the original file — written to give this session's construction-only scope its own second ALS activity, since the original file's other two activities were deletion-specific and moved to Session 12).
- **This is session 10 of the Sem-3 sequence** (see `sem-3-sequence.md`) — the first of three sessions replacing the original combined DLL session. Session 11 (Insertion) and Session 12 (Deletion) both assume today's "two pointers, always" discipline is solid.
- **Activity 1's "both arrows" discipline is worth over-investing in.** Every checkpoint in Sessions 11 and 12 assumes students already flinch at a lone `next` arrow with no `prev` partner.
