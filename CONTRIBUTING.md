# Contributing — Interview Prep Study Guide

Anyone can improve this repo via **GitHub Pull Request** (with or without Cursor). Optional: mirror to **GitBook Free** + Git Sync — **source of truth is GitHub markdown**.

**Repo:** https://github.com/adityanayak2000/Interview-Prep-Study-Guide  

**Who may push `main` directly:** only the repository owner **`adityanayak2000`**. Everyone else opens a PR and needs approval before merge.

---

## Architecture

**Strategy** = `Study_Guide/` (companies, topics, matrix, roadmaps, archetypes).  
**Library** = `🎯 Interview Prep Resources.md` + `Interview_Prep_Resources_Context.md` (PDFs, Boss Sheets, pattern tables, LC archives). Guides **deep-link** the library with full `https://` URLs; they do not paste entire Drive catalogs.

Compensation / campus CTC / student PII are **never** published here.

```
Interview-Prep-Study-Guide/
├── README.md                       ← human entry
├── CONTRIBUTING.md                 ← you are here
├── prompts/AI_CONTRIBUTOR_BRIEF.md ← paste prompt for LLMs
├── 🎯 Interview Prep Resources.md
├── Interview_Prep_Resources_Context.md
└── Study_Guide/                    ← strategy (GitBook sync root)
    ├── SUMMARY.md
    ├── 00_INDEX.md
    ├── companies/                  ← README = status SoT + backlog
    ├── topics/
    ├── archetypes/
    └── _legacy/README.md           ← living Google Doc + LC archive rules
```

---

## Contribute in 5 steps

1. Fork or clone the repo; create a feature branch.  
2. Read this file + the template for your change (`Study_Guide/companies/_TEMPLATE.md` for companies).  
3. Collect materials (Discuss / GFG / Drive PDF links, notes).  
4. Paste into an LLM with [`prompts/AI_CONTRIBUTOR_BRIEF.md`](prompts/AI_CONTRIBUTOR_BRIEF.md) so it places content in the right files.  
5. Open a **Pull Request** to `main`. Do not force-push or push to `main` unless you are an owner listed above.

### PR checklist
- [ ] One feature per PR (one company, one topic deepen, or one link batch)
- [ ] All new links are `[Title](https://full-url)`
- [ ] No CTC / LPA / student PII
- [ ] No invented OA formats; thin research → `insufficient` + search log
- [ ] §8 Drive folders not labeled “OA” (they are LC archives)
- [ ] Status board updated if company touched
- [ ] File under ~80–120KB
- [ ] Did **not** regenerate a monolith Master guide

---

## How links work

| From | To | Rule |
|---|---|---|
| Company file | Topics | Relative: `../../topics/OS.md` |
| Topic file | Companies | Relative into `companies/tier_*/` + archetype |
| Any strategy file | Library | Absolute `https://` from Interview Prep context §13 |
| Resource Panel | LC practice pack | Optional `[Name LC archive (legacy)](https://drive.google.com/drive/folders/…)` — **never** “OA folder” |

§8 Drive folders in Interview Prep are **company-tagged LeetCode archives**, not campus OAs. See `Study_Guide/_legacy/README.md`.

**Resource Panel size:** 5–15 curated links + “See also: `00_INDEX`”.

---

## Templates

### Company — copy `Study_Guide/companies/_TEMPLATE.md`
Required: Process, OA (honest), Rounds, Topic Weights, Related topics, Resource Panel, Sources as `[Title](https://…)`. Thin data → `Status: insufficient` + Search log. Update `Study_Guide/companies/README.md`.

### Topic — suggested section order
1. Why it matters  
2. Concept summary  
3. Patterns / drills (LC links)  
4. Question bank  
5. Code sketches  
6. **Boss Sheet** (10 · 3 · 5)  
7. **Resource Panel**

---

## Living Google Doc sync

**Living Doc:** https://docs.google.com/document/d/10mDBpsx1RuV9IgvK2yR-aXZN52mL46AJnTH5q70qTdA/edit?tab=t.0#heading=h.xdu8h5bvqhh8  

When the Doc gains new PDFs / Boss Sheets / pattern links, port deltas into the library md and (optionally) one Resource Panel / `00_INDEX` row. Do not regenerate a monolith from the Doc.

Agents: see `.cursor/rules/living-doc-sync.mdc`.

---

## GitBook / publishing

1. Prefer content changes via GitHub PR.  
2. GitBook Free → Git Sync → this repository → folder **`Study_Guide/`** (nav = `SUMMARY.md`).  
3. Do not publish CTC or maintainer-only plan files.

---

## Agent session map

Use this when an AI agent (Cursor / Claude Code / etc.) opens the repo after `git pull`.

| Layer | Path | Role |
|---|---|---|
| Strategy | `Study_Guide/` | Companies, topics, roadmaps, archetypes, GitBook `SUMMARY.md` |
| Library | `🎯 Interview Prep Resources.md`, `Interview_Prep_Resources_Context.md` | PDFs, Boss Sheets, pattern tables, LC archive pointers |
| Status SoT | `Study_Guide/companies/README.md` | done-v3 / insufficient / todo for companies |
| Feedback | [`FEEDBACK.md`](FEEDBACK.md) + `.github/ISSUE_TEMPLATE/` + Discussions | Visitor ideas & fixes (**no Google Form**) |
| Living Doc | Google Doc linked above | Often newer than frozen library exports — port **deltas only** |
| AI briefs | `prompts/AI_CONTRIBUTOR_BRIEF.md`, `prompts/CURSOR_SESSION_MASTER.md` | Paste prompts |
| Private extracts / plans | Maintainer machine only (e.g. local `ME_private_plans/`) | **Never commit or push** |

**Insert**
- Company → copy `companies/_TEMPLATE.md` → correct `tier_*` folder → update status board (+ root README index when adding to the published backlog).
- Topic deepen → edit existing `topics/*.md`; preserve **Boss Sheet 10 · 3 · 5**; Resource Panel stays 5–15 curated `https://` links.
- New topic file → also wire `topics/README.md`, `SUMMARY.md`, and usually `00_INDEX.md`.
- Library link → Context (± emoji library) + optional one INDEX / Resource Panel row — never dump Drive catalogs.
- STL day-before → `Study_Guide/topics/DSA/STL/`.

**Extract → merge (systems topics)**  
If private paraphrased extracts exist locally: read their INDEX → fill **gaps only** in `OS.md` / `Concurrency_Multithreading.md` / `Cpp_Fundamentals.md` / `OOPs_LLD.md` / `Computer_Networks.md` → do not paste Medium/LC/PDF bodies → do not commit extract files.

**Pull / push**
1. `git pull --ff-only origin main` before editing.  
2. Contributors: feature branch + PR.  
3. Only **`adityanayak2000`** pushes `main` directly.  
4. No force-push; no CTC; no monolith Master guide.

**Cursor rules:** `.cursor/rules/living-doc-sync.mdc`, `.cursor/rules/study-guide-architecture.mdc`.

---

## AI contributor brief

See [`prompts/AI_CONTRIBUTOR_BRIEF.md`](prompts/AI_CONTRIBUTOR_BRIEF.md) for cheap-model paste prompts (including “here are N links…”).  
Long Cursor runs: [`prompts/CURSOR_SESSION_MASTER.md`](prompts/CURSOR_SESSION_MASTER.md).  
Visitor feedback: [`FEEDBACK.md`](FEEDBACK.md).
