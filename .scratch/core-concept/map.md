# Map: Core Concept

Label: `wayfinder:map`

## Destination

A game design concept doc covering combat, map, progression, and monetization —
deep enough to build a vertical-slice prototype from, and to judge whether this
is worth committing to.

## Working method

**Adopted 2026-07-21, replacing sequential grilling.**

1. Pick one ticket.
2. The user word-dumps everything they think about it — no question sequencing,
   no multiple choice.
3. The dump is used to **rebuild this map**, including whatever it touched
   outside that ticket's borders.
4. Understanding is confirmed back to the user.
5. The user says proceed, or corrects.

**Why, in the user's framing:** *"game development cannot be linear. It's left,
right, up, down, in, out, because decisions change."* A ticket graph with
blocking edges assumes settled decisions stay settled. They don't here. So the
map is rebuilt rather than traversed, and rebuilding is the normal operation —
not a cleanup that eventually stops being necessary.

**Why sequential grilling was dropped:** the user, on being asked question 1 of
5 — *"you ask a single question and my brain forks a thousand times."* Depth-first
questioning assumes a tree. This design is a graph where every node touches every
other node, so each question kept landing on unresolved dependencies and spawning
forks. One dump conveyed more design than five sequenced questions had.

### The rule that makes rebuilding safe

**Rejections are append-only.** Every rebuild carries forward every recorded
"no," with its reason, even when the new dump doesn't mention it. A reversal must
be flagged *as* a reversal, in the user's words — never a silent deletion.

This is not hypothetical caution. Rebuilding from a compressed summary is exactly
how the v1 prototype shipped a tug-of-war bar the user had rejected twice: the
summary had dropped the correction. A rebuild reconstructs from the newest input,
and what it silently loses is the old "no," because closed questions stop coming
up.

The repo is under git as of 2026-07-21. **One commit per rebuild** — every prior
map version stays recoverable and diffable.

## Notes

**Domain:** real-time mobile lane-battler with compound spellcasting, a chosen
hero, and a constructed deck.

**Skills to consult:** `/grilling` for structure when a ticket needs it,
`/prototype` for anything with a "how should this feel" core, `/domain-modeling`
as vocabulary settles. Note `/wayfinder` is referenced by `CLAUDE.md` but is not
currently installed.

### Locked constraints — do not re-litigate without saying so explicitly

> **Standing caveat, in the user's words (2026-07-29):** *"Just to confirm.
> Everything that I say is always open to change. Let's make that clear."*
> Filed here because this is where a future rebuild looks for what is fixed.
> Nothing in this map is a lock unless it is explicitly marked as one — the
> `[committed]` tags and this section are the marks. Everything else, including
> everything tagged `[provisional]`, is open. This does **not** weaken the
> append-only rule: a change is still a **reversal, flagged as one, in the
> user's words** — the caveat says decisions may change, not that records may
> vanish.

- Real-time, **cooldown-based**. No turns. Cards accrue on a timer.
- Three lanes on a **Dota-shaped** map — bending lanes, forest/jungle, terrain
  that matters — scaled for a phone. Explicitly *not* Clash Royale's bare tracks.
- **Automated creeps** march and contest lanes. Players influence lanes; they do
  not directly command an army.
- **Creeps are units, not a meter.** The front line emerges from individual
  creeps fighting. A tug-of-war bar or fill-percentage has been **rejected
  twice** — do not reintroduce it.
  - **⚠ Language trap, filed 2026-07-26.** The user described the strategic
    dynamic as *"you're trying to have that tug of war, right? Make your lanes
    and heroes stronger than they are."* **This is not a reversal.** "Tug of
    war" there names the back-and-forth *contest* — the thing three lanes of
    fighting creeps produce — not a bar, meter or fill-percentage. The rejection
    is about the **abstraction**, never the word. A future rebuild reading that
    quote cold could easily mistake it for permission. It is not.
  - **⚠ Second language trap, filed 2026-07-29.** The win condition is now a
    **reinforcement pool** that drains as creeps die. **This is not the rejected
    meter.** The rejected thing was a bar that *stands in for the front line*.
    The pool counts **how many creeps are left to spawn**; the front line is
    still produced by individual creeps fighting, and nothing about it is
    abstracted. Two different objects that are both numbers. Not permission to
    abstract the lane.
- Core loop: accrue cards → **combine into a compound spell** → **select a
  target**. **Casting is selection, not performance.** `[committed]` **Reversed
  2026-07-26** from *"gesture to cast → aim into a lane"*; see the reversal log.
- **Four target classes** `[provisional]` (2026-07-26): *"either help your hero,
  help your lane, hurt their lane, or slow down their hero. That's the gameplay
  loop."* Note this is the first statement that cards target the **enemy** side —
  their lane and their hero — not just your own. Effects are described as
  in-lane or in-jungle.
- **No fog of war** `[provisional]` (2026-07-26). *"there won't be any fog
  because we need to see their hero to be able to choose what we're going to do
  to negatively affect it."* Forced by the targeting model: you cannot select
  what you cannot see. Answers the spatial half of 10.
- **Gestures are never drawn symbols.** No tracing shapes to cast. Physical and
  fast, not notational. This rejection survives the skill-shot removal and binds
  *any* touch interaction the design adopts. **But its scope is now open:** with
  casting reduced to selection, whether flick/drag gestures remain anywhere at
  all — combining, hero steering — is unanswered. See "Not yet specified."
