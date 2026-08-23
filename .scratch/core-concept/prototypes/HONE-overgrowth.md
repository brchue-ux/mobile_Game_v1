# Hone pass — `whole-a-reclaim.html`

Run against the already-committed, already-corrected artifact per `/hone`'s own
contract: the direction does not change here, and nothing below is a redesign.
Card: [`COMMITMENT-overgrowth.md`](COMMITMENT-overgrowth.md). Findings this
pass builds on: [`FINDINGS-overgrowth.md`](FINDINGS-overgrowth.md).

**Measurement conditions, restated because a number without them is a
rumour:** headless Chrome via `chrome-devtools-axi`, `whole-a-reclaim.html`
served from `python3 -m http.server`. Interaction claims are driven through
the file's own exposed gate apparatus (`window.__proto`) and through real
`PointerEvent`s dispatched at real DOM elements, never read off the source.
Frame cost is `window.__proto.perf()`, the same instrument `FINDINGS` uses.
Two sizes throughout, the same two the card names: **390×844** (composed) and
**320×568** (the card's own hostile condition).

---

## Entry

**The substitute line**, per `/hone`'s own rule for a session honing what it
just helped correct — one honest reaction to the artifact as built, stamped
before any reading below and not revisable afterward:

> *It reads clearly as order cut through wild — a bright causeway laid into
> dark growth, legible at a glance — but everything holding still right now
> feels inert: no unit is doing anything, the bar's gauges are thin flat bars
> that don't pull the eye, and the one card in hand just sits there with no
> sense that touching it would do anything.*

That names two things this pass owes an answer to: nothing under the finger
answers touch (lever 3), and nothing punctuates the moment the design's own
signature happens (lever 6). Both are addressed below. Read the card next.

---

## Two build decisions closed 2026-08-22 — build against them

Neither of these is `/hone` work. Both are recorded here because they had to
land *before* honing could start (the readiness report's own two named
prerequisites), and everything after this section is measured against the
artifact **with both applied**.

### 1. Tap-sequence disambiguation — accepted as-is, no code change

The run-latch scheme in `FINDINGS-overgrowth.md` §5 is now the accepted
resolution to the sharpest open input question (decision record:
`mg-prototype-redesign-readiness-decision-tap-sequence-disambiguation`,
2026-08-22, *"accepted as-is, for now"*). The implementation was already
built and measured — nothing in `tap()`, `stepHero()`'s order handling, or the
run-latch timing (`RUN_W`, the 0.36 s upgrade window) was touched this pass.

**Re-verified rather than assumed**, since this pass does touch nearby DOM
code (`updateBar()`'s hand rendering — see the floor repair below) and a
regression there was worth ruling out explicitly:

| input | result | matches FINDINGS §5 |
|---|---|---|
| single tap, empty ground | `press` | yes |
| second tap, same spot | `travel`, latch on | yes |
| six taps on the open lane, 0.12 s apart | all `travel` | yes |
| tap on a camp while running | `engage`, latch cleared | yes |
| empty ground 0.7 s after the last flee tap | `press` | yes |
| empty ground 0.2 s after a flee tap | `travel` — the documented cost | yes |

Unchanged, as required.

### 2. Command bar — 15% bigger than its built size

The captain's own number for the one open `/hone` prerequisite he had to give
a figure for (*"the bottom screen needs to be a little bigger... I have an
S26 Ultra and it feels a tad small"*, 2026-08-12 — cited in
`COMMITMENT-overgrowth.md`/`FINDINGS-overgrowth.md`/`01-battlefield-geometry.md`,
no proportion given until now).

**Implementation.** One CSS custom property, `--bx: 1.15`, declared once on
`:root` with the decision cited inline, and every content dimension in `#bar`
wrapped in `calc(Npx * var(--bx))` — a single auditable multiplier rather than
thirty hand-rounded pixel guesses. `#bar`'s own `height`/`min-height`/
`max-height` scale the same way: **32% → 36.8%, 226px → 260px, 312px → 359px**.

**Deliberately NOT scaled: every `1px solid` rule.** The Materials line
specifies *"1px rules"* as a fixed property of the bar's strict order, not a
proportional one — a 1.15px hairline anti-aliases into mush and reads as
sloppy, not bigger. `border-radius` stays at 0 throughout (F6 unaffected).

**Measured, at both sizes:**

| viewport | bar height (was) | bar height (now) | card target | board height |
|---|---|---|---|---|
| 390×844 | 270 px (32.0%) | **310.6 px (36.8%)** | 50.6 px (was 44) | 533 px (was 574) |
| 320×568 | 226 px (39.8%, floor) | **259.9 px (45.8%, floor)** | 50.6 px | 308 px (was 342) |

### Two floor repairs the resize forced, labelled as floor repairs

Per `/hone`'s carve-out: these are not lever changes, they came from a real
break, and their form is *give the secondary text back its old size*, not
*shrink the primary content* — the six camp rows and the three card slots are
what the card's own Floor requires visible without scrolling.

- **`.pfoot` (the jungle glyph key) exempted from `--bx`.** At 15% bigger, its
  own text wraps enough extra lines inside its unchanged column width that it
  grew from ~28px to 72.5px tall at 320×568, which pushed `#rBody`'s six camp
  rows to **131px of content in a 123px box (clipping)**. This is the exact
  failure class `FINDINGS` round 1 already fixed once (*"the glyph key was cut
  off... shortened... all six rows now fit at 320"*) — the bigger-bar decision
  re-triggered it from the other direction. Fixed by holding `.pfoot` and
  `.pfoot span` at their original literal sizes: **`#rBody` now needs exactly
  139px and has exactly 139px, 0 clipping**, all six rows visible at both
  sizes, wording untouched (nothing was shortened this time; the whole key and
  the whole caveat line are on screen verbatim).
- **`.cnote` (the hand panel's status caption) exempted from `--bx`**, same
  class of squeeze: the caption text (which grows with game state — `S.log`
  can append an arbitrary message) was pushing `#hand`'s needed height past its
  box at 320×568. The three card slots themselves were never clipped (they sit
  above the caption and total 162px of a 196px box); only the caption's tail
  was cut. Exempting it dropped the overflow from 34px to 31px.

**What this floor repair did NOT reach, and it is named rather than
absorbed.** `#hand`'s overflow at 320×568 is **31px, pre-existing in the
already-shipped, already-gated HEAD build (measured there: 34px, same
`cnote` text)** — confirmed by serving the unmodified `git show HEAD` copy
side by side. It is not caused by this pass and is not one of the six levers,
so it is reported and left alone rather than pulled into scope here. The
three card slots remain fully visible either way; only a dynamic status line
tail is affected.

### What the resize cost, stated rather than hidden

The board absorbs the bar's growth (ticket 01's own principle), so the
camera's zoom `s` drops with it: **1.148 → 1.067 at 390×844 (−7%)**, which
re-opens the exact tension `FINDINGS`' round-2 pass fought hard to close (a
smaller `s` means fewer screen pixels per world-unit of canopy, which is what
made the dead-block count spike the first time). Re-run against the resized
build, same 7×12/sd<6 gate `FINDINGS` defines:

| size | dead blocks (of 84) | fraction | round-2 gate's own reading | verdict |
|---|---|---|---|---|
| 390×844 | 8–10 (varies run to run) | 9.5–11.9% | 2/84, 2.4% | **still pass** (threshold 14.3%) |
| 320×568 | 10 | 11.9% | 1/84, 1.2% | **still pass**, less margin |

Frame cost, same instrument, moved the other way (smaller board, less to
draw): **5.67–6.11ms** at both sizes, against 6.94/6.92ms before — under
target either way. **Not a hone finding — a cost of the captain's own
decision, adjudicated here rather than relitigated**: touching the terrain
constants that would recover the margin (`CELL`, crown radius, tip size) is
exactly the code this project's own history flags as fragile (three real
regressions across two correction passes, one a genuine hash bug), and
gate-adjacent tuning is `verve`'s work, not `hone`'s. Still comfortably inside
the threshold at both sizes; recorded so the margin loss isn't silent.

---

## Pre-flight — re-running `verve`'s finish gate, per `/hone`'s own instruction

Required before honing starts, because the size decision above is a real
structural change to an artifact this same session is touching. Beyond the
frame/bill numbers above:

- **Population.** Unchanged content at rest: 3 card slots (empty slots drawn
  as empty slots), 6 camp rows with full six-figure readouts, race track
  markers and hatch, phase strip wedge and event marks — all present at 0:00
  at both sizes, verified live.
- **Card audit, run not remembered:**

  | refusal | check | result |
  |---|---|---|
  | F1 no fence/ring/dash/arrow marks the leash | `grep -c setLineDash`, `leashRing\|drawFence` | 0, 0 — pass |
  | F2 no static painted terrain | `grep -cE 'jungleRegion\|JUNGLE_POLY\|terrainPath'` | 0 — pass |
  | F4 no glow/blur/gradient | `grep -cE 'shadowBlur\|box-shadow\|filter:.*blur\|createRadialGradient\|createLinearGradient'` | 0 — pass |
  | F6 nothing in the bar over 0-radius | `border-radius` above 0 anywhere | none — pass |

  F3 (symmetry) and F5 (no health bar on a unit) are untouched by anything in
  this pass — no geometry, noise seeding, or unit-draw code was edited — so
  they are not re-probed; the last measured values stand.

No dead frame, no empty container, nothing here is unfinished. Honing
proceeds.

---

## The six levers

### 1. Latency — no pass needed

Driven, not estimated: a real `PointerEvent('pointerdown')`→`pointerup` pair
dispatched at the board sets `hero.order` and `S.tapAck` **synchronously,
inside the handler**, before the dispatch call even returns. The same is true
for every DOM button now (see lever 3). The only latency anywhere is the
~16.7ms until the next paint at 60Hz — the definition of same-frame. Nothing
here waits on a timer before its acknowledgement fires. **No change; already
at the floor the lever names.**

### 2. Easing and weight — no pass needed, one shared change with lever 3

Measured by driving `advance()` and sampling `Math.hypot(vx,vy)` every 50ms:
hero velocity is a real exponential approach to `HERO_SPD` (132 u/s), not a
linear ramp — `kA = min(1, 520/maxv * dt)` — reaching 90% of max speed at
**~0.5s** and 95% at **~0.7s**, consistent with a heavy commander unit rather
than a light UI element. Arrival is not a hard stop either: an order clears
at `dist<6` while the hero still carries real residual velocity (measured
**~64 u/s, ~48% of max**, at the moment an order ends), so it visibly coasts
the last stretch rather than snapping still. Momentum on the camera pan
(`exp(-dt/0.19)`) and the tap acknowledgement's own decay (3.6/s) are both
already non-constant. **No defect found in the primary loop; already reads
as mass.**

One quirk was found and deliberately **not** touched: ordering the hero to
`hold` while at speed produces a brief overshoot-and-correct (it coasts past
the hold point on inertia, then reverses to return to it) rather than a clean
brake. Real, but `hold` (tapping your own hero) is not in the guided run's six
taught steps and is the rarest of the game's inputs; fixing hero
pursuit-braking physics is real regression risk in a subsystem this pass has
no other reason to touch, for a payoff scoped to an edge case. Named, not
fixed.

The one change that *does* touch this lever is shared with lever 3 below —
see the ledger.

### 3. Nothing dead under the finger — changed

**Reading, before.** `*{-webkit-tap-highlight-color:transparent}` is set
globally, and no `<button>` in the file had a press rule of its own — no
`:active`, no JS-driven state. Driven check: dispatching `pointerdown` on the
first card slot produced **zero visual change**; the only feedback arrived on
`pointerup`, via a class swap already gated behind the next `updateBar()`
tick. Every button in the bar and on the board overlay (`#recentre`,
`#cSkip`) was in the same state: rest and result, nothing in between.

**Change.** A delegated pair of listeners on `#app` sets/clears a `.pressed`
class synchronously on `pointerdown`/`pointerup`/`pointercancel`/
`pointerleave` — one wiring point, so a card rebuilt by `buildHand()` or a row
rebuilt by `buildTuner()` never needs its own. Press displaces the element
`1.5px * var(--bx)` straight down (no radius, no glow — F4/F6 unaffected) and
swaps to the board's own tap-acknowledgement ivory, `#efe6cd` — the exact
colour `S.tapAck` already uses for *"a tap registered"*, not an invented
accent. Release (removing `.pressed`) eases back over **130ms** (inside the
lever's 90–160ms range) because the rest rule carries the transition and
`.pressed` itself sets `transition:none` — press is instant, release is not,
the asymmetry the card's own Lever 2 (*"what a tap does inside one
frame... the acknowledgement"*) and this lever both ask for.

**A real bug found underneath it, fixed rather than deferred.**
`updateBar()`'s hand-diff rewrote `el.className` wholesale on every card
redraw. Verified: holding a synthetic press across a live redraw (a new card
arriving mid-press) **silently cleared `.pressed`** before the fix. Replaced
with `classList.add/remove/toggle`, which touches only the tokens that
function owns. Re-verified: `.pressed` now survives 2+ seconds of live
redraws.

**Driven verification (not read off the source):**

| check | result |
|---|---|
| `pointerdown` on a card → `.pressed` present | same call stack, **0ms** |
| computed `background`/`border`/`transform` while held | `rgb(78,66,31)` / `rgb(239,230,205)` / `translateY(1.73px)` (= 1.5×1.15) |
| `pointerup` → `.pressed` cleared | yes, `transitionDuration` on the rest rule: **0.13s** |
| `#recentre`, `#tuneBtn` same cycle | pressed→released cleanly, background/colour swap confirmed |
| `.pressed` survives a live card-hand redraw (post-fix) | yes, 2.5s held, confirmed by screenshot |

### 4. Detail at close range — no pass needed, and the lever doesn't apply uniformly here

**The board.** A 1:1 crop of a quiet jungle region (400×400 at DPR2, both
sizes) shows real two-scale structure — coarse crown blobs, fine bright tips,
sub-cell aggregate, litter in openings — sd of luminance **58** over a nominal
"flat" region; nowhere close to a flat fill. This is the correction passes'
own work (the `h2` hash fix, the crown-sizing fix) and this pass didn't touch
terrain generation, so it carries over unchanged. Verified fresh at both
sizes rather than assumed.

**The bar is a deliberate exception, not a gap.** The card's own Placement
rule reads *"growth may go anywhere on the BOARD and nowhere in the BAR"* —
the bar's flat gauge tracks and card backgrounds are order asserting itself,
which is the direction, not an underbuilt surface. Texturing them would be
the generic fix (levers.md's own warning: *"a lever whose fix would look the
same under any direction was fixed generically"*) applied against an explicit
card refusal. **No change; the lever's own text says record it as absent
where the medium (here, the card) genuinely doesn't offer it.**

### 5. Focal punch — no pass needed

Squint test, both sizes: the full-page screenshot box-downsampled to a
~25×55-block thumbnail (a heavy averaging blur) at 390×844 and 320×568. In
both, the bright lane is the unambiguous single winner — the only element
above L\*~80 in the frame — with the dark bar staying quiet beneath it rather
than competing. Nothing else in the coarse view registers as a second focus;
no furniture (labels, panel titles, the minimap) reads louder than the road.
**Already at a clean 1-winner reading at both sizes; no change.**

### 6. The one unreasonable moment — changed

**Reading, before.** The signature — *the road opening, growth peeling back
off a pushed lane* — happens and is measured to happen (`FINDINGS`), but the
moment ground actually changes hands renders at the same ceiling it settles
into: `scar[i]` is exactly 1.0 at creation and the wash it drives never
exceeds `alpha = scar * cw * 0.44`. The instant was exactly as quiet as the
18s of history it leaves behind — the punctuation was missing, which is
exactly what the entry line named (*"the moment your world grows or closes"*
is the card's own stated unit of payoff, and it had no reflex of its own).

**Change.** One additive `fillRect` in the same draw call, same colour
(`rgba(232,220,192,…)`, the scar's own), derived entirely from `scar[i]`'s
existing value — **no new array, no new timer, `updateClaim()` untouched.**
`scar[]` decays linearly over `SCAR_S` (18s), so `(scv-0.95)/0.05` isolates
the newest **0.9s** of that decay from the scalar that already exists, and
squaring it front-loads the spike the way an actual impact decays rather than
a linear fade. The window is 0.9s rather than the card's own cited *"~0.4s"*
picture-lags-truth figure, and that departure is deliberate and stated:
`drawTerrainSlice()` repaints only `1/REBUILD_SLICES` of the board per frame
— a full sweep costs ~470ms at 60fps by this project's own measurement, more
under load — so a flash shorter than that would go unpainted for a cell whose
redraw slice had just had its turn. 0.9s outlives one full sweep with margin.

**Driven verification.** Snapshotting the terrain buffer before and
immediately after forcing a hard front-line push (`S.front[1] += 0.2`,
`advance(0.02)`), restricted to cells that were already within the surveyed
shoulder (not raw jungle converting to lane, which swamps the comparison with
an unrelated, much larger delta): a cell measured **rgb(101,112,117) →
rgb(199,199,188)** at the instant of the flip — a **+98 delta in red alone**,
far past what the base 0.44-ceiling wash alone produces there (arithmetic
check: at `cw≈1`, base-only alpha is 0.44; with the flash, effective combined
opacity is `1-(1-0.44)(1-0.9) ≈ 0.94` — more than double the coverage at the
peak instant). The same location settled back to its pre-push value once the
front relaxed, confirming the addition doesn't linger past its own decay.

**Removal test.** Take it out: the moment a push crosses the seam goes back
to a wash creeping in under a ceiling it never breaks — noticeably tamer, not
merely less decorated. It was the moment, not decoration.

**One signature, not two.** This is the card's own Signature line, pushed
further at the exact instant it already names, in the exact colour and
mechanism the card already specifies. Nothing new was introduced for the
board to mean.

---

## The ledger

| LEVER | what changed, before → after, with a number | card line served | cost | what else it moved |
|---|---|---|---|---|
| 3 (+2) | Every button: 0 press feedback → `.pressed` in the same call stack, `1.5×1.15px` displacement, ivory `#efe6cd` (reused from `S.tapAck`), 130ms eased release | Lever 2, *"what a tap does inside one frame... the acknowledgement"*; F4/F6 unaffected (no radius, no glow) | Found & fixed a real bug: `updateBar()`'s `el.className=` overwrite was wiping `.pressed` mid-press; replaced with `classList` ops | Dead-block reading: `-` (re-measured, unaffected — buttons are DOM, terrain is canvas). Frame cost: `-` (no measurable change; press-state CSS costs nothing per frame) |
| 6 | Scar-flip flash: peak effective opacity `0.44 → ~0.94` for 0.9s, decaying back into the unchanged 18s curve | Signature, *"the moment your world grows or closes"*; Materials (same scar colour, no new one) | None found — additive draw call only fires on an actual sign-flip, measured no frame-cost change at rest | Frame cost at rest: `-` (measured 4.73ms post-change vs 5.67ms pre-change at 390×844 — both readings are within this project's own documented run-to-run noise band, not attributed to this line) |

**Floor repairs** (own section per `/hone`'s rule — not lever changes, not
subject to the transplant test, form is *restore the exempted text's own
size*, never *shrink the primary content*):

| what | before → after | why |
|---|---|---|
| `.pfoot` (jungle glyph key) | scaled by `--bx` (72.5px tall @320) → held at original size | was pushing the 6 required camp rows into a scroll; wording untouched |
| `.cnote` (hand status caption) | scaled by `--bx` → held at original size | same squeeze on the 3 required card slots; wording untouched |

### Spread check

Every dimension this pass deliberately touched **widened**, none narrowed:

- **Button state count**: rest/sel/mod/empty → + pressed (a new, distinguishable
  state added, not merged into an existing one).
- **Button state contrast**: 0 (no press feedback existed) → a measured
  background/border/displacement delta on press, decaying to 0 — the *range*
  of what a button can look like across its lifecycle grew from 2 states worth
  of contrast to 3.
- **Scar opacity range**: `0 → 0.44` (flat ceiling) → `0 → ~0.94 → 0.44 → 0`
  (a new, higher peak, same floor). Strictly wider.

No dimension this pass touched came out narrower. (The dead-block percentage
*did* move against the artifact — see "What the resize cost" — but that is
the captain's own build decision's side effect, not a hone-lever change, and
is reported in its own section rather than folded into this check.)

---

## Re-confrontation

Driven again after the changes, not read off the ledger's intentions, at both
sizes:

- **Attachment.** Board tap and every bar button now acknowledge in the same
  frame, driven via real `PointerEvent`s — see lever 1/3 tables above.
- **Sweep.** Every touchable DOM element enumerated: 3 card slots, `#tuneBtn`,
  `#recentre`, `#cSkip`, tuner steppers, `#closeTune` — rest/press/release now
  distinguishable on all of them without a side-by-side (press is a visible
  colour+displacement change on every one, confirmed by direct computed-style
  reads, not eyeballed).
- **Crop.** Re-run post-change at both sizes: still sd 58 on a nominal jungle
  quiet region; the bar's flat fields are unchanged, which is correct per the
  card's own Placement rule (lever 4 above).
- **Squint.** Re-run post-change at both sizes: the lane is still the sole
  winner; the new button press states and the scar flash are both far too
  local and far too brief to register in a blurred coarse view, which is
  correct — they are for the hand and for the moment, not for the silhouette.
- **Spread.** See above — nothing narrowed.
- **Ledger.** Both changes carry a number, a card line, and a filled fifth
  column; the two floor repairs are in their own section, not mixed into the
  lever rows.
- **Card, against the artifact.** F1/F2/F4/F6 re-run and passing (pre-flight
  section above); F3/F5 untouched by this pass, not re-probed. Signature
  confirmed still the same signature, pushed further, not a second one.
- **Name test, twice.** Before: nameable — order cut through wild, one bright
  seam. After: still nameable, and the seam's own moment of change is now the
  thing that pops hardest in real-time play rather than something you have to
  already know to look for. Harder to name it did not become.

---

## Handover

**What it does to the eyes.** The instant a push actually crosses the seam is
now the loudest thing in the frame for about 0.9 seconds — roughly double the
opacity of the wash it used to arrive at directly — before settling into the
same 18-second scar it always left behind. Nothing else in the board's value
hierarchy moved; the lane is still the single squint-test winner at both
sizes, the jungle crop still shows the same two-scale texture it did before
this pass touched anything.

**What it does to the hands.** Every button that could be tapped now answers
inside the same frame the finger lands — a 1.15×-scaled 1.5px drop and the
board's own tap-ivory, gone in 130ms on release — where before there was
nothing between finger-down and the result arriving. The command bar itself
is 15% larger at every content dimension the captain's decision touches
(card targets 44→50.6px, all four panels' text and gauges scaled to match),
with two pieces of secondary caption text deliberately held at their old size
so the six camp rows and three card slots — the actual decision surface —
never lose visibility to it.

**What's owed and still open, named rather than silently passed:**

- **Real-device frame measurement — still not met.** CPU-throttled
  approximation only (below), explicitly not a phone. `/hone`'s own
  prerequisite from the readiness report is not closed by this pass.
- **The pre-existing hand-panel caption overflow** at 320×568 (~31px, present
  in HEAD before this pass touched anything) — named, not fixed, out of scope
  for both the two build decisions and the six levers.
- **The `hold`-command overshoot** — named under lever 2, not fixed, same
  reasoning: rare input, real regression risk, low payoff at this pass's
  scope.
- **The command bar's own zoom cost** (dead-block margin at 390×844 down from
  2.4% to 9.5–11.9%, still passing 14.3%) — the captain's decision's own cost,
  adjudicated and left alone rather than chased into the fragile terrain
  constants.

---

## On-device frame measurement — approximated, not met

Both `FINDINGS-overgrowth.md` and `COMMITMENT-overgrowth.md`'s Budget
amendment (A4) flag the same open prerequisite: every frame number on record
is desktop, uncontended, no throttling. No phone was available to this pass
either. Rather than let that pass silently or invent an on-device number,
Chrome's CPU-throttling emulation (`chrome-devtools-axi emulate --cpu N`) was
used as a **labelled approximation** — the same technique Lighthouse's mobile
preset uses, not a substitute for the real thing, and stated as such
everywhere it's cited.

| condition | 390×844 | 320×568 |
|---|---|---|
| unthrottled (this pass's own build) | 5.67 ms | 6.11 ms |
| **4× CPU throttle** (Lighthouse's mid-tier-mobile figure) | **24.56 ms** | **16.82 ms** |
| 6× CPU throttle | 32.60 ms | — |

The 4× figure is what earlier passes only extrapolated (*"a mid-range phone's
single-thread JS is commonly 3–5× slower, which would put this at roughly
20–33 ms"*) — this pass's own unthrottled reading times 4 lands at 22.7–24.4
ms, matching the empirical 4×-throttle number closely, which is the first
time that extrapolation has been checked against anything rather than stated
on its own authority. **This is still a 12-thread desktop CPU running slower,
not a phone's actual silicon, thermal envelope, or GPU path — the ceiling
(16.7ms) is missed at 390×844 under the approximation and borderline at
320×568, and that is exactly the risk the unmet prerequisite names.**
`REBUILD_SLICES` and `CELL` remain the recorded, cheap levers if a real
device measurement confirms the risk. **Say unverified, not "fine" — the
prerequisite from the readiness report remains formally unmet after this
pass; this section bounds the risk, it does not close it.**
