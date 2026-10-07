# Case study: results from a live pilot

Five batches of CVs (56 in total) for one trader role, before and after the agent went live. All candidates are anonymised: `P` = pre-pilot batch, `B1`–`B4` = batches 1–4.

- **Manual period** = pre-pilot batch (24 CVs) + batch 1 (8 CVs)
- **Agent period** = batches 2–4 (24 CVs)

## Headline numbers

| Dimension | Manual | Agent | Change | Type |
|---|---|---|---|---|
| CV handed to hiring manager → invite sent (median) | 5.5 days | 19 hours | −86% | measured |
| Manual coordination time per candidate | ≈37 min | ≈6 min | −84% | estimate |
| Hiring manager's shortlist rate | 34% (11/32) | 58% (14/24) | +24 pp | measured |
| Round 1 → next round | 12.5% (1/8) | 40% (4/10) | +27.5 pp | measured |
| CV → offer (hired candidates) | 29 days | 28 days | flat | measured |
| Double bookings | — | 0 | | measured |
| Bounced invites caught in the same run | — | 3/3 | | measured |
| Slot conflicts auto-resolved | — | 3, no HR input | | measured |
| Roll-out across 4 earlier hiring lines (67 candidates) | 32.5 h | 6.7 h | 25.8 h saved | estimate |

## Finding
The HR stage went from days to hours, but end-to-end time-to-hire stayed flat. The bottleneck moved to interviewer availability and second-round scheduling.

## How numbers were measured
- "CV handed over" = upload time to the hiring manager's shortlist / drop folders, so it includes the manager's screening time.
- Effort model: 10 min per outbound email and 60 min to cross-check schedules per 5 candidates (HR's estimates); 2.9 outbound emails per arranged candidate (measured on 8 manual-period candidates). See `data/effort_model.csv`.
- Limits: small sample; the shortlist-rate rise began before the agent went live.

## Files
| File | Content |
|---|---|
| `data/funnel_by_batch.csv` | CVs → shortlist → round 1 → next round → hire, per batch |
| `data/candidates_shortlisted.csv` | Per-candidate timeline (anonymised) |
| `data/cvs_dropped_by_date.csv` | CVs the manager dropped, by date |
| `data/speed_metrics.csv` | Stage durations, manual vs agent |
| `data/effort_model.csv` | Assumptions and calculation |
| `data/history_rollout.csv` | Roll-out estimate across earlier hiring lines |
| `data/reliability.csv` | Conflicts, bounces, errors |
