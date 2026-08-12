# The jungle — role and autonomy

Type: grilling
Status: open — **substantially answered 2026-08-11**, in two dumps of its own.
**Where the jungle sits is answered** (typical MOBA layout, nothing traversable
outside the outer lanes). **Jungle *control* is dissolved rather than answered** —
there is no jungle control in the MOBA sense in a 1v1 with no fog and no allies;
what remains is jungle **access**. **The autonomy ladder is answered rung by
rung**: rung 2 **adopted** with a pre-commitment readout, rung 3 **adopted but
narrowed to a time curve**, rung 4 **open with a shape**, rung 4a **adopted with
an attribution principle**, rung 5 **rejected**. **The chasm is cut *"for now"***
and the two jungle halves connect by ordinary traversal. **Trees are destructible
walls**, so jungle geometry is mutable mid-match. **⚠ The hero-autonomy record is
amended** — a hero is *"not fully autonomous"*, and **control is by tapping the
map**. **Still open:** what the jungle contains (commissioned), jungle symmetry,
and whether invading the opponent's jungle is possible at all.
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

> **⚠ Both open items above are answered 2026-08-11.** **Screen budget is
> confirmed no longer a constraint** — asked directly, *"That's correct."* And
> **where the jungle sits is answered** — see the first dump below.

### Carried in from 05 — recorded here for the first time

**Recorded, not re-derived.** These were decided inside
[05](05-match-shape-win-condition.md) while this ticket was explicitly *not*
rebuilt. They are the standing context every 2026-08-11 answer below sits on.

- **The jungle is one arm of the central strategic axis** `[provisional]`
  (2026-08-11) — *"Are you going to push for map control and earn gold via that...
  or are you going to farm the jungle to get the unique items... or a balance of
  the two."* It is no longer merely playable space.
- **What the jungle pays** `[provisional]` — **unique items and certain
  power-ups** from its monsters, **plus a smaller gold drop**. **Lanes pay more
  gold than the jungle.** Gold buys similar-but-not-identical power-ups at the
  main base.
- **Jungle creeps and items are one of the three sources feeding the hero power
  threshold** (2026-08-09), which is the loss condition.
- **⚠ Jungle reachability is a function of the front line** (2026-08-11, the
  leash decision). How much of the jungle your hero can work is set by how far
  the lane has been pushed; conceding ground **closes your own jungle toward your
  base.** **The other arm of the axis gates access to this one.**

## Dump — 2026-08-11 (first): the jungle's shape, the hero's control, and what the jungle is not

> **⚠ Source note.** This dump and the second one below were **captured before
> any action**, per the standing preference. **Quoted passages are his own
> wording as captured**; unquoted material is record-paraphrase of that capture.
> This file's convention requires keeping the distinction.

### ⚠ AMENDMENT — the hero is not fully autonomous, and control is by tapping the map

**His words:**

> *"A hero is not fully autonomous."*

**This amends recorded material and is flagged as an amendment.** The map and
`AGENTS.md` say the player sets **standing orders** and *"never steers
directly"*, with the hero working the jungle automatically on route/behaviour
modes.

**How it is recorded, precisely:** as an **amendment to `[provisional]`
material, not a reversal of a `[committed]` one.** The never-steers-directly line
is `[provisional]` in the map. What is `[committed]` is a **different axis** —
*casting is selection, not performance*, and the removal of skill shots. **A hero
movement control does not by itself violate that.**

**Three candidate control schemes were named at the time, and none was chosen:**

1. **A small joystick button** to move the hero around.
2. **Tapping a minimap** to send it somewhere.
3. **Preset buttons** that move the hero to a certain area on press.

Asked whether he wanted to settle the scheme before the commissioned brainstorm
returned, he said to **present all three as a possibility** — an instruction that
proposals must work across all three, or state which they depend on.

#### ✅ DECIDED, later — control is by tapping the map `[provisional]`

> *"I think player control will need to be done via tapping on the map."*

**The joystick and the preset move-to-area buttons are not chosen.** Tap-to-move
on the map is the control scheme. It is **consistent with casting-as-selection**:
the player **selects a destination**, they do not pilot.

