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

## 2026-10-07 source-completion pass

Staged in PWCG-Plus, pending compile/runtime proof:
- fail-closed Journal DebriefLogResolver: bound .mlg preferred; otherwise only a complete contiguous bound [0]..[N].txt set; no newest-log search.
- provider-neutral StoryProvider interface.
- StoryFactAssembler contract forces analyser JSON + PWCG authority through reconciliation before any model/provider sees data.
- JournalStoryController uses SwingWorker so analyser/provider work is off the Swing EDT; raw logs and raw analyser JSON are not passed to StoryProvider.
- guardrails now separately require every supplied casualty/person, award and promotion fact, in addition to loss-cause/final-state/style checks.
- compatibility fixtures cover seven schema-v1 kill causes, bailout/capture/end-in-air, delayed kill, multipart text, old-Journal and deleted-bound-log cases.
- release-only packaging regression requires il2_debrief.exe + GPL LICENSE + credit, and LICENSE-mlg2txt whenever mlg2txt.exe is shipped. This is intentionally not a compile prerequisite.

Still intentionally pending:
- concrete StoryFactAssembler implementation against real PWCG AAR/campaign objects (requires compile/source-fit iteration and real-log corpus validation).
- concrete StoryProvider/network/key UX.
- final CampaignJournalGUI button wiring/replacement confirmation; do not expose an unusable button before the above dependencies are proven.
- real PWCG log corpus and Arrow comparison, especially collision, bailout and escort.
- local/cloud compile evidence.
