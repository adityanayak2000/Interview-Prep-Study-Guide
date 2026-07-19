# Legacy content

Material that is **useful but not primary navigation**. Strategy lives under `Study_Guide/` (companies, topics, matrix, roadmaps, archetypes).

## Living online doc (source of updates)

**Canonical editable / living copy of the legacy Interview Prep content** (kept current as you revise):

- [Interview Prep — Google Doc (living)](https://docs.google.com/document/d/10mDBpsx1RuV9IgvK2yR-aXZN52mL46AJnTH5q70qTdA/edit?tab=t.0#heading=h.xdu8h5bvqhh8)

When this Doc gains new PDFs, Boss Sheets, pattern links, or section rewrites, **port the delta into this GitHub repo** (library md + selective Resource Panels / `00_INDEX`) before or as part of publishing GitBook. Do **not** treat a stale repo export as newer than the Doc. Sync rules: [`../../CONTRIBUTING.md`](../../CONTRIBUTING.md) → *Living Google Doc sync*.

**Last Agent living-Doc URL sync:** 2026-07-19 — exported Doc TXT and diffed against library markdown: almost all Doc URLs already present in `🎯 Interview Prep Resources.md` / Context; added / confirmed [notescs/notes](https://github.com/notescs/notes) on `00_INDEX` and kept constraint table in DSA Overview (already aligned). No monolith regen.

Frozen markdown snapshots in-repo (may lag the Doc):

## What is legacy vs strategy

| Kind | Role | Where |
|---|---|---|
| **Strategy** | How to prep for a company/topic; Topic Weights; process intel | `Study_Guide/companies/**`, `topics/**`, `archetypes/**` |
| **Library** | PDFs, Boss Sheets, Systems bible, pattern tables | `🎯 Interview Prep Resources.md`, `Interview_Prep_Resources_Context.md` |
| **Living Doc** | Online editable Interview Prep (updates land here first) | [Google Doc](https://docs.google.com/document/d/10mDBpsx1RuV9IgvK2yR-aXZN52mL46AJnTH5q70qTdA/edit?tab=t.0#heading=h.xdu8h5bvqhh8) |
| **Legacy archives** | LC practice pack pointers, screenshots | This folder |

## Original Interview Prep document (repo export)
- Full export: [`../../🎯 Interview Prep Resources.md`](../../🎯%20Interview%20Prep%20Resources.md)
- Structured extract: [`../../Interview_Prep_Resources_Context.md`](../../Interview_Prep_Resources_Context.md)
- **Prefer the living Google Doc** when checking “what’s new”; then update the exports above.

## Company-wise LeetCode archives (NOT OAs)
Drive folders under the doc heading **“Company Wise LC Qs / Company Wise Leetcode”** are **company-tagged LeetCode / practice archives**.

- **Do not** call them “Company OA folders” in PRs, Resource Panels, or indexes.
- Optional Resource Panel line: `[Qualcomm LC archive (legacy)](https://drive.google.com/drive/folders/…)`
- Full folder list: open the original Interview Prep md — **do not** paste 100 folders into `00_INDEX.md`.

## Screenshots (optional OA-ish)
- [2023 OA Screenshots](https://drive.google.com/drive/folders/1gwzOS1cYQEg59mUG_y3ZuIRj8tSGoN1e) — label `legacy/screenshots` only.

## How to add a new PDF / library link
1. Prefer adding the link to `Interview_Prep_Resources_Context.md` (and optionally the original Interview Prep md).
2. Expand to full `https://` (`drive/FILE_ID` → `https://drive.google.com/file/d/FILE_ID/view`).
3. If a strategy topic should surface it: add **one** line to that topic’s Resource Panel + optionally to `00_INDEX.md` **Library quick links** (not a dump).
4. Open a PR — see [`../../CONTRIBUTING.md`](../../CONTRIBUTING.md).

## How NOT to mislabel
| Wrong | Right |
|---|---|
| “Qualcomm OA folder” for §8 Drive | “Qualcomm LC archive (legacy)” or omit |
| Pasting CTC / placement tables into guides | Do not publish CTC in this repo |
| Regenerating one giant MASTER guide | One company or one topic file per PR |
