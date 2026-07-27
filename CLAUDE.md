# Mobile Game (placeholder name)

Real-time mobile lane-battler with compound spellcasting. Concept design is
underway; **no code yet**.

## Status

**Concept design in progress.** The canonical artifact is the wayfinder map at
[.scratch/core-concept/map.md](.scratch/core-concept/map.md), with its 18 tickets
in `.scratch/core-concept/issues/`. **Read the map before doing anything here.**

Session narrative lives in [CHANGELOG.md](CHANGELOG.md) — grep it for a past
decision or why something was tried. It is not auto-loaded.

Engine, stack, platform and name are deliberately out of scope until the concept
settles.

## Working method — read `## Working method` in the map first

One ticket per session. The user word-dumps everything they think about it; that
dump is used to **rebuild the map**, not just to close the ticket. Confirm
understanding, then wait for the user to say proceed.

Sequential grilling was tried and dropped — this design is a graph, not a tree,
and question-at-a-time forced forks faster than they could be answered.

**One commit per rebuild.** Every prior map version stays diffable. This is
load-bearing, not hygiene.

`/wayfinder` is referenced in older notes but is **not installed**. `/grilling`
and `/prototype` are.

## Rules that govern every rebuild

- **Rejections are append-only.** Every rebuild carries forward every recorded
  "no" with its reason. A reversal is flagged *as* a reversal, in the user's
  words — never silently dropped. A rebuild is precisely what lost the
  tug-of-war rejection once already.
- **After every rebuild, diff the deletions** (`git diff --cached`), never trust
  the insertion count. This has caught silently dropped live content on five
  separate rebuilds across two sessions.
- **Build from the user's words, not from a summary.** A summary is lossy exactly
  where a correction lives.
- **Locked constraints live in the map's `## Notes`.** Don't re-litigate without
  saying so explicitly.
- **Ticket 18's "budget" governs what ships in a build, never what gets
  explored.** It may not be invoked to discourage an idea. Define the term or
  don't use it.

## Ticket state

- **Resolved:** 02 (combining = payload + modifiers, amended for small recipe
  sets), 13 (prototype).
- **Closed by removal:** 03 (gesture) — the subject was cut, not answered.
- **Shelved:** 09 (banking) — good shape, no payoff worth its cost. Not rejected;
  don't reintroduce unprompted. **⚠ See the open question below.**
- **Substantially answered:** 01, 05, 10, 15.

## Where the design stands

All `[provisional]` unless marked.

- **Core loop:** accrue cards → combine into a compound spell → **select a
  target**. Casting is **selection, not performance** `[committed]`. Four target
  classes: help your hero, help your lane, hurt their lane, slow their hero.
- **Camera:** a pannable MOBA observer over a slightly angled overhead
  battlefield. The map exceeds the screen; you drag around it. The player is a
  **commander, not an avatar**.
- **Screen:** portrait 1080×2400. Warcraft 3 zoomed out — top ~75% map viewport,
  bottom ~25% command bar holding the cards, readouts on **both** heroes, and the
  hero's standing orders.
- **Information:** **no fog of war** (forced by casting-as-selection — you can't
  select what you can't see). The **hand is hidden**, and probably the opponent's
  field-manipulation capability. You always see what is happening, never quite
  what is coming.
- **Hero:** works the jungle automatically on route/behaviour modes; the player
  sets **standing orders** (lane, jungle camp) but never steers directly. Cards
  influence power, orders influence priorities. Differentiation is **asymmetry,
  not power level**. Death costs nothing; 1–2 priced buybacks per match.
- **Match:** base destruction ends it — **⚠ held under protest**, see below.
  Concession/disconnect is a win by default. PvE and PvP share one shape.
- **Jungle:** playable space for spells, **not a wall** (the hero must traverse
  it — this is now a pricing baseline, since blocking traversal is only worth a
  card because passage is the default). Lane creeps leash back on lost aggro.
- **Terrain manipulation** is the leading objective candidate — water, lava,
  holes impeding enemy traversal.
- **Cards:** ~100, bring ~20. All obtainable by every player, none
  purchase-exclusive. **All hero power variance is match-bound** `[committed]` —
  no persistent power, no purchased power, no gacha.
- **Cards must be judgeable against visible battle state.** The bottom bar is the
  **decision substrate**, not a HUD.
- **No comeback mechanic may reward deliberate losing** `[committed]`.
  **Preventive beats restorative**: a device that stops a snowball starting gives
  a thrower nothing; one that pays out in proportion to how badly you're doing is
  what a thrower farms.

## Open questions that need the user

- **⚠ Is the accrual cost-gate the same system as banking (09)?** *"I did mean
  accrue"* is confirmed, but its stated job is gating the cost of powerful
  effects, not 09's tempo-vs-investment, and it was held as a hypothetical.
  Either 09 returns, or there are two accrual systems and 18 must know it. **A
  shelved ticket whose mechanic is in use under another name should not
  persist.**
- **⚠ What replaces "destroy their base."** Wanted gone as *"so prototypical."*
  Nothing has replaced it. Towers exist but are unspecified, and the turret is
  rejected as MOBA copying — the brief is a **lane breakpoint with a power curve
  that doesn't read as a building**.
- **Where execution skill lives, or whether the design accepts having none.**
  Skill is now entirely cognitive. Is that the identity or a hole? Don't fill it
  reflexively — re-adding dexterity under another name would undo the removal.
- **Target resolution within a class** — whole lane, or a point inside it?
- **Whether any gesture survives anywhere.** Tap-only is live and unchosen.

## Prototype

`.scratch/core-concept/prototypes/` holds a playable feel prototype. Serve it:

```
cd .scratch/core-concept/prototypes && python3 -m http.server 8931
```

`index.html` symlinks the current version, so edits show on reload. Open it from
a phone over LAN or Tailscale — it is a touch game and does not read on desktop.

## Hard-won gotchas

- **Creeps are units, not a meter.** A tug-of-war / fill-bar abstraction has been
  rejected **twice**. The v1 prototype shipped one anyway; `*.v1-tugofwar.html.bak`
  is kept as the record. **The word "tug of war" is not the ban** — the user uses
  it for the strategic contest. The *abstraction* is what's rejected.
- **Don't over-read rough artifacts.** A napkin sketch answers only what it was
  drawn to answer. A super-rough layout sketch was once read as evidence the
  jungle didn't fit; the user had decided no such thing. Retracted.
- **Don't over-extend a cascade.** When a decision is removed, scope its
  consequences to what it actually touched. Removing *player card* skill shots
  did **not** shrink terrain's job — terrain is paid for by hero and creep
  movement, pathing and sightlines. Corrected by the user.
- **Watch for reference-vs-proposal in quotes.** The user describes other games
  to explain a shape. *"Your selectable army"* was Warcraft 3's UI, not a request
  for commandable units.
- **Don't rebuild DOM inside the animation loop.** v1 rebuilt the hand every
  frame, restarting CSS animations 60×/sec — cards flickered, taps missed, and
  the prototype was unusable. Board rendering belongs on canvas.
- **A syntax check is not a test.** Both prototype bugs were runtime-only. Say
  "unverified" when no browser is available.
- **Prototypes need a guided first run and a passive-by-default AI.** Without
  them, any reaction about feel is confounded — v2 read as "very unintuitive"
  purely because there was no tutorial and the AI crushed the player instantly.
  That was wrongly recorded as design evidence and had to be retracted. Label
  crude placeholders as crude on screen.
