# Pre-match setup & the pre-game state

Type: grilling
Status: open
Blocked by: —

## Question

What happens between opening the app and the match starting?

New — raised 2026-07-21: *"you'll also need to make a note about the pre-game
state and the setup that takes place prior to actually going into a match."*

Until now the map covered only the real-time match. There is a pre-match layer,
and it carries at least two real decisions — hero choice and deck construction —
both made before matchmaking.

### Established by the 2026-07-21 dump

- **Hero is chosen before searching for a match.** *"before you would search for
  a match, you would choose a hero."* `[provisional]` See 15.
- **Deck is chosen before the match** — 20 from ~100. `[provisional]` See 16.
- **Item slots are NOT filled pre-game.** *"I don't want them to be filled
  pre-game."* Items are an in-match economy. `[committed by explicit rejection]`
  See 17.

### The answer must settle

- **The order and shape of the flow.** Hero then deck, deck then hero, or both
  on one screen?
- **Whether deck is constrained by hero.** If a hero restricts legal cards, the
  two choices stop being independent and deckbuilding gets much heavier.
- **Whether you see the opponent's hero before the match.** A pick/counter-pick
  layer is a whole genre of decision. Interacts with 10 (information).
- **Whether any of it is skippable.** Presets and recommended decks are the
  standard answer for new players. Interacts with 04 and 06.
- **How long this layer takes.** Every second here is dead time before the
  real-time game starts, on a phone, possibly on a commute.

Interacts: 15, 16, 17, 10, 06, 04.