- **All hero power variance is match-bound.** `[committed]` *"if power can change
  on heroes at all from weapons or stats, it will come from in game cards or
  match bound power ups. try to steer away from pay2win gacha mechanics."* No
  persistent power, no purchased power, no gacha. Extends the card fairness
  constraint to heroes and items. (2026-07-21)
- **No comeback mechanic may reward deliberate losing.** `[committed]`
  (2026-07-26) *"people don't just purposely lose in order to get them to get
  free things because it lets them snowball in reverse."* Comeback dynamics are
  required, but every candidate must be tested against a player throwing on
  purpose to farm it. This rules out the naive forms of the usual designs — flat
  behind-bounties, catch-up gold, underdog buffs — unless shaped so losing costs
  more than the bonus returns.
  - **The test that came out of it** (2026-07-26): **preventive beats
    restorative.** A device that applies to both players from the opening
    whistle and stops a snowball *starting* gives a thrower nothing. A device
    that pays out in proportion to how badly you are doing is what a thrower
    farms. Pseudo-towers are explicitly the first kind — *"a way to just stall
    the game"*, not a comeback.
- **The hand is hidden; the board is not.** `[provisional]` (2026-07-26) *"you
  won't know what cards they have. Maybe you can't know how they are able to
  manipulate the field."* Settles the drift 10 was showing: everything about the
  **battlefield** is calculable, everything about the opponent's **options** is
  not. You always see what is happening, never quite what is coming.
- **The jungle must be mechanically live, not scenery.**
- **When accessibility and novelty conflict, accessibility wins.**
- PvE and PvP are both intended modes.
- **All cards are obtainable by every player. None are purchase-exclusive.** Not
  all unlocked on day one.
- Monetization must be light and genuinely non-resented.
- **Item slots are never filled pre-game.** *"I don't want them to be filled
  pre-game."* Items are an in-match economy. (2026-07-21)
- **Large combinatorial recipe tables stay rejected** — authoring cost and
  opacity. Amended 2026-07-21 to permit a *small fixed set* (3–4, few
  ingredients, taught). The rejection was always about scale; see 02's amendment.

### ✅ Resolved challenge — skill shots removed (2026-07-26)

**The challenge filed 2026-07-21 was resolved by removal.** Asked directly
whether skill-shot casting exists at all, the user: *"remove it."*

The constraint it challenged is **reversed**. Cards act on a selected target — a
lane, the jungle, or the hero — so casting is **selection, not performance**.
Ticket 03 loses its subject and closes; its file is kept as the record, not
deleted.

**What this costs, recorded now so it is not rediscovered later as a surprise:**
the gesture was the only proposed home for *execution* skill. Player skill now
lives entirely in selection, timing, combining and deckbuilding — a more
accessible game and a flatter one. The trade was made knowingly. Where (or
whether) execution skill returns is now an open question owned by 04 and 06.

Both 2026-07-21 quotes are preserved verbatim in the reversal log below and in
[03](issues/03-gesture-skill.md).

### ✅ Resolved challenge — the protest on "destroy their base" is lifted and narrowed (2026-07-29)

**The challenge filed 2026-07-26 is resolved by narrowing.** It was recorded as
*the user does not want the win condition it currently has*. That was wider than
the objection actually is. **This is a reversal of the recorded status and is
flagged as one**, in the user's words:

> *"So the issue that I have with the base dying being the win condition. It's
> just that every game does it."*

> *"while I want there to be a base because there needs to be logic like where
> are the minions with the creeps coming from? I don't necessarily want - the
> base can be the thing that dies. I guess that's fine. I just don't want it to
> be the prototypical way of you push the minions through three towers through
> like a barracks or something for powered up minions and then destroy more
> towers to reach a core, right? Like that's how everyone's always done it."*

- **Not rejected:** the base being the thing that dies. *"I guess that's fine."*
- **Rejected** `[committed by explicit rejection]`: the **prototypical route** —
  creeps through three towers → barracks for powered-up creeps → more towers →
  core. *"that's how everyone's always done it."*

**What this section said before, kept verbatim so the narrowing is diffable
without leaving the map.** It read: *"**The user does not want the win condition
it currently has**, and said so while answering a different ticket"* —

> *"you can eventually, I guess, destroy their base. I don't really want it to be
> 'destroy their base' so maybe there's something else that can be thought of
> later on just because that's so prototypical."*

— *"**Status: dissatisfied, deferred, not decided.** Base destruction stands as
the `[provisional]` answer because nothing has replaced it — but it is now
explicitly **held under protest** rather than settled, and this is the second
time the loss condition has moved (see the reversal log). The objection is
*genre-fatigue*, not mechanics: it works, it's just the obvious thing. Filed here
rather than quietly in 05 because the same design has now discarded hero-death
*and* soured on base-destruction, which means the match's ending is one of the
least settled things in the concept while reading like one of the most settled."*

That filing judgement was right and is worth keeping: the ending has now moved
**three** times. The full protest text also lives in
[05](issues/05-match-shape-win-condition.md). It is not deleted, and it is not
still live at its original width.

**⚠ Do not extend this cascade.** The rejection reaches the **tower chain as a
win path** and stops there. **Pseudo-towers are untouched** — they are on record
as a stall/pacing device explicitly on the preventive side of the
deliberate-losing rail, and a scaling gate that stops an early bulldoze is a
different object from a link in a destruction sequence. The map already carries a
"don't over-extend a cascade" gotcha, learned from a retraction. **Owned by 05.**

