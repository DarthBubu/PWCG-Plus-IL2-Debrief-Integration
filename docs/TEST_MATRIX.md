# PWCG Compatibility Test Matrix

| ID | Scenario | Status |
|---|---|---|
| A | Normal fighter / direct kill | Pending real log |
| B | Delayed loss after player damage | Pending real log |
| C | Bailout | Pending real log |
| D | Enemy collision | Pending real log |
| E | Friendly collision | Pending real log |
| F | Player-involved collision | Pending real log |
| G | Escort | Pending real log |
| H | Ground attack / building / vehicle kill | Pending real log |
| I | AA-caused AI loss | Pending real log |
| J | Friendly-fire AI loss | Pending if obtainable |
| K | Multi-part missionReport text logs | Pending real log |
| L | MLG input | Pending real log |
| M | Mission ended in air / Alive | Pending real log |
| N | Player KIA/MIA/capture | Pending real log |
| O | Multiple named PWCG flight members | Pending real log |
| P | Spawned / late-spawn AI | Pending if present |
| Q | Busy mission with unrelated aircraft | Pending real log |

## Acceptance per case

Confirm the correct mission/log was selected; PWCG identities match conservatively; loss language follows `kill_cause`; PWCG final casualty adjudication wins where required; compact payload contains only relevant facts; story does not invent unsupported events; and any failure leaves normal PWCG AAR/Journal/campaign behavior intact.

Evidence should be stored under `evidence/<case-id>/` only when redistribution/privacy/licensing permits. Otherwise record hashes, analyser version and a redacted expected/actual report.
