# Finish gate — findings

Run against the artifacts, in a real browser at a real phone viewport, not
against intentions. Two versions, two sizes each. Card:
[`COMMITMENT-overgrowth.md`](COMMITMENT-overgrowth.md).

**Measurement conditions, recorded because a number without them is a rumour:**
headless Chrome on Linux via `chrome-devtools-axi`, 12 hardware threads, no
competing load, **no CPU throttling**, page served from a local
`python3 -m http.server`. `devicePixelRatio` 1 unless stated. Frame cost is
`performance.now()` around update + terrain + draw, averaged over 30 frames —
so it is the work attributable to the artifact, not wall-clock.

**Sizes.** Composed at **390 × 844** (the phone in hand). Also run at
**320 × 568** — the hostile condition named on the card: *the first twenty
seconds, one-handed, on a small phone in daylight, by someone who has never
seen it.*

---

## Version A — `whole-a-reclaim.html`

### Frame

| size | dead blocks (of 84) | fraction | where | verdict |
|---|---|---|---|---|
| 390 × 844 | 1 | 1.2% | r9,c4 | pass |
| 320 × 568 | 1 | 1.2% | r2,c0 | pass |

Measured, not eyeballed: the board canvas is sampled on a 7 × 12 grid and each
block's luminance standard deviation computed; a block counts as dead below
sd 6. Largest contiguous dead region is a single block — **1.2% against a
threshold of one seventh (14.3%)**.

**Adjudicating the dead blocks.** Both are cleared ground inside the home
field's cultivated core. **The card pays for it** (`Materials`: the apron is the
cultivated ground the base keeps clear) **and the thing paying is built** — the
apron has its own ruling density, its own edge, and it visibly retracts across
the match. Recorded as resolved, not relitigated.

An earlier reading, before the fixes below, had **three** dead blocks and a
frame that was one uniform pale field — see "What the gate caught and I fixed".

### Population

Every container holds real content at rest, before anyone touches anything:

- **Card panel** — three slots, and empty slots are drawn as empty slots
  (dotted, labelled "empty slot"), not as nothing.
- **Race track** — both markers and the hatched gap are present at 0:00,
  because the axis frames the pair rather than running from an invented zero.
- **Phase strip** — the retraction wedge and both event marks are drawn for the
  whole match from the first frame.
- **Jungle panel** — six camps with their full six-figure readout at 0:00.
- **Board** — camps hold their units at rest; nothing is a placeholder box.

### Density

Quadrant mean sd at 390 × 844: **41.7 / 48.9 / 43.2 / 46.8**. Even, and every
quadrant is far above the dead threshold. Nothing is uniform emptiness.

### Bill

Budget line: milliseconds per frame, ceiling 16.7, target ≤ 8.

| reading | total | sim | terrain | draw |
|---|---|---|---|---|
| 390 × 844, DPR 1 | **5.46 ms** | 0.16 | 2.77 | 2.53 |
| 320 × 568, DPR 1 | **7.31 ms** | 0.21 | 3.55 | 3.55 |
| 390 × 844, DPR 2 (780 × 1232 backing store) | **4.75 ms** | — | — | — |

**Under target at every reading.** The commitment predicted this would only be
affordable because the per-pixel reading of the direction was replaced at
commitment time by a coarse grid with cached lane projections; that prediction
held — `sim` is 0.16 ms because every cell's projection onto every lane is
precomputed once rather than each frame.

**The honest caveat, which the conditions above make visible:** this is a
12-thread desktop with no throttling. A mid-range phone's single-thread JS is
commonly 3–5× slower, which would put version A at roughly **16–27 ms** — at or
over the ceiling. The levers if that happens are on record and cheap:
`REBUILD_SLICES` (currently 6) spreads terrain work over more frames, and `CELL`
(currently 16) trades growth detail for cost quadratically. **Not measured on a
phone — say unverified, not "fine".**

### Card audit, against the artifact

Run, not remembered. Runnable checks first.

