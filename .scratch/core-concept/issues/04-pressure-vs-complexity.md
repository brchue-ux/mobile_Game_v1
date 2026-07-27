# Pressure vs. complexity — the learning curve

Type: grilling
Status: open
Blocked by: 02

## Question

How do deliberate card-combining and a running real-time clock coexist without
the clock punishing the exact behaviour the game is built around?

The user named this directly as a likely fall-off point. It is the design's
central tension, not a polish concern:

- Combining rewards thought. Real-time punishes thought. A new player who stops
  to reason about a combo gets run over, learns that thinking loses, and either
  stops thinking or stops playing.

Things the answer must settle:

- **Does time ever yield?** Slow-mo while composing, a compose buffer, a pause on
  card selection, or nothing at all — clock runs flat.
- **The onboarding ramp.** How does a player meet combining for the first time?
  Is there a low-pressure context (PvE, tutorial, practice) where combos can be
  learned without a clock?
- **Cognitive load ceiling.** How many simultaneous things is a player tracking —
  three lanes, creep states, hand, cooldowns, opponent's field? What gets cut?
- **Is depth optional?** Can a player who never combines still function, with
  combining as the mastery layer above? Or is combining mandatory from minute
  one?
- **Where the skill floor sits** relative to where you want the ceiling.
- **Where execution skill lives, or whether it lives at all** —
  **inherited 2026-07-26** from [03](03-gesture-skill.md), which was closed by
  removing skill-shot casting. All remaining skill is cognitive: selection,
  timing, combining, deckbuilding. Two readings, and this ticket must pick one:
  either that is the game's **identity** (a commander game, deliberately not a
  dexterity game — which sits well with the accessibility-beats-novelty lock), or
  it is a **hole** where the ceiling used to be. Do not fill it reflexively; the
  removal was made on complexity grounds and re-adding a dexterity layer under
  another name would undo it.

**Note the tension eased on 2026-07-26.** Removing skill shots deleted the
sharpest form of this ticket's problem: a deliberate puzzle decision immediately
followed by a dexterity test under the same clock. What remains is thinking vs.
the clock, which is still the central risk but is now one problem rather than
two.

Blocked until 02 defines what combining costs in attention and time.
