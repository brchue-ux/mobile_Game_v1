# Commitment card — the "convey the whole" prototype

Written **before** anything was made, per `/verve` step 4. Not reverse-engineered.
Audited against the artifact at the finish gate — findings in
[`FINDINGS-overgrowth.md`](FINDINGS-overgrowth.md).

**The card is live and the direction is unchanged.** Two amendments have been
made to it since it was written, both deliberate and both recorded below rather
than absorbed: the Materials amendment of the original pass, and the **Lever 1 /
F2 amendment of the 2026-08-13 correction pass**. See
[`## Amendments`](#amendments) at the foot of this file. Nothing else has moved.

---

```
COMMITMENT

Compass:    "prototype is less about how it ends right now and how the whole was
            envisioned."  →  convey the whole as envisioned.

Narrowed to: ONE playable match on ONE phone, opened cold. Not the game, not a
            feature tour — the first five minutes in the hand.

Medium:     A real-time touch board in a portrait phone browser. Canvas board in
            the top ~75%, ordered command bar in the bottom ~25%. Read by eyes
            first (board, then bar) and by one thumb (tap, drag-to-pan). No
            sound. Duration: continuous real-time on a ~15-minute match clock,
            of which a cold reader gives maybe five. The world moves on its own
            schedule and is indifferent; the player moves the camera and picks
            destinations.

            Levers (the five channels that actually carry it here):
              1. Territory as a visible field — value across the ground says
                 whose ground this is. The ground, not the units, is the
                 primary information carrier.
                 [AMENDED 2026-08-13, see A2: drawn only inside the lane's
                 surveyed shoulder. The rule still spans the board; the
                 rendering does not.]
              2. Weight and feedback at the fingertip — what a tap does inside
                 one frame; hero acceleration; the acknowledgement.
              3. Motion and timing of the seam — the front line's continuous
                 drift, and the rate at which reach opens and closes.
              4. Scale contrast — board against bar; the 4px creep against the
                 territorial consequence it produces.
              5. Reveal across the match clock — retraction schedule, camps
                 ripening, the event telegraph.

            Unit of payoff: THE MOMENT YOUR WORLD GROWS OR CLOSES. The leash has
            never been felt by anyone. Everything else is in service of it.

Direction:  OVERGROWTH — "something ordered being taken over by something
            irregular and alive."

            For this thing: the lanes are the order — surveyed, ruled, held open
            by fighting. The jungle is the wild, and the wild is not scenery: it
            is what closes over ground nobody holds. The front line is not a
            line, it is the BAND OF GROWTH between two territories, and the
            hero's leash is simply where the cleared ground ends. Push and the
            growth peels back off the road; concede and it rolls over it. The
            home field is your cultivated apron, and it retracts because you
            cannot hold that much ground all match — his "schedule of
            legitimacy", made physical.

            The way in, taken: the order is winning in one lane and losing badly
            in another AT THE SAME TIME. Three lanes are three simultaneous
            states of the same contest, so the board reads as uncertain rather
            than as a finished effect.

Materials:  Wild:      #0b1811 ground, growth mass #16301f, live tips #305e38.
                       Two grain scales — 26px coarse blobs, 7px tips. Generated
                       from a value-noise field, never a painted region.
            Your held: warm bone #d9cfba at full claim → #7d7a6c at the edge,
                       ruled ALONG the lane axis at 1px.
            Their held:cool bone #c3cdd6 → #6c7885, ruled ACROSS the lane axis.
                       (warm/cool is the blue–yellow axis, which red–green
                       colourblindness preserves; the ruling direction is the
                       redundant cue.)
            Scar:      #e8dcc0, ground that changed hands, decaying over 18s.
            Units:     hard chips, dark-cored so they read on bright ground.
                       Heroes are the only things that cast a shadow.
            Bar:       #14120e, strict order, 1px rules, no radius over 2px.

            Placement rule: growth may go anywhere on the BOARD and nowhere in
            the BAR. The bar is the last piece of pure order and does not get
            invaded, decorated, or softened.

Rhythm:     One ratio, 2.0, governs every interval that is mine to choose.
              Growth boundary chases true claim at 0.9 board-units/sec, so the
              picture lags the truth by ~0.4s — alive, not lying.
              Scar decay 18s. Creep wave 11s. Camp respawn 50s.
              Field retraction: 46% of the half-length at 0:00 → 8% at 15:00.
              Event telegraph 60s lead, events at 5:00 and 10:00.
            Fixed anchors, from the record, not invented here: ~15 minute match,
            ~5 minute event cadence.

Budget:     Currency: milliseconds per frame. Ceiling 16.7ms at 60fps on a
            phone; my target is ≤8ms of update+draw so a mid-range phone has
            headroom.
            The committed reading of Overgrowth is a per-pixel generated growth
            field — 2.6M samples/frame at 1080×2400, which is order-100ms/frame
            in JS and CANNOT BE PAID FOR. Decided here, not later:
              - claim computed on a 16-unit grid (~62×125 = 7,750 cells) at 10Hz,
              - growth rendered as cached stamps into an offscreen terrain
                canvas, redrawn incrementally,
              - per-frame animation only on the seam band (typically <600 cells).
            Same growth, far fewer samples. Expected spend ≤6ms/frame at DPR 2.

Signature:  THE ROAD OPENING. When your creeps break the enemy line, the growth
            peels back off the lane ahead of the hero in a wave that outruns the
            front line, surveyed ground writing itself over wild ground, and the
            hero — pressed against nothing visible a second ago — is free to walk
            into it. It leaves a pale scar that fades over 18s, so the board
            carries the history of where the line has been.

Banned:     The three defaults this exact brief and medium would have produced.
            1. "v2 plus more systems" — the existing prototype's dark-slate
               board, cyan-vs-red, thin-stroked dots on lines, #0e1116 rounded
               panels, range-slider tuning drawer, 7-step modal tutorial, with a
               jungle bolted on.
            2. "The MOBA minimap look" — green jungle polygons, tan lane strips,
               blue/red base circles, team-ringed unit discs, a health bar over
               every unit. Every symbol borrowed from the genre this design is
               explicitly trying not to copy.
            3. "The dashboard" — solving 'convey the whole' with readouts: a HUD
               of labelled meters, chips, numbered badges and a six-row camp
               table, until the board is a diagram to be annotated and the
               experience is reading a spreadsheet with a battle behind it.

Forbidden:  Six refusals the obvious version would have leaned on. Each has the
            check that settles it.

            F1. No fence, ring, dashed line or arrow marks the leash. Reach is
                legible ONLY from the ground itself.
                check: `grep -n 'setLineDash' <file>` returns nothing in board
                drawing; no leash-ring draw call exists.
            F2. No static painted terrain. Every order/growth boundary is
                computed from live claim. The jungle is not a polygon; it is
                where nobody's claim reaches.
                [AMENDED 2026-08-13, see A2: the jungle is where no LANE
                reaches — a continuous function of distance to a lane, still
                not a polygon. Inside the shoulder, boundaries are still
                computed from live claim. The check below is unchanged.]
                check: no literal region path/polygon arrays for terrain;
                `grep -n 'jungleRegion\|JUNGLE_POLY\|terrainPath'` empty.
            F3. Nothing is symmetrical in the growth. The two halves are not
                mirrored.
                check: noise seeding has no mirror term (`grep -n 'H - y\|mirror'`
                in the noise/growth path); confirmed by eye at the gate.
            F4. No glow, drop shadow or blur standing in for light or depth. The
                hero's shadow is a drawn occlusion ellipse, not a blur.
                check: `grep -n 'shadowBlur\|box-shadow\|filter:.*blur'` returns
                nothing.
            F5. No health bar over any unit. A unit's state reads from the unit.
                check: no bar geometry inside the unit draw function.
            F6. Nothing in the command bar is irregular — no growth motif, no
                organic shape, no blob, no radius over 2px. The bar is the order
                that is winning outright.
                check: no growth/noise draw call inside the bar's DOM or rect;
                `grep -n 'border-radius' <file>` shows nothing above 2px in bar
                styles.
```

---

## Floor, stated so it can be checked

- **Works:** playable, no runtime errors, real 60fps on a phone.
- **Affordable:** the Budget line above, measured at the gate rather than
  estimated once.
- **Content survives:** the design's spine is legible, the crude things are
  labelled crude on screen, and the placeholder card system stays inside
  `mg-card-placeholder-spec.md`.
- **Hostile condition:** *the first twenty seconds, one-handed, on a 360px-wide
  phone in daylight, by someone who has never seen it.* This is where a
  territory-by-value design washes out and where an unlabelled leash reads as a
  bug. The direction has to hold there.
- **Nobody excluded:** order-vs-wild carried by value (L\* 82 against L\* 8), side
  carried by the blue–yellow axis plus ruling direction, no strobing, no
  information in hue alone.

## Amendments

Amending a commitment card is a deliberate act, not a drift. Each amendment
below states what changed, what forced it, and what was **not** allowed to
change with it.

### A1 — Materials: their ground darkened to slate (original pass)

Their ground was specified as *cool bone* at the same value as yours. At phone
scale warm-vs-cool at equal value was not readable, so their ground was darkened
to slate (L\* ~55 against bone's ~82). The blue–yellow separation and the
ruling-direction cue both survive; **value was added, nothing was removed.**

### A2 — Lever 1 and F2: the order is drawn only where the order reaches (2026-08-13)

**Changed.** Lever 1 read *"Territory as a visible field — value across the
ground says whose ground this is."* F2's prose read *"The jungle is not a
polygon; it is where nobody's claim reaches."*

Both now read: **territory is drawn only inside the lane's surveyed shoulder.**
The claim field is unchanged and still spans the whole board — it is the leash
rule, and it still governs where a hero may go in the jungle — but outside the
shoulder it is **not rendered**. The jungle is where the **lanes** do not reach,
a continuous function of distance to a lane, and the ground there is nobody's
and looks it.

**What forced it.** The captain could not tell the two territorial systems
apart: *"the way that you did the force field was no. I'm not even sure what it
is... I see like these lines. Is that the leash? I don't know."* Two territorial
systems rendered on one board collapsed into one unreadable layer. The agreed
resolution is that **the leash gets no rendering of its own** — its boundary is
the lane's front line, which is visible by definition — which leaves the home
field alone in the territorial channel. The broad claim wash **was** the second
system, and it was also what made the lanes read as too wide.

**What did NOT change with it.**

- **The claim field itself.** `legal()` still reads it across the whole board.
  The leash still gates jungle access, and conceding still closes your own
  jungle toward your base. This is a rendering amendment, not a rule change.
- **F2's runnable check**, which still passes: no region path or polygon array
  exists for terrain; the boundary is computed, not painted.
- **The Direction**, which this arguably serves harder than the original
  reading did — the card already said *"the lanes are the order — surveyed,
  ruled, held open by fighting. The jungle is the wild."* Surveyed ground
  stopping where the survey stops is that sentence taken literally.
- **The unit of payoff.** The moment your world grows or closes is still
  carried, and it now has far more ground to act on: the jungle went from a
  thin strip to 61% of the board.

**What it costs, stated rather than hidden.** In the jungle, the ground no
longer says whose it is. Where your reach ends out there has to be read off the
neighbouring lane's front line and extrapolated. He accepted exactly that trade
— *"I guess that's just up to the player to pay attention to"* — and the build
pays for it on the other side, by never refusing the input and never grinding at
the edge. See F1 below, which is unchanged and still holds.

## What is NOT mine to decide, and is not decided here

Per the brief and the concept doc: the power threshold, the economy's numbers,
and the card system. The match has **no terminal state** and that absence is
accepted by the captain, not an oversight — the clock runs out and says so.