| refusal | check | result |
|---|---|---|
| F1 no fence/ring/dash/arrow marks the leash | `grep -c setLineDash` ; `grep -c 'leashRing\|drawFence\|ctx.arc('` | 0, 0 — **pass** |
| F2 no static painted terrain | `grep -c 'jungleRegion\|JUNGLE_POLY\|terrainPath'` | 0 — **pass** |
| F3 nothing symmetrical in the growth | grep found 3 hits, **all the word "unmirrored" in comments** — so the grep was insufficient and was replaced by a numeric probe: mean absolute difference of the growth noise across a top-bottom mirror, 780 samples | **0.091 mean, 0.329 max — not mirrored, pass** |
| F4 no glow, drop shadow or blur | `grep -cE 'shadowBlur\|box-shadow\|filter:.*blur\|createRadialGradient'` | 0 — **pass** (the hero's shadow is a drawn ellipse) |
| F5 no health bar over any unit | no bar geometry in the unit draw path | 0 — **pass** |
| F6 nothing in the command bar is irregular | `border-radius` above 0 anywhere | 0 — **pass** |

**F3's grep was a bad check and the audit is what exposed it.** A word-match on
"mirror" hits the very comments that claim the refusal is honoured — the check
would have passed forever while telling me nothing. Replaced with a probe that
returns a number.

Materials, Rhythm, Signature checked by eye against the render:

- **Materials** — bone/slate/growth present as specified. **One deliberate
  amendment, made during the pass and recorded rather than smuggled:** their
  ground was specified as *cool bone* at the same value as yours. At phone scale
  warm-vs-cool at equal value was not readable, so their ground was darkened to
  slate (L\* ~55 against bone's ~82). The blue–yellow separation and the
  ruling-direction cue both survive; **value was added, nothing was removed.**
  This is a card amendment, not drift.
- **Rhythm** — scar decay 18 s, wave 11 s, camp respawn 50 s, retraction 46%→8%
  of half-length across 15:00, telegraph 60 s: all as written.
- **Signature** — *the road opening* happens and is caused by the direction:
  pressing the mid lane moved `front[1]` from 0.50 to 0.59, the growth pulled
  back off the road, and ground that had been illegal became walkable. Verified
  in play, not asserted.
- **Banned defaults** — none present. No range-slider drawer, no modal tutorial
  overlay, no cyan-on-slate, no green polygons, no unit rings, no HUD of meters.

### Critique

- **Name test.** From the artifact alone the direction is nameable: something
  ordered is being eaten. **Pass.**
- **Coarse test.** Blurred to values only, the frame is three bands — bright
  bone, dark growth, mid slate — with three pale roads running through them and
  terminating at different heights. There is a focal path and it is the seam.
  **Pass.**
- **Delete test.** The most decorative element is the growth "tip" marks (the
  fine 1.2 px second grain scale). Removing them leaves the coarse blobs reading
  as dots rather than as vegetation — they carry the second scale that stops the
  texture reading as an overlay. **Kept, and it earns its place.**
- **Payoff test.** The unit of payoff was *the moment your world grows or
  closes*. It happens, and the direction causes it: the growth is what closes.
  **Pass.**
- **Mean audit.** None of the three named defaults is present.
- **Edge test.** Held at 320 × 568 after the fixes below. Three-value contrast
  survives; the camp readout keeps all six figures; the card slots keep one line
  each.

### What the gate caught, and I fixed in this version rather than deferring

1. **The home field swallowed the board.** A 780-unit disc at full strength
   made the entire home half one uniform pale field with no growth in it —
   Overgrowth with no growth in the opening frame. Fixed by splitting the field
   into three readable layers of one mechanism: a small cultivated **core** that
   cuts the wild, a **reach** that shows as denser ruling and a wash, and an
   **edge** drawn where it ends. Empowerment still runs to the full radius,
   which is what his description actually specifies.
2. **Order-vs-wild was the same axis as mine-vs-theirs, so the jungle stopped
   being jungle.** Fixed by separating **vegetation** (a property of the ground,
   precomputed from lane distance) from **claim** (whose ground it is). The
   jungle now stays jungle on ground you hold, and the growth still closes over
   the road at the seam.
3. **The reinforcement pool exhausted in 62 seconds** of a 15-minute match.
   Provisional pool raised 40 → 520, so running dry is reachable around 10:30
   rather than automatic at 1:00.
4. **The opening frame did not contain the seam.** Fixed by composing the frame
   deliberately — hero at the bottom edge, its ground below, growth band above,
   a band of their ground at the top — and by starting the hero out of its base.
5. **Warm-vs-cool at equal value was unreadable at phone scale.** See the
   Materials amendment above.
6. **Failures at 320 × 568 that were failures, not caveats:** the camp readout
   lost its item column, the card text clipped, the strip labels clipped, the
   right panel's crude-labelling note was cut off. All fixed — bar sizing,
   column format, a 3-slot hand instead of a 5-card library, shorter labels.
7. **The guided first run could wedge.** It gated strictly on each step's
   trigger, so a player who did something else sat on step 1 indefinitely —
   observed at 82 seconds. Every step now also advances on a timeout. This
   matters more than it looks: a confounded guided run is exactly the failure
   this project already had to retract once.

---

## Version B — `whole-b-encroach.html`

**What it changes structurally, in one sentence:** in A the wild is a *rendering*
of the contest — growth is computed from the claim field, so the leash is a rule
the game states; in B the wild is an *agent* with its own clock that grows toward
its own potential, advances from its own thickest edge, and is cut back only by
units that actually walk through it — so the leash is not stated anywhere, it is
whatever the creeps happen to have trampled open.

That is a change to the generator and to the legality rule, not a change of
intervals or colours. `legal()` in B does not read `claim` at all.

### Gate

| size | dead blocks | frame cost |
|---|---|---|
| 390 × 844 | **0 of 84** | **11.21 ms** (sim 0.34 / terrain 4.85 / draw 6.02) |
| 320 × 568 | **0 of 84** | **10.77 ms** |

Quadrant mean sd at 390 × 844: 37 / 25 / 48.3 / 40.2 — the top-right quadrant is
thinner than the rest but not dead. Population and the card audit carry over
unchanged; the same runnable checks pass.

### What B does better

- The wild reads as **alive**. Three trodden channels through a continuous
  forest, kept open only by what walks them, is a stronger image than A and a
  truer reading of *"an irregular agent with its own logic invading it."*
- **Evidence of time** is at full strength: your hero cuts a visible path
  through the jungle and that path closes behind it.
- The home field's retraction is felt as **the wild advancing on your base**,
  which is the schedule of legitimacy expressed as something happening to you.

### What B costs, and it is decisive

- **It loses the territory read.** Whose ground is whose is buried under growth
  almost everywhere. Map control's worth is *economic denial* — you have to be
  able to see the ground you have taken from them — and in B you largely cannot.
- **It weakens the leash, which is the thing the prototype exists to convey.**
  Because the hero tramples its own path, it walked to y = 744, deep in the
  enemy half, with `front[1]` at 0.69. In A the same order held it at the seam.
  B's hero is bounded by *thickness*, not by the front line, and the design's
  rule is explicitly *"the hero's legal roam in a lane extends as far forward as
  that lane's front line."* B does not enforce that rule; it approximates it.
- **It costs roughly double.** 11.21 ms against A's 5.46 ms at the same size —
  over my 8 ms target, still under the 16.7 ceiling, and the phone extrapolation
  above puts it clearly over.

---

## The choice

**Ship A** (`whole-a-reclaim.html`), and keep B.

B is arguably the better *image* and it is the more committed reading of the
direction. It is not the better answer to this compass. The heading names a
thing — *convey the whole as envisioned* — and the whole includes a leash that
behaves the way the design says it behaves and territory you can read at a
glance. B's structural change bought atmosphere and spent both.

That is also the outcome the method predicted: **where the compass names a
thing rather than a quality, expect the structural change to cost you that
thing.** It did. The prediction is recorded here as having held, not as having
been assumed — B was built, played, and gated before it was judged.

**What B found that A should keep, and does not yet have:** the hero leaving a
visible trodden path behind it. That is pure evidence-of-time, it costs almost
nothing, and it does not touch the leash rule. Not added here — it is a change
to a gated artifact and belongs to the next pass, not to this one's write-up.
