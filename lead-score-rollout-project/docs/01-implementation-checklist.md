# Implementation checklist

Blockers (B) must be complete before launch.

## Handover: data science to engineering and ops

- [ ] Model card: purpose, population, features, metrics by band and region, limits, fairness checks (DS) **[B]**
- [ ] Code tagged v1.0.0 in Git; pinned environment (lockfile plus container image digest) (DS) **[B]**
- [ ] Model in registry with training-data snapshot hash and feature spec; semantic versioning (major = features change) (MLOps) **[B]**
- [ ] Reproducibility check: retrain from the tag reproduces AUC within 0.002 and golden-file scores within 0.001 (MLOps) **[B]**
- [ ] Train/serve parity tests: golden set of 500 leads plus unit tests on feature logic (DS) **[B]**
- [ ] Runbook: failure modes, rollback, who to page, fallback behaviour (MLOps) **[B]**
- [ ] Written handover sign-off: engineering accepts, DS stays on call for 4 weeks (PM) **[B]**

## Pipeline and CRM

- [ ] Data contract for the lead extract (columns, types, nullability) stored in the repo (Data Eng) **[B]**
- [ ] All nine pipeline checks live; alerts routed to named owners (Data Eng) **[B]**
- [ ] Score write-back to CRM: score, band, top 3 reason codes, model version, scored_at (CRM Admin) **[B]**
- [ ] Fail-safe: stale or missing score is labelled and routing falls back to legacy round-robin (MLOps) **[B]**
- [ ] Override field with mandatory reason code, logged with user and time (CRM Admin) **[B]**
- [ ] Manager view: band mix, contact-SLA, overrides per rep (Sales Ops)

## Validation

- [ ] UAT executed in staging and gate met (UAT tab) (PM) **[B]**
- [ ] Rollback drill completed end to end in under 30 minutes (MLOps) **[B]**
- [ ] Load test at 3x peak daily leads, scored within SLA (MLOps)

## People

- [ ] Managers and reps trained; attendance 95% or more, 100% of managers (Enablement) **[B]**
- [ ] One champion per region (about 1 per 6 reps) named (Sales Ops)
- [ ] Hypercare rota covering go-live plus 14 days (PM) **[B]**
- [ ] Leadership message: why scores, what changes, what does not (VP Sales)
