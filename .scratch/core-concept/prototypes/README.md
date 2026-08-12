# Prototypes

Throwaway HTML feel prototypes for the concept in `.scratch/core-concept/`.
Fidelity is not the goal — reaction is. Serve from this directory:

```
python3 -m http.server 8931
```

`index.html` symlinks the current version; open it from a phone over LAN or
Tailscale (touch-only, does not read on desktop).

## Current: `whole-a-reclaim.html`

The **whole-as-envisioned** prototype, built to the heading *"prototype is less
about how it ends right now and how the whole was envisioned."* Unlike the two
before it, this is not a single-mechanic feel test — it runs the spine together:
three lanes, bases top and bottom, jungle between all of it, creeps as units,
the front line as the hero's leash, the retracting home field, the
push-versus-farm economy, tap-to-move, telegraphed events, and the command bar.

Design decisions and the reasoning behind them:

- [`COMMITMENT-overgrowth.md`](COMMITMENT-overgrowth.md) — the commitment card,
  written before anything was made.
- [`CENTRE-SCREEN.md`](CENTRE-SCREEN.md) — the delegated centre-screen choice
  and its reason, as his instruction requires.
- [`FINDINGS-overgrowth.md`](FINDINGS-overgrowth.md) — what the finish gate
  caught, measured at two phone sizes, and the A-versus-B comparison.

**React to:**

- **The leash.** Tap ahead of your hero into the growth. Your reach ends where
  your lane's front line does — push and the road opens, concede and it closes
  over. Does that read as a decision, or as a fence?
- **Move versus attack-move through one tap.** The two intents are separated
  **in space, by what you tap**, not by a mode: pale ground you hold = travel
  and ignore everything; the growth at the front = press to the edge and hold
  it; a camp, a tree or a unit = go and fight that; your own hero = stop. Does
  being locked into the wrong intent still feel bad?
- **Push or farm.** Lanes pay gold on any hero kill of a minion, no
  last-hitting. The jungle pays less gold plus items, and every camp shows its
  difficulty, time, damage, mana, gold and item chance **before** you commit.
  Does the choice feel live, or is one arm obviously right?
- **The home field.** Its cultivated core, its reach, and its edge all retract
  over the match. Can you tell **why** a push stalled? (The phase strip under
  the race track draws the schedule.)
- **Travel distance** — the number carrying the most weight. Tuning panel,
  "Map length"; changing it restarts the match.

**Deliberately crude, and labelled on screen:**

- Placeholder shapes everywhere — no art.
- **The card system is a placeholder**, per its binding spec: five cards, one
  line each, one per target class, a three-card hand labelled arbitrary, and
  combining with a visible, obviously arbitrary +20 s accrual cost. No imbue
  loop, no freeze slot, no deck building.
- **Nothing ends the match.** The clock runs to 15:00 and says so. The power
  threshold is parked by the captain's own instruction; its absence is
  deliberate, and the race track has no finish line for the same reason.
- **Event lane placement is randomised and says so** — the principle is
  "influence, not selection" but the mechanism is commissioned and unchosen.
- The opponent is **passive by default** (Tuning → Opponent). Verified: 130 s of
  no input leaves the lanes at 0.49 / 0.44 / 0.47 and your hero untouched.
- Mana is shown only because the camp readout specifies a mana cost; whether
  mana exists at all is open.
- Provisional numbers are measurement apparatus, not balance decisions. The
  fixed anchors from the record — 15-minute match, 5-minute event cadence — are
  not tunable.

## Also kept: `whole-b-encroach.html`

The second version, kept as a separate artifact rather than overwriting the
first. Structurally: the wild stops being a rendering of the contest and becomes
an **agent** — it grows on its own clock, spreads from its own thickest edge,
and is cut back only by units that walk through it, so the leash is not stated
anywhere. Better image, and it costs the two things the heading needs: the
territory read and the leash itself. Reasoning and numbers in
[`FINDINGS-overgrowth.md`](FINDINGS-overgrowth.md).

## Kept for the record

- `05-reinforcement-exhaustion.html` — ticket
  [05](../issues/05-match-shape-win-condition.md)'s match-shape prototype, built
  under the since-superseded reading that reinforcement exhaustion was the win
  condition. Its forward-structure variants are moot (the structure was cut
  2026-08-11); kept as the record.

  <details><summary>Its original README entry, preserved verbatim rather than
  deleted — the user never reacted to it, so the questions are still unanswered
  even though two of them have since been overtaken.</summary>

  > Built for ticket [05](../issues/05-match-shape-win-condition.md) — match shape
  > under the `[provisional]` win condition, reinforcement exhaustion. It answers
  > nothing; it makes the shape reactable.
  >
  > **React to:**
  > - Does watching the reinforcement pool drain feel like the thing that matters,
  >   or do you stop watching it?
  > - When a pool hits zero and only the hero is left — does that read as a loss,
  >   or as a new phase? Neither is the "right" answer; that's the open question.
  > - Flip between the four forward-structure variants (Tuning panel) mid-match.
  >   Does any of them change how you play the lane, or just add a number? Two of
  >   your own candidates (guards, vicinity buffs) and a plain turret are not
  >   built at all — they're already rejected on your own test.
  > - Is the default match length (3:00, range 1:30–15:00) closer to right?
  >
  > **Deliberately crude, labelled on screen:**
  > - Placeholder shapes for creeps, heroes, and forward structures — dots and
  >   rectangles, no art.
  > - Bases are drawn dim and inert; what they're for isn't decided here.
  > - The AI is near-passive by default (raise "Enemy difficulty" to push back).
  > - Numbers (pool size, wave interval, cooldowns, damage) are rough scaffolding
  >   to make the shape playable, not tuned values.

  </details>
- `13-sixty-seconds.html` / `.v1-tugofwar.html.bak` — the prior prototype
  (ticket 13). Mostly failed as a feel test; kept, including the rejected
  tug-of-war v1, as the record of what was wrong. See ticket 13's `## Answer`.
