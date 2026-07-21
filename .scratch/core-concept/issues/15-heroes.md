# Heroes — stats, roles, and the loss condition

Type: grilling
Status: open
Blocked by: —

## Question

What is a hero, and what does it do during a match?

New — raised 2026-07-21. The largest single addition to the design since
charting, and it reaches into the win condition, the jungle, and the economy.

The user's words:

> *"before you would search for a match, you would choose a hero. Imagine there
> are eight heroes and these heroes all have different strengths and weaknesses.
> We have different amounts of armor, health, and mana and that hero is the thing
> that causes you to lose the game when it dies. That hero is also going to
> interact with the jungle but it will be automated."*

### Established by that statement

- **~8 heroes**, differentiated by strengths and weaknesses. `[provisional]`
- **Stats: armor, health, mana.** The first numeric stat block in the design.
  `[provisional]`
- **Hero death is the loss condition.** `[provisional]` This answers a large part
  of 05, which had been open with no candidate.
- **The hero acts in the jungle automatically.** The player does not drive it.
  `[provisional]` This is a concrete answer to 12's autonomy question — and it is
  *not* the candidate 12 was carrying.

Also floated, owned elsewhere: hero abilities working in tandem with card
combinations, and 3–4 preset combinations that make the hero take a jungle
action affecting map state. That mechanism belongs to 09 and 12; this ticket
owns the hero itself.

### The answer must settle

- **What differentiates heroes beyond stat spreads.** Abilities? Jungle
  behaviour? If the only difference is armor/health/mana numbers, eight heroes
  is eight difficulty settings, not eight identities.
- **What mana is for.** Cards accrue on a timer and cost no mana. A second
  resource needs a job, or it is a stat with no verb attached. Interacts with 11.
- **Where the hero physically is.** Three lanes plus a jungle on a phone screen
  is already tight (01). A hero that wanders adds a fourth thing to track.
- **Whether the player can influence the hero at all.** "Automated" is a spectrum
  from fully autonomous to steerable-with-a-flick.
- **What killing a hero actually requires.** Creeps? Spells? Both? This is the
  win condition's real mechanism, and 05 cannot close without it.
- **Whether hero choice is a power decision or an expression decision.** If
  heroes differ in power, hero unlocks collide with the locked fairness
  constraint. Interacts with 06 and 07.

Interacts: 05, 12, 11, 01, 14, 06.
