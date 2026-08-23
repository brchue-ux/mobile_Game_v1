# Gold and items — the in-match economy

Type: grilling
Status: open — **substantially answered 2026-08-19/21.** Gold and hero items
are now separate channels: gold funds creep/unit upgrades, buyback, and the
neutral merchant; hero power comes only from jungle-item drops and cards/chosen
skills. Item granularity is WC3-style complete random drops, unwanted items may
be sold for gold, and items never affect the map. The flat-vs-tiered item fork
and the existing inventory/attention/visibility holds remain open.
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

- ~~**Gold, drops, or both?**~~ **ANSWERED 2026-08-19/21: both, with separate
  jobs.** The original description mixes two systems: gold *earned* from
  creeps and jungle, and items that *drop* from creeps. Warcraft 3 had both — a
  shop you spend at and neutrals that drop items. Which is this, or is it both?
  ~~Unresolved, and deliberately not guessed.~~ Gold funds creep/unit upgrades,
  buyback, and merchant stock; hero-power items drop from jungle creeps. See the
  dated rebuild below.
- **How many item slots**, and whether they can be swapped once filled.
- **Whether pickup costs attention.** The hero is automated (15). If the player
  must notice and collect a drop under a running clock, that is a new input
  channel competing with casting; if the hero auto-collects, items stop being a
  decision.
- **Whether items snowball.** Gold from winning fights buys power that wins more
  fights. Real-time games punish this hard. Interacts with 05's comeback
  dynamics and 11.
- **Whether the opponent can see your items.** Interacts with 10.

### LOCKED — all power is match-bound (2026-07-21)

> *"if power can change on heroes at all from weapons or stats, it will come from
> in game cards or match bound power ups. try to steer away from pay2win gacha
> mechanics."*

`[committed]` Hero power variance comes **only** from in-match cards and in-match
power-ups. Nothing persistent, nothing purchased, no gacha. Extends the existing
fairness constraint from cards to heroes and items.

**Consequence for this ticket:** itemization may tier *inside* a match; it may
never carry power *between* matches. Whatever this ticket decides about drops,
gold and slots, all of it resets at the final whistle.

### Flat vs. tiered itemization — the fork this ticket must resolve

Raised in the 2026-07-21 heroes dump, and it decides whether heroes differ
laterally or vertically:

> *"Does the great sword only exist and it only ever is five and a dagger is three
> in terms of attack power? It's the only one there ever is but the attack speed
> is 1.8 times as fast or 2.2 times as fast so you trade more attacks for less
> damage per attack. Can you find a greatsword with six? Can you find a greatsword
> with seven? Can you upgrade it to be that?"*

**Flat** — one greatsword at 5, one dagger at 3, differentiated by attack-speed
trades. Keeps every difference asymmetric, stays clean against the fairness
constraint, and makes items an identity choice rather than a power climb.

**Tiered** — greatswords at 5, 6, 7, findable or upgradeable. Creates in-match
power progression, which is the snowball risk already flagged below, and makes
matches decidable early. Permitted by the match-bound rule, but not made safe
by it.

The user's framing: *"These are all points that have to be answered at one point
in time, which affects how heroes will differ in power."* Constrains 15.

### Complexity note

This is the single largest complexity cost in the 2026-07-21 material: a
currency, a drop system, a slot inventory, and a shop or pickup interaction — all
under a real-time clock, on a phone. Flagged for 18, not argued here.

Interacts: 15, 12, 05, 11, 10, 18.

## Rebuild — 2026-08-19 through 2026-08-21

### ✅ Gold and hero items are separate channels `[provisional]`

The ticket's old **gold, drops, or both?** question closes as **both, with
different jobs**:

- **Gold buys no hero power.** It funds **creep/unit upgrades** — weapons,
  armor, and unit-type changes such as a mage variant — plus **buyback** and the
  **neutral merchant**.
- **Hero power comes only from jungle-item drops and cards/chosen skills.** It
  never comes from gold, directly or through the merchant.

This corrects the prior 05 line that gold bought similar power-ups at the main
base. It is a **reversal of that recorded line**, not a silent narrowing. The
flat-vs-tiered fork below remains live, but now applies **only to items**; the
proposed gold/item tier split is moot, not adopted.

### ✅ Gold sink 1 — creep/unit upgrades only, never hero power

