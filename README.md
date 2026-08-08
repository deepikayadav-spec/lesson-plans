# Lesson Plans — site

Static site of instructor lesson plans. Markdown in, static HTML out, hosted on Vercel.

```
site/
├─ content/                     ← the source of truth. Edit here.
│  ├─ programming-foundations/
│  │  ├─ course.json
│  │  ├─ session-01-….md  …  session-15-….md
│  │  ├─ practice-session-playbook.md
│  │  └─ README.md
│  ├─ dsa/          course.json only — no sessions yet
│  ├─ aptitude/     course.json only — no sessions yet
│  └─ english/      course.json only — no sessions yet
├─ build.py                     ← markdown → dist/
├─ dist/                        ← generated. Never edit by hand.
└─ vercel.json
```

---

## Build locally

```bash
cd site
python build.py
```

Writes `dist/`. To preview, serve it — opening the files directly won't work because
the pages link to `/` and `/<course>/`:

```bash
cd dist && python -m http.server 8000
# open http://localhost:8000
```

---

## Deploy to Vercel

**First time**

```bash
cd site
npx vercel          # links the project, deploys a preview
npx vercel --prod   # promotes to production
```

**After that**, connect the folder to a Git repo and Vercel rebuilds on every push.
`vercel.json` already sets `buildCommand: python3 build.py` and `outputDirectory: dist`,
so pushing a new markdown file is enough — no manual build.

`dist/` is **not** committed — Vercel regenerates it on every deploy.

> **If a Vercel build ever fails** because `python3` isn't on the build image, switch to
> committing the built output instead:
>
> 1. Delete the `"buildCommand"` line from `vercel.json`.
> 2. Delete the `dist/` line from `.gitignore`.
> 3. `python build.py && git add -A && git commit -m "build" && git push`
>
> From then on, run `python build.py` yourself before each push.

---

## Adding a course

1. Make a folder under `content/` — the folder name becomes the URL, so use a
   lowercase slug like `dsa` or `soft-skills`.
2. Add `course.json`:

   ```json
   {
     "name": "DSA",
     "subtitle": "Data structures and algorithms",
     "order": 2
   }
   ```

   `order` controls position on the home page. Lower is higher.

3. Drop in the markdown. `python build.py`. Done — the course appears on the home page
   automatically.

Courses with a `course.json` but no session files show on the home page as
**Not yet added** and get no page of their own. That's how `dsa`, `aptitude` and
`english` are set up right now.

---

## File naming

| Filename | Becomes |
|---|---|
| `session-01-anything.md` | Session 1, listed under **Sessions**, ordered by number |
| `anything-else.md` | Listed under **Guides** |
| `_anything.md` | **Ignored** — use this for internal/ops docs you don't want published |

---

## What the build reads out of a plan

The reader is generated from the markdown itself, so plans need no extra metadata —
but these conventions drive the interface:

| In the markdown | Effect |
|---|---|
| `# Session 4 — Variables and Data Types` | Page title. The `Session N —` prefix is stripped in the sidebar |
| `**Session type** Support session` | Adds the orange **SUPPORT** chip |
| The words *"no video and no slide deck exist"* | Adds the ⚠ marker, and a note in the header |
| `## Classroom Quiz (27–34 min)` | Becomes a segment in the 60-minute timeline, sized by duration |
| `## ⚡ Activity 1 — Spot the Bug (44–50 min)` | Same, but coloured as an activity |
| `[text](./session-09-relational-operators.md)` | Rewritten to an in-app link automatically |

Timeline segments are built only from `##` headings that carry a `(N–M min)` marker.
A heading without one still renders — it just doesn't appear in the strip.

---

## Notes

- **`content/` is the source of truth.** The original copies under
  `Programming Foundation/Lesson Plans/` are the drafts these were seeded from — edit
  here, not there, or the two will drift.
- Everything is inlined into each page: no CDN, no fonts, no external requests. Pages
  work offline once loaded, which matters in a classroom with unreliable wifi.
- Each course is its own page, so adding courses doesn't slow down the others.
- Deep links work: `/programming-foundations#session-13` opens Session 13, and
  `#classroom-quiz-27-34-min` jumps to a block within it.
