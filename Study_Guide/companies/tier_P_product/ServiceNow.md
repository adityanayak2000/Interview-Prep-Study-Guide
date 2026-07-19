# ServiceNow
**Role(s):** Associate Software Engineer (ASE / IC1 / SDE-1); Software Engineer (fresher off-campus); ASE / SDE Intern (summer)
**Tier:** P
**Status:** done-v3

## Process Overview
ServiceNow India early-career SWE hiring runs through **campus drives**, **careers-portal / off-campus**, and occasional **HackerRank contests** (e.g. Women Code to Win). Primary engineering hubs: **Hyderabad** (most ASE write-ups); **Bengaluru** also appears on recent off-campus Software Engineer postings — confirm on the live requisition.

| Path | Entry | Typical flow |
|---|---|---|
| On-campus | TPO / college pool | HackerRank OA → 2 technical → hiring manager / HR (sometimes merged final) |
| Off-campus | careers.servicenow.com, contest → recruiter | Resume screen (sometimes) → OA → 2 technical (often same day) → HM / HR |
| Intern | Contest / portal | OA → 2 technical → techno-managerial |

**Timeline:** OA invite often ~1 week after apply; full loop commonly **2–4 weeks** (varies).

**M.E./M.Tech CS:** Off-campus ASE/Software Engineer listings routinely list **M.E./M.Tech/MCA** alongside B.E./B.Tech (e.g. 2023 ASE drive). Campus 2021 ASE allowed CS + select circuit branches with **CGPA ≥ 7** — PG eligibility is drive-specific; **no dedicated M.Tech interview write-ups found**; expect the same DSA + fundamentals loop with heavier resume/project depth.

> Platform-specific ServiceNow product certification is **not** required for fresh SWE roles — interviews focus on CS fundamentals, Java/JS, and projects.

## Online Assessment (OA)
- **Platform:** HackerRank (consensus across campus + off-campus reports)
- **Duration:** ~60–75 minutes (varies by drive)
- **Negative marking:** Not reported
- **Format is drive-dependent — do not assume one template.** Reported shapes include:

| Reported OA shape | Source channel |
|---|---|
| **1 coding + 10–15 MCQs** (OS, DBMS, DSA; pointer/output MCQs in some drives) | GFG campus 2020, 2021; GFG off-campus |
| **2 coding in 60 min** (platforms / pair-sum style) | GFG campus 2022 |
| **2 DSA coding** (array/string, LeetCode medium) | Off-campus + campus applicant (Roundz) |
| **3 coding** (easy → medium) | Medium ASE intern write-up |
| **Multi-skill mix:** 2 DSA + 2 REST API + 1 SQL + 1 prompt-engineering | Medium off-campus 2025 |
| **2 hard coding** (1 full + 1 partial still shortlisted in one report) | LinkedIn contest applicant |

- **Coding difficulty:** Easy → hard depending on drive; several campus reports stress **optimal solutions** for full score
- **MCQ topics (when present):** OS, DBMS, DSA, code output; occasional aptitude
- **Non-DSA sections (recent off-campus):** REST/HTTP, SQL joins/aggregation, structured prompt writing — treat invite email as binding

## Interview Rounds
1. **Technical 1 (~45–90 min)** — 1–3 DSA problems (arrays, strings, linked lists, trees, stacks/queues, parentheses/BST); dry-run + complexity; Java/JS OOP and output-tracing; LRU cache / hash collisions (reported); language follows resume/team
2. **Technical 2 (~50–70 min)** — More DSA (often 2 problems/round in recent loops); deep **resume / project** grill (schema, ER diagrams, tech-stack rationale, traffic/scaling); DB design + SQL queries; React/frontend hooks when resume is full-stack
3. **Hiring manager / HR / techno-managerial (~45–90 min)** — Mix of behavioral (teamwork, conflict, why ServiceNow), light CS (OS processes, cloud IaaS/PaaS/SaaS, SQL vs NoSQL, indexing, transactions), basic schema/design (Netflix-style DB, booking platform HLD in intern loop); puzzles/aptitude occasionally in older campus loops
4. **Separate HR culture round** (some off-campus loops) — Standard fitment after HM

**Senior / lateral (context only):** LC Discuss Staff Engineer Hyderabad reports DSA + **system design** (analytics platform ETL, web crawler) — not the default fresh ASE loop.

