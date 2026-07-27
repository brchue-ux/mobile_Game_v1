# Changelog

Session-by-session narrative for the mobile lane-battler concept. Read on demand
— grep it for a past decision, a reversal, or why something was tried. It is not
auto-loaded.

`CLAUDE.md` is the sibling reference and holds only what is **true right now**.
The canonical design artifact is `.scratch/core-concept/map.md`; the git history
of that file is the authoritative record of every rebuild (one commit each).

---

## 2026-07-26 — skill shots removed, the board answered, the match shaped

Four map rebuilds in one session. The largest single day of design so far, and
the first one that made the design *smaller*.

### `af6d2aa` — Remove skill shots; casting is selection, not performance

The live challenge filed on 2026-07-21 was resolved by removal. Asked directly
whether skill-shot casting exists at all, the user: *"remove it."*

- Reversed a **locked core-loop constraint**. Was *accrue → combine → gesture to
  cast → aim into a lane*; now a combined spell acts on a **selected target**.
- **Closed ticket 03 by removal, not resolution** — the file is kept as the
  record of what was cut and why.
- First simplification the design has ever taken: system count ~11 → ~10, and
  the one lost was a *dexterity* system, the expensive kind to teach.
- The central risk (deliberate combining vs. real-time pressure) **eased for the
  first time** — it had deleted the sharpest form of its own problem, a puzzle
  decision immediately chased by a dexterity test on one clock.
- Opened three questions: where execution skill lives now (→ 04), target
  granularity (→ 01), and whether any gesture survives anywhere. Tap-only became
  live and unchosen.

### `785681a` — Rebuild 01: pannable observer camera, no fog, WC3 screen split

- **Camera is a pannable MOBA observer.** The map exceeds the screen and the
  player drags around it, spectator-style, with no direct hero control. This
  reframed 01's founding question from a *fitting* problem to a *navigation*
  one, and incidentally defused the angled-view far-lane legibility cost and the
  long-standing portrait-vs-Dota-shape tension.
- **No fog of war** — forced by casting-as-selection: you cannot select what you
  cannot see. Answered 10's spatial half.
- **Screen split is Warcraft 3 zoomed out**: top ~75% map viewport, bottom ~25%
  command bar. Confirmed as a screen split, *not* a board layout — the jungle's
  position on the battlefield stayed open.
- **New principle:** cards must be judgeable against visible battle state; the
  bottom bar is the **decision substrate**, not a HUD. Given an acceptance test
  in 01.
- Jungle: playable space for spells, not a wall, lane creeps leash back on lost
  aggro. **Towers** and **aggro** appeared for the first time, unowned.
- Filed loudly: *"destroy their base"* **held under protest** (→ 05).

**Two language traps filed** — quotes that a future cold read could mistake for
permission:

1. *"you're trying to have that tug of war"* — names the back-and-forth contest,
   **not** a meter. The twice-rejected abstraction stands.
2. *"your selectable army"* — describes **Warcraft 3's** bottom bar, supplied as
   a visual reference. Not a proposal for commandable units.

**Correction taken:** the agent had proposed that terrain's job shrank and
bending lanes lost what paid for them once skill shots went. Wrong — *"you're
referencing the skill shots of the user from the cards as opposed to what the
heroes or the creeps might do."* Terrain and lane shape are paid for by hero and
creep movement, pathing, sightlines and combat. Logged as an over-extended
cascade, sibling to over-reading a rough artifact.

### `4167f48` — Rebuild 05: match shape, comeback rail, terrain manipulation

- **New locked constraint:** no comeback mechanic may reward deliberate losing.
  Rules out naive behind-bounties, catch-up gold and underdog buffs unless losing
  costs more than the bonus returns.
- **Terrain manipulation** (water, lava, holes impeding enemy traversal) became
  the leading objective candidate — spatial without skill shots, makes terrain
  mechanically live, gives the pannable camera something to pan for.
- **Standing orders** added to 15: left/mid/right lane, farm here or there. Cards
  influence hero *power*; orders influence hero *priorities*. Resolved the old
  untouchable-vs-steerable fork with a third answer, and gave the command bar a
  second job.
- Answered: concession/disconnect ends a match; hero death costs nothing with 1–2
  priced buybacks; PvE and PvP share one match shape; creeps alone almost
  certainly cannot finish a match.
- **Towers proposed and doubted in the same dump** — the job is wanted, the
  turret is not (*"copying every other MOBA that exists"*).