**⚠ The superseded phrasing lives in other files and is pointed at rather than
silently left wrong.** None of these is edited by this rebuild:

- **`map.md`** — *"The player gives the hero standing orders"* in "Decisions so
  far", and *"How manually the hero's position can be manipulated"* in "Not yet
  specified". **Amended in place by this rebuild**, since the map is what a
  rebuild rewrites.
- **[15](15-heroes.md)** — carries *"you don't get to control your hero
  directly"* in several places, **stated twice** in its own record. **15 is not
  rebuilt here; its phrasing is superseded and must be read against this
  amendment.**
- **`AGENTS.md` / `CLAUDE.md`** — *"the player sets standing orders (lane, jungle
  camp) but never steers directly."* **Superseded. Reported, not edited.**

**Firstmate note, recorded as an error to correct:** several briefs asserted
*"the player never drives the hero directly"* as a **committed** constraint. That
was **firstmate over-stating provisional material**, and any work resting on it
should be re-read against this amendment.

#### ⚠ The open sub-problem he named — move versus attack-move

**Recorded, not solved.** His words:

> *"Not sure how to intuitively give the move and A+move ability though. Moving
> to a spot and getting attacked because you chose that option and its locked in,
> or the hero cant a+move will feel really bad."*

**The problem stated precisely:** a single tap is **one gesture** and there are
**two intents** — *go there and ignore everything* versus *go there and engage
what you meet*. Committing the player to the wrong one, or offering only one,
produces a bad feeling that is about **control**, not balance.

**This is a feel problem and therefore prototype work, not paper work.** It is
the sharpest thing for a prototype to answer, because **hero movement is the
player's primary verb**. *(Related, recorded elsewhere and not this ticket's
subject: the prototype's heading was given separately as **convey the whole as
envisioned** — *"prototype is less about how it ends right now and how the whole
was envisioned."*)*

### ✅ Confirmed without change

- **The jungle is playable space and the hero must traverse it.**
- **It pays gold for killing its creeps, plus items and certain power-ups.**
- **Screen budget is no longer a constraint**, because the camera pans — asked
  and answered directly: *"That's correct."*

### ✅ Aggro leashing confirmed — and it gains a condition, which is new structural material

Creeps can be pulled into the jungle by aggro and leash back, **but only where
the geometry allows it**:

> *"if they are in a spot where the jungle is open to allow that, or if the trees
> that separate the jungle from other areas of the jungle and from the lane get
> destroyed for whatever reason."*

**What that establishes** `[provisional]`:

- **Trees are walls**, separating jungle areas from **each other** and from the
  **lanes** — so the jungle is **a set of chambers, not one open field.**
- **Those walls are destructible** — *"get destroyed for whatever reason"* — and
  destroying them **changes where aggro pulls can reach.**
- Therefore **jungle geometry is mutable during a match**, and **aggro behaviour
  is a function of current geometry** rather than a fixed rule.

**⚠ Its relationship to terrain manipulation has not been asked.** Recorded
terrain manipulation already has a giant tree root blocking hero passage between
lanes, priced against traversal-by-default. **Whether these are the same system
has not been put to him. Do not assume it.** His instruction on this was to keep
**trees, the chasm and terrain manipulation all live** — *"present all three as a
possibility"* — and **not to collapse them into one system or split them into
three by inference.**

> **⚠ Updated by the second dump the same day: the chasm is cut *"for now."***
> **Trees and terrain manipulation both stay live, and their relationship is
> still unasked.**

### ✅ Jungle control — ANSWERED by dissolving the question

> *"There isn't really jungle control like a typical MOBA."*

**His reasoning, kept because it is a clean piece of first-principles work:**

- **No fear of being ganked.**
- **No teammates** to pressure other lanes and create the opening to move in.
- **No vision, and no need for vision**, to feel safe invading.

So the MOBA concept of jungle control — **contested territory policed by threat
and information** — **has no substrate in a 1v1 game with no fog and no allies.**
He was unsure whether this answered the ticket's question; **it does, by
dissolving it.**

