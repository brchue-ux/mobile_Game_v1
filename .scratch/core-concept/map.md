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

- Real-time, **cooldown-based**. No turns. Cards accrue on a timer.
- Three lanes on a **Dota-shaped** map — bending lanes, forest/jungle, terrain
  that matters — scaled for a phone. Explicitly *not* Clash Royale's bare tracks.
- **Automated creeps** march and contest lanes. Players influence lanes; they do
  not directly command an army.
- **Creeps are units, not a meter.** The front line emerges from individual
  creeps fighting. A tug-of-war bar or fill-percentage has been **rejected
  twice** — do not reintroduce it.
- Core loop: accrue cards → **combine into a compound spell** → **select a
  target** — a lane, the jungle, or your hero. **Casting is selection, not
  performance.** `[committed]` **Reversed 2026-07-26** from *"gesture to cast →
  aim into a lane"*; see the reversal log.
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
| 01 | Battlefield geometry & phone readability | open; camera + portrait set; aiming surface simplified |
| 02 | What "combining cards" actually means | resolved + amended |
| 03 | Gesture as skill expression | **closed — removed** 2026-07-26 |
| 04 | Pressure vs. complexity — the learning curve | open, **eased**; now owns "where does skill live" |
| 05 | Match shape & win condition | open, answer **reversed** 2026-07-21 |
| 06 | Unlock progression & the hook | open, **needs revisit after 16** |
| 07 | Monetization model | open |
| 08 | Consolidation pass | open (terminal) |
| 09 | Banking — combining over time | **shelved** (not rejected) |
| 10 | Information — what you see of your opponent | open; **spatial half merged into 01** |
| 11 | Card accrual economy | open |
| 12 | The jungle — role and autonomy | open, updated |
| 13 | Prototype — sixty seconds of a match | resolved |
| 14 | Pre-match setup & the pre-game state | open, **new** |
| 15 | Heroes — stats, roles, differentiation | open, **substantially answered** |
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
- **Target granularity.** "Select a lane, the jungle, or the hero" does not say
  at what resolution. A whole lane, a point inside it, a region, a specific creep
  clump? This is what survives of 01's aiming-surface question and it is a real
  design axis, not a UI detail — it sets how much positional thinking the game
  has left. Owned by 01.
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
