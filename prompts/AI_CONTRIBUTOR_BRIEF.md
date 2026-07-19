# AI Contributor Brief — cheap / free models

Use with Gemini Flash, GPT-4o-mini, Claude Haiku, local Llama, Cursor, etc. **No special IDE required.**

## Always load
1. [`CONTRIBUTING.md`](../CONTRIBUTING.md)
2. [`Interview_Prep_Resources_Context.md`](../Interview_Prep_Resources_Context.md) — §§8, 9, 13 (if library links)
3. [`Study_Guide/companies/_TEMPLATE.md`](../Study_Guide/companies/_TEMPLATE.md) — if company work
4. **Only** the target file path(s) named in the task

## Hard rules
- Edit only the paths the human named (plus `companies/README.md` if status changes).
- Strategy deep-links library with `https://`; never dump Drive catalogs.
- §8 folders = **LC archives (legacy)**, NOT OA.
- **No CTC / LPA / student PII.**
- No monolith Master guide.
- Sources / Resource Panel = `[Title](https://…)`.
- Thin company research → `insufficient` + search log; do not invent OA.
- Contributor opens a **PR** (do not push `main` unless owner).

---

## Paste prompt — single file task

```
LOAD: CONTRIBUTING.md + Interview_Prep_Resources_Context.md §§8–9–13 + <TARGET_FILE>.
Edit ONLY <TARGET_FILE> (and companies/README.md if status changes).
Strategy guides deep-link library with https://; never dump Drive catalogs.
§8 folders = LC archives (legacy), NOT OA. No CTC. No monolith. Sources = [Title](https://…).
Task: <ONE FEATURE>
```

---

## Paste prompt — “here are N links, put them in the right files”

```
You are contributing to https://github.com/adityanayak2000/Interview-Prep-Study-Guide

LOAD:
1) CONTRIBUTING.md
2) Study_Guide/00_INDEX.md (for library / hub placement)
3) Study_Guide/companies/_TEMPLATE.md (if any company material)
4) Any existing topic/company files that clearly match the links

RULES:
- Place each link in the best Resource Panel, INDEX curated row, or DSA Overview hubs — do not dump catalogs.
- Prefer one PR-sized change set; list every file you will edit first, then edit.
- Full https URLs only. §8 Drive folders = "LC archive (legacy)", never "OA folder".
- No CTC/LPA/student PII. No invented interview processes.
- If a company has no file yet: add a status row as todo OR write a full file only if materials support done-v3 / insufficient.

HUMAN MATERIALS (links + short notes):
1) <url or note>
2) <url or note>
…

After edits, summarize: files touched + where each link landed.
```

---

## Extract → then merge (systems topics)

When the maintainer has local paraphrased extracts (outside git):

1. **Extract phase** — write notes under a private folder; produce an INDEX: source URL → extract section → target `Study_Guide/topics/…`.  
2. **Merge phase** — edit only named topic files; fill **gaps**; preserve Boss Sheets; Resource Panel += curated links; never commit extracts.

OS / Concurrency link bank (examples):

- [YC Kuo Contents](https://yc-kuo.medium.com/contents-e8eedc905fa)  
- [Little Book of Semaphores (PDF)](https://greenteapress.com/semaphores/LittleBookOfSemaphores.pdf)  
- [LC Discuss — Top 17 OS Qs](https://leetcode.com/discuss/post/5873921/part-3-top-17-os-interview-questions-wit-4fiw/)  
- [OSTEP](https://pages.cs.wisc.edu/~remzi/OSTEP/)  
- [POSIX-Threads practice](https://github.com/adityanayak20/POSIX-Threads)  
- [notescs/notes](https://github.com/notescs/notes)

STL quick-ref (in-repo): `Study_Guide/topics/DSA/STL/` ← source [Striver-TUF-Plus STL](https://github.com/adityanayak20/Striver-TUF-Plus/tree/main/STL).

Visitor URL suggestions → route via [`FEEDBACK.md`](../FEEDBACK.md) (Issues / Discussions, no Google Form).

Long Cursor checklist: [`CURSOR_SESSION_MASTER.md`](CURSOR_SESSION_MASTER.md).

## Good tasks
- Add or deepen one company file + status board row  
- Deepen one topic Resource Panel (5–15 links)  
- Add pattern-hub URLs to DSA Overview / INDEX  
- Fix mislabeled “OA folder” → “LC archive (legacy)”  
- Add / fix STL quick-ref or feedback templates  

## Bad tasks
- “Rewrite the whole study guide”  
- “Generate MASTER_STUDY_GUIDE.md”  
- “List all company OA folders”  
- “Paste CTC / placement spreadsheet”  
- “Commit private extracts or ME_private_plans”