# PayPal (SDE)
**Role(s):** Software Engineer / SDE-1 (entry-level, sometimes labeled T22); Software Engineer 2 (SDE2); Senior Software Engineer (SDE3); Associate Software Engineer; SDE intern (conversion path)
**Tier:** P
**Status:** done-v3

> 🚪 [Start](../../START_HERE.md) · 🗺️ [Map](../../README.md) · 🏢 [Companies](../README.md) · 📚 [Library](../../library/README.md) · 🔍 [Find](../../FIND.md)

## Process Overview
PayPal India engineering hiring is **channel- and seniority-dependent**. India tech hubs include **Chennai, Bengaluru, Mumbai, and Hyderabad**. Treat the invite email as binding — loop shape differs between campus fresher drives, off-campus applications, and lateral SDE2+ pipelines.

| Channel | Typical funnel |
|---|---|
| On-campus (FTE / intern) | Resume/CGPA gate → OA → 2× technical → HR or tech+HR |
| Off-campus (0–2 YOE) | Application → OA → 1–2 technical → HR (sometimes tech-heavy) |
| Lateral SDE2+ | Recruiter screen → OA → DSA → system design → role specialization → bar raiser → HM |

**M.E./M.Tech CS:** Public write-ups rarely isolate PG candidates; eligibility commonly lists M.E./M.Tech alongside B.Tech for engineering roles. Expect the **same loop** as undergrads with deeper project/internship grilling. No separate M.Tech-only track found in sourced reports.

Official PayPal India framework (experienced hires; teams may vary): optional take-home → **Coding 1 (DSA)** → **Coding 2 (PR/code review)** → **system design** → **project retro** → **hiring manager**. SDE2+ loops in candidate reports often add explicit **bar raiser** rounds. Timeline OA→offer commonly **2–8 weeks**; gaps of 1–2 weeks between rounds are reported for senior loops.

## Online Assessment (OA)
**Format is not fixed** — platform, duration, and question mix vary by drive and role level. Do not assume one canonical OA.

- **Platform (sourced; varies):** HackerRank (most common in fresher + lateral reports), HackerEarth (on-campus SDE-1 2025), CodeSignal (some experienced loops)
- **Duration:** ~60–90 minutes typical; **2 hours** reported for at least one on-campus SDE-1 drive
- **Sections & format (reported variants — check your invite):**
  - **2–3 DSA coding only** (easy→medium; GFG recruitment overview)
  - **2 hard DSA problems** on HackerEarth (on-campus SDE-1, Jul 2025)
  - **6 MCQ + 2 coding** (medium→hard) on HackerRank (off-campus SE, Jul 2024)
  - **1 medium DSA + 10–15 MCQ** (JavaScript/web fundamentals; SDE intern campus 2023)
  - **Java/OOP MCQ + 1 coding** (older on-campus sets on HackerRank)
  - **Lateral SDE2:** 90-min HackerRank with **3 tasks** — 2 DSA + 1 Java/Spring-style API implementation (candidate report)
  - **Lateral SDE3:** 90-min OA with **2 LC-style problems** (easy + medium)
- **Negative marking:** Not consistently reported
- **Topics tested:** arrays/strings, graphs, DP, greedy, heaps/priority queues, binary search, implementation; occasional **SQL**, **Java OOP**, or **Spring** items in mixed OAs
- **Difficulty:** Campus shortlists often cite medium→hard; GFG overview says easy→medium for some fresher OAs
- **Advancement:** Strong OA performance is necessary but not always sufficient (off-campus candidate cleared HR yet received late rejection)

## Interview Rounds
### Campus / fresher (SDE-1, intern)
1. **OA** — gate (format varies; see above)
2. **Technical 1 (~45–60 min)** — resume/projects; 1–2 DSA (e.g., pair sum, Josephus, rotated sorted array); clarify + edge cases + complexity
3. **Technical 2 (~45–60 min)** — internship/agile discussion; DSA with **multiple data-structure approaches** (e.g., kth smallest via heap/BST/quickselect); OOP/DBMS follow-ups in some loops
4. **HR / tech+HR (~30–45 min)** — intro, motivation, projects; occasional extra DSA (e.g., max points on a line); SQL/OOP in some off-campus HR rounds

### Off-campus (entry-level SE)
1. **OA**
2. **Technical (~40–60 min)** — 2 DSA problems with dry runs (search in rotated array, XOR unique element)
3. **HR (~30 min)** — projects, situational/behavioral, GitHub, SQL joins, OOP pillars

### Lateral SDE2+ (Chennai/Bengaluru reports; Glassdoor Mar 2026 aligns)
1. **Recruiter screening**
2. **OA** (when issued)
3. **DSA (~45 min)** — easy→medium LC-style; project/API follow-ups; Java/Spring basics
4. **System design (~45 min)** — payment send-money flow, chat app, rate limiter, calendar app; APIs, DB schema, caching, sharding, load balancing
5. **Role specialization (~45–60 min)** — OOP in production, design patterns, **Java concurrency** (synchronized vs thread-safe DB connections), Spring DI
6. **Bar raiser (~45 min)** — scalability scenarios, behavioral alignment with company principles, managerial probes
7. **Hiring manager** — culture, team fit, motivation

