# PWCG+ Journal UX Contract

The intended minimal hook is the existing PWCG Campaign Journal narrative editor.

A **Generate Story** action will:
1. preserve the current narrative;
2. resolve the exact mission/log for that CombatReport;
3. run the local analyser asynchronously off the Swing EDT;
4. reconcile analyser facts with PWCG facts;
5. build a compact story payload;
6. invoke the configured story provider;
7. validate the returned prose;
8. only then place it into the existing editable narrative field.

If the narrative is already non-empty, replacement requires explicit confirmation. Failure never silently overwrites text.

The player can edit the generated prose before the normal PWCG save path persists `CombatReport.narrative`.

No new Journal database/persistence format is required for v1. Ordinary Journal and AAR use must remain fully functional if this optional feature is absent, disabled, misconfigured or fails.