- Flagged, not acted on: *"cards or a crew, like stored benefits"* read as
  **accrue**, i.e. banking (09) described unnamed, with terrain manipulation as
  the payoff whose absence had got it shelved.

### `ef59c89` — 10's hidden-info answer; pseudo-towers reframed as pacing

- **The hand is hidden; the board is not.** Settled 10's drift toward fully-open
  information — which had happened by accumulation, never by a decision. The
  opponent's field-manipulation capability is probably hidden too, which is what
  stops a slow accrual from telegraphing itself. Net: *you always see what is
  happening, never quite what is coming.*
- **"I did mean accrue"** — confirmed; the commandable-squad reading is dead. But
  the stated job is **gating the cost of powerful effects** (*"that shouldn't
  just be one card"*), not 09's tempo-vs-investment, and it was held as *"just a
  hypothetical."* Left unresolved deliberately and re-framed as a **bookkeeping
  hazard**: a shelved ticket whose mechanic is in use under another name.
- **Pseudo-towers reframed by the user** from comeback mechanic to **scaling
  gate** — *"a way to just stall the game"*, preventing an early bulldoze.
  Generalised into a test for the deliberate-losing rail: **preventive beats
  restorative**.
- Giant-tree-root example recorded, plus its interaction with 12: blocking lane
  traversal is only worth playing *because* traversal is the default, promoting
  that rule from a movement detail to a pricing baseline.

### Process note

The deletion-diff discipline earned its place twice this session. The first 01
rebuild silently dropped the prototype-at-real-phone-dimensions rule and the
target-granularity enumeration; the 05 rebuild dropped 15's original
"untouchable, or steerable with a flick?" fork. All three were caught by reading
`git diff --cached` for removed lines, and restored before commit. The insertion
count would have looked healthy in every case.

---

## 2026-07-21 — charting, the hero dump, and two reversals

Reconstructed from the map and commits `ab08e82`, `baa4edd`, `5880431`,
`953b63d`, `467f39d`, `5cf17dd`.

- **Repo initialised** and the wayfinder map created. One commit per rebuild
  established as load-bearing practice, not hygiene.
- **Working method changed mid-session.** Sequential grilling was tried and
  dropped after the user, on question 1 of 5: *"you ask a single question and my
  brain forks a thousand times."* Replaced with: user word-dumps, agent rebuilds
  the map from it, confirms, waits for proceed. The design is a graph, not a
  tree.
- **Tickets 14–18 added** — pre-match setup, heroes, deckbuilding, gold/items,
  slice sequencing.
- **The hero dump** answered 05, 12 and 09 while nominally addressing 09 alone.
  Established: hero chosen pre-match, ~8 heroes, the hero works the jungle
  automatically, ~100 cards with 20-card decks, and hero differentiation as
  **asymmetry not power level**.
- **Camera decided** — a first-person UX layer over a slightly angled overhead
  battlefield. The player is a commander, not an avatar.
- **Loss condition reversed the same day it was set.** Was *hero death ends the
  match*; became *hero death is a temporary power-down, base destruction ends
  it*. The user spotted it unprompted: an autonomous hero plus a commander camera
  means the hero is not your avatar. **The camera decided the win condition** —
  the clearest illustration of how non-linear this design is.
- **Banking shelved, not rejected** — good shape, no payoff worth its cost after
  heroes, items, gold and deckbuilding. Four candidate uses preserved in 09.
- **Orientation set to portrait 1080×2400** from a hand sketch.
- **Locked:** all hero power variance is match-bound — in-match cards and
  power-ups only, no persistent or purchased power, no gacha.
- **Two over-reads retracted**: the v2 prototype's *"unintuitive"* verdict
  (confounded by no tutorial and a crushing AI) and the layout sketch (read as
  excluding the jungle, which the user had not decided).

---

## Appendix — `CLAUDE.md` as it stood before the 2026-07-26 split

Preserved verbatim so nothing was lost when CLAUDE.md was trimmed to
current-state-only. Superseded content; do not treat as live.

<pre>
# Mobile Game (placeholder name)

Real-time mobile lane-battler with compound spellcasting. Concept design is
underway; no code yet.

## Status

**Concept design in progress.** The canonical artifact is the wayfinder map at
[.scratch/core-concept/map.md](.scratch/core-concept/map.md), with its 18 tickets
in `.scratch/core-concept/issues/`. Read the map before doing anything here.

**Working method (adopted 2026-07-21) — read `## Working method` in the map
first.** One ticket per session; the user word-dumps everything they think about
it; that dump is used to **rebuild the map**, not just to close the ticket.
Confirm understanding, then wait for the user to say proceed.

Sequential grilling was tried and dropped — this design is a graph, not a tree,
and question-at-a-time forced forks faster than they could be answered.

`/wayfinder` is referenced in older notes but is **not currently installed**.
`/grilling` and `/prototype` are.

## Notes

- No name, stack, engine, or platform decisions made yet — deliberately out of
  scope until the concept settles.
- Locked design constraints live in the map's `## Notes`. Don't re-litigate them
  without saying so explicitly.
- **Rejections are append-only.** Every map rebuild carries forward every
  recorded "no" with its reason. A reversal gets flagged *as* a reversal, in the
  user's words — never silently dropped. This rule exists because a rebuild is
  precisely what lost the tug-of-war rejection once already.
- Resolved: 02 (combining = payload + modifiers, amended for small recipe sets)
  and 13 (prototype). **Closed by removal:** 03 (gesture) — the subject was cut,
  not answered. **Shelved:** 09 (banking) — good shape, no payoff worth its cost;
  not rejected.
- Provisional as of 2026-07-21: the hero works the jungle automatically; hero
  differentiation is asymmetry not power (rock-paper-scissors + one novel map
  mechanic each); ~100 cards / 20-card decks; **base destruction ends the match,
  hero death is only a temporary power-down** (reversed from an earlier
  "hero-death-loses" call — the camera made the hero a commanded unit, not the
  player's avatar); portrait 1080×2400; camera is a first-person UX layer over a
  slightly angled overhead battlefield.
- **Locked 2026-07-21:** all hero power variance is match-bound — in-match cards
  and power-ups only, no persistent/purchased power, no gacha.
- **Reversed 2026-07-26 — skill shots removed** (*"remove it"*). Casting is
  **selection, not performance**: a combined spell acts on a chosen lane, the
  jungle, or the hero. This reverses the locked core-loop constraint that casting
  is a skill-based gesture, and **closes 03**. Three things it opened: where
  execution skill lives now (04), target granularity (01), and whether any
  gesture survives anywhere. "Never drawn symbols" still stands.
- **Ticket 18's "budget" governs what ships in a build, never what gets
  explored.** It may not be invoked to discourage an idea. Define the term or
  don't use it.

## Prototype

`.scratch/core-concept/prototypes/` holds a playable feel prototype. Serve it:

```
cd .scratch/core-concept/prototypes && python3 -m http.server 8931
```

`index.html` symlinks the current version, so edits show on reload. Open it from
a phone over LAN or Tailscale — it is a touch game and does not read on desktop.

## Hard-won gotchas

- **Creeps are units, not a meter.** A tug-of-war / fill-bar abstraction has been
  rejected twice. The v1 prototype shipped one anyway; `*.v1-tugofwar.html.bak`
  is kept as the record.
- **Build from the user's words, not from a summary.** That v1 mistake came from
  working off a compressed gist that had dropped the correction.
- **Don't over-read rough artifacts.** A napkin sketch answers only what it was
  drawn to answer. On 2026-07-21 a super-rough layout sketch was read as evidence
  the jungle didn't fit and portrait forces bare lanes — the user hadn't decided
  either. Retracted. Same failure family as the confounded prototype (13): a
  rough thing can't answer a question it wasn't built for.
- **After every map rebuild, diff the deletions** (`git diff --cached`), don't
  trust the insertion count. Two separate rebuilds this session silently dropped
  live content (the central-risk note; 15's verbatim quotes) that only the
  deletion diff caught.
- **Don't rebuild DOM inside the animation loop.** v1 rebuilt the hand every
  frame, restarting CSS animations 60×/sec — cards flickered, taps missed, and
  the prototype was unusable. Board rendering belongs on canvas.
- **A syntax check is not a test.** Both prototype bugs were runtime-only. Say
  "unverified" when no browser is available.
- **Prototypes need a guided first run and a passive-by-default AI.** Without
  them, any reaction about feel is confounded — v2 read as "very unintuitive"
  purely because there was no tutorial and the AI crushed the player instantly.
  That was wrongly recorded as evidence against the card mechanic and had to be
  retracted. Label crude placeholders as crude on screen.
</pre>
