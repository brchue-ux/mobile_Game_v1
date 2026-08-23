# Battlefield geometry & phone readability

Type: prototype
Status: open — **⚠ updated 2026-08-12/13 by his play-test of the prototype.**
**The camera comes IN** — *"a little more zoomed in"*, targeting *"closer to the
max zoom out of typical MOBAs, but maybe slightly more just because it's a mobile
game"* — which brings with it **the design's first requirement that texture and
material be legible**. **The command bar is larger**, with the principle recorded
rather than a number: **the bar gets the fixed real estate and the board absorbs
the variation, because the board pans and the bar cannot.** **The bar must not be
a numeric HUD** — *"way too much information and it was all about numbers"* —
which is **the existing decision-substrate constraint being enforced, not a new
preference.**
Blocked by: —

## Question

How much of a Dota-shaped map fits legibly on a phone screen, and what does
terrain actually *do*?

## The camera — answered 2026-07-21

The first concrete statement about what this game *looks like*. `[provisional]`

> *"I envision there being a first-person view of your UX and then just beyond
> that view would not be an eagle-eye view of the battlefield but a slightly
> angled eagle-eye view of the battlefield. You would see the lanes and you could
> see your hero down there going through either a purposeful path to attack creeps
> and farm or a randomized one. Events would be happening inside of the jungle."*

Established:

- **A first-person UX layer in the foreground**, with the battlefield beyond it.
- **A slightly angled overhead view — explicitly not straight-down eagle-eye.**
  The angle is stated as deliberate.
- **The hero is visible on the field**, pathing either purposefully (farming
  creeps) or randomly.
- **The jungle runs visible events.** Not a backdrop.

**The player is a commander looking at a battlefield, not an avatar in it.** This
is what forced the loss-condition reversal in 15 — worth holding onto, because
the camera turned out to determine the win condition.

**What the angle costs.** A tilted view compresses distance toward the horizon:
the far lane is smaller and harder to read than the near one, and asymmetric
legibility in a symmetric game is a competitive problem. Prototype before
committing.

**Still unanswered here:** how much of the map is visible at once, whether it
scrolls, and how a player learns a lane is collapsing off-screen.

### Orientation & first layout sketch — 2026-07-21

**Orientation is portrait, 1080×2400.** `[provisional]` This is the one firm
decision from the session; everything else below is a rough first pass.

Artifact: `Misc Help/PENUP_20260721_175017.png` — a **super-rough hand sketch**,
described as such by the user. What it shows: three lanes running top-to-bottom,
a midline across the centre, a base at each end, "Hero Cam" picture-in-picture
panels in two corners, and the card hand as a semi-transparent shadow overlay on
the player's half.

**What the sketch does and does not establish — read before building on it.**
It is a napkin, not a spec. Over-reading it once already produced a wrong
conclusion this session (see below).

- **Establishes:** portrait orientation; a rough sense of where the player wants
  major elements to sit; that the user is thinking about hero visibility (the
  Hero Cams) and about saving screen space (cards as an overlay, which is a genX
  idea worth keeping).
- **Does NOT establish:** lane shape, jungle placement, or that the jungle is
  excluded. The user was explicit: *"this is just a super rough hand drawing. i
  am not excluding jungle based on it at all. it still needs to be further
  fleshed out."* The jungle being absent from the sketch means nothing.