### Reversal log

Decisions that were recorded and then changed. Kept so the old version cannot be
silently re-adopted.

- **Skill-shot casting** (challenged 2026-07-21, **removed 2026-07-26**)
  `[committed]`. Was: *casting is skill-based execution — accrue → combine →
  gesture to cast → aim into a lane*, a locked core-loop constraint. Now:
  *casting is selection — a combined spell acts on a chosen lane, the jungle, or
  the hero.* **Why, in the user's words:** *"If the cards can affect the jungle
  and the cards can affect the lane and the cards can affect your hero, then we
  don't necessarily need to add in the user having to skill shot something
  there"*, and *"I'm thinking about omitting it entirely because of the added
  layer of complexity it'll already add on top of everything else."* Confirmed
  2026-07-26: *"remove it."* Closes ticket 03. Note this is the **first
  simplification** the design has taken — every other 2026-07-21 decision added
  systems.
- **Loss condition** (2026-07-21, reversed same day). Was: *hero death ends the
  match.* Now: *hero death is a temporary power-down; base destruction ends the
  match* `[provisional]`. **Why:** the user spotted that an autonomous
  jungle-farming hero plus an overhead commander camera means the hero is not the
  player's avatar, so its death cannot be the player's defeat. The camera
  decision (01) determined the win condition — worth remembering as an example of
  how non-linear this design is.
- **The protest on base destruction** (filed 2026-07-26, **narrowed and lifted
  2026-07-29**). Was: *the win condition is held under protest; the user does not
  want it.* Now: *base destruction as an ending is fine; the prototypical
  tower-chain route to it is rejected.* **Why, in the user's words:** *"the base
  can be the thing that dies. I guess that's fine. I just don't want it to be the
  prototypical way of you push the minions through three towers through like a
  barracks or something for powered up minions and then destroy more towers to
  reach a core... that's how everyone's always done it."* This is the **third**
  time the match's ending has moved. Scope: the win *path*, not pseudo-towers.
- **Hero-only-after-exhaustion** (filed 2026-07-29 as an open question,
  **disowned 2026-08-07**). Was: *"once you run out of reinforcements, then your
  base doesn't spawn anymore minions or something, and then all you have is your
  hero. I don't know"* — held open as "is that a loss, or an endgame state?"
  Now: the user **no longer recalls or endorses that framing**, and the loss
  condition is **the enemy hero reaching their goal** — sketched 2026-08-09 as a
  **Warcraft 3-style power threshold**. **⚠ No verbatim quote survives from the
  2026-08-07 session**: it was recorded as a decision note, and the phrasing
  above is the note's, not his. Flagged that way rather than dressed up as a
  quote. **Scope:** this disowns the *framing*, not the reinforcement pool and
  not the three levers; whether exhaustion still ends a match is **unstated and
  open**. The fourth time the match's ending has moved. See
  [05](issues/05-match-shape-win-condition.md).
- **Three win conditions → one win condition with three levers** (2026-07-29).
  Was, in this map's reading: *terrain manipulation, hero power and
  reinforcements are three separate candidate win conditions.* Now: **one
  scoreboard — the reinforcement pool — with three levers on it.** *"I'm OK
  currently with having those 3 levers on the one win condition."* Recorded as a
  reversal of the map's reading rather than of a user decision, because the
  three-separate framing was the map's, not his.
- **Banking** (2026-07-21) — shelved, not rejected. See below.
- **Recipes** (2026-07-21) — narrowed, not reversed. See 02's amendment.

### The central risk

**Design against it, not around it:** combining is deliberate and puzzle-like;
real-time is pressure. Those two fight each other. **Ticket 04 owns this.**

It got materially worse on 2026-07-21. Heroes, items, gold and deckbuilding all
add things to know and things to watch, and every one of them spends the same
budget the combining mechanic needs. 18 exists because of this.

**It got better on 2026-07-26 — the first time.** Removing skill shots takes an
entire execution layer out of the moment where combining is already asking the
player to think under a clock. That was the sharpest instance of the deliberate
-vs-pressure conflict: a puzzle decision immediately followed by a dexterity
test. It is gone. 04's problem is now smaller and more purely cognitive.

### Superseded principles — kept deliberately, not deleted

- **"Ordering principle: resolve what constrains before what adapts."**
  Superseded by the working method above. It assumed a stable dependency graph;
  the 2026-07-21 dump answered 05, 12 and 09 while nominally addressing 09 alone.
  Kept because if the non-linear method fails, this is what it replaced.
- **"Known keystone: ticket 02."** Retired on 02 resolving. There is no single
  keystone now; 04 and 18 are the closest equivalents.
- **"Standing preference: rabbit-hole each ticket in depth."** Still true in
  spirit — the depth now arrives as a word dump rather than an interrogation.

### Process constraints, learned the hard way

**Build from the user's words, not from this map's summary.** The v1 prototype
rebuilt a rejected mechanic because the agent worked from a compressed gist
instead of the transcript. A summary is lossy exactly where a correction lives.

**Prototypes must be observed running.** The first prototype was unusable from a
render bug no syntax check could catch. With no browser available, say plainly
that the artifact is unverified rather than implying it works.

