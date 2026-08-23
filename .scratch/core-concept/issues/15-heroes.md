# Heroes — stats, roles, and differentiation

Type: grilling
Status: open, substantially answered. **Rebuilt 2026-08-19/21 for two items
only:** heroes gain XP and level from the same jungle-creep and lane-minion kills
that pay gold, while what levels grant stays open; and the twice-revised
hero-weakening rule is recorded below. Hero selection, roster, controls, and
ability design are untouched by this pass.
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
- ~~**Where the hero is on screen** and how the player tracks it (01).~~
  **Answered 2026-07-26:** you pan the map like a MOBA observer and look at him.
  No fog, so he is always visible if you point the camera at him. The Hero Cam
  picture-in-picture from the napkin sketch may be unnecessary — unreconciled,
  see 01.
- **How autonomous "autonomous" is** — **largely answered later the same day; see
  "Standing orders" below.** The hero runs a **route/behaviour system with several
  modes** (farm, defend, assist lane, push): *"auto-programmed dynamic routes to
  farm creeps and maybe defend towers or help his lanes or attack at certain
  points"*, and — stated twice — *"you don't get to control your hero directly."*
- **Towers.** New on 2026-07-26, and **doubted the same day** — the user is wary
  of lane towers as MOBA copying, while wanting the *job* a tower does. See 05.

## Standing orders — 2026-07-26 `[provisional]`

> *"Maybe there is a way to cue very simple commands to the hero, like: left
> lane, mid lane, right lane, farm this part of the jungle, farm that part of
> the jungle. Something like that."*

**The player sets the hero's priority; the hero executes it autonomously.** This
answers the open question of whether anything influences the hero's *priorities*
as opposed to its power — cards do power, standing orders do priorities.

**It also resolves the fork this ticket originally posed:** *"How autonomous
'autonomous' is — untouchable, or steerable with a flick?"* Neither pole won.
The hero is **not untouchable** — you can redirect it — but it is not steered
either, and "with a flick" is dead on its own terms, since skill shots were
removed and flicks may not exist anywhere in the design. The answer turned out to
be a third thing: **coarse standing orders.**

**It is not a reversal of "you don't get to control your hero directly."** A
standing order is a destination, not steering: you say *mid lane*, you do not
walk him there, and everything between the order and the outcome stays automated.
Recorded explicitly because the two statements were made minutes apart and a cold
read could see a contradiction. **If the user did mean this to loosen the
no-direct-control rule, that needs saying.**

Convergences worth noting:

- It gives the **bottom command bar actual commands**, matching the Warcraft 3
  analogy that named *"action commands"* — the panel now has a second job beyond
  readouts.
- It pairs with 10's *"their goal"* readout: if the panel shows the enemy hero's
  current objective, and you set your own hero's objective, then orders and
  intent-reading are the same mechanic seen from both sides.

**Open within it:** how many orders exist, whether they are free or cost
something, whether the hero can refuse or delay, and whether an order is a mode
that persists or a one-shot instruction.

### ⚠ Hero control granularity now has a dependent — 2026-07-29

The open question *"how manually can the player manipulate the hero's
position?"* stopped being a hero-only detail. The win condition
([05](05-match-shape-win-condition.md)) hangs a structural choice off it:

> *"reinforcements will be 1 pool per side as of right now. If we choose, or if
> we end up deciding that you can more manually manipulate your hero's position,
> then maybe a pool per lane would make sense."*

**One pool per side is live; a pool per lane is conditional on this ticket
loosening.** That is a dependency, **not** a decision, and *"as of right now"* is
the user's hedge, kept.

**Also new here, and it must not be mistaken for that loosening:** one of the
three win-condition levers is **a card that puts your hero into a lane for ~10
seconds** to push it further, with farmed power-ups making the push harder or
letting him take less damage. That is a **card effect with a timer**, not manual
control — the hero still is not steered. Recorded explicitly because a cold read
could take "a card that moves my hero" as the direct-control rule having already
loosened. **It has not.** The rule stands: *"you don't get to control your hero
directly."*

This is also the first mechanism by which **farmed hero power reaches the win
condition** — indirectly, through how hard he can push a lane. See 05 and
[10](10-information-visibility.md).
- **What the hero does in the jungle**, concretely (12).
- **Whether hero unlocks exist**, and if so how they stay clear of the match-bound
  power constraint (06, 07, 14).

Interacts: 01, 05, 06, 11, 12, 14, 17, 18.

## Rebuild — 2026-08-19 / 2026-08-21: experience and hero weakening

### ✅ Heroes gain experience and level; the source mirrors gold `[provisional]`

> *"Heroes will definitely level, creeps will provide experience as well as
> minions."*

Heroes gain XP from **jungle creeps and lane minions**, on the same kills that
already pay gold. XP is a **second income stream riding existing kills**, not a
separate resource node or activity to farm. This closes the existence-and-source
half of `mg-hero-experience-and-levelling`.

### ❓ What levelling grants remains fully open

Whether a level grants **stat growth, ability unlocks, or something else** was
not answered and is tracked separately as `mg-hero-level-grants`. Nothing in
this rebuild chooses or narrows it.

### ⚠ Hero weakening — the final rule after a same-session walkback

The captain first stated an absolute rule: a hero could never be weakened by
anything except enemy hero spells or abilities, and those effects are
duration-based. **He then explicitly walked that absolute back in the next
dump.** The final, operative rule is:

- An **enemy hero's spells or abilities** may weaken a hero, duration-based.
- An **item's own debuff effect** may weaken a hero.
- **Terrain** may weaken a hero, including reducing **movement speed, damage, or
  accuracy**.
- **Gold and the merchant never weaken a hero directly.** The lane-targeted
  merchant idea is already covered by the existing hurt-their-lane terrain
  channels, not a hero debuff SKU; see 17.

**This is a genuine walkback, not a reinterpretation.** His later words reopen
items — *"if an item ends up having some sort of debuff, then sure, that can
affect it"* — and reopen terrain beyond movement friction to real combat-stat
debuffs.

### ❌ HoN uphill miss is rejected; general terrain accuracy reduction survives

The specific chance-to-miss-when-attacking-uphill mechanic is rejected as
*"just extra stuff not necessary for a MOBA game."* That narrow rejection does
**not** reverse the broader permission for terrain to reduce accuracy; the two
are distinct and recorded that way.

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
