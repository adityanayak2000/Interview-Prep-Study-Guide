# Cursor Session Master (public-safe)

Paste into a Cursor **Agent** chat on this repo. Full maintainer copy with private extract paths lives outside git (ask owners). This file is enough to re-run feedback, STL, architecture, living-Doc delta sync, and topic gap-fill.

**Repo:** https://github.com/adityanayak2000/Interview-Prep-Study-Guide  
**Living Doc:** https://docs.google.com/document/d/10mDBpsx1RuV9IgvK2yR-aXZN52mL46AJnTH5q70qTdA/edit  

```text
You are editing Interview-Prep-Study-Guide.

LOAD: CONTRIBUTING.md, FEEDBACK.md, prompts/AI_CONTRIBUTOR_BRIEF.md,
Study_Guide/_legacy/README.md, .cursor/rules/living-doc-sync.mdc,
.cursor/rules/study-guide-architecture.mdc (if present).

HARD RULES
- No CTC/LPA/PII. No monolith. No inventing OA.
- §8 Drive folders = "LC archive (legacy)", never "OA folder".
- Strategy deep-links library via full https://. Resource Panels 5–15 links.
- Preserve Boss Sheet 10·3·5 on every topic touched.
- Feedback = GitHub Issues + Discussions only (no Google Form).
- Commit/push only when the human authorizes (owners may push main).

ARCHITECTURE
- Strategy = Study_Guide/ | Library = root Interview Prep md files
- Status SoT = Study_Guide/companies/README.md
- Topic shape: Why → Concept → Patterns → Bank → Code → Boss → Resource Panel
- Insert company: _TEMPLATE → tier folder → status board (+ root index if needed)
- Insert library link: Context md ± emoji library ± one INDEX/Resource Panel row
- Living Doc newer than exports → port deltas only into library/INDEX panels
- Maintainer-only extracts/plans stay OUTSIDE git (local private folder)
- README / Living Doc / link hygiene: root README.md Living Doc link must open in a new tab (HTML `<a href="..." target="_blank" rel="noopener noreferrer">` — plain Markdown cannot force new tabs on GitHub)

FEATURES (do the ones the human names; default = all remaining gaps)
A) FEEDBACK.md + .github ISSUE_TEMPLATE + DISCUSSION_TEMPLATE; wire README/CONTRIBUTING
B) Expand CONTRIBUTING "Agent session map" + AI_CONTRIBUTOR_BRIEF extract→merge notes
C) Study_Guide/topics/DSA/STL/ quick-refs from
   https://github.com/adityanayak20/Striver-TUF-Plus/tree/main/STL
   (README, 00 quick, 01 containers, 02 algorithms); wire SUMMARY/INDEX/topics README;
   Samsung no-STL caveat
D) Export Living Doc TXT; diff URLs vs library; port missing high-value links only;
   stamp _legacy/README.md last sync
E) If private extracts exist locally: merge GAPS only into OS / Concurrency / Cpp /
   OOPs / CN topics (paraphrase)
F) Nav consistency sweep
G) Commit (± push) only if human said so

OS/Concurrency link bank (Resource Panels):
- https://yc-kuo.medium.com/contents-e8eedc905fa
- https://greenteapress.com/semaphores/LittleBookOfSemaphores.pdf
- https://leetcode.com/discuss/post/5873921/part-3-top-17-os-interview-questions-wit-4fiw/
- https://pages.cs.wisc.edu/~remzi/OSTEP/
- https://github.com/adityanayak20/POSIX-Threads
- https://github.com/notescs/notes

DONE: checklist A–G, files touched, Boss Sheets preserved?, sync URL delta count.
```

See also: [AI_CONTRIBUTOR_BRIEF.md](AI_CONTRIBUTOR_BRIEF.md) · [FEEDBACK.md](../FEEDBACK.md) · [CONTRIBUTING.md](../CONTRIBUTING.md)
