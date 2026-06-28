# Campaign Experiment — KPI Framework & A/B Test Analysis

**Student:** Dhiraj Kalbande
**Student ID:** bitsom_ba_25111016
**Repository:** dhirajkalbande_bitsom_ba_25111016_part2_kpi_experiment

---

## Business Context

A subscription-based digital product company launched a new onboarding
and activation campaign to improve user conversion and early engagement.
Users were split into two groups — Control (existing experience) and
Treatment (new campaign experience). The goal was to determine whether
the new campaign should be rolled out to all users.

---

## Dataset Description

- **File:** data/campaign_experiment_data.xlsx
- **Total users:** 1,408
- **Control group:** 693 users
- **Treatment group:** 715 users
- **Date range:** January 2025 – May 2025
- **Key columns:** user_id, signup_date, experiment_group, region,
  device_type, traffic_source, plan_type, visited_landing_page,
  started_trial, completed_onboarding, converted_to_paid, revenue_30d,
  support_tickets_30d, refund_requested, days_to_convert,
  engagement_score

---

## Data Cleaning Notes

The following checks were performed on the raw dataset:

| Check | Result |
|-------|--------|
| Missing values (user_id, group, region, device, source, plan) | 0 |
| Missing values (binary conversion columns) | 0 |
| Missing values (days_to_convert) | 59 blanks — expected, as non-converters have no conversion date |
| Missing values (engagement_score) | 0 |
| Duplicate user IDs | 8 duplicate rows found at bottom of file (frequency = 2); these are the same users appearing twice and were excluded from rate calculations |
| Invalid binary values (visited_landing_page, started_trial, completed_onboarding, converted_to_paid) | 0 |
| Invalid binary values (refund_requested) | 100 records checked — all valid |
| Revenue outliers | Top 10 revenues ranged from $1,858 to $8,610. These were reviewed and retained as legitimate high-value conversions, not data errors |

---

## North Star Metric

**Paid Conversion Rate** was selected as the North Star metric.

This metric directly measures whether users are becoming paying customers,
which is the clearest signal that the campaign achieved its commercial
objective. Other metrics such as trial start rate and onboarding
completion rate are important supporting metrics but do not confirm
revenue impact on their own. Engagement score and landing page visit rate
indicate early-funnel health but are too far removed from the actual
business outcome to serve as the primary decision metric.

Risk of blind optimization: if conversion rate is optimized without
monitoring revenue quality, the company could attract users who convert
but quickly refund or churn — inflating the number without delivering
real business value.

---

## KPI Tree Summary

See: outputs/kpi_tree.png

The North Star metric (Paid Conversion Rate) breaks down into three
primary drivers:

**1. Acquisition Quality**
- Landing page visit rate
- Traffic source mix (organic vs paid vs referral)

**2. Activation Effectiveness**
- Trial start rate
- Onboarding completion rate

**3. Revenue Quality**
- Average revenue per converted user
- Refund rate (guardrail)

**Guardrail Metrics:**
- Refund rate
- Support ticket rate
- Average days to convert

---

## Experiment Analysis

Full analysis in: analysis/experiment_analysis.xlsx

### Control vs Treatment Summary

| Metric | Control | Treatment |
|--------|---------|-----------|
| User count | 693 | 715 |
| Landing page visit rate | 63.64% | 72.59% |
| Trial start rate | 25.11% | 29.09% |
| Onboarding completion rate | 15.58% | 21.26% |
| Paid conversion rate | 3.17% | 7.22% |
| Avg revenue per user | $51.75 | $53.88 |
| Avg revenue per converted user | $498.09 | $535.01 |
| Avg engagement score | 57.03 | 62.93 |

The Treatment group outperformed Control across every funnel metric.
Conversion rate more than doubled from 3.17% to 7.22%.

---

## Hypothesis Test Summary

Full notes in: analysis/hypothesis_test_notes.md

- **Test:** One-tailed z-test for proportions
- **Null hypothesis:** Treatment conversion rate ≤ Control conversion rate
- **Alternate hypothesis:** Treatment conversion rate > Control
- **Significance level:** α = 0.05

| Input | Value |
|-------|-------|
| Control rate | 3.17% |
| Treatment rate | 7.22% |
| Pooled proportion | 5.11% |
| Standard error | 0.01174 |
| Z-statistic | 3.2519 |
| P-value | 0.00057 |
| Decision | Reject H₀ — Launch |

The p-value of 0.00057 is far below the 0.05 threshold. There is
statistically significant evidence that the new campaign improved paid
conversion rate. The probability of observing this result by chance
alone is less than 0.06%.

---

## Guardrail Metrics

| Guardrail Metric | Control | Treatment | Risk? |
|-----------------|---------|-----------|-------|
| Refund rate | 0.00% | 0.42% | Low — only 3 refunds in Treatment, negligible |
| Support ticket rate | 14.72% | 24.62% | Moderate — Treatment users raised significantly more tickets |
| Avg days to convert | 8.9 days | 6.5 days | Positive — Treatment users converted faster |

**Key finding:** The support ticket rate increase from 14.72% to 24.62%
in the Treatment group is the only guardrail that warrants attention.
This may indicate that the new onboarding experience, while more
effective at converting users, is also generating more questions or
confusion post-signup. This should be monitored closely after launch
and addressed through improved in-product guidance or FAQ updates.

---

## Segment-Level Insight

Segment analysis was conducted across region, device type, and traffic
source. The Treatment campaign showed consistent improvement in
conversion rate across all four regions (North, South, East, West),
suggesting the campaign effect is not limited to a specific geography.
Device type and traffic source breakdowns further confirmed broad
effectiveness with no single segment driving the entire lift.

---

## Final Recommendation

**Launch the new onboarding and activation campaign to all users.**

The Treatment group delivered a conversion rate of 7.22% versus 3.17%
in Control — a 128% relative improvement that is statistically
significant (p = 0.00057). Revenue per converted user also improved
from $498 to $535. The only guardrail concern is an elevated support
ticket rate in Treatment, which should be addressed through improved
onboarding documentation and in-app support resources within 30 days
of launch.

---

## Assumptions and Limitations

- Users are assumed to be randomly and independently assigned to groups
- No significant external events (promotions, outages) are assumed
  during the experiment window
- The 59 missing days_to_convert values are expected and belong to
  non-converting users; they were excluded from the days-to-convert
  average calculation
- Revenue outliers (up to $8,610) were retained as valid high-value
  conversions
- Duplicate rows at the bottom of the dataset (8 users with
  frequency = 2) were identified and excluded from calculations
- Experiment ran January–May 2025; long-term churn and retention
  effects are not yet observable

---

## Screenshots

| File | Contents |
|------|----------|
| screenshots/summary_metrics.png | Control vs Treatment comparison table |
| screenshots/hypothesis_test_output.png | Z-test calculation sheet |
| screenshots/kpi_tree_preview.png | KPI tree diagram |
