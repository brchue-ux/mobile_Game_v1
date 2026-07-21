# Heroes — stats, roles, and differentiation

Type: grilling
Status: open, substantially answered
Blocked by: —

## Question

What is a hero, and what does it do during a match?

Raised 2026-07-21, dumped on the same day. The largest single addition to the
design since charting — it reaches into the win condition, the jungle, the
economy, and the camera.

## What the hero is

- **~8 heroes**, chosen before matchmaking (14). `[provisional]`
- **Stats: armor, health, mana.** `[provisional]`
- **The hero acts autonomously**, farming creeps in lanes and doing things in the
  jungle. The player does not drive it. `[provisional]`
- **The player is not the hero.** See the loss-condition reversal below — this
  turned out to be the load-bearing fact about heroes.

## Differentiation

Six axes, from the dump:

- **Race**
- **Passives**
- **Size**
- **Weapons**
- **Style of attack** — physical, melee, magic, ranged, summoning
- **One novel map-affecting thing per hero** — see below; this is the headline

### The archetype layer is rock-paper-scissors

> *"casters generally beating melee. Range generally beats melee but if melee gets
> into melee range on any of those, melee wins."*

Plus a cross-cutting equipment/armor layer: *"light armor versus heavy armor
versus cloth, dagger versus giant [greatsword]."*

**This is asymmetry, not power level** — confirmed with the user. Heroes differ
in *shape*, and a heavy melee hero is slow and **weak to ranged** rather than
weak outright. (That last clause is a reconstruction of a garbled transcription:
*"he'll be slow because he's heavy and he'll be weak to ranged"* — accepted
because it is the only reading consistent with the rock-paper-scissors above.)

The distinction matters because lateral asymmetry is compatible with the locked
fairness constraint and a straight power ladder is not.

### The novel per-hero map mechanic

Each hero gets **one novel thing that can affect the map in some way.**

**Recorded as a potential headline differentiator, not as a cost.** The user's
framing, and it is the right one: *"it's also the novel mechanic that could drive
people to the game. It's not a reason to be like, 'Oh we're not gonna do it. We're
not gonna even think of it or we won't even flesh out the what-ifs.'"*

Build cost — eight bespoke mechanics is eight things to design, balance and
teach — is noted in 18 as a **shipping-order** question only. It does not gate
exploring or fleshing these out. See 18's scope note.

## Mana

Still unresolved, with a live candidate: *"Maybe they don't have mana but maybe
they do. Maybe the cards affect the jungle but the hero still requires mana to use
abilities."*

**Candidate division of labour:** cards act on the jungle, lanes and the hero;
mana is what the *hero* spends on its own abilities. That gives mana a verb, which
is what it was missing. Not chosen. Interacts with 11.

## Power differences — LOCKED CONSTRAINT

> *"if power can change on heroes at all from weapons or stats, it will come from
> in game cards or match bound power ups. try to steer away from pay2win gacha
> mechanics."*

**All hero power variance is match-bound.** `[committed]` Sourced from in-match
cards and in-match power-ups only. Nothing persistent, nothing purchased, no
gacha. This extends the existing fairness constraint from cards to heroes and
items, and it is the cleanest resolution the design has produced for the
"heroes differ in power" problem: within a match, power can move; across matches,
everyone starts level.

Consequence for 17: itemization may tier *inside* a match, never outside one.

## The loss-condition reversal

**Superseded — 2026-07-21 (recorded same day it was made).**

**Old:** hero death is the loss condition. `[provisional]` From the first dump:
*"that hero is the thing that causes you to lose the game when it dies."*

**Reversed by the user on spotting the contradiction themselves:**

> *"if your hero is doing things in the jungle autonomously but then your hero is
> also technically you behind the UI watching the map as an eagle eye view, then
> that really doesn't work."*

If the hero farms on its own while the player commands from overhead, the hero is
not the player's avatar — so its death cannot be the player's death without the
fiction breaking.

**New, leading candidates:** `[provisional]`

1. **Hero death is a temporary power-down** until it revives — a setback, not an
   ending. *"that's just like your down power until it revives."*
2. **Base destruction is the loss condition.** *"maybe it is just your base
   getting destroyed or something like that."*

These compose: heroes die and revive, bases end matches. That is also the Dota
lineage the map already commits to. Not settled — 05 owns closing it.

**The old version is kept above deliberately.** Per the map's append-only rule, a
reversal is recorded as a reversal, not a deletion.

## Still open

- **What differentiates heroes mechanically** beyond the six axes — how much is
  stat spread versus genuinely distinct behaviour?
- **What mana does**, if anything.
- **Where the hero is on screen** and how the player tracks it (01).
- **How autonomous "autonomous" is** — untouchable, or steerable with a flick?
- **What the hero does in the jungle**, concretely (12).
- **Whether hero unlocks exist**, and if so how they stay clear of the match-bound
  power constraint (06, 07, 14).

Interacts: 01, 05, 06, 11, 12, 14, 17, 18.

## Source — verbatim, both dumps

Kept unabridged. This ticket has been rewritten twice already, and the map's
standing rule is to build from the user's words rather than from a summary of
them. Paraphrase above; ground truth here.

**First dump (2026-07-21), which introduced heroes:**

> *"earlier I had an idea where before you would search for a match, you would
> choose a hero. Imagine there are eight heroes and these heroes all have
> different strengths and weaknesses. We have different amounts of armor, health,
> and mana and that hero is the thing that causes you to lose the game when it
> dies. That hero is also going to interact with the jungle but it will be
> automated. Perhaps that is how we can implement some sort of card combination
> type thing or in tandem with hero abilities. There are three or four preset
> combinations or cards that can be used where then your hero takes an action in
> the jungle that affects map state."*

**Second dump (2026-07-21), the heroes session:**

> *"Things that will separate heroes from one another will be: race, passives,
> size, weapons, style of attack (physical, melee, magic, ranged, blah blah blah,
> summoning), one novel thing that maybe can affect the map in some way."*

> *"Maybe they don't have mana but maybe they do. Maybe the cards affect the
> jungle but the hero still requires mana to use abilities."*

> *"What will kill a hero will be. It's a good one because if your hero is doing
> things in the jungle autonomously but then your hero is also technically you
> behind the UI watching the map as an eagle eye view, then that really doesn't
> work. Maybe the hero can die on the field and then that's just like your down
> power until it revives and maybe it is just your base getting destroyed or
> something like that."*

> *"Heroes will differ in power but they will differ in power. In terms of
> anything it'll have strengths but it'll have weaknesses. A melee guy will do
> tons of melee damage and not take a ton of damage but he'll be slow and he'll be
> weak too. Ranged and the same thing with casters: they'll be good at attacking
> melee people but if melee people ever get in range they're gonna get screwed.
> The typical stuff like that but we will attempt to ensure to do something
> novel."*

Note the last block contains the transcription garble discussed above
(*"he'll be weak too"* → read as *"weak to ranged"*) and a doubled clause
(*"differ in power but they will differ in power"*). Left as-is rather than
tidied, so the reconstruction stays auditable against the original.
