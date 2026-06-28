# Hypothesis Test Notes

Date: June 28, 2026

## Business Decision Link

The business decision is whether the new onboarding campaign should be rolled out widely. The statistical question I tested was whether treatment genuinely improved paid conversion, or whether the observed lift could be random variation.

## Metric Tested

Primary metric: Paid conversion rate

Definition:
- paid conversion rate = converted_to_paid users / total users in each group

Why this metric:
- It directly captures the campaign objective.
- It provides a clear signal for launch decisions.

## Hypotheses

Null hypothesis (H0): treatment conversion is less than control conversion.

H0: p_t < p_c

Alternative hypothesis (H1): treatment conversion is greater than control conversion.

H1: p_t > p_c

## Tail Type and Significance Level

- Test type: two-proportion z-test
- Tail type: one-tailed (right tail)
- Significance level: alpha = 0.05

Why one-tailed:
- The business hypothesis is directional. The concern is whether treatment performs better.

## Test Inputs

- Control users: 693
- Control conversions: 22
- Control rate: 3.17%
- Treatment users: 715
- Treatment conversions: 50
- Treatment rate: 6.99%
- Absolute lift: +3.82 percentage points
- Relative lift: +120.3%

## Calculation Summary

Pooled proportion:

p_hat = (22 + 50) / (693 + 715) = 0.0511

Standard error:

SE = sqrt(p_hat * (1 - p_hat) * ((1/693) + (1/715))) = 0.011744

Test statistic:

z = (0.0699 - 0.0317) / 0.011744 = 3.2519

## Test Output

- z-statistic: 3.2519
- critical value (one-tailed, alpha 0.05): 1.6449
- p-value (one-tailed): 0.000573
- p-value (two-tailed reference): 0.001146

## Decision Rule

- If p-value < 0.05, reject H0.
- If p-value >= 0.05, fail to reject H0.

Observed p-value is 0.000573, so H0 is rejected.

## Interpretation Logic

I used three checks before drawing the business conclusion:
1. Statistical significance: Is the lift likely real?
2. Practical significance: Is the lift large enough to matter?
3. Guardrails: Is the improvement safe to scale?

So conversion significance is necessary, but not sufficient for full rollout.

## Business Interpretation

Treatment clearly improved paid conversion. This supports launch, but only with guardrail scrutiny.

Guardrail observations:
- Refund rate increased from 0.00% to 0.42%.
- Support ticket rate increased from 0.22 to 0.37.
- Revenue per converted user declined.

Conclusion from the test and guardrails combined:
- The campaign works for conversion.
- Full rollout still carries operational and revenue-quality risk.

## Supporting Tests

Revenue (30-day), independent t-test:
- t = -0.1060
- p = 0.9156
- Interpretation: no significant difference in overall average revenue per user.

Engagement score, independent t-test:
- t = -7.9445
- p < 0.0001
- Interpretation: treatment users are significantly more engaged.

## Recommendation Connected to the Test

Based on hypothesis results and guardrails:
- Proceed with selective launch, not full launch.
- Prioritize segments with strongest lift (Free plan and mobile/tablet).
- Continue testing after support-friction fixes.

Evidence image:
- screenshots/hypothesis_test_output.png