**Retracted over-read.** The agent initially read the sketch as evidence that
portrait forces bare Clash-Royale-style vertical tracks and squeezes the jungle
out — treating a rough drawing as a considered layout. That was the same error
this project already carries a scar for (13: rough artifacts can't answer
questions they weren't built to answer). Retracted. The portrait-vs-Dota-shape
tension is real and worth examining, but this sketch is not evidence for it.

**Genuinely open, carried forward for the fleshing-out pass:**

- The user's stated instinct that the top and bottom of the map feel *"a bit
  long"* — worth taking seriously as an early legibility signal, not as a
  measurement.
- Whether the Hero Cam is the right way to show an autonomous jungle hero, or
  whether the hero should be visible in the jungle directly. Interacts with 12
  and 15.
- Where the jungle physically lives on a portrait board.
- How much of the opponent's side you see — which is **10's** whole question,
  arriving here through the camera. See the 01/10 note below.

### 01 and 10 have partly merged

"How much of the opponent do you see" is 10's core question, and the camera
decides it more directly than any card-visibility rule. 10 was written about hand
and bank visibility; the spatial half of it now lives here. Keep both, but design
them together.

The map is committed to bending lanes with forest/jungle between them, not bare
vertical tracks. That commitment has consequences this ticket has to pay for:

- **Readability.** How much of the board can a player see at once? Whole map
  fixed, or a scrolling/zooming camera? If it scrolls, how does a player know a
  lane is collapsing off-screen?
- **Terrain semantics.** Does terrain block spells, redirect them, provide cover,
  break line of sight — or is it visual texture with no mechanical weight? A
  forest that does nothing is cheaper but weakens the case for not being Clash
  Royale.
- **Off-lane space.** Is the jungle playable — somewhere creeps or spells can go
  — or is it a wall between lanes?
- **Target granularity** — **class answered 2026-07-26, resolution still open.**
  You target your hero, your lane, their lane, their hero, or the jungle. What
  that does *not* say is the resolution **within** one: a whole lane? A point
  inside one? A region, an arc, a specific creep clump? The pannable no-fog
  camera makes a point-target technically available — you can see and touch any
  part of the map — so this is a free choice, not a constraint.

Prototype the board at real phone dimensions before deciding. A sketch at desktop
scale will lie about legibility.

Constrains creep design. (Formerly blocked 03, now closed — see
[03](03-gesture-skill.md).)

## The observer camera — answered 2026-07-26

> *"This one's point is to be able to somehow view all of your lanes. I guess
> you're going to need to be able to touch the screen and pan or scroll the map.
> You'll have it almost like you're an observer in a MOBA. Imagine it that way:
> you're an observer and you use your finger to pan around the map but you don't
> get to control your hero directly."*

**The camera is a pannable MOBA observer.** `[provisional]` The map is larger
than the screen; you drag to move around it. This reframes the ticket's opening
question — "how much of a Dota-shaped map fits legibly on a phone" — from a
*fitting* problem into a *navigation* problem, which is a materially easier
problem and the first real answer this ticket has had.

**Consequences worth holding:**

- **The angled view's legibility cost is defused.** A tilted camera compresses
  the far lane, and asymmetric legibility in a symmetric game was flagged as a
  competitive problem. If you can pan to the far lane, the asymmetry stops being
  structural. The user considers the angle settled: *"on the angled cast we've
  discussed that."* It does not fully vanish — the lane you are *not* looking at
  is the one that surprises you — which is what the alerting question below is
  for.
- **The observer framing completes the commander identity.** You pan like a
  spectator and cannot drive your hero. Consistent with the camera decision that
  reversed the loss condition on 2026-07-21.
- **The portrait-vs-Dota-shape tension is largely dissolved**, not resolved. A
  bending three-lane map with real jungle no longer has to fit in 1080×2400 at
  once. Recorded as a genuine open tension in the map since 2026-07-21; panning
  is what closes it.

### Screen split & the control panel `[provisional]`

> *"I kind of envision you have the panable map at the top and then your control
> thing. You have some sort of screen that describes both heroes and gives
> actions or something like that. That's just a rough thought right now. I don't
> know."*

**Confirmed 2026-07-26 — the reference is Warcraft 3, zoomed out.**

> *"The top portion of the map is the top portion of your screen, like the top
> 75%. That is the map that you play on, that you pan around and build on...
> The very bottom of the screen would have action commands, a portrait of a hero,
> and your selectable army. That is a rough idea of how I imagine the screen
> being split."*

- **Top ~75% is the map viewport** — pannable, the thing you actually play on.
  This is a **screen split, not a board layout**: the earlier "top two-thirds"
  line was about the viewport, and the jungle's physical position on the
  battlefield remains open. Ambiguity resolved.
- **Bottom ~25% is a command bar**, in the shape of an RTS one.
- **What's in it, in this game:** *"that's where the card stuff is going to be
  and then you would have a sort of insight into how their hero is doing."*
- **⚠ Read the WC3 analogy carefully.** It names *"your selectable army"* — that
  is a description of **Warcraft 3's** bottom bar, supplied as a visual
  reference for the split and the kind of furniture that lives there. It is
  **not** a proposal for commandable units, and it does not touch the locked
  constraint that players influence lanes but do not directly command an army.
  Filed because a cold read of that quote could easily mistake it for one.
- The panel **describes both heroes.** Both — required by no fog and by cards
  that target the enemy hero.
- **Flagged as rough by the user** (*"I can't even picture one right now"*). Not
  to be built on hard.

**The panel has a stated job, and it is not decoration.** `[provisional]`

> *"you would have a sort of insight into how their hero is doing. That way you
> can better make decisions on whether you should use your cards to attempt to
> slow their hero down, speed your hero up, or attack their lanes. The user needs
> to be able to get information like that. That makes the information on the
> cards relevant to the state of battle."*

The bottom bar exists to make card decisions **informed** — it is the decision
substrate, not a HUD. This is the first stated purpose any UI element in this
design has had, and it sets an acceptance test: *if a player cannot tell from the
bottom 25% whether slowing their hero beats attacking their lane right now, the
panel has failed.* See the design principle it produced, in the map.
- **Not reconciled with the napkin sketch**, which had Hero Cam picture-in-picture
  panels in two corners and cards as a semi-transparent overlay. This is the
  newer statement; the sketch is not retired. The Hero-Cam-vs-see-the-hero-directly
  question is arguably answered by panning — you can just look at him.

### Off-screen lane collapse — direction, not decision

> *"I guess it would just be typical, right, a notification or you'd have a mini
> map that would have a ping on it or something like that. Figure that out in
> terms of what the control part of the screen looks like at the bottom."*

Panning creates this problem — the price of not seeing everything at once — and
the answer is deferred into the control-panel design. Candidates on the table: a
notification, or a **minimap with pings**. Note a minimap competes for the same
bottom quarter as the hand and the hero actions.

### Terrain, jungle and fog — answered 2026-07-26

**Forest and jungle behave like a typical MOBA, with one deliberate exception:
there is no fog of war.** `[provisional]`

> *"I think the forests and the jungle will operate just like a typical MOBA
> does, except that there won't be any fog because we need to see their hero to
> be able to choose what we're going to do to negatively affect it if that's what
> the user chooses to do."*

This is **forced by the targeting model** — casting is selection, and you cannot
select what you cannot see. A card that slows their hero requires their hero to
be on screen and pickable. It also settles the spatial half of [10](10-information-visibility.md).

**Off-lane space** `[provisional]`:

- **Spells can go into the jungle.** It is playable space.
- **Lane creeps do not enter the jungle** — *unless pulled there by aggro, and
  they snap back once aggro is lost.* First appearance of aggro in this design.
- **It is not a wall between lanes**, because the hero has to move through it.

### Correction — terrain's job did not shrink

The agent proposed that removing skill shots reduced terrain to texture and left
bending lanes unpaid-for. **Wrong, and corrected by the user:** *"you're
referencing the skill shots of the user from the cards as opposed to what the
heroes or the creeps might do."* Terrain and lane shape are paid for by hero and
creep movement, pathing, sightlines and combat. The card change touched player
targeting only. The "blocks/redirects spells" question survives for hero and
creep abilities, not for card targeting.

## The command bar's layout — answered 2026-08-11

**The bottom quarter is divided into three panels.** `[provisional]` This is the
first concrete layout this ticket has carried for the bottom 25%, and it arrives
against a bottom quarter that already had four claimants competing for it.

- **Left: the cards.**
- **Middle, wider than either side individually: a "screen" showing your hero
  and the enemy hero, displaying their progress and power.**
- **Right: undecided.** His own framing: *"something tactical that controls one
  of the game's other levers?"*

### Why the middle panel is load-bearing

The loss condition is **the enemy hero reaching a power threshold**, and his
framing of the whole game is **preventing your opponent from maximising that
power journey while maximising your own**. A central readout of both heroes'
progress is therefore **the scoreboard of the actual win condition** — not a
status readout, and not a HUD. It is the UI the power threshold has needed since
it was proposed, and **it arrives before the threshold's own specifics**, which
remain parked by his own scope instruction (see
[05](05-match-shape-win-condition.md)).

This is the same job the 2026-07-26 acceptance test already set for the bottom
bar — the bar exists to make decisions **informed** — now pointed at the win
condition rather than only at card choice.

### The right panel — candidates, none chosen

Recorded as candidates drawn from the design's other levers. **None is chosen,
and the list is not a shortlist.**

- **The jungle pre-commitment readout** from 12's second dump — roughly **six
  camps**, each showing **difficulty, how long it would take, damage and mana
  cost, expected gold and possible items**. See
  [12](12-jungle-role.md).
- **The event panel** — the telegraph countdown, the event's known type, the
  imbue commitment, and whatever placement influence turns out to be.
- **The gold conversion site** — spending gold on power-ups at the main base,
  where the push arm turns into hero power.
- **A minimap**, which is on record as showing both heroes at all times —
  **though this is information rather than a lever**, and so does not answer the
  question as he framed it.

**A firstmate observation, offered and not decided:** the two arms of the central
axis are pushing lanes and farming the jungle; cards are the lane arm, so a
jungle readout on the right would make the bar **lane arm, the race between
them, jungle arm**. **Not his, not adopted.**

### Panel swapping — accepted

> *"If another lever is required, but no space, need an option to toggle/swap it
> visible when needed."*

**The bar is not required to be three fixed panels.** When a lever needs a
surface and the bar has no room, **a toggle or swap that brings it up on demand
is the accepted mechanism.** `[provisional]`

Recorded as a **general principle for the command bar**, **not** a decision about
which lever holds the fixed right slot — that remains undecided above. It bears
directly on the standing bottom-25% competition (the cards, both heroes, the
leash readout, off-screen lane alerts, a reinforcement count), because it means
the competition does not have to be settled by permanent allocation.

### The centre screen's direction — DELEGATED, not open

> *"Based on what the agent feels works better, have them choose the direction
> for the centre screen. I remember my rationale for both, but things have
> diverged since."*

**He has explicitly handed this decision to whoever builds it**, on the grounds
that his own reasoning for each option predates changes that may have
invalidated it. **This is a delegation, not an unresolved captain decision** — it
should not be filed as one or brought back to him.

**Whoever chooses must record the choice and the reason** here, so the design
keeps a rationale rather than a fait accompli.

**The two framings, both his, both preserved:**

- **2026-08-07** — the command bar should be **centred on a display of the enemy
  hero's status, not a paired readout beside your own**. Its reason: it is *the
  thing you watch to make gameplay choices*, and likely the same UI that tracks
  progress toward the goal. Recorded in [05](05-match-shape-win-condition.md).
- **2026-08-11** — the middle panel shows **your hero and the enemy hero**, their
  progress and power.

**⚠ The tension is stated and deliberately not resolved.** It may be a refinement
rather than a reversal — the 2026-08-07 objection was to a paired readout
**beside your own**, and a single central screen carrying both is a different
arrangement — **but it is close enough to the rejected shape that it is not
smoothed over here.** It is **not** flagged as a reversal, because he has not
said it is one.

**What has diverged since 2026-08-07 — material for the chooser, explicitly not
a steer:**

- The loss condition became **the enemy hero reaching a power threshold**, and
  his framing of the whole game became a **race** between two power journeys.
  **A race has two runners.**
- **Map control became economic rather than informational**, so the panel's job
  is less about watching for danger and more about reading the race.
- **The leash arrived**, which ties reachable ground to lane state and **may
  itself want a readout in the same bar.**
- **A minimap showing both heroes at all times is already on record**, which
  already covers *where is the enemy hero* and **may leave the centre screen's
  job as progress rather than position.**

### Standing cautions — set aside for this pass

The user, explicitly: *"your standing cautions, no let's just ignore those for
now."* The napkin-sketch caution and the prototype-at-real-dimensions rule were
waived for this round of thinking. **Waived, not repealed** — both still apply
before anything here is promoted to `[committed]`.

## Play-test — 2026-08-12 / 2026-08-13: the camera comes in, the bar grows, and the bar stops being numeric

> **⚠ Source note.** His reactions to the playable prototype in
> `.scratch/core-concept/prototypes/` — the **shipped build** on 2026-08-12 and
> the **corrected build** on 2026-08-13, both played on an S26 Ultra. **Quoted
> passages are his own wording as captured**; unquoted material is
> record-paraphrase. The prototype's own artifacts —
> [`COMMITMENT-overgrowth.md`](../prototypes/COMMITMENT-overgrowth.md) and its
> `## Amendments`, and
> [`FINDINGS-overgrowth.md`](../prototypes/FINDINGS-overgrowth.md) — are
> **cited, never imported.**

### ✅ The camera comes IN `[provisional]`

> *"The space where you're viewing the map needs to be a little more zoomed in.
> So that way when you're getting to watch your hero, you actually get a good
> view of it, and a good view with spells, and a good view with the creeps, and a
> good view of the actual textures of the game. Right now it's a little too top
> down far away."*

**His target, in his own words, with his own hedge attached:**

> *"closer to the max zoom out of typical MOBAs, but maybe slightly more just
> because it's a mobile game. I'm not totally sure there."*

**So: roughly a MOBA's maximum zoom-out, permitted to be a little wider for a
phone.** This does not disturb the pannable-observer camera (2026-07-26) — **the
map still exceeds the screen and you still drag around it.** What changes is how
much of it a screenful holds.

### 🆕 The consequence — TEXTURE AND MATERIAL MUST BE LEGIBLE

**This is the substantive part of the zoom change, and it is a first for this
design.** Every prior statement about the board has been about **shape** — lane
routing, jungle placement, what fits. His list of what he wants a good view of
ends with *"the actual textures of the game"*, which is **the first requirement
anywhere in the design for texture and material to read.**

**What it obliges:** **the ground, the units and the canopy all need a surface
rather than a fill.** At a closer camera a flat fill reads as a flat fill, so
material becomes something the board has to render rather than something it can
imply.

**⚠ It is not free, and the prototype paid for it deliberately.** The build's own
frame budget was **exceeded** by this change and its commitment card was
**amended with measurements rather than allowed to drift** — see
[`COMMITMENT-overgrowth.md`](../prototypes/COMMITMENT-overgrowth.md)'s
`## Amendments`, **A4 (Budget)**, and the measurements in
[`FINDINGS-overgrowth.md`](../prototypes/FINDINGS-overgrowth.md). **Cited, not
restated here, and not a concept decision** — but recorded because **a
legibility requirement that costs frame time is a real constraint on this
ticket**, and because the number a phone actually produces is **still not
measured on a phone.**

### ✅ The command bar is LARGER — and the principle outlives the number

**He asked for bigger without giving a number**, on 2026-08-12:

> *"I feel like the bottom screen needs to be a little bigger... I have an S26
> Ultra and it feels a tad small."*

**The principle, which is what this ticket should carry forward** `[provisional]`:

> **The bar gets the fixed real estate and the board absorbs the variation,
> because the board pans and the bar cannot.**

**Why:** the board has a **pannable camera**, so it absorbs any change in screen
size for free — a shorter board just means a little more panning. **The bar has
no such slack.** Everything in it sits at a **fixed position a thumb has to
reach**: card targets, the shared readouts, whatever holds the right panel. **So
the bar is sized from its contents and the board takes what is left** — the
opposite of the usual instinct, which is to protect the board and squeeze the
bar.

**⚠ No proportion is recorded here as his.** He gave none. The corrected build
**derived roughly a third of screen height from its contents** and he has not
reacted to it; **that is the build's derivation, cited and not adopted.** The
recorded **~75 / ~25 split (2026-07-26) is `[provisional]`** and is **the thing
his "a tad small" bears on** — **no new split is decided here.**

**✅ DECIDED 2026-08-22 — he gave the number.** *"15% bigger than its current
built size"*, closing the one `/hone` prerequisite the captain needed to give
a figure for (the readiness report's own naming of it). `[provisional]` like
every number here — the principle above is what outlives it, and the previous
paragraphs stand as the record of what preceded the number. Built as one
scale factor over every content dimension in the bar — height 32%→36.8% of
screen, floor 226→260px, ceiling 312→359px, the 44px card-target floor itself
to 50.6px — with the bar's own 1px rules held fixed (a hairline is a Materials
property, not a proportion, so 1.15px would have read as sloppy rather than
bigger). **What it cost, stated rather than hidden:** the board absorbs the
growth per the principle above, so the camera's zoom `s` drops **~7%**
(1.148→1.067 at 390×844), which measurably thins the margin on the round-2
dead-block gate — 2.4%→9.5–11.9% at 390×844, 1.2%→11.9% at 320×568, **both
still inside the 14.3% threshold**. Two floor repairs were forced by the same
squeeze (the jungle glyph key and the hand panel's status caption both held
at their pre-scale size so the six camp rows and three card slots stay
visible at 320 wide, per the card's own Floor). Full record:
`prototypes/HONE-overgrowth.md`.

### ⚠ The bar must NOT be a numeric HUD — an existing constraint being ENFORCED

> *"While the lower panel with all the information was good, there was way too
> much information and it was all about numbers and moving numbers. It needs to
> be a lot more intuitive."*

**Recorded as the existing constraint being enforced, not as a new preference.**
This ticket already states — since 2026-07-26 — that the bottom bar is the
**decision substrate, not a HUD**, and that cards must be **judgeable against
visible battle state**. **A panel of moving counters is a HUD.** The acceptance
test written here in July is the same test this feedback failed.

**What it asks for, and it is a design constraint rather than a styling one:**
**cost and worth should be carried by size, weight, shape, fill and position** —
read at a glance rather than computed. **The power track's *gap* is the model**:
it shows a **distance between two things** rather than two figures, so the state
is felt.

**A firstmate observation, offered and not decided:** the **densest numeric
object in the design is one he asked for himself** — the jungle **pre-commitment
readout** from [12](12-jungle-role.md), carrying difficulty, time, damage, mana,
gold and possible items **per camp** across roughly six camps. **That is dozens
of numbers by construction.** The fix implied is **not to drop the information
but to express it**, which raises the price of that readout without changing what
he asked for. **Not his, not adopted.**

### Recorded here because they land on this ticket's surfaces

- **The leash needs no rendering of its own on the board** (2026-08-13, from
  [05](05-match-shape-win-condition.md)) — its boundary **is** the lane's front
  line, which is visible by definition, and a second drawn territorial system is
  what made the leash and the home field indistinguishable. **⚠ This does NOT
  retire the leash readout as a claimant on the bottom 25%**, which is this
  ticket's question and is **untouched**. **Do not extend that cascade.**
- **The home field is expressed as a boundary marked in the lane**, not a drawn
  volume — *"just some sort of visual indicator maybe in the lane that tells you
  the line in the sand"*. **A second territorial mark on this ticket's board**,
  and the only one now drawn.
- **Hero control is a tap on the map, validated by play** (*"the tap to move is
  actually really good"*), and **intent is one tap attack-move / two taps move
  only** (2026-08-13, from [12](12-jungle-role.md)). **The viewport this ticket
  owns is now an input surface with two intents on it**, and **how a spam
  sequence resolves is open** — see 12. **✅ DECIDED 2026-08-22, see 12** — the
  run-latch scheme is accepted as-is, for now.

### Open after the play-test

- **The camera's actual zoom level.** *"Closer to the max zoom out of typical
  MOBAs, but maybe slightly more"*, with his own hedge — *"I'm not totally sure
  there"* — attached. **A direction, not a figure.**
- ~~**The command bar's proportion.**~~ **✅ DECIDED 2026-08-22** — see
  "The command bar is LARGER" above: 15% bigger than the round-2 built size,
  his own number.
- **How the bar carries cost and worth without numbers**, especially for the
  **jungle pre-commitment readout**, which is numeric by construction and is
  **his own request.**
- **What "texture and material legible" costs on a phone** — **still not measured
  on a phone**, only in a desktop browser. The standing rule that **prototypes
  must be observed running** and the finish gate's own note both bear on this.
- **The leash readout in the bottom 25%** — **still live.** The board needs no
  drawn leash; **the bar's claimant is a separate question and is untouched.**
