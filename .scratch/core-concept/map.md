# Map: Core Concept

Label: `wayfinder:map`

## Destination

A game design concept doc covering combat, map, progression, and monetization —
deep enough to build a vertical-slice prototype from, and to judge whether this
is worth committing to.

## Notes

**Domain:** real-time mobile lane-battler with compound spellcasting.

**Skills every session should consult:** `/grilling`, `/domain-modeling`,
`/prototype` for anything with a "how should it look or feel" core.

**Locked constraints — do not re-litigate these without saying so explicitly:**

- Real-time, **cooldown-based**. There are no turns. Cards accrue on a timer.
- Three lanes on a **Dota-shaped** map — bending lanes, forest/jungle, terrain
  that matters — scaled down for a phone. Explicitly *not* Clash Royale's bare
  vertical tracks.
- **Automated creeps** march and contest lanes. Players influence lanes; they do
  not directly control an army.
- **Creeps are units, not a meter.** The front line emerges from individual
  creeps meeting and fighting. A tug-of-war bar or fill-percentage abstraction
  has been explicitly rejected twice — do not reintroduce it.
- Core loop: accrue cards → **combine into a compound spell** → **gesture to
  cast** (skill-based execution, not tap-and-resolve) → aim into a lane.
- **Gestures are flicks, drags and aims — never drawn symbols.** No tracing
  triangles or rectangles to cast. Physical and fast, not notational.
- **The jungle must be mechanically live, not scenery.**
- **When accessibility and novelty conflict, accessibility wins.**
- PvE and PvP are both intended modes.
- **All cards are obtainable by every player. None are purchase-exclusive.** But
  they are not all unlocked on day one.
- Monetization must be light and genuinely non-resented.

**Standing preference:** the user intends to rabbit-hole each ticket in depth.
Ticket sessions should go deep, not broad — breadth is this map's job, not a
ticket's.

**Known keystone:** ticket 02 (combining) blocks three others and is where the
design either has a soul or doesn't. Prefer it when choosing freely.

**Central risk to design against, not around:** combining is deliberate and
puzzle-like; real-time is pressure. Those fight each other. Ticket 04 owns it.

**Ordering principle:** resolve what *constrains* before what *adapts*. The
blocking edges encode this. Resolving a peripheral ticket ahead of the keystone
it depends on is how this map generates rework.

**Reversibility rail:** every decision in `## Decisions so far` is tagged
`[committed]` or `[provisional]`. Provisional means: good enough to build the
next ticket on, not yet load-bearing enough to defend. Most decisions should be
provisional for most of this map's life — tag honestly rather than
performing certainty. Ticket 08 is where provisional decisions get promoted or
revised.

**Explore-then-commit:** for any ticket whose answer cascades, put 2–3 candidates
on the table and trace each forward through the tickets it affects *before*
choosing. A decision made with its downstream wake visible is a different act
from a decision made blind.

**Build from the user's words, not from this map's summary.** The sixty-seconds
prototype rebuilt a tug-of-war bar the user had already rejected, because the
agent worked from a compressed gist instead of the transcript. Before building
anything concrete, re-read what the user actually said about it — a summary is
lossy exactly where a correction lives.

**Prototypes must be observed running.** The first prototype was unusable due to
a render bug that a syntax check could never have caught. If no browser is
available, say plainly that the artifact is unverified rather than implying it
works.

**A prototype cannot test feel until it is teachable and survivable.** Ship a
guided first run and a passive-by-default opponent, and label crude parts as
crude. Otherwise a reaction of "unintuitive" or "not fun" measures the missing
tutorial and the beating, not the mechanic — and must not be recorded as design
evidence. This already happened once on
[Prototype — sixty seconds of a match](issues/13-prototype-sixty-seconds.md).

## Decisions so far

<!-- one line per closed ticket: gist + link + [committed]/[provisional] -->

- [What "combining cards" actually means](issues/02-combining-mechanic.md) —
  at-cast combining is **payload + modifiers** `[provisional]`; accessibility
  beats novelty `[committed]`; shape-composition dead once gestures were ruled
  to be flicks not drawn symbols `[committed]`; elemental recipes rejected on
  learning-curve and authoring cost `[committed]`. Ticket was mis-scoped — the
  rest of the card system split into 09–13.
- [Prototype — sixty seconds of a match](issues/13-prototype-sixty-seconds.md) —
  mostly **failed as a feel test**, which is the finding. Creeps must be units
  not a meter `[committed]`; 60s is far too short `[provisional]`; the bank was
  the only positive signal `[provisional]`. "Unintuitive" was **confounded** by
  no tutorial + crushing AI + crude mock, and says nothing about combining — an
  earlier claim to the contrary is retracted. Modifier cap / reversibility /
  card interval got no signal and return to 09 and 04. Next prototype needs a
  guided first run and a passive-by-default opponent.

## Not yet specified

- **Deployable units to bolster a lane.** The user floated units as well as
  spells. May fold into 09 (banking) or 12 (jungle) rather than standing alone —
  revisit once those land.
- **What "RPG elements" concretely means.** Stated as wanted, never defined.
  Mastery? Heroes? Levels? Crucially: does any of it touch power?
- **Meta-progression outside the real-time match.** The user asked what exists
  between matches. Partly owned by 06 (unlocks) and 11 (accrual), but the
  broader shape — is there anything else out there at all? — is unexamined.
- **The three unpicked merge outcomes.** 09 picks one for the vertical slice;
  higher-tier cards, transmutation and ultimate-charge remain wanted expansion
  space, unscheduled.
- **PvE mode design.** AI opponents, campaign, co-op — all unexamined.
- **Real-time PvP netcode feasibility.** A genuine go/no-go risk for a
  real-time mobile game; flagged, not yet assessed.
- **Matchmaking fairness across unlock states.** If players have different
  unlocked pools, PvP matching gets harder. Depends on 06.
- **Session length for mobile contexts.** Commute-length play vs. long matches.
- **Art direction and tone.**

## Out of scope

- Engine, stack, and platform choice — build decisions, not concept decisions.
- Art production pipeline.
- Naming and branding.
- Funding, team, and publishing.
