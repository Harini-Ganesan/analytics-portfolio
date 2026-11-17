# Does Gamification Influence Electric Two-Wheeler Purchase Intent? A Survey Analysis in Chennai

**Harini Ganesan** · Final-year team capstone, B.Com Marketing Management, M.O.P. Vaishnav College for Women · Endowment Award · Tools: Google Forms, R

## 1. Business question

Electric two-wheeler brands increasingly use game-like features such as ride tracking, leaderboards, loyalty rewards, eco-impact scores and cost-savings calculators. Do these features actually make buyers more likely to choose an EV, and does the effect differ by age or gender?

## 2. Data

| Item | Detail |
|---|---|
| Method | Quantitative survey (Google Forms and in-person) |
| Respondents | 111 EV buyers and prospective buyers in Chennai, aged 18 to 50+ |
| Gender split | 72 female, 39 male |
| Scale | 5-point Likert scale for attitudes |
| Key variables | Gamification score, EV purchase choice, promotion effectiveness, likelihood to consider an EV, satisfaction with EV performance, age group, gender |

## 3. Hypotheses and tests

| # | Question | Test |
|---|---|---|
| H1 | Does gamification influence EV purchase choice? | Simple linear regression |
| H2 | Is promotion effectiveness related to likelihood to consider an EV? | Pearson correlation |
| H3 | Does satisfaction with EV performance differ between men and women? | Welch's two-sample t-test |
| H4 | Is age group associated with likelihood to consider an EV? | Chi-square test of independence |

## 4. Results

### H1: Gamification and purchase choice (regression)

| Measure | Value |
|---|---|
| R | 0.451 |
| R² | 0.204 (adjusted 0.196) |
| Intercept | 1.016 (SE 0.381, p = 0.008) |
| Gamification coefficient (B) | 0.536 (SE 0.101) |
| t | 5.27 |
| p-value | 6.7 × 10⁻⁷ |

**Reading:** gamification explains about a fifth of the variation in purchase choice. Each one-point rise in the gamification score goes with about a half-point rise in purchase choice. The effect is real but moderate: about 80% of the variation comes from other factors such as price, charging infrastructure and incentives.

### H2: Promotion effectiveness and likelihood to consider an EV (correlation)

| Measure | Value |
|---|---|
| Pearson r | 0.309 |
| n | 111 |
| p-value (recalculated) | ≈ 0.001 |

**Reading:** a moderate positive relationship. Respondents who rated promotions as more effective were more likely to consider an EV. Note: the original report gave p = 0.008; recalculating from r = 0.309 and n = 111 gives p ≈ 0.001. Both are below 0.05, so the conclusion is unchanged.

### H3: Satisfaction by gender (Welch's t-test)

| Group | n | Mean | SD |
|---|---|---|---|
| Female | 72 | 3.78 | 0.77 |
| Male | 39 | 3.51 | 0.97 |

| Measure | Value (recalculated from the group summaries) |
|---|---|
| Difference in means | 0.27 (female higher) |
| Welch t | ≈ −1.50 |
| df | ≈ 64.6 |
| p-value | ≈ 0.14 |

**Reading:** women rated EV performance slightly higher, but the difference is not statistically significant. Note: the original report gave t = −1.715 and p = 0.070; recalculating Welch's test from the reported means and standard deviations gives t ≈ −1.50 and p ≈ 0.14. Both are above 0.05, so the conclusion is unchanged.

### H4: Age group and likelihood to consider an EV (chi-square)

| Measure | Value |
|---|---|
| Pearson X² | 14.308 |
| df | 12 |
| p-value | 0.28 |
| Valid cases | 111 |

**Reading:** no significant link between age group and likelihood to consider an EV. Age does not appear to be a deciding factor in this sample.

## 5. Descriptive findings

| Finding | Share of respondents |
|---|---|
| Believe gamification can address concerns like cost, range and charging | 81% |
| Say gamification influenced their purchase | 44.4% |
| See charging infrastructure as a major barrier | 45% |

## 6. Reproducing the corrected tests in R

```r
# H2: p-value for a Pearson correlation of r = 0.309 with n = 111
r <- 0.309; n <- 111
t_cor <- r * sqrt(n - 2) / sqrt(1 - r^2)
2 * pt(-abs(t_cor), df = n - 2)
# Output: 0.00097

# H3: Welch's t-test from group means, SDs and sizes
m1 <- 3.507692; s1 <- 0.969856; n1 <- 39   # male
m2 <- 3.777778; s2 <- 0.773181; n2 <- 72   # female
se <- sqrt(s1^2 / n1 + s2^2 / n2)
t_w <- (m1 - m2) / se
df_w <- se^4 / ((s1^2 / n1)^2 / (n1 - 1) + (s2^2 / n2)^2 / (n2 - 1))
p_w <- 2 * pt(-abs(t_w), df = df_w)
c(t = t_w, df = df_w, p = p_w)
# Output: t = -1.50, df = 64.57, p = 0.138
```

## 7. Limits of this study

| Limit | Effect |
|---|---|
| Survey sent through Google Forms and in person | Closer to convenience sampling than true random sampling, so results may not represent all Chennai EV buyers |
| Self-reported Likert answers | Attitudes, not observed purchases |
| Single city, 111 respondents | Results may not generalise to other markets |
| Regression has one predictor | The 20% explained leaves most of the variation to other factors that were not modelled |
| Chi-square across many age-by-answer cells | Some cells may have small expected counts, which weakens the test |

## 8. What this means for EV brands

- Gamification is worth using, but as one part of the offer, alongside price, financing and charging access.
- Promotions matter: campaigns built around game-like features are linked to higher purchase consideration.
- Messages do not need to be split by age or gender based on this sample.

## 9. What I learned

- How to turn a business question into testable hypotheses and pick the right test for each.
- A p-value is not enough on its own: R² showed that gamification matters but explains only part of the decision.
- Re-checking reported numbers matters. Recalculating two of the tests from their own summary figures changed the p-values, though not the conclusions.
