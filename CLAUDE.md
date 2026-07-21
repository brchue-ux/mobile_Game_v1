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
  and 13 (prototype). Provisional as of 2026-07-21: hero death is the loss
  condition, the hero works the jungle automatically, ~100 cards / 20-card decks.

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
