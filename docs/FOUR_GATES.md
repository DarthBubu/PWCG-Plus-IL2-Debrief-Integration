# Four Mandatory Integration Gates

## Gate 1 — Contract freeze

Freeze and version the upstream CLI contract, story guardrails and reference Java client. Initial PWCG+ support is schema v1 only. Preserve field limitations, exact-log identity and version diagnostics.

## Gate 2 — Java/headless wrapper

Separate ProcessBuilder invocation, timeout, stream safety, exit/output checks, proper JSON parsing, schema admission, campaign-local/cache output, fail-soft behavior and asynchronous Journal execution. Keep story-provider transport behind an interface rather than coupling a cloud service to CampaignJournalGUI.

## Gate 3 — Real PWCG compatibility

Arrow has explicitly noted that PWCG missions were untested. No release claim until the real-PWCG corpus has been compared end-to-end: raw log → analyser JSON → PWCG AAR/campaign facts → reconciled payload → narrative → guardrail result.

## Gate 4 — Licensing / packaging / credit

When PWCG+ distributes the analyser, package the external executable(s) with the required upstream GPL licence, mlg2txt MIT notice/credit, and short IL-2 Campaign Tracker attribution/source reference. Do not copy parser source into PWCG+.

A release regression should verify that executable, required notices and credit travel together.
