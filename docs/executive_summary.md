# Executive Summary

**Telco Customer Churn Analysis**  
Taofeek Salami · July 2026, revised October 2026

---

## Summary

26.54% of customers churned (1,869 of 7,043). They had been paying £139,130.85 a month, 30.50% of all monthly charges, or about £1.67M a year. Churn is not spread evenly: it is highest among month-to-month customers, customers in their first year, fibre-optic customers and customers who pay by electronic check. The month-to-month and fibre-optic groups also hold most of the business's monthly revenue.

---

## Background

The data is a single snapshot of 7,043 customers of a telecom company: their contract, services, payment method, tenure, charges and whether they had churned. It has no dates, so it shows which customers left but not when, or how their behaviour changed beforehand. Every figure below was calculated in SQL and reported through an Excel dashboard.

---

## Key Findings

### Customers

| Group | Churn rate | Comparison |
|-------|-----------|------------|
| Month-to-month contract | 42.71% | One-year 11.27%, two-year 2.83%; month-to-month is 15× the two-year rate |
| First 12 months of tenure | 47.44% | 13–36 months 25.54%, 37+ months 11.93%; these customers are 55.5% of all churners (1,037 of 1,869) |
| Fibre-optic internet | 41.89% | DSL 18.96%, no internet service 7.40% |
| Electronic-check payment | 45.29% | Mailed check 19.11%, bank transfer 16.71%, credit card 15.24% |

Churned customers had an average tenure of 18.0 months, against 37.6 months for customers who stayed.

### Revenue

- **Monthly charges paid by churned customers:** £139,130.85 of £456,116.60, or 30.50%. Annualised, £1,669,570.20.
- **Charges by churn status:** churned customers were paying £74.44 a month on average, £13.17 more than retained customers (£61.27).
- **Churn by charge level:** customers paying £70 or more a month churned at 35.48%, against 23.65% for £35–£70 and 10.86% for under £35.
- **Revenue per customer by contract:** two-year customers average £3,728.93 in total charges, 2.7× month-to-month customers (£1,369.25).

### Concentration

- **Month-to-month contracts:** 55.02% of customers and 56.41% of monthly revenue, in the contract type with the highest churn rate.
- **Fibre-optic service:** 62.11% of monthly revenue, in the service with the highest churn rate.
- **One profile:** customers on month-to-month contracts, paying over £70 a month, with under 12 months' tenure. 814 customers fit it, and 69.53% of them churned, 3.3× the 20.92% rate for all other customers.

---

## What This Means

Retention effort is likely to matter most where churn and revenue overlap: month-to-month customers in their first year, and fibre-optic customers. These groups have the highest churn rates, and month-to-month and fibre-optic customers also hold most of the business's monthly revenue (56.41% and 62.11%).

---

## Recommendations

1. **Early-tenure retention.** Customers in their first 12 months have the highest churn rate and make up more than half of all churners. Onboarding and first-year engagement are the natural place to test retention measures.
2. **Longer contracts.** Month-to-month customers churn at 42.71%, against 2.83% for two-year contracts. Test incentives to move customers to one- or two-year plans, and measure whether those who switch stay longer.
3. **Fibre-optic experience.** Fibre optic brings in the most revenue and has the highest churn of any service. The data cannot say why, so the next step is to look at service quality, pricing and support contacts for these customers.
4. **Higher-paying customers.** Customers paying £70 or more a month churned at 35.48%. Retention offers for this group early in their tenure are worth testing, since churners averaged 18 months of tenure.
5. **Test the high-risk profile before using it.** 566 of the 814 customers in the profile had already churned. Apply the profile to customers who are still active, and check after a few months whether it flagged the ones who later left, before using it to target offers.

---

## Risks and Limitations

- **Association, not cause.** Every finding compares churn rates between groups. The groups overlap (one customer can be on a month-to-month contract, on fibre optic and in their first year at once), and no test separates their effects, so none of the differences can be read as a cause.
- **No significance testing.** The differences between groups were not tested statistically. Most are large and the groups contain hundreds or thousands of customers, but the smallest comparisons (such as the 15 one-year customers in their first 12 months on the highest charges) are too small to rely on.
- **Single snapshot.** With no dates, the data cannot show churn over time, seasonal patterns or what customers did before leaving.
- **Revenue lost is a snapshot.** The £1.67M annualises the monthly charges of customers who had already churned. It is not a forecast of future losses.
- **Currency.** The source data does not state a currency; amounts are reported in pounds (£).
- **Data source.** This is public IBM sample data, so the findings illustrate the method and are not evidence about a real company.

---

## Next Steps

- Collect dated customer records (start date, end date, monthly charges over time) so churn can be tracked by cohort and the high-risk profile can be tested on customers before they leave.
- Test whether the differences by contract, tenure, service and payment method hold when the others are held constant, for example with a logistic regression.
- Agree with the business the size of reduction in churn that would justify a retention programme, so future results can be judged against it.
