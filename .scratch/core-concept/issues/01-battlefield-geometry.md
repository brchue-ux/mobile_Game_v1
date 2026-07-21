# Battlefield geometry & phone readability

Type: prototype
Status: open
Blocked by: —

## Question

How much of a Dota-shaped map fits legibly on a phone screen, and what does
terrain actually *do*?

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
