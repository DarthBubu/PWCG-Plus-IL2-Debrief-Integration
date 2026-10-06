# Fact Authority and Reconciliation

## Analyser authority

Use the debrief JSON for logged player combat events and timing, direct/delayed kill evidence, damage evidence and known/unknown attacker, AI loss cause through `kill_cause`, logged takeoff/landing/parachute touchdown, and logged player final state except where PWCG has a campaign-level final casualty decision.

## PWCG authority

Use PWCG for pilot identity and rank, squadron/roster, mission type/objective/briefing, campaign date/location/context, awards/promotions/transfers, and final campaign casualty status where PWCG has adjudicated it.

## Loss-language invariant

An AI aircraft being generically recorded with `outcome=shot_down` is not sufficient evidence for prose saying it was shot down.

Narrative cause is bound to `kill_cause`. “Shot down” is allowed only for `kill_cause=shot_down`. Collision, friendly fire, AA and crash causes must retain their factual distinction.

The player does not have an equivalent `kill_cause`; player collision/loss inference therefore remains conservative.

## Conflict rule

Never give conflicting raw facts to a story model and ask it to choose. Reconciliation happens first.

If a material conflict cannot be deterministically resolved from the authority rules, story generation stops (or uses a code-built factual fallback where appropriate). The existing Journal narrative remains untouched.
