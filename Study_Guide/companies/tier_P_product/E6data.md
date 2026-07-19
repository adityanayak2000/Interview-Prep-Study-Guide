# E6data
**Role(s):** Software Engineer (Engine); Software Engineer (Perf / Rust); Backend Developer; Rust Engineer – Systems & Performance; SDET – Database Internals; Software Engineer Intern → FTE
**Tier:** P
**Status:** done-v3

> 🚪 [Start](../../START_HERE.md) · 🗺️ [Map](../../README.md) · 🏢 [Companies](../README.md) · 📚 [Library](../../library/README.md) · 🔍 [Find](../../FIND.md)

## Process Overview
E6data builds a **lakehouse / distributed SQL compute engine** (Bengaluru hybrid). Public GFG/LeetCode Discuss/Glassdoor campus write-ups are **thin**. Strongest process signals are the **company-authored Engine JD rubric** and **campus-adjacent competitive-programming** funnels (e.g. PES Algomania). BITS-like profiles often enter via **internship → FTE conversion** rather than a mass GFG-style campus OA.

| Path | Entry | Typical flow |
|---|---|---|
| Off-campus Engine SDE | TCS iON / Cutshort / LinkedIn / Zoho Recruit | Application → **~3-hour coding deliverable** → live code-modification → technical deep-dives → fit |
| Campus-adjacent CP (PES Algomania) | Contest | HackerRank prelims → offline cycles → internship / PPO signal |
| BITS-like internship | Targeted outreach | Recruiter-led interviews; intern cohort → conversion review |

**Campus vs off-campus:** Algomania-style paths look like **LC Medium–Hard CP**. Engine SDE off-campus emphasizes **performance + internals + defending your submitted code**, not a classic 2-problem HackerRank only. Role tracks (Engine vs Data/QA/Frontend) differ — do not mix OA assumptions across tracks.

**M.E./M.Tech CS:** Engine listing explicitly lists **M.Tech – Computer Technology** alongside B.Tech CS/IT. Strong fit for systems/DB/distributed projects.

## Online Assessment (OA)
Do **not** invent a mass-campus OA — public candidate OA banks are scarce.

- **Platform:** **HackerRank** for Algomania prelims (sourced). Engine SDE timed coding platform **Unknown** (JD says “code in 3 hours” without naming vendor)
- **Duration:** **~3 hours** coding component for Engine SDE (company JD)
- **Sections:** Unknown for standard SDE OA; Algomania = team CP rounds
- **Negative marking:** Unknown
- **Topics / difficulty:** Working, performant code under time pressure; Algomania described as LC Medium–Hard; follow-up interviews require **live tweaks** to your submission
- **Other:** Some job mirrors mention **up to 3 technical discussions** covering prior work + coding

## Interview Rounds
1. **Screening / application** — resume + passion projects; recruiter outreach
2. **Timed coding (~3 hours)** — deliver working code (Engine JD)
3. **Code modification** — implement interviewer-requested changes to your submission live
4. **Technical deep-dive(s)** — DSA (hashmaps, complexity); sync vs async / GC; cache hierarchy / SIMD bonus; atomics vs locks; **cache LLD** with progressive constraints (entry count → memory cap)
5. **Manager / culture fit** — small-company, recruiter-guided processes reported
6. **Intern → FTE** — performance review after internship (cohort pattern)

## Topic Weights
| DSA | OS | C/C++ | DBMS | CN | LLD | HLD | Concurrency | Aptitude |
|---|---|---|---|---|---|---|---|---|
| High | Med–High | Med | Med–High | Low–Med | High | High | High | Low |

## Recurring Patterns & Tips
- Expect **systems / query-engine thinking**, not FAANG-only LC loops.
- Practice **LRU-style cache design** and evolving constraints.
- Be ready to **modify your own take-home** under interviewer direction.
- Java/Rust appear in postings; JD stresses **fundamentals over language trivia**.
- Passion projects in distributed systems / DB internals / benchmarking help.
- Confirm track (Engine vs Perf vs DE) from the specific JD before prep.

## Related topics
- [DSA Overview](../../topics/DSA/00_DSA_Overview.md)
- [System Design HLD](../../topics/System_Design_HLD.md)
- [OOPs / LLD](../../topics/OOPs_LLD.md)
- [Concurrency](../../topics/Concurrency_Multithreading.md)
- [Operating Systems](../../topics/OS.md)
- [DBMS / SQL](../../topics/DBMS_SQL.md)
- [Systems Interview](../../topics/Systems_Interview.md)

## Resource Panel
- [30 Coding Patterns](https://drive.google.com/file/d/1EQHkfIdslaNfyfD0Py6hoNl8ZlXuEcYD/view)
- [Complete DSA Roadmap](https://drive.google.com/file/d/10e8Q1yVymwxWhz9LgcWxwrkpW9eMxRla/view)
- [donnemartin / system-design-primer](https://github.com/donnemartin/system-design-primer)
- [LLD Boss Sheet](https://drive.google.com/file/d/1vG8CqGV8kGYOqTbA812-mKHKyeP1jGAQ/view)
- [OSTEP — Operating Systems](https://pages.cs.wisc.edu/~remzi/OSTEP/)
- [Designing Data-Intensive Applications (overview)](https://dataintensive.net/)
- [e6data product — lakehouse compute](https://www.e6data.com/product/lakehouse-compute-engine-e6data)
- See also: [00_INDEX](../../00_INDEX.md) · [Software_Product_SDE](../../archetypes/Software_Product_SDE.md)

## Sources
- [Software Engineer (Engine) — TCS iON / e6data JD](https://www.tcsion.com/jobs/E6data-Computing-Private-Limited/Software-Engineer-Engine-13182/)
- [Software Engineer — e6data India Remote (RemoteRocketship)](https://www.remoterocketship.com/company/e6data/jobs/software-engineer-india-remote/)
- [Algomania 3.0 — PES University](https://events.pes.edu/11437/)
- [EncodeAI PESU — e6data Algomania sponsor](https://www.linkedin.com/posts/encodeai-pesu-25a2762b0_algomania3-pesu-e6data-activity-7437518312965705728-muuQ)
- [e6data Zoho Recruit careers](https://e6data.zohorecruit.in/jobs/careers)
- [e6data — Cutshort company](https://cutshort.io/company/e6data-98-0rAuZxnp)
- [Backend Developer — Instahyre](https://www.instahyre.com/job-369048-backend-developer-at-e6data-work-from-home/)
- [e6data company LinkedIn](https://www.linkedin.com/company/e6data)
