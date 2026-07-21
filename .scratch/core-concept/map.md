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
- Core loop: accrue cards → **combine into a compound spell** → **gesture to
  cast** → aim into a lane.
- **Gestures are flicks, drags and aims — never drawn symbols.** No tracing
  shapes to cast. Physical and fast, not notational.
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

### The central risk

**Design against it, not around it:** combining is deliberate and puzzle-like;
real-time is pressure. Those two fight each other. **Ticket 04 owns this.**

It got materially worse on 2026-07-21. Heroes, items, gold and deckbuilding all
add things to know and things to watch, and every one of them spends the same
budget the combining mechanic needs. 18 exists because of this.

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
- **Hero death is the loss condition** `[provisional]` (2026-07-21) — see
  [15](issues/15-heroes.md), [05](issues/05-match-shape-win-condition.md). The
  mechanism of death is unresolved.
- **The hero works the jungle, automatically** `[provisional]` (2026-07-21) — see
  [15](issues/15-heroes.md), [12](issues/12-jungle-role.md).
- **~100 cards, ~20 brought per match; all deck cards available in-match**
  `[provisional]` (2026-07-21) — see [16](issues/16-deckbuilding.md). This killed
  higher-tier merging as banking's payoff.

## Ticket index

Rebuilt 2026-07-21. Blocking edges are weaker than they look — see the working
method; treat them as "this informs that," not as a build order.

| # | Ticket | Status |
|---|---|---|
| 01 | Battlefield geometry & phone readability | open |
| 02 | What "combining cards" actually means | resolved + amended |
| 03 | Gesture as skill expression | open |
| 04 | Pressure vs. complexity — the learning curve | open |
| 05 | Match shape & win condition | open, partially answered |
| 06 | Unlock progression & the hook | open, **needs revisit after 16** |
| 07 | Monetization model | open |
| 08 | Consolidation pass | open (terminal) |
| 09 | Banking — combining over time | open, **rewritten** |
| 10 | Information — what you see of your opponent | open |
| 11 | Card accrual economy | open |
| 12 | The jungle — role and autonomy | open, updated |
| 13 | Prototype — sixty seconds of a match | resolved |
| 14 | Pre-match setup & the pre-game state | open, **new** |
| 15 | Heroes — stats, roles, loss condition | open, **new** |
| 16 | Deckbuilding — 100 cards, bring 20 | open, **new** |
| 17 | Gold and items — the in-match economy | open, **new** |
| 18 | Slice sequencing — what ships | open, **new**, standing gate |

## Not yet specified

- **What banking is for.** The shape (bank-or-cast under pressure) survives; the
  payoff does not. 09 carries four candidates and one garbled instruction about
  whether banking is shelved.
- **The ultimate.** *"I do like the ultimate idea"* — wanted, but no longer
  banking's payoff. Currently homeless.
- **What mana does.** Heroes have mana; cards cost none. A stat without a verb.
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
