# Hypothesis Test Notes

## Business Decision
Should we launch the new onboarding campaign to all users?

## Metric Being Tested
Paid Conversion Rate

## Hypotheses
- **Null Hypothesis (H₀):** The paid conversion rate of the Treatment group 
  is equal to or less than that of the Control group.
- **Alternate Hypothesis (H₁):** The paid conversion rate of the Treatment 
  group is greater than that of the Control group.

## Test Type
One-tailed test (we only care if Treatment is *better*, not just *different*)

## Significance Level
α = 0.05 (5%)

## How to Interpret
If p-value < 0.05: Reject H₀. There is statistically significant evidence 
that the treatment improved conversion rate.
If p-value ≥ 0.05: Fail to reject H₀. We cannot conclude the treatment 
improved conversion.


## Test Results
- Control conversion rate: 0.031746032
- Treatment conversion rate: 0.06993007
- Z-statistic: 3.251871262
- P-value: 0.00057324
- Decision: Reject H0 - Launch

## Business Interpretation
[Since p < 0.05]: The treatment group showed a statistically significant 
improvement in paid conversion rate. This is unlikely to be due to chance.
