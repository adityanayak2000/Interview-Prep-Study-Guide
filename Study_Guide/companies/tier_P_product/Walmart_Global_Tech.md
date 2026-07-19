# Walmart Global Tech (SDE)
**Role(s):** Software Development Engineer (SDE / FTE); SDE intern pipelines with possible FTE conversion; lateral SDE-2 (IN2/IN3) off-campus/referral tracks are separate from fresher campus loops
**Tier:** P
**Status:** done-v3

> 🚪 [Start](../../START_HERE.md) · 🗺️ [Map](../../README.md) · 🏢 [Companies](../README.md) · 📚 [Library](../../library/README.md) · 🔍 [Find](../../FIND.md)

## Process Overview
Walmart Global Tech India (WGT; Bengaluru / Chennai) hires SDEs through **campus placement**, **contest/diversity drives** (e.g. CodeHers), and **off-campus** (referrals, careers portal). Loop shape varies by batch and channel — treat the invite email as binding.

| Channel | Typical funnel |
|---|---|
| On-campus | Resume / CGPA gate → OA → 2× technical (Zoom) → hiring manager / HR |
| Contest / special drive | MCQ quiz → coding challenge → same-day 2× technical → managerial |
| Off-campus / referral | Recruiter screen (sometimes) → OA → 2× technical → hiring manager (+ HR debrief) |

**M.E./M.Tech CS:** Eligible in published campus/contest drives alongside B.E./B.Tech; few write-ups isolate PG candidates — expect the **same OA + interview loop** with heavier resume/project depth. Outcomes may split FTE vs intern-with-conversion in the same cohort.

Timeline OA→offer commonly **days to ~3 weeks**; debrief panels can delay HR closure (Glassdoor forum reports).

## Online Assessment (OA)
- **Platform (sourced; varies — check invite):** **HackerEarth** (campus 2021, GFG recruitment overview, March 2024 college hiring); **HirePro** (recent on-campus SDE write-up); **HackerRank** (off-campus / experienced loops on Medium & aggregated Bengaluru reports)
- **Duration:** ~60–90 minutes most common (1 h HackerEarth campus batch; 90 min in several campus/off-campus reports)
- **Sections & format:** Often **two-part**: MCQ block on CS fundamentals + **2 coding problems**; some off-campus SDE-2 reports split ~25 MCQs (~30 min) then 2 DSA problems (~40 min); contest pipelines add a short standalone MCQ quiz before a separate coding challenge
- **Sectional cutoffs:** GFG recruitment overview notes **separate MCQ and coding cutoffs** on HackerEarth — partial coding passes have still advanced in campus batches
- **Negative marking:** Not consistently reported
- **Topics tested (MCQ):** OOPS/SOLID, OS, DBMS, CN, compiler basics, SQL, aptitude; DSA theory
- **Topics tested (coding):** arrays/strings, graphs, DP, greedy, trees, implementation; scoring often weights **hidden/private test cases**
- **Difficulty:** Medium → hard for fresher campus; off-campus SDE-2 reports range easy–medium to medium–hard

## Interview Rounds
1. **OA** — gate; platform per invite (see above)
2. **Technical 1 (45–75 min, virtual)** — live coding on shared IDE / doc; 1–2 DSA problems; resume projects; Java/OOP (inheritance, SOLID, interfaces); occasional SQL
3. **Technical 2 (45–70 min, virtual)** — second DSA round **or** core-CS deep dive (OSI/TCP-IP, threading, paging, STL/BST tricks); puzzles; sorting/graph variants; follow-ups on time/space complexity
4. **Hiring manager / managerial (45–60 min)** — behavioral, leadership, motivation; light tech (cloud basics, team fit); company/team discussion; may include situational judgment
5. **HR (optional / combined)** — traditional HR + debrief-driven closure; not always a separate elimination round

**Off-campus SDE-2 pattern (LC Discuss):** OA → 2× ~75 min technical (project walkthrough + string parsing / Java fundamentals) → ~40 min HM behavioral.

**Senior / SSE tracks (Medium, Glassdoor):** OA on HackerRank → 3 virtual rounds mixing DSA, LLD, HLD → HM behavioral; design depth rises with level.

## Topic Weights
| DSA | OS | C/C++ | DBMS | CN | LLD | HLD | Concurrency | Aptitude |
|---|---|---|---|---|---|---|---|---|
| Very High | Med–High | Med | Med | Med | Low–Med | Low | Low–Med | Low |