**What remains is not jungle *control* but jungle *access***, and access is
governed by **the leash** (how far forward the hero may legally roam) and **the
retracting home field**.

### ✅ Where the jungle sits — ANSWERED `[provisional]`

> *"Just think of it as a typical MOBA map. You have the main base at the top and
> bottom. You have the three lanes: middle, left, right. And then you have the
> jungle that exists in between all of that, but nothing really traversable on
> the outsides."*

**Consistent with his 2026-08-07 refinement** that the jungle is everything
between the outer lanes except the bases, spanning nearly the full length of the
field, with little to no jungle outside the outer lanes.

#### ⚠ Heroes of Newerth — a reference describing a shape, explicitly NOT a request

He raised HoN's outskirts travel, where you could move around the map edges and
through trees, and noted its maze-like traversal was far heavier than League's.
**His own framing:**

> *"I don't know that that's necessarily something I want to implement"*

> *"maybe that viewpoint can be implemented in some sense with another novel
> idea, but that's neither here nor there."*

**Recorded as a reference, not a proposal.** The project carries a standing
gotcha about exactly this failure mode — *"watch for reference-vs-proposal in
quotes"* — and this is the case it was written for.

### 📤 Open, and commissioned — what the jungle actually contains

Deliberately deferred to its own session:

> *"this is going to have to be its own giant dump because I want it to be
> similar to a typical feel but still attempt to implement novel elements in as
> many areas as possible."*

He asked for an agent to brainstorm it first. **That brainstorm exists** —
`firstmate/data/mg-jungle-contents-brainstorm/report.md`, **cited, not imported**
— and the second dump below is his reaction to it. **No jungle contents are
proposed here.**

### ⚠ Jungle autonomy — unanswerable as asked, not open

> *"I don't know what you mean by how much of the jungle runs itself. Like creeps
> will respawn on a cadence or whatever the mechanism ends up being. I don't know
> what the exact mechanism is yet, so I guess I can't really answer three."*

**Recorded as unanswerable-as-asked rather than as an open question.** His own
example — camps respawning on a cadence — is itself the **low end of the autonomy
scale**, so the instinct was present even though the question did not land. The
question needed re-putting **concretely**. It was, as the brainstorm's **autonomy
ladder**, and the second dump below answers it rung by rung.

### ❓ Question returned to firstmate — owed an explanation, not a decision

He does not understand this ticket's carried candidate *"lanes take cast spells
(tempo), the jungle takes merged banks (investment)"* — specifically the
lanes-take-cast-spells half. **Owed a plain explanation.** Note the candidate
originates in **shelved [09](09-banking-mechanic.md)**, so it may be moot
regardless.

## Dump — 2026-08-11 (second): reacting to the jungle brainstorm

> **⚠ Source note.** His reaction to
> `firstmate/data/mg-jungle-contents-brainstorm/report.md`. **The report's
> contents are cited, never adopted** — what is recorded below is **his**
> answers. The ladder's rung numbering is the report's and is used here only as
> the shared vocabulary the answers were given in.

### ✅ Rung 2 — ADOPTED, with the content he wants in it `[provisional]`

**Endorsed directly.** Using a hypothetical **six camps a side**, for each camp
you know:

- **its difficulty**, and therefore **how long it would take you to finish it**,
- **how much damage you would take**,
- **how much mana it would cost you**,
- **an indication of what the camp is worth in gold**, and
- **what you could potentially get item-wise.**

**So rung 2's visible state is a pre-commitment readout**: the **cost** of taking
a camp and its **expected return, before you go.** That makes **the farm arm of
the axis comparable against the push arm without playing it out.**

**⚠ His own note, and it is an instruction:** *"Tons more decisions stemming from
that, but those are later."* **Do not open them.**

### ✅⚠ Rung 3 — ADOPTED, but NARROWED to a time curve `[provisional]`

> *"I think is also going to be a parameter, but maybe just in the sense of the
> earlier the game, the easier the creeps are, the less impactful the items. And
> then as the game goes on, they eventually get more difficult, drop better, drop
> more."*

