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
