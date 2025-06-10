# Case study: Loan approval system fairness audit 

## Context

A financial institution is deploying a machine learning model to automate personal loan approvals. The system uses applicant data such as income, employment history, and credit score to predict default risk. Given past discriminatory practices in lending, the team is prioritizing fairness across race, gender, and income level.

---

## 1. Historical Context Assessment

- **Background**: Lending in the U.S. has a documented history of racial and gender bias.
- **Stakeholders**: Credit applicants, compliance/legal teams, regulators.
- **Potential Harms**: Unfair denials, higher default risk due to biased approvals, reputation damage, legal risk.
- **Protected Groups Identified**:
  - Race (Black, Hispanic, Asian, White)
  - Gender (Male, Female, Non-binary)
  - Income Level (Low, Medium, High)

---

## 2. Fairness Definition Selection

- **Primary Goal**: Equal opportunity — qualified applicants should receive equal treatment.
- **Secondary Metrics**: Predictive parity and demographic parity (for monitoring purposes).
- **Why**:
  - Lending is merit-based → Equal opportunity is key.
  - Regulatory bodies care about impact, not just intent.
  - Stakeholders want to ensure approvals are meaningful across demographics.

---

## 3. Bias Source Identification

- **Label Bias**: Ground truth ("default") may be influenced by past biased lending.
- **Feature Bias**: Income and employment stability reflect systemic inequalities.
- **Representation Bias**: Underrepresentation of older, low-income women in training data.

---

## 4. Fairness Metrics Implementation

| Metric                            | Value (95% CI)     | Notes                              |
|----------------------------------|--------------------|------------------------------------|
| **TPR Difference (Black vs White)** | 0.09 [0.06 – 0.12]  | Equal opportunity violation        |
| **PPV Difference (Race)**          | 0.06 [0.01 – 0.11]  | Predictive parity concern          |
| **Demographic Parity Difference**  | 0.11 [0.04 – 0.18]  | Indicates disparity in approvals   |
| **Intersectional TPR (Black + Female)** | 0.15 [0.09 – 0.21] | High disparity missed in aggregate |

**Visuals Produced**:
- Disparity bar charts for race/gender/income
- Intersectional fairness heatmap

---

## 5. Mitigation Actions

- **Constraint-based retraining**: Targeted equal opportunity across groups.
- **Threshold adjustment**: Group-specific post-processing.
- **Fair representation learning**: Reduced feature leakage from protected attributes.
- **Result**: TPR gap reduced to 0.03 (from 0.09); predictive parity improved; intersectional TPR gap halved.

---

## 6. Lessons & Recommendations

- Multiple metrics reveal different issues — use them together.
- Intersectional analysis is essential: largest disparities were at attribute intersections.
- Small sample sizes required Bayesian estimation + uncertainty visualization.
- Continuous monitoring with fairness dashboards recommended post-deployment.

---

## Integration with the Fairness Audit Playbook

| Component                     | Output Summary                                      |
|------------------------------|------------------------------------------------------|
| Historical Context Tool      | Identified relevant biases, stakeholders             |
| Fairness Definition Tool     | Selected equal opportunity + predictive parity       |
| Bias Source Identification   | Mapped label + feature bias, flagged underrepresentation |
| Fairness Metrics Tool        | Applied 4 metrics with CI + visualization            |

---

## Validation Summary

- **Statistical significance**: All disparities passed p < 0.05 with corrections
- **Confidence intervals reported**: Transparent uncertainty communication
- **Robustness**: Confirmed disparities consistent across time and data splits

---

## Final Recommendation

Deploy with model cards and dashboards that include:
- Key fairness metrics
- Confidence intervals
- Links to mitigation logic
- Stakeholder explanation

This system is not perfectly fair — but is now substantially more accountable, transparent, and equitable.
