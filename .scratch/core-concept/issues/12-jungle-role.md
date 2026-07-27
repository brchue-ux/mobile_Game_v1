# The jungle — role and autonomy

Type: grilling
Status: open
Blocked by: 01

## Question

What is the jungle for, and how much happens there without the player?

Split out of 02. The user is explicit that the game should affect *"not just the
lanes but the jungle area"* — and equally explicit that its autonomy is
unresolved: *"see how autonomous that will be versus not."*

A locked constraint from charting is that the jungle must be **mechanically
live, not scenery**. This ticket decides what that means.

The answer must settle:

- **What the jungle contains.** Neutral camps? Objectives? Terrain that can be
  altered? Nothing but space to route through?
- **Autonomy.** Does the jungle run itself — camps spawning, neutrals fighting,
  objectives ticking — or does it only ever do what a player makes it do? A
  fully autonomous jungle adds a third thing to watch, which pressures 04.
- **How a player interacts with it**, given they command no hero and no direct
  units. Spells? Merged banks (09's leading candidate)? Deployables?
- **Whether jungle control feeds the lanes** or is a parallel win condition
  (interacts with 05).
- **Screen budget.** The jungle competes with three lanes for a phone screen.
  01 sets that budget; this ticket spends it.

Strong candidate carried from 09: **lanes take cast spells (tempo), the jungle
takes merged banks (investment).** That would give both mechanics a distinct
home. Not decided — evaluate it here against alternatives.

### Update — 2026-07-21

The dump answered the autonomy question from an unexpected direction, and **not**
with the candidate above.

**The hero works the jungle, automatically.** `[provisional]` *"That hero is also
going to interact with the jungle but it will be automated."* So the jungle is
not player-operated and not self-running — it is operated by an autonomous unit
that belongs to the player. That is a third answer the ticket had not considered.

**A second live candidate for player influence:** 3–4 preset card combinations
that cause the hero to take a jungle action affecting map state. *"There are
three or four preset combinations or cards that can be used where then your hero
takes an action in the jungle that affects map state."* This is the user's
proposed home for transmutation — see the amendment on 02 and the rewrite of 09.

**The jungle also produces gold** (17), giving it a second mechanical job.

Now interacting: 15 (the hero doing the work), 17 (gold), 09 (what cards do to
the jungle). This ticket got substantially more constrained without being closed.

### Update — 2026-07-26: the jungle is playable space, and it is not a wall

Answered while working 01. `[provisional]`

- **Spells can go into the jungle.** It is a legitimate target class — the core
  loop names in-jungle effects alongside in-lane ones. This answers "how a player
  interacts with it" without needing 09's banking.
- **It is not a wall between lanes** — *"the hero would need to be able to go
  through them."* Lane-to-lane traversal through jungle is required. **This rule
  became load-bearing later the same day:** terrain manipulation can *"block off
  the ability for the hero to go to another lane"* (a giant tree root), which is
  a play worth making **only because passage is the default**. Traversal-by-default
  is now the baseline that terrain effects are priced against, not just a
  movement rule. See [05](05-match-shape-win-condition.md).
- **Lane creeps stay out of it, with an exception:** *"creeps from the lane won't
  go there unless they happen to be pulled there via aggro but then they would
  snap back once aggro is lost."* **First appearance of aggro in this design** —
  creeps have a threat model and a leash. That is a genuine new system, small but
  real, and 18 should know about it.
- **Forest and jungle otherwise behave like a typical MOBA**, minus fog of war
  (see [10](10-information-visibility.md)).

**Screen budget — reframed, not spent.** This ticket said "01 sets the budget;
this ticket spends it." With a pannable camera, 01's budget is no longer a fixed
allowance: the map exceeds the screen and the player navigates it. The jungle no
longer has to win space away from three lanes. **Where the jungle physically
sits on the board is still open** — the 2026-07-26 dump's "top two-thirds" line
is recorded in 01 as being about the map viewport, and flagged for confirmation.
