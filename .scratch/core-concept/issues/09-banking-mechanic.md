# Banking — combining over time

Type: grilling
Status: shelved
Blocked by: 02

## Question

What is banking *for*?

Rewritten 2026-07-21. The original framing — "banked cards merge into something
better, TFT-style" — has been substantially dismantled by the user, and the
ticket now asks a harder question than it did.

### What survives

**The shape is still good, and this is why the ticket is still alive.** The
moment-to-moment decision is a **binary made repeatedly under pressure** — bank
or cast. Near-zero cognitive load per instance, real depth in aggregate. That fits
the accessibility priority from 02 better than anything else surfaced.

**The framing the user endorsed:** *"playing your cards now for immediate
board-state effect versus holding them for a future strategic purpose."* Tempo
versus investment. That axis is the thing worth keeping.

**Weak positive signal from 13:** the bank visual was the one thing the user
singled out as landing. `[provisional]` — weak evidence, but the only positive the
prototype produced.

### What the 2026-07-21 dump removed

- **Higher-tier merging is dead.** `[provisional]` Superseded by deckbuilding
  (16): *"instead of higher-tier cards being used, maybe every single card can be
  available in an individual match."* If every card is available, an in-match
  power ladder has nothing to climb.
- **Ultimate-charge is not banking's payoff.** *"Maybe banking won't be for an
  ultimate. I do like the ultimate idea."* The ultimate survives as a wanted
  feature; it is no longer this mechanic's answer. Parked in the map's fog.
- **Transmutation has moved out of banking.** It now lives as 3–4 preset recipes
  that make the hero act in the jungle (see 02's amendment, 12, 15).

That leaves banking with a good shape and **no payoff attached** — which is
precisely the open question.

### SHELVED — 2026-07-21

The garbled sentence resolved to **shelve it**:

> *"I'm looking for the word. I think that there is a possibility there. I'm not
> really sure how to implement it. It could just be some extra clutter that,
> after everything else, isn't necessary so just shelve it for now. If we ever
> think of a way to make it reasonable or good then we can come back to it."*

**This is a shelving, not a rejection.** The distinction matters for the
append-only rule: banking has not been ruled out on its merits, and the user
explicitly left the door open. Do not treat it as a locked "no," and do not
reintroduce it unprompted either.

**The condition for return:** a use for banking that is clearly worth its screen
space and teaching cost. The shape was never the problem — bank-or-cast as a
repeated low-load binary is still the best-fitting idea this design has produced
for the accessibility constraint. What it lacks is a payoff, and every candidate
payoff either died (higher-tier), moved elsewhere (transmutation → hero/jungle
recipes), or was declined for this job (the ultimate).

**The user's own reason for shelving is the sharpest argument in the ticket:**
*"extra clutter that, after everything else, isn't necessary."* After everything
else — heroes, items, gold, deckbuilding, recipes — banking is a system competing
for a budget that 18 says is already oversubscribed. That is a sequencing call,
and it is the right one.

The four candidate uses below are preserved for whenever it comes back.

### ⚠ A fifth candidate may have arrived on its own — 2026-07-26

**Unresolved, and it needs the user, not an inference.** While answering 05 on
objectives, the user described **terrain manipulation** — creating water, lava or
holes to impede enemy creeps and heroes — and said it would be powered by:

> *"You get cards or a crew, like stored benefits, that can allow you to affect
> the terrain."*

**"a crew" is very likely "accrue."** The dumps arrive by voice, and *"you get
cards, or accrue, like stored benefits"* is both grammatical and exactly what the
sentence needs to mean. **Stored benefits accumulated over time and spent on a
board-changing effect is banking**, described from scratch by the user who
shelved it five days earlier without naming it.

**Why this would satisfy the condition for return.** The condition above is *"a
use for banking that is clearly worth its screen space and teaching cost"* —
banking's problem was never its shape, it was the missing payoff. Terrain
manipulation is a payoff with the right properties:

- **Expensive and board-changing**, so it wants a build-up. A tempo card does not
  reshape a map; an investment might.
- **Naturally the "investment" pole** of the tempo-vs-investment split this
  ticket was built around — and it is a *better* fit than any of the four
  candidates below, none of which changed the board.
- **Compatible with everything decided since**: it needs no skill shots, it gives
  the pannable camera something to look at, and it makes terrain mechanically
  live, which is a standing constraint.

**Not unshelved, and deliberately so.** The rule is not to reintroduce banking
unprompted. The user raised the shape themselves, which makes it prompted — but
they did not name it, may have meant something else, and the alternate reading
("a crew" = a literal squad) would instead brush the locked constraint that
players do not command an army. **This is a yes/no for the user.**

### Candidate uses, none chosen

The user asked for a novel use case rather than a payoff picked off the original
list. Candidates, for reaction rather than selection:

1. **The bank feeds the hero, not the lanes.** Cast cards go to lanes (tempo);
   banked cards fuel the hero's automated jungle actions (investment). This is
   12's original "lanes take spells, jungle takes banks" candidate re-expressed
   with the hero as the intermediary — and it survives all the new material
   intact, which is a point in its favour. It also gives the 3–4 recipes a
   natural trigger.
2. **Banking as a telegraphed threat.** A bank visible to the opponent means
   investing costs *information* as well as tempo — you are announcing what is
   coming. Turns the bank into a bluffing surface and gives 10 something concrete
   to own. The cost stops being purely economic.
3. **Banking as a deferred cast.** A banked card fires later on a trigger — a
   creep wave reaching a point, a timer, a lane collapsing. The most literal
   reading of "future strategic purpose": you are not storing power, you are
   scheduling it. Trap and landmine logic.
4. **Banking as gold conversion.** Banked cards convert to the item economy (17),
   tying two new systems together. Cheap to state, but it makes cards a currency
   and may cheapen them.

Candidates 1 and 2 compose — a bank that feeds the hero *and* is visible costs
tempo and information at once, which is a genuinely interesting price.

### The answer must still settle

- **What banking produces** — the above, or something else entirely.
- **How many cards a bank holds**, and whether there are multiple banks.
- **What the risk is.** The user said *"you risk putting a card in a bank."* Is
  the cost only tempo, or can a bank be lost, stolen, or attacked?
- **Whether banking is visible to the opponent.** Interacts with 10, and
  candidate 2 makes it the whole mechanic.
- **Whether merges are automatic on threshold or player-triggered.**
- **How banking interacts with a 20-card deck** (16) and with accrual (11).
