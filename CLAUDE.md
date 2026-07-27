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