### Official “Connect / Code / Design” buckets (PayPal Technology Blog)
- **Code:** optional take-home; DSA round emphasizing signals and readable code; PR-review round (tests, NPEs, readability)
- **Design:** system design whiteboard; project retrospective (“nosedive”)
- **Connect:** hiring manager dialogue; team intros

## Topic Weights
| DSA | OS | C/C++ | DBMS | CN | LLD | HLD | Concurrency | Aptitude |
|---|---|---|---|---|---|---|---|---|
| Very High | Med | Med (Java-heavy backend) | Med | Low–Med | Med (SDE2+) | Med–High (SDE2+) | Med | Low |

## Recurring Patterns & Tips
- **FinTech framing:** payment flows, idempotency/double-charge prevention, rate limiting, ledger consistency appear in design rounds.
- **Java + Spring Boot** surface often for backend India roles — know DI, testing, thread safety, not just LeetCode.
- **Communication > trick solutions:** official blog stresses clarifying questions, readable code, and trade-off discussion.
- **Resume integrity:** every project bullet gets grilled; internship/agile stories matter on campus.
- **Two prep tracks:** (A) campus/off-campus OA + 2× DSA + HR; (B) lateral OA + DSA + HLD + specialization + bar raiser.
- **Process variance:** team-specific loops differ; senior frontend reports show backend-leaning system design even for FE roles.
- **Patience on scheduling:** multi-week gaps and uneven recruiter follow-up reported on Glassdoor — not universal but common enough to plan for.

## Related topics
- [Arrays & Strings](../../topics/DSA/Arrays_Strings.md)
- [Binary Search](../../topics/DSA/Binary_Search.md)
- [Trees](../../topics/DSA/Trees.md)
- [Heaps](../../topics/DSA/Heaps.md)
- [Dynamic Programming](../../topics/DSA/Dynamic_Programming.md)
- [Operating Systems](../../topics/OS.md)
- [DBMS & SQL](../../topics/DBMS_SQL.md)
- [OOPs & LLD](../../topics/OOPs_LLD.md)
- [System Design HLD](../../topics/System_Design_HLD.md)

## Resource Panel
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- [Complete DSA Roadmap](https://drive.google.com/file/d/10e8Q1yVymwxWhz9LgcWxwrkpW9eMxRla/view)
- [Awesome LeetCode Resources](https://github.com/ashishps1/awesome-leetcode-resources)
- [Sean Prashad LeetCode Patterns](https://seanprashad.com/leetcode-patterns/)
- [donnemartin / system-design-primer](https://github.com/donnemartin/system-design-primer)
- [OOPS Boss Sheet](https://drive.google.com/file/d/1s0HeZt05eck7cuwXxQZtDiZ_NEPfZwo6/view)
- [LLD Boss Sheet](https://drive.google.com/file/d/1vG8CqGV8kGYOqTbA812-mKHKyeP1jGAQ/view)
- See also: [00_INDEX](../../00_INDEX.md) · [Software_Product_SDE](../../archetypes/Software_Product_SDE.md)

## Sources
- [PayPal Recruitment Process (GFG)](https://www.geeksforgeeks.org/interview-experiences/paypal-recruitment-process/)
- [PayPal SDE-1 On-Campus (GFG, Jul 2025)](https://www.geeksforgeeks.org/interview-experiences/paypal-interview-experience-for-sde-1-on-campus/)
- [PayPal SE Off-Campus India (GFG, Jul 2024)](https://www.geeksforgeeks.org/interview-experiences/paypal-india-interview-experience-software-engineer-off-campus/)
- [PayPal SDE Intern On-Campus 2023 (GFG)](https://www.geeksforgeeks.org/interview-experiences/paypal-interview-experience-for-sde-intern-on-campus-2023/)
- [How to Prepare for an Engineering Interview at PayPal India (PayPal Technology Blog / Medium)](https://medium.com/paypal-tech/how-to-prepare-for-an-engineering-interview-at-paypal-india-288dd90e4804)
- [PayPal Software Engineer Interview Questions (Glassdoor)](https://www.glassdoor.com/Interview/PayPal-Software-Engineer-Interview-Questions-EI_IE9848.0,6_KO7,24.htm)
- [PayPal \| Software Engineer \| SDE2 \| Chennai (LC Discuss)](https://leetcode.com/discuss/post/6068980/paypal-software-engineer-sde2-chennai-by-u6dw/)
- [PayPal Interview Experience \| SDE3 \| Chennai (LC Discuss)](https://leetcode.com/discuss/post/7374048/paypal-interview-experience-sde3-chennai-6hz4/)
- [PayPal Senior Software Engineer Frontend Interview Experience (LC Discuss)](https://leetcode.com/discuss/interview-experience/7358334/)
