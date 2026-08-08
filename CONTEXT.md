# Mobile Game (working title) — Core Concept

A real-time mobile lane-battler with compound spellcasting, currently in
concept-design phase (no code yet). Single-context repo — the canonical design
artifact is [`.scratch/core-concept/map.md`](.scratch/core-concept/map.md); this
glossary pins down the vocabulary that recurs across it, its 18 tickets, and the
feel prototypes. Terms marked "open" or "unresolved" are genuinely unsettled in
the source material, not simplified for this document — check the linked ticket
before treating them as decided.

## Language

### Core loop & casting

**Card**:
The base unit of player action. Cards accrue automatically on a timer
(cooldown-based, never turn-based) and are combined at the moment of casting
into a compound spell. ~100 cards exist total; a player brings ~20 in a deck.

**Compound spell**:
The result of combining cards together at cast time — the thing a player
actually casts. Built from the payload + modifiers model (see below).

**Payload + modifiers**:
The chosen model for at-cast combining: one card is the spell's body (the
payload), other cards modify it (+damage, splits into three, applies a slow).
Chosen over elemental recipes and shape/positional composition because it
degrades gracefully (a bare payload still works) and doesn't require gestures.
_Avoid_: Elemental recipes, shape/positional composition — rejected as the
general combining model.

**Casting is selection**:
The rule that casting a compound spell means choosing a target — a lane, the
jungle, or a hero — not performing a skilled physical action to aim or execute
it. `[committed]`, reversed from an earlier gesture-based model.
_Avoid_: Skill-shot casting, gesture-to-cast, aiming — the rejected model this
replaced. "Never drawn symbols" still binds any touch interaction that remains.

**Target class**:
One of four things a compound spell can be aimed at: help your hero, help your
lane, hurt their lane, or slow their hero. Settled; *target resolution* — a
whole lane vs. a point or region within it — is still open.

**Accrual**:
The timed, automatic arrival of cards into a player's hand. Whether the rate is
fixed for everyone or influenceable in-match is open; any out-of-match or
purchasable way to influence it would violate the match-bound-power
constraint, so this must not be decided by drift.

**Recipe**:
One of a small, fixed set (provisionally 3–4, each with few ingredients,
explicitly taught) of preset card combinations that make the hero perform a
jungle action affecting map state. The current home for *transmutation*.
_Avoid_: Elemental recipes — a different, larger, rejected combining model that
shares the word "recipe" but not the mechanic.

**Transmutation**:
The idea that certain card combinations produce a map-changing effect via the
hero acting in the jungle, rather than the original "two cards become a third
card" reading (rejected). Implemented as a Recipe.

### Battlefield, camera & information

**Lane**:
One of three bending paths (Dota-shaped, explicitly not Clash Royale's bare
tracks) that automated creeps march down and contest. Jungle sits between
lanes.

**Jungle**:
The off-lane terrain between lanes. Playable space — spells and the hero's
automated actions can affect it — and not a wall: the hero must be able to
traverse it lane-to-lane. Lane creeps stay out of it unless pulled in by aggro.

**Aggro**:
A creep's threat/targeting state. A lane creep pulled into the jungle by aggro
snaps back once aggro is lost; otherwise lane creeps do not enter the jungle.

**Creep**:
An individual automated unit marching and fighting along a lane. Creeps are
units whose individual combat produces the front line.
_Avoid_: Tug-of-war bar, fill-percentage, front-line meter — an abstraction
rejected twice; a v1 prototype shipped one anyway and is kept as
`*.v1-tugofwar.html.bak` as the record. ("Tug of war" as a phrase for the
back-and-forth *contest* between lanes is not rejected — only the bar/meter
abstraction is.)

**Observer camera**:
The player's camera: a pannable MOBA-observer view, dragged around a
battlefield larger than the screen, angled rather than straight-down. The
player commands from this camera and never controls a hero directly.

**Commander**:
The player's relationship to their hero and lanes — directing from the
observer camera and issuing standing orders — as opposed to being an avatar
embodied on the field. This framing is what forced the loss-condition
reversal (see Base destruction).

**No fog of war**:
The whole battlefield, including the enemy hero, is always visible (subject to
panning to it). Forced by casting-as-selection — a card cannot target what
isn't visible.

**Hidden hand**:
A player's own cards, and probably their field-manipulation/terrain
capability, are not visible to the opponent. The one deliberate reserve of
hidden information in a design that is otherwise fully open on the board:
*you always see what is happening, never quite what is coming.*

**Command bar**:
The bottom ~25% of the portrait screen (Warcraft-3-style), holding cards,
readouts on both heroes, and standing-order controls. Its stated job is to be
the *decision substrate* — every card must be judgeable against visible
battle state — not a HUD.

### Heroes

**Hero**:
A player's chosen, autonomous unit (~8 to choose from, picked before
matchmaking). Farms creeps and acts in the jungle on its own; the player never
drives it directly. Differs from other heroes by asymmetry (race, passives,
size, weapon, attack style, one novel per-hero map-affecting mechanic), not by
power level.