**This is a narrowing and it is recorded as one.** The ladder's rung 3 was *the
jungle responds to **game state*** — which is to say, to **who is winning**. **He
redefined it as responding to match TIME:** camps scale **on a clock, not on the
scoreline.**

**Consequences worth noting, not deciding:**

- A time curve is **symmetric and predictable**, so **it cannot be farmed by a
  losing player** and **raises no `[committed]` deliberate-losing rail concern.**
- It puts the jungle on **the same match clock** as the retracting home field and
  the leash — **a third mechanism on one clock.**

**Tuning is his, and he parked it:** *"That will have to be fleshed out
balance-wise as well."*

### 🔧 Rung 4 — OPEN, with a shape

> *"If that was a thing, it would probably be on like a timer/cadence/event type
> thing."*

Then, plainly:

> *"is it like a neutral thing that pops up and does that? I don't know. I don't
> know what that one."*

**So: if** things leave the jungle to act on a lane, it happens **on a timer or
cadence, not continuously.** **Whether the thing that leaves can be an unclaimed
neutral that appears on its own is unresolved, and he said so.**

### ❌ Rung 5 — REJECTED, with both his reasons

> *"Monsters act on their own as in like they path and patrol... I mean, I'm
> trying to envision how that plays out. It just seems rather chaotic. Makes your
> own pathing pretty difficult too. So that's probably not going to be
> implemented."*

**Two reasons, both his, and the second is the sharper one:**

1. **It reads as chaotic.**
2. **It interferes with the player's own pathing** — which is specific to *this*
   design, where **hero movement is the thing being decided** and **route
   planning is the player's main spatial act.**

**Carried forward as a rejection with those reasons attached**, per the
append-only rule.

### ✅ Rung 4a, and the attribution principle

On the **Heroes of the Storm pattern** — clear a camp and it marches down your
lane for you:

> *"this is something that can be looked at. I don't mind that."*

**And on whether that counts as the jungle acting — it does not.** The question
was put to him directly and he ruled it is **the player** acting:

> *"If we're going to give camps the ability to be taken down and then taken
> over, I don't think you can count that as the jungle... That's got to be
> something you're doing."*

**Then he sharpened it himself, and the sharpening is the reusable part:**

> *"you're not getting power from the jungle, but you are claiming something of
> the jungle that then benefits you."*

**Recorded as a principle, not merely an answer:** the jungle is **not a
dispenser you receive from; it is a place you claim things out of.** That is
consistent with the central axis — **farming is an act, not an income stream** —
and it is a **usable test for future jungle proposals.**

### ❌ The chasm — CUT *"for now"*

**Its origin, which he supplied and which explains it:**

> *"It was just like an idea because I was playing around with you don't ever
> pass your own side type of deal. And so I'm like, oh, there can be this big
> giant gap in the middle and then a portal takes you across. I think it was my
> way of like preventing you from pushing early game or something like that."*

**Why it goes:** the problem it was invented for — **stopping an early push** —
now belongs to **the retracting home field**, and the **crossing rule it assumed
has been replaced by the front-line leash.** He considered alternatives and
**dismissed them as typical**:

> *"instead of like a river, how every other game does it, or just some elevated
> or lower elevation, something else."*

**The decision, in his words:**

> *"Maybe just crossing over is fine. There's a lot that has to be done already.
> Maybe just take out the chasm for now. We'll just consider it typical
> traversal."*

**⚠ The *"for now"* is his and must be preserved** — a shelving with a stated
reason, the same standing as banking (09), **not a permanent no.**

**⚠ The scope reasoning is recorded because it is a first:** *"there's a lot that
has to be done already."* **This is the first thing cut explicitly to limit scope
rather than because it failed on its merits.**

**Consequence, and it closes a long-standing question:** the two jungle halves
**connect by ordinary traversal.** The standing *"how do the halves connect, if
at all"* question is **closed by this.**

### ❌ Home field gating jungle access — NO

**Answered directly: no.** It produced a new subject in the same breath — below.

