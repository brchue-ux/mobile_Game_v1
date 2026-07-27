# Match shape & win condition

Type: grilling
Status: open — **⚠ current answer held under protest** (2026-07-26)
Blocked by: —

## ⚠ The user does not want the win condition this ticket has (2026-07-26)

> *"you can eventually, I guess, destroy their base. I don't really want it to be
> 'destroy their base' so maybe there's something else that can be thought of
> later on just because that's so prototypical."*

**Base destruction stands only because nothing has replaced it.** The objection
is genre-fatigue, not mechanics — it works, it is simply the obvious thing. Not a
reversal, not a decision; a deferral with stated dissatisfaction, and it must not
be read later as settled.

**Why this is filed loudly.** This design has now discarded hero-death *and*
soured on base-destruction. The ending of a match is one of the least settled
things in the whole concept while presenting as one of the most settled. It also
just acquired a new piece to work with: **towers** appeared for the first time on
2026-07-26 (the hero *"may defend towers"*) and nothing about them is specified —
whether they shoot, gate lane progress, or are themselves the thing destroyed.

**Also relevant:** the match's strategic dynamic was described as *"trying to
have that tug of war... make your lanes and heroes stronger than they are."*
That names the contest, **not** a meter — see the language trap filed under the
creeps constraint in the map.

## Question

What does a match look like from start to finish, and what ends it?

The MOBA framing implies structure that has never been specified. Creeps march
and contest lanes — but toward what?

### Partial answer — 2026-07-21, then reversed the same day

**Superseded:** *"The loss condition is your hero dying"* `[provisional]` — from
the first dump, *"that hero is the thing that causes you to lose the game when it
dies."* Kept per the append-only rule; do not silently re-adopt it.

**Reversed by the user**, who spotted the contradiction unprompted: if the hero
farms the jungle autonomously while the player commands from an angled overhead
view (01), the hero is not the player's avatar, and its death cannot be the
player's defeat without the fiction breaking.

**Current leading candidates** `[provisional]`, which compose:

1. **Hero death is a temporary power-down** until revival — a setback, not an
   ending.
2. **Base destruction is the loss condition.**

This is the Dota lineage the map already commits to, and it is kinder to the
other open questions here: a revive timer is a natural comeback valve, and a base
with structures gives the match a shape longer than one decisive fight — which
13's "far far too short" finding demands.

**What is still unclosed:** whether bases have towers or intermediate objectives,
what revive costs, and whether creeps alone can end a match or players must
actively finish it.

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

## Dump — 2026-07-26

### Answered

**How a match ends procedurally.** `[provisional]` *"The match will end whenever
one person leaves and the other defaults to winning or the win condition is met
by the other person."* Concession/disconnect is a win by default. First time
quitting has been addressed at all.

**Comeback dynamics exist, with a hard rail attached.** `[committed]` — this is
a requirement, not a candidate:

> *"Comeback dynamics will need to exist but I need to make sure that whatever
> they are, people don't just purposely lose in order to get them to get free
> things because it lets them snowball in reverse."*

**No comeback mechanic may reward deliberate losing.** Any candidate has to be
tested against a player throwing on purpose to farm it. Note this rules out the
naive version of the most common comeback designs — flat bounties for being
behind, catch-up gold, scaling underdog buffs — unless they are shaped so the
loss costs more than the bonus returns.

**Hero death costs nothing.** `[provisional]` Death is a respawn timer, not a
penalty — consistent with hero-death-as-power-down. **Buybacks:** one or two per
match, *"they'll pay a price to get it back immediately."* So the free path is
waiting; the paid path is instant. Cost unspecified.

> ⚠ The sentence after buybacks — *"and then it probably doesn't come back for
> healthful men either"* — did not transcribe. Best guess is that a bought-back
> hero, or a subsequent death, carries a longer respawn. **Not recorded as
> design.** Needs re-stating.

**PvE and PvP share a match shape.** `[provisional]` *"PvE and PvP are the same
thing, just human versus AI. Maybe there will be some subtle differences, I don't
know."* Closes the ticket's PvE/PvP question at the structural level.

**Creeps alone almost certainly cannot end a match.** `[provisional]` *"maybe
Creeps alone could end it but I don't see that really ever happening."* So a
player has to actively finish.

### Towers — proposed, then doubted, in the same dump

**Both statements are recorded; this is a live wobble, not a decision.**

First, in favour of what a tower *does*:

> *"towers because those usually break points in the lane, places where you can
> slow your opponent down as a comeback mechanic type thing. You give those bonus
> gold, like how we do in League of Legends, but I'm not really sure. I don't
> really want to just copy that."*

Then, against the tower itself:

> *"I don't know if I want towers on the lanes because then it just becomes
> you're copying every other MOBA that exists. Maybe there'll be something in the
> lanes but maybe it's not a tower."*

