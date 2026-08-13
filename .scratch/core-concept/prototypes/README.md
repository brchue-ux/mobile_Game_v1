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

**Corrected 2026-08-13 against his play-test.** Same artifact, same commitment
card, same direction — six corrections, not a redesign. His verdict on the thing
being corrected was *"honestly, for a verve, that's pretty decent"* and *"this
is better than I thought."* **What changed, and what to look at first:**

- **The board is re-routed to the recorded layout.** Side lanes run out to the
  left and right edges and down them, mid runs down the centre, nothing
  traversable outside them. The lanes no longer read as a chicken foot and they
  no longer eat the middle: **the jungle is now 61% of the board** and lane
  width is **derived from the creep** rather than picked.
- **The jungle is semi-open**, per his amendment — paths and clearings by
  default, camps in pockets off them. Measured: the whole map is one connected
  region, nothing is sealed, and no tree has to be cut to reach anything.
- **The leash has no rendering.** Its boundary is the lane's front line, which
  is now a dark band cut across a bright road. The home field keeps the
  territorial channel to itself and is cross-hatched so it cannot be confused
  with a lane.
- **The leash is a limit, not a barrier.** Tapping past the front line is always
  accepted; the hero goes as far as it may and settles. It never grinds and it
  takes **zero** damage doing it.
- **The command bar is bigger (32%, floored at 226px) and far less numeric** —
  from ~37 visible figures down to 3.
- **One tap is attack-move, two taps is travel.** His proposal, no new control.
  The choice of which way round was the build's to make and the reason is
  recorded on the file and in the findings.

**One line of the commitment card was amended**, deliberately and on the record:
Lever 1 / F2, because deleting the second territorial system is what he asked
for and the card's original wording ruled it out. See
[`COMMITMENT-overgrowth.md` § Amendments](COMMITMENT-overgrowth.md#amendments).

Design decisions and the reasoning behind them:

- [`COMMITMENT-overgrowth.md`](COMMITMENT-overgrowth.md) — the commitment card,
  written before anything was made.
- [`CENTRE-SCREEN.md`](CENTRE-SCREEN.md) — the delegated centre-screen choice
  and its reason, as his instruction requires.
- [`FINDINGS-overgrowth.md`](FINDINGS-overgrowth.md) — what the finish gate
  caught, measured at two phone sizes, and the A-versus-B comparison.

**React to:**

- **The board.** Does it read as lanes and jungle now, and is there enough
  jungle that farming is a real alternative to pushing rather than the obvious
  second choice?
- **The jungle's character.** Paths, clearings, pockets, thickets you route
  around. Is that the semi-open forest you described, or is it too open?
- **The leash.** Tap deep into their half, past your front line. Your hero goes
  as far as it may and stops. Does the front line tell you where that is, or do
  you still not know where your reach ends?
- **Move versus attack-move by tap count.** **One tap = attack-move** (go there
  and fight what you meet). **Two taps = travel** (go there, ignore everything).
  This build picked that way round; the other way is one line of code. Does
  being locked into the wrong intent still feel bad?
- **The command bar.** It is bigger, and almost nothing in it is a number any
  more — cost and worth are length, weight, count and fill. Can you still tell
  whether a camp is worth taking? Is anything now harder to read than it was?
- **Push or farm.** Lanes pay gold on any hero kill of a minion, no
  last-hitting. The jungle pays less gold plus items, and every camp still shows
  its difficulty, time, damage, mana, gold and item chance **before** you commit
  — the information is all there, it is just not carried by figures. Does the
  choice feel live, or is one arm obviously right?
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
- The opponent is **passive by default** (Tuning → Opponent). Re-verified after
  the corrections: 130 s of no input leaves the lanes at 0.47 / 0.50 / 0.45 and
  your hero at full health, untouched.
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
