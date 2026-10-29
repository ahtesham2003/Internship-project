# A/B evaluation: scored vs unscored routing

- Unit: lead, randomised 50/50 within each region, stratified by lead source.
- Primary metric: lead-to-opportunity within 30 days. Guardrails: contact SLA, representative satisfaction, pipeline value per lead.
- Assumptions: baseline 10%, significance 5% two-sided, power 80%, clustering inflation 1.1, 2,500 new leads per week.
- Fixed horizon; interim reads are for safety only. Analysis: two-proportion test, then a model with representative as a random effect.

| Relative lift | Total leads | Weeks to enrol |
|---|---|---|
| 5% | 1,27,097 | 51 |
| 10% | 32,453 | 13 |
| 15% | 14,723 | 6 |
| 20% | 8,446 | 4 |
| 30% | 3,899 | 2 |

Add about 5 weeks for outcomes to mature. The test runs after launch; the pilot checks guardrails only.
