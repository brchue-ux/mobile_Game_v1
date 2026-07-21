# Prototype — sixty seconds of a match

Type: prototype
Status: resolved
Blocked by: 02

## Question

What does a minute of this game actually feel like?

**Mode change, and it is the point of this ticket.** Charting and 02 were run as
multiple-choice grilling, and the user twice asked to brainstorm instead —
*"I want some mechanic that revolves around that to help me brainstorm"*,
*"there's just so many things."* Choosing between abstractions is the hardest
possible way to reason about a game that does not exist yet. This ticket makes
something concrete to **react to** instead.

Build a rough, throwaway simulation of sixty seconds of play: cards arriving on
a timer, a bank filling, creeps marching, a lane collapsing. Fidelity is not the
goal — reaction is. Use `/prototype`.

### Parameters this must surface (deferred here from 02)

The at-cast model is payload + modifiers, but its numbers are unset. The
prototype exists to make these visible rather than argue them on paper:

- Cap on modifiers per cast, and what enforces it
- Whether composition is reversible mid-build or committed as you go
- Whether nonsense combinations exist, and what attempting one does
- How legible a compound spell is to an opponent
- What the card arrival interval feels like — the single most texture-defining
  number in the game

### What a good outcome looks like

Not a decision. A set of reactions specific enough to sharpen 09, 04 and 11 —
and ideally at least one surprise neither party predicted on paper.

## Answer

Assets: `prototypes/13-sixty-seconds.html` (v2, current),
`prototypes/13-sixty-seconds.v1-tugofwar.html.bak` (v1, kept as the record of
what was wrong). Served locally with `python3 -m http.server 8931` from the
prototypes dir; `index.html` is a symlink to the current version.

**The prototype largely failed as a feel test, and that is itself the finding.**
Very little of what was built matched what the user pictures. Recorded plainly
so the next prototype does not repeat it.

### What the reactions actually established

- **Creeps are units, not a meter.** `[committed]` v1 abstracted the lanes into
  a 0–100 fill bar. The user: *"the tug-of-war mechanic is not what I want."*
  This had already been said during charting and was lost in summarisation —
  see the failure note below. Now a locked constraint on the map.
- **Match length is far longer than a minute.** `[provisional]` 60s was rejected
  outright as *"far far too short."* v2 defaults to 3:00 with a range to 15:00;
  the real number is unfound. Feeds 05.
- **The bank was the one thing that landed.** `[provisional]` The user singled
  out the bank visual as the only positive on screen. Weak evidence, but it is
  the only positive signal the prototype produced — 09 should treat banking as
  live rather than speculative.
- **The composition interaction read as unintuitive — but the signal is void.**
  `[no conclusion]` On v2 the user said *"it's very unintuitive"*, and the agent
  initially recorded this as evidence against the payload+modifier model. The
  user then corrected: it was unintuitive because there was **zero tutorial**,
  the **AI crushed them instantly**, and it was a **crude mock with no prior
  game to pattern-match against**. Any mechanic would read as unintuitive under
  those three conditions. **This tells us nothing about combining**, and the
  earlier claim that it was "first evidence on the central risk" was an
  overreach that has been retracted from the map.

### Two build failures worth recording

1. **A rendering bug invalidated v1 entirely.** The hand's DOM was rebuilt every
   animation frame, restarting a fade-in animation 60×/sec, so cards appeared
   faded and flickering and taps landed on elements destroyed mid-touch. The
   user could not see the cards. Fixed in v2 by rebuilding DOM only on a dirty
   flag and moving the board to canvas.
2. **v1 rebuilt a concept the user had already rejected.** The agent worked from
   its own compressed summary of the design rather than from what the user
   actually said, and the summary had dropped the correction. See
   `feedback_summary_drops_rejections` in memory.

### Not verified

v2 was syntax-checked and confirmed served. It was **never observed running** —
no browser was available. "Fixed" means the cause is structurally gone, not that
the fix was seen to work. The one substantive reaction to v2 ("unintuitive")
suggests it rendered, but this is inference, not verification.

### Requirements for the next prototype

Established by the confounded-signal correction above. A prototype cannot test
whether something *feels* right until these are true:

- **Guided first run.** A tutorial, a coached opening, or at minimum on-screen
  prompts naming the next action. Without one, "unintuitive" measures the
  absence of teaching, not the mechanic.
- **A passive or difficulty-tiered opponent.** Being crushed immediately means
  the player never reaches the behaviour under test. Default the AI to
  near-passive, with difficulty as a slider.
- **Say what is crude.** The user cannot infer intent from a rough mock the way
  they would from a finished game. Label placeholders as placeholders on screen.

### What this does not settle

The parameters this ticket was meant to surface — modifier cap, reversibility,
nonsense-combo handling, card interval — got **no useful signal**, because the
board and the interaction failed first. They return to 09/04, or to a second
prototype built after the board reads correctly.
