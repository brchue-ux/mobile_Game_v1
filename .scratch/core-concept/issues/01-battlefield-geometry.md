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
