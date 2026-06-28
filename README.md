# Part 2 KPI Experiment

Name: Meera Mohiddin Shaik  
Student ID: 2511902  
Date: June 28, 2026

## Business Context

I analyzed an onboarding and activation experiment for a subscription product. The company tested two user experiences:
- Control group: current onboarding flow
- Treatment group: new campaign onboarding flow

The leadership question was straightforward: should the treatment be rolled out to all users?

## Business Problem Statement

The decision is whether to launch to all users, launch only to selected segments, or continue testing.

Who this impacts:
- Product and growth teams (acquisition and conversion goals)
- Revenue team (paid user growth and revenue quality)
- Support operations (ticket volume and effort)
- New users (onboarding clarity and early experience)

Metric that should improve:
- Paid conversion rate (North Star metric)

Risks to monitor:
- Refund rate
- Support ticket rate
- Revenue per converted user
- Segment-level drop-offs

Evidence required before recommendation:
- Statistically significant uplift in the primary metric
- Guardrails staying within acceptable risk
- Segment-level checks, not only top-line averages

## Dataset Description

Data file: data/campaign_experiment_data.xlsx

Dataset snapshot:
- 1,408 users total
- Control: 693
- Treatment: 715
- 16 columns covering funnel actions, revenue, support, and segmentation

Important columns:
- user_id, experiment_group, region, device_type, traffic_source, plan_type
- visited_landing_page, started_trial, completed_onboarding, converted_to_paid
- revenue_30d, refund_requested, support_tickets_30d, days_to_convert, engagement_score

## North Star Metric

North Star metric: Paid Conversion Rate

Why this is the main metric:
- It measures the exact behavior the campaign is supposed to improve.
- It links directly to subscription growth.
- It captures end-to-end onboarding effectiveness better than any single step metric.

Why other metrics are supporting:
- Landing page visits, trials, and onboarding completion explain where movement happens in the funnel.
- Engagement score indicates user quality and intent.
- Revenue metrics explain business quality after conversion.

Risk of blind optimization:
- Conversion can rise while experience quality falls, which can show up as higher refunds, support burden, or weaker revenue quality.

## KPI Tree Summary

North Star:
- Paid Conversion Rate

Primary drivers and sub-drivers:
1. Acquisition
- Landing page visit rate
- Traffic source quality

2. Activation
- Trial start rate
- Onboarding completion rate
- Engagement score

3. Monetization
- Paid conversion rate
- ARPU
- Days to convert

Guardrail metrics used:
- Refund rate
- Support ticket rate
- Average revenue per converted user
- Segment-level decline checks

KPI tree files:
- outputs/kpi_tree.png
- screenshots/kpi_tree_preview.png

## Data Preparation and Quality Checks

Prepared in analysis/experiment_analysis.xlsx.

Checks completed and handling decisions:
- Missing values:
  - device_type: 18 missing, labeled as Unknown
  - traffic_source: 24 missing, labeled as Unknown
  - days_to_convert: blank for non-converters by definition, kept blank
  - engagement_score: 14 missing, excluded only from engagement average
- Group counts: Control 693, Treatment 715
- Duplicate user IDs: none found
- Invalid binary values (0/1): none found
- Revenue outliers: kept after manual review as valid high-value users
- Segment distribution across groups: reviewed for region, device, source, and plan; no severe imbalance

## Experiment Analysis Approach

I created outputs/experiment_summary.xlsx to compare Control vs Treatment across required metrics:
- User count
- Landing page visit rate
- Trial start rate
- Onboarding completion rate
- Paid conversion rate
- Average revenue per user
- Average revenue per converted user
- Refund rate
- Support ticket rate
- Average engagement score
- Average days to convert

Segment analysis included:
- Region
- Device type
- Plan type
- Traffic source

## Headline Results

Top-line movement from Control to Treatment:
- Paid conversion rate: 3.17% to 6.99% (+3.82 pp)
- Landing visit rate: 63.6% to 72.6%
- Trial start rate: 25.1% to 29.1%
- Onboarding completion rate: 15.6% to 21.3%
- Average engagement score: 57.03 to 62.93
- Average days to convert: 8.86 to 6.40

Guardrail movement:
- Refund rate: 0.00% to 0.42%
- Average support tickets: 0.22 to 0.37
- Average revenue per converted user: USD 1,630 to USD 770

## Hypothesis Test Summary

Detailed test notes are in analysis/hypothesis_test_notes.md.

Primary test details:
- Metric tested: paid conversion rate
- Method: two-proportion z-test
- Tail: one-tailed (treatment > control)
- Significance level: alpha = 0.05

Result:
- z = 3.2519
- p-value (one-tailed) = 0.000573
- Decision: reject H0

Interpretation:
- There is strong statistical evidence that treatment improves paid conversion rate.

## Guardrail Metrics Considered

Guardrail readout is mixed:
- Positive: engagement is higher and users convert faster.
- Risk: support ticket load and refunds increased, and revenue per converted user declined.

Because of these trade-offs, this is not a full-rollout case yet.

## Final Recommendation

Recommendation: launch for selected segments and continue controlled monitoring.

Suggested launch segments:
- Free plan users
- Mobile and tablet cohorts

Suggested holdout:
- Basic plan users until support and revenue-quality signals improve

## Assumptions and Limitations

- Random assignment is assumed valid.
- Time window is short for long-term retention and LTV conclusions.
- Segment performance can shift with future channel mix and seasonality.
- Unknown labels were used for some missing categorical values to keep top-line coverage intact.

## Screenshots Included

- screenshots/summary_metrics.png: control vs treatment summary view
- screenshots/hypothesis_test_output.png: hypothesis test evidence
- screenshots/kpi_tree_preview.png: KPI tree preview

## Repository Artifacts Checklist

- data/campaign_experiment_data.xlsx
- analysis/experiment_analysis.xlsx
- analysis/hypothesis_test_notes.md
- outputs/kpi_tree.png
- outputs/experiment_summary.xlsx
- outputs/recommendation_memo.md
- screenshots/summary_metrics.png
- screenshots/hypothesis_test_output.png
- screenshots/kpi_tree_preview.png
- README.md