Gold pays for upgrades to automated units: **weapons, armor, and changes of unit
type** (the captain's example was *"a mage or something like that"*). “Only” is
about the upgrade target: **creeps/units, never the hero**. No balance value or
upgrade magnitude is chosen here.

### ✅ Gold sink 2 — buyback, priced as a real deterrent

Buyback is paid in gold. Its structural intent is that repeated reckless hero
deaths must be expensive enough to deter them — not a casual toll — while still
allowing the *"I really need my hero back"* choice. **The exact price is parked**
and no number is selected.

### ✅ Gold sink 3 — the contestable neutral merchant

The merchant is in the **horizontal middle**, equally contestable, while ticket
12 records the captain's more specific **lean** away from dead-center-mid toward
a multi-lane confluence. That siting remains a lean, not a lock.

Its confirmed stock and clock:

- **Gold-bought terrain effects** — the structural hurt-their-lane channel.
- **A mercenary/neutral unit**, bought at the merchant, then **tap-to-place only
  in your own currently-owned lane space** under ticket 12's interpolated
  boundary field.
- **One copy of each offering per restock**, shared and contested: if the
  opponent buys the copy first, it is unavailable until the next restock.
- A **periodic restock on its own clock**, deliberately separate from the event
  telegraph's cadence. The captain reconsidered the earlier same-clock example
  in the same session. **The exact offset and all cooldown lengths remain
  parked.**

This constrained, stock-limited site is the allowed exception to the rejected
idea of spending gold freely anywhere to affect the map. Its scarcity bounds
the snowball channel: more gold does not create more copies.

### ✅ Item drops are random, fully made items

Item granularity is **WC3-style**: creeps drop **random complete items**, not
League-style components that the player assembles. This closes
`mg-item-granularity`.

### ✅ Unwanted items may be sold for gold

If a random item does not fit the chosen hero — for example, a caster/melee
mismatch against the eight-hero selection — the player may **sell it for gold**.
This is the backstop for random complete drops, not a component-crafting loop.

### ⚠ Map-affecting crafted items were proposed, then REVERSED

The first 2026-08-21 reaction floated a rare second item tier: earn an
*"expendable token"* plus something else in-match and combine them into one
unique, player-chosen, map-affecting item. **The next dump reverses it outright:**
*"No map affecting items"* and *"no crafted item that affects map."*

**Operative rule:** items never affect the map — no random drop, no crafted
tier, no exception. Map effects keep their existing two-channel split:
**cards** act momentarily, and the **merchant** sells structural, gold-bought
terrain effects. The proposed crafted tier is recorded only here as a
same-session proposal-and-reversal; it is not added to the live design.

### ✅ Merchant mercenary logistics are resolved

The earlier gap — a merchant that is not dead-center cannot simply imply where a
bought unit appears — closes as: **buy at the merchant, tap to place, and only
inside your own currently-owned lane space.** Ticket 12 owns the boundary field
that defines that legal space.

### ✅ No merchant hero-debuff channel

The captain reframed the brainstorm candidate from hero-targeted to
**lane-targeted**, then chose **no new merchant SKU** for it: the existing
hurt-their-lane channels already cover the job — cards momentarily and
gold-bought merchant terrain effects structurally. This closes
`mg-gold-merchant-stock-brainstorm-decision-merchant-hero-debuff-channel`.

**Gold and the merchant never weaken a hero directly.** Ticket 15 holds the
complete final hero-weakening rule, including the later reopening of item
debuffs and terrain debuffs.

## Still open after the 2026-08-21 rebuild

- **Flat versus tiered itemization** remains wholly open and applies only to
  items, not to a gold/item split.
- **Item-slot swap/discard**, **item pickup attention**, and **item/inventory
  visibility** remain exactly as open as before.
- The merchant's exact restock offset/cooldowns, buyback price, upgrade values,
  item stats, drop rates, and every other balance number remain parked.
- Merchant siting remains a confluence-spine **lean** with *"I guess"* preserved;
  ticket 12 keeps the W2-dead-zone and mid-region-lopsidedness holds open.

**No longer open:** gold-versus-items as competing sources of hero power; item
drop granularity; the merchant mercenary's placement; the merchant hero-debuff
channel; and whether merchant stock contains anything beyond terrain effects.
