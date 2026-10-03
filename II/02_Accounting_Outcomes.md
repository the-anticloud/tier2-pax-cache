# Accounting Outcomes

**Project:** `PAX_CACHE`  
**Tier:** TIER_2_ANTICLOUD_PAX  
**Identity:** First-party project (no upstream clone)

## The eight outcomes

Every settled action is classified as exactly one of these. The set is
deliberately wider than pass/fail, because a system that reports only
'within budget' cannot distinguish good planning from a budget nobody
read.

| Outcome | Meaning | Compliant |
| --- | --- | --- |
| `ADHERED` | spent within the declared allocation | yes |
| `USED` | consumed granted-but-undeclared budget | yes |
| `TOUCHED` | budget read, ~zero consumption | yes |
| `IGNORED` | budget available, never consulted | **no** |
| `EFFICIENCY` | finished materially under allocation, as planned | yes |
| `OVERSPEND` | exceeded allocation without escalation | **no** |
| `UNDERSPEND` | far under allocation: possible underplanning | yes |
| `REFUSED` | declined to act; budget preserved | yes |

`UNDERSPEND` is not `EFFICIENCY`. Finishing well under a realistic
allocation is good planning; finishing far under one usually means the
estimate was wrong or the work was skipped. The two should not score
the same, so they are separate outcomes.

## This project's standing

| Fact | Value |
| --- | --- |
| Upstream | first-party |
| Commit | NOT YET MEASURED |
| Upstream licence | NOT YET MEASURED |
| Licence class | NOT YET MEASURED |
| Clone size | NOT YET MEASURED |
| Ledger | no ledger file |
| Current TRL | NOT YET MEASURED |
| Post-optimisation TRL | NOT YET MEASURED |
| II budget cap | 750.0 IIU |
| Verified upstream edits | 0 |

Ledger blocks: **0**

Envelope `II-PAX_CACHE` caps spend at 750.0 IIU, warning at
600, escalating at
712.5.

The cap is a policy allocation, not a measurement. Until an action
settles into the ledger there is no observed cost for this project,
and the standing is genuinely unknown rather than good.