**The job survives the object.** What is wanted in a lane is a **breakpoint** — a
thing that segments the lane, slows a pushing opponent, and rewards taking it.
What is not wanted is a turret, because it reads as copied. That is a design
brief, and a decent one: *find a lane breakpoint that isn't a tower.*

### Clarified later the same day — the breakpoint is a stall, not a comeback

The agent flagged a friction: a breakpoint described as *"a comeback mechanic
type thing"* is the shape that can reward being behind. **The user corrected the
framing** rather than the mechanic:

> *"I get what you're saying... it can't be something that you chase. You can't
> chase being down in the match because you're looking for that comeback
> mechanic. I don't view my pseudo towers as that. It's more of a way to just
> stall the game. It prevents you from bulldozing through a lane at the beginning
> because whatever is in that depth of that lane is too strong for you at the
> current point of the game."*

**The job is pacing, not catch-up.** `[provisional]` A pseudo-tower is a
**scaling gate**: something deep in a lane that is simply too strong for you
early, and becomes passable as you grow. It stops an early bulldoze from ever
starting.

**This resolves the friction, and it generalises into a useful test.** Preventing
a snowball is not the same as rewarding being behind:

- A **preventive** device applies equally to both players from the opening
  whistle, and gives the losing player nothing they did not already have. It
  passes the deliberate-losing rail cleanly.
- A **restorative** device pays out in proportion to how badly you are doing,
  which is what a thrower farms.

**Keep pseudo-towers on the preventive side of that line.** The earlier "bonus
gold for taking it, like League" idea is fine under this reading — that pays the
*attacker* for clearing the gate — and would fail it only if the payout scaled
with how far behind the attacker was.

**Still open:** what the thing actually *is*, given the turret is rejected as
copying. It needs to read as a lane obstacle with a power curve, not a building.
Terrain manipulation is a neighbouring idea and may share machinery.

### Terrain manipulation — the new material `[provisional]`

> *"I was thinking something like you could mess up their terrain... You get cards
> or a crew, like stored benefits, that can allow you to affect the terrain. Maybe
> create more water, create lava, or create holes in the ground that can make it
> harder for their creeps to traverse or for their heroes to traverse. Maybe that
> can somehow affect what the overall win condition is."*

**Players can reshape the battlefield** — water, lava, holes — to impede enemy
creep and hero movement. This is the strongest candidate this ticket has produced
for an objective that is not a copied MOBA objective.

Why it is a good fit, recorded so the reasoning survives:

- It gives **terrain a mechanical job that no other system was doing**, which the
  map has wanted since "the jungle must be mechanically live, not scenery."
- It is **spatial without needing skill shots** — the player is changing the
  board, not aiming at it. Compatible with casting-as-selection.
- It gives the **pannable observer camera something worth panning for.**

**Unresolved within it:** whether terrain damage is permanent or decays, whether
it can be repaired or countered, whether it hits your own units too, and the
user's own *"maybe that can somehow affect what the overall win condition is"* —
which is a hint, not a mechanism.

**Concrete example, and its cost model — 2026-07-26.** *"a giant tree root
blocks off the ability for the hero to go to another lane."* So terrain effects
can **deny lane-to-lane traversal**, and the user's instinct is that an effect
that strong *"shouldn't just be one card"* — it should be accrued. See
[09](09-banking-mechanic.md) for what that accrual is and is not.

> **⚠ Interaction to keep straight, not a contradiction.** [12](12-jungle-role.md)
> records that the jungle *"is not a wall between lanes, because the hero would
> need to be able to go through them."* A tree root that blocks traversal does
> not violate that — it **temporarily creates** a wall where the default is
> passage. In fact the rule is what gives the effect its value: blocking is only
> a play worth making because traversal is the norm. If lanes were walled by
> default, the card would do nothing.

### ⚠ "Cards or a crew, like stored benefits" — this may be banking

**Flagged, not acted on.** Two readings, and they lead to different places:

1. **"accrue"** — near-certain given voice input. *"you get cards, or accrue,
   like stored benefits."* That describes **saving something up over time and
   spending it on a terrain effect** — which is [09](09-banking-mechanic.md),
   the mechanic **shelved on 2026-07-21**.
2. **"a crew"** — a literal squad or unit, which would be new and would brush
   the locked no-commandable-army constraint.

If reading 1 is right, this matters a lot: **banking was shelved for having no
payoff worth its cost, and terrain manipulation is a payoff.** It is expensive,
board-changing, and naturally wants a build-up — exactly the "investment" half
of the tempo-vs-investment split that 09 was designed around, and none of 09's
four preserved candidates were this good.

**Not unshelved.** The map says do not reintroduce banking unprompted; the user
raised the shape themselves, which makes it prompted, but they did not name it
and may not have meant it. **This needs a yes or no from the user, not an
inference from me.**

### Still not answered — the win condition itself

Base destruction remains **held under protest**. Terrain manipulation was floated
as possibly feeding into it, but no replacement was named. The ticket's headline
question is still open.