*(Fresher campus SDE skew; SDE-2+ off-campus adds LLD/HLD and backend stack depth.)*

## Recurring Patterns & Tips
- **Resume integrity** — interviewers drill every project bullet; ML/backend resumes get domain follow-ups (bias–variance, model choice, etc.).
- **Core CS parity with DSA** — some campus loops skip live coding in a round but heavily test OS/CN/OOP; do not treat OA DSA prep as sufficient alone.
- **Communicate before coding** — state approach and complexity; explain trade-offs on follow-ups (Kadane variants, modified Dijkstra, train scheduling).
- **OA platforms change** — never assume HackerEarth; read the scheduling email.
- **Partial OA passes can advance** — optimize for full solves but one complete + one partial has cleared in campus batches.
- **Managerial round ≠ formality** — leadership, hackathon stories, and “why Walmart” matter; research recent WGT initiatives.
- **Off-campus:** referral → OA lag of weeks is common; HM round may precede formal debrief/offer (Glassdoor India forum).
- **Puzzles & parenthesis/string classics** appear in older campus SDE-2 write-ups alongside standard LC mediums.

## Related topics
- [Arrays & Strings](../../topics/DSA/Arrays_Strings.md)
- [Trees](../../topics/DSA/Trees.md)
- [Graphs](../../topics/DSA/Graphs.md)
- [Dynamic Programming](../../topics/DSA/Dynamic_Programming.md)
- [OOPs & LLD](../../topics/OOPs_LLD.md)
- [OS](../../topics/OS.md)
- [DBMS & SQL](../../topics/DBMS_SQL.md)

## Resource Panel
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- [Complete DSA Roadmap](https://drive.google.com/file/d/10e8Q1yVymwxWhz9LgcWxwrkpW9eMxRla/view)
- [Awesome LeetCode Resources](https://github.com/ashishps1/awesome-leetcode-resources)
- [Sean Prashad LeetCode Patterns](https://seanprashad.com/leetcode-patterns/)
- [OOPS Boss Sheet](https://drive.google.com/file/d/1s0HeZt05eck7cuwXxQZtDiZ_NEPfZwo6/view)
- [OS Boss Sheet](https://drive.google.com/file/d/1vG8CqGV8kGYOqTbA812-mKHKyeP1jGAQ/view)
- See also: [00_INDEX](../../00_INDEX.md) · [Software_Product_SDE](../../archetypes/Software_Product_SDE.md)

## Sources
- [Walmart SDE On-Campus (GFG)](https://www.geeksforgeeks.org/interview-experiences/walmart-interview-experience-for-sde-on-campus-1/)
- [Walmart SDE On-Campus 2021 Virtual (GFG)](https://www.geeksforgeeks.org/interview-experiences/walmart-interview-experience-for-sde-on-campus-2021-virtual/)
- [Walmart Labs Recruitment Process (GFG)](https://www.geeksforgeeks.org/interview-experiences/walmart-labs-recruitment-process/)
- [How I got into Walmart Global Tech (Medium — CodeHers pipeline)](https://prayukti.medium.com/how-i-got-into-walmart-global-tech-dafab3c38816)
- [Walmart SDE-II Bengaluru March 2024 (LC Discuss)](https://leetcode.com/discuss/post/5004333/walmart-sde-ii-bengaluru-march-2024-offe-qqf9/)
- [Walmart SDE-2 India 2024 Offer (LC Discuss)](https://leetcode.com/discuss/interview-experience/5066439/Walmart-or-SDE-2-or-India-or-2024-Offer)
- [Interview Experience at Walmart for Senior Software Engineer (Medium)](https://medium.com/@vineetkamath1997/interview-experience-at-walmart-for-senior-software-engineer-role-122c276a3083)
- [Walmart Global Tech interview questions (Glassdoor India)](https://www.glassdoor.co.in/Interview/Walmart-Global-Tech-Interview-Questions-E3293060.htm)
- [WGT India debrief / HR closure (Glassdoor Forum)](https://www.glassdoor.co.in/Community/walmart-global-tech-india-o2cm-5/the-recruiter-at-walmart-told-me-that-i-have-cleared-all-the-rounds-but-in-the-hr-round-the-hr-told-me-that-they-will-have-a-debrief)
