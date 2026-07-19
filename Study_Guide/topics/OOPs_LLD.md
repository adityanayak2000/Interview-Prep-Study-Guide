# OOPs & LLD (router)
**Software / Product track** · Archetype: [Software_Product_SDE](../archetypes/Software_Product_SDE.md)

## Why it matters
Product OAs and interviews grill OOP pillars + **machine coding / LLD** (build a small working system). Semiconductor tracks care less about LLD volume — see [Semiconductor_Systems](../archetypes/Semiconductor_Systems.md) — but still ask **virtual / vtable / diamond** on C++ output rounds ([Cpp_Fundamentals](Cpp_Fundamentals.md)).

## Concept map

### Four pillars (oral)
- **Encapsulation** — data + methods; prefer private state + public API (getters careful — don’t leak mutability).  
- **Abstraction** — model the essential interface; hide implementation.  
- **Inheritance** — reuse & “is-a”; prefer composition when reuse without subtyping.  
- **Polymorphism** — same interface, different behavior: **overload** (compile-time) vs **override** (runtime via `virtual`).

### Virtual / vtable (Tier S + product)
- Non-virtual call = static type; **virtual** = dynamic type via **vptr → vtable**.  
- **Always** virtual destructor if `delete` through base pointer.  
- Pure virtual (`= 0`) → abstract class; cannot instantiate.  
- **Diamond problem:** two base paths → duplicate subobjects; fix with **virtual inheritance** (shared base). Oral from [YC Series 01](https://yc-kuo.medium.com/c-interview-01-oop-virtual-polymorphism-204d8d466087) + [notescs virtual notes](https://github.com/notescs/notes/tree/main/C-CPP-OOPS-for-Interviews).  
- During ctor/dtor, virtual dispatch uses the *currently constructing* class — do not call overrides expecting derived state.

### Static members & private-constructor factories (light oral)
A `static` data member is shared across all instances (e.g. a live instance counter); a `static` member function needs no instance and can only touch static data — usable as a factory to instantiate a class with a **private constructor** (common singleton/factory pattern building block). *Trap:* static functions can never be `virtual` — dynamic dispatch needs an instance (`this`)/vtable lookup that static functions don't have. (Paraphrased from notescs C++/OOP notes.)

### Copies & smart pointers
- Default copy of classes with raw owning pointers = **shallow** → double-free. Need deep copy / Rule of Five, or rule of Zero with `unique_ptr`/`vector`.  
- Prefer `unique_ptr`; `shared_ptr` + `weak_ptr` for shared graphs. Details in [Cpp_Fundamentals](Cpp_Fundamentals.md).

### SOLID (one-liner each)
S — one reason to change · O — extend without editing · L — subtypes substitutable · I — fat interfaces bad · D — depend on abstractions.

### LLD machine coding
6-step (Interview Prep): clarify requirements → entities → relationships → APIs → code → edge cases.  
Patterns: singleton (thread-safe C++11 static / `call_once`), factory, strategy, observer — know *when*.  
Concurrent LLD: LRU cache, rate limiter, pub-sub — link [Concurrency](Concurrency_Multithreading.md).

## Practice direction
- Implement: parking lot / tic-tac-toe / snake / catalog search (machine coding style).  
- LC hybrid: [LRU Cache (146)](https://leetcode.com/problems/lru-cache/).  
- Oral: draw diamond with virtual base; explain vptr layout for single inheritance.

## Boss Sheet
Day-before: [OOPS Boss Sheet](https://drive.google.com/file/d/1s0HeZt05eck7cuwXxQZtDiZ_NEPfZwo6/view) + [LLD Boss Sheet](https://drive.google.com/file/d/1vG8CqGV8kGYOqTbA812-mKHKyeP1jGAQ/view).

## Resource Panel
- [OOPS Interview Questions PDF](https://drive.google.com/file/d/19E0KwbC_ufqGPl6-sgL8jMWASraCiQ0E/view)
- [Dive Into Design Patterns](https://drive.google.com/file/d/1uu3Ye48X9h0YifMl56o2BbN5vkQdFiJk/view)
- [awesome-low-level-design](https://github.com/ashishps1/awesome-low-level-design)
- [LLD CrashCourse](https://github.com/Sunchit/SystemDesignLLDCrashCourse)
- [Design Patterns playlist](https://www.youtube.com/playlist?list=PLrhzvIcii6GNjpARdnO4ueTUAVR9eMBpc)
- [YC Series 01 — OOP/Virtual/Polymorphism](https://yc-kuo.medium.com/c-interview-01-oop-virtual-polymorphism-204d8d466087)
- [notescs — C/C++/OOPS for Interviews](https://github.com/notescs/notes/tree/main/C-CPP-OOPS-for-Interviews)
- Full OOP/LLD strategy text: [Interview Prep](../../🎯%20Interview%20Prep%20Resources.md) §OOP  
- Related: [Cpp_Fundamentals](Cpp_Fundamentals.md) · [Concurrency](Concurrency_Multithreading.md) · [00_INDEX](../00_INDEX.md)
