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
**⚠ Amended again 2026-08-12/13 by his play-test of the prototype:** **the jungle
is SEMI-OPEN** — *"a forested area with clear openings and paths to traverse and
little pockets where the creeps will hang out"* — a **clarification of what the
jungle physically is, NOT a reversal of destructible trees**; **traversal must be
made a much better experience** (routes and angles, **not** sightline denial);
**the symmetry tension is dissolved** — rotational stays, mirror with a ruled
axis goes; **tap-to-move is validated by play**; and **hero intent is one tap
attack-move / two taps move**, leaving the **spam-to-single-tap problem** as the
sharpest open input question. **The live open-questions list is now at the foot
of this file.**
**⚠ Rebuilt 2026-08-18 through 2026-08-21:** access is now a **per-lane,
interpolated boundary field**; jungle side layouts lean **asymmetric but bounded**
with fairness only through randomized side assignment across matches, still
hedged *"I don't know"* / *"maybe not"*; there is **no jungle ownership**;
invasion is confirmed possible through the same push gate; jungle contents never
touch reinforcements; rung 4 is a **kill-then-capture HotS camp** whose units
march to their lane on their own pace; the steal risk is closed by **pause, not
transfer**; the ramp/fog idea is rejected; and merchant mercenaries are placed
only in your currently-owned lane space. Encounter novelty is explicitly
deferred and remains open. The dated rebuild below is authoritative for these
points.
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
  - **⚠ Corrected 2026-08-19:** gold buys **no hero power**. It funds creep/unit
    upgrades, buyback, and the neutral merchant; hero power comes from
    jungle-item drops and cards/chosen skills. See 05 and 17.
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

## Play-test — 2026-08-12 / 2026-08-13: the jungle's physical character, traversal, symmetry, and tap intent

> **⚠ Source note.** His reactions to the playable prototype in
> `.scratch/core-concept/prototypes/` — the **shipped build** on 2026-08-12 and
> the **corrected build** on 2026-08-13, both played on an S26 Ultra. **Quoted
> passages are his own wording as captured**; unquoted material is
> record-paraphrase. The prototype's own artifacts —
> [`COMMITMENT-overgrowth.md`](../prototypes/COMMITMENT-overgrowth.md) and its
> `## Amendments`, and
> [`FINDINGS-overgrowth.md`](../prototypes/FINDINGS-overgrowth.md) — are
> **cited, never imported**.

### ✅ AMENDMENT — the jungle is SEMI-OPEN, and this is a clarification, not a reversal `[provisional]`

**His definition, which is new material and supersedes an earlier reading:**

> *"The jungle is not an open forested area, neither is it a completely dense
> forested area. It is a forested area with clear openings and paths to traverse
> and little pockets where the creeps will hang out."*

And, separately:

> *"The hero does walk through the jungle. It is accepted."*

**What it establishes:** **paths and clearings by default, camps sitting in
pockets off them, and passage as the default state.**

**⚠ How this is recorded, precisely — it is a clarification of what the jungle
physically IS, not a reversal.**

- **Destructible trees stand.** Trees still separate jungle areas from each other
  and from the lanes, they are still destructible, and **aggro-pull geometry is
  still a function of current geometry** (see the 2026-08-11 first dump). **None
  of that is withdrawn.**
- **What the amendment touches is the *default density*.** The map's phrasing —
  *"the jungle is a set of chambers, not one open field"* — **was the map's
  reading of his aggro condition, not his words**, and it is **amended in place**
  by his definition above: the openings and paths are the normal state, and the
  trees are what stands between and beside them.
- **It is consistent with the standing traversal-by-default pricing baseline**
  (2026-07-26): blocking passage is only worth a card *because* passage is the
  default. His *"the hero does walk through the jungle"* restates that baseline
  rather than changing it.

**Sequence, kept so the record is diffable.** On 2026-08-12 he saw the hero path
straight through the jungle and **deferred rather than accepted** it — *"the only
issue being it's going through the jungle and stuff like that, but I guess that
doesn't matter right now."* That deferral was recorded at the time as **not** a
design change. The 2026-08-13 statement above is what settles it, in his words.

### 🆕 REQUIREMENT — traversing the jungle must be a much better experience `[provisional]`

**His words, and the requirement stands on its own:**

> *"the ability to traverse the jungle needs to be made a much better
> experience"*

**What prompted it, and what he then ruled out himself:**

> *"The jungle literally is just two vertical lines with pockets, right? There's
> no angles that create fog of war, like vision cutoffs."*

He immediately supplied the caveat himself — *"I guess that doesn't really matter
if you can always see where their hero is"* — since **there is no fog and a
minimap shows both heroes at all times.** **So sightline denial is explicitly
not the point.**

