# Commitment card — the "convey the whole" prototype

Written **before** anything was made, per `/verve` step 4. Not reverse-engineered.
Audited against the artifact at the finish gate — findings in
[`FINDINGS-overgrowth.md`](FINDINGS-overgrowth.md).

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

## What is NOT mine to decide, and is not decided here

Per the brief and the concept doc: the power threshold, the economy's numbers,
and the card system. The match has **no terminal state** and that absence is
accepted by the captain, not an oversight — the clock runs out and says so.
