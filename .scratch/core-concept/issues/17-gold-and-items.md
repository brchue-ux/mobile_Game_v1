# Gold and items — the in-match economy

Type: grilling
Status: open
Blocked by: 15

## Question

How do items enter a match, and what do they do?

New — raised 2026-07-21.

The user's words:

> *"your hero could have item slots and maybe those item slots are filled in
> game. I don't want them to be filled pre-game. Let's have them filled in game,
> similar to how Warcraft 3 and Dota would be, where once you get gold from
> creeps or gold from the jungle then you can pick up items that drop from the
> creeps or whatever."*

### Established

- **Items fill hero item slots.** Interacts with 15. `[provisional]`
- **Slots are filled in-match, never pre-game.** `[committed by explicit
  rejection]` — *"I don't want them to be filled pre-game."* This is a stated
  rejection and is append-only: do not reintroduce pre-game itemization without
  flagging it as a reversal.
- **Gold comes from creeps and from the jungle.** `[provisional]` This gives the
  jungle a second reason to be mechanically live, alongside 12.
- **WC3/Dota lineage** is the stated reference point.

### The answer must settle

- **Gold, drops, or both?** The description mixes two systems: gold *earned* from
  creeps and jungle, and items that *drop* from creeps. Warcraft 3 had both — a
  shop you spend at and neutrals that drop items. Which is this, or is it both?
  Unresolved, and deliberately not guessed.
- **How many item slots**, and whether they can be swapped once filled.
- **Whether pickup costs attention.** The hero is automated (15). If the player
  must notice and collect a drop under a running clock, that is a new input
  channel competing with casting; if the hero auto-collects, items stop being a
  decision.
- **Whether items snowball.** Gold from winning fights buys power that wins more
  fights. Real-time games punish this hard. Interacts with 05's comeback
  dynamics and 11.
- **Whether the opponent can see your items.** Interacts with 10.

### Complexity note

This is the single largest complexity cost in the 2026-07-21 material: a
currency, a drop system, a slot inventory, and a shop or pickup interaction — all
under a real-time clock, on a phone. Flagged for 18, not argued here.

Interacts: 15, 12, 05, 11, 10, 18.