## Topic Weights
| DSA | OS | C/C++ | DBMS | CN | LLD | HLD | Concurrency | Aptitude |
|---|---|---|---|---|---|---|---|---|
| Very High | Med–High | Med | Med–High | Low–Med | Low–Med | Low | Low–Med | Low–Med |

*Weights reflect ASE / fresher SWE reports; team-specific frontend or Java-heavy panels shift language column toward JS/Java.*

## Recurring Patterns & Tips
- **Two technical rounds × ~2 DSA each** is the most repeated fresh-loop shape (2022–2025 reports).
- Arrays, strings, linked lists, stacks/queues, trees, sliding window / two-pointer patterns recur; know **complexity + edge cases** out loud.
- Resume depth matters: schema, scaling, deadlock/ACID, cloud basics — not just LeetCode.
- Java **and** JavaScript both appear; match the language on your resume; frontend-leaning teams may surprise you with JS-only panels.
- Recent off-campus OAs add **SQL + REST + prompt clarity** — prep beyond pure DSA.
- HM round can reject despite strong tech (communication / fit tie-breaker in multiple write-ups).
- Ask constraints before coding; interviewers often help with hints if stuck.
- Read what ServiceNow the **company/platform** does; “why ServiceNow?” appears in most final rounds.

## Related topics
- [Arrays & Strings](../../topics/DSA/Arrays_Strings.md)
- [Linked Lists](../../topics/DSA/Linked_Lists.md)
- [Trees](../../topics/DSA/Trees.md)
- [Heaps](../../topics/DSA/Heaps.md)
- [Stacks & Queues](../../topics/DSA/Stacks_Queues.md)
- [Operating Systems](../../topics/OS.md)
- [OOPs & LLD](../../topics/OOPs_LLD.md)

## Resource Panel
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- [Complete DSA Roadmap](https://drive.google.com/file/d/10e8Q1yVymwxWhz9LgcWxwrkpW9eMxRla/view)
- [Awesome LeetCode Resources](https://github.com/ashishps1/awesome-leetcode-resources)
- [Sean Prashad LeetCode Patterns](https://seanprashad.com/leetcode-patterns/)
- [donnemartin / system-design-primer](https://github.com/donnemartin/system-design-primer)
- [OOPS Boss Sheet](https://drive.google.com/file/d/1s0HeZt05eck7cuwXxQZtDiZ_NEPfZwo6/view)
- See also: [00_INDEX](../../00_INDEX.md) · [Software_Product_SDE](../../archetypes/Software_Product_SDE.md)

## Sources
- [ServiceNow ASE On-Campus 2021 (GFG)](https://www.geeksforgeeks.org/interview-experiences/servicenow-interview-experience-for-associate-software-engineer-on-campus-2021/)
- [ServiceNow ASE On-Campus 2022 (GFG)](https://www.geeksforgeeks.org/interview-experiences/service-now-interview-experience-for-associate-software-engineer-2022-on-campus/)
- [ServiceNow ASE On-Campus 2020 (GFG)](https://www.geeksforgeeks.org/interview-experiences/servicenow-interview-experience-on-campus-associate-software-engineer/)
- [ServiceNow Off-Campus ASE (GFG)](https://www.geeksforgeeks.org/interview-experiences/service-now-interview-experience-off-campus/)
- [ServiceNow Interview Experience — multi-skill OA (Medium)](https://medium.com/@prathoseraaj0312/servicenow-interview-experience-65221a917813)
- [ServiceNow ASE Intern — OA + HM design (Medium)](https://medium.com/@shashank21005/my-servicenow-interview-experience-ase-intern-016036b30cc1)
- [ServiceNow Staff Engineer — Hyderabad (LC Discuss)](https://leetcode.com/discuss/post/7272656/servicenow-staff-engineer-interview-expe-k8z4/)
- [ServiceNow Interview Questions (Glassdoor)](https://www.glassdoor.com/Interview/ServiceNow-Interview-Questions-E403326.htm)

## Search log
- Queries: `ServiceNow software engineer interview India M.Tech campus GFG`; `ServiceNow SDE online assessment LeetCode Discuss`; `ServiceNow interview Medium off campus`; `ServiceNow M.Tech M.E. associate software engineer`; `site:leetcode.com/discuss ServiceNow`; `site:glassdoor.com ServiceNow interview software engineer India`
- **Thin:** No first-person **M.Tech-only** ASE loop; LC Discuss has strong **Staff+** India posts but few entry-level ASE threads; Glassdoor India fresher detail is sparse vs GFG/Medium — Glassdoor used for general SWE question themes (Java, SQL, JS, DB joins).
