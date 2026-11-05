# Statistical analysis in R

Two applied statistics projects in R (tidyverse, ggplot2, emmeans, car), each written as a reproducible R Markdown report for a reader who knows R but not the data. Both follow the same approach: check data integrity, choose the right test or model, report results with standard statistical conventions, and explain what they mean in plain English.

## 1. Which London Underground line should trial a new cooling system?
[`underground-temperatures/`](underground-temperatures/)

**Question:** Using monthly temperature readings across deep-level Tube lines, is the Bakerloo or Central line the better candidate for a cooling trial?

**Method:** data validation (missing values, duplicates, category checks), outlier identification and removal with documented reasons, descriptive statistics by line, violin plots, and Welch two-sample t-tests (all months and summer only).

**Findings:**
- Year-round, Bakerloo runs about 0.7°C hotter than Central (Welch t(281.6) = 2.18, p = 0.030; 95% CI 0.07 to 1.34°C).
- In summer (May to August) the difference disappears (t(92.98) = 0.16, p = 0.875): both lines are equally hot.
- Recommendation: target Bakerloo for year-round relief, but plan network-wide measures for summer heat.

## 2. Credit, wellbeing and a store trial
[`loans-wellbeing-and-store-trial/`](loans-wellbeing-and-store-trial/)

### Part 1: Payday loans, credit scores and wellbeing
**Question:** What predicts an applicant's credit score and self-reported wellbeing, and does higher income soften the credit-score penalty of an adverse credit event?

**Method:** data validation and documented exclusions, mean-centred multiple regression, an income × adverse-event interaction with nested model comparison, multicollinearity checks (VIF), estimated marginal means and residual diagnostics.

**Findings:**
- Income and adverse credit events drive credit score (R² = 0.42): each extra £1 of weekly income adds 1.22 points, and an adverse event costs 47.7 points (both p < .001).
- Higher income does not soften the adverse-event penalty (interaction p = .531).
- For wellbeing, an adverse credit event lowers scores by 1.03 points on a 7-point scale, more than loan approval raises them (0.70 points); income and credit score add nothing once these are included.

### Part 2: Did a new store layout increase sales?
**Question:** Six stores trialled a new layout and signage from Q3 while six acted as controls. Did the trial work?

**Method:** a mixed repeated-measures ANOVA (quarter within store, trial status between stores), planned before-versus-after contrasts, and outlet-level t-tests as a robustness check.

**Findings:**
- Sales trajectories diverged after the trial began (quarter × trial interaction, F(3, 30) = 11.33, p < .001).
- Trial stores gained about £353,000 more in average quarterly sales than control stores after the change (95% CI £219,000 to £487,000), with the effect starting immediately at Q3.
- Control stores showed no significant change, and all six trial stores improved, so no single store drove the result.

## Notes
- The original datasets are not included.
- Generative AI was used for code suggestions, proofreading and presentation; all analysis, model choices and interpretation are my own.

**Author:** Jashwanth Anand Shankar · [LinkedIn](https://linkedin.com/in/jash24298)
