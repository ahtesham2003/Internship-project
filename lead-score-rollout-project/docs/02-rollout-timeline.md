# Rollout timeline and gates

Full go-live: 21 Dec 2026

| Phase | Start | End | Owner |
|---|---|---|---|
| Handover and repro checks | 29 Oct 2026 | 05 Nov 2026 | DS to MLOps |
| Pipeline, CRM and checks build | 05 Nov 2026 | 19 Nov 2026 | Data Eng, CRM |
| UAT in staging | 19 Nov 2026 | 26 Nov 2026 | PM, Sales Ops |
| Shadow mode, all regions | 19 Nov 2026 | 03 Dec 2026 | MLOps, DS |
| Training (managers, then reps) | 26 Nov 2026 | 16 Dec 2026 | Enablement |
| Pilot: West region live | 03 Dec 2026 | 17 Dec 2026 | Sales Ops |
| Readiness review, go/no-go | 17 Dec 2026 | 18 Dec 2026 | VP Sales |
| Hypercare (all 60 reps) | 21 Dec 2026 | 04 Jan 2027 | PM, MLOps |

## Shadow gate

2 weeks, all regions. Scores written to a hidden field; reps see nothing.

| Criterion | Required |
|---|---|
| Daily pipeline runs succeeded | ≥ 99 % |
| Leads scored within SLA | ≥ 98 % |
| Live vs golden score parity | ≥ 99 % |
| AUC drop vs validation | ≤ 0.03 abs |
| Top-band lift as share of validation lift | ≥ 80 % |
| Open critical alerts | ≤ 0 # |

## Pilot gate

2 weeks, West region (20 reps) sees scores and routing. North and South stay in shadow.

| Criterion | Required |
|---|---|
| UAT critical tests passed | ≥ 100 % |
| Reps opening the score weekly | ≥ 70 % |
| Hot leads contacted within SLA | ≥ 85 % |
| Override rate | 5 to 25 % |
| Overrides with a reason code | ≥ 90 % |
| Conversion vs pre-pilot baseline (guardrail) | ≥ -3 % rel. |
| Rep satisfaction (1 to 5) | ≥ 3.5 score |
| Sev-1 incidents | ≤ 0 # |

## Go-live gate

Full launch on the fixed date for North and South, West continues.

| Criterion | Required |
|---|---|
| Pilot gates all met (1 = yes) | ≥ 1 flag |
| Rollback drill passed (1 = yes) | ≥ 1 flag |
| Training completion, reps | ≥ 95 % |
| Training completion, managers | ≥ 100 % |
| Pipeline SLO met, trailing 14 days | ≥ 99 % |
| Hypercare rota confirmed (1 = yes) | ≥ 1 flag |

## Rollback procedure

Triggers (any one): Sev-1 data or scoring incident unresolved for 4 hours; Hot-lead SLA below 60% for 3 days; escalation from two or more regions; conversion guardrail breached for 2 weeks.

1. MLOps incident lead declares rollback; VP Sales informed within 15 minutes.
2. Feature flag returns CRM routing to legacy round-robin; score fields hidden but still written.
3. Revert to the last registered model version if the model is the cause; otherwise fix the pipeline in place.
4. Sales Ops messages all representatives within 1 hour.
5. Target: steps 2 to 3 complete in under 30 minutes (proved in the rollback drill).
6. Re-entry: root-cause note, one clean day in shadow, then a new go decision.
