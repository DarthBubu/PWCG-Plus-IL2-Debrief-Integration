# Implementation Status

Date: 2026-10-07

## Confirmed

- Feasibility confirmed.
- Upstream author permission confirmed.
- Separate/headless analyser contract confirmed.
- Initial schema-v1 boundary frozen.
- PWCG Journal persistence architecture audited.
- PWCG AAR already resolves mission log identity; integration should reuse it rather than discover by recency.
- Provider-independent PWCG+ foundation staged.

## PWCG+ foundation currently staged

- `DebriefClient`
- `StoryFactReconciler`
- `StoryPayloadBuilder`
- `StoryGuardrailValidator`
- schema-v1 edge fixture
- offline structural regression
- staging into local and cloud whole-stack compile paths

The implementation was corrected for the frozen PWCG Gson 2.7 dependency before final staging.

## Still pending

- final local/offline compile acceptance evidence for the newly staged foundation (current GitHub Actions jobs terminate before useful validation evidence);
- Journal-side reader/controller for the new exact-log binding sidecar; old reports without a recorded binding intentionally fail closed;
- real PWCG compatibility corpus;
- Arrow-requested collision/bailout/escort samples;
- executable/licence release packaging;
- asynchronous Journal controller/button;
- StoryProvider implementation/provider choice;
- API-key/network/cost UX if a cloud provider is selected;
- runtime proof.

Until those are complete, this integration is not a released PWCG+ capability.

## 2026-10-07 hardening update

- Debrief wrapper now drains stdout concurrently so the timeout is real, redirects stderr, requires exit 0 + ok=true + output + schema 1, and avoids Files.readString/InputStream.readAllBytes dependencies.
- Reconciliation now binds exactly to Arrow schema-v1 kill causes: shot_down, collision_enemy, collision_friendly, friendly_fire, killed_by_aa, crashed_combat, crashed.
- Guardrail source now checks report-like output, likely truncation, false shot-down wording, final-state conflicts, reasoning leakage and conservative unknown person-like names.
- Frozen PWCG CombatReport persistence was re-audited: it contains no source-log identity. PWCG+ therefore stages a campaign-local exact-log sidecar written only after successful mission AAR using the LogFileSet PWCG itself selected. It does not use a newest-log fallback for Journal history.
- Sidecar replacement uses atomic move where the filesystem supports it, with replace fallback.
