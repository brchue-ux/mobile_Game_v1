# Slice sequencing — what ships in the vertical slice

Type: grilling
Status: open
Blocked by: —

## Question

Of everything in this design, what is in the vertical slice and what is not?

New — raised 2026-07-21. This ticket exists because the design is growing faster
than its teachable surface, and nobody owned that.

### Why it exists

02 rejected shipping all four merge outcomes on stated grounds: four subsystems
taught under a running clock is the trade the accessibility call refuses.

The 2026-07-21 dump then added hero selection, hero stat blocks, an automated
jungle hero, a gold economy, item drops, item slots, and deck construction — on
top of card accrual, at-cast combining, gesture casting, lane aiming, three
lanes, terrain, and creeps.

That is roughly eleven systems. Ticket 13 established that even the minimal
version of this game was untestable without a tutorial: the one reaction it
produced was confounded by having too much unfinished at once.

### What this ticket is not

**Nothing here is proposed for deletion.** The user wants this material and it is
recorded as wanted. This ticket decides **sequence**, not scope — what the slice
must contain to answer its question honestly, and what is deliberately deferred.

### The answer must settle

- **The single question the vertical slice exists to answer.** One question. If
  the slice has three, it will answer none of them cleanly — that is the lesson
  of 13.
- **The minimum set of systems that can answer it.** Everything else is a
  confound, not a feature.
- **What is explicitly deferred**, written down, so deferral is a decision rather
  than an oversight that gets discovered mid-build.
- **Whether the slice is meant to be fun or merely instrumented.** These build
  differently.
- **How much tutorial is required before any reaction to it counts as evidence.**
  Non-negotiable per 13.

### Standing gate

Per the working method adopted 2026-07-21, the design will keep growing between
sessions — that is expected and fine. **Revisit this ticket every time it does**,
rather than letting the slice quietly absorb each new system by default.

Interacts: everything. Especially 04, 13, 17.
