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

**Corrected twice on 2026-08-13** against two play-tests. Same artifact, same
commitment card, same direction — corrections, never a redesign, and no second
version. His verdict on the original build was *"honestly, for a verve, that's
pretty decent"* and *"this is better than I thought."* His verdict after the
first round of corrections was *"this is an improvement to your points for the
lane and the boards."*

### Round 2 — what changed, and what to look at first

- **The layout is rotationally symmetric and mirror-symmetric nowhere**, which
  is the answer to *"their maps don't look so NASCAR track with a line in the
  middle."* One half is authored and the other is that half turned 180°, so
  fairness is exact by construction (measured: max vertex error **0.0000**).
  The **bases came off the centre line** and **mid runs diagonally**, swinging
  248 units across the middle — there is no longer an axis for a mirror to run
  down.
- **The jungle is a route network**, not two corridors: 42 bent paths, **two
  closed loops** in the west region, a **chokepoint neck** in the east, 16
  clearings at the junctions, 28 thickets set at angles. Measured: nothing is
  sealed, and **all 28 thickets can be passed on either side**.
- **The camera came in 2.4×** — the board holds 33% of the map's width, a
  MOBA's far zoom with a little extra for a phone. The hero is 30 px, a creep
  10 px. **Everything therefore acquired a surface**: aggregate on the roads,
  three crowns and live tips to a cell in the canopy, scrub and litter in the
  clearings. Panning carries momentum and the minimap is a tap target.
- **The home field is a boundary, not a volume** — a survey threshold marked
  across each lane at the field's radius, walking back down the lane as the
  field retracts. **New mechanic: the buff lingers after a minion leaves the
  field** (`FIELD_LINGER`, 6 s, provisional and on the tuner) so the line
  cannot be camped.
- **Tap intent confirmed, and its hard problem answered.** One tap
  attack-move, two taps travel, as he proposed. A **run latch** carries the
  travel intent through a fast spam wherever the taps land, and an aimed tap
  breaks out of it in the same frame. **No latency is added anywhere.** What
  it costs is documented in the findings rather than buried.

**Two card lines were amended**, deliberately and on the record: **F3**
(mirror symmetry is what is banned; rotational symmetry is required for
fairness) and **Budget** (the card's ≤6 ms expectation is exceeded; measured
at +1.2 to +1.5 ms against the shipped build). See
[`COMMITMENT-overgrowth.md` § Amendments](COMMITMENT-overgrowth.md#amendments).

**One real bug was found underneath the texture work:** `h2`, the hash the
whole board's texture runs on, **never returned a value above 0.5** — an
overflow past 2^53. Half the growth palette, the bright tip colour and half of
every jitter had been unreachable since the file was written. Fixing it took
the finish gate from 9 dead blocks to 2 on its own.

### Round 1 — what changed then

- **The board is re-routed to the recorded layout.** Side lanes run out to the
  left and right edges and down them, mid runs through the centre, nothing
  traversable outside them. The lanes no longer read as a chicken foot and they
  no longer eat the middle: **the jungle went to 61% of the board** (67% after
  round 2's rebuild) and lane width is **derived from the creep** rather than
  picked.
- **The jungle is semi-open**, per his amendment — paths and clearings by
  default, camps in pockets off them.
- **The leash has no rendering.** Its boundary is the lane's front line, which
  is now a dark band cut across a bright road. The home field keeps the
  territorial channel to itself.
- **The leash is a limit, not a barrier.** Tapping past the front line is always
  accepted; the hero goes as far as it may and settles. It never grinds and it
  takes **zero** damage doing it.
- **The command bar is bigger (32%, floored at 226px) and far less numeric** —
  from ~37 visible figures down to 3.
- **One tap is attack-move, two taps is travel.** His proposal, no new control.
  Which way round was the build's choice, and it asked whether being locked
  into the wrong intent still felt bad. **Round 2 answered it:** he reached the
  same assignment himself, with a better reason — *"if a player chooses to spam
  to run away, it's always run away versus choosing to attack is deliberate"* —
  so the question is closed and the assignment is now his.

**Lever 1 / F2 of the commitment card was amended in that round**, because
deleting the second territorial system is what he asked for and the card's
original wording ruled it out.

Design decisions and the reasoning behind them:

- [`COMMITMENT-overgrowth.md`](COMMITMENT-overgrowth.md) — the commitment card,
  written before anything was made.
- [`CENTRE-SCREEN.md`](CENTRE-SCREEN.md) — the delegated centre-screen choice
  and its reason, as his instruction requires.
- [`FINDINGS-overgrowth.md`](FINDINGS-overgrowth.md) — what the finish gate
  caught, measured at two phone sizes, and the A-versus-B comparison.

**React to:**

- **The layout.** Turn the phone upside down — it is the same map. Now look at
  it the right way up: mid crosses on a diagonal, the bases sit either side of
  centre, and the two jungle regions are different shapes. Is the NASCAR read
  gone, and does it still feel even-handed?
- **The camera.** Can you see the hero, the creeps, the spells and the ground
  now? Is it too close — you see 7% of the map and the rest is a drag away —
  or is that the right trade? Drag hard and let go; tap the minimap to jump.
- **The jungle to move through.** Take a route rather than a straight line.
  There are two ways round the west region and one neck through the east. Is
  going through it a better experience than it was, or still a chore? And the
  question from last round is still open: is that the semi-open forest you
  described, or is it now too open — or too closed?
- **The board.** Does it read as lanes and jungle, and is there enough jungle
  that farming is a real alternative to pushing rather than the obvious second
  choice?
- **The home field's line in the sand.** A bright threshold across each lane,
  moving toward the base as the match runs. And the new lingering buff — sit
  just outside their line and try to farm their wave as it comes out. Does 6 s
  of breathing room feel like the right amount, or is it too generous?
- **The leash.** Tap deep into their half, past your front line. Your hero goes
  as far as it may and stops. Does the front line tell you where that is, or do
  you still not know where your reach ends?
- **Spamming to flee, then attacking on a dime.** Double-tap to travel, then
  keep tapping ahead of yourself — a box round the mark means the next tap is
  still flight. Tap a camp or a thicket and it attacks immediately. Then try
  attack-moving at open ground straight out of a run: **that one makes you
  pause for half a second, and that is the whole cost of the scheme.** Does it
  ever bite?
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
  the round-2 corrections: 130 s of no input leaves the lanes at
  0.48 / 0.49 / 0.47 and your hero at full health, untouched.
- **`FIELD_LINGER` (6 s) is a made-up number** like every other one here, and
  it is on the tuning panel precisely so it can be argued with. The mechanic is
  his; the duration is not.
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
