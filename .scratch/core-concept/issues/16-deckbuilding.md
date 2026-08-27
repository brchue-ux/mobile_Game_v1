# Deckbuilding — 100 cards, bring 20

Type: grilling
Status: open
Blocked by: —

## Question

How is a deck constructed, and what makes two cards combinable?

New — raised 2026-07-21. It also **replaces higher-tier merging** as a candidate
answer to what banking produces (see 09).

The user's words:

> *"instead of higher-tier cards being used, maybe every single card can be
> available in an individual match. It's more like you have a deck of 20 cards or
> something. There are like 100 total cards and you have to pick what 20 cards
> you want to bring but the cards that are able to be combined have to have some
> sort of common denominator across them."*

### Established

- **~100 cards total, ~20 brought per match.** `[provisional]`
- **Every card in your deck is available within the match.** No in-match tier
  ladder, no cards that unlock mid-match. `[provisional]`
- **Combinable cards share a "common denominator."** `[provisional]` This is the
  first real constraint on the payload+modifier model from 02.

### The answer must settle

- **What the common denominator actually is.** This is the ticket's core. A
  faction, a keyword, an element, a stat type, a colour? Whatever it is, it is
  the thing every player must learn in order to combine anything — so it sets
  04's learning curve more directly than any other single decision.
- **Whether it is readable from the card face alone.** If a player has to
  remember which cards share a denominator, that is recipe memorization arriving
  through the side door, which 02 rejected. Accessibility beats novelty.
- **Deck size, and whether duplicates are allowed.**
- **Whether decks are hero-constrained.** Interacts with 14 and 15.
- **How a 20-card deck meets timed accrual.** Is it a shuffled draw pile, or are
  all 20 always eligible? Completely different games. Interacts with 11.
- **Whether construction is a wall for new players.** Interacts with 06, 14.

### Tension this creates with 06

06 assumed a growing card pool was the progression hook. A 100-card pool played
20 at a time changes what unlocking means — and sharpens the fairness problem,
since deck quality now varies with collection size. **06 must be revisited after
this lands.**

Interacts: 02, 09, 11, 06, 14, 15, 04.

## Amendment — 2026-08-26: the pool stays, the deck shrinks `[provisional]`

**Standing caveat, in his own words (2026-08-27):** *"yes to both, but its
written in pencil not stone."* `[provisional]`, not `[committed]`.

The card system is decided as a **composite**, and lane-state cards run on
**Shape A (Cycle)** — a small deck on deterministic rotation, with combining
priced as cycle cost. See [02](02-combining-mechanic.md).

- **The ~100-card pool STANDS**, unchanged. So does *every card in your deck is
  available within the match*, and *combinable cards share a common denominator*.
- **⚠ REVERSAL — the ~20 brought per match becomes ~8–12.** Recorded as a
  reversal of this ticket's own `[provisional]` line above and of the same
  figure in the map, per the append-only rule. **Shape A's depth device only
  exists if the deck actually cycles**; ~20 in a ~15-minute timer-accrual match
  is a **pool, not a deck**. This is a **mechanism** constraint — where inside
  8–12 the line sits is balance.

**The number is recorded identically in [11](11-accrual-economy.md), which
carries the reasoning in full. Keep the two consistent; do not restate the
reasoning here.** This ticket's title still reads *"bring 20"* — **left as
written on purpose**, so the reversal stays visible rather than disappearing into
a rename.

### What this sharpens, and what it does not

- **The common denominator gets harder, not easier.** A deck of 8–12 is a
  **small identity**, so ~100 cards of breadth now have to be expressible in far
  fewer slots — the direct cost of Shape A, and it presses on this ticket's
  flavour-and-customisation job. **Recorded as a cost, not solved.**
- **The card-face legibility watch item stands, and now covers the claim badge
  too** (see [12](12-jungle-role.md)): if a player must **remember** which cards
  share a denominator, or what an active claim does, recipe memorisation has
  re-entered by the side door.
- **Still open and untouched:** what the common denominator actually is,
  duplicates, hero-constrained decks, and whether construction is a wall for new
  players. **06 still needs its revisit** — a smaller deck sharpens the
  collection-size fairness question rather than relieving it.
