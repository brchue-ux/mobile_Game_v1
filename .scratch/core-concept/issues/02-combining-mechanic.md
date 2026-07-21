# What "combining cards" actually means

Type: grilling
Status: resolved
Blocked by: —

## Question

When a player combines cards into a single compound spell, what is the
mechanical operation?

This is the keystone of the whole design. The user's stated win condition is
"understanding how to use your cards in combination" — so if combining is
shallow, the game has no core.

Candidate shapes surfaced during charting, none chosen:

- **Payload + modifiers.** One card is the spell body; others modify it
  (+damage, splits into three, applies slow). Readable, scales without number
  inflation, degrades gracefully — you can cast the payload bare when the clock
  is tight.
- **Elemental recipes.** Cards carry elements; pairs produce named results from a
  lookup table. Highly discoverable and collection-friendly, but authoring cost
  grows with the square of the pool and it's opaque until memorized.
- **Shape/positional composition.** Cards define the attack's geometry — area,
  arc, pierce, duration — rather than its stats. Ties tightly to aiming and the
  gesture; harder to read at a glance on a phone.
- **Free additive stacking.** Everything sums. Trivial, but there's no "aha,"
  which undercuts the premise.

Things the answer must also settle:

- How many cards can go into one cast? Is there a cap, and what enforces it?
- Is combining reversible mid-composition, or committed as you go?
- Do failed/nonsense combinations exist, and what happens when you try one?
- Does the compound spell's identity need to be *legible to the opponent* — the
  user wants players reading each other's fields.

Blocks 03 (gesture), 04 (pressure vs. complexity), 06 (unlock progression).

## Answer

**At-cast combining is payload + modifiers.** One card is the spell body; others
modify it. `[provisional]`

**Why, and what it cost:** the three candidates were traced forward through 03,
04 and 06 before choosing. The trace found that 03 (gesture-as-skill) and 04
(learning curve) pull in opposite directions — gesture wants shape-composition,
the learning curve wants payload+modifier. The user resolved it as a values
call: **accessibility beats novelty when they conflict.** `[committed]`

**Shape-composition is dead, and the reason matters:** it only ever earned its
cost if the gesture *drew* the spell's geometry. The user then ruled that
gestures are flicks, drags and aims — *not* drawn symbols ("no one's gonna want
to play that for more than two seconds"). That removes C's entire justification
while leaving all of its costs. `[committed]`

**Elemental recipes rejected:** worst fit for the learning curve (no meaningful
"cast it bare"), and authoring cost grows with the square of the card pool.

### This ticket was mis-scoped — the rest is now split out

02 was written as one decision but was functionally the whole card system. Only
the at-cast model is settled here. Spun out as their own tickets:

- **09** — banking as a second, vertical axis (combining over time)
- **10** — information: what you see of the opponent's hand
- **11** — card accrual economy and whether the rate is influenceable
- **12** — the jungle's mechanical role and how autonomous it is

### Deliberately still open within at-cast combining

The model is chosen; its parameters are not. Ticket **13** (prototype) exists to
surface these concretely rather than settle them on paper:

- Cap on modifiers per cast, and what enforces it
- Whether composition is reversible mid-build or committed as you go
- Whether nonsense combinations exist and what happens when you attempt one
- How legible a compound spell is to the opponent

### Noted for later, not decided

Four candidate merge outcomes were surfaced (jungle plays, higher-tier cards,
transmutation, ultimate charge). The user wants all four eventually. Assessment:
mechanically compatible, but each is a subsystem, and shipping four at once
means teaching four things under a running clock — the exact trade the
accessibility call refuses. Recommend one for the vertical slice, the rest as
expansion space. Ticket 09 owns this.

## Amendment — 2026-07-21: recipes, scoped

**This narrows a `[committed]` decision. Recorded explicitly rather than
absorbed, per the map's rule on re-litigation.**

Elemental recipes were rejected above on two grounds: authoring cost growing with
the square of the pool, and opacity until memorized. The user has amended this:

> *"I know that we talked about accessibility in not having 50 recipes but a
> small amount of recipes that are very basic in terms of how many 'ingredients'
> there are, along with tutorials. That shouldn't be that difficult to grasp."*

**What is amended:** a *small, fixed* set of recipes — 3–4, each with few
ingredients, taught explicitly — is now in scope. `[provisional]`

**What is unchanged and still committed:** a large combinatorial recipe table is
still rejected, and for the original reasons. Both stated grounds survive the
amendment at small N — 4 recipes cost almost nothing to author, and 4 recipes
with a tutorial are not opaque. The rejection was always about scale; this makes
that explicit rather than reversing it.

**What it is for:** the recipes are the proposed home for **transmutation**,
which this ticket had ruled out. The user's construction is that a preset
combination makes the hero take an action in the jungle that changes map state —
so transmutation returns not as "two cards become a third card," but as "certain
combinations produce a *map effect* via the hero." That is a materially different
mechanic wearing the same name. See 09 and 12.

**Watch item for 04 and 16:** the recipes must stay legible from the card face.
If a player has to memorize which cards share a "common denominator" (16), recipe
memorization has re-entered through the side door and this amendment has
overreached. Accessibility beats novelty remains `[committed]`.

