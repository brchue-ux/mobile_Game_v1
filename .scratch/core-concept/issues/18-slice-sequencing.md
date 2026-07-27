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
top of card accrual, at-cast combining, ~~gesture casting, lane aiming~~ target
selection, three lanes, terrain, and creeps.

That was roughly eleven systems. **2026-07-26: skill-shot casting was removed**
(see [03](03-gesture-skill.md)), collapsing gesture casting and lane aiming into
a single selection step — call it ten, and one fewer *dexterity* system to teach,
which is the more expensive kind. **This is the first time the count has gone
down.** It does not retire this ticket; it buys it room.

Ticket 13 established that even the minimal version of this game was untestable
without a tutorial: the one reaction it produced was confounded by having too
much unfinished at once.

### What this ticket is not — read this before invoking it

**Nothing here is proposed for deletion.** The user wants this material and it is
recorded as wanted. This ticket decides **sequence**, not scope.

**Definition, because the jargon caused a real misunderstanding on 2026-07-21.**
"Budget" here means exactly two things: *the number of systems a player must
learn in order to play one build*, and *the number of things competing for one
phone screen*. Nothing else.

**It does not mean ideas, design work, or what-ifs.** Those are unbounded and
this ticket has no authority over them. The user, correctly, on being told the
per-hero novel mechanic was "the most expensive line in the list":

> *"it's also the novel mechanic that could drive people to the game. It's not a
> reason to be like, 'Oh we're not gonna do it. We're not gonna even think of it
> or we won't even flesh out the what-ifs.' ... I don't know what the budget is
> and I don't know what oversubscribed means but if it's thoughts about specific
> artifacts in the game or specific points of the game then the hell we're
> oversubscribed."*

**This ticket may never be used to discourage exploring an idea.** If it is being
invoked against thinking rather than against a build's contents, it is being
misused. Cost belongs in the footnotes of a design, not in its headline.

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
