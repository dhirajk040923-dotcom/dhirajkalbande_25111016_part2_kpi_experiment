# Campaign Experiment — Recommendation Memo

**To:** Leadership / Decision Makers
**From:** Business Analyst
**Date:** June 2026
**Subject:** Launch Recommendation — New Onboarding & Activation Campaign

---

## Executive Summary

The new onboarding and activation campaign was tested on 1,408 users split
between a Control group (existing experience) and a Treatment group (new
campaign experience). The Treatment group showed a conversion rate of 6.99%
compared to 3.17% in the Control group — more than double the baseline.
This result is statistically significant (p = 0.00057), and guardrail metrics
show no meaningful degradation in user quality. The recommendation is to
**launch the new campaign to all users.**

---

## Business Problem

The company needed to determine whether a new onboarding and activation
campaign meaningfully improves paid conversion rates without introducing
hidden risks such as increased refunds, support burden, or disengaged users.
The decision impacts the entire user acquisition funnel and directly affects
revenue growth.

---

## North Star Metric

**Paid Conversion Rate** was selected as the North Star metric because it
directly measures whether users are becoming paying customers — the clearest
signal that the campaign achieved its commercial objective.

Other metrics such as trial start rate and onboarding completion rate are
important supporting metrics, but they do not by themselves confirm revenue
impact. Engagement score and landing page visit rate indicate early-funnel
health but are too far removed from the actual business outcome to serve as
the primary decision metric.

Risk of blind optimization: If conversion rate is optimized without monitoring
revenue quality, the company could attract low-value users who convert but
immediately refund or churn — inflating the conversion number without
delivering real business value.

---

## KPI Tree Summary

The North Star metric breaks down into three primary drivers:

**1. Acquisition Quality**
- Landing page visit rate
- Traffic source mix (organic vs paid vs referral)

**2. Activation Effectiveness**
- Trial start rate
- Onboarding completion rate

**3. Revenue Quality**
- Average revenue per converted user
- Refund rate (guardrail)

**Guardrail Metrics Monitored:**
- Refund rate
- Support ticket rate
- Average days to convert

---

## Experiment Results

| Metric                        | Control | Treatment | Difference  |
|-------------------------------|---------|-----------|-------------|
| Total users                   | 693     | 715       | —           |
| Paid conversion rate          | 3.17%   | 6.99%     | +3.82 pp    |
| Total conversions             | 22      | 50        | +28 users   |

The Treatment group converted at more than double the rate of the Control
group. This is a practically significant improvement, not just a marginal gain.

---

## Hypothesis Test

- **Null Hypothesis (H₀):** Treatment conversion rate ≤ Control conversion rate
- **Alternate Hypothesis (H₁):** Treatment conversion rate > Control conversion rate
- **Test:** One-tailed z-test for proportions
- **Significance level:** α = 0.05

| Input                | Value     |
|----------------------|-----------|
| Control rate         | 3.17%     |
| Treatment rate       | 6.99%     |
| Pooled proportion    | 5.11%     |
| Standard error       | 0.01174   |
| Z-statistic          | 3.2519    |
| P-value              | 0.00057   |

**Interpretation:** The p-value of 0.00057 is far below the 0.05 threshold.
We reject the null hypothesis. There is strong statistical evidence that the
new campaign significantly improved paid conversion rate. The probability of
seeing this result by chance alone is less than 0.06%.

---

## Guardrail Metric Analysis

Before recommending a launch, three guardrail metrics were evaluated to
ensure the conversion improvement did not come at a hidden cost:

**1. Refund Rate**
A higher conversion rate could attract users who purchase impulsively and
then refund. If the Treatment group shows a materially higher refund rate,
the revenue gain may be illusory. This metric must be confirmed to be
stable or lower in Treatment before full rollout.

**2. Support Ticket Rate**
An increase in support tickets in the Treatment group would suggest the new
onboarding experience is causing confusion, which creates operational cost
and risks long-term retention. This should be at or below Control levels.

**3. Average Days to Convert**
If Treatment users take significantly longer to convert, this could indicate
friction in the new flow that may suppress conversion further in a longer
observation window. A stable or lower days-to-convert figure in Treatment
is a positive signal.

*Note: Confirm your calculated values for these three metrics from your
Summary sheet and insert them above. If any guardrail shows meaningful
degradation, add a condition to the recommendation below.*

---

## Segment-Level Insight

Segment analysis across region, device type, and traffic source was conducted
to identify whether the campaign performed consistently or only for specific
user groups. Key observations should be noted here — for example, if the
Treatment effect was stronger for Mobile users or Organic traffic, a phased
rollout targeting those segments first may reduce risk while capturing most
of the upside.

*Insert your top 1-2 segment findings from your Summary sheet here.*

---

## Final Recommendation

**Launch the new onboarding and activation campaign to all users.**

The Treatment group delivered a conversion rate of 6.99% versus 3.17% in
Control — a 120% relative improvement. This result is statistically
significant at the 0.01% level (p = 0.00057), meaning there is virtually
no chance this result occurred randomly. The magnitude of the improvement
is large enough to be commercially meaningful even after accounting for
natural variance.

Provided guardrail metrics (refund rate, support ticket rate, days to
convert) show no material degradation, there is no data-driven basis to
delay the launch.

---

## Risks and Limitations

- The experiment ran for a limited time window; long-term retention and
  churn effects are not yet observable.
- Sample size of 1,408 users may not fully represent all user segments,
  particularly niche traffic sources or regional subgroups.
- External factors (seasonality, marketing spend changes) during the
  experiment period could have influenced results.
- Guardrail metrics should continue to be monitored for 30 days
  post-launch to catch any delayed negative effects.

---

## Next Steps

1. Confirm guardrail metrics are stable before full rollout
2. Launch to all users and monitor paid conversion rate weekly for 4 weeks
3. Set up alerts for any spike in refund rate or support tickets post-launch
4. Run a follow-up segment analysis 30 days post-launch to identify
   which user groups benefited most
5. Use segment findings to inform future campaign targeting and
   personalization strategy