### 🆕 Invading the opponent's jungle — three separate things, not one

> *"If you go into your opponent's jungle, if we give that the ability to do
> that, that you get reduced gold and like no items, at least for like the first
> 5 minutes or something, or the first 3% or the first 50% or something, to
> prevent like smurfs from just like rolling new players."*

**These must not be collapsed:**

1. **Whether invading the enemy jungle is possible at all is itself open** — note
   his conditional, *"if we give that the ability to do that."*
2. **If it is, invasion pays less rather than being forbidden**: **reduced gold**
   and **no items.**
3. **The penalty is time-boxed, and the measure is undecided** — he offered
   **five minutes**, **3%** and **50%** **without choosing**, and the last two are
   not obviously the same kind of unit as the first.

**⚠ His stated purpose is unusual and is preserved exactly: it is an anti-stomp
device, aimed at stronger players rolling new ones** — *"to prevent like smurfs
from just like rolling new players"* — **not a balance lever between equals.**
That makes it a **player-experience decision**, even though its numbers are
tuning.

**Recorded, not asked:** it interacts with **the leash**, which already governs
how deep anyone can go, and with **the home field**. **Whether all three are
needed to bound early aggression has not been put to him.**

### 🔧 Jungle symmetry — DIRECTION GIVEN, tension unresolved

**He wants it not totally symmetrical:**

> *"Part of me wants to say yes for simplicity's sake, but I also want there to
> be some semblance of variety when you play."*

> *"I would like it to not be totally symmetrical, so that way depending on what
> side you end up getting for that map, maybe there's a difference."*

**The tension, in his words, and it is unresolved:**

> *"I'm not sure how to weigh the repetitiveness of symmetry versus the potential
> benefits you get from being on a certain side versus ones you don't."*

**His reference points, and they are references describing shapes, not
requests:** League has red and blue side with a jungle and river that are **not**
symmetrical; Heroes of the Storm's maps are symmetrical — *"and some aren't, or
maybe they all are, I don't know."*

**⚠ Do not resolve this.** The direction is his; **the weighing is not done.**

**Firstmate note, flagged as a note and not a decision:** in a 1v1 with no draft,
side asymmetry is a **fairness** question and not only a variety question — there
is no team composition or pick order to absorb a side advantage.

## Open questions after the 2026-08-11 dumps

**This is the live list for this ticket.**

- **📤 What the jungle actually contains** — **commissioned as its own session**
  at his instruction. The brainstorm report exists and is **cited, not adopted**;
  **no contents are chosen here.**
- **⚠ Jungle symmetry** — **direction given** (not totally symmetrical, for
  variety), **tension unresolved** (repetition versus side advantage). **His to
  weigh.**
- **⚠ Whether invading the opponent's jungle is possible at all** — his own
  conditional. If it is: **reduced gold, no items**, **time-boxed**, and **the
  measure is undecided** (five minutes / 3% / 50%, none chosen). **Purpose is
  anti-stomp, not inter-equal balance.**
- **🔧 Rung 4 — whether anything leaves the jungle for a lane**, and **whether an
  unclaimed neutral can do it on its own.** *"I don't know what that one."* The
  **shape** is settled if it happens: **timer or cadence, not continuous.**
- **How move versus attack-move is expressed through one tap.** **Prototype
  work**, his stated concern being that a locked-in wrong intent *"will feel
  really bad."*
- **How trees, terrain manipulation and jungle geometry relate to each other** —
  **not asked.** The chasm is cut *"for now"*; **trees and terrain manipulation
  both stay live and must not be collapsed.**
- **The many decisions stemming from the rung-2 readout** — *"those are later."*
  **Deliberately not opened.**
- **How rung-3's time curve is tuned** — **explicitly balance work, flagged by
  him and parked.**
- **Whether the leash, the home field and the invasion penalty are all needed**
  to bound early aggression — **not put to him.**
- **An explanation owed to him** of the carried *"lanes take cast spells, the
  jungle takes merged banks"* candidate — **an explanation, not a decision**, and
  possibly moot since it originates in shelved 09.
