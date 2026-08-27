# Card accrual economy

Type: grilling
Status: open
Blocked by: 02

## Question

Do cards arrive at a fixed rate for everyone, or can the rate be influenced?

Split out of 02. Cards accrue on a timer — that is locked. What is *not* settled
is whether that timer is a constant or a variable players can act on.

The answer must settle:

- **Fixed or influenceable in-match.** Can a card, a jungle play, or a map
  objective speed up your draw rate? An influenceable rate creates a second
  economy to play against; a fixed rate keeps the game legible and symmetrical.
- **Whether both players always draw at the same rate**, or whether tempo
  advantage can compound. Compounding rates snowball hard in real-time games
  (see 05, comeback dynamics).
- **What happens with a full hand.** Do cards stop arriving, overflow, or
  auto-bank? Interacts with 09.
- **Whether accrual is the right pressure valve** for 04's learning-curve
  problem — a slower rate is a gentler game.

### The tension this ticket must not resolve by drift

The user asked whether **out-of-match, passive things** could affect accrual
rate. If they can, that is **power progression**, and it collides head-on with a
locked constraint: all cards obtainable, nothing purchase-exclusive, no
pay-to-win. A buyable or grindable draw-rate advantage voids that constraint
however it is dressed up.

This must be decided deliberately. If out-of-match progression touches accrual,
say so explicitly and revisit the fairness constraint in the map's Notes — do
not let it arrive sideways. Interacts with 06 and 07.

## Amendment — 2026-08-26: Shape A forces the deck to shrink `[provisional]`

**Standing caveat, in his own words (2026-08-27):** *"yes to both, but its
written in pencil not stone."* `[provisional]`, not `[committed]`.

The card system's shape is decided as a **composite**, and the arm this ticket
sits closest to — **lane-state cards** — runs on **Shape A (Cycle)**: a small
deck, a small hand, deterministic rotation, spent cards returning in a fixed
order. Combining is priced as **cycle cost**. See
[02](02-combining-mechanic.md) for the price and the other two arms.

### ⚠ REVERSAL — deck size shrinks to ~8–12, from ~20 `[provisional]`

**Recorded as a reversal, per the append-only rule, not absorbed.** The standing
figure was **~100 cards, bring ~20** (2026-07-21, `[provisional]`, recorded in
the map and in [16](16-deckbuilding.md)). **The ~20 figure is reversed.**

**The deck must shrink to roughly 8–12 cards** — Clash Royale (8) and Stormbound
(12) scale.

**Why this is a mechanism constraint and not a balance number:** Shape A's entire
depth device is the rotation. A ~20-card deck in a ~15-minute real-time match
with timer accrual is a **pool**, not a deck — you draw a large fraction of it
once and very little of it twice, so it never cycles, and if it never cycles
there is no rotation to do arithmetic on and **no cycle cost to price combining
with.** *Small enough to cycle, or it is not Shape A.* **Where exactly the line
sits inside 8–12 is balance; that there is a line is not.**

**What is NOT reversed:** the **~100-card pool** stands, unchanged. So does
**every card in your deck being available within the match**, and **all cards
obtainable, nothing purchase-exclusive**. See [16](16-deckbuilding.md), which
owns the number — it is recorded there and here as the same figure, deliberately,
and must stay consistent between them.

### 🆕 Hand size gains a second job under Shape A `[provisional]`

Hand size was set aside in the 2026-08-11 reset as one of the specifics. Under
Shape A it is no longer only **04's pressure valve**. It is the dial on **how
much of the player's own future rotation is visible.**

A bigger hand exposes more of the rotation, which **raises the planning ceiling
and lowers the pressure at the same time** — the two move together, so the
number cannot be set from pressure alone any more. **The number itself stays
parked**; what is decided is what it controls.

### Still open, and unchanged by this

- **What happens when the hand is full** — cap-and-leak, overflow, or auto-bank.
  Still a **structural fork, not a tuning question**, and it interacts with
  [09](09-banking-mechanic.md), which is **untouched and still shelved.**
- **Whether the accrual rate is influenceable in-match**, and the out-of-match
  progression tension recorded above. **Nothing here touches either**; the
  accrual timer itself is unchanged by the composite.
- **⚠ Parked, not answered:** Claimed Grammar's **affinity charge** (see
  [02](02-combining-mechanic.md), [12](12-jungle-role.md)) is a second,
  slow-regenerating accrual-shaped meter sitting beside this ticket's timer.
  Whether that means banking returns or the design knowingly runs two such
  systems is **explicitly parked pending
  `mg-card-system-brainstorm-decision-banking-return`.**
