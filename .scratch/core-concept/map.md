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
  - **⚠ The open half is closed 2026-08-11:** exhaustion is **not** a loss
    condition — see the entry below.
- **Reinforcement exhaustion as an ending** (recorded 2026-07-29 as *"the win
  condition is reinforcement exhaustion"*, **closed out 2026-08-11**). Was: the
  **win condition** — *"you only live as long as you have reinforcements."* Now:
  **not a loss condition at all.** Reinforcements tick down, **zero means you stop
  spawning creeps, and that is the whole consequence** — the price of a strategic
  choice, not a defeat state. **Why, in the user's words:** Warcraft 3 is the
  reference — *"a level 10 hero with good items can sometimes beat bigger armies
  by themselves, because that's the nature of the game"* — so **the hero is the
  main thing that wins or loses the game**, and running dry is a sacrifice that
  bought hero power: *"if you run out of reinforcements because you spent most of
  your time farming in the jungle to get your hero stronger instead of bringing it
  to the lanes to maintain map control, then perhaps the power that you've gained
  via that sacrifice can allow you to somehow win with better strategy."* **His
  hedges — *"perhaps"*, *"somehow"* — are part of the record: the principle is
  stated, the mechanism that converts that power into a win is not.** **Scope,
  stated because a cold read will over-extend it:** this changes exhaustion's
  **standing**, and does **not** delete the pool, the three levers or any
  2026-07-29 material — the pool survives as the **resource** the strategic axis
  is fought over. It also **does not move the ending a fifth time**; the loss
  condition is still the enemy hero's power threshold (2026-08-09). See
  [05](issues/05-match-shape-win-condition.md).
- **The forward structure** (answered 2026-08-07 / 2026-08-09, developed
  2026-08-11, **CUT 2026-08-11**) — **the largest structural change this design
  has taken.** Was: *forward structures sit dormant, activate on a telegraphed
  lane event, and the hero may garrison and defend one; map control changes hands
  by taking or losing one.* Now: **there is no forward structure**, and **the
  hero's legal roam in a lane extends as far forward as that lane's front line.**
  **Why, in the user's words:** *"i like your replacement, lets go with that (hero
  leash)."* **Scope, stated because a cold read will get it wrong in both
  directions:** the structure is **cut as a consequence of adopting the leash** —
  the adopted candidate has **no object in the lane at all** — **not rejected on
  its merits**. His own reason for wanting one (*"trying to deviate from the
  typical MO whilst still maybe foolishly attempting to retain it"*) and the
  **function** he wanted from it survive the cut; the function is now a
  **standing unmet requirement** (see "Not yet specified"). **Events survive the
  building**; **the telegraph, the ~5-minute cadence and the ~1-minute lead
  survive**; **the defended building, the garrison and structure-imbue do not.**
  **The reasoning that produced it:** under strict confinement a *winning* push
  moves the fighting into the enemy half where the hero may not follow, so **your
  gold income transfers to your opponent** and turtling is the stable line — a
  contradiction **no object in the lane can repair, only a crossing rule can.**
  Originates in the `mg-lane-without-structure` investigation (position **P3a**,
  candidate **R5**), adopted by him. See
  [05](issues/05-match-shape-win-condition.md).
- **Map control's worth** (recorded 2026-08-11 as *information denial*,
  **reversed later the same day**). Was: *"you can cause your opponent to be
  scared because of lack of information. Therefore, they have to play
  significantly more cautious and they don't get to scale as quickly."* Now:
  **economic denial** — pushing past their front line makes their farming
  dangerous, so **they earn less gold.** **Why, and it is his own reasoning:** he
  rejected the information answer himself because **a minimap shows both heroes
  at all times**, so nobody is ever pushing blind and there is **no fog to fear.**
  **Scope:** the **effect** — slowing the opponent's scaling — is unchanged, and
  map control remains **the front line** rather than an object. **What changed is
  the mechanism of the harm.** See
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

- **The leash is a LIMIT, not a barrier, and it gets no rendering of its own**
  `[provisional]` (2026-08-12/13, from his play-test) — **tapping past the front
  line is always accepted**: *"I think you should always be able to tap past the
  frontline to have your hero run in that direction."* **His requirement:**
  *"there needs to be some sort of mechanism where it doesn't just constantly
  attempt to run through an invisible barrier taking damage."* **His own
  resolution:** a tap aimed past the limit **defaults to a move on arrival**
  rather than continuing to pursue — the hero **travels as far as it legally can
  and then settles**. **Never rejects input, never grinds at the edge**, and he
  is content that some of it is the player's job: *"I guess that's just up to the
  player to pay attention to."* **Separately, the leash needs no drawn boundary**
  — he agreed it is already visible through **the creeps forming the front
  line**, and the previously drawn version made the leash and the home field
  indistinguishable: *"I'm not even sure what it is... I see like these lines. Is
  that the leash? I don't know."* **⚠ Scope: this answers what is drawn on the
  board. It does NOT retire the leash readout as a claimant on the bottom 25%** —
  that is 01's question and is untouched. **Do not extend the cascade.** See
  [05](issues/05-match-shape-win-condition.md).
- **The home field is expressed as a BOUNDARY, and the buff LINGERS**
  `[provisional]` (2026-08-13) — **on expression:** *"not a literal force field,
  just some sort of visual indicator maybe in the lane that tells you the line in
  the sand of where minions will be buffed versus where they won't be."* **A line
  in the lane, not a drawn volume**; the field's shape and its job as the
  locked-in early-rush brake are **unchanged**. **NEW MECHANIC, his:** *"as
  minions leave the force field, as they're pathing through their lane and
  walking out of the force field, there is a timer that it is still up before it
  dissipates."* **The buff persists for a period after a minion leaves the
  field.** **Its purpose in his words:** *"so they can't just sit at the line of
  the force field and then wait for them to come out and farm minions"* —
  **without it the boundary is a camping spot** — and it buys the defender *"a
  little bit of breathing room."* **⚠ The duration is NOT a decision** — the
  prototype carries a provisional tuner value, cited and not adopted. **⚠ Open
  and never put to him:** the lingering buff also **turns the field's retraction
  from a hard cliff into a gradient in time**, and **whether that softening is
  intended is unasked** — surfaced independently by firstmate and the prototype
  worker, which is why it is recorded rather than assumed. See
  [05](issues/05-match-shape-win-condition.md).
- **The jungle is SEMI-OPEN, and traversal must be interesting** `[provisional]`
  (2026-08-13, from his play-test of the prototype) — *"The jungle is not an open
  forested area, neither is it a completely dense forested area. It is a forested
  area with clear openings and paths to traverse and little pockets where the
  creeps will hang out."* And: *"The hero does walk through the jungle. It is
  accepted."* **Paths and clearings by default, camps in pockets off them,
  passage the default state.** **⚠ This is a CLARIFICATION of what the jungle
  physically is, NOT a reversal:** **destructible trees stand**, **aggro-pull
  geometry as a function of current geometry stands**, and it is **consistent
  with the traversal-by-default pricing baseline** — blocking passage is only
  worth a card because passage is the default. What it amends in place is this
  map's own phrasing *"a set of chambers, not one open field"*, **which was the
  map's reading of his aggro condition, not his words.** **A requirement arrives
  with it:** *"the ability to traverse the jungle needs to be made a much better
  experience"* — **routes, angles and choices, not corridors with alcoves** —
  and **he ruled out sightline denial himself** as the reason, since there is no
  fog and a minimap shows both heroes. See [12](issues/12-jungle-role.md).
- **Jungle symmetry — the tension is DISSOLVED by a distinction** `[provisional]`
  (2026-08-13) — his objection to the corrected prototype was *"I'm not crazy
  about the layout. It's very symmetrical... their maps don't look so NASCAR
  track with a line in the middle."* **Rotational symmetry stays** — it is what
  keeps a **1v1 with no draft** fair, there being no pick order to absorb a side
  advantage — **while mirror symmetry with a ruled straight axis goes**, that
  being what produces the NASCAR read. **Irregular internal geometry supplies the
  variety he asked for without handing either side an advantage**, so **his
  2026-08-11 tension — *"I'm not sure how to weigh the repetitiveness of symmetry
  versus the potential benefits you get from being on a certain side"* — was
  never a real conflict.** His direction (*"not totally symmetrical"*) is
  **satisfied, not overridden**. **⚠ The objection is his; the distinction is a
  firstmate reading offered to be overruled, and his reaction to the built result
  is not yet recorded.** See [12](issues/12-jungle-role.md).
