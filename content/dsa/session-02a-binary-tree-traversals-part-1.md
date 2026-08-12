# Session 02a — Binary Tree Traversals (Part 1 of 2)

**Duration** 33 min · **Topic** Binary Tree Traversals — Why Traversal & the Node Template · **Prerequisite** Session 01b — Introduction to Binary Trees, Part 2 · **Session type** Concept lecture

<!-- Split note: original session-02 ran 60 min. Split at the Classroom Quiz boundary (the deck's own "Quiz Time!" slide 34 lines up closely with this halfway point). Part 1 covers the Node template and why traversal matters. Part 2 (session-02b) covers the four traversal orders and the worked dry runs. -->

**Platform units**

| Resource | Link |
|---|---|
| Video + deck — Binary Tree Traversals | https://docs.google.com/presentation/d/1Jd2OWb4FjwoWDe6efW1-Zl5ce2aEok950kLvW1FoAPY/edit |

---

## Learning Objectives

By the end of this session, students will be able to:

1. Define traversal as visiting every node of a binary tree exactly once, in a specific order, to process or print its data. *(REMEMBERING)*
2. Explain why traversal is necessary, citing Data Retrieval (checking/searching a value) and Tree Modification (locating a node to change the tree's structure) as the two motivating use cases. *(UNDERSTANDING)*
3. Trace a Node-class definition (`data`, `left`, `right`, constructor) to explain how left/right pointers physically represent the tree being traversed. *(APPLYING)* <!-- placement: inferred -->

*(The four traversal orders and their worked dry runs are covered in Part 2.)*

---

## Warm-Up Poll — Retrieval Practice on Session 01 (0–7 min)

> From this session onward, the warm-up poll is retrieval practice on the *immediately preceding* session, not a diagnostic. Today's poll checks Session 01 (Introduction to Binary Trees) terminology and tree-type recall, since today's traversal rules assume students already have a working mental model of "node," "root," and "at most two children."

Say: *"Seven questions on last session. This is the same tree vocabulary you'll need in about ten minutes — so if you're unsure, guess and we'll fix it live."*

**Q1.** What is the maximum number of children a node can have in a binary tree?
`A` 1 · `B` 2 · `C` 3 · `D` Unlimited
→ *Read:* This is the one fact every traversal rule assumes — "left" and "right," nothing else. If this isn't near 100%, restate it before Slide Block A.

**Q2.** A node with no children is called a ___.
`A` Root · `B` Parent · `C` Leaf node · `D` Ancestor

**Q3.** *(MSQ — pick 2)* Which of these are true of the root node?
`A` It's the topmost node · `B` It has no parent · `C` It always has exactly two children · `D` It's always a leaf
→ *Read:* If C gets picked, they're conflating "root" (a position) with "Full/Perfect" (a shape guarantee) — a Session 01 misconception. A 15-second correction now saves confusion later.

**Q4.** Last session flagged that two people can give different "height" values for the *same* tree. Why?
`A` One of them made an arithmetic mistake · `B` One counts nodes on the longest path, the other counts edges · `C` Height only applies to Perfect trees · `D` Height depends on which programming language is used
→ *Read:* If fewer than ~60% get this, re-state which convention this classroom uses — height/depth reasoning resurfaces constantly once we start writing traversal code.

**Q5.** A binary tree where every level is completely filled AND every leaf sits at the same level is called:
`A` Complete · `B` Perfect · `C` Full · `D` Balanced
→ *Read:* Complete vs. Perfect was the single most-missed distinction last session. If this is weak, spend 30 seconds re-drawing it: Complete only requires every level *except possibly the last* to be full.

**Q6.** A binary tree where every node has either 0 or 2 children, never exactly 1, is:
`A` Balanced · `B` Full · `C` Degenerate · `D` Skewed

**Q7.** True or false: a file system's directory tree, where a folder can contain many subfolders, is always a valid Binary Tree.
`A` True · `B` False
→ *Read:* False — ties directly into today's Node template, where every node has exactly two pointers (`left`, `right`) and nothing else. A folder with five subfolders simply can't be represented by one `Node` object the way this deck defines it.

**Running it** — poll tool, ~45 s per question, project the distribution after each. Never name individuals. Total 7 min including your reads.

---

## Hook (7–11 min)

Put this on the board, quoting the deck directly (Slide 18):

> **Why do we need traversal?**
> **PROBLEM:** To check / search the value of the node.

Draw the 7-node tree from the deck (root 1; left child 2 with children 4 and 5; right child 3 with children 6 and 7). Ask: *"I want to know if the value 60 exists somewhere in a tree like this. No rules yet — just tell me, where do YOU start looking, and in what order do you check the rest?"*

Take 2-3 different ad hoc answers — someone will say "start at the root," someone will say "check the biggest branch first," someone will improvise something inconsistent.

Then: *"You just each invented your own traversal — and none of you visited the nodes in the same order. That's a problem the moment two people need to agree on a result, or the moment you need to write code that does this the same way every single time. Part 2 gives you four traversal orders, defined precisely enough that any two programmers get the identical sequence."*

---

## Slide Block A (11–20 min) — DELIVER SLIDES AS-IS

<!-- placement: inferred slide range — Slides 4-20: What is a Traversal, the Node template (C++ then Python), Why We Need Traversal, and Importance of Traversal (Data Retrieval + Tree Modification) -->

**Beats to emphasise**

- **Traversal, precisely:** "visiting each node of the tree exactly once, in a specific order" (Slide 4) — the word "exactly once" matters as much as "specific order"; flag both.
- **The Node template is the foundation for everything today.** Each node holds one value (`data`) and two pointers (`left`, `right`); the constructor's whole job is to set the value and default both pointers to null/None so a brand-new node starts with no children (Slide 7). Build the example tree live, edge by edge, exactly as the deck does (`root`, then `root->left`, `root->right`, then the four grandchildren) rather than describing it — show the pointers connecting.
- **Show the Python version as a fast syntax comparison, not a re-teach** (Slide 16) — same three fields, same idea, `None` instead of `nullptr`. <!-- placement: inferred — decide before class which language to lead with based on this course's primary language track; treat the other as a ~1 minute comparison. -->
- **Two concrete reasons traversal matters** (Slides 19-20, 50): **Data Retrieval** — checking whether a value exists in the tree; **Tree Modification** — locating a specific node so you can change the tree's structure around it (e.g. attaching a new child). These aren't the same operation — retrieval only reads, modification changes the tree.

**Checkpoint (at 20 min)** — cold-call two students:
> *"In one sentence each — what's the difference between traversing for Data Retrieval versus traversing for Tree Modification?"*
> **Answer:** Data Retrieval just checks whether a value is present (read-only). Tree Modification uses the same kind of search to locate a node, then changes the tree — e.g. attaching a new child to it.

---

## ⚡ Activity 1 — Spot the Bug: The Missing Pointer (20–25 min)

**Format:** Spot the Bug · **Exposes:** the assumption that "the constructor obviously sets everything up right" — a real bug students will write themselves the first time they hand-build a `Node` class. <!-- placement: inferred — this specific broken snippet is instructor-authored for this activity; the deck does not contain an explicit "mistakes" bank the way Session 1's Python-intro reference deck does. It is built directly on the deck's own stated constructor behaviour (Slide 7: "Sets left and right to nullptr — no children initially"). -->

**Setup line (say this):**
> *"Same Node class as the slide, except I've broken exactly one line. Before I build the example tree with this constructor, tell me what goes wrong — and where it shows up."*

Put this on screen:

```cpp
class Node {
public:
    int data;
    Node* left;
    Node* right;
    Node(int val) {
        data = val;
        right = nullptr;
        // left was never touched
    }
};
```

**What students do:** 60 seconds silent, then hands up — no shouting the answer, describe the *symptom* first.

**How it surfaces:** If nobody spots it immediately, prompt: *"According to the slide, what should the constructor set left and right to? Read both lines back to me from the code above."* The gap becomes visible once they read it aloud.

**Answer:** `left` is never initialized, so a brand-new node's left pointer holds garbage/undefined memory instead of `nullptr` — any later check like `if (node->left == nullptr)` becomes unreliable, and building the example tree (`root->left = new Node(20)`) will still technically work by *overwriting* the garbage, but any node left as a true leaf on its left side stays broken.

**Debrief line:**
> *"The constructor's only job is to leave you with a clean, fully-defined node — value set, both pointers null. Forget one line and you don't get an error today, you get a bug that only shows up three traversals from now when you check a pointer that was never actually nullptr. Read constructors completely, not just the lines that look important."*

**Cut rule:** If running short, skip the live discussion of *why* it doesn't crash immediately and just state the fix (`left = nullptr;`) — the core lesson (constructors must set every field) still lands from the setup line alone.

---

## Classroom Quiz (25–30 min)

**Classroom Quiz** (~5 min) — 5-6 MCQs from the platform bank, run here. <!-- placement: inferred — question bank not available in source material; instructor to pull from platform. Note: the deck itself places a "Quiz Time!" marker slide at Slide 34, roughly 42% through its 81 slides — close enough to this part's own halfway point that this placement lines up with the deck's own structure, not just the course-wide convention. -->

---

## ⚡ Part 1 Wrap — Active Learning Strategy: Muddiest-Point Cards (30–33 min)

**Why this strategy here:** Part 1 is entirely setup — vocabulary and a code template — for the traversal rules in Part 2. A muddiest-point card surfaces exactly which piece of the setup (the Node template, or the retrieval-vs-modification distinction) is still shaky, *before* Part 2 assumes it's solid.

**Run it (3 minutes):**
> *"On a slip of paper or in the chat, one sentence: what's the one thing from today that's still fuzzy — the Node class, why we even need traversal, or something else? No names needed, hand it in or type it as you leave."*

Skim 5-6 responses out loud (anonymously) before dismissing, and note the most common theme — you'll open Part 2's warm-up poll with a question aimed squarely at it.

> *"Hold onto today's Node class — every traversal in the next session is just a different order of visiting `left`, `data`, `right` on this exact object. Nothing new gets added to it."*

---

## Common Misconceptions (Part 1 scope)

| Misconception | Why students hold it | Correct it live by |
|---|---|---|
| Traversal is only ever about printing/displaying values | Most introductory examples end in a printed sequence | Restating Tree Modification (Slides 50-55) as an equally valid traversal use case — locating a node in order to change the tree, not just read it |
| A constructor "obviously" initializes every field correctly just because it exists | Constructors look boilerplate and easy to skim | Activity 1 — one missing line (`left = nullptr`) is enough to break the guarantee the whole rest of the session depends on |

---

## Instructor Notes

- **This is Part 1 of a 60-minute original session, split at the Classroom Quiz boundary** — which the deck's own "Quiz Time!" slide (34) already treats as a natural pause, roughly 42% through its 81 slides.
- **The Node-class slides (5-16) show the same class in C++ then Python.** Decide before class which language to lead with based on this course's primary track; the second language is a ~1 minute "same idea, different syntax" pass, not a re-teach.
- **The Data Retrieval worked example (Slides 39-49, searching for value 60) and the Tree Modification worked example (Slides 50-55, adding a right child to node 70) both contain extracted values that don't cleanly match the template tree** (10, 20, 30, 40, 50, 60, 70) — numbers like 35, 45, 95, and 55 appear in the raw extraction with no clear origin. Treat both examples at the conceptual level only ("traversal finds the target node, then optionally modifies it") in Slide Block A, and verify the exact on-screen walkthrough against the live slides before narrating specific intermediate steps.
- **Part 2 (session-02b) picks up immediately with the DFS/BFS split** — no re-teaching of the Node template needed there, just a short retrieval warm-up.
