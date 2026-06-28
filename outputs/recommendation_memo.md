# Recommendation Memo

To: Product and Growth Leadership  
From: Business Analyst  
Date: June 28, 2026  
Subject: Rollout decision for onboarding campaign experiment

## Executive Summary

The treatment experience produced a clear and statistically significant lift in paid conversion rate versus control. Funnel movement was positive from landing visit through paid conversion.

However, the result is not risk-free. Support ticket rate increased meaningfully, and average revenue per converted user declined. Based on that trade-off, the best decision is selective rollout rather than full rollout.

Recommended decision: launch for high-response segments now, and continue controlled testing before expanding to all users.

## Business Problem

Decision options considered:
- Launch to all users
- Launch to selected segments
- Continue testing
- Do not launch

Who this decision affects:
- Product and growth teams
- Revenue outcomes
- Support operations
- User onboarding quality

Evidence needed:
- Reliable conversion uplift
- Guardrail stability
- Segment-level validation

## North Star Metric

North Star metric: Paid conversion rate

Why this metric was selected:
- It directly measures whether onboarding is turning signups into paying customers.
- It has the strongest connection to business growth in a subscription model.

Why the others are supporting:
- Funnel rates explain where users are progressing or dropping.
- Engagement and guardrails indicate quality and sustainability of the uplift.

Risk if optimized in isolation:
- A conversion-only lens can hide experience friction and lower long-term value.

## KPI Tree Explanation

North Star:
- Paid conversion rate

Primary drivers:
1. Acquisition
- Landing page visit rate
- Traffic quality

2. Activation
- Trial start rate
- Onboarding completion rate
- Engagement score

3. Monetization
- Paid conversion rate
- ARPU
- Days to convert

Guardrails:
- Refund rate
- Support ticket rate
- Revenue per converted user
- Segment-level declines

Files:
- outputs/kpi_tree.png
- screenshots/kpi_tree_preview.png

## Experiment Result Summary

Control (n=693) vs Treatment (n=715):
- Landing visit rate: 63.6% vs 72.6%
- Trial start rate: 25.1% vs 29.1%
- Onboarding completion: 15.6% vs 21.3%
- Paid conversion: 3.17% vs 6.99% (+3.82 pp)
- Avg revenue per user: USD 51.75 vs USD 53.88
- Avg revenue per converted user: USD 1,630 vs USD 770
- Refund rate: 0.00% vs 0.42%
- Avg support tickets: 0.22 vs 0.37
- Avg engagement score: 57.03 vs 62.93
- Avg days to convert: 8.86 vs 6.40

Supporting files:
- outputs/experiment_summary.xlsx
- screenshots/summary_metrics.png

## Hypothesis Test Interpretation

Primary test setup:
- Two-proportion z-test (one-tailed)
- H0: treatment conversion <= control conversion
- H1: treatment conversion > control conversion
- alpha = 0.05

Observed output:
- z = 3.2519
- p-value = 0.000573

Decision:
- Reject H0

Interpretation:
- The paid conversion lift is statistically significant and practically meaningful.
- The treatment has a real performance advantage on the primary metric.

Evidence:
- analysis/hypothesis_test_notes.md
- screenshots/hypothesis_test_output.png

## Guardrail Analysis

1. Support ticket rate
- Increased from 0.22 to 0.37.
- This is the highest operational risk signal.

2. Refund rate
- Increased from 0.00% to 0.42%.
- Low absolute count, but direction should be monitored.

3. Revenue per converted user
- Fell from USD 1,630 to USD 770.
- Suggests possible conversion-mix or value-quality trade-off.

4. Engagement and speed to convert
- Both improved in treatment.
- Positive signs for adoption and onboarding momentum.

Guardrail conclusion:
- Uplift is real, but risks are also real. This supports phased rollout.

## Segment-Level Insight

Segment findings:
- Free plan users show the strongest lift.
- Mobile and tablet cohorts outperform desktop lift.
- Basic plan users show limited incremental gain.

Implication:
- A segment-first launch captures upside while controlling downside.

## Final Recommendation

Decision: Launch only for selected segments.

Launch now:
- Free plan users
- Mobile and tablet users

Hold and retest:
- Basic plan users
- Any segment with elevated support-friction signals

This is the most balanced decision based on the available evidence.

## Risks and Limitations

- Randomization quality is assumed.
- Experiment window is short for long-term retention and LTV.
- Segment behavior may shift as traffic mix changes.
- Some categorical missing values were mapped to Unknown.

## Next Steps

1. Roll out to selected segments with daily guardrail monitoring.
2. Diagnose support ticket drivers in treatment users.
3. Test onboarding fixes for friction points.
4. Re-measure guardrails after 2 to 4 weeks.
5. Decide on full rollout only if support and value-quality metrics stabilize.