**What the requirement asks for instead:** the jungle should be **interesting to
move through** — **angles, routes, and choices about which way to go** — rather
than **corridors with alcoves.** This sits directly on the recorded principle
that **route planning is the player's main spatial act** (rung 5's rejection,
2026-08-11), and it raises the price of the still-commissioned
what-the-jungle-contains question without answering it.

### ✅ Jungle symmetry — the tension is RESOLVED BY A DISTINCTION `[provisional]`

**His objection to the corrected layout:**

> *"I'm not crazy about the layout. It's very symmetrical... when I picture other
> games, their maps don't look so NASCAR track with a line in the middle."*

**The resolution, and it splits one word into two things:**

- **Rotational symmetry stays** — the map landing on itself when turned 180° is
  **what keeps a 1v1 with no draft fair.** There is no draft and no team
  composition to absorb a side advantage, so this is close to mandatory.
- **Mirror symmetry with a ruled straight axis goes** — a perimeter shape with a
  line down the middle is **what produces the NASCAR read.** That is the thing he
  is objecting to.

**Irregular internal geometry supplies the variety he asked for without handing
either side an advantage** — which **dissolves the tension he recorded on
2026-08-11** and could not weigh: *"I'm not sure how to weigh the repetitiveness
of symmetry versus the potential benefits you get from being on a certain side
versus ones you don't."* **The two were never in conflict**, which is what that
tension assumed. His direction — *"I would like it to not be totally
symmetrical"* — is **unchanged and satisfied**, not overridden.

**⚠ Attribution, stated so it is not misread as his.** **The objection is his.
The rotational-versus-mirror distinction is a firstmate reading**, offered to be
overruled, and the corrected prototype was built to it — see
[`COMMITMENT-overgrowth.md`](../prototypes/COMMITMENT-overgrowth.md)'s
`## Amendments`, **A3**, which amends the card's own symmetry refusal for the
same reason. **His reaction to the result is not yet recorded.**

### ✅ Hero control — one tap is attack-move, two taps is move only `[provisional]`

**He reasoned it aloud and landed on the assignment himself:**

> *"maybe attack is one and then just move is two. So if a player chooses to spam
> to run away, it's always run away versus choosing to attack is deliberate."*

**One tap = attack-move. Two taps = move only.**

**⚠ His rationale is the load-bearing part and outlives the mechanism: panic is
spammy, so spam must resolve to fleeing**, while **attacking is the deliberate
act.** A control scheme that inverted this would punish exactly the moment a
player is least deliberate.

**Sequence:** he first offered it on 2026-08-12 **without choosing which way
round** — *"Maybe one tap is attack move and two taps is move, or the opposite"* —
with the constraint *"Maybe we don't need another verb"*, i.e. **both intents on
one gesture, no extra control added and no screen space spent.** The 2026-08-13
reasoning above is what chose the direction.

**This answers the *assignment* half of the move-versus-attack-move problem
recorded on 2026-08-11. It does not answer the half below.**

#### ✅ DECIDED 2026-08-22 — was the sharpest open input question in the design

**His words:**

> *"how do you spam tap to force your hero to move without attacking really
> quickly, but then somehow swap on a dime to the last tap being taken as a
> single tap?"*

**The problem stated precisely: with tap-count semantics a rapid sequence is
ambiguous by construction.** Every single tap must wait out the double-tap window
to find out whether a second tap is coming, so **either attack-move is delayed by
that window, or a fast run of intended moves is chopped into alternating
intents.** The prototype carries an implementation and its cost is documented in
[`FINDINGS-overgrowth.md`](../prototypes/FINDINGS-overgrowth.md) — **cited, not
adopted, and he has not reacted to it.**

**✅ DECIDED 2026-08-22 — the cited implementation is now the accepted answer,
for now.** *"For now"* is his own qualifier — not a permanent lock, and a
reversal would be recorded as one rather than silently dropped, per this
map's own append-only rule. Decision record:
`mg-prototype-redesign-readiness-decision-tap-sequence-disambiguation`. The
run-latch scheme, unchanged from `FINDINGS-overgrowth.md` §5: an aimed tap
fires attack-move immediately; a second tap within 0.36s upgrades to travel
and latches travel-intent for 0.5s, refreshed by every further tap; any
aimed tap (a camp, a tree) breaks the latch instantly; the known, stated cost
is no attack-move onto empty ground within 0.5s of a flee-tap. The
2026-08-22 `/hone` pass built against it without touching it and re-verified
the whole table by driving `tap()` directly — see
[`HONE-overgrowth.md`](../prototypes/HONE-overgrowth.md).

### ✅ Tap-to-move — VALIDATED BY PLAY

> *"The tap to move is actually really good."*

