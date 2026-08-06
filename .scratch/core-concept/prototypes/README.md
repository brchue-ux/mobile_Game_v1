# Prototypes

Throwaway HTML feel prototypes for the concept in `.scratch/core-concept/`.
Fidelity is not the goal — reaction is. Serve from this directory:

```
python3 -m http.server 8931
```

`index.html` symlinks the current version; open it from a phone over LAN or
Tailscale (touch-only, does not read on desktop).

## Current: `05-reinforcement-exhaustion.html`

Built for ticket [05](../issues/05-match-shape-win-condition.md) — match shape
under the `[provisional]` win condition, reinforcement exhaustion. It answers
nothing; it makes the shape reactable.

**React to:**
- Does watching the reinforcement pool drain feel like the thing that matters,
  or do you stop watching it?
- When a pool hits zero and only the hero is left — does that read as a loss,
  or as a new phase? Neither is the "right" answer; that's the open question.
- Flip between the four forward-structure variants (Tuning panel) mid-match.
  Does any of them change how you play the lane, or just add a number? Two of
  your own candidates (guards, vicinity buffs) and a plain turret are not
  built at all — they're already rejected on your own test.
- Is the default match length (3:00, range 1:30–15:00) closer to right?

**Deliberately crude, labelled on screen:**
- Placeholder shapes for creeps, heroes, and forward structures — dots and
  rectangles, no art.
- Bases are drawn dim and inert; what they're for isn't decided here.
- The AI is near-passive by default (raise "Enemy difficulty" to push back).
- Numbers (pool size, wave interval, cooldowns, damage) are rough scaffolding
  to make the shape playable, not tuned values.

## Kept for the record

- `13-sixty-seconds.html` / `.v1-tugofwar.html.bak` — the prior prototype
  (ticket 13). Mostly failed as a feel test; kept, including the rejected
  tug-of-war v1, as the record of what was wrong. See ticket 13's `## Answer`.
