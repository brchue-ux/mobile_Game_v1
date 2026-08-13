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

---

# Correction pass — 2026-08-13

**Appended, not replacing.** Everything above is the record of the original
`/verve` pass and its gate, and it stays as written. This section records the
pass that followed his play-test of `whole-a-reclaim.html` on an S26 Ultra.

**It is a correction pass, not a second `/verve` and not a `/hone`.** The
commitment card stands, the direction stands, the artifact keeps its identity
and its filename. One line of the card was amended and it is recorded as an
amendment — [`COMMITMENT-overgrowth.md` § Amendments, A2](COMMITMENT-overgrowth.md#amendments).

**His verdict on the thing being corrected:** *"honestly, for a verve, that's
pretty decent"*, and *"this is better than I thought."* Full reaction record:
`firstmate/data/mg-prototype-feedback-2026-08-12.md`.

**Measurement conditions, restated because a number without them is a rumour:**
headless Chrome on Linux via `chrome-devtools-axi`, no CPU throttling, page
served from `python3 -m http.server`, `devicePixelRatio` 1. Frame cost is
`performance.now()` around update + terrain + draw, averaged over 30 frames.
**Three sizes this time**, because the complaint that started it was about size:
**390 × 844** (composed), **320 × 568** (the card's hostile condition), and
**412 × 915** (an S26-Ultra-class viewport, which the last gate did not run).

---

## 1. Board geometry — the largest correction

**What was wrong.** *"The lanes are too wide... nowhere near enough jungle...
they look like a chicken foot."* Three lanes radiating from the base as spokes
consumed the middle, which is where the jungle should be. The old build did not
have a lane-width number at all: the width you saw was `LANE_REACH`, the
sideways spread of the claim field, at 190 units either side of three lanes —
1,140 units of tint across a 1,000-unit map. **The lanes ate the jungle**, and
narrowing them alone would not have produced one.

**Re-routed to the recorded layout.** Bases top and bottom; the side lanes leave
the base sideways, run **out to the left and right edges and down them**; mid
runs down the centre; nothing traversable outside the side lanes. The jungle is
then what is left **between** mid and each side lane — regions, not strips.

**Lane width is now derived, and the derivation is in the file.** The creep is
the atom: a body is 8.4 world units and a wave is three abreast at a 9-unit
offset, so a wave spans ~26 units. A lane must carry two of those in contact
with room for a hero (20 units) to pass, which is five creeps wide — a **54-unit
road** (`ROAD_W` 27). `TINT_R` (64) is where the surveyed shoulder ends, and it
is the only number that decides how wide a lane looks. **Widen a lane and the
jungle shrinks by exactly that much**, which is the property the old build did
not have.

Measured on the artifact, not asserted:

| | shipped build | corrected |
|---|---|---|
| board | 1000 × 2000 | **1150 × 2000** |
| surveyed (lane) ground | claim spread 190/side, 3 lanes | **28.0% of cells** |
| thick jungle (veg > 0.4) | a strip | **61.2% of cells** |
| lane lengths (left / mid / right) | near-identical spokes | **2236 / 1765 / 2268** |
| creep at the composed zoom | ~4 px | **3.9 px** — the atom survives |
| road on screen | — | **25 px** |
| front-line band on screen | — | **12 px** |

Creep speed is now **normalised by lane length** (`LANE_REF_LEN`). Without it
the side lanes, being the long way round, would have moved their creeps faster
over the ground and resolved first every match. Same for event minions.

**Left and right are not mirrors** — required by 12's direction (*"I would like
it to not be totally symmetrical"*). Measured: mean absolute difference of the
vegetation field across a left–right mirror is **0.154** over 1,215 samples, and
the two side lanes differ in length by 32 units.

## 2. The jungle's character — his amendment, built

*"The jungle is not an open forested area, neither is it a completely dense
forested area. It is a forested area with clear openings and paths to traverse
and little pockets where the creeps will hang out."*

Built as a **routed space, not sealed chambers**: seven jungle paths (three in
the left region, four in the right — deliberately not a mirror) thin the growth
along them, and each camp sits in a **pocket** whose clearing opens onto a path.
Trees still separate and are still destructible; two of them pinch a path
without closing it.

**Passage is the default state, and this is measured rather than eyeballed.**
Flood fill over terrain-passable ground (in bounds, not inside a live tree) from
the hero's start:

- **30,328 passable cells, 30,328 reached — 100%, one connected region.**
- **0 of 12 camps unreachable.** Both bases reachable. **Nothing is sealed**, and
  no tree has to be cut to get anywhere.

A second flood fill with the leash left switched on reached all six of **your**
camps and none of theirs, which is the leash doing its job rather than the
terrain doing it.

**The jungle floor is now two tones**, and that is what makes a path read as a
path: near-black under canopy, bare duff in an opening. Four value tiers carry
the board — canopy L\* 9, opening L\* 17, their bone L\* 55, your bone L\* 85.

## 3. Territorial rendering — the second system deleted

*"The way that you did the force field was no. I'm not even sure what it is...
I see like these lines. Is that the leash? I don't know."*

**The leash now gets no rendering at all.** Territory is drawn only inside the
lane's surveyed shoulder; the claim field still spans the board as the **rule**,
but outside the shoulder it is not drawn, so the broad wash that read as an
unexplained arc is gone. The home field keeps the territorial channel to itself
and is additionally **cross-hatched both ways** where a lane is ruled one way
only, so the two cannot be confused. He allowed the field itself: *"I think I
see the force field, that's also fine for a rough concept."*

**The front line had to be made to carry the leash on its own, and it does.**
Held ground now fades back toward bare ground as the claim on it goes to zero,
so the seam is a dark band cut across a bright road rather than a soft change of
tint. Measured down the mid road, as a 22-px-wide strip mean:

- their road **L\* 134** → **band, minimum L\* 22, 38 px / 81 world units deep**
  → your road **L\* 218**.

Three value tiers on one road. That band is the front line, and it is the only
thing the leash needs.

**This is the card amendment (A2).** It is recorded on the card with what forced
it, what did not change with it, and what it costs.

## 4. Leash behaviour — a limit, not a barrier

*"I think you should always be able to tap past the frontline to have your hero
run in that direction"*, and the hard requirement: *"there needs to be some sort
of mechanism where it doesn't just constantly attempt to run through an
invisible barrier taking damage."*

Built to his own sketch: an order aimed past the limit is **clipped to the
furthest legal point on the line, pulled back by a 24-unit standoff**, an
`engage` **defaults to a move** (it drops the thing it was pursuing), and on
arrival the order **ends**. A stall detector settles the hero after 0.4 s of
getting nowhere for any reason — the limit, a tree, a corner.

Measured, driving the real pointer listeners rather than the internal function:

| check | result |
|---|---|
| tap at their base, far past the line — input accepted? | **yes**, order set |
| hero settles after | **3.55 s** |
| order still set 30 s later | **no** — cleared |
| re-attempt ticks over the following 30 s | **0** |
| **HP lost while settled at the limit** | **0 of 320** |
| `engage` on an out-of-reach enemy camp | → **`press`**, camp dropped, clipped, settled |
| hero stranded by a line that fell back through it | **withdraws** y 300 → 1033, legal again |

**Never refused, never grinding, never a damage loop.** The last row is a case
the old build could not have survived: the front line receding past a standing
hero left it on ground it may not be on, unable to move at all.

## 5. The command bar — bigger, and far less numeric

**Bigger, sized from its contents rather than from a fraction.** Three 44-px
card targets, ≥ 96 px of vertical run for the power track's gap, ≥ 42 px for the
phase strip, six 18-px camp rows and a pinned key, under a ~30-px state strip.
That is ~226 px of content, so: **height 32%, floor 226 px, ceiling 312 px**
(was 27% / 168 / 240). The board takes the remainder and absorbs the
loss by panning; the bar cannot pan.

| viewport | bar | board | card targets |
|---|---|---|---|
| 390 × 844 | **270 px (32.0%)** | 574 px | 44 / 44 / 44 |
| 412 × 915 (S26-class) | **293 px (32.0%)** | 622 px | 44 / 44 / 44 |
| 320 × 568 (hostile) | **226 px (39.8%)** | 342 px | 44 / 44 / 44 |

**Far less numeric — the more important half.** *"There was way too much
information and it was all about numbers and moving numbers."* This was a
recorded constraint the build missed, not a new preference: the bottom bar is
**the decision substrate, not a HUD**.

Nothing was deleted. Every figure changed carrier:

| was | is now |
|---|---|
| `GOLD 412 · 3i` | hundreds as blocks + a part-hundred fill; items as pips |
| `REINF 520 / 520` | two depletion bars, yours over theirs |
| `320hp · 120mp` | condition bars for **both** heroes, health over mana |
| `next 12s` | an accrual track closing, with the combine cost **hatched onto its end as extra distance** |
| `YOU 47 · THEM 39 · +8` | the gap (already there) plus a **lead wedge** whose depth is the lead |
| telegraph `60s` | a bar running down |
| event `LANE 1 / LANE 3` | a three-cell lane diagram — position, not a number |
| camp row `34s 45/33 289g 47%` × 6 | difficulty as pips · **time as bar length** · damage as a slice of **your current health** · mana as a slice of **your current mana** · gold as a count of blocks · item chance as a fill across five pips |

The camp readout was the densest numeric object in the design by construction —
six camps × difficulty, time, damage, mana, gold and item chance — and it is
where the biggest gain is. Damage and mana are now expressed **against your own
state**, so a camp's worth is situational and felt rather than computed, which
is what *"judgeable against visible battle state"* asks for. **The cost figures
are the ones the sim actually charges**, not a label sitting beside a different
number.

**Measured: digits visible in the decision substrate** (the tuner is excluded —
it is the explicitly-labelled numbers drawer, and numbers belong in it).

- shipped build: **~37** — 3 strip readouts, an accrual countdown, 3 race
  figures, and 30 camp figures.
- corrected build: **3**, at every size, and all three are card durations from
  the placeholder card spec's one-line descriptions (*"stall 4s"*, *"faster
  10s"*, *"cut growth 15s"*).

The bar's DOM is now **built once and updated by width and class**, rather than
re-`innerHTML`-ed seven times a second. That is the project's own gotcha about
rebuilding DOM in the loop, applied before it bit.

## 6. Kept, and added

- **Tap-to-move is untouched.** *"The tap to move is actually really good."*
- **Attack-move by tap count**, his proposal, with no control added (*"maybe we
  don't need another verb"*). **He did not choose which way round; this build
  chose ONE TAP = ATTACK-MOVE, TWO TAPS = TRAVEL**, and the reason is written
  into the file: getting attack-move when you wanted travel costs you a fight
  you can walk out of, whereas getting travel when you wanted attack-move is the
  failure he named — a hero walking through enemies unresponsive — so that one
  must not be the accident. Travel is the deliberate refusal to engage, so it
  asks for the deliberate gesture. **The first tap commits in the same frame**
  and the second upgrades it, so nothing waits on a double-tap timer. Taught as
  steps 2 and 3 of the guided first run.
- **The trodden path**, carried over from version B's findings. Measured: 217
  cells marked by a 14-second walk, fading to 72 after 30 s idle (`TREAD_S` 34).
  It cuts the growth where a hero has walked and closes behind it. It does not
  touch the leash rule.

---

## The gate, re-run against the corrected artifact

### Frame

| size | dead blocks (of 84) | fraction | where | verdict |
|---|---|---|---|---|
| 390 × 844 | **0** | 0.0% | — | pass |
| 412 × 915 | **0** | 0.0% | — | pass |
| 320 × 568 | **3** | 3.6% | r2c1, r5c4, r7c5 | pass |

Threshold is one seventh (14.3%). Quadrant mean sd at 390 × 844:
**25.2 / 20.8 / 40.0 / 25.7** — even, all far above the dead threshold.

**This is where the correction pass nearly failed, and the gate is what caught
it.** The first corrected build measured **8 dead blocks (9.5%)**, all of them
in the two jungle columns, and an attempt to fix it by lightening the canopy
made it **worse — 22 blocks, 26.2%, over the threshold and a hard fail.**

The diagnosis, once measured rather than guessed: a dead block had mean L\* 27.6
and sd 4.50 with a range of 20–71. **The whole jungle palette lived inside
twelve points of L\***, so no amount of re-tinting inside it could produce
variance. On the old bright ground a dark crown had all the contrast it needed;
on a dark jungle floor it had none. Two changes fixed it, and both are more
truthful to the direction than what they replaced:

1. **Crowns are sized so the floor shows between them** (radius 1.5 + 2.2·g, was
   2.3 + 3.4·g, against a 7-unit cell). They were overlapping into a paint layer.
2. **Live tips at the card's own `#305e38`, at a size that survives the
   downscale.** The card always licensed L\* 34 for tips; the old build drew them
   sub-pixel and only on thin growth.

Result: **0 dead blocks, and the frame got cheaper** — smaller ellipses cost
less. A worked example of the gate finding a real defect that eyeballing had
passed twice.

The 3 remaining blocks at 320 × 568 are unbroken canopy in the enemy jungle.
**Adjudicated, not relitigated:** a block of unbroken canopy is the direction
working — it is the wild holding ground nobody has taken — and at 3.6% against a
14.3% threshold it is not the failure the test exists to catch.

### Population

Every container holds real content at rest:

- **Card panel** — 3 slots at 44 px, empty slots drawn as empty slots, plus the
  accrual track, present and inert when the hand is full.
- **Strip** — 6 gauges and 10 pips, all populated from frame one.
- **Race track** — both markers, the hatched gap and the lead wedge at 0:00.
- **Phase strip** — the retraction wedge and both event marks for the whole match.
- **Jungle panel** — 6 rows × (2 gauges + 13 pips) = 12 gauges and 78 pips, with
  the key and the crude-labelling caveats pinned as a footer. All six rows are
  visible without scrolling at all three sizes, 320 included.
- **Board** — 6–8 camps holding 24–31 units at rest; the paths, pockets and
  thickets are there before anyone touches anything.

### Bill

Budget line: milliseconds per frame, ceiling 16.7, target ≤ 8.

| reading | total | sim | terrain | draw |
|---|---|---|---|---|
| 390 × 844 | **6.94 ms** | 0.36 | 3.84 | 2.73 |
| 412 × 915 | **6.49 ms** | 0.32 | 3.50 | 2.67 |
| 320 × 568 | **6.92 ms** | 0.32 | 3.74 | 2.86 |

**Under target at every reading**, on a grid that is 1.53× denser than the
shipped build's (`CELL` 16 → 14, map 1000 → 1150 wide). An intermediate build
measured 8.00–8.05 ms; `REBUILD_SLICES` went 6 → 10, which spreads the terrain
rebuild over 167 ms — well inside the ~0.4 s lag the card already specifies for
the growth boundary.

**The honest caveat is unchanged and still stands.** This is a 12-thread desktop
with no throttling. A mid-range phone's single-thread JS is commonly 3–5×
slower, which would put this at roughly **20–33 ms** — over the ceiling.
`REBUILD_SLICES` and `CELL` are still the cheap levers. **Not measured on a
phone — unverified, not "fine".** `/hone`'s note that it needs real S26 numbers
is untouched by this pass.

### Card audit, against the artifact

Runnable checks, run rather than remembered.

| refusal | check | result |
|---|---|---|
| F1 no fence/ring/dash/arrow marks the leash | `grep -c setLineDash` / `leashRing\|drawFence` / `ctx.arc(` | 0, 0, 0 — **pass** |
| F2 no static painted terrain *(amended, A2)* | `grep -cE 'jungleRegion\|JUNGLE_POLY\|terrainPath'` | 0 — **pass** |
| F3 nothing symmetrical in the growth | numeric probe: mean absolute difference of vegetation across a top–bottom mirror, 1,215 samples | **0.232 mean** (was 0.091) — **pass, and more unmirrored than before** |
| F4 no glow, drop shadow or blur | `grep -cE 'shadowBlur\|box-shadow\|filter:.*blur\|createRadialGradient'` | 0 — **pass**; 0 gradients of any kind |
| F5 no health bar over any unit | bar geometry in the unit draw path | 0 — **pass** |
| F6 nothing in the command bar is irregular | `border-radius` above 0 anywhere | 0 — **pass** |

**Three of these needed a judgement, and they are stated rather than waved
through:**

- **F1 and the settle acknowledgement.** Settling draws a brief mark at the
  hero's stopping point. It is **not** a leash marking: it is transient (0.8 s),
  it is drawn at the hero rather than along a boundary, and it is the same
  vocabulary as the tap acknowledgement that was already there and already
  gated. Nothing persistent marks the limit. **F1 holds.**
- **F5 and the hero condition bars.** F5 bans a health bar **over a unit** — a
  unit's state must read from the unit — and its check is bar geometry inside
  the unit draw path, which is still 0. The condition bars are in the command
  bar, which is the decision substrate and which the design requires to carry
  *"insight into how their hero is doing"*. **F5 holds**, and this is recorded
  because a cold read could mistake it for a violation.
- **F6 and the accrual hatch.** The combine cost is drawn as a 2-px CSS stripe
  hatch. That is strict order, not an organic motif, and it is the same device
  the race track's gap already uses. **F6 holds.**

Materials, Rhythm and Signature by eye against the render:

- **Materials** — bone / slate / growth as specified, plus the new duff tone for
  jungle openings and the A2 amendment above. The card's `#0b1811` ground and
  `#305e38` tips are now used **more** literally than in the shipped build.
- **Rhythm** — scar 18 s, wave 11 s, camp respawn 50 s, retraction 46%→8%,
  telegraph 60 s: unchanged. **`SEAM` 0.055 → 0.072**, so the band of growth is
  deep enough to read at the new lane width. That is a tuning of a rhythm
  number, not a change of ratio.
- **Signature** — *the road opening* survives the amendment and is stronger for
  it: the seam is now a dark band that the bright road writes itself over as you
  push, instead of a soft change of tint.
- **Banned defaults** — none present. In particular the bar did not become "the
  dashboard": it went the other way, from ~37 figures to 3.

### Critique

- **Name test.** Still nameable from the artifact alone: something ordered is
  being eaten, and the ordered thing is now clearly *roads through a forest*
  rather than a tinted field. **Pass.**
- **Coarse test.** Blurred to values, the frame is a dark mass with three pale
  roads through it, each terminating at a different height, each with a dark
  band across it. The focal path is the seam. **Pass, and cleaner than before** —
  the four value tiers replaced two.
- **Delete test.** The most decorative element is now the tree thickets. Deleting
  them leaves the jungle a texture with no obstacles and nothing to route
  around, and the semi-open character collapses into open ground. **Kept, and
  they earn it.**
- **Payoff test.** The moment your world grows or closes now has 61% of the board
  to act on instead of a strip. **Pass, and this is the correction's main win.**
- **Edge test.** Held at 320 × 568: all six camp rows visible, the glyph key
  pinned and visible, card targets still 44 px, no horizontal scroll anywhere.
  The bar takes 39.8% there, which is the floor doing its job on a small screen.

### What this pass caught and fixed rather than deferring

1. **The corridor was still eating half the board** on the first corrected
   build — measured at 50/50 tint-to-jungle. `TINT_R` 112 → 64, and the
   vegetation ramp moved in behind it. Now 28% / 61%.
2. **The jungle paths were invisible.** They were cleared but the cleared ground
   had no value of its own, so a path was a dark slot in a dark forest. Fixed by
   the two-tone floor, and widened (clear within 20, full canopy by 50).
3. **The dead-block regression**, twice — see the Frame section. The gate caught
   what two visual passes had accepted.
4. **The frame went over target** at 8.00 ms. `REBUILD_SLICES` 6 → 10, tree
   strokes 3 → 2.
5. **The glyph key was cut off at 320 and 390.** The camp rows scrolled and the
   key scrolled with them, so the alphabet the panel had just been rewritten in
   was unreachable — the same class of failure the last gate caught with the
   crude-labelling note. Fixed by pinning it as a footer outside the scroll area
   and shortening it; all six rows now fit at 320.
6. **Creep speed was not normalised** for the new lane lengths, so the side lanes
   would have resolved first every match.

### Verified still true after the corrections

- **The opponent is passive by default.** 130 s of no input leaves the lanes at
  **0.47 / 0.50 / 0.45** and the hero at **320/320**, untouched. This is a
  mandatory property and the project has already had to retract one finding for
  losing it.
- **The guided first run advances through real gestures** — driven with real
  pointer events, it reached step 3 through pan → tap → double-tap — and every
  step still also advances on a timeout, so it cannot wedge.
- **Panning issues no order.** A real drag moves the camera and leaves
  `hero.order` null.
- **The pool runs dry at ~12:20** of the 15:00 match rather than automatically,
  which is what the provisional 520 was set to do.

### 7. What the deletion diff caught — the rule earned its keep again

The project's standing rule is *"after every rebuild, diff the deletions, never
trust the insertion count."* It is written about map rebuilds. Applied to this
artifact it caught one real loss that the gate would not have:

**The camp panel's crude-labelling note was silently dropped.** Rewriting the
readout from figures to glyphs replaced the row format and the note under it in
one move, and the note carried three things that are not decoration: *camps
scale with match TIME* (12's rung-3 time curve), *nothing patrols* (12's rung-5
rejection), and *mana is shown only because the readout specifies it — whether
mana exists is open* (a live open question, which the README still claimed was
on screen). The card's own Floor requires the crude things to be **labelled
crude on screen**, so losing it was a floor failure, not a tidy-up.

Restored, cut to the irreducible facts so it survives 320 wide, and paid for by
deleting the column header the pinned key had made redundant. All six camp rows
are still visible at every size.

**Nothing else in the 174 deleted lines was live content** — every other
deletion is a line whose corrected replacement sits beside it in the diff.

---

# Second correction pass — 2026-08-13

His verdict on the first corrections: *"this is an improvement to your points
for the lane and the boards."* Then four substantial notes and one new
mechanic. **Same artifact, same commitment card, same direction. Five
corrections, not a redesign, and no second version.** Two card lines were
amended deliberately and on the record — **F3** and **Budget**, both in
[`COMMITMENT-overgrowth.md` § Amendments](COMMITMENT-overgrowth.md#amendments).

## 1. The layout — rotational symmetry kept, mirror symmetry deleted

*"I'm not crazy about the layout. It's very symmetrical... their maps don't
look so NASCAR track with a line in the middle."*

The distinction that carries the whole correction is in
[A3](COMMITMENT-overgrowth.md#a3--f3-mirror-symmetry-is-banned-rotational-symmetry-is-required-2026-08-13-round-2)
and is not repeated here. What was built:

- **One half is authored; `rot()` generates the other.** `rot(p) = (1000-x,
  2000-y)` in the reference frame. The east lane **is** the west lane rotated
  and reversed. Mid's second half **is** `rot()` of its first half. Every
  path, tree, clearing and camp is authored once and rotated once. Fairness
  cannot drift, because there is nothing to keep in sync.
- **The bases came off the centre line.** Mine at reference (392, 1876),
  theirs at (608, 124) — 124 world units either side of centre. There is now
  no axis for a mirror to run down, which is the NASCAR read killed at the
  root rather than disguised.
- **Mid runs diagonally.** It leaves my base heading east, swings out to
  x = 596, crosses the centre on the diagonal, comes back west to x = 404 and
  enters their base from the other side. Excursion **248 units** of a
  1000-unit reference width. Portrait forbids a true corner-to-corner mid;
  this is the shape that is available and it is an S, not a rule.
- **The two jungle regions are different shapes.** Because mid leans east on
  my half, the east region pinches to a neck at y ≈ 1500 while the west region
  opens out — and on their half it is the other way round. Same ground per
  side, different ground.

Measured at the gate:

| check | result |
|---|---|
| west lane rotates onto east lane, max vertex error | **0.0000** |
| mid rotates onto itself, max vertex error | **0.0000** |
| bases rotate onto each other | **0.0000** |
| all 12 camps rotate onto each other, max error | **0.0000** |
| side lane lengths | **2293.2 / 2293.2** (mid 1912.3) |
| base offset from the centre line | **124.2** world units |

And the drawn board is *not* symmetric under anything, because the growth is
seeded independently of the geometry — the numeric probe is in A3.

## 2. Jungle traversal — a route network instead of two corridors

*"The jungle literally is just two vertical lines with pockets. There's no
angles."* / *"the ability to traverse the jungle needs to be made a much better
experience."*

The ask is explicitly **not** vision denial — he noted himself that with no fog
and both heroes always on the minimap, sightline cutoffs matter less. It is
that moving through the jungle should present routes and choices.

- **21 path polylines per half, 42 in all, and every one of them bends.** No
  straight runs.
- **Two closed loops in the west region** (w2–w4–w3, and w4–w6–w5–w3), so
  between any two of its clearings there is more than one way to go.
- **One neck in the east region** at (742, 1502) joining a south chamber to a
  north chamber, with a loop only beyond it. The two regions have deliberately
  different topology: one is a choice of routes, the other is a chokepoint.
- **16 clearings**, at the junctions, so a route is legible as a route — you
  arrive somewhere and can see where the ways part.
- **28 tree thickets at angles**, sitting between the routes and inside the
  loops, two of them pinching the east neck from either side without closing
  it.
- **12 camps in pockets 70–100 units off the routes** — the pocket's clearing
  opens toward a path, but you leave the path to take one.

Measured on the walkable grid at 5-unit resolution, bounds and thickets only
(claim excluded, because claim is the leash and it is *supposed* to gate you):

| check | result |
|---|---|
| walkable cells | 76,420 |
| reached from my base | **76,420** |
| sealed cells | **0** |
| every camp reachable | **yes** |
| every clearing reachable | **yes** |
| enclosed obstacles (thickets you can pass either side of) | **28 of 28** |

**Every thicket on the board is something you route around rather than
something that walls you in**, which is the semi-open character stated as a
number instead of asserted. Obstacle sizes come in identical pairs, which is
the rotational symmetry showing up in a test that was not looking for it.

A separate run of the same flood fill **with** claim applied reports camps 6,
8, 9 and 10 unreachable at 0:00 and a 288-cell pocket behind the enemy line.
That is the **leash working**, not a seal — those are on their half, behind
their front line — and it is recorded here so a future reading of the same
number does not mistake it for a defect.

## 3. The camera — in by 2.4×, and the texture that costs

*"Right now it's a little too top down far away"*, wanting a good view of the
hero, the spells, the creeps *"and a good view of the actual textures of the
game."* Target: *"closer to the max zoom out of typical MOBAs, but maybe
slightly more just because it's a mobile game."*

The board now holds **33% of the map's width or 25% of its length, whichever
is tighter** — a MOBA's far end, allowed the little extra a phone wants. On a
390-wide board that is s = 1.148 against the shipped build's 0.467:

| | shipped | corrected |
|---|---|---|
| hero | 12.6 px | **29.8 px** |
| creep | 4.0 px | **9.6 px** |
| road width | 26 px | **62 px** |
| one grid cell | 6.9 px | **16.1 px** |
| map width on screen | 78% | **29.5%** |
| map area on screen | 47% | **7.4%** |

**The last row of the first table is the consequence that is not a camera
value.** At 16 px a cell, a flat fill reads as a flat fill, and this is the
first request in the whole design for material to be legible. What that
actually cost is section 6.

**Panning had to become good, because a closer camera spends navigation
rather than information** — the board pans and nothing is hidden, so the whole
cost is getting there:

- **The drag carries.** Velocity is tracked on the frame clock and decays over
  ~0.19 s after release, and it stops dead at the map edge rather than
  bouncing. Verified with real pointer events: a flick carried **206 world
  units** after the finger left the glass.
- **The minimap is a tap target** and is larger for it (58 → 74 px). Tapping
  it centres the camera there. It used to issue a **hero order** at whatever
  world point sat under it — wrong at any zoom, unusable at this one.
  Verified: tapping it moves the camera and leaves `hero.order` null.

## 4. The home field — a boundary in the lane, and a buff that lingers

**Rendering**, his words: *"not a literal force field, just some sort of
visual indicator maybe in the lane that tells you the line in the sand of
where minions will be buffed versus where they won't be."*

The disc wash, its cross-hatch and its edge ring are **gone**. What replaces
them is a survey threshold drawn across each lane at the field's radius, in
vector rather than in the terrain grid — six marks, three lanes by two sides,
one re-solved per frame round-robin because the radius moves at 0.58 world
units per second. It walks back down the lane as the field retracts, so the
retraction schedule reads as **movement** rather than as a shrinking circle.

Vector because it has to stay a hairline: at `CELL` 14 the terrain buffer
cannot draw a 3-unit line, and a band would read as a second front line —
exactly the confusion [A2](COMMITMENT-overgrowth.md#amendments) was written to
end.

**The rule and the picture now agree, and they did not before.** The old
`apron()` returned a gradient and creeps were empowered at `apron > 0.22`,
which put the real buff boundary at **0.879 R** while nothing was drawn at
either radius. `inField()` is one comparison and the mark is drawn at exactly
that radius.

**The lingering buff is new design, not presentation**, and needs routing into
ticket 05 — it is not written into the concept doc by this pass. His words:
*"as minions leave the force field, as they're pathing through their lane and
walking out of the force field, there is a timer that it is still up before it
dissipates"*, because otherwise *"they can't just sit at the line of the force
field and then wait for them to come out and farm minions"*, and what it buys
the defender is *"a little bit of breathing room."*

Built as `P.FIELD_LINGER`, **provisional and crude like every other number
here**, defaulting to 6 s and on the tuning panel so it can be felt. The
empowerment is visible on the unit and **wears off rather than switching off**
— the creep shrinks back to its base size over the last two seconds. No
strobe, and no bar over the unit (F5 holds).

Verified by driving the sim: a creep left the field at t = 19.5 s and held the
buff until t = 25.5 s — **6.0 s exactly**.

**Not asked and not answered:** this extends the defensive floor past the
field's own radius, which interacts with the retraction schedule — as the
field pulls back, the lingering buff is what stops the retraction being a hard
cliff. Whether that is intended is his to say.

## 5. Tap intent — confirmed, and the hard problem answered

He arrived at the build's assignment independently and with a better reason
than the build had: *"maybe attack is one and then just move is two. So if a
player chooses to spam to run away, it's always run away versus choosing to
attack is deliberate."* **One tap = attack-move, two taps = travel. Unchanged.**

Then he named the failure the assignment implies, and it is the sharpest input
question in the design:

> *"How do you spam tap to force your hero to move without attacking really
> quickly, but then somehow swap on a dime to the last tap being taken as a
> single tap?"*

The naive reading really is broken. Every lone tap must wait out the
double-tap window to learn whether a second is coming, so either **attack-move
is late by that window on every single use**, or **a fast run of intended
moves is chopped into alternating attacks and moves.**

**The resolution, and it adds latency to nothing:**

1. **Nothing waits.** The first tap issues attack-move in the same frame; a
   second within 0.36 s **upgrades** that order to travel. It does not resolve
   a deferred decision, it revises one already made. This was already true and
   it is what makes the rest possible.
2. **A run latch carries the intent forward.** Once a double tap has said
   travel, the next 0.5 s of taps are travel **wherever they land**, and each
   tap refreshes the window. This is what fixes the spam case: fleeing means
   tapping ahead of yourself along a route, so every tap lands somewhere new,
   and distance-gated double-tap detection would have read each one as a fresh
   single tap — the chopping failure, exactly.
3. **An aimed tap breaks the latch immediately.** A tap on a camp or a thicket
   is unambiguous — nobody flees *into* a camp — so it drops out of the run and
   engages in the same frame with no pause. That is *"swap on a dime"*,
   answered.
4. **The run is visible while latched** — the travel mark gets a second box
   around it — so the player can see which way the next tap will be read.

**What it costs, stated rather than buried.** For 0.5 s after a flee tap you
cannot issue an attack-move onto **empty ground**. Aimed attacks are
unaffected and instant. Attack-move after a beat is unaffected and instant.
The one unreachable input is *"stop running and attack-move at nothing in
particular, within half a second"*, and you leave the run by pausing rather
than by waiting on a timer. **`/hone` should have this**: no latency was added
anywhere, which is worth more than the rest of this pass, but the 0.5 s window
is a feel number and 0.5 is a guess.

Verified by driving `tap()` with the sim clock advanced between calls:

| input | result |
|---|---|
| single tap, empty ground | `press` (attack-move), same call |
| second tap, same spot | `travel`, latch on |
| six taps at six **different** points, 0.12 s apart | **all `travel`** — not chopped |
| tap on a camp while running | `engage`, same call, latch cleared |
| empty ground 0.7 s after the last flee tap | `press` |
| **empty ground 0.2 s after a flee tap** | **`travel` — the documented cost** |

## 6. What the camera cost, and a real bug it exposed

### The dead-block regression, and how far it went

The first draft of the closer camera measured **41 dead blocks of 84 (48.8%)**
against a 14.3% threshold — a hard fail, and nearly three times the shipped
build's own reading. **The shipped build was re-measured beside it in the same
session with the same code**, because a fixed 7 × 12 block grid at a 2.4×
closer camera is not measuring the same thing, and the comparison is the only
honest reading:

| build | dead blocks | threshold |
|---|---|---|
| shipped (`whole-a-reclaim` at HEAD) | 24 / 84 = **28.6%** | 14.3% |
| corrected, first draft | 41 / 84 = **48.8%** | fail |
| **corrected, shipped here** | **2 / 84 = 2.4%** | pass |

*(Method, stated because it is a reconstruction rather than the original
gate's code: 7 × 12 blocks over the live board canvas, a block is dead if the
standard deviation of its CIE L\* is below 6. The absolute counts are not
comparable to the last pass's table; the two rows measured in this session
are comparable to each other, which is the point.)*

Three things were tried. **Two of them made it worse and are recorded because
that is the useful part:**

1. **A per-cell value grain.** At 16 px a cell it painted a visible
   **chequerboard** across the entire board. Reverted; replaced with sub-cell
   aggregate placed from two independent hashes over a range that overspills
   the cell, so the grain has no lattice to give away.
2. **A low-frequency value wash on the jungle floor.** It moved the opening
   tier's mean **down 5 L\*** and its variance **down**, collapsing the
   canopy/opening separation. Reverted. The project's own record — *"what
   worked was structure, not colour"* — was right again, for the third
   consecutive pass.
3. **Structure at a scale a block can resolve**, which is what worked: three
   crowns to a cell instead of one, each with its own value; live tips drawn
   **after** every crown in the cell rather than between them; shade under
   thick canopy; scrub in the openings; aggregate on every surface; sleepers
   and ruling three-to-a-cell instead of one-every-three-cells.

### The bug underneath it, and it was load-bearing

Chasing the tips down to **0.4% of the canopy's pixels when they were meant to
hold ~12%** found this in `h2`, the hash the whole board's texture runs on:

```js
n = (n ^ (n >> 13)) * 1274126177;     // lands above 2^53
```

The double drops its low bits, so the final mix is fed a number with a zeroed
bottom byte. Measured over the whole 82 × 143 grid, for **every** stride
pattern the file uses:

> **`h2` never once returned a value above 0.5.** Mean 0.250, fraction above a
> half **0.000**.

Everything downstream had been running on half its range: crown mottle only
ever reached the dark half of the growth palette, the bright `#46804f` tip
could **never** fire (`to > 0.82` was unreachable), crown jitter and creep
spacing used half their spread, and `fbm` returned [0, 0.5] so the growth
threshold was biased low and there was systematically more canopy than the
number asked for.

**The previous pass diagnosed the symptom honestly and treated it as a palette
problem** — *"the whole canopy palette lives inside twelve points of L\*"*, and
the two fixes it shipped were real improvements. But the cause was this. Fixed
with `Math.imul`, which keeps every step inside int32: mean 0.503, fraction
above a half 0.509.

The fix alone took the frame from **9 dead blocks to 2**, and it is why the
value tiers below land where the card said they should rather than where the
last pass could get them.

### The value-tier budget, re-measured

The project's recorded rule is that board legibility is a **value-tier budget,
not a palette**. Measured on the drawn terrain, classified by the sim's own
fields:

| tier | shipped | corrected | recorded target |
|---|---|---|---|
| canopy | 11.9 (sd 6.8) | **9.9 (sd 10.7)** | 9 |
| jungle opening | 24.2 (sd 9.4) | **24.4 (sd 10.3)** | 17 |
| their bone | 58.3 (sd 7.0) | **53.2 (sd 9.6)** | 55 |
| your bone | 83.9 (sd 7.1) | **79.2 (sd 7.2)** | 85 |

**Four separated tiers, all within a few points of where they were, and every
one of them now carrying real internal variance instead of near-none.** That
second column is the whole of what "texture and material" means as a
measurement.

### The Frame, at four sizes

| size | dead blocks (of 84) | fraction | quadrant mean sd | verdict |
|---|---|---|---|---|
| 390 × 844 | **2** | 2.4% | 12.2 / 13.7 / 14.0 / 14.8 | pass |
| 412 × 915 | **2** | 2.4% | 12.1 / 13.8 / 14.2 / 15.2 | pass |
| 360 × 640 | **1** | 1.2% | 12.4 / 15.7 / 14.2 / 14.7 | pass |
| 320 × 568 | **1** | 1.2% | 12.4 / 14.9 / 14.4 / 14.9 | pass |

The one or two survivors at every size are the **bright road** (L\* 80–81,
sd 5.4–5.9). **Adjudicated rather than relitigated**, on the same footing the
last pass used for unbroken canopy: the road is the *order*, it is surveyed,
and a surveyed road being uniform is the direction working. At 2.4% against a
14.3% threshold it is not the failure the test exists to catch.

## The Bill, round 2

Budget line: milliseconds per frame, ceiling 16.7, target ≤ 8, and the card's
own arithmetic expected ≤ 6. See
[A4](COMMITMENT-overgrowth.md#a4--budget-the-6ms-expectation-is-exceeded-and-the-8ms-target-is-at-its-edge-2026-08-13-round-2)
— **the ≤6 ms expectation is exceeded and this is not shipped quietly.**

**The box was under load while these were taken** — a 12-thread desktop
carrying a load average of 7 to 12, shared with other work — so single
readings are worthless and absolute numbers are contaminated. What is reported
is the **median of 20 samples**, and the shipped build measured **immediately
before and after** each run so the comparison carries the same contention:

| | shipped | corrected | delta |
|---|---|---|---|
| run A, median | 6.14 ms | **7.68 ms** | +1.54 |
| run B, median | 7.59 ms | **8.74 ms** | +1.15 |
| corrected, min observed | — | 6.77 ms | |
| corrected, terrain / draw (median) | 3.3 / 2.6 | 3.7–4.1 / 3.7–4.3 | |

**The delta is what this pass controls and it is +1.2 to +1.5 ms**, for a 2.4×
closer camera and a terrain buffer with 4× the pixels. Against the last gate's
uncontended 6.94 ms for the shipped build, that projects to roughly **8.1–8.4
ms unloaded — over the ≤8 target, well under the 16.7 ceiling.**

What was paid to keep it that close:

1. **The terrain blit is clipped to the visible slab.** The screen holds 7% of
   the map; the whole 1150 × 2000 buffer was being pushed through the
   rasteriser every frame to be clipped.
2. **Trees and camps are culled to the same slab.** The thicket count doubled
   with the rotational rebuild — 56 strokes a frame to have 50 of them
   clipped.
3. **`REBUILD_SLICES` 10 → 28**, spreading a full terrain repaint over ~470 ms.
4. **Aggregate marks 4 → 2**, at a larger size, for the same coverage at half
   the call count.

**The identified next lever, not taken here:** the floor, aggregate, litter
and scrub are entirely static — they depend on vegetation and lane distance,
never on claim — so they could be baked once into a second buffer and blitted
per slice, leaving only the claim-dependent layers to redraw. That is a real
refactor with real regression risk and this pass is a correction pass, so it
is recorded rather than attempted.

**Unchanged and still true: not measured on a phone.** `/hone`'s note that it
needs real S26 numbers is untouched, and is now more pressing than it was.

## Card audit, round 2

| refusal | check | result |
|---|---|---|
| F1 no fence/ring/dash/arrow marks the leash | `grep -c setLineDash` / `leashRing\|drawFence` / `ctx.arc(` | 0, 0, 0 — **pass** |
| F2 no static painted terrain *(amended, A2)* | `grep -cE 'jungleRegion\|JUNGLE_POLY\|terrainPath'` | 0 — **pass** |
| F3 mirror banned, rotation required *(amended, A3)* | numeric probe of drawn L\*, 42,075 samples | rot 14.6, mirror 21.2 / 22.9 — **pass** |
| F4 no glow, drop shadow or blur | `grep -cE 'shadowBlur\|box-shadow\|filter:.*blur\|createRadialGradient\|createLinearGradient'` | 0 — **pass** |
| F5 no health bar over any unit | bar geometry in the unit draw path | 0 — **pass** |
| F6 nothing in the command bar is irregular | `border-radius` above 0 anywhere | 0 — **pass** |

**Two judgements, stated rather than waved through:**

- **F1 and the home-field mark.** The threshold drawn across each lane is a
  line on the board that was not there before, and F1 bans exactly that *for
  the leash*. It is not the leash: it marks the **home field**, whose boundary
  is a positional rule that has nothing to do with how far the hero may go,
  and the leash still has no rendering of its own. The two cannot be confused
  by construction — the leash's boundary is the front line, a **dark band**
  that moves with the creeps; this is a **bright hairline with posts** that
  crawls slowly toward a base. **F1 holds**, and this is recorded because a
  cold read could take it for a violation.
- **F3 and the vegetation field.** Because paths, clearings, camps and lanes
  are now exactly rotationally symmetric, the vegetation field derived from
  them is too. The *growth* is not — the threshold is noise-modulated with no
  rotation term — and the probe measures the drawn result at 14.6 mean absolute
  ΔL\* under rotation, against 21.2 and 22.9 for the two mirrors. This is the substance of A3 and it is required for
  fairness, not a slip.

Materials, Rhythm and Signature against the render:

- **Materials** — bone / slate / growth as specified, plus the duff tone whose
  value moved (L\* 17.5 → 20.6) so the canopy and opening tiers stopped
  converging, and the aggregate / litter / scrub / shade that the closer camera
  required. Every green in the wild is still the card's own `#0b1811`,
  `#16301f`, `#305e38` or the `#46804f` the last pass added — and `#46804f`
  can now actually appear, which it could not before.
- **Rhythm** — scar 18 s, wave 11 s, camp respawn 50 s, retraction 46%→8%,
  telegraph 60 s, `SEAM` 0.072: all unchanged. `FIELD_LINGER` 6 s is new and
  is a mechanic's number, not a ratio.
- **Signature** — *the road opening* is unchanged and reads harder at the new
  distance, because the road now has a surface for the growth to peel off.
- **Banned defaults** — none present.

## Verified still true after the second corrections

- **The opponent is passive by default.** 130 s of no input leaves the lanes at
  **0.48 / 0.49 / 0.47**, the hero at **320/320**, and `foe.order` null. This is
  a mandatory property and the project has already had to retract one finding
  for losing it.
- **The guided first run advances through real gestures** — driven with real
  pointer events it reached step 4 through pan → tap → double-tap, and every
  step still also advances on a timeout, so it cannot wedge.
- **Panning issues no order**, and neither does tapping the minimap.
- **No runtime errors** in the console across every run above.

## What the deletion diff caught this time

The standing rule is *"after every rebuild, diff the deletions, never trust the
insertion count."* Applied to this pass it caught one thing worth recording:
the old `apron()` gradient was deleted wholesale when the field became a
boundary, and it was carrying a **rule** as well as a rendering — the
`apron > 0.22` empowerment test. Deleting the drawing without noticing would
have deleted the home field's entire mechanical effect. It was replaced by
`inField()`, which is the same rule stated once, and the 12% disagreement
between the old test and the old drawing is section 4.

`apronCore()` was **kept**, unchanged: it is what cuts the wild back around a
base, it is a separate job from the boundary, and nothing in the round-2
feedback touched it.
