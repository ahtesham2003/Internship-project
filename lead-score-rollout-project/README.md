# Lead score rollout: delivery plan

Delivery plan for taking a validated lead scoring model live across 60 sales representatives in three regions (North, West, South).

## Structure
| Path | Contents |
|---|---|
| `index.html` | Interactive plan: timeline, checklist, pipeline checks, UAT, rollout gates, A/B calculator, monitoring, RACI, readiness review. Open in any browser; no install. |
| `docs/` | Printable deliverables generated from the same data (checklist, timeline and gates, RACI, pipeline checks, UAT plan, monitoring spec, training outline, readiness review, A/B design). |
| `scripts/build_docs.js` | Regenerates `docs/` from `index.html` (`node scripts/build_docs.js`). |

## Assumptions
- Full go-live 21 Dec 2026; change it in the page header or in `scripts/build_docs.js`.
- About 20 representatives and 3 managers per region; West is the pilot region.
- A/B inputs (10% baseline conversion, 2,500 leads per week) are placeholders; replace with actual figures.
- Score band cut-offs and alert thresholds are starting values to tune during shadow mode.
