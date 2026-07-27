# Information — what you see of your opponent

Type: grilling
Status: open — **spatial half answered 2026-07-26**
Blocked by: 02

## Spatial visibility — answered: no fog of war `[provisional]`

> *"the forests and the jungle will operate just like a typical MOBA does, except
> that there won't be any fog because we need to see their hero to be able to
> choose what we're going to do to negatively affect it."*

**You see the whole battlefield, including their hero, at all times** (subject to
panning — see [01](01-battlefield-geometry.md)). Not a preference: it is *forced*
by casting-as-selection, since a card that slows their hero needs their hero
visible and pickable.

**This pushes the ticket hard toward the open end of its own axis.** The question
was framed as running from fully hidden (bluffing, reads) to fully open
(chess-like, pure calculation). Spatially, the answer is now **fully open**.
Whatever hidden information this design keeps has to live in the **hand** — cards
and combinations — because the map holds none.

That sharpens rather than settles the rest: with the board fully visible, hand
visibility is the only remaining lever, so it now carries the entire weight of
whether this game has bluffing in it at all.

**Enemy hero *state* is open too** `[provisional]` — not merely its position.
The bottom command bar is specified to give *"a sort of insight into how their
hero is doing"*, explicitly so the player can judge slow-their-hero vs.
speed-mine vs. hit-their-lane. **What "how their hero is doing" contains is
unspecified** — health, level, gold, items, current behaviour mode, all
plausible, none chosen. That list is this ticket's next real question, because
each entry is a different amount of the opponent's plan given away.

**Net:** everything spatial and everything about the enemy hero is open by
design. The hidden-information budget has been spent down to the hand alone.

## Question

How much of the opponent's hand, bank, and intent is visible?

Split out of 02. From the original premise: *"based on what the other person has
on their field, showing for their cards what they might have."* That sentence
wants partial information, but never says how partial.

The axis runs from fully hidden (bluffing, reads, guesswork) to fully open
(chess-like, pure calculation). The user is unsure and suspects the answer is in
between — *"maybe you should see some and not others."*

The answer must settle:

- **Hand visibility.** Hidden, fully open, or partial — e.g. card *count* but
  not identity, or the payload but not the modifiers stacked on it.
- **Bank visibility.** Arguably more important than hand: a filling bank
  telegraphs a coming investment, which is exactly the tell that makes
  tempo-vs-investment play readable. Interacts with 09.
- **Cast telegraphing.** Between committing a combination and it landing, does
  the opponent see anything? A window to react changes the game profoundly.
  **Reframed 2026-07-26:** with skill shots removed there is no gesture to read,
  so this is purely about whether a *spell in flight* (or a committed target) is
  visible — a property of the spell, not a tell from the caster. Note this is now
  the design's main remaining source of reactive play.
- **How this reads on a phone.** Every piece of visible information is screen
  space competing with three lanes and a jungle. Constrained hard by 01.
- **Whether PvE mirrors PvP here**, or the AI plays open-handed.

Note the accessibility pressure from 02: hidden information raises the skill
ceiling but also the floor — a new player who can't read tells simply loses
without knowing why.