**A prototype cannot test feel until it is teachable and survivable.** Ship a
guided first run and a passive-by-default opponent, and label crude parts as
crude. Otherwise "unintuitive" measures the missing tutorial and the beating, not
the mechanic — and must not be recorded as design evidence. This already happened
once, on ticket 13.

**Don't over-extend a cascade.** Corrected by the user, 2026-07-26. After skill
shots were removed the agent proposed that terrain's job had shrunk and that
bending lanes had lost what paid for them — reasoning that geometry mattered
mainly because projectiles travelled through it. Wrong: *"you're referencing the
skill shots of the user from the cards as opposed to what the heroes or the
creeps might do."* **Terrain and lane shape are paid for by hero and creep
movement, pathing, sightlines and combat** — none of which the card change
touched. The removal was scoped to *player card targeting* and nothing else.
Sibling error to over-reading a rough artifact: both invent implications the
source never carried.

**Explore-then-commit:** for any ticket whose answer cascades, put candidates on
the table and trace each forward through the tickets it affects *before* choosing.

**Reversibility rail:** decisions are tagged `[committed]` or `[provisional]`.
Provisional means good enough to build the next ticket on, not yet load-bearing.
Most decisions should stay provisional for most of this map's life — tag honestly
rather than performing certainty. Ticket 08 promotes or revises.

## Decisions so far

- [What "combining cards" actually means](issues/02-combining-mechanic.md) —
  at-cast combining is **payload + modifiers** `[provisional]`; accessibility
  beats novelty `[committed]`; shape-composition dead once gestures were ruled to
  be flicks not drawn symbols `[committed]`; large recipe tables rejected
  `[committed]`, **amended 2026-07-21** to allow 3–4 taught recipes
  `[provisional]`.
- [Prototype — sixty seconds of a match](issues/13-prototype-sixty-seconds.md) —
  mostly **failed as a feel test**, which is the finding. Creeps must be units
  not a meter `[committed]`; 60s far too short `[provisional]`; the bank was the
  only positive signal `[provisional]`. "Unintuitive" was **confounded** by no
  tutorial + crushing AI + crude mock and says nothing about combining — the
  earlier contrary claim is retracted.
- **The loss condition is the enemy hero reaching a power threshold**
  `[provisional]` (2026-08-09) — **the ending has now moved a fourth time.** You
  lose when the **enemy hero reaches their goal**, and the goal is a **Warcraft
  3-style hero power threshold**: units and structures matter, but nothing
  compares to the hero once it is strong enough, and past the threshold it no
  longer needs to farm and can go win outright. Power accrues through mechanics
  already in the design — **defending forward-structure events**, **killing lane
  creeps** when the hero is sent to a lane, and **jungle creeps/items**. His
  framing, **verbatim and load-bearing**: *"the whole game is preventing your
  opponent from maximizing that power journey while maximizing your own."*
  **The user flagged the specifics himself as still wishy-washy** — whether the
  threshold is a **hard gate** or a **continuous curve**, and how it is tuned
  against the assumed 15-minute match, are **open**. **This reframes
  [12](issues/12-jungle-role.md) and the forward-structure economy as the levers
  of that race** rather than as separate systems; 12 is not rebuilt here.
  **Relationship to reinforcement exhaustion, stated precisely because a cold
  read will get it wrong:** what was disowned is the *hero-only-after-exhaustion
  framing* (see the reversal log), **not** the pool or its three levers, and the
  user **did not say** whether running out of reinforcements still ends a match.
  That is **open**, not answered either way. See
  [05](issues/05-match-shape-win-condition.md).
- **Match length is assumed ~15 minutes, with a lane event roughly every 5
  minutes** `[provisional]` (2026-08-09) — each event bounded to something quick
  to resolve. The first answer 05's "match length" question has had.
- **What the forward structure does — answered by the user's own candidate**
  `[provisional]` (2026-08-07, extended 2026-08-09). Forward structures sit
  **dormant** and **activate** on an interval (time, or reinforcement-pool), with
  either a pre-set ability or a TFT-augment-style pick-1-of-N. The hero may
  **enter one and garrison it**, at which point it stops acting as a normal hero
  and operates a **different ability set**, contextual on lane, match time, and
  **which cards were spent beforehand to prep the structure** — the user leaned
  toward this bolstering the **structure**, not the hero. **The cost is that it
  pulls the hero off the map.** His own flagged risk — that garrisoning becomes a
  **forced tax** if the opponent picks the timing — is addressed on 2026-08-09 by
  a **telegraphed event system**: both players get **simultaneous notice** of an
  event in a specific lane and each **independently** chooses whether to defend,
  because the trigger is a **shared schedule**, not opponent whim. **Losing a
  structure costs map control, not a direct penalty** — enemy creeps push closer
  to your base, cramping how far your hero can safely roam your own jungle.
  **One structure per lane for now**; multi-structure **step-down defence lines
  are deferred to playtesting, not rejected.** **Garrison abilities must stay
  card-selected, never direct hero piloting** — that is the `[committed]`
  commander framing. **The two rejected candidates (guards, vicinity buffs) and
  the user's test stand untouched**; see "Not yet specified" below for what is
  still open, including a **live cut candidate**. See
  [05](issues/05-match-shape-win-condition.md).