**The largest control risk in the design is closed by evidence rather than by
argument.** The 2026-08-11 decision chose tapping the map over **a joystick** and
**preset move-to-area buttons** on reasoning alone; this is the first time it has
been played. **Cross-reference [15](15-heroes.md)**, which still carries the
superseded *"you don't get to control your hero directly"* phrasing and is **not
rebuilt here**, and **[01](01-battlefield-geometry.md)**, which owns the viewport
the taps land on.

## Open questions after the 2026-08-11 dumps

**⚠ Bookkeeping: superseded as the live list by the play-test.** Original text
kept verbatim; status markers added in place, nothing deleted. The live list is
now "[Open questions after the play-test](#open-questions-after-the-play-test)"
at the end of this file.

~~**This is the live list for this ticket.**~~

- **📤 What the jungle actually contains** — **commissioned as its own session**
  at his instruction. The brainstorm report exists and is **cited, not adopted**;
  **no contents are chosen here.**
- **⚠ Jungle symmetry** — **direction given** (not totally symmetrical, for
  variety), **tension unresolved** (repetition versus side advantage). **His to
  weigh.**
  - **✅ DISSOLVED 2026-08-13 by a distinction** — **rotational symmetry stays
    (fairness), mirror symmetry with a ruled axis goes (the NASCAR read)**, and
    irregular internal geometry carries the variety. **His direction is
    unchanged and satisfied.** **The distinction is a firstmate reading; his
    reaction to the built result is not yet recorded.**
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
  - **✅🔧 HALF-ANSWERED 2026-08-13.** **The assignment is his: one tap is
    attack-move, two taps is move only**, because *"panic is spammy"* — spam must
    resolve to fleeing. **What remains open is the spam-to-single-tap problem in
    his own words**, and it is **the sharpest input question in the design.**
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

## Open questions after the play-test

**This is the live list for this ticket.** Everything above that is not marked
answered, commissioned or dissolved is still live. New and revised:

- ~~**How a fast tap sequence resolves into intent.**~~ **✅ DECIDED
  2026-08-22** — see "DECIDED 2026-08-22" above: the run-latch scheme is
  accepted as-is, for now. 15.
- **🆕 What makes jungle traversal interesting.** *"the ability to traverse the
  jungle needs to be made a much better experience"* — **routes, angles and
  choices, not corridors with alcoves**, and **explicitly not sightline denial**,
  which he ruled out himself because there is no fog and both heroes are always
  visible. **A requirement with no accepted answer**, and it lands on the
  **still-commissioned** what-the-jungle-contains question.
- **📤 What the jungle actually contains** — **unchanged, still commissioned as
  its own session.** The traversal requirement above **raises its price**: the
  contents now have to sit in a route network rather than in alcoves.
- **⚠ Whether invading the opponent's jungle is possible at all** — **unchanged
  and untouched by the play-test.**
- **🔧 Rung 4 — whether anything leaves the jungle for a lane** — **unchanged.**
- **How trees, terrain manipulation and jungle geometry relate** — **still not
  asked**, and **the semi-open amendment does not answer it.** Trees stay
  destructible, terrain manipulation stays live, and **they must not be collapsed
  into one system.**
- **Whether the leash, the home field and the invasion penalty are all needed**
  to bound early aggression — **unchanged, still not put to him.**
- **The rung-2 readout's downstream decisions**, and **rung-3's tuning** —
  **unchanged, deliberately not opened.**

## Rebuild — 2026-08-18 through 2026-08-21: the boundary field, access, camps, and merchant

### ✅ Jungle access is an interpolated field across all three lanes `[provisional]`

Each lane has its own push line, and **all three lines extend into and shape the
jungle boundary**. If all three lanes are pushed equally, the boundary is
**linear**. When they are uneven, it **curves toward whichever lane is behind**,
preserving safer farm near that lane for either side. This replaces the old
question of which single lane governs a between-lanes chamber: the answer is a
continuously recomputed field, not nearest-lane lookup.

**Still open, exactly as hedged:** the curve is *"a sine wave or a wave, I don't
know exactly which one."* No curve function, weighting rule, or balance number
is chosen here.

### 🔧 Jungle symmetry points toward bounded asymmetry, still hedged

**This corrects rather than silently overwrites the 2026-08-13 firstmate reading
that rotational symmetry settled fairness within each match.** The captain's
later direction is genuine per-side asymmetry, bounded so it does not largely
affect gameplay, with side assignment randomized so exposure tends toward
fifty/fifty over a player's lifetime of matches. Fairness is therefore supplied
**across matches**, not by making each individual map rotationally identical.

His uncertainty is part of the decision record and remains verbatim: *"I don't
know"* and *"maybe not."* This is a direction, **not a lock**.