- **Hero intent: one tap is attack-move, two taps is move only** `[provisional]`
  (2026-08-13) — *"maybe attack is one and then just move is two. So if a player
  chooses to spam to run away, it's always run away versus choosing to attack is
  deliberate."* **His rationale outlives the mechanism: panic is spammy, so spam
  must resolve to fleeing**, and attacking is the deliberate act. He had offered
  the pairing on 2026-08-12 **without choosing which way round**, under the
  constraint *"maybe we don't need another verb"* — **both intents on one
  gesture, no extra control, no screen space.** **This answers the *assignment*
  half of 12's move-versus-attack-move problem and not the other half** — see
  "Not yet specified". **Separately, tap-to-move is VALIDATED BY PLAY** — *"the
  tap to move is actually really good"* — which closes the
  joystick-versus-minimap-versus-buttons question **by evidence rather than by
  argument.** See [12](issues/12-jungle-role.md), reaches
  [15](issues/15-heroes.md).
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
- **The command bar is three panels, and the middle one is the win condition's
  scoreboard** `[provisional]` (2026-08-11) — **the first concrete layout the
  bottom 25% has had.** **Left: the cards. Middle, wider than either side
  individually: a screen showing your hero and the enemy hero with their progress
  and power. Right: undecided** — his own framing, *"something tactical that
  controls one of the game's other levers?"* **Why the middle is load-bearing:**
  the loss condition is **the enemy hero reaching a power threshold** and his
  framing of the whole game is **preventing your opponent from maximising that
  power journey while maximising your own**, so a central readout of both heroes'
  progress is **the scoreboard of the win condition, not a status readout** — and
  **it arrives before the threshold's own specifics, which stay parked.**
  **Candidates for the right panel, none chosen:** the **jungle pre-commitment
  readout** (~six camps — difficulty, time, damage and mana cost, expected gold,
  possible items), the **event panel** (telegraph countdown, event type, imbue
  commitment, placement influence), the **gold conversion site** at the main
  base, and a **minimap** — **which is information rather than a lever.**
  - **Panel swapping is ACCEPTED** — *"If another lever is required, but no
    space, need an option to toggle/swap it visible when needed."* **The bar is
    not required to be three fixed panels**, and a lever may be brought up on
    demand. **A general principle for the command bar, NOT a decision about which
    lever holds the fixed slot.** It bears on the standing bottom-25%
    competition, because that competition no longer has to be settled by
    permanent allocation.
  - **⚠ The centre screen's direction is DELEGATED, not open.** *"Based on what
    the agent feels works better, have them choose the direction for the centre
    screen. I remember my rationale for both, but things have diverged since."*
    **He has handed the choice to whoever builds it** — **do not file it as a
    captain decision and do not bring it back to him** — and **whoever chooses
    must record the choice and its reason** in 01. **Both framings are his and
    both are preserved:** 2026-08-07, *the bar centred on the **enemy** hero's
    status, not a paired readout beside your own*; 2026-08-11, **both heroes** in
    the middle. **The tension is stated and deliberately unresolved, and is NOT
    flagged as a reversal, because he has not called it one.** **What diverged,
    recorded as material for the chooser and not as a steer:** the loss condition
    became a **race**, which has two runners; map control became **economic**
    rather than informational; the **leash** arrived and may want a readout in
    the same bar; and a **minimap showing both heroes at all times** is already
    on record, which may leave the centre screen's job as **progress** rather
    than **position**. See [01](issues/01-battlefield-geometry.md).
- **The front line is the hero's leash, and the forward structure is cut**
  `[provisional]` (2026-08-11) — **the largest structural change so far.** *"i
  like your replacement, lets go with that (hero leash)."* **The hero's legal
  roam in a lane extends as far forward as that lane's front line** — push and
  your world grows, concede and it closes. **Not strict confinement, not free
  crossing.** There is **no object in the lane**, which is why adopting it
  **cuts the forward structure** (reversal log above; the structure material is
  carried forward as history in 05, not deleted).
  - **What it fixes, and it is why he took it.** Gold comes from **the hero
    killing any minion, no last-hitting**. Confine the hero to its own half and a
    *successful* push moves the fighting — and therefore the dying minions —
    into the enemy half where the hero may not follow, so **winning a lane
    transfers your gold income to your opponent** and the stable line is to hold
    at your own border and farm arrivals. **The leash dissolves that: pushing
    extends where the hero may farm.** The two arms of the axis become
    **sequential** — push to open ground, then farm the ground you opened.
  - **What it does for the clash he wanted:** contact happens **at the seam where
    the two leashes meet — automatically, and only there.** He had wanted heroes
    to clash *"even if the way you control your hero is just by like simple input
    commands"* while also intending that *"your hero would never cross your own
    side of the map"* — **the leash is what he took instead of choosing between
    them.**
  - **It makes a locked constraint load-bearing:** creeps acquire a new job —
    **they define where your hero may be.** *"Creeps are units, not a meter"*
    stops being merely honoured.
  - **Known costs, recorded as open risks, not defects.** **It snowballs**:
    winning a lane compounds. It **passes the `[committed]` deliberate-losing
    rail** — a thrower gains nothing — **but it risks blowouts.** And it **needs a
    new readout**: the player must see at a glance **where the hero may go**,
    competing for the same bottom 25% as everything else.
  - **What it does NOT settle, per his own decision record:** where the **imbue
    loop** lands (homeless unless imbue moves onto the hero), whether telegraphed
    events are **shared or mirrored**, rehousing the **hero-in-lane card** as a
    temporary leash extension, and whether **hero strength boosting structure
    power** survives at all. **None of these is closed here.**
  - **Reach, recorded not rebuilt:** **[12](issues/12-jungle-role.md)** (jungle
    reachability is now a function of the front line),
    **[01](issues/01-battlefield-geometry.md)** (the new readout; the midline
    gains meaning as the moving seam), **[15](issues/15-heroes.md)** (roam is
    bounded — **steering is unchanged**, still coarse standing orders; whether
    that meets the per-lane-pool condition is **not stated**).
- **The shrinking home field is LOCKED IN as the early-rush brake**
  `[provisional]` (2026-08-11) — *"I think we are going to go with the force
  field, so let's lock that concept in."* **No longer a floated candidate.** The
  **home base emits a field**, **minions inside it are empowered**, and **the
  field retracts over the match**; it is a **hard defensive floor** that holds
  regardless of how badly a lane is going, and **the retraction is a schedule of
  legitimacy** that **defines the game's phases.** **This answers the early-rush
  requirement** — the one that arrived when cutting the forward structure removed
  the brake. **⚠ The lock does not answer what sits beneath it:** **readability**
  of an indirect cause, the **interaction with the gold rule**, and **whether it
  stacks with the leash or replaces part of it** — **none has been put to him.**
  See [05](issues/05-match-shape-win-condition.md).
- **Map control's worth is ECONOMIC denial, not informational** `[provisional]`
  (2026-08-11) — **a reversal of the recorded worth, flagged as one, and it is his
  own reasoning that produced it.** He **rejected the peace-of-mind answer
  himself**, because **a minimap shows both heroes at all times**, so nobody
  pushes blind and there is **no fog to fear.** Where he landed: *"Eventually you
  could potentially push beyond the frontline of their first creeps and that
  makes them more dangerous for them to farm it, so they're going to be earning
  less gold."* **Pushing shrinks their reachable ground, which shrinks their
  income** — consistent with the leash, and the right answer for a game with no
  fog. **The effect on the opponent's scaling rate is unchanged; what changed is
  why.** **Two open questions came out of the same reasoning** — how a pushed-back
  player pushes back, and something that pushes the game toward an ending — both
  in "Not yet specified". Reaches [10](issues/10-information-visibility.md), which
  is **not rebuilt.** See [05](issues/05-match-shape-win-condition.md).
- **Event lane placement is influence, not selection** `[provisional]`
  (2026-08-11) — *"I think it should be some sort of combination of both. I think
  that the player should be able to perhaps influence where it goes without being
  able to just 100% outright select the lane."* **This answers the fork he had
  left with both options live and neither chosen, by taking a combination.** **The
  mechanism is commissioned and unchosen — do not pick one.** **His stated intent
  is unchanged:** *"so it's not always you will be forced to meet the other player
  in lane if you both choose to defend."* **A finding from the commissioned work,
  recorded as a finding and not as his:** **the variable that must not be fully
  controlled is the collision, not the lane** — **determination** and
  **disclosure** are separate dials, and **his words are a determination
  statement while his reason is a disclosure problem.** **Which he wants has not
  been put to him.** See [05](issues/05-match-shape-win-condition.md).
- **Hero control is tapping the map** `[provisional]` (2026-08-11) — *"I think
  player control will need to be done via tapping on the map."* **A joystick and
  preset move-to-area buttons were the two other candidates and are not chosen.**
  It follows the amendment *"A hero is not fully autonomous"*, which **amends the
  `[provisional]` never-steers-directly line** (see the standing-orders entry
  below and its in-place amendment). **Consistent with casting-as-selection** —
  the player selects a destination, they do not pilot. **⚠ Open and recorded as
  prototype work, not solved:** how **move** and **attack-move** are both
  expressed through one tap — being locked into the wrong intent *"will feel
  really bad."* See [12](issues/12-jungle-role.md), and note
  [15](issues/15-heroes.md) and `AGENTS.md` still carry the superseded phrasing.
