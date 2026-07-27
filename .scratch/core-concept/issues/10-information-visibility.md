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
speed-mine vs. hit-their-lane.

### What the panel shows about their hero — answered 2026-07-26 `[provisional]`

> *"their current power status / their level / what skills they've chosen / their
> goal / their current income / how strong they're getting"*

Six readouts. Three observations worth keeping:

- **"Their goal" is the aggressive one.** That is enemy *intent*, not enemy
  state — the panel would be telling you what they are trying to do. Nothing
  else in this design gives away intent, and it is the single largest concession
  of hidden information made so far. Note it also implies the AI/hero behaviour
  system has a legible, nameable current objective (see 15's route modes).
- **"How strong they're getting" is a rate, not a snapshot.** It implies a trend
  readout — a derivative — which is a different and harder UI object than a
  number, and it needs a window ("since when?").
- **"What skills they've chosen"** presumes heroes pick skills during a match.
  That is not recorded anywhere in 15 and is effectively new.

### Hand visibility — answered 2026-07-26 `[provisional]`

Asked whether the drift toward fully-open information was intended:

> *"you won't know what cards they have. Maybe you can't know how they are able
> to manipulate the field."*

**The hand is hidden.** That is the deliberate reserve, and it settles the
ticket's first bullet.

**A second hidden element arrived with it:** *how* an opponent can manipulate the
field — i.e. their terrain-effect capability (see [05](05-match-shape-win-condition.md))
is concealed, not just the cards themselves. Hedged with *"maybe"*, so
`[provisional]` and weakly held, but note what it buys: terrain manipulation is
slow and accrued, so hiding the *capability* is what stops a telegraphed
build-up from being fully readable in advance. Without it, accrual would announce
itself.

### Net position — the design is not fully open

**Open:** the whole board (no fog), enemy hero position, and six readouts on
enemy hero state including *"their goal"*, which is intent.

**Hidden:** the hand, and probably the opponent's field-manipulation capability.

**So the original axis lands off-centre, not at either pole.** Everything about
the *battlefield* is calculable; everything about the *opponent's options* is
not. That is a coherent split — you can always see what is happening, never quite
what is coming — and it is worth stating as the ticket's answer rather than
leaving it implied. The earlier concern that this was drifting to fully-open by
accumulation is resolved: it was not intended, and the hand is the reserve.

**Still open:** whether hand visibility is total darkness or partial (card
*count* but not identity, payload but not modifiers — the ticket's original
framing), and whether PvE mirrors it or the AI plays open-handed.

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
