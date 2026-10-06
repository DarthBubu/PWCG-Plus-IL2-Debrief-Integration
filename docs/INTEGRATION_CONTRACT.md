# Integration Contract — v1

## External-process boundary

PWCG+ invokes the supplied analyser as a separate program. Parser source is not copied into PWCG+.

Command contract:

```
il2_debrief.exe <log> [<log> ...] --out <result.json>
```

Preferred input is one MLG. Text fallback must provide all `missionReport...[N].txt` parts; never knowingly pass only part 0 when later parts exist. Output must be outside the IL-2 FlightLogs directory.

## Schema admission

PWCG+ initial support is strictly `schema_version == 1`.

- schema 1: consume known fields and ignore unknown additive fields.
- schema >1: stop story generation with an actionable compatibility diagnostic.
- missing/invalid schema: reject.
- record `generator.version` and selected source log(s).

Do not consume `summary.crashed`, `summary.total_damage_taken` or `event.time_raw`.

## Process behavior

The wrapper must:
1. start the external analyser with Java ProcessBuilder;
2. avoid stdout/stderr pipe deadlocks;
3. impose a timeout;
4. require exit 0;
5. require the output file;
6. parse JSON with a real parser;
7. validate schema before consuming facts;
8. preserve error code/version/source-log diagnostics;
9. fail without affecting AAR/campaign/Journal persistence.

Known analyser exit meanings captured from the upstream contract: 2 input error; 3 MLG converter error; 4 parse error; 5 no player. PWCG+ adds its own start/timeout/no-output/schema failures.

## Log identity

Primary rule: reuse the exact mission log identity PWCG already resolved during AAR whenever it can be associated with the Journal report.

Timestamp/newest-file discovery is fallback-only and must never silently substitute a newer mission for an older Journal entry. Missing historical source log means Generate Story fails clearly and leaves the existing narrative untouched.

## Identity

`player.name` is the IL-2 login identity, not PWCG pilot identity.

Named AI matching is conservative: compare the analyser's aircraft name before the first comma against the PWCG roster. `squadron_flights` may contain aircraft from both sides and must be separated by country/side before PWCG squadron use.