### ✅ No jungle ownership; push earns access uniformly

Nothing in the jungle belongs to either player. There is no separately owned,
neutral, or enemy jungle territory: **a hero may reach any jungle point only
when the same push-based boundary field has opened access to it.** The merchant
is contestable because this general rule applies there too, not because it sits
inside a special neutral zone.

### ✅ Jungle contents never touch reinforcements

**No jungle content adds to, removes from, or otherwise changes the reinforcement
pool.** Jungle creeps pay hero power/economy returns and create the push-versus-
farm positioning choice; they are not a fourth reinforcement lever.

### ✅ Jungle invasion exists, through the same boundary

Invasion is possible. The hero must first push far enough for the interpolated
boundary to admit it into that part of the opposing side's jungle. **Only the
existence half closes here.** The previously recorded penalty remains unchanged:
reduced gold, no items, time-boxed, intended as an anti-stomp device. **Its exact
measure remains parked** — five minutes / 3% / 50% were examples and none was
chosen.

### ✅ Rung 4 is kill, then capture; captured units march independently

The adopted HotS-style sequence is:

1. Kill the camp.
2. After the camp clears, a capture circle opens for a short window.
3. Stand in it uncontested to claim the camp.
4. Claimed units march toward their **corresponding lane** on their own pace,
   **not synchronized to the minion wave**.

Incidental alignment with a minion wave is fine either way and is not engineered.
The 2026-08-21 *captured-camp lane push* question was raised and confirmed as
**already fully covered by this rung-4 decision**, not a new rule.

### ✅ The camp-steal risk closes as “pause, not transfer”

The 2026-08-19 baseline left capture stealing open as potentially *"cheesy."*
The captain later adopted the actual HotS contest rule: **either side must stand
in the circle uncontested; if both heroes are present, the circle remains
contested and neither side's progress completes.** The first hero to arrive does
not silently win the camp.

**Attribution boundary:** he confirmed this mechanic itself. He did **not**
independently confirm the scout's two companion measures — shared notification
of the kill/capture window, or treating the boundary field as sufficient risk
containment. Those remain scout recommendations only. He separately accepted
melee-versus-caster contest fairness as a known, intended hero-choice risk; it
creates no new hold.

### ❌ Vision-blocking height/ramp terrain is rejected

The HoN-style rise that hides a camp until the hero climbs it was first floated,
then downgraded to *"just a spitball idea"*, then rejected: *"Okay, skip the
ramp idea."* **Reason:** it is the same hidden-information shape as the
fog-for-camps idea he already floated and walked back, while this design has no
fog anywhere because casting is selection and selectable targets must be visible.

The narrower **HoN uphill-miss** rule is also rejected as *"just extra stuff not
necessary for a MOBA game."* This does not prohibit terrain from reducing a
hero's accuracy generally; that distinct rule lives in 15.

### 🔧 Merchant siting leans toward a multi-lane confluence, not a lock

The merchant is **not dead-center-mid**, where creeps crash. The captain accepted
the confluence-spine framing: multiple lanes must be pushed to reach it, not only
mid — *"that's what I want anyway"* — while preserving *"I guess."* This is a
lean, not a locked site. **The existing W2 dead-zone and mid-region-lopsidedness
holds remain open and untouched.**

**Cross-reference to 17:** a mercenary unit bought at the merchant is
**tap-to-place and restricted to your own currently-owned lane space under this
boundary field.**

### ❓ Jungle camp encounter novelty remains open and deferred

The captain explicitly deferred this to a future session: *"I don't know. I'll
have to revisit that another time."* Two candidates must not be re-proposed as
answers:

- **State-dependent/sequential composition changes** are rejected: if the change
  is consistent, *"what's the point?"*; if random, he does not want it.
- **Roaming camps** were already rejected as inconsistent and as interference
  with player pathing.

No replacement candidate is invented here. The static-camp baseline remains
while encounter novelty stays open.

## Open questions after the 2026-08-21 rebuild

**This is the live addendum; every earlier open item not explicitly closed above
remains live.** In particular:

- The boundary's exact curve remains open: *"a sine wave or a wave, I don't know
  exactly which one."*
- Jungle camp encounter novelty beyond a static camp is deferred to a future
  session.
- Merchant siting is only a confluence-spine lean; **W2 dead zone** and
  **mid-region lopsidedness** remain open.
- All balance values remain parked, including rung-3 tuning, the capture-window
  length, and the invasion-penalty measure.
- The fast-tap intent problem, traversal-quality requirement, tree/terrain
  relationship, and readout downstream decisions remain unchanged.

**No longer open:** whether invasion exists; whether rung 4 is claimed; the
camp-capture steal risk; and whether a merchant can sell anything beyond terrain
effects (17 records the mercenary unit).
