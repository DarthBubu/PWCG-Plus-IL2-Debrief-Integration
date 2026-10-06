# For Arrow / Alexander

Thank you for making `il2_debrief.exe` available for PWCG+ integration.

This repository is the shared interoperability/evidence workspace so we can report PWCG-specific findings with exact, reproducible inputs and expected/actual results rather than passing large descriptions through forum messages.

## Integration we are implementing

PWCG+ will call your analyser as a **separate process**. We will not copy the parser into PWCG+.

Initial contract:

```
il2_debrief.exe <log> [<log> ...] --out <result.json>
```

PWCG+ initially accepts **schema_version 1 only**. We retain analyser error codes, generator version and exact selected source log for diagnostics.

PWCG+ supplies its own pilot identity/rank, squadron, objective, briefing, campaign date/context, awards/promotions and campaign-level casualty adjudication. The analyser supplies logged combat facts/timing and AI loss cause.

The model will never receive raw FlightLogs. PWCG+ first reconciles the two factual sources and builds a compact fact payload.

## Items we particularly want to validate with you

The first real-PWCG corpus will include normal direct kills, delayed losses, bailout, enemy/friendly/player-involved collision, escort, ground attack, AA loss, friendly fire if obtainable, multi-part missionReport logs, MLG, mission-ended-in-air, player casualty outcomes, multiple named PWCG flight members, late/spawned AI and busy missions.

For every case we will preserve:

```
input log
→ analyser JSON
→ relevant PWCG AAR facts
→ reconciled facts
→ expected narrative constraints
→ pass/fail finding
```

We will send you the collision, bailout and escort cases you specifically requested once captured.

## Important policies already frozen

- Exact PWCG AAR-resolved mission log identity is preferred; we will not silently use the newest FlightLog for an old Journal entry.
- IL-2 login name from `player.name` is not treated as PWCG pilot identity.
- AI `kill_cause` controls narrative cause. Generic `outcome=shot_down` does not permit “shot down” wording unless `kill_cause=shot_down`.
- PWCG campaign casualty adjudication wins over the logged player final state where PWCG has made a campaign-level decision.
- Unresolved material conflicts stop story generation rather than asking an LLM to decide what happened.
- The integration is fail-soft and cannot become an AAR/campaign dependency.

See [docs/TEST_MATRIX.md](docs/TEST_MATRIX.md) for the planned compatibility corpus.

## Cross-project issue format

If we find an analyser/PWCG compatibility issue, we will record the smallest redistributable test case with expected versus actual JSON, analyser version/schema, PWCG context required to reproduce it, and whether the issue is parser-side, PWCG-side or unresolved.

That should let both projects change independently without creating an undocumented coupling.