- **The jungle is a set of destructible-walled chambers, and jungle *control*
  does not exist here** `[provisional]` (2026-08-11) — **12's first dump.**
  **Trees are walls** separating jungle areas from each other and from the lanes,
  **they can be destroyed**, and destroying them **changes where lane creeps can
  be aggro-pulled** — so **jungle geometry is mutable mid-match** and aggro is a
  function of current geometry. **⚠ Its relationship to terrain manipulation has
  not been asked; do not assume they are one system.** Separately, *"There isn't
  really jungle control like a typical MOBA"* — **no ganks to fear, no teammates
  to make an opening, no vision to need**, so the MOBA idea has **no substrate in
  a 1v1 with no fog and no allies.** **The question is dissolved, not answered:**
  what remains is jungle **access**, governed by **the leash** and **the
  retracting home field.** **Where the jungle sits is answered** — a typical MOBA
  layout, bases top and bottom, three lanes, jungle between all of it, **nothing
  really traversable on the outsides.** His **Heroes of Newerth** remark is a
  **reference describing a shape, explicitly not a request** (*"I don't know that
  that's necessarily something I want to implement"*). **Confirmed unchanged:**
  playable space the hero must traverse, gold plus items and power-ups, and
  **screen budget is no longer a constraint** (*"That's correct"*). See
  [12](issues/12-jungle-role.md).
- **The jungle's autonomy, answered rung by rung** `[provisional]` (2026-08-11) —
  **12's second dump**, reacting to a commissioned brainstorm whose ladder
  supplied the vocabulary. **Rung 2 adopted**, with content: roughly **six camps a
  side**, each showing **difficulty, how long it would take, damage and mana
  cost, expected gold and possible items** — a **pre-commitment readout** that
  makes farming comparable to pushing **before you commit**. *"Tons more decisions
  stemming from that, but those are later"* — **do not open them.** **Rung 3
  adopted but NARROWED**, and the narrowing is his: the ladder's rung 3 responded
  to **game state**; **he redefined it as responding to match TIME** — earlier is
  easier with weaker drops, later is harder with better and more. A time curve is
  **symmetric and predictable**, so it **raises no deliberate-losing concern**;
  tuning is his and is parked. **Rung 4 open, with a shape** — if things leave the
  jungle for a lane it is **on a timer or cadence, not continuous**; whether an
  **unclaimed neutral** can do so is unresolved, *"I don't know what that one."*
  **Rung 5 rejected**, both reasons his: it **reads as chaotic**, **and it
  interferes with the player's own pathing** — the sharper objection, and specific
  to a design where **route planning is the player's main spatial act.** **Rung 4a
  adopted with an attribution principle:** the Heroes of the Storm pattern (clear
  a camp, it marches your lane) is **the player acting, not the jungle** — *"you're
  not getting power from the jungle, but you are claiming something of the jungle
  that then benefits you."* **The jungle is a place you claim things out of, not a
  dispenser you receive from** — a reusable test. See
  [12](issues/12-jungle-role.md).
- **The chasm is CUT *"for now"*, and the two jungle halves connect by ordinary
  traversal** `[provisional]` (2026-08-11) — **its origin is his:** it came from a
  *"you don't ever pass your own side"* assumption and was *"my way of like
  preventing you from pushing early game."* **Why it goes:** that job now belongs
  to **the retracting home field**, and the crossing rule it assumed was
  **replaced by the leash.** He **rejected river and elevation variants as
  typical.** *"Maybe just crossing over is fine. There's a lot that has to be done
  already. Maybe just take out the chasm for now. We'll just consider it typical
  traversal."* **⚠ The *"for now"* is his** — a shelving with a reason, the same
  standing as banking. **⚠ The scope reasoning is a first:** *"there's a lot that
  has to be done already"* is **the first thing cut to limit scope rather than on
  merit.** **Consequence:** the long-standing **how-do-the-jungle-halves-connect**
  question is **closed** — ordinary traversal. **Also answered: the home field does
  NOT gate jungle access — no.** See [12](issues/12-jungle-role.md).
- **Events survive the structure; event lane placement becomes a variable**
  `[provisional]` (2026-08-11) — *"Can still do events that summon large minions
  that need to be dealt with."* The **~5-minute cadence**, the **~1-minute
  telegraph** and the **large-unique-minion type** all survive; **only the
  defended building died.** **One event per side stays, but its lane is now a
  variable** — *"maybe the player gets to choose which lane they wanted to spawn
  in, or there is some mechanism that determines which lane it spawns in."* **He
  offered both and picked neither.** **His intent:** *"so it's not always you
  will be forced to meet the other player in lane if you both choose to
  defend."* **This answers the parallel-versus-contested question in a third
  way** neither option covered: **collision becomes emergent** — not guaranteed,
  not excluded. See [05](issues/05-match-shape-win-condition.md).
- **An imbue is visible to the opponent** `[provisional]` (2026-08-11) — *"I would
  say so."* Extends board-open / hand-hidden to **prep**. **In the same breath, a
  hero talent-tree idea:** imbues selected by **hero choice or a pre-match pick**,
  *"two or three ways that they can affect it based on the type of hero that they
  are"*, *"like how in World of Warcraft you have a talent tree."* **⚠ It may
  complement the card-imbue loop or replace it — he did not say which, and this
  is not decided here.** Reaches **[14](issues/14-pre-match-setup.md)** and
  **[15](issues/15-heroes.md)**; neither is rebuilt. See
  [05](issues/05-match-shape-win-condition.md).
- **Reinforcement exhaustion is NOT a loss condition** `[provisional]`
  (2026-08-11) — the question 2026-08-09 left *"not stated either way"* is
  answered by the user. Reinforcements tick down; **zero means you stop spawning
  creeps and nothing more.** It is **the price of a strategic choice, not a defeat
  state**, because *"a level 10 hero with good items can sometimes beat bigger
  armies by themselves"* — **the hero is what wins or loses the game.** **The pool,
  the three levers and all 2026-07-29 material survive as the resource system**
  the axis below is fought over; the ending does **not** move a fifth time. See
  the reversal log and [05](issues/05-match-shape-win-condition.md).
- **The central strategic axis: push the lanes for map control, or farm the
  jungle for power** `[provisional]` (2026-08-11) — the choice the whole match is
  organised around, in his framing: *"How could choosing to put your hero in the
  lanes to push them to gain map control be used as a strategic benefit over
  choosing to keep your hero in the jungle to farm gold and items while giving up
  map control?"* **Both arms pay, in comparable magnitude, in different
  currency** — this is explicitly *not* a tradeoff where one arm is the real path
  and the other a tax.
  - **The lane resource is gold, earned whenever the hero kills a minion.**
    **Last-hitting explicitly will not work here**, so any minion the hero kills
    pays. **Lanes pay more gold than the jungle**; **the jungle pays unique items
    and power-ups plus a smaller gold drop**; **gold buys similar-but-not-identical
    power-ups at the main base**, the same place **units are upgraded**. His own
    statement of the choice: *"Are you going to push for map control and earn gold
    via that... or are you going to farm the jungle to get the unique items...
    or a balance of the two."*
  - **⚠ Superseded 2026-08-11 by the leash, bullet below kept as written:** with
    no structure, **map control does not change hands by taking an object — it
    *is* the front line**, moving continuously as creeps fight, and what it pays
    the hero is **reach**. **Its stated worth is unchanged.**
  - **Map control changes hands by losing your own forward structure or destroying
    the opponent's**, and **its stated worth is information denial** — *"you can
    cause your opponent to be scared because of lack of information. Therefore,
    they have to play significantly more cautious and they don't get to scale as
    quickly as their opponent because of it."*
    - **⚠ REVERSED later 2026-08-11, bullet above kept as written.** **Its worth
      is economic denial, not information denial** — he rejected the information
      answer himself on the grounds that **a minimap shows both heroes at all
      times.** **Pushing past their front line makes their farming dangerous, so
      they earn less gold.** See the reversal log.
  - **The optimum is matchup-dependent, not fixed** — it moves with the opponent's
    hero choice, farm choice and cards, *"so the decision could change each
    match."*
  - **The forward structure must be wrapped into this axis**, not sit beside it —
    it is the **fulcrum** of push-versus-farm. That is the constraint this dump
    imposes on the structure work.
    - **⚠ The axis survives; its fulcrum moved 2026-08-11.** The question is
      unchanged and still the spine. **The structure is cut, and the leash takes
      the fulcrum job** — pushing a lane buys the ground the hero may farm.
  - **Reach, recorded not rebuilt:** **[12](issues/12-jungle-role.md)** (the
    jungle is now one arm of the central choice, not merely playable space),
    **[17](issues/17-gold-and-items.md)** (gold and items is where hero power is
    bought, at the main base), **[10](issues/10-information-visibility.md)** (map
    control's value is *denying information*, giving board-open/hand-hidden a
    strategic consequence). **None of the three is rebuilt in this pass.**
  - **His scope instruction:** proceed with the **structure and axis** items;
    **park the power-threshold and economy items**, which *"require a lot of
    individual thought."* See [05](issues/05-match-shape-win-condition.md).
- **Cards have two distinct uses: acting on lane state, and imbuing a forward
  structure before a telegraphed event** `[provisional]` (2026-08-11) — *"two
  different things"*, not one mechanic wearing two hats. **(1) Lane-state cards**,
  the existing class: AoE damage, **a blocker that stops creeps moving up for a
  time**, movement slows. **(2) Structure-imbue cards**, played into the ~1-minute
  telegraph against a **known event type** — *"this monster is going to be
  fire-based, so maybe you should save your ice stuff for it"* — which is **the use
  that makes prep a real decision**, and creates a **hold-versus-spend tension on
  the hand** (an ice card saved is a card not spent on the lane now). **Routing
  note from this rebuild, not his:** it plainly bears on
  [02](issues/02-combining-mechanic.md), [11](issues/11-accrual-economy.md) and
  [16](issues/16-deckbuilding.md); **none is rebuilt here and he named none of
  them.** **⚠ Bookkeeping:** this
  **bears on** the 2026-08-07 question of whether *"prep with cards"* is the
  existing help-your-lane target class or a new one, but he framed it as two
  **uses** and **never used the target-class vocabulary** — **not recorded as
  answered.** It also confirms the two burdens in his **unfinished
  card-complexity sentence** are genuinely distinct, **without finishing that
  sentence.** See [05](issues/05-match-shape-win-condition.md).
  - **⚠ Use (2) loses its target later the same day.** With the structure cut
    **there is nothing to imbue**, unless the imbue is rehoused — his own
    **talent-tree idea** names **the hero** as the candidate host. **The finding
    that the two uses are distinct is not withdrawn; where the second one lives
    is open, and he has not chosen.** Use (1), lane-state cards, is untouched.
    The **~1-minute counter-prep telegraph survives** — it is a property of the
    event, not of the building.
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
  - **⚠ Updated 2026-08-11, text above kept as written.** The last sentence is now
    answered: **exhaustion is not a loss condition** (entry above). On the
    threshold itself he **leaned away from a hard gate without choosing** — *"I
    don't think it's a hard gate. Maybe it is, I don't know."* The **firm
    requirement underneath** is that **there must be a resolution line, because if
    both sides can defend it cannot be a stalemate**; his concept for it is an
    **"exodia moment"** — *"if the hero reaches some sort of exodia moment, then
    they just win"*, an accumulation that becomes unanswerable once complete,
    **concretely undefined**. And the tuning is **explicitly unknown, in his own
    words**: *"I don't know how it tunes yet. And I don't know how hero power will
    convert to a win yet. I don't know anything about the power thresholds just
    yet."* **Parked by his own scope instruction — do not close it.**
  - **⚠ Untouched by the leash decision — the ending does NOT move a fifth
    time.** One detail above ages: **there is no forward structure to defend**,
    so that power source loses its object. **Events survive the building**, so
    *defending an event* may still pay power — **he did not restate it either
    way, and it is not inferred here.** Lane creeps and jungle creeps/items are
    unaffected; the leash changes **where** the hero may collect the first of
    them.
- **Match length is assumed ~15 minutes, with a lane event roughly every 5
  minutes** `[provisional]` (2026-08-09) — each event bounded to something quick
  to resolve. The first answer 05's "match length" question has had. **Untouched
  by the leash decision: the cadence survives the building.**
- **~~What the forward structure does~~ — CUT 2026-08-11, entry kept as
  history.** **The structure no longer exists** (see the leash entry above and
  the reversal log); **every dependent below is retired, rehoused or open, and
  05 carries the itemised list.** Kept because it is the record of three
  sessions' reasoning and because **its rejections and its `[committed]` test
  outlive the object.** Original entry follows.
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
  - **⚠ Extended 2026-08-11 — the structure now has to serve the central axis,
    and it grew a live problem.** **(a)** It is the **fulcrum of push-versus-farm**
    (entry above), not a separate subsystem. **(b)** **One structure, as the
    starting test** — he re-raised the count himself, which **reopens** the
    2026-08-09 simplification, and came back to one **with a reason attached**:
    multiples depend on **map size** and **how long minions take to cross**, both
    unknown, and it is a **mobile game that needs to be short**, so *"one is
    probably just the best way to start now as a test."* **Reinforced, not newly
    decided**, and **step-down defence lines stay deferred, not rejected.**
    **(c)** **Ordinary minions probably spawn at the base** (*"I think maybe the
    minions do start at the bottom"*); **rare units spawning at the structure was
    developed and then CUT** — see (e). **(d) ⚠ The forced-tax problem returned
    through a different door.** He wanted a **defence bonus**, then spotted the
    flaw himself: *"If you can summon a special unit from it, then you kind of
    don't really get an option of saving it or not. You're kind of forced to,
    otherwise you lose power."* **The telegraphed-event system exists specifically
    to prevent that**, and it fixes *who picks the timing*, not *whether you can
    afford to decline*. **(e) ❌ Rejection, later the same session, with his hedge
    intact:** *"kill the ability for ad hoc rare units to be spawned at the
    structures **for now**."* **The recursion is resolved by removal, not by
    balance** — with no unique power source attached, losing a structure costs
    **map control** and nothing else, so it is **concedable again**. **The problem
    statement is kept as the reason for the cut** and returns if anything unique is
    re-attached. **The *"for now"* is his** — a shelving with a reason, the same
    standing as banking, not a permanent no. **It also reopens how forward creep
    spawning works**, since rare units were the candidate answer; **forward creep
    spawning itself is still not dead.** Left **unstated**: whether a defence bonus
    is still wanted now its rationale is gone. **(f) The telegraph gains a lead
    time and a type** — *"There is a timer. In one minute, the big monster is going
    to spawn and start wrecking your forward structure. So, start thinking about
    what type of cards you're going to use to imbue it."* **~1 minute**, enough to
    commit cards and not enough to re-plan; **events have a known nature you
    counter-prep against** (*"this monster is going to be fire-based, so maybe you
    should save your ice stuff for it"*), which makes the telegraph
    **informational, not a countdown**, and creates a **hold-versus-spend tension
    on the hand**. **(g)** He **did not restate his `[committed]` test** against
    any of this — **unstated, not passed.**
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
  making the push harder or more survivable. **⚠ 2026-08-11: lever 3's card is to
  be rehoused as a temporary leash extension** — **a rehousing, not a deletion**,
  and its concrete form is unspecified. The pool and all three levers are
  otherwise untouched by the leash decision. This **replaces the map's earlier
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
  - **⚠ AMENDED 2026-08-11, text above kept as written.** *"A hero is not fully
    autonomous."* **This amends `[provisional]` material; it is not a reversal of
    a `[committed]` one** — what is `[committed]` is the *other* axis, casting as
    selection rather than performance, **which a hero movement control does not by
    itself violate.** **Decided: control is by tapping the map** — *"I think
    player control will need to be done via tapping on the map."* **The joystick
    and preset move-to-area buttons were the other two candidates and are not
    chosen.** The player still **selects a destination rather than piloting**, so
    the commander framing survives; what does **not** survive is *"never steers
    directly."* **⚠ That superseded phrasing is still carried by
    [15](issues/15-heroes.md) (stated twice) and by `AGENTS.md` — neither is
    edited by this rebuild; both must be read against this amendment.**
    **Firstmate error recorded:** several briefs asserted *"the player never
    drives the hero directly"* as **committed**. It was provisional. See
    [12](issues/12-jungle-role.md).
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
| 01 | Battlefield geometry & phone readability | open, **substantially answered** — pannable observer camera, no fog, screen split; **2026-08-11 (from 05): the hero leash needs a new readout** — the player must see at a glance **where the hero may go**, competing for the same bottom 25% — **and the midline gains meaning**, as the moving seam where the two leashes meet. Recorded, **not rebuilt**; **2026-08-11 (from 12): where the jungle sits is answered** — typical MOBA layout, **nothing really traversable on the outsides**, jungle as **destructible-walled chambers** — and **screen budget is confirmed no longer a constraint** (*"That's correct"*); **hero control is a tap on the map**, which puts a **new input surface** on the viewport this ticket owns. Recorded, **not rebuilt**; **⚠ 2026-08-11 — REBUILT in part: the command bar's layout is written in.** **Three panels — left the cards; middle, wider than either side individually, a screen showing both heroes' progress and power; right undecided** (*"something tactical that controls one of the game's other levers?"*). **The middle is the scoreboard of the win condition**, because the loss condition is the enemy hero's power threshold and the game is *"preventing your opponent from maximizing that power journey while maximizing your own"* — **it arrives before the threshold's specifics, which stay parked.** **Right-panel candidates recorded, none chosen** (jungle pre-commitment readout, event panel, gold conversion site, minimap — the last being information, not a lever). **Panel swapping ACCEPTED as a general principle** — the bar need not be three fixed panels — **which loosens the bottom-25% competition without settling it.** **⚠ The centre screen's direction is DELEGATED to whoever builds it, not open** — both his framings (2026-08-07 **enemy-centred**; 2026-08-11 **both heroes**) are preserved, **the tension is stated and unresolved and is not a reversal**, and **whoever chooses must record the choice and its reason** |
| 02 | What "combining cards" actually means | resolved + amended; **⚠ 2026-08-11 (from 05): a finding from commissioned card-system work, recorded as a finding and not as his — *combining is currently unpriced*.** 02 chose payload + modifiers and left the cap, reversibility and failure cases open, and nothing states **what combining costs**, so *combine everything, every time* is the dominant line and **the keystone mechanic has no decision in it.** Recorded, **not rebuilt** |
| 03 | Gesture as skill expression | **closed — removed** 2026-07-26 |
| 04 | Pressure vs. complexity — the learning curve | open, **eased**; now owns "where does skill live" |
| 05 | Match shape & win condition | open, **substantially answered**; **the ending moved a fourth time 2026-08-09** — loss is the **enemy hero reaching a WC3-style power threshold**, specifics wishy-washy by his own account; **the forward structure's job is answered 2026-08-07/09** (dormant structures, telegraphed lane events, hero garrison) with its specifics open; ~15-min match, ~5-min event cadence. **2026-08-11: exhaustion is NOT a loss condition** — the pool survives as a **resource**, its three levers untouched — and the ticket gains its **central axis with a stated payout on the pushing side**: **lanes pay gold on any hero minion kill (no last-hitting), jungle pays unique items plus less gold, gold buys power-ups at the main base**. **Cards split into lane-state and structure-imbue uses**; the telegraph gains a **~1-min lead and a known event type**. **Rare units at structures cut *"for now"***; **forward creep spawning is not dead but has no mechanism**; **threshold, tuning and power-to-win conversion parked by his instruction**. **⚠ 2026-08-11, later the same day — the largest structural change so far: the forward structure is CUT and the front line is the hero's leash** (*"i like your replacement, lets go with that (hero leash)"*). The hero's legal roam in a lane reaches **as far forward as that lane's front line** — not confinement, not free crossing — which **dissolves the contradiction that a winning push handed your gold income to your opponent**. **Everything structure-dependent is retired, rehoused or open, kept as history**; **events survive the building** (~5-min cadence, ~1-min telegraph, large-minion type) and **event lane placement becomes a variable** (player-chooses or mechanism — **he picked neither**), making collision **emergent**. **New unmet requirement: something must stop an early lane collapse.** **The shrinking home field is a floated, unchosen candidate for it.** **Imbue confirmed visible to the opponent**; **where the imbue lives is now open**. **⚠ 2026-08-11, backlog answers — AMENDED AGAIN: the shrinking home field is LOCKED IN** as the early-rush brake (*"let's lock that concept in"*), so that requirement is **met at concept level** while everything beneath it stays open. **Map control's worth is REVERSED to ECONOMIC denial** — he rejected the information answer himself because a minimap shows both heroes at all times — which opened two new questions: **how a pushed-back player pushes the line back**, and **something that pushes the game toward an ending** (*"not literally a berserk timer"*; the retracting field **may** already be it, flagged not assumed). **Event lane placement is answered in principle — influence, not selection** — with the **mechanism commissioned and unchosen**. **The imbue now has three threads and none is chosen**, including his own proposal that **the home field absorb the structure's creep buff** — an automatic positional constant in place of a prepared per-event card decision. **A hold-position order is neither ruled in nor out, but must be easily accessible and cancellable if it exists.** **The card system is RESET** to his restated goal, with five commissioned shapes and **none chosen**; **⚠ 2026-08-12/13 — REBUILT AGAIN from his play-test of the prototype.** **The leash is a LIMIT, not a barrier**: tapping past the front line is **always accepted**, the hero **travels as far as it legally can and then settles** (*"defaults to a move after you've reached your target spot"*), and it must **never grind at an invisible barrier taking damage**. **The leash gets no rendering of its own** — already visible through the creeps forming the front line — **which does NOT retire the leash readout as a bottom-25% claimant (01's question, untouched)**. **The home field is expressed as a boundary in the lane, not a drawn volume.** **NEW MECHANIC — the lingering buff:** the empowerment **persists for a period after a minion leaves the field**, *"so they can't just sit at the line of the force field and then wait for them to come out and farm minions"*, buying the defender *"a little bit of breathing room"*. **Its duration is NOT a decision.** **⚠ Newly open and never put to him: whether that lingering buff is meant to soften the field's retraction from a cliff into a gradient** |
| 06 | Unlock progression & the hook | open, **needs revisit after 16** |
| 07 | Monetization model | open |
| 08 | Consolidation pass | open (terminal) |
| 09 | Banking — combining over time | **shelved** — **⚠ may have found its payoff** 2026-07-26, awaiting user yes/no |
| 10 | Information — what you see of your opponent | **largely answered** — board open, hand hidden; partial-visibility detail still open; **new 2026-08-07 (from 05): the command bar should centre on the enemy hero's status** — recorded, not rebuilt; **2026-08-11 (from 05): map control's value is framed as denying the opponent information**, which gives board-open/hand-hidden a strategic consequence — recorded, not rebuilt; **2026-08-11 later the same day (from 05): an imbue IS visible to the opponent** (*"I would say so"*), extending board-open/hand-hidden to **prep**, and **map control's mechanism is now the front line** though its worth is unchanged — recorded, not rebuilt; **⚠ 2026-08-11, backlog answers (from 05): map control's worth is REVERSED — it is ECONOMIC denial, not informational.** He rejected the information answer himself because **a minimap shows both heroes at all times**, so nobody pushes blind and there is no fog to fear; pushing past their front line **makes their farming dangerous, so they earn less gold.** The **effect** on their scaling is unchanged; the **mechanism of the harm** is not. Also **still unanswered: whether the opponent can see your event lane placement before committing**, the natural companion to the imbue being visible. Recorded, **not rebuilt**; **⚠ 2026-08-11 (from 01): the 2026-08-07 enemy-centred command bar constraint recorded here is now one of two live framings** — he has since described **both heroes** in the middle panel — and **the choice between them is DELEGATED to whoever builds it, not a captain question.** **The tension is preserved and unresolved; it is not a reversal.** Recorded, **not rebuilt** |
| 11 | Card accrual economy | open; **⚠ 2026-08-11 (from 05): the card system is RESET** — hand size, freeze slot and deck size **set aside** in favour of his restated four-clause goal, and **five commissioned shapes are on the table with none chosen.** The **unpriced-combining** finding bears directly on accrual. Recorded, **not rebuilt** |
| 12 | The jungle — role and autonomy | open, **substantially answered — REBUILT 2026-08-11 from two dumps of its own**. **Where the jungle sits: answered** (typical MOBA layout, bases top and bottom, three lanes, jungle between all of it, **nothing really traversable on the outsides**; his Heroes of Newerth remark is a **reference, explicitly not a request**). **Jungle *control*: dissolved, not answered** — no ganks, no teammates, no vision needed, so the MOBA concept has no substrate here; **what remains is jungle access**, governed by the leash and the retracting home field. **Trees are destructible walls** separating chambers and lanes, so **jungle geometry is mutable mid-match** and aggro-pull reach changes with it — **its relation to terrain manipulation is unasked**. **Autonomy answered rung by rung:** **rung 2 adopted** (a **pre-commitment readout** — difficulty, time, damage, mana, expected gold and possible items, ~six camps a side), **rung 3 adopted but narrowed from game state to match TIME**, **rung 4 open with a shape** (timer/cadence, not continuous; unclaimed neutrals unresolved), **rung 4a adopted** with the principle *"you're not getting power from the jungle, but you are claiming something of the jungle that then benefits you"*, **rung 5 rejected** (chaotic, **and it interferes with the player's own pathing**). **The chasm is cut *"for now"*** on the retracting field and the leash, **and for scope** — *"there's a lot that has to be done already"* — so **the two halves connect by ordinary traversal**. **The home field does not gate jungle access.** **⚠ The hero-autonomy record is amended** — *"A hero is not fully autonomous"*, **control is tapping the map** — and **move-versus-attack-move through one tap is open prototype work**. **Still open:** jungle contents (**commissioned**), **symmetry** (direction given, tension unresolved), **whether invading the enemy jungle is possible at all** (reduced gold, no items, time-boxed, measure unchosen; **an anti-stomp device by his own statement**). Earlier: playable space, not a wall, aggro leash; **reframed 2026-08-09 by 05** as one of the levers of the hero power race (jungle creeps/items feed the threshold), not a separate system — recorded there, not rebuilt here; **2026-08-11 (from 05): the jungle is now explicitly one arm of the central strategic choice** — unique items and power-ups plus a smaller gold drop, weighed against pushing lanes for gold and map control — recorded, not rebuilt; **⚠ 2026-08-11 later the same day (from 05): the jungle's reachability is now a function of the front line** — how much of it your hero can work is set by how far the lane has been pushed, and conceding ground **closes your own jungle toward your base**. The other arm now **gates access** to this one — recorded, **not rebuilt**; **⚠ 2026-08-12/13 — REBUILT AGAIN from his play-test of the prototype.** **The jungle is SEMI-OPEN** — *"a forested area with clear openings and paths to traverse and little pockets where the creeps will hang out"*, and *"the hero does walk through the jungle. It is accepted"* — a **clarification of what the jungle physically is, NOT a reversal of destructible trees**, which stand along with aggro-pull geometry. **New requirement: traversal must be a much better experience** — routes, angles and choices, **not** sightline denial, which he ruled out himself. **The symmetry tension is DISSOLVED** — rotational stays for fairness, mirror-with-a-ruled-axis goes; **the distinction is a firstmate reading and his reaction to the built result is not yet recorded.** **Hero intent is decided: one tap attack-move, two taps move**, because *"panic is spammy"*; **tap-to-move is VALIDATED BY PLAY** (*"the tap to move is actually really good"*). **Still open and now the sharpest input question: how a spam sequence swaps to a single-tap intent on a dime** |
| 13 | Prototype — sixty seconds of a match | resolved |
| 14 | Pre-match setup & the pre-game state | open, **new**; **2026-08-11 (from 05): the hero talent-tree idea would put a pre-match pick in the design** — *"a variable you choose prior to starting the game"*, two or three imbue options per hero. **Floated, unchosen** — recorded, not rebuilt; **⚠ 2026-08-11, backlog answers (from 05): he did not recognise the talent-tree idea as his own**, asking whether it meant a hero aura — **it did not; it was about where the *options* for an imbue come from.** **Owed a plain restatement, not a decision**, and a **third thread** now exists (the home field absorbing the structure's creep buff). Recorded, **not rebuilt** |
| 15 | Heroes — stats, roles, differentiation | open, **substantially answered**; standing orders added 2026-07-26; **2026-08-11 (from 05): the leash bounds where a hero may roam — it does NOT change how the hero is steered** (still coarse standing orders), and **whether that meets the per-lane-pool condition is not stated**; separately the **talent-tree idea** gives each hero *"two or three ways that they can affect it"* — recorded, not rebuilt; **⚠ 2026-08-11 (from 12): the hero-autonomy line is AMENDED — *"A hero is not fully autonomous"*, and control is DECIDED as tapping the map** (joystick and preset buttons not chosen). **This ticket still carries the superseded *"you don't get to control your hero directly"* phrasing, stated twice, and is NOT rebuilt** — read it against the amendment. **Whether tap-to-move meets the per-lane-pool condition is not stated by him.** **Newly open: move versus attack-move through one tap — prototype work**; **⚠ 2026-08-12/13 (from 12): tap-to-move is VALIDATED BY PLAY** (*"the tap to move is actually really good"*), and **hero intent is decided — one tap attack-move, two taps move only**, his rationale being that **panic is spammy so spam must resolve to fleeing.** **What remains open is how a spam sequence swaps to a single-tap intent on a dime.** **Whether any of this changes the per-lane-pool condition is still not stated by him.** Recorded, **not rebuilt** |
| 16 | Deckbuilding — 100 cards, bring 20 | open; **⚠ 2026-08-11 (from 05): the card system is RESET to its goal** — deck size is one of the specifics **set aside**, and **no shape is chosen.** Recorded, **not rebuilt** |
| 17 | Gold and items — the in-match economy | open, **flat-vs-tiered fork**; **2026-08-11 (from 05): gold is earned whenever the hero kills a minion (last-hitting explicitly will not work), lanes pay more gold than the jungle, the jungle pays unique items and power-ups plus a smaller gold drop, and gold buys similar-but-not-identical power-ups at the main base** — this is where hero power is bought. Recorded, **not rebuilt**; the economy items are **parked by his own scope instruction** |
| 18 | Slice sequencing — what ships | open, **new**, standing gate |

## Not yet specified

- **⚠ THE EARLY-RUSH BRAKE — a requirement, unmet.** `[open]` 2026-08-11, **in
  his words**: *"As much as I don't want towers because it's prototypical, there
  needs to be some mechanism to prevent someone from just blowing down the mid
  lane or any lane at the beginning of the game and having nothing to stop
  them."* **This is a constraint on all future design, not a proposal and not a
  solved problem.** It arrived because cutting the forward structure removed the
  brake, and he then named the brake **independently of the object that used to
  supply it** — the tower's real job in his own framing being *"a way to slow the
  game down because you're not strong enough to pass without huge risk."*
  **⚠ The tension is deliberate and is not a defect:** he **does not want towers,
  because they are prototypical**, **and he requires the function towers
  perform.** **His standing `[committed]` test narrows it further** — a brake
  that merely makes units take longer to arrive **is already rejected.** **One
  candidate exists and is unchosen** (the home field, below). **Whether the leash
  itself supplies part of the brake is unanalysed and must not be assumed.** 05.
  - **✅ MET 2026-08-11 by his decision — the shrinking home field is locked in.**
    *"I think we are going to go with the force field, so let's lock that concept
    in."* **The requirement text above stands and still governs every future
    proposal**, including the `[committed]` test that a brake which merely adds
    delay is already rejected; **what changes is its "unmet" status.** **Whether
    the leash also supplies part of the brake is still unanalysed** — now a
    question about **overlap**, not sufficiency. 05.
- **⚠ The shrinking home field — floated, NOT adopted.** `[open]` 2026-08-11.
  **His concept, offered as a candidate for the requirement above**, his own
  framing: *"it's an interesting concept."* The **home base emits a field**,
  **minions inside it are empowered**, and **the field retracts over the match**.
  Aimed at *"if someone chooses to just push too far down the middle lane, then
  they end up facing slightly stronger creeps, which slows their progress."*
  **Its shape, in his own correction: a hard defensive floor that holds no matter
  how badly a lane is being lost** — the attacker can only take the part the aura
  is not buffing, *"and that line will be defended"* — **not** a decaying
  advantage. **The retraction is a schedule of legitimacy**: the aura starts
  *"very far out, technically midpoint"* and pulls back, so by the time a push to
  a given depth is possible **the match is no longer early enough for it to count
  as too soon** — **the schedule defines the game's phases.** **Awaiting his
  decision.** Open beneath it, none of it put to him: **readability** of an
  indirect cause, the **interaction with the gold rule** (empowered home creeps
  kill without the hero, which may cut the defender's own income), and **whether
  it stacks with the leash or replaces part of it.** 05.
  - **✅ ADOPTED 2026-08-11 — it is no longer floated.** See the decision entry in
    "Decisions so far". **The three questions beneath it are untouched and still
    open, and none has been put to him.**
  - **🔧 2026-08-13 — expression answered, one question partly addressed, and a
    new mechanic attached.** The field is **a boundary marked in the lane, not a
    drawn volume**, which bears on **readability** without closing it; the
    **gold-rule interaction** and **whether it stacks with the leash** are
    **untouched and still unasked**. **New: the buff LINGERS** for a period after
    a minion leaves the field, **so the line cannot be camped** — his mechanic,
    **its duration not a decision**. 05.
- **🆕⚠ Whether the lingering buff is MEANT to soften the field's retraction.**
  `[open]` 2026-08-13, **and it has NOT been put to him.** The retraction is on
  record as **a schedule of legitimacy that defines the game's phases**; a buff
  that persists past the field's radius **makes that boundary a gradient in time
  rather than a cliff.** **Surfaced independently by firstmate and by the
  prototype worker** — recorded for that reason rather than assumed either way.
  **Not framed as a defect, and not resolved.** 05.
- **⚠ Where the imbue lives, now that there is nothing to imbue.** `[open]`
  2026-08-11. The structure-imbue card use is **homeless unless the imbue moves
  onto the hero**, and his own **talent-tree idea** — *"either hero choice or
  maybe like a variable you choose prior to starting the game"* — **may
  complement the card-imbue loop or replace it.** **He did not say which; do not
  decide it.** **Answered alongside it:** an imbue **is visible to the
  opponent.** Reaches 14 and 15. 05.
  - **🔧 Developed 2026-08-11, still not closed — there are now three threads.**
    **(1)** hero talents, above. **(2)** **the retracting home field absorbing
    what the structure did for nearby creeps** — his own proposal, *"that could
    now be the fading force field type thing that's buffing the minions"* — which
    **trades a prepared per-event card decision for an automatic, positional
    constant.** **(3)** staying in the hand. **He has chosen none.** **⚠ And he
    did not recognise the talent-tree idea as his own**, asking whether it meant a
    hero aura buffing nearby minions — **it did not; it was about where the
    *options* for an imbue come from.** **Owed a plain restatement, not a
    decision.** 05.
- **🆕 How a pushed-back player pushes the line back.** `[open]` 2026-08-11, his
  words: *"I'm not really sure of what the mechanism is to help them push the
  line back to be able to even the odds."* Under the leash, being pushed back
  **shrinks your farm, which weakens you, which makes pushing back harder.** **He
  did not frame it as a snowball concern**, but it is the same shape as the
  leash's known snowball risk, and the `[committed]` deliberate-losing rail
  **constrains any answer.** **No candidate exists.** 05.
- **🆕 Something that pushes the game toward an ending.** `[open]` 2026-08-11 —
  *"Not literally a berserk timer, just some mechanism that pushes the game
  towards an ending."* Sits alongside the existing anti-stalemate requirement.
  **⚠ Flagged, not assumed: the retracting home field may already be this**,
  since its retraction makes deep pushes progressively legitimate. **Whether it
  suffices alone, or whether a separate end-forcing device is wanted, has not
  been asked.** 05.
- **The mechanism for event lane placement.** `[open]` 2026-08-11 — **the
  principle is answered** (*"some sort of combination of both"*: the player
  **influences** placement **without outright selecting** the lane), **the
  mechanism is commissioned and unchosen.** Its live sub-question is
  **disclosure** — whether the opponent sees your placement before committing.
  **A finding from the commissioned work, recorded as a finding and not put to
  him:** **the variable that must not be fully controlled is the collision, not
  the lane**, and **determination and disclosure are separate dials.** 05.
- **Whether a hold-position order exists.** `[open]` 2026-08-11 — **not ruled in
  or out.** *"It's probably not difficult to just put one in somehow, but it needs
  to be, if it is going in, be extremely easily accessible and cancellable."*
  **If it exists, accessibility and cancellability are requirements, not
  polish.** He also raised a **factual uncertainty about how MOBAs actually
  behave** when two heroes stand adjacent — **owed a plain answer.** Related to
  12's **move-versus-attack-move** problem; **neither settles the other.** 05, 12.
- **⚠ The card system, reset to its goal.** `[open]` 2026-08-11 — *"Yeah, I'm not
  really sure how to approach this one anymore."* **Hand size, the freeze slot and
  deck size are set aside** in favour of his restated goal: a card/power-up/spell
  system that adds **flavour and customisation**, feels like **one of only a few
  core parts of the game**, is **simple enough to be easy to learn and fun**, and
  **complex enough to feel mentally rewarding and implementable at a high skill
  level, like real strategy.** **Commissioned work puts five shapes on the table
  and none is chosen — do not adopt one.** **Its central finding, recorded as a
  finding and not as his:** **combining is currently unpriced**, so
  *combine-everything-every-time* is the dominant line and **the mechanic 02 calls
  the keystone has no decision in it.** Bears on 02, 11, 16. 05.
- **Whether telegraphed events are shared or mirrored** — one contested point, or
  two parallel ones. `[open]` 2026-08-11, and named in the decision record as
  **the sharpest open question**. **Now layered with lane placement**, which he
  left as **player-chooses or mechanism-determines, picking neither** — and with
  the unasked companion, **whether the opponent sees your lane choice before
  committing.** 05.
- **Rehousing the hero-in-lane card as a temporary leash extension.** `[open]`
  2026-08-11 — **a rehousing, not a deletion**, and its concrete form is
  unspecified. 05.
- **⚠ The leash's snowball risk.** `[open]` 2026-08-11 — winning a lane
  compounds: more ground → more reach → more income → more ground. **It passes
  the `[committed]` deliberate-losing rail** (a thrower gains nothing) **but it
  risks blowouts**, which is the *other* failure mode that rail's
  preventive/restorative split exists to name. **An open risk, recorded and not
  solved.** 05.
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
  - **⚠ Touched but not answered 2026-08-11.** The leash **bounds where the hero
    may roam** — it does **not** change **how** the hero is steered, which is
    still coarse standing orders. **Whether that counts as position becoming
    "more manually manipulable", and so whether the per-lane pool comes back onto
    the table, is not stated by him and is not inferred here.** Separately, the
    **hero-in-lane card is to be rehoused as a temporary leash extension**, which
    remains a card effect with a timer. 05, 15.
  - **⚠ AMENDED 2026-08-11 by 12's dumps — the "steering is unchanged" reading
    above is superseded.** *"A hero is not fully autonomous"*, and **control is
    decided: tapping the map** (the joystick and the preset move-to-area buttons
    are **not** chosen). **What that does to the per-lane-pool condition is NOT
    stated by him and is not inferred here** — whether tap-to-move counts as
    position becoming *"more manually manipulable"* is his call, not this map's.
    **Newly open in its place:** how **move** and **attack-move** are both
    expressed through **one tap** — recorded as **prototype work**, his concern
    being that a locked-in wrong intent *"will feel really bad."* 12, 15.
  - **✅ VALIDATED BY PLAY 2026-08-12** — *"the tap to move is actually really
    good."* The control decision is no longer only argued; it is played. **What
    that does to the per-lane-pool condition is still not stated by him** and is
    still not inferred here. 12, 15.
- **⚠ How a fast tap sequence resolves into intent — the sharpest open input
  question in the design.** `[open]` 2026-08-13, **his words**: *"how do you spam
  tap to force your hero to move without attacking really quickly, but then
  somehow swap on a dime to the last tap being taken as a single tap?"* **The
  assignment is settled** — one tap attack-move, two taps move — **but with
  tap-count semantics a rapid sequence is ambiguous by construction**: every
  single tap must wait out the double-tap window, so **either attack-move is
  delayed or a fast run of moves is chopped into alternating intents.**
  **Unresolved.** The prototype carries an implementation and its cost;
  **cited, not adopted, and he has not reacted to it.** 12, 15.
- **🆕 What makes jungle traversal interesting.** `[open]` 2026-08-13 — *"the
  ability to traverse the jungle needs to be made a much better experience"*:
  **routes, angles and choices about which way to go, not corridors with
  alcoves.** **Explicitly NOT sightline denial** — he ruled that out himself,
  since there is no fog and a minimap shows both heroes at all times. **A
  requirement with no accepted answer**, and it **raises the price of the
  commissioned what-the-jungle-contains question** without answering it. 12.
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
  - **Updated 2026-08-11.** **The forward-spawn variant is NOT dead** — *"I don't
    think it's dead. Just need to figure out how that functions."* So this question
    is live at the **mechanism** level. **Rare units at the forward structure were
    briefly the candidate answer and were cut *"for now"***, which leaves the
    mechanism with no candidate again. Meanwhile the main base **gains a job inside
    05's own material for the first time**: it is where **gold buys power-ups**
    and where **units are upgraded** — the tech-tree work above is now load-bearing
    for 05's central axis rather than adjacent to it. 05.
  - **⚠ Untouched by the leash decision later the same day.** Where creeps spawn
    was never a property of the forward structure, so **cutting the structure
    neither kills nor answers this** — the forward-spawn variant is **still
    alive with no mechanism.** The main base's job — where gold buys power-ups
    and units are upgraded — is **unaffected.** 05.
- ~~**What the forward structure DOES.**~~ **⚠ THE SUBJECT IS CUT 2026-08-11 —
  entry kept as history.** There is no forward structure; see the leash entry in
  "Decisions so far" and the reversal log. **The rejections and the `[committed]`
  test below outlive the object and still govern.** Original entry follows.
  **Substantially answered 2026-08-07 /
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
  - **⚠ MOOT 2026-08-11 — subject cut, not answered.** **There is no forward
    structure.** The 2026-08-07/09 answer, and every candidate ever proposed for
    it, lose their subject. **What outlives the object and still governs:** the
    two rejections (**guards**, **vicinity buffs**) and the `[committed]` **test**
    — which now bites hardest on the **early-rush requirement**, since that
    requirement asks for the *function* a tower performs while the test bars any
    answer that merely adds delay.
- **What is still open inside the forward structure.** `[open]` 2026-08-09 —
  the **concrete list of event types** beyond his two named examples (killing a
  large unique minion; a structure-ability defence), the **exact event timing
  offsets** within the assumed 15 minutes, and the **defend-bonus design** (a
  bonus for defending successfully, versus merely avoiding the loss — floated,
  undecided). **Deferred, not rejected:** multi-structure **step-down defence
  lines**, held until playtesting shows real match length and map size. 05.
  - **Updated 2026-08-11.** The **event-type list is now commissioned work** — the
    user asked for a brainstorm of existing-game and novel ideas to bring back to
    him; **do not propose types in this map or in 05.** The imbue loop **raises its
    price**: an event type now needs a **stated nature to counter-prep against**,
    not just a name. The **defend-bonus** lost its stated rationale when rare units
    were cut, and **whether he still wants one is unstated, not withdrawn**.
    **One structure remains the starting test**, now with a reason: map size and
    minion travel time are unknown and the game is mobile and short. **Newly open:
    what imbuing concretely does to a structure**, and **how the structure's stake
    is stated concretely enough to make pushing compete with farming.** 05.
  - **⚠ Sorted 2026-08-11 by the cut, text above kept as written.**
    **Survives:** the **event-type list as commissioned work** (with the brief
    narrowed — **no type may assume a defended building**), the **timing
    offsets**, and the **~5-minute cadence**. **Moot:** the **defend-bonus for
    holding a structure**, **one-structure-as-the-starting-test**, **step-down
    defence lines** (deferred, never rejected — that record stands), and **what
    imbuing does to a structure**. **Rehoused:** the structure's stake becomes
    **what holding ground pays** — reach. **New in its place:** **whether an
    event pays a bonus for being dealt with**, which **has not been put to
    him.** 05.
- **⚠ Live cut candidate — hero strength affecting structure power.** `[open]`
  2026-08-09. It is **in tension** with **card-selected-only garrison
  abilities**, and the user **agreed the concern is real** rather than dismissing
  it. **Neither side is chosen; do not resolve this by picking one.** A second,
  independent watch-item from the same session: the **card-based prep/customisation
  portion adds its own balance surface** to design and test. 05.
  - **⚠ Made conditional, then left open by the cut, 2026-08-11.** Asked
    directly: *"I guess if we are cutting forward structures then it doesn't make
    sense, but if we're keeping them then we should explore it."* **The
    structures are cut, so on its face it dies with them** — but in the same
    breath he floated **two alternatives that need no structure**: *"auras on
    heroes is another way. Or the even the forward structure generating some sort
    of aura."* **So whether hero strength expresses itself spatially at all is
    still open, and neither alternative has been ruled on.** Both express
    strength **spatially rather than through direct control**, which fits the
    `[committed]` commander framing. 05.
- **What crossing the hero power threshold concretely means.** `[open]`
  2026-08-09 — a **hard gate** that flips the hero into a win-capable state, or a
  **continuous power curve** with no sharp line; and **how it is tuned** against
  the assumed 15-minute match and ~5-minute event cadence, so games neither end
  in an early blowout nor drag on past the threshold with no resolution. **The
  user called the specifics wishy-washy himself.** Also open: **what becomes of
  reinforcement exhaustion as a loss trigger** now that the threshold is the loss
  condition — unstated. 05.
  - **Updated 2026-08-11.** The exhaustion half is **answered — it is not a loss
    trigger** (see the decision entry and the reversal log). On the threshold
    itself: **leaning away from a hard gate without choosing** — *"I don't think
    it's a hard gate. Maybe it is, I don't know."* **The firm requirement
    underneath is durable: there must be a resolution line, because if both sides
    can defend it cannot be a stalemate**, and his concept for it is an **"exodia
    moment"** (*"if the hero reaches some sort of exodia moment, then they just
    win"*) — **concretely undefined**. **Tuning and the power-to-win conversion
    are explicitly unknown in his own words** and **parked by his own scope
    instruction.** 05.
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
  **⚠ Updated 2026-08-11: the forward structure is cut, so nothing is in the lane
  at all** — and the **pacing gate's job has been restated by him as a standing
  requirement**, the early-rush brake at the top of this section. The two objects
  were always distinct; **now only the job survives, and it has no object.**
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
  - **⚠ Restated by the user himself 2026-08-11, and promoted.** After the
    structure was cut he named this job as a requirement in his own words — *"there
    needs to be some mechanism to prevent someone from just blowing down the mid
    lane or any lane at the beginning of the game"* — while **still not wanting
    towers, because they are prototypical.** **The design brief here is unchanged
    and the requirement entry at the top of this section is the live form of
    it.** One unchosen candidate exists: the **shrinking home field**. 05.
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
  - **A further claimant, 2026-08-11: the leash readout.** The player must see
    **at a glance where the hero may legally go**. **A stated cost of the leash
    decision, recorded as an open risk** — four jobs now compete for one quarter
    of a phone. 05, touches 01.
  - **🔧 Partly structured 2026-08-11 — the bar now has a layout, and swapping is
    accepted.** **Three panels: cards left, both heroes' progress and power in a
    wider middle, right undecided** — see the decision entry in "Decisions so
    far" and [01](issues/01-battlefield-geometry.md). **The competition is
    loosened, not settled:** *"If another lever is required, but no space, need
    an option to toggle/swap it visible when needed"* means **the bar need not
    allocate a permanent slot per job.** **Which lever holds the fixed right slot
    is undecided**, with four candidates recorded and none chosen, and **the
    minimap and the leash readout are still claimants.** 01.
- **Whether any gesture survives.** The "never drawn symbols" rejection still
  binds, but with casting reduced to selection it is unclear whether flicks and
  drags remain anywhere — combining cards together, steering the hero (15 asks
  this), or nowhere at all. Tap-only is now a live possibility that nobody has
  chosen.
  - **One of the three is answered 2026-08-11: steering the hero is a tap on the
    map.** **Combining** is still unstated, and **tap-only overall is still
    unchosen** — do not read the control decision as settling the rest. 12.
- **⚠ Whether invading the opponent's jungle is possible at all.** `[open]`
  2026-08-11 — his own conditional, *"if we give that the ability to do that."*
  **If it is:** invasion **pays reduced gold and no items** rather than being
  forbidden, and **the penalty is time-boxed with the measure undecided** — he
  offered **five minutes**, **3%** and **50%** and **chose none**. **⚠ His stated
  purpose is preserved exactly: it is an anti-stomp device aimed at stronger
  players rolling new ones** (*"to prevent like smurfs from just like rolling new
  players"*), **not a lever between equals** — a player-experience decision whose
  numbers happen to be tuning. **Whether the leash, the home field and this are
  all needed to bound early aggression has not been put to him.** 12.
- **⚠ Jungle symmetry — direction given, tension unresolved.** `[open]`
  2026-08-11. **He wants it not totally symmetrical**, for variety: *"I would like
  it to not be totally symmetrical, so that way depending on what side you end up
  getting for that map, maybe there's a difference."* **The tension is his and is
  not resolved:** *"I'm not sure how to weigh the repetitiveness of symmetry
  versus the potential benefits you get from being on a certain side versus ones
  you don't."* His **League** and **Heroes of the Storm** remarks are
  **references describing shapes, not requests.** **Do not resolve it.** 12.
  - **✅ DISSOLVED 2026-08-13 — the two halves were never in conflict.**
    **Rotational symmetry (fairness) stays; mirror symmetry with a ruled axis
    (the NASCAR read) goes**, and **irregular internal geometry carries the
    variety.** **His direction is satisfied, not overridden.** **The distinction
    is a firstmate reading, and his reaction to the built result is not yet
    recorded.** See the decision entry above. 12.
- **What the jungle actually contains.** `[open]` 2026-08-11 — **commissioned as
  its own session** at his instruction: *"this is going to have to be its own
  giant dump."* A brainstorm report exists outside this repo and is **cited, not
  adopted**; **no contents are proposed in this map or in 12.** 12.
- **Whether anything leaves the jungle for a lane (ladder rung 4).** `[open]`
  2026-08-11 — **the shape is settled if it happens** (a **timer or cadence, not
  continuous**); **whether an unclaimed neutral can do it on its own is
  unresolved**, *"I don't know what that one."* Note **rung 4a is adopted** and is
  a different object — a **claimed** camp marching your lane is **the player
  acting.** 12.
- **How trees, terrain manipulation and jungle geometry relate.** `[open]`
  2026-08-11 — **not asked.** Trees are destructible walls that change where lane
  creeps can be aggro-pulled; terrain manipulation already blocks hero passage
  with a tree root. **His instruction was to keep them live and not collapse
  them into one system or split them into three by inference.** The **chasm** was
  the third member and is **cut *"for now"***. 12.
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