- **The win condition is reinforcement exhaustion** `[provisional]` (2026-07-29)
  — *"you have reinforcements and so like you only live as long as you have
  reinforcements. And maybe it can be something like once you run out of
  reinforcements, then your base doesn't spawn anymore minions or something, and
  then all you have is your hero. I don't know."* Reference is a **World of
  Warcraft battleground**, hedged (*"I can't remember where it was, maybe"*).
  The user's hedges are part of the record: whether hero-only-after-exhaustion is
  a **loss** or just an **endgame state** is explicitly unanswered. The base
  survives — it is where creeps come from, and it may still be the thing that
  dies. What died is the tower-chain route. See
  [05](issues/05-match-shape-win-condition.md).
  - **⚠ Updated 2026-08-07/09, kept above rather than rewritten.** The
    **hero-only-after-exhaustion framing is disowned** (reversal log above), and
    the **loss trigger is now the enemy hero's power threshold** — see the entry
    above this one. The **pool and its three levers are not deleted**; what the
    user did **not** say is whether exhaustion still ends a match. Open.
- **One win condition, three levers on it** `[provisional]` (2026-07-29) — *"I'm
  OK currently with having those 3 levers on the one win condition."* The levers:
  **(1)** baseline drain as your own creeps die; **(2)** **terrain manipulation**
  — a black-hole-class spell that eats their creeps in a lane and costs them
  *extra* reinforcements; **(3)** **hero intervention** — a card that puts your
  hero in the lane for **~10 seconds** to push it further, with farmed power-ups
  making the push harder or more survivable. This **replaces the map's earlier
  reading** that terrain, hero power and reinforcements were three *separate*
  candidate win conditions. **Consequence for [18](issues/18-slice-sequencing.md):
  one win condition is one thing to teach, not three.** It also gives
  [10](issues/10-information-visibility.md)'s enemy-hero readouts a possible
  *win-condition* reason to exist, beyond the card-decision one.
