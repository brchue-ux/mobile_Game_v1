# Match shape & win condition

Type: grilling
Status: open
Blocked by: —

## Question

What does a match look like from start to finish, and what ends it?

The MOBA framing implies structure that has never been specified. Creeps march
and contest lanes — but toward what?

### Partial answer — 2026-07-21

**The loss condition is your hero dying.** `[provisional]` From the dump: *"that
hero is the thing that causes you to lose the game when it dies."* See 15.

This closes the biggest gap in this ticket, and it kills the tug-of-war
resolution option outright — consistent with creeps-are-units being locked.

What it does **not** close: *how* a hero dies. Creeps reaching it? Spells cast at
it? Both? Until 15 answers that, this ticket has a win condition with no
mechanism. Comeback dynamics and match length also remain open, and both got
harder — a single kill-target loss condition can end a match abruptly, which sits
badly with 13's finding that matches should run minutes, not seconds.

The answer must settle:

- **The win condition mechanism.** Hero death is the trigger; what actually
  applies the damage? Blocked on 15.
- ~~**The win condition.**~~ Answered provisionally above. Destroy a base/ancient?
  Push all lanes past a threshold? Score at a time limit? Tug-of-war resolution?
- **Towers and objectives.** Does the map have structures? Are there neutral
  objectives worth contesting in the jungle?
- **Match length.** Mobile sessions are short and interruptible. A 40-minute Dota
  match is not a phone match. What's the target, and does it survive a commute?
- **Comeback dynamics.** Real-time lane games snowball. What prevents a match
  being decided in the first ninety seconds while still taking ten minutes?
- **PvE vs. PvP differences.** Do both modes share a match shape, or does PvE
  have its own structure?
- **What the player does when they have no cards.** Dead time is a real risk in a
  cooldown-gated design.
