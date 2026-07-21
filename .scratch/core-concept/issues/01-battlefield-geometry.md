# Battlefield geometry & phone readability

Type: prototype
Status: open
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
- **Aiming surface.** What is a player's thumb actually pointing at: a lane, a
  point, an arc, a region?

Prototype the board at real phone dimensions before deciding. A sketch at desktop
scale will lie about legibility.

Blocks 03 (gesture) and constrains creep design.