- **The reinforcement pool is one per side** `[provisional]` (2026-07-29) —
  *"reinforcements will be 1 pool per side as of right now."* **A pool per lane is
  a live alternative and it is conditional**, not deferred: *"If we choose, or if
  we end up deciding that you can more manually manipulate your hero's position,
  then maybe a pool per lane would make sense."* That is a **dependency on an
  open question** — hero control granularity, owned by [15](issues/15-heroes.md)
  (currently coarse standing orders, *"you don't get to control your hero
  directly"*) — **not a decision**. It also gives
  [01](issues/01-battlefield-geometry.md)'s open target-*resolution* question a
  stake it did not have: a per-lane pool makes lane identity load-bearing for the
  win condition. Note the hero-intervention lever is a card effect with a timer,
  **not** manual control, so it does not by itself meet the condition.
- **Terrain manipulation is the leading objective candidate** `[provisional]`
  (2026-07-26) — players reshape the battlefield (*"create more water, create
  lava, or create holes in the ground"*) to impede enemy creeps and heroes. The
  best answer this design has produced for "an objective that isn't a copied MOBA
  objective," and it makes terrain mechanically live without needing skill shots.
  **⚠ It may also have handed [09](issues/09-banking-mechanic.md) the payoff that
  got banking shelved — unresolved, see below.** See
  [05](issues/05-match-shape-win-condition.md). **Updated 2026-07-29:** it is no
  longer a candidate *objective* in its own right — it is **lever 2 on the one
  win condition**, and the user's dangling 2026-07-26 hint (*"maybe that can
  somehow affect what the overall win condition is"*) is answered: it drains the
  enemy reinforcement pool faster than baseline attrition does.
- **The player gives the hero standing orders** `[provisional]` (2026-07-26) —
  *"left lane, mid lane, right lane, farm this part of the jungle, farm that part
  of the jungle."* Cards influence the hero's **power**; standing orders
  influence its **priorities**. Not a reversal of *"you don't get to control your
  hero directly"* — an order is a destination, not steering. See
  [15](issues/15-heroes.md).
- **PvE and PvP share one match shape** `[provisional]` (2026-07-26) — *"the same
  thing, just human versus AI."*
- **Hero death costs nothing; buybacks are limited** `[provisional]`
  (2026-07-26) — death is a respawn timer, not a penalty. One or two buybacks per
  match pay a price for an instant return. See 05.
- **The camera is a pannable MOBA observer** `[provisional]` (2026-07-26) —
  *"almost like you're an observer in a MOBA... you use your finger to pan around
  the map but you don't get to control your hero directly."* The map is **larger
  than the screen** and you drag to move around it; there is no fixed whole-map
  view. This answers "how much of the map is visible at once" by making it a
  navigation question instead of a fitting one, and it **defuses the angled-view
  legibility problem** — a far lane that reads poorly can be panned to. See
  [01](issues/01-battlefield-geometry.md).
- **Screen split: Warcraft 3, zoomed out** `[provisional]` (2026-07-26) — **top
  ~75% is the pannable map viewport**, bottom ~25% is an RTS-style command bar
  holding *"the card stuff"* and readouts on **both** heroes. Confirmed to be a
  **screen split, not a board layout** — the jungle's position on the
  battlefield is still open. The WC3 analogy mentions *"your selectable army"*;
  that describes **WC3's** bar, not a proposal for commandable units, and does
  not touch the locked no-direct-army-command constraint.
- **Cards must be judgeable against visible battle state** `[provisional]`
  (2026-07-26) — the design's first stated UI *purpose*. *"That way you can
  better make decisions on whether you should use your cards to attempt to slow
  their hero down, speed your hero up, or attack their lanes... That makes the
  information on the cards relevant to the state of battle."* The bottom bar is
  the **decision substrate**, not a HUD. This binds card design as much as
  layout: a card whose value cannot be read off visible state is a card the
  player guesses with. Acceptance test in [01](issues/01-battlefield-geometry.md).
- **Skill-shot casting is removed; casting is selection** `[committed]`
  (2026-07-26) — a combined spell acts on a chosen lane, the jungle, or the hero.
  Reverses a locked core-loop constraint at the user's explicit instruction
  (*"remove it"*). Closes [03](issues/03-gesture-skill.md); simplifies
  [01](issues/01-battlefield-geometry.md)'s aiming surface; removes one system
  from [18](issues/18-slice-sequencing.md)'s count. Leaves execution skill
  homeless — see "Not yet specified."
- ~~**Hero death is the loss condition**~~ — **reversed same day**, see the
  reversal log. Now: hero death is a temporary power-down, base destruction ends
  the match `[provisional]`.
- **The hero works the jungle, automatically** `[provisional]` (2026-07-21) — see
  [15](issues/15-heroes.md), [12](issues/12-jungle-role.md).
- **The camera is a first-person UX layer over a slightly angled overhead
  battlefield** `[provisional]` (2026-07-21) — explicitly not straight-down. The
  hero is visible on the field; the jungle runs visible events. The player is a
  commander, not an avatar. See [01](issues/01-battlefield-geometry.md).
- **Hero differentiation is asymmetry, not power level** `[provisional]`
  (2026-07-21) — race, passives, size, weapons, attack style, plus one novel
  map-affecting mechanic each. Rock-paper-scissors: casters and ranged beat
  melee, melee wins once it closes. See [15](issues/15-heroes.md).
- **Orientation is portrait, 1080×2400** `[provisional]` (2026-07-21) — from the
  first layout sketch (`sketches/01-layout-portrait-v1.png`). Only the
  orientation is decided; lane shape, jungle placement and the hero-visibility
  approach are all still open. The sketch is a napkin — do not read anything else
  into it. See [01](issues/01-battlefield-geometry.md).
- **~100 cards, ~20 brought per match; all deck cards available in-match**
  `[provisional]` (2026-07-21) — see [16](issues/16-deckbuilding.md). This killed
  higher-tier merging as banking's payoff.

## Ticket index

Rebuilt 2026-07-21. Blocking edges are weaker than they look — see the working
method; treat them as "this informs that," not as a build order.

| # | Ticket | Status |
|---|---|---|
| 01 | Battlefield geometry & phone readability | open, **substantially answered** — pannable observer camera, no fog, screen split |
| 02 | What "combining cards" actually means | resolved + amended |
| 03 | Gesture as skill expression | **closed — removed** 2026-07-26 |
| 04 | Pressure vs. complexity — the learning curve | open, **eased**; now owns "where does skill live" |
| 05 | Match shape & win condition | open, **substantially answered**; **the ending moved a fourth time 2026-08-09** — loss is the **enemy hero reaching a WC3-style power threshold**, specifics wishy-washy by his own account; **the forward structure's job is answered 2026-08-07/09** (dormant structures, telegraphed lane events, hero garrison) with its specifics open; reinforcement exhaustion and its three levers are **not deleted** but exhaustion's standing as a loss trigger is unstated; ~15-min match, ~5-min event cadence |
| 06 | Unlock progression & the hook | open, **needs revisit after 16** |
| 07 | Monetization model | open |
| 08 | Consolidation pass | open (terminal) |
| 09 | Banking — combining over time | **shelved** — **⚠ may have found its payoff** 2026-07-26, awaiting user yes/no |
| 10 | Information — what you see of your opponent | **largely answered** — board open, hand hidden; partial-visibility detail still open; **new 2026-08-07 (from 05): the command bar should centre on the enemy hero's status** — recorded, not rebuilt |
| 11 | Card accrual economy | open |
| 12 | The jungle — role and autonomy | open, updated — playable space, not a wall, aggro leash; **reframed 2026-08-09 by 05** as one of the levers of the hero power race (jungle creeps/items feed the threshold), not a separate system — recorded there, not rebuilt here |
| 13 | Prototype — sixty seconds of a match | resolved |
| 14 | Pre-match setup & the pre-game state | open, **new** |
| 15 | Heroes — stats, roles, differentiation | open, **substantially answered**; standing orders added 2026-07-26 |
| 16 | Deckbuilding — 100 cards, bring 20 | open |
| 17 | Gold and items — the in-match economy | open, **flat-vs-tiered fork** |
| 18 | Slice sequencing — what ships | open, **new**, standing gate |

## Not yet specified

- **Banking — shelved 2026-07-21, not rejected.** *"Just shelve it for now. If we
  ever think of a way to make it reasonable or good then we can come back to
  it."* The shape survives and is still the best fit the design has produced for
  the accessibility constraint; it has no payoff attached, and after heroes,
  items, gold and deckbuilding it was judged *"extra clutter."* Four candidate
  uses preserved in 09. Do not treat as a locked "no"; do not reintroduce
  unprompted.
- **The ultimate.** *"I do like the ultimate idea"* — wanted, but no longer
  banking's payoff. Currently homeless.
- **What mana does.** Heroes have mana; cards cost none. Live candidate: cards act
  on jungle/lane/hero, mana is what the *hero* spends on its own abilities. Not
  chosen, and whether mana exists at all is still open.
- **Flat vs. tiered itemization.** One greatsword at 5 differentiated by attack
  speed, or greatswords at 5/6/7 that can be found and upgraded? Decides whether
  heroes differ laterally or vertically. Owned by 17, constrains 15.
- **Where execution skill lives now — or whether the design accepts having
  none.** Opened by the 2026-07-26 removal. Skill currently lives in selection,
  timing, combining and deckbuilding, all of them *cognitive*. Whether that is a
  deliberate identity ("a commander game, not a dexterity game") or a gap needing
  a replacement is undecided. Owned by 04, touches 06.
- **Target *resolution*, as opposed to target class.** 2026-07-26 answered
  *what* you target — your hero, your lane, their lane, their hero, the jungle —
  but not at what **granularity within** one. Does a lane-targeted spell hit the
  whole lane, or a spot in it? The pannable no-fog camera makes a point-target
  now *technically* available (you can see and touch any pixel of the map), so
  this is a live choice rather than a constraint. Owned by 01. **The earlier
  worry that lane-granular targeting reduces the board to three buttons is
  substantially answered** — panning, no fog, and enemy-hero targeting keep
  spatial reading in the game regardless. **New stake, 2026-07-29:** if the
  reinforcement pool ever goes per-lane, lane identity becomes load-bearing for
  the *win condition*, not just for card effects. That does not answer this
  question; it raises its price. See 05.
- **How manually the hero's position can be manipulated.** Owned by
  [15](issues/15-heroes.md) — currently coarse standing orders, *"you don't get
  to control your hero directly."* **Promoted from detail to dependency
  2026-07-29:** the per-lane reinforcement pool is explicitly conditional on this
  loosening. A card that puts the hero in a lane for ~10 seconds exists as a
  win-condition lever, but it is a card effect with a timer, **not** manual
  control, and does not meet the condition.
- ~~**What replaces "destroy their base."**~~ **Answered 2026-07-29** —
  reinforcement exhaustion, one condition with three levers. The base was never
  the problem; the tower-chain route was. See the resolved challenge above and
  05.
- **What the main base is for, if creeps spawn forward.** `[open]` 2026-07-29.
  The base's stated job is *"where are the minions with the creeps coming
  from?"* — creeps need a source. But the user also floated creeps spawning at
  forward positions where the outer towers would be, *"and so no minions actually
  flow through the lane."* **If they spawn forward, the main base has no stated
  job left.** Recorded as an open question, not a defect — the forward-spawn
  version is not chosen. 05.
  - **Partly answered 2026-08-09.** The forward structure turned out to be an
    **event/garrison structure**, and nothing in either August dump has creeps
    spawning from it — losing one lets **enemy creeps push closer to your base**,
    which describes a lane they travel, not a spawn point that replaced the base.
    **Whether the forward-spawn variant is dead or merely unmentioned is not
    stated**, and is not inferred here. Separately, in-progress work outside this
    map gives the base a **candidate second job — a global upgrade tech-tree**
    (funding possibly a TFT-augment-style pick-1-of-N at fixed checkpoints, still
    open; one sub-question settled: *"units"* there means **creeps only, hero
    excluded**). That is its own subject, noted here only because it bears on the
    base's job.
- ~~**What the forward structure DOES.**~~ **Substantially answered 2026-08-07 /
  2026-08-09** by the user's own candidate — dormant structures activated by a
  telegraphed, symmetric, scheduled lane event, garrisonable by the hero with a
  card-prepped ability set. See the decision entry above and
  [05](issues/05-match-shape-win-condition.md). **The rejections and the test are
  carried forward unchanged and still govern:** both of the user's own earlier
  candidates were **rejected by him on the same grounds** — guards *"just makes
  it a tower"*, and vicinity buffs are *"just a defensive tower structure, just a
  different kind. It just delays your opponent from getting in the lane."* **The
  test that came out of it** `[committed]`: *"I want to change how it makes your
  units interact with the game, not simply just make it take your units longer to
  get to the core."* Delay is not a mechanic; interaction change is. **He did not
  restate that test against the new candidate** — recorded in 05 as unstated, not
  as passed. The four firstmate-proposed candidates remain in 05 as **proposals
  he never reacted to** — not his, not accepted, none of them live; a later
  research report added eight more and likewise chose none.
- **What is still open inside the forward structure.** `[open]` 2026-08-09 —
  the **concrete list of event types** beyond his two named examples (killing a
  large unique minion; a structure-ability defence), the **exact event timing
  offsets** within the assumed 15 minutes, and the **defend-bonus design** (a
  bonus for defending successfully, versus merely avoiding the loss — floated,
  undecided). **Deferred, not rejected:** multi-structure **step-down defence
  lines**, held until playtesting shows real match length and map size. 05.
- **⚠ Live cut candidate — hero strength affecting structure power.** `[open]`
  2026-08-09. It is **in tension** with **card-selected-only garrison
  abilities**, and the user **agreed the concern is real** rather than dismissing
  it. **Neither side is chosen; do not resolve this by picking one.** A second,
  independent watch-item from the same session: the **card-based prep/customisation
  portion adds its own balance surface** to design and test. 05.
- **What crossing the hero power threshold concretely means.** `[open]`
  2026-08-09 — a **hard gate** that flips the hero into a win-capable state, or a
  **continuous power curve** with no sharp line; and **how it is tuned** against
  the assumed 15-minute match and ~5-minute event cadence, so games neither end
  in an early blowout nor drag on past the threshold with no resolution. **The
  user called the specifics wishy-washy himself.** Also open: **what becomes of
  reinforcement exhaustion as a loss trigger** now that the threshold is the loss
  condition — unstated. 05.
- **Towers/structures.** Appeared for the first time on 2026-07-26 — the hero
  *"may defend towers."* Nothing else about them exists: whether they shoot,
  whether they gate lane progress, whether they are the thing that gets destroyed
  instead of a base. **Narrowed 2026-07-29:** the tower *chain* as a win path is
  rejected, and the forward-structure question above is the live form of this.
  Pseudo-towers as a pacing gate are untouched by that rejection. **Updated
  2026-08-09:** the forward structure now has a job (see the decision entry
  above) — dormant, event-activated, garrisonable, one per lane for now. That
  answers what a *forward structure* is, and says nothing about whether a
  separate in-lane pacing gate exists; the two are still distinct objects.
- **Whether the reinforcement pool refills, decays, or only drains** — ~~not
  raised~~ **deliberately undecided as of 2026-08-09**: the user wants to *feel*
  trickle-refill versus no-refill in a working prototype before deciding. That
  prototype exists but its pull request is open and unmerged, so he has not
  reacted to it. A **deferral to evidence, not a gap.** And **what a
  reinforcement count looks like on a phone**, which competes for the same bottom
  25% as everything else — still unraised. 05, touches 01.
- **⚠ Whether the accrual gate and banking are one system or two.** *"I did mean
  accrue"* — confirmed 2026-07-26. But its stated job is **gating the cost of
  powerful effects** (*"that shouldn't just be one card"*), whereas
  [09](issues/09-banking-mechanic.md)'s job was tempo-vs-investment. Same shape,
  different purpose, and held as *"just a hypothetical."* **The hazard is
  bookkeeping, not design:** a shelved ticket whose mechanic is quietly in use
  under another name is how a design loses track of itself. Pick one — 09
  returns, or the design has two accrual systems and 18 must know it.
- **What replaces towers in the lane.** The turret is rejected as copying, but
  the *job* is wanted and was **clarified 2026-07-26 to be pacing, not catch-up**:
  a **scaling gate** too strong to pass early, which stops an early bulldoze.
  Design brief: a lane obstacle with a power curve that doesn't read as a
  building. Terrain manipulation may share machinery with it. **Unchanged by the
  2026-07-29 rejection of the tower chain** — the pacing job survives intact; see
  the resolved challenge above. Related but distinct from the forward-structure
  question, which is about what a *spawn point* does, not about a gate.
- **What terrain damage is** beyond its existence: permanent or decaying,
  repairable, counterable, and whether it hits your own units too. ~~Plus the
  user's own dangling *"maybe that can somehow affect what the overall win
  condition is."*~~ **That half is answered 2026-07-29:** it is lever 2 — it
  drains their reinforcements faster.
- **What else fits in the bottom 25%.** It must hold the cards, readouts on both
  heroes, and — proposed for off-screen lane alerts — *"a notification or you'd
  have a mini map that would have a ping on it."* Three jobs, one quarter of a
  phone. Whether a minimap survives that competition is unresolved. Note this is
  a **newer statement than the napkin sketch**, which put Hero Cams in two
  corners and cards as a semi-transparent overlay; the two are unreconciled and
  the sketch is not retired.
  - **New constraint from 05's 2026-08-07 dump, recorded not rebuilt.** Reacting
    to the vision sketch, the user wants the **command bar centred on a display
    of the enemy hero's status** — *the thing you watch to make gameplay
    choices* — rather than a paired readout beside your own, and likely the same
    UI that would track progress toward the hero power threshold. **This tightens
    the bottom-25% competition and touches
    [01](issues/01-battlefield-geometry.md) and
    [10](issues/10-information-visibility.md)**, neither of which is rebuilt in
    this pass.
- **Whether any gesture survives.** The "never drawn symbols" rejection still
  binds, but with casting reduced to selection it is unclear whether flicks and
  drags remain anywhere — combining cards together, steering the hero (15 asks
  this), or nowhere at all. Tap-only is now a live possibility that nobody has
  chosen.
- **What "RPG elements" concretely means.** Stated as wanted, never defined.
  Heroes and items now cover part of it. Does any of it touch power?
- **Meta-progression outside the match.** Partly owned by 06 and 11; the broader
  shape is unexamined, and hero unlocks are now part of it.
- **Deployable units to bolster a lane.** Floated during charting. May fold into
  09, 12 or 17.
- **The three unpicked merge outcomes.** Two are now relocated rather than
  unpicked — transmutation to the hero/jungle recipes, higher-tier to nothing.
- **PvE mode design.** AI opponents, campaign, co-op — unexamined.
- **Real-time PvP netcode feasibility.** A genuine go/no-go risk. Flagged, never
  assessed. Heroes and items make the sync problem harder.
- **Matchmaking fairness across unlock states.** Sharpened by 16 — deck quality
  now varies with collection size.
- **Session length for mobile contexts.**
- **Art direction and tone.**

## Out of scope

- Engine, stack, and platform choice — build decisions, not concept decisions.
- Art production pipeline.
- Naming and branding.
- Funding, team, and publishing.