**Standing orders**:
Coarse priority commands a player gives their hero (e.g. "left lane," "farm
this jungle camp"). Orders set the hero's *priorities*; cards set its *power*.
Not a form of direct steering — the hero still executes automatically.

**Match-bound power**:
The constraint that all hero power variance comes only from in-match cards and
power-ups — nothing persistent, nothing purchased, no gacha. `[committed]`

**Mana**:
An unresolved hero resource. Live candidate: cards act on the jungle, lane, and
hero, while mana is what the hero spends on its own (currently unspecified)
abilities. Not chosen; whether it exists at all is open.

### Economy & deckbuilding

**Deck**:
A player's chosen set of ~20 cards (from a pool of ~100) brought into a match;
every card in it is available throughout the match, with no in-match tier
ladder. Cards can only be combined with others sharing a *common
denominator* — a still-undefined shared property (faction? keyword? element?)
that every player must learn in order to combine anything.

**Gold / items**:
The in-match economy. Hero item slots exist but are filled only in-match,
never pre-game, using gold earned from creeps and the jungle and/or item drops.
Unresolved: whether gold-earning and item-dropping are one system or two, and
whether itemization is *flat* (one version of each item, differentiated
laterally) or *tiered* (findable/upgradeable versions, a power ladder).

### Match shape & win condition — the least settled part of the design

**Base destruction**:
The current, provisional loss condition. Held under protest by the user as too
genre-typical ("so prototypical"), with no replacement chosen. Superseded an
earlier "hero death ends the match" rule, which was itself reversed once the
commander framing made the hero not the player's avatar.

**Buyback**:
A priced option to instantly end a hero's respawn timer after death. One or
two per match; hero death otherwise costs nothing but time.

**Preventive vs. restorative**:
The test applied to any comeback-dynamics candidate. A preventive device
applies equally to both players from the start and stops a snowball from ever
starting; a restorative device pays out in proportion to how far behind a
player is. Only preventive designs are acceptable — a restorative one can be
farmed by deliberately losing, which is a locked rejection.

**Pseudo-tower** (open, object undecided):
The wanted *job* of a lane obstacle: a scaling gate, too strong to pass early,
that stalls an early rush without being chased as a comeback mechanic — a
pacing device, not a catch-up device. What the object concretely *is* remains
undecided; a literal turret is rejected as MOBA-copying.
_Avoid_: Turret — the object shape explicitly rejected; only the pacing *job*
is wanted, not the building.

**Terrain manipulation**:
Player-driven reshaping of the battlefield (creating water, lava, or holes) to
impede enemy creep and hero movement. The leading candidate for a
non-copied match objective. Whether/how it feeds the win condition itself is
an open question the user raised and has not answered.

**Banking** (shelved, not rejected):
A mechanic where cards are saved rather than cast immediately, trading tempo
for a later payoff — bank-or-cast as a repeated low-load binary decision.
Shelved for lacking a payoff worth its screen/teaching cost, not rejected on
its shape. Do not reintroduce without the user's prompt.

**Accrual cost-gate** (open — possibly the same system as Banking):
A hypothesized mechanic where a sufficiently powerful effect (e.g. a terrain
effect that blocks lane traversal) must be paid for by saving up over time
rather than being a single card. Raised by the user as "just a hypothetical"
while discussing terrain manipulation, and explicitly not yet reconciled with
Banking above — whether these are one system or two is an unresolved
bookkeeping question the design has flagged against itself.

### Reinforcement-exhaustion prototype — unconfirmed, feel-test only

This subsection covers vocabulary introduced by
[`05-reinforcement-exhaustion.html`](.scratch/core-concept/prototypes/05-reinforcement-exhaustion.html),
a throwaway prototype built to make ticket 05's match shape *reactable*, not to
settle it. None of these terms appear in `map.md` yet — the prototype came
after the map's last rebuild — and its own README states it "answers nothing."
Treat everything here as exploratory material awaiting the user's reaction, not
as design decisions.

**Reinforcement pool**:
A per-side count, in this prototype, of how many creeps are left to spawn —
draining as creeps are spawned and lost. Explicitly a spawn-budget counter, not
a front-line/health meter (the twice-rejected tug-of-war abstraction — see
Creep). When a side's pool hits zero, that side's base stops spawning and only
its hero remains; whether that state should read as a loss or as a new phase
is the open question the prototype exists to surface.

**Forward structure**:
In the same prototype, a structure partway down each lane where creeps spawn,
in place of a full-lane march from a main base (which is drawn dim and inert;
what it's for is undecided). Its behaviour when destroyed is one of four
switchable, none-yet-chosen variants: *Composition gate* (changes what spawns
next), *Ownership flip* (spawning flips to feed the enemy), *Salvage
re-fielding* (surviving creeps are recovered — flagged as potentially
restorative-shaped and untested against the deliberate-losing rail), and
*Terrain anchor* (a terrain-effect card only works in a lane while its forward
structure is held). Two other candidates, *guards* and *vicinity buffs*, were
already rejected by the user on his own test ("just makes it a tower") and are
not built.
_Avoid_: Turret — considered and rejected as the forward structure's shape,
same rejection as Pseudo-tower above.